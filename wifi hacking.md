
# WIFI Hacking
### WIFI Hacking 1 附件提供的pcap中有多少可用AP:
在wireshark中打开pcap包，无线LAN统计

![1.png](http://upload-images.jianshu.io/upload_images/8086912-60eeeba5549634a7.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

其中一个SSID为\357\277\...经过转码得到名称，统计结果有：
* ChinaNet
* CMCC-WEB
* CMCC
* CMCC-EDU
* CUC
* and-Business
* 桃花岛训练专用WIFI
* A101E
* CUC-AC-001
* lczhap
* a101e-guest

### WIFI Hacking 2 附件中所有尝试连接过ssid为a101e-guest的无线客户端MAC地址:

将无线LAN统计表中'ssid=a101e-guest'作为过滤条件进行过滤，在主窗口查看MAC地址

![2.png](http://upload-images.jianshu.io/upload_images/8086912-bf26ef5af9eb96b3.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

或在无线LAN统计表中展开'ssid=a101e-guest'

![3.png](http://upload-images.jianshu.io/upload_images/8086912-91c401b3aa23243f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

得到结果：
* e2:08:bd:58:1e:3b
* 70:14:a6:39:f8:2f
* 00:1a:a9:c1:fc:35
* 56:75:f1:3c:4c;08
* 38:bc:1a:64:2c:08
* 6c:25:b9:1f:cb:94
* 78:9f:70:03:44:3a
* 64:9a:be:82:9f:c5
* 60:f8:1d:87:0e:19
* 08:70:45:dd:20:a0
* 34:23:ba:8b:97:b7

### WIFI Hacking 3 附件中无线客户端尝试连接过但抓包期间信号覆盖范围内不存在的AP的SSID集合:

选择一个Probe Request,将‘Type/Subtype:Probe Request(0x0004)’作为过滤条件，得到所有试图连接AP的SSID集合
![4.png](http://upload-images.jianshu.io/upload_images/8086912-d6ff4018ce10a2c3.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

包括：GGBWG-G,CUC,lczhap,Chu-Sushi,Apple Setup,sharkAP,CMCC-WEB

除去可用AP即为信号覆盖范围内不存在的AP的SSID集合,结果为：
* GGBWG-G
* Chu-Sushi
* Apple Setup
* sharkAP

### WIFI Hcking 4 附件中唯一的一个“乱入”的手机，这部手机没有连接上任何一个热点，但暴漏了它曾经连过很多热点:

在无线LAN中看到7c;1d:d9:df:a1:0b广播了多个请求但都未收到回复

![5.png](http://upload-images.jianshu.io/upload_images/8086912-f2b239b80aa9c166.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

将其MAC地址作为过滤条件，得到SSID


![6.png](http://upload-images.jianshu.io/upload_images/8086912-96a6477bdb03282a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

其中将SSID=\357\277\275\...解码：
先复制为Hex流

![7.png](http://upload-images.jianshu.io/upload_images/8086912-1347d5ec3420fb45.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

再将复制结果粘贴到hex2bin转码平台在线得到转码结果

![8.png](http://upload-images.jianshu.io/upload_images/8086912-ef87d31d60c2ce49.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

统计结果：
* KL4
* SQBG8701
* LieBaoWiFi744
* XUE
* Feixun_AFE4B3
* gg
* linan
* sxblz
* 神州专车
* sft4-1
* sxbl
* ganluyuan5

### WIFI Hacking 5 附件中哪些AP仅支持使用WPA2 CCMP/AES认证加密模式,这些热点的MAC地址集合:

在beacon frame的RSN字段中找gcs.type==4&&pcs.type==4两条作为过滤条件


![9.png](http://upload-images.jianshu.io/upload_images/8086912-cf97e31b40c7956a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

得到SSID:CMCC,CUC-AC-001,dj,48-A102

找到对应的BSSID:


![10.png](http://upload-images.jianshu.io/upload_images/8086912-28e1ebf39e2ce8fd.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

结果为：
* 52:1a:a9:c1:fc:37
* ac:f1:df:78:c7:67
* 6c:70:9f:e8:57:90
* ec:88:8f:95:ff:12

### WIFI Hacking 6 附件中哪些AP支持WPA/WPA2企业级认证方式,这些热点的MAC地址集合:

在RSN中将版本号和AKM认证密钥类型作为过滤条件
![11.png](http://upload-images.jianshu.io/upload_images/8086912-1e2779c9805d14d0.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

得到SSID结果为：a101e-lab,CMCC

找到对应的MAC地址，结果：
* d8:fe:e3:e5:31:18
* 52:1a:a9:c1:fc:37

### WIFI Hacking 7 附件中哪些AP可能是设置了禁止SSID广播？试列举所有的BSSID:

禁止SSID广播之后检测不到网络beacons为0，但之前连接过的仍然能够发送请求并得到probe response


![12.png](http://upload-images.jianshu.io/upload_images/8086912-1f654f7ea700c901.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

得到的SSID有:dj,48-A102

对应的MAC地址结果为：
* 6c:70:9f:e8:57:90
* ec:88:8f:95:ff:12
