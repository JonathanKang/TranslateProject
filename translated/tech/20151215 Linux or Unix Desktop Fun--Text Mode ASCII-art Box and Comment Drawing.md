
Linux / Unix 桌面娱乐 :
文字模式的带有ASCII艺术的Box与评论绘制

================================================================================
Boxes 命令不仅是一个文本过滤器，同时是一个很少人知道的可以为了乐趣或者需要在它的输入文本或者代码周围画各种ASCII艺术画的工具。你可以迅速创建邮件签名，或者使用各种编程语言创建局部评论。这个命令计划被vim文本编辑器使用，但是也可以被支持过滤的文本编辑器使用，同时从命令行作为一个单独的工具使用。


### 任务: 安装 boxes ###

使用 [apt-get command][1] 在 Debian / Ubuntu Linux中安装 boxes  :

    $ sudo apt-get install boxes

输出示例 :

    Reading package lists... Done
    Building dependency tree
    Reading state information... Done
    The following NEW packages will be installed:
      boxes
    0 upgraded, 1 newly installed, 0 to remove and 6 not upgraded.
    Need to get 0 B/59.8 kB of archives.
    After this operation, 205 kB of additional disk space will be used.
    Selecting previously deselected package boxes.
    (Reading database ... 224284 files and directories currently installed.)
    Unpacking boxes (from .../boxes_1.0.1a-2.3_amd64.deb) ...
    Processing triggers for man-db ...
    Setting up boxes (1.0.1a-2.3) ...

RHEL / CentOS / Fedora Linux 用户, 使用 [yum command to install boxes][2] (首先 [enable EPEL repo as described here][3]):

    # yum install boxes

输出示例 :

    Loaded plugins: rhnplugin
    Setting up Install Process
    Resolving Dependencies
    There are unfinished transactions remaining. You might consider running yum-complete-transaction first to finish them.
    --> Running transaction check
    ---> Package boxes.x86_64 0:1.1-8.el6 will be installed
    --> Finished Dependency Resolution
    Dependencies Resolved
    ==========================================================================
     Package        Arch            Version               Repository     Size
    ==========================================================================
    Installing:
     boxes          x86_64          1.1-8.el6             epel           64 k
    Transaction Summary
    ==========================================================================
    Install       1 Package(s)
    Total download size: 64 k
    Installed size: 151 k
    Is this ok [y/N]: y
    Downloading Packages:
    boxes-1.1-8.el6.x86_64.rpm                         |  64 kB     00:00
    Running rpm_check_debug
    Running Transaction Test
    Transaction Test Succeeded
    Running Transaction
      Installing : boxes-1.1-8.el6.x86_64                                 1/1
    Installed:
      boxes.x86_64 0:1.1-8.el6
    Complete!

FreeBSD 用户可以按如下来使用 :

    cd /usr/ports/misc/boxes/ && make install clean

或者，使用  pkg_add 命令来增加包:

    # pkg_add -r boxes

### 在一些给定文本周围画出任何种类的box ###

输入下列命令 :

    echo "This is a test" | boxes

或者，通过设置要使用的设计的名字来使用 :

    echo -e "\n\tVivek Gite\n\tvivek@nixcraft.com\n\twww.cyberciti.biz" | boxes -d dog

输出示例 :

![Unix / Linux: Boxes Command To Draw Various Designs](http://s0.cyberciti.org/uploads/l/tips/2012/06/unix-linux-boxes-draw-dog-design.png)

Fig.01: Unix / Linux: Boxes 命令来画出各式各样的设计 

#### 怎么样输出所有的设计 ####

语法如下:

    boxes option
    pipe | boxes options
    echo "text" | boxes -d foo
    boxes -l
 
设计 -d 选项设置要使用的设计的名字 . 语法如下:


    echo "Text" | boxes -d design
    pipe | boxes -d desig

-l 选项列出所有设计 . 它显示在配置文件中的所有的box设计图，同时也显示关于其创作者的信息。
 

    boxes -l
    boxes -l | more
    boxes -l | less

输出示例:		

    43 Available Styles in "/etc/boxes/boxes-config":
    -------------------------------------------------
    ada-box (Neil Bird ):
        ---------------
        --           --
        --           --
        ---------------
    ada-cmt (Neil Bird ):
        --
        -- regular Ada
        -- comments
        --
    boy (Joan G. Stark ):
                        .-"""-.
                       / .===. \
                       \/ 6 6 \/
                       ( \___/ )
          _________ooo__\_____/______________
         /                                   \
        |   joan stark   spunk1111@juno.com   |
        |     VISIT MY ASCII ART GALLERY:     |
        | http://www.geocities.com/SoHo/7373/ |
         \_______________________ooo_________/  jgs
                        |  |  |
                        |_ | _|
                        |  |  |
                        |__|__|
                        /-'Y'-\
                       (__/ \__)
    ....
    ...
    output truncated
    ..

### 在使用vi/vim文本编辑器时如何通过boxes过滤文本? ###

你可以使用vi或vim支持的任何附加命令，在这个例子中, [insert current date and time][4], 输入:

    !!date

或者

    :r !date
你需要在vim中输入以上命令来读取数据命令的输出，这将在当前行后面加入日期和时分秒:

    Tue Jun 12 00:05:38 IST 2012

你可以用boxes命令做到同样的. 创建一个作为样本的shell脚本或者如下的一个c程序:


    #!/bin/bash
    Purpose: Backup mysql database to remote server.
    Author: Vivek Gite
    Last updated on: Tue Jun, 12 2012

现在输入如下 (将光标移到第二行，也就是以"Purpose: ..."开头的行)

    3!!boxes

瞧，你就会看到如下的输出 :

    #!/bin/bash
    /****************************************************/
    /* Purpose: Backup mysql database to remote server. */
    /* Author: Vivek Gite           */
    /* Last updated on: Tue Jun, 12 2012                */
    /****************************************************/
这个短片将会给你介绍boxes命令:

注：youtube 视频
<iframe width="595" height="446" frameborder="0" src="http://www.youtube.com/embed/glzXjNvrYOc?rel=0"></iframe>

(Video:01: boxes command in action. BTW, this is my first video so go easy on me and let me know what you think.)

另见

- boxes man 手册

--------------------------------------------------------------------------------

via: http://www.cyberciti.biz/tips/unix-linux-draw-any-kind-of-boxes-around-text-editor.html

作者：Vivek Gite 
译者：[zky001](https://github.com/zky001)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[1]:http://www.cyberciti.biz/tips/linux-debian-package-management-cheat-sheet.html
[2]:http://www.cyberciti.biz/faq/rhel-centos-fedora-linux-yum-command-howto/
[3]:http://www.cyberciti.biz/faq/fedora-sl-centos-redhat6-enable-epel-repo/
[4]:http://www.cyberciti.biz/faq/vim-inserting-current-date-time-under-linux-unix-osx/
