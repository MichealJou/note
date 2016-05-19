以下是网络中收集，写的很好：
1 首先清理openjdk，如果没有直接忽略
sudo apt-get purge openjdk*
2 如果以前装过或者安装有问题，先清理掉现有jdk，如果没有也可以忽略
sudo rm /var/lib/dpkg/info/oracle-java7-installer*
sudo apt-get purge oracle-java7-installer*
sudo rm /etc/apt/sources.list.d/*java*
sudo apt-get update
3 安装jdk7
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java7-installer
备注：当然其他版本类似，如：
sudo apt-get install oracle-java6-installer
Oracle JDK 7(较新的稳定版本)
sudo apt-get install oracle-java7-installer
Oracle JDK 8(最新预览版本)
sudo apt-get install oracle-java8-installer
如果有两个版本可以设置使用哪一个：
sudo update-alternatives –config java
