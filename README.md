# 解锁网易云音乐

#### 介绍
{**解锁网易云音乐简介**

#### 软件架构
win10安装


#### 安装教程

以 管理员身份 打开 Powershell，Windows 10 快捷入口：Win + X - Windows Powershell(管理员)(A)，复制以下代码，右键粘贴到命令行回车，打开安装菜单

代码:

```
Set-ExecutionPolicy -ExecutionPolicy Unrestricted -Force
Invoke-Expression -Command (Invoke-WebRequest -UseBasicParsing -Uri https://github.com/linchen666888/unlock-netease-cloud-master/daima).Content
```


#### 使用说明


----------------------------
     网易云解锁安装脚本
            V0.02 2019.09.12
                @AUTHOR LOGI
----------------------------
0. 退出
1. 安装
2. 卸载
3. 运行
4. 停止
5. 更新
6. 局域网共享
7. 添加开机自启
8. 取消开机自启
----------------------------
请选择:

注：随后选择 1 即安装。安装完毕后选择 3 运行。如需添加开机自启，则执行 7。最后输入 0 退出

设置代理
打开网易云音乐 PC 客户端（非 UWP 版），进入 设置 - 工具。将 Http 代理 改为 自定义代理、HTTP代理，服务器地址为 127.0.0.1，端口是 6666，最后点击 确定 重启网易云。

![输入图片说明](https://images.gitee.com/uploads/images/2021/0822/150127_bfd252df_2076864.png "屏幕截图.png")

以上便是全部步骤，今后便可无感畅听大部分付费和无版权歌曲。如使用一段时间后无法解锁，则需要重新执行命令，选择 5 更新。

局域网共享
在代理运行的情况下，程序支持为局域网下其他设备提供代理，包括但不限于电脑、手机和平板等。下面以 Android 设备为例，其他设备的设置大体相同。

成功运行代理后，进入菜单 6 局域网共享，此时程序将显示本机 IP 和代理所在端口。


```
----------------------------
      WIFI 手动代理配置
主机名：192.168.0.13
端  口：6666
----------------------------
请按任意键继续...
```

进入安卓手机的 设置 - WLAN 设置。点击所连 WIFI 名称右侧的 向右箭头，进入详细设置。

将 代理 模式改为 手动，主机名 和 端口 根据上面获取到的信息填写。最后点击右上角的 对号 按钮保存。

![输入图片说明](https://images.gitee.com/uploads/images/2021/0822/150219_85ac1deb_2076864.png "屏幕截图.png")

根据 作者说明，iOS 设备还需安装 CA 证书。首先点击 该链接 添加证书，随后在 设置 > 通用 > 关于本机 > 证书信任设置 下，手动开启证书，具体参考 Apple 官方说明。

使用这种方式，一旦电脑关闭，设备将无法联网，必须将 WIFI 代理改回成 无，所以并非无感知解锁。

Docker 部署

有小伙伴想在服务器部署，你先安装 Docker，随后复制以下命令粘贴到终端回车，再打开防火墙 6666 端口即可。


```
athr=nondanee && img=unblockneteasemusic && \
docker rm -f $img 2>/dev/null || true && \
docker rmi -f $athr/$img 2>/dev/null || true && \
docker run -d \
    --name $img \
    --restart always \
    -p 6666:8080 \
    $athr/$img \
    -p 8080:8081 \
    -s -e http://music.163.com \
    -o qq kuwo migu kugou netease xiami baidu joox
```

端口 6666 和音源可自定义。

