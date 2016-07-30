**# 一、交叉编译环境配置**

来源网友博文： [极路由1s(mt7620a)OpenWrt交叉编译go程序](http://studygolang.com/articles/7326)


// 下载go-mips32源 
git clone https://github.com/gomini/go-mips32.git 
cd go-mips32/src

// 配置GO编译参数 
export GOOS=linux 
export GOARCH=mips32le

// 执行编译

./make.bash 
cd ..

// 创建编译后文件存放文件夹 
sudo mkdir /opt/mipsgo

// 复制 
sudo cp -R * /opt/mipsgo



// 如果第一步无报错完成后再继续下一步操作，如果出现问题请Google修复，或更换系统，我用ubuntukylin-15.10编译成功。





**# 二、编译kcptun**

源码来源：https://github.com/xtaci/kcptun

// 创建程序目录
mkdir /opt/kcptun
cd /opt/kcptun

// go工程参数配置 
export GOPATH=/opt/mipsgo/src/gocode
export GOOS=linux 
export GOARCH=mips32le
export GOROOT=/opt/mipsgo 
export PATH=/opt/mipsgo/bin:$PATH

// 提前下载kcptun的依赖库
go get -v  golang.org/x/crypto/pbkdf2
go get -v  github.com/xtaci/kcp-go
go get -v  github.com/urfave/cli
go get -v  github.com/hashicorp/yamux
go get -v  github.com/golang/snappy
go get -v  golang.org/x/net/ipv4

// 由于依赖库没mips32le，需要填坑
// go get -v  golang.org/x/net/ipv4
// 运行以上命令时会提示报错：/golang.org/x/net/ipv4/icmp.go:34:2: error: use of undefined type 'sysICMPFilter'
// 参考补丁填坑：https://bugzilla.redhat.com/attachment.cgi?id=1147705&action=diff
// 填坑步骤：gen.go里面添加mips32le的判断。复制一个zsys_linux_mips64le.go文件，改名zsys_linux_mips32le.go
// 填坑完成后再运行一次：
go get -v  golang.org/x/net/ipv4

// 下载kcptun
go get -v  github.com/xtaci/kcptun/client
go get -v  github.com/xtaci/kcptun/server

// 编译
VERSION=`date -u +%Y%m%d`
LDFLAGS="-X main.VERSION=$VERSION -s -w"
env CGO_ENABLED=0 GOOS=linux GOARCH=mips32le go build -ldflags "$LDFLAGS" -o client_linux_mips  github.com/xtaci/kcptun/client
env CGO_ENABLED=0 GOOS=linux GOARCH=mips32le go build -ldflags "$LDFLAGS" -o server_linux_mips  github.com/xtaci/kcptun/server

// 几秒后出现程序文件，编译成功。我们路由只需要用client。
// 毕竟路由不做server，server主程序要去github下载或参考以上步骤，改export GOARCH=amd64就能自己编译amd64版本。


**# 三、部署服务**

// kcptun服务端部署教程
// https://blog.kuoruan.com/102.html
// http://www.cmsky.com/kcptun/

// 服务器:
./server_linux_amd64 -t "服务器IP地址:8388" -l ":554" -key hiboy -mtu 1400 -sndwnd 2048 -rcvwnd 2048 --crypt none --mode fast2 --nocomp  // 转发到服务器的本地8388端口
// crypt：xor/none都不算加密，通过参数 -nocomp 在两端同时设定以关闭压缩。key可以自定义

// kcptun配置客户端参考

// 客户端: 
./client_linux_mips -r "服务器IP地址:554" -l ":8388" -key hiboy -mtu 1400 -sndwnd 256 -rcvwnd 2048 --crypt none --mode fast2 --nocomp  -dscp 46   // 监听客户端的本地8388端口
// xor/none都不算加密，通过参数 -nocomp 在两端同时设定以关闭压缩。key可以自定义
// D1双核4线程可以添加 [--conn 4] 参数实现多线程下载

// Shadowsocks 客户端配置
// 在SS服务器新建服务端口：8388
// 路由SS配置服务器地址:：127.0.0.1
// 路由SS配置服务器端口:：8388
// 正确填写你的 Shadowsocks 密码，加密方式，协议和混淆方式。
// 两边都启动kcptun、启动SS，测试是否正确运行。

// 已经在华硕7620固件测试有效，稍后会集成到固件里面的。




sndwnd/rcvwnd 设定参考
sndwnd * mtu 不能超过上行带宽, rcvwnd * mtu 不能超过下行带宽
对延迟不敏感的情况，比如只用于数据传输，可以用MODE_FAST，20ms的内部时钟，默认值
对延迟敏感的情况，可以用FAST2模式，但必须严格注意第一条规则
更多说明移步：https://github.com/xtaci/kcptun

