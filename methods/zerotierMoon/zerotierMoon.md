# zerotier-moon记录

>   参考视频：[搭建zeroTier Moon](https://tvtv.fun/vps/001.html)。

由于原视频和教程都是个人记录，保存在其个人博客网站上面，为了避免技术失传，在此重新进行记录。

---

## 服务器配置

-   首先更新和升级apt

```shell
sudo apt update
sudo apt upgrade
```

-   然后在服务器安装zerotier-one

```shell
curl -s https://install.zerotier.com | sudo bash
```

在zerotier官网创建一个虚拟局域网，或者使用已有的局域网，获取其网络ID，然后让服务器加入局域网。

```shell
sudo zerotier-cli join xxxxxxxx
```

其中，xxxxxxxx表示局域网ID，这个ID从zerotier的管理网站获取。

-   判断是否成功加入到局域网中

在服务器中，使用命令：

```shell
sudo zerotier-cli listnetworks
```

检查ip地址是否包含zerotier网站上分配的虚拟地址，如果有，说明加入成功。

-   配置Moon

由于内容不在普通用户的HOME中，因此接下来的任务推荐使用root用户进行。

首先要进入zerotier-one的安装目录，一般是`/var/lib/zerotier-one`。

```shell
cd /var/lib/zerotier-one
```

-   生成moon.json配置文件

```shell
sudo zerotier-idtool initmoon identity.public >> moon.json
```

-   编辑moon.json配置

```shell
sudo nano moon.json
```

也可以用vi或者vim。将json配置文件中的`"stableEndpoints": []`，修改为`"stableEndpoints": ["ServerIP/9993"]`，其中，`ServerIP`替换成云服务器的公网IP。

-   生成`.moon`文件

```shell
sudo zerotier-idtool genmoon moon.json
```

生成的`.moon`文件的文件名一般是6个前导0，加上服务器的zerotierID。

-   将`.moon`文件移动到`moons.d`文件夹中

```shell
sudo mkdir moons.d
sudo mv 000000xxxxxxxxxx.moon moons.d
```

-   重启zerotier-one服务

```shell
sudo systemctl restart zerotier-one
```

至此，Moon配置完毕。

## PC（windows）配置

>   **提示**：Windows 系统的默认程序目录位于 `C:\Program Files (x86)\ZeroTier\One`。

-   以管理员身份打开 PowerShell，将命令中的两组 `xxxxxxxxxx` 都替换成 moon 的节点ID。

```cmd
PS C:\Windows\system32> zerotier-cli.bat orbit xxxxxxxxxx xxxxxxxxxx
```

-   检查是否添加成功

```cmd
PS C:\Windows\system32> zerotier-cli.bat listpeers
```

上面的命令可以列出虚拟局域网中的全部终端，且在每一行（每个终端）的末尾标明终端类型，`LEAF`表示普通终端；`Moon`表示Moon终端；`Planet`表示行星服务器。

