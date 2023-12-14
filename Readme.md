# 大数据第一周
## 1.markdown文件编辑方法
使用vscode编辑markdown文件，首先建立一个目录，在目录上使用右键菜单“用code打开”，在vscode左边的资源管理中新建一个文件，例如：1.md。
安装三个扩展：

* Markdown All in One; 

* Markdown Preview Enhanced;

* Markdown Image；

插图联系：剪切一个图片到剪贴板，在要粘贴图片的地方点击右键，选择粘贴图片
![image-20230914114323165](.\images\image-20230914114323165.png)

## 2.安装linux
使用VirtualBox安装ubuntu22.04，Desktop版本。
安装前，硬盘空白空间要>20G
### 1）安装前配置
右键以管理员身份运行打开VirtualBox。点击新建：

填入相应内容，点击下一步：
内存调整到8G，点击下一步：
虚拟盘大小建议大于60G，点击创建后设置完成。
检查设置：
* 系统：cpu核心数，可以选物理核心数的一半；内存>4G。

* 观察网络形式，尽量不修改。

* 加载安装映像：

  ![image-20230914123256995](.\images\image-20230914123256995.png)

### 2）安装
点击“启动”，界面上选择“Install Ubuntu”, 到如下界面需要处理：

![image-20230914115043023](.\images\image-20230914115043023.png)

去掉安装时更新选项，一直继续到选时区，选择上海

![image-20230914115400543](.\images\image-20230914115400543.png)

在以下界面中填入相应内容。

![image-20230914115512036](.\images\image-20230914115512036.png)

点击“重启”

![817358e4a6f21d2d4cc13638f38c804](C:\Users\Administrator\AppData\Local\Temp\WeChat Files\817358e4a6f21d2d4cc13638f38c804.png)

直接回车键重启，如果启动有问题，可以强制推出，然后退出安装映像，再启动。

![image-20230914120127570](.\images\image-20230914120127570.png)

![image-20230914120209940](.\images\image-20230914120209940.png)

### 3）安装后配置和常用软件安装

#### （1）安装增强功能（物理机下没有）

增强功能解决问题：与host之间的显示匹配、文件共享、剪贴板共享。
从菜单设备->安装增强功能
![1694671276738](images\1694671276738.png)

双击打开光盘：

![1694671222650](.\images\1694671222650.png)

按惯例分析，应该是运行autorun.sh.在当前界面上点击右键，点击“Open in Terminal”:
![1694671453425](.\images\1694671453425.png)

输入后回车执行：./autorun.sh
安装完成后重启，设置显示和粘贴板。

#### （2）安装软件

安装好linux后需要重新选择镜像源，为了下载速度快。设置方法：

点击左下角9个点，找到Software & Updates,将软件源改成国内的镜像。

同步软件源：sudo apt-get update

更新软件：sudo apt-get upgrade

两种方法：使用库安装，下载软件安装

（1）库安装

安装openssh-server软件：sudo apt-get install openssh-server

安装vim编辑器：sudo apt-get install vim

（2）下载安装

如果库里没有这个软件，或者库里的版本不对，需要下载安装，以安装chorm浏览器为例，下载

对应的chorm安装包，一般是.deb类型

安装有多种方式，建议用apt install安装,安装时要求全路径：

在软件所在目录下执行：

sudo apt-get install ./google-chrome-stable_current_amd64.deb

#### （3）配置汉字输入法

设置->Region & Language->Manage Installed Language

显示需要安装时，允许安装，重启虚拟机。

设置->Keyboard->右侧界面+->选Chineses->选一个自己喜欢的输入法，重启虚拟机。

在右上角可以看到汉语输入法的选项。

## 3.linux使用入门

### 1）ls:列表显示当前目录下的目录和文件。

不带参数的情况下，显示常规属性的文件和目录

显示所有文件，带参数-a;

显示详细内容，带参数-l,或者直接用ll

### 2）cd:切换目录

快捷操作：cd：回到家目录；根：/；当前目录：.；上一级目录：..;切换到最新的历史路径：cd -;当前用户家目录：~。

### 3）linux目录结构

![image-20230921120300575](.\images\image-20230921120300575.png)

linux的图形界面一般只能访问当前用户的家目录内容。

mount 挂载，指可切除设备（一般热插拔设备）连接到系统

### 4）pwd：显示当前路径

### 5）创建文件：touch

### 6）创建目录：mkdir

可以相对路径（从当前路径开始的），也可以绝对路径（从/开始的）

### 7）显示文件内容：cat, more, less

cat：显示所有文件内容

more：分页显示，但是只能前进

less：分页显示，可以前进后退

### 8）创建新用户

用图形界面或者命令行（adduser或useradd）都可以。

可以创建新用户的前提是：当前用户拥有sudo权限。

### 9）切换用户

前提是：当前用户拥有sudo权限；或者另外一个用户的权限。

命令：su 用户名

### 10）vim的使用

vim有三种模式：命令、编辑、底行命令（或者说冒号命令）

进入操作界面是命令模式，按i等进入编辑模式，按Esc键进入命令模式，在命令模式下按冒号键进入底行命令模式。

课堂练习：新建一个用户（有sudo权限），切换到此用户，在此用户家目录下创建并填入

一个有100行数据的文件，用cat显示文件内容,再创建一个目录，将此文件移动到此目录下。mv cp

# 大数据第三周

## 1.Ubuntu网络配置

虚拟机注册后，启动前，打开设置，找到网络：

![image-20230928102906146](.\images\image-20230928102906146.png)

如果是下载的虚拟机，第一次启动前一定要随机化MAC地址。网络类型改成桥接网卡。

启动虚拟机后，设置ip地址：点击右上角网络图标

![image-20231214102558486](images\image-20231214102558486.png)

![image-20231214101807610](images\image-20231214101807610.png)

修改后，查看网络图标，如果正常，打开一个终端，合适ip地址，输入命令：ip a

查看host与虚拟机之间的网络连通情况：

从host连虚拟机：cmd下：ping  虚拟机ip

从虚拟机连host：在终端下：ping host-ip

## 2.软件版本选择

spark,hadoop,scale,java

软件依赖关系：spark依赖java，spark应用程序在hadoop集群上运行，hadoop依赖java，spark使用scala语音。

* spark依赖：java、hadoop、scala
* hadoop依赖：java
* scala依赖：java

所以版本选择顺序：spark、hadoop、scala、java

###  1）选择spark版本

从https://spark.apache.org查看。从download里查看版本，spark、hadoop、scala

的版本关系，从https://hadoop.apache.org里可以看到hadoop和java之间的依赖关系。

![image-20231214102343499](images\image-20231214102343499.png)

选择结果：spark3.3以上版本，hadoop都是3.3以上版本，scala是2.12，java是java8

## 3.hadoop下载安装

### 1）从官方网站或课程ftp下载。

需要从ubuntu下下载：打开文件管理器，左侧点击+Other Location，页面底部出现url输入框，输入完整的URL后，点击右侧的Connect。

下载后，解压缩：有两种方法：双击（有时候不行），用命令：

tar -zxvf hadoop-3.3.6.tar.gz

### 2）基本概念

集群内不可以有安全策略。ubuntu的安全策略有两个：防火墙、SElinux，但是默认都是关闭的。

集群的模式：

Local（StandAlone）：本地模式（单机）

Pseudo-Distributed Mode：伪集群（单机），用java线程模拟

Fully-Distributes Mode：集群（多机）

### 3）需要安装的软件

java8，ssh

#### （1）java

安装到本用户下，即权限是本用户。

下载，解压缩：

tar -zxvf jdk-8u351-linux-x64.tar.gz

测试软件可用性：运行java

![1696644835874](.\images\1696644835874.png)

配置路径，路径配置在本用户下：将路径添加到本用户的环境变量PATH里。编辑。bashrc，添加如下内容：

```shell
export JAVA_HOME=/home/bigdatadevelop/software/jdk18
export PATH=$JAVA_HOME/bin:$PATH
```

![image-20231007104743526](.\images\image-20231007104743526.png)

#### （2）ssh

```shell
sudo apt-get install ssh
sudo apt-get install pdsh
```

### 4）下载配置hadoop

####  （1）local模式配置

(A)配置文件 

hadoop软件包下的etc/hadoop/hadoop-env.sh中，配置JAVA_HOME。

![image-20231007114903334](.\images\image-20231007114903334.png)

### 5）测试hadoop命令

在hadoop软件包根目录下，执行bin/gadoop

![image-20231007115156673](.\images\image-20231007115156673.png)

### 6）配置hadoop路径

要配置hadoop根路径和hadoop可执行文件路径到PATH。

```shell
export HADOOP_HOME=/home/bigdatadevelop/software/hadoop-3.3.6
export PATH=$HADOOP_HOME/bin:$PATH
```

新打开一个终端：

![image-20231007120224736](.\images\image-20231007120224736.png)

### 7）local模式运行系统实例

手册上的例子：

```shell
$ mkdir input
$ cp etc/hadoop/*.xml input
$ bin/hadoop jar share/hadoop/mapreduce/hadoop-mapreduce-examples-3.3.6.jar grep input output 'dfs[a-z.]+'
$ cat output/*
```

为了避免在hadoop软件包里写入内容，将路径进行修改：

在家目录下，新建了hadoopExample目录，用于保存程序运行数据。这样相关路径需要进行修改:

```shell
mkdir hadoopExample
cd hadoopExample/
mkdir input
cp $HADOOP_HOME/etc/hadoop/*.xml input
cd ..
hadoop jar $HADOOP_HOME/share/hadoop/mapreduce/hadoop-mapreduce-examples-3.3.6.jar grep input output 'dfs[a-z.]+'
```

## 4. hadoop集群配置

### 1）几个概念：

不作高可用的情况下。

namenode：主节点，master，一台机器

datanode：数据节点，worker，其他机器

# 大数据第五周

##  1.集群配置准备

### 1）用户名要相同

### 2）写域名解析文件

所有节点名字不同，修改虚拟机名字方法：修改etc/hostname

要求用固定ip

写域名解析文件etc/hosts

写法是：

![image-20231012104135221](.\images\image-20231012104135221.png)

验证域名文件：

ping 域名

### 3）时间同步

ubuntu默认是网络时间同步，节点如果可以连接广域网，时间是同步的。全局域网一定要作：

选若干个节点作为时间服务器，其他节点与其同步，用ntp工具。

### 4）ssh免密设置

任何一个节点都要做，步骤：生成密钥对，传递公钥到所有节点，包括自己。

如果没有其他的免密，建议先删除.ssh文件

生成密钥对命令：ssh-keygen -t rsa 

回车到最后。

![image-20231012111423061](.\images\image-20231012111423061.png)

传递公钥：ssh-copy-id 节点名

![image-20231012111438416](.\images\image-20231012111438416.png)

验证：ssh 节点名，不需要密码，要对所有的节点验证，包括自身。

## 2.集群配置

只读文件：core-default.xml, hdfs-default.xml, yarn-default.xml and mapred-default.xml.

如果不在配置文件中写对应的配置，则只按照只读文件的配置执行

需要配置的文件：etc/hadoop/core-site.xml, etc/hadoop/hdfs-site.xml, etc/hadoop/yarn-site.xml 

and etc/hadoop/mapred-site.xml, etc/hadoop/hadoop-env.sh, etc/hadoop/yarn-env.sh。

### 1）hadoop-env.sh

增加两个环境变量HADOOP_PID_DIR，HADOOP_LOG_DIR，需要建立两个文件夹，将这两个环境变量指向文件夹。

```shell
export JAVA_HOME=/home/bigdata3/software/jdk18
export HADOOP_PID_DIR=/home/bigdata3/hadoopData/HADOOP_PID_DIR
export HADOOP_LOG_DIR=/home/bigdata3/hadoopData/HADOOP_LOG_DIR
```

###  2）core-site.xml

```xml
<property>
  <name>fs.defaultFS</name>
  <value>hdfs://xu123:9000/</value>
</property>

<property>
  <name>io.file.buffer.size</name>
  <value>131072</value>
</property>
```
在以下内容中有新设置。

### 3）hdfs-site.xml

dfs.namenode.name.dir和dfs.datanode.data.dir的默认设置如下：

```xml
<property>
  <name>dfs.namenode.name.dir</name>
  <value>file://${hadoop.tmp.dir}/dfs/name</value>
  <description>Determines where on the local filesystem the DFS name node
        should store the name table(fsimage).  If this is a comma-delimited list
        of directories then the name table is replicated in all of the
        directories, for redundancy. 
  </description>
</property>

<property>
  <name>dfs.datanode.data.dir</name>
  <value>file://${hadoop.tmp.dir}/dfs/data</value>
  <description>Determines where on the local filesystem an DFS data node
   	    should store its blocks.  If this is a comma-delimited
        list of directories, then data will be stored in all named
        directories, typically on different devices. The directories should be tagged
        with corresponding storage types ([SSD]/[DISK]/[ARCHIVE]/[RAM_DISK]) for HDFS
        storage policies. The default storage type will be DISK if the directory does
        not have a storage type tagged explicitly. Directories that do not exist will
        be created if local filesystem permission allows.
  </description>
</property>
```

都指向了变量：hadoop.tmp.dir，搜索此变量设置位置：

默认值在core-default.xml中是：

```xml
<property>
  <name>hadoop.tmp.dir</name>
  <value>/tmp/hadoop-${user.name}</value>
  <description>A base for other temporary directories.</description>
</property>
```

在core-site.xml中修改hadoop.tmp.dir的值

```xml
<property>
  <name>hadoop.tmp.dir</name>
  <value>/home/bigdata3/hadoopData</value>
  <description>A base for other temporary directories.</description>
</property>
```

dfs.blocksize的默认设置：128MB；dfs.namenode.handler.count的默认值是10，对于我们做实验都足够了，所以不修改。

hdfs-site.xml当前没有修改。

### 4）yarn-site.xml

yarn.resourcemanager.address如果设置，将覆盖变量yarn.resourcemanager.hostname的值，查看yarn.resourcemanager.hostname变量定义：

```xml
<property>
    <description>The hostname of the RM.</description>
    <name>yarn.resourcemanager.hostname</name>
    <value>0.0.0.0</value>
 </property>    
```

ip地址0.0.0.0，表示按照当前主机的IP地址。

当前不修改，类似配置都不修改。

当前此文件没有修改。

### 5）mapred-site.xml

mapreduce.framework.name默认是local模式，需要修改：

```xml
<property>
	<name>mapreduce.framework.name</name>
	<value>yarn</value>
	<description>The runtime framework for executing MapReduce jobs.
		Can be one of local, classic or yarn.
	</description>
</property>
```

mapreduce.jobhistory.intermediate-done-dir的默认值是：

```xml
<property>
  <name>mapreduce.jobhistory.intermediate-done-dir</name>
  <value>${yarn.app.mapreduce.am.staging-dir}/history/done_intermediate</value>
  <description></description>
</property>
```

指向变量yarn.app.mapreduce.am.staging-dir，设置的值是：

```xml
<property>
  <name>yarn.app.mapreduce.am.staging-dir</name>
  <value>/tmp/hadoop-yarn/staging</value>
  <description>The staging dir used while submitting jobs.
  </description>
</property>
```

将其指向自己设定的目录：/home/bigdata3/hadoopData/staging

### 6）workers

将datanode节点写入此文件，一行一个

workers:

##  3.集群启动

### 1）namenode格式化

namenode格式化在namenode节点上进行，初始化hdfs文件系统，格式化的效果是可以在namenode上看到我们设置的目录建立起来。集群第一次启动时，会在所有节点上建立hdfs文件系统，效果是可以在所有节点上看到数据目录建立起来。

namnode格式化第一次启动集群后，不能再次进行格式化，否则会进入数据保护模式（安全模式）。

如果进行第二次格式化，需要删除所有节点上的数据目录。

命令：

hdfs namenode -format

![image-20231026123615038](.\images\image-20231026123615038.png)

### 2）启动集群

可以用自动化脚本启动start-all.sh，不能安装pdsh（卸载：sudo apt remove pdsh）。

停止的脚本是stop-all.sh。

用jps检测：

![image-20231026123055497](.\images\image-20231026123055497.png)

web页面检测：

![image-20231026125644335](.\images\image-20231026125644335.png)

## 4.hdfs命令

命令帮助，命令行输入hadoop fs。

### 1）远程集群使用

两种用法：

（1）修改配置文件：fs.defaultFS；

​	有两种方法：

* a.直接修改core-site.xml	

![image-20231102103919784](.\images\image-20231102103919784.png)

* b.修改hosts中master对应的ip地址。

​	修改后，hdfs的远程使用与本地使用是相同的。

（2）在命令中，直接写入hdfs的位置。

### 2）-mkdir

命令格式：

haddop fs -mkdir hdfs的URI/路径

如果hdfs的URI与配置文件相同，可以省略。

例如：

hadoop fs -mkdir hdfs://172.21.2.6:9000/210110900628

### 3）-ls

文件系统列表显示。

命令格式：

haddop fs -ls hdfs的URI/路径

例如：

hadoop fs -ls hdfs://172.21.2.6:9000/210110900628

### 4）-put -copyFromLocal

从本地文件系统拷贝文件到hdfs：

命令格式：

hadoop fs -put hdfs的URI/路径/文件名

同名可以省略文件名

![image-20231026122452068](.\images\image-20231026122452068.png)

### 5）-get -copyToLocal

从hdfs拷贝文件到本地。

命令格式：

hadoop fs -get hdfs的URI/路径/文件名 本地路径/文件名

同名可以省略文件名。

例如：

hadoop fs -get hdfs://172.21.2.6:9000/210110900628/a.txt ~/b.txt

### 6）-cat

显示hdfs文件内容。

hadoop fs -cat hdfs的URI/路径/文件名

### 7）-appendToFile

向hdfs文件增加内容。

节点数调整?

### 8）-cp

在hdfs中进行文件或目录拷贝。

### 9）-moveFromLocal, -moveToLocal, -mv

文件移动。

### 10）-rm

删除文件和目录。

删除文件：

hadoop fs -rm /b.txt

删除目录：

hadoop fs -rm -r /012345678

### 11）-rmdir

删除目录（要求是空目录）。

hadoop fs -rmdir /012345678

![image-20231102114423925](.\images\image-20231102114423925.png)

### 12）-touch

创建一个文件。

## 5.hdfs文件对应本地文件

从web页面上查看文件存储位置和Block ID：

![image-20231102114120424](.\images\image-20231102114120424.png)

进入相应节点，找到对应的Block ID文件：

![image-20231102115535534](.\images\image-20231102115535534.png)

## 6.scala语言入门

下载scala2.12版本，解压缩，配置环境变量PATH。

解压缩：

tar -zxvf scala-2.12.15.tgz 

验证：进入bin目录，执行./scala

![image-20231102111325812](.\images\image-20231102111325812.png)

配置环境变量：

```shell
export SCALA_HOME=/home/bigdata3/software/scala-2.12.15
export PATH=$SCALA_HOME/bin:$PATH
```

![image-20231102111745945](.\images\image-20231102111745945.png)

## 7.spark编程

# 大数据第九周

## 1.scala语言环境

### 1）scala基本语言环境

### 2）通过spark启动scala语言环境

下载，解压缩：

```shell
tar -zxvf spark-3.5.0-bin-hadoop3.tgz
```

![image-20231109101804102](images\image-20231109101804102.png)

测试：在bin目录下执行：

```shell
./spark-shell
```

![image-20231109102920488](images\image-20231109102920488.png)

如果/etc/hosts中的master的域名不是自己，可能无法启动，所以需要将master的域名解析注释掉。

添加环境变量SPARK_HOME,将spark-shell命令路径添加到PATH。

编辑.bashrc，添加：

```shell
export SPARK_HOME=/home/bigdata3/software/spark-3.5.0
export PATH=$SPARK_HOME/bin:$PATH
```

![image-20231109104842101](images\image-20231109104842101.png)

### 3）集成开发环境

下载，解压缩：tar -zxvf ideaIC-2023.2.4.tar.gz

为了方便使用，添加idea.sh到PATH。

第一次启动idea：

```shell
export PATH=/home/bigdata3/software/idea-IC-232.10203.10/bin:$PATH
```

![image-20231109121631811](images\image-20231109121631811.png)

![image-20231109121203727](images\image-20231109121203727.png)

点击New Project：

![image-20231109121524675](images\image-20231109121524675.png)

安装scala插件：

![image-20231109121900692](images\image-20231109121900692.png)

安装完毕后，重启IDE，重启后，选择New Project：

输入project的Name，选择scala语言，Build System选择IntellJ，检查jdk版本是否与我们当前使用的相符。Scala SDK，点击Create，一

般情况下会找到我们配置SCALA_HOME的scala版本。

![image-20231111161321528](images\image-20231111161321528.png)

## 2.scala语言

### 1）变量声明

* 变量声明必须指明var、val，var：可变，val：不可变。

* 声明时可以不指定数据类型，系统会自动判断，但需要注意是否符合要求，因为自动判断一般只有三种：

  （1）字面无小数点的数字：Int

  （2）字面有小数点的数字：Double

  （3）字符串

* 如果指定数据类型：变量名后用":"，然后写数据类型；或者用数字后的类型标识。
  
### 2）基本数据类型

String类型是通过默认导入Java.lang包实现的，其他的是scala的相应包。

![Alt text](images/1699505903964.png)

### 3）算术运算符
与其他语言雷同，与Java相同
### 4）关系运算符
与其他语言雷同，与Java相同
### 5）逻辑运算符

![Alt text](images/1699506018933.png)

### 6）位运算符
运算结果是数字，运算过程是对两个数字的对应二进制位进行逻辑操作，得到结果的对应二进制位的值。
运算符三种：与&、或|、异或^

![Alt text](images/1699506116764.jpg)

![Alt text](images/1699506175155.png)

### 7）赋值运算符

+=、-=

![Alt text](images/1699506230151.png)

### 8）返回值
语句快的最后执行的那一条语句的值，就是返回值。
语句块的划分：逻辑分隔，{}
例如：
val a={val c=2;val d=3;c+d}
结果a的值是5。

![Alt text](images/1699501794831.png)

### 9）条件语句
两种写法：
（1）写在不同行：

```scala
int b；
if(a<0) b=0；
else b=100；
```

```scala
val b={if(a<0) 0 else 100}
```

（2）写在同一行：

守卫用法：在其他结构里嵌入if语句的应用方式

### 10）for

#### （1）for的写法

for(变量<-集合){循环体}

注意：变量不可以用val或var。

Range表达方式：起点 to 终点 或者 起点 until 终点；区别是是否包括终点：until不包括。没有step，步进就是1。

例如：打印1到10整数

```java
object Main {
  def main(args: Array[String]): Unit = {
    val a = 5;
    for (i <- 1 to 10){
      println(i);
    }
  }
}
```

![image-20231116101535941](images\image-20231116101535941.png)

#### （2）for中使用守卫（if）

写法：

for(变量<-集合 if(布尔表达式)){循环体}

例如：打印1到10的偶数

```java
object Main {
  def main(args: Array[String]): Unit = {
    val a = 5;
    for (i <- 1 to 10 if (i % 2 == 1)) {
      println(i);
    }
  }
}
```

![image-20231116102533633](images\image-20231116102533633.png)

守卫中的if如果有多个条件，scala建议是直接写出，不写逻辑与，例如

```java
object Main {
  def main(args: Array[String]): Unit = {
    val a = 5;
    for (i <- 1 to 10 if (i % 2 == 1) if( i != 9)) {
      println(i);
    }
  }
}
```

#### （3）for的嵌套

写法：

for(最外层变量<-集合1；下一层变量<-集合2；···){循环体}

for的嵌套中使用守卫，例如：集合1：1 to 10;集合2：11 to 13;计算两个集合个元素的乘积，集合1中只要偶数，并且不要4，集合2不要13。

```java
object Main {
  def main(args: Array[String]): Unit = {
    for (i <- 1 to 10 if (i % 2 == 0) if (i != 4); j <- 11 to 13 if (j != 13)) {
      println(i * j)
    }
  }
}
```

scala建议，for嵌套时，先写嵌套for内容，然后写守卫。

例2：打印出100以内的素数

```java
object Main {
  def main(args: Array[String]): Unit = {
    for (i <- 2 to 100) {
      var flag = 1
      for (j <- 2 until i) {
        if (i%j==0){
          flag = 0
        }
      }
      if (flag == 1){
        println(i)
      }
    }
  }
}
```

![image-20231116110456277](images\image-20231116110456277.png)

循环语句中默认没有break和continue，如果一定要使用，需要手工导包。

### 11）while

与其他语言相同

### 12）do while

与其他语言相同

### 13）组合数据结构

#### （1）Array

默认是定长数组。如果一定要使用非定长数组，需要自己导包。

访与其他语言的不同之处：用圆括号。

访问使用索引。

#### （2）Map

类似Python的字典，但默认长度不可变。写法不同，用圆括号，key与value之间用"->"。

例如：val a=("a"->1,"b"->2)

#### （3）Tuple

与其他语言相同。但访问方式比较特殊，用"._序号"形式访问。

特别注意：序号从1开始。

例1：val a=("a","b","c",1,2,3)，访问元素2，a._5

#### （4）List

与Array类似，但List要求元素是相同数据类型。

#### （5）Set

集合：无顺序、元素不重复

## 3.函数

### 1）普通函数

主要定义方法：
#### （1）标准定义

def 函数名(参数列表)：返回值类型={函数体}

其中：参数列表写法：参数1：类型1，参数2：类型2，···；类型必须写。

返回值类型可以不写。

一般不用return，因为最后执行的那一句的值就是返回值。

例1：

```java
def add1(a1: Int, a2: Int): Int = {
    a1 + a2
}
println(add1(1, 2))
```

#### （2）匿名函数定义

(参数列表)=>{函数体}

### 2）高阶函数

参数或者返回值是函数的函数。

####  （1）参数是函数

参数是函数的优点：函数功能更灵活、维护方便、编程任务分配简单。

##### A 基本写法

def 函数名（形参列表）：返回值类型={函数体}

形参列表中有函数形参，函数形参的写法：

函数名：函数类型，其中函数类型写法：（形参类型列表）=>返回值类型。

调用：函数形参，直接写函数名

例1：

```java
object Main {
  def main(args: Array[String]): Unit = {
    def mul1(a1: Int, a2: Int): Int = {a1 * a2}
    def add1(a1: Int, a2: Int): Int = {a1 + a2}
    def minus1(a1: Int, a2: Int): Int = {a1 - a2}
    def div1(a1: Int, a2: Int): Int = {a1 / a2}
    def highFunc(f1: (Int, Int) => Int, a1: Int, a2: Int): Int = {f1(a1, a2)}
    print("*:");
    println(highFunc(mul1, 1, 2))
    print("+:");
    println(highFunc(add1, 1, 2))
    print("-:");
    println(highFunc(minus1, 1, 2))
    print("/:");
    println(highFunc(div1, 1, 2))
  }
}
```

![image-20231116130110164](images\image-20231116130110164.png)

##### B 形参有默认值

没有默认值的形参要写在形参表的前面。

例2：

```java
object Main {
  def main(args: Array[String]): Unit = {
    def mul1(a1: Int, a2: Int): Int = {a1 * a2}
    def add1(a1: Int, a2: Int): Int = {a1 + a2}
    def minus1(a1: Int, a2: Int): Int = {a1 - a2}
    def div1(a1: Int, a2: Int): Int = {a1 / a2}
    def highFunc(f1: (Int, Int) => Int, a1: Int=1, a2: Int=2): Int = {f1(a1, a2)}
    print("*: "); println(highFunc(mul1))
    print("+: "); println(highFunc(add1))
    print("-: "); println(highFunc(minus1))
    print("/: "); println(highFunc(div1))
  }
}
```

例3：

```java
object Main {
  def main(args: Array[String]): Unit = {
    def mul1(a1: Int, a2: Int): Int = {a1 * a2}
    def add1(a1: Int, a2: Int): Int = {a1 + a2}
    def minus1(a1: Int, a2: Int): Int = {a1 - a2}
    def div1(a1: Int, a2: Int): Int = {a1 / a2}
    def highFunc(f1: (Int, Int) => Int=add1, a1: Int=1, a2: Int=2): Int = {f1(a1, a2)}
    print("*: "); println(highFunc(mul1))
    print("+: "); println(highFunc())
    print("-: "); println(highFunc(minus1))
    print("/: "); println(highFunc(div1))
  }
}
```

##### C 调用时不按顺序传参

带形参名传参，即形参赋值方式。

例4：

```java
object Main {
  def main(args: Array[String]): Unit = {
    def mul1(a1: Int, a2: Int): Int = {a1 * a2}
    def add1(a1: Int, a2: Int): Int = {a1 + a2}
    def minus1(a1: Int, a2: Int): Int = {a1 - a2}
    def div1(a1: Int, a2: Int): Int = {a1 / a2}
    def highFunc(f1: (Int, Int) => Int=add1, a1: Int=1, a2: Int=2): Int = {f1(a1, a2)}
    print("*: "); println(highFunc(mul1))
    print("+: "); println(highFunc(a2=9))
    print("-: "); println(highFunc(minus1))
    print("/: "); println(highFunc(div1))
  }
}
```

##### D 函数调用时传匿名函数

当作为参数的函数只用一次，并且写法比较简单的情况下，可以使用匿名函数。

例5：

```java
object Main {
  def main(args: Array[String]): Unit = {
    def highFunc(f1: (Int, Int) => Int, a1: Int=1, a2: Int=2): Int = {f1(a1, a2)}
    print("*: "); println(highFunc((a1: Int, a2: Int) => {a1 * a2}))
    print("+: "); println(highFunc((a1: Int, a2: Int) => {a1 + a2}))
    print("-: "); println(highFunc((a1: Int, a2: Int) => {a1 - a2}))
    print("/: "); println(highFunc((a1: Int, a2: Int) => {a1 / a2}))
  }
}
```

![image-20231123103936202](images\image-20231123103936202.png)

练习：基础函数是def highFunc(f2:(Int,Int)=>Int,a1:Int=1,a2:Int=2)={f2(a1,a2)},计算a*b/(a+b),a=5,b=8

```java
object Main {
  def main(args: Array[String]): Unit = {
    def highFunc(f1: (Int, Int) => Int, a1: Int = 1, a2: Int = 2): Int = {f1(a1, a2)}
    println(highFunc((a1: Int, a2: Int) => {a1 * a2 / (a1 + a2)},5,8))
  }
}
```

##### E 函数调用时传使用下划线的匿名函数

匿名函数中下划线的使用前提：使用下划线不会影响参数判断，下划线所代表的参数在函数体中只使用一次。

例如函数：（a1:Int,a2:Int）=> {a1*a2} 可以写成:

```java
_*_
```

下划线与声明时的形参按位置对应。

例：四则运算程序可以变形为：

```java
object Main {
  def main(args: Array[String]): Unit = {
    def highFunc(f2:(Int, Int) => Int ,a1:Int=1,a2:Int=2)={
      f2(a1,a2)
    }
    print("*: ");println(highFunc(_*_,2,3))
    print("+: ");println(highFunc(_+_,2,3))
    print("-: ");println(highFunc(_-_,2,3))
    print("/: ");println(highFunc(_/_,2,3))
  }
}
```



#### （2）返回值是函数

例1：

```java
object Main {
  def main(args: Array[String]): Unit = {
    def highFunc(a1:Int=1)= {
      if (a1<0) (a1:Int,a2:Int)=>{a1*a2}
      else (a1:Int,a2:Int)=>{a1+a2}
    }
    val a = highFunc(6)
    val b = a(5,8)
    println(b)
    println(highFunc(-9)(5,8))
    //print("*: ");println(highFunc((x:Int,y:Int)=>{x*y/(x+y)},5,8))
  }
}
```

![image-20231123112318496](images\image-20231123112318496.png)

#### （3）scala的标识符

scala的标识符包括字母、数字、下划线。scala建议使用驼峰命名法：第一个单词全部小写，其后的单词首字母大写;下划线不建议放在首、尾位置。常量在java中一般是全大写，scala是第一个字母大写。

_在scala中的含义比较多，最多的用法是通配符（用在匿名函数）和范围标识。

匿名函数使用_，是在调用时使用，可以简化函数写法。

# Spark

## 1.绪论

### 1）RDD

弹性分布式数据集。是spark的基本数据集。

RDD的计算主要分为两种：转换计算、执行计算。

转换计算的计算结果还是RDD。

计算流程：输入->转换->转换->···->执行

执行操作结果一般不是RDD，所以执行操作一般是spark的最后一步。

spark的转换操作是惰性的，只有遇到执行操作，才按顺序执行转换操作。这样可以提高资源利用率。

### 2）DAG

有向无环图，是spark计算过程的描述。

### 3）Executor

运行在worker节点上的进程。负责task的运行。

### 4）Task

具体的任务计算。

### 5）Job

### 6）Stage

一组相互间没有shuffle依赖关系的task组成的集合，也称为TaskSet。

窄依赖：数据仅在本分区；

宽依赖：数据在不同分区有交换（shuffle）。

### 1）生成RDD

#### （1）用文件生成RDD

文本文件，用sc.textFile,例如

val RDD1 = sc.textFile("/home/bigdata3/a.txt")

![image-20231130104112001](images\image-20231130104112001.png)

DAG:

![image-20231130105038953](images\image-20231130105038953.png)

集群文件：

![image-20231130110502896](images\image-20231130110502896.png)

#### （2）用程序中的数据生成RDD

D对于数组，使用sc.parallelize(数组)

例如：

![image-20231130105452381](images\image-20231130105452381.png)

DAG:

![image-20231130105602498](images\image-20231130105602498.png)

### 2）输出

#### （1）print相关

print在本地模式:直接显示；集群模式：打印到log文件中。

练习：val RDD2 = sc.parallelize(Array1)，用println打印RDD2的所有元素。

![image-20231130110530288](images\image-20231130110530288.png)

#### （2）写入文件

saveAsTextFile(路径)

![image-20231130111837013](images\image-20231130111837013.png)

![image-20231130112026384](images\image-20231130112026384.png)

DAG：

![image-20231130111658951](images\image-20231130111658951.png)

### 3）常用转换操作

![Alt text](images\1701314745653.png)
![Alt text](images\1701314678339.png)
![Alt text](images\1701314770360.png)
![Alt text](images\1701314782479.png)

### 4）常用动作操作

![Alt text](images\1701314870604.png)
![Alt text](images/1701314879760.png)

###  5）spark集成开发环境建立

从菜单File->New->Project:

![image-20231130114129895](images\image-20231130114129895.png)

输入相关信息后，点击Create。

从菜单File->Project Structure:

![image-20231130114509705](images\image-20231130114509705.png)

左侧栏选择Global Liberaries,中间栏点击+，选择java，在跳出的界面中选择spark软件下的jars目录里的所有jar包：

![image-20231130114819240](images\image-20231130114819240.png)

点击ok，等待右下角indexing进度完成。

编写程序

```java
import org.apache.spark.{SparkConf, SparkContext}

object Main {
  def main(args: Array[String]): Unit = {
    val conf = new SparkConf().setAppName("firstSpark").setMaster("local[4]")
    val sc = new SparkContext(conf)
    val rdd1 = sc.textFile("/home/bigdata3/b.txt")
    rdd1.saveAsTextFile("/home/bigdata3/sparkOut/3")
    Thread.sleep(1000*60*5)
    sc.stop()
  }
}
```

执行：

![image-20231130122049706](images\image-20231130122049706.png)

DAG：

![image-20231130122132869](images\image-20231130122132869.png)

# 大数据第十三周

## 1.转换操作

![image-20231207113639807](images\image-20231207113639807.png)

rdd:Array[String] = Array(Good morning, Good, morning, Good afternoon, 1, 2, 3, 4, 5, 6, 6)

### 1）filter

用法：rdd.**filter**（*func*），func要求返回值是布尔值，如果是真，数据传递到新创建的数据集。

例1：数据集中字符串长度大于4的留下，其他抛弃

![image-20231207104430939](images\image-20231207104430939.png)

![image-20231207104331315](images\image-20231207104331315.png)

### 2）map

用法：rdd.**map**（*func*），将rdd中的每一个元素经过func处理，生成一个新的RDD。

例如：每个元素+1：

![image-20231207110108410](images\image-20231207110108410.png)

### 3）flatMap

用法：rdd.**flatMap**（*func*），可以把数据集中各元素之间的分隔去掉，之后的数据按func组合。

例1：按照空格分词：

![image-20231207110832667](images\image-20231207110832667.png)

练习：每个词后添加一个大写的END：

![image-20231207111135192](images\image-20231207111135192.png)

### 4）reduceByKey

用法：rdd.**reduceByKey**（*func*），在 （K， V） 对的数据集上调用时，返回 （K， V） 对的数据集，其中每个键的值使用给定的 reduce 函数 *func* 进行聚合。

例1：将每个词写成（词，1）：

![image-20231207112421832](images\image-20231207112421832.png)

例2：用redudeByKey统计单词：

![image-20231207113547740](images\image-20231207113547740.png)

## 2.行动操作

### 1）count

返回元素个数。

### 2）collect

将RDD转换为Array。

### 3）take(n)

取前n个。

### 4）first

第一个。

### 5）foreach(func)

将每个元素送到func处理。

## 3.wordCount链式写法

### 1）spark-shell

```java
sc.textFile("/home/bigdata3/b.txt").flatMap(_.split(" ")).map(x=>(x,1)).reduceByKey(_+_).collect
```

![image-20231207120301630](images\image-20231207120301630.png)

### 2）通用程序

```java
sc.textFile("/home/bigdata3/b.txt").flatMap(_.split(" ")).map(x=>(x,1)).reduceByKey(_+_).foreach(println)
```

![image-20231207120218468](images\image-20231207120218468.png)

## 4.集成开发环境

### 1）程序运行时不使用参数

```java
import org.apache.spark.{SparkConf, SparkContext}

object Main {
  def main(args: Array[String]): Unit = {
    val conf = new SparkConf().setAppName("firstSpark").setMaster("local[3]")
    val sc = new SparkContext(conf)
    val rdd1 = sc.textFile("/home/bigdata3/b.txt")
    sc.textFile("/home/bigdata3/b.txt")
      .flatMap(x=>x.split(" "))
      .map((_,1))
      .reduceByKey(_+_)
      .foreach(println)
    Thread.sleep(1000*60*5);
    sc.stop()
  }
}
```

窄依赖：数据仅在本分区；

宽依赖：数据在不同分区有交换（shuffle）。本程序中的reduceByKey。

程序的DAG：

![image-20231207123356952](images\image-20231207123356952.png)

针对DAG:

（1）为什么有两个stage？

因为reduceByKeyz执行过程中有shuffle操作。

stage按shuffle进行分割。

（2）分区有无变化？

![image-20231207123048663](images\image-20231207123048663.png)

stage0有两个tasks,就是说有两个分区：stage1有两个tasks,也是两个分区，所以分区无变化。

（3）job

如何让本程序变成两个job：添加一个action操作。

job数量一般对应action的数量。

```java
import org.apache.spark.{SparkConf, SparkContext}

object Main {
  def main(args: Array[String]): Unit = {
    val conf = new SparkConf().setAppName("firstSpark").setMaster("local[3]")
    val sc = new SparkContext(conf)
    val rdd1 = sc.textFile("/home/bigdata3/b.txt")
      .flatMap(x => x.split(" "))
      .map((_, 1))
      .reduceByKey(_ + _, 3)
    rdd1.foreach(println)
    rdd1.saveAsTextFile("/home/bigdata3/sparkOut/4")
    Thread.sleep(1000 * 60 * 5);
    sc.stop()
  }
}
```

Jobs:

![image-20231207124601523](images\image-20231207124601523.png)

Job0的DAG:

![image-20231207124731299](images\image-20231207124731299.png)

Jobs1的DAG：

![image-20231207124809379](images\image-20231207124809379.png)

虽然有两个stage，但stage2与stage0工作相同，是由stage0完成的。

## 5.数据平衡

### 1）分区

创建环境时用.setMaster("local[3]")指定了计算使用3个线程，后续如果不指定分区，分区数系统自动优化，数量<=3。

一般有shuffle的转换操作都有一个分区参数。创建RDD的方法也有分区参数。

创建RDD时：
![image-20231214105411012](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20231214105411012.png)
第二个参数是minPartitions，也是最少分区数。
程序：

```java
import org.apache.spark.{SparkConf, SparkContext}

object Main {
  def main(args: Array[String]): Unit = {
    val conf = new SparkConf().setAppName("firstSpark").setMaster("local[5]")
    val sc = new SparkContext(conf)
    sc.textFile("/home/bigdata3/wordTest",4)
      .saveAsTextFile("/home/bigdata3/sparkOut/7")
    sc.stop()
  }
}
```

查看分区数据：

![image-20231214104603428](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20231214104603428.png)

共有5个分区，但有两个分区数据量是0，说明分区数据及其不平衡，后续运算资源的使用就非常不合理。

观察wordCount完整程序的计算结果分区情况。

````java
import org.apache.spark.{SparkConf, SparkContext}

object Main {
  def main(args: Array[String]): Unit = {
    val conf = new SparkConf().setAppName("firstSpark").setMaster("local[5]")
    val sc = new SparkContext(conf)
    sc.textFile("/home/bigdata3/wordTest",4)
      .flatMap(x => x.split(" "))
      .map((_, 1))
      .reduceByKey(_ + _)
      .saveAsTextFile("/home/bigdata3/sparkOut/9")
    Thread.sleep(1000 * 60 * 5);
    sc.stop()
  }
}
````

DAG：

![image-20231214105241670](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20231214105241670.png)

观察输出数据文件：

![image-20231214105156664](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20231214105156664.png)

输出文件的数据平衡情况良好。

####  （2）repartition的数据平衡

##### A）repartition可以进行分区数的调整，同时会对分区数据进行随机的平衡

验证过程：

没有repartition：

```java
import org.apache.spark.{SparkConf, SparkContext}

object Main {
  def main(args: Array[String]): Unit = {
    val conf = new SparkConf().setAppName("firstSpark").setMaster("local[5]")
    val sc = new SparkContext(conf)
    sc.textFile("/home/bigdata3/wordTest",4)
      .flatMap(x => x.split(" "))
      .map((_, 1))
      .saveAsTextFile("/home/bigdata3/sparkOut/10")
    sc.stop()
  }
}
```

输出：

![image-20231214110600238](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20231214110600238.png)

加入repartition之后：

```java
import org.apache.spark.{SparkConf, SparkContext}

object Main {
  def main(args: Array[String]): Unit = {
    val conf = new SparkConf().setAppName("firstSpark").setMaster("local[5]")
    val sc = new SparkContext(conf)
    sc.textFile("/home/bigdata3/wordTest",4)
      .flatMap(x => x.split(" "))
      .map((_, 1))
      .repartition(4)
      .saveAsTextFile("/home/bigdata3/sparkOut/10")
    sc.stop()
  }
}
```

输出：

![image-20231214110712661](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20231214110712661.png)

结论：经过repartition后数据平衡状况非常好。

##### B）repartition使用位置

考虑两个因素：要在窄依赖计算的最前端使用；因为repartition需要通过网络传递数据，需要考虑网络传输数据的开销。

```java
sc.textFile("/home/bigdata3/wordTest",4)
      .flatMap(x => x.split(" "))
      .repartition(4)
      .saveAsTextFile("/home/bigdata3/sparkOut/13")
```

结果：

![image-20231214112711698](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20231214112711698.png)

结论：综合考虑，repartition应该放到flatMap后比较好。

##### C）考虑数据平衡和输出的wordCount程序

```java
import org.apache.spark.{SparkConf, SparkContext}

object Main {
  def main(args: Array[String]): Unit = {
    val conf = new SparkConf().setAppName("firstSpark").setMaster("local[5]")
    val sc = new SparkContext(conf)
    sc.textFile("/home/bigdata3/wordTest",4)
      .flatMap(x => x.split(" "))
      .repartition(4)
      .map((_, 1))
      .reduceByKey(_ + _, 1)
      .saveAsTextFile("/home/bigdata3/sparkOut/14")
    Thread.sleep(1000 * 60 * 5);
    sc.stop()
  }
}
```

