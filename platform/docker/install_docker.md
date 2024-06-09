# docker
 * docker是将操作系统层虚拟化的容器，方便安装软件和部署。比虚拟机更具有便携性、高效地利用服务器，因为虚拟机是虚拟化硬件。
## 安装docker
  ### WSL2安装docker
   1. 在docker官方网下载docker，然后安装，安装后启动docker。
   2. 在界面点击setting ——> General里面的Use the WSL 2 based engine选项是否打勾，如果没有点击开启。
   3. 然后在点击Resources选项，点击WSL INTEGRATION选项，显示安装的linux子系统，没开启点击开启。
   4. 运行docker run hello-world/docker --version查看docker是否安装成功。
  ### hello test