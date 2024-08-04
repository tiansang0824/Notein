# windows的特殊文件夹

本文中的文件夹，都可以使用`shell:指令`的方式打开，可以是cmd指令，也可以是windows运行指令。

## 1. startup

通过`startup`文件夹可以完成自定义的程序自启动：
```text
shell:startup
```

这个文件夹默认对当前用户生效，如果想要设置所有用户生效，可以修改前面的shell指令：
```text
shell:common startup
```

将程序快捷方式放入这个文件夹，则会打开全体用户的启动文件夹。

## 2. fonts-字体文件夹

通过`fonts`可以打开字体文件夹。

```text
shell:fonts
```

这样的方法可以打开本地字体文件夹，方便查看和设置/删除本机中的全部字体。

## 3. send to文件夹

通过`sendto`可以打开sendto文件夹：
```text
shell:sendto
```

该菜单对应windows右键图标的“发送到”文件夹，从而手动指定常用应用启动特殊程序。

## 4. programs文件夹

```text
shell:programs
```

该文件夹是开始菜单结构。可以通过修改文件夹的方式修改开始菜单结构。

同startup文件夹一样，该文件夹可以通过common参数，打开全局设置。

## 5. appsfolder

```text
shell:appsfolder
```

该文件夹会列出电脑上安装的所有应用，方便检查电脑的应用和创建对应快捷方式。

## 6. Quick Launch

```text
shell:Quick Launch
```

在quick launch文件夹下面，有一个`user pinned`文件夹，该文件夹中可以管理托盘图标。