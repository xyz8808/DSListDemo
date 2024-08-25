服务端集成：
插件会每10秒从配置文件读取新配置，不必停止服务进程就可以加载最新配置，这让动态修改服务进程中的一些参数更方便。
在GameInstance的init事件中注册服务器，使用“RegisterServer”节点

![image](https://github.com/user-attachments/assets/95e4c21e-11fc-46b6-978b-24267efc5db6)

“GetDedicatedServerSlotName” 节点可以获取从启动参数传递过来的SlotName

![image](https://github.com/user-attachments/assets/1cf377b4-4a92-41ea-b322-ae9d7fcc8bef)
![image](https://github.com/user-attachments/assets/71ab6ad0-6c2b-44dd-902a-8f5de8f32afe)


“SetExtraData” 节点可以在服务器运行中动态添加扩展数据，然后通过“GetExtraData”获取扩展数据

![image](https://github.com/user-attachments/assets/d916ce25-0512-4513-a829-2bbc542ab070)
![image](https://github.com/user-attachments/assets/9c5057c4-3180-4777-965c-20758241cb96)

“GetLocalConfig”节点可以获取从配置文件中加载的信息

![image](https://github.com/user-attachments/assets/322be4b1-298a-4cb0-90e6-d10cebb5df0e)


配置文件格式：
如配置文件名：DedicatedServer.config
文件内容：
{
  "ShowLog":false,
  "SubscriptionID": "dev",
  "ServerNativeName": "中文服务器名",
  "ServerEnName": "chinese servername",
  "Region": "CN",
  "GameMode": "PVP",
  "MaxPlayerNum": 100,
  "Password": "",
  "OrderNum": 1,
  "IP": "127.0.0.1",
  "ExtraDataWithConfig":{
	"test":"test value"
  }
}

客户端集成：
可以直接复制UI文件夹中的内容到项目中，使用默认的UI。
在需要打开服务器列表的地方调用：
添加UI到界面上，绑定服务器确认事件

![image](https://github.com/user-attachments/assets/c47dd154-483b-43d5-8ccb-51f5f0a25db4)

ServerConfirm：在事件中提供了服务器信息，使用OpenLevel连接服务器

![image](https://github.com/user-attachments/assets/e67e601a-20da-47da-8268-8d7b8a4c7518)

自定义UI：
参考UI中的处理，使用以下节点处理搜索服务器请求，搜索结果事件，验证密码请求，验证密码事件，Ping完成事件
搜索服务器请求：

![image](https://github.com/user-attachments/assets/92e5d2c0-8b1e-46fb-83aa-5d67560f094e)
![image](https://github.com/user-attachments/assets/2a9765ee-9a91-49bc-99a4-b84dcf678081)

搜索结果事件：

![image](https://github.com/user-attachments/assets/923e569a-c6d8-4e6c-afec-6202dfb578be)

验证密码请求：

![image](https://github.com/user-attachments/assets/ea192a8e-592e-4e23-80f8-967c83265fce)

验证密码事件：

![image](https://github.com/user-attachments/assets/b314fce0-42dd-4e0b-8206-0d746094a213)

Ping完成事件：

![image](https://github.com/user-attachments/assets/3845ec63-02ba-4e08-8839-08dc71531904)


