<b>简单说明</b>
![](http://7xwdl6.com1.z0.glb.clouddn.com/pic/android_kcptun.png)
1. 实现了手机上 Kcptun 的开启关闭的 Dialog；
2. 点击 `打开` 按钮可以打开Kcptun，点击 `关闭` 按钮可以关闭 Kcptun，点击 `阴影空白区域` 可以取消操作；
3. 遵循 Material Design；
4. 可以通过 Tasker 的 App Factory 导出独立 APK 运行，我就导出了一个哈哈。

为了方便，这个脚本除了 Tasker 主程序之外还有一个依赖。

<b>依赖和要求</b>
1. [`Tasker`](http://www.coolapk.com/apk/net.dinglisch.android.taskerm)  作者好像把命令也汉化了，不知道英文版能不能正常运行，我是酷安网这个版本。
2. [`Material Design Plugin`](http://www.coolapk.com/apk/com.nick.mowen.materialdesignplugin)这个做对话框比较方便，也符合系统规范，也推荐大家使用。
3. `Root 权限`，这个不用多说。
4. 将符合自己手机架构的预编译版本放到 `/system/bin/` 权限 `755`， 这样脚本直接能用，也方便你的调试和拓展 ^_^ 如果不在这个路径或不是这个文件名，请自己修改脚本里的路径和文件名。
5. 运行使用了 `nohup`，关闭使用了 `pkill` ，请先确认shell能正常运行这些命令和 Kcptun。
6. 为了这种小程序用起来方便，我没有弄动态的参数设置啥的，做起来也麻烦，反正就配置一次而已。

<b>XML文件</b>
```xml
<TaskerData sr="" dvi="1" tv="4.8u5m">
	<Task sr="task2">
		<cdate>1470064304000</cdate>
		<edate>1470109963742</edate>
		<id>2</id>
		<nme>Kcptun</nme>
		<pri>100</pri>
		<Kid sr="Kid">
			<launchID>2</launchID>
			<pkg>com.android.kcptun.shell</pkg>
			<vnme>1.1</vnme>
			<vnum>2</vnum>
		</Kid>
		<Action sr="act0" ve="7">
			<code>607566781</code>
			<Bundle sr="arg0">
				<Vals sr="val">
					<com.twofortyfouram.locale.intent.extra.BLURB>An activity with the title Kcptun and items of 打开</com.twofortyfouram.locale.intent.extra.BLURB>
					<com.twofortyfouram.locale.intent.extra.BLURB-type>java.lang.String</com.twofortyfouram.locale.intent.extra.BLURB-type>
					<com.yourcompany.yourapp.extra.BOOLEAN_BACK>false</com.yourcompany.yourapp.extra.BOOLEAN_BACK>
					<com.yourcompany.yourapp.extra.BOOLEAN_BACK-type>java.lang.Boolean</com.yourcompany.yourapp.extra.BOOLEAN_BACK-type>
					<com.yourcompany.yourapp.extra.BOOLEAN_CLICK>false</com.yourcompany.yourapp.extra.BOOLEAN_CLICK>
					<com.yourcompany.yourapp.extra.BOOLEAN_CLICK-type>java.lang.Boolean</com.yourcompany.yourapp.extra.BOOLEAN_CLICK-type>
					<com.yourcompany.yourapp.extra.BOOLEAN_DARK_STATUS>false</com.yourcompany.yourapp.extra.BOOLEAN_DARK_STATUS>
					<com.yourcompany.yourapp.extra.BOOLEAN_DARK_STATUS-type>java.lang.Boolean</com.yourcompany.yourapp.extra.BOOLEAN_DARK_STATUS-type>
					<com.yourcompany.yourapp.extra.BOOLEAN_LIST_FAB>false</com.yourcompany.yourapp.extra.BOOLEAN_LIST_FAB>
					<com.yourcompany.yourapp.extra.BOOLEAN_LIST_FAB-type>java.lang.Boolean</com.yourcompany.yourapp.extra.BOOLEAN_LIST_FAB-type>
					<com.yourcompany.yourapp.extra.BOOLEAN_LIST_SHARE>false</com.yourcompany.yourapp.extra.BOOLEAN_LIST_SHARE>
					<com.yourcompany.yourapp.extra.BOOLEAN_LIST_SHARE-type>java.lang.Boolean</com.yourcompany.yourapp.extra.BOOLEAN_LIST_SHARE-type>
					<com.yourcompany.yourapp.extra.BOOLEAN_MENU>false</com.yourcompany.yourapp.extra.BOOLEAN_MENU>
					<com.yourcompany.yourapp.extra.BOOLEAN_MENU-type>java.lang.Boolean</com.yourcompany.yourapp.extra.BOOLEAN_MENU-type>
					<com.yourcompany.yourapp.extra.BOOLEAN_MOVE>false</com.yourcompany.yourapp.extra.BOOLEAN_MOVE>
					<com.yourcompany.yourapp.extra.BOOLEAN_MOVE-type>java.lang.Boolean</com.yourcompany.yourapp.extra.BOOLEAN_MOVE-type>
					<com.yourcompany.yourapp.extra.BOOLEAN_PERSISTENT>false</com.yourcompany.yourapp.extra.BOOLEAN_PERSISTENT>
					<com.yourcompany.yourapp.extra.BOOLEAN_PERSISTENT-type>java.lang.Boolean</com.yourcompany.yourapp.extra.BOOLEAN_PERSISTENT-type>
					<com.yourcompany.yourapp.extra.BOOLEAN_SINGLE_ICON>false</com.yourcompany.yourapp.extra.BOOLEAN_SINGLE_ICON>
					<com.yourcompany.yourapp.extra.BOOLEAN_SINGLE_ICON-type>java.lang.Boolean</com.yourcompany.yourapp.extra.BOOLEAN_SINGLE_ICON-type>
					<com.yourcompany.yourapp.extra.BOOLEAN_SWIPE>false</com.yourcompany.yourapp.extra.BOOLEAN_SWIPE>
					<com.yourcompany.yourapp.extra.BOOLEAN_SWIPE-type>java.lang.Boolean</com.yourcompany.yourapp.extra.BOOLEAN_SWIPE-type>
					<com.yourcompany.yourapp.extra.INT_SIDE>0</com.yourcompany.yourapp.extra.INT_SIDE>
					<com.yourcompany.yourapp.extra.INT_SIDE-type>java.lang.Integer</com.yourcompany.yourapp.extra.INT_SIDE-type>
					<com.yourcompany.yourapp.extra.STRING_BCOLOR>#ffffff</com.yourcompany.yourapp.extra.STRING_BCOLOR>
					<com.yourcompany.yourapp.extra.STRING_BCOLOR-type>java.lang.String</com.yourcompany.yourapp.extra.STRING_BCOLOR-type>
					<com.yourcompany.yourapp.extra.STRING_BOTTOM></com.yourcompany.yourapp.extra.STRING_BOTTOM>
					<com.yourcompany.yourapp.extra.STRING_BOTTOM-type>java.lang.String</com.yourcompany.yourapp.extra.STRING_BOTTOM-type>
					<com.yourcompany.yourapp.extra.STRING_BOTTOM_COMMAND></com.yourcompany.yourapp.extra.STRING_BOTTOM_COMMAND>
					<com.yourcompany.yourapp.extra.STRING_BOTTOM_COMMAND-type>java.lang.String</com.yourcompany.yourapp.extra.STRING_BOTTOM_COMMAND-type>
					<com.yourcompany.yourapp.extra.STRING_BOTTOM_ICON></com.yourcompany.yourapp.extra.STRING_BOTTOM_ICON>
					<com.yourcompany.yourapp.extra.STRING_BOTTOM_ICON-type>java.lang.String</com.yourcompany.yourapp.extra.STRING_BOTTOM_ICON-type>
					<com.yourcompany.yourapp.extra.STRING_COLOR>#26518f</com.yourcompany.yourapp.extra.STRING_COLOR>
					<com.yourcompany.yourapp.extra.STRING_COLOR-type>java.lang.String</com.yourcompany.yourapp.extra.STRING_COLOR-type>
					<com.yourcompany.yourapp.extra.STRING_COMMAND>y,c</com.yourcompany.yourapp.extra.STRING_COMMAND>
					<com.yourcompany.yourapp.extra.STRING_COMMAND-type>java.lang.String</com.yourcompany.yourapp.extra.STRING_COMMAND-type>
					<com.yourcompany.yourapp.extra.STRING_ICONS>关闭</com.yourcompany.yourapp.extra.STRING_ICONS>
					<com.yourcompany.yourapp.extra.STRING_ICONS-type>java.lang.String</com.yourcompany.yourapp.extra.STRING_ICONS-type>
					<com.yourcompany.yourapp.extra.STRING_ITEMS>打开</com.yourcompany.yourapp.extra.STRING_ITEMS>
					<com.yourcompany.yourapp.extra.STRING_ITEMS-type>java.lang.String</com.yourcompany.yourapp.extra.STRING_ITEMS-type>
					<com.yourcompany.yourapp.extra.STRING_LENGTH></com.yourcompany.yourapp.extra.STRING_LENGTH>
					<com.yourcompany.yourapp.extra.STRING_LENGTH-type>java.lang.String</com.yourcompany.yourapp.extra.STRING_LENGTH-type>
					<com.yourcompany.yourapp.extra.STRING_MESSAGE>Kcptun</com.yourcompany.yourapp.extra.STRING_MESSAGE>
					<com.yourcompany.yourapp.extra.STRING_MESSAGE-type>java.lang.String</com.yourcompany.yourapp.extra.STRING_MESSAGE-type>
					<com.yourcompany.yourapp.extra.STRING_SCOLOR>#adaeb0</com.yourcompany.yourapp.extra.STRING_SCOLOR>
					<com.yourcompany.yourapp.extra.STRING_SCOLOR-type>java.lang.String</com.yourcompany.yourapp.extra.STRING_SCOLOR-type>
					<com.yourcompany.yourapp.extra.STRING_SEPARATOR></com.yourcompany.yourapp.extra.STRING_SEPARATOR>
					<com.yourcompany.yourapp.extra.STRING_SEPARATOR-type>java.lang.String</com.yourcompany.yourapp.extra.STRING_SEPARATOR-type>
					<com.yourcompany.yourapp.extra.STRING_TCOLOR></com.yourcompany.yourapp.extra.STRING_TCOLOR>
					<com.yourcompany.yourapp.extra.STRING_TCOLOR-type>java.lang.String</com.yourcompany.yourapp.extra.STRING_TCOLOR-type>
					<com.yourcompany.yourapp.extra.STRING_TICON>需要打开或关闭吗？</com.yourcompany.yourapp.extra.STRING_TICON>
					<com.yourcompany.yourapp.extra.STRING_TICON-type>java.lang.String</com.yourcompany.yourapp.extra.STRING_TICON-type>
					<com.yourcompany.yourapp.extra.STRING_TYPE>Dialog</com.yourcompany.yourapp.extra.STRING_TYPE>
					<com.yourcompany.yourapp.extra.STRING_TYPE-type>java.lang.String</com.yourcompany.yourapp.extra.STRING_TYPE-type>
					<com.yourcompany.yourcondition.extra.INT_VERSION_CODE>87</com.yourcompany.yourcondition.extra.INT_VERSION_CODE>
					<com.yourcompany.yourcondition.extra.INT_VERSION_CODE-type>java.lang.Integer</com.yourcompany.yourcondition.extra.INT_VERSION_CODE-type>
					<net.dinglisch.android.tasker.RELEVANT_VARIABLES>&lt;StringArray sr=""&gt;&lt;_array_net.dinglisch.android.tasker.RELEVANT_VARIABLES0&gt;%md_command
Dialog item is clicked: command is returned
Dialog is dismissed: Dismissed is returned

&lt;/_array_net.dinglisch.android.tasker.RELEVANT_VARIABLES0&gt;&lt;/StringArray&gt;</net.dinglisch.android.tasker.RELEVANT_VARIABLES>
					<net.dinglisch.android.tasker.RELEVANT_VARIABLES-type>[Ljava.lang.String;</net.dinglisch.android.tasker.RELEVANT_VARIABLES-type>
					<net.dinglisch.android.tasker.extras.VARIABLE_REPLACE_KEYS>com.yourcompany.yourapp.extra.STRING_MESSAGE com.yourcompany.yourapp.extra.STRING_ITEMS com.yourcompany.yourapp.extra.STRING_COLOR com.yourcompany.yourapp.extra.STRING_COMMAND com.yourcompany.yourapp.extra.STRING_BCOLOR com.yourcompany.yourapp.extra.STRING_BOTTOM com.yourcompany.yourapp.extra.STRING_BOTTOM_COMMAND com.yourcompany.yourapp.extra.STRING_TCOLOR com.yourcompany.yourapp.extra.STRING_SCOLOR com.yourcompany.yourapp.extra.STRING_ICONS com.yourcompany.yourapp.extra.STRING_BOTTOM_ICON com.yourcompany.yourapp.extra.STRING_TICON com.yourcompany.yourapp.extra.STRING_SCOLOR</net.dinglisch.android.tasker.extras.VARIABLE_REPLACE_KEYS>
					<net.dinglisch.android.tasker.extras.VARIABLE_REPLACE_KEYS-type>java.lang.String</net.dinglisch.android.tasker.extras.VARIABLE_REPLACE_KEYS-type>
					<net.dinglisch.android.tasker.subbundled>true</net.dinglisch.android.tasker.subbundled>
					<net.dinglisch.android.tasker.subbundled-type>java.lang.Boolean</net.dinglisch.android.tasker.subbundled-type>
				</Vals>
			</Bundle>
			<Str sr="arg1" ve="3">com.nick.mowen.materialdesignplugin</Str>
			<Str sr="arg2" ve="3">com.nick.mowen.materialdesign.ui.DialogEditActivity</Str>
			<Int sr="arg3" val="20"/>
		</Action>
		<Action sr="act1" ve="7">
			<code>37</code>
			<ConditionList sr="if">
				<Condition sr="c0" ve="3">
					<lhs>%md_command</lhs>
					<op>2</op>
					<rhs>y</rhs>
				</Condition>
			</ConditionList>
		</Action>
		<Action sr="act10" ve="7">
			<code>548</code>
			<Str sr="arg0" ve="3">已取消开启或关闭 Kcptun</Str>
			<Int sr="arg1" val="0"/>
		</Action>
		<Action sr="act2" ve="7">
			<code>548</code>
			<Str sr="arg0" ve="3">正在打开...</Str>
			<Int sr="arg1" val="0"/>
		</Action>
		<Action sr="act3" ve="7">
			<code>123</code>
			<Str sr="arg0" ve="3">nohup /system/bin/kcptun -l :12948 -r 你的IP:端口 -key 你的密码 -mtu 1400 -sndwnd 128 -rcvwnd 1024 -mode fast2 -dscp 46 &gt;/sdcard/nohup.out 2&gt;&amp;1 &amp;</Str>
			<Int sr="arg1" val="0"/>
			<Int sr="arg2" val="1"/>
			<Str sr="arg3" ve="3"/>
			<Str sr="arg4" ve="3"/>
			<Str sr="arg5" ve="3"/>
		</Action>
		<Action sr="act4" ve="7">
			<code>548</code>
			<Str sr="arg0" ve="3">已打开 Kcptun</Str>
			<Int sr="arg1" val="0"/>
		</Action>
		<Action sr="act5" ve="7">
			<code>43</code>
			<ConditionList sr="if">
				<Condition sr="c0" ve="3">
					<lhs>%md_command</lhs>
					<op>2</op>
					<rhs>c</rhs>
				</Condition>
			</ConditionList>
		</Action>
		<Action sr="act6" ve="7">
			<code>548</code>
			<Str sr="arg0" ve="3">正在关闭...</Str>
			<Int sr="arg1" val="0"/>
		</Action>
		<Action sr="act7" ve="7">
			<code>123</code>
			<Str sr="arg0" ve="3">pkill /system/bin/kcptun</Str>
			<Int sr="arg1" val="0"/>
			<Int sr="arg2" val="1"/>
			<Str sr="arg3" ve="3"/>
			<Str sr="arg4" ve="3"/>
			<Str sr="arg5" ve="3"/>
		</Action>
		<Action sr="act8" ve="7">
			<code>548</code>
			<Str sr="arg0" ve="3">已关闭 Kcptun</Str>
			<Int sr="arg1" val="0"/>
		</Action>
		<Action sr="act9" ve="7">
			<code>43</code>
		</Action>
		<Img sr="icn" ve="2">
			<cls>net.dinglisch.android.tasker.Kid</cls>
			<pkg>com.android.kcptun.shell</pkg>
		</Img>
	</Task>
</TaskerData>
```
<b>请将配置中的参数修改为你自己的！否则无法运行。</b>
[文章地址](http://ouyang.ga/android_kcptun_tasker_dialog.html)