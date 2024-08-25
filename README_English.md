How to use:
Start the server with command line parameters:
start DSListDemoServer.exe ThirdPersonMap -log -slotname=ThirdPersonMap_01 -DedicatedServerConfigPath=Z:\ue\projects\DSListDemo\ WindowsServer\DedicatedServer.config
ThirdPersonMap: map name
-log ：Output log
-slotname: set the slot name, you can use GetDedicatedServerSlotName to get the corresponding value.
-DedicatedServerConfigPath specifies the path to the configuration file.

Server-side integration:
The plugin reads the new configuration from the configuration file every 10 seconds, so you don't have to stop the server process to load the latest configuration, which makes it easier to dynamically modify some parameters in the server process.
Register the server in the init event of the GameInstance, using the “RegisterServer” node

![image](https://github.com/user-attachments/assets/95e4c21e-11fc-46b6-978b-24267efc5db6)

The “GetDedicatedServerSlotName” node can be used to get the SlotName passed from the startup parameter

![image](https://github.com/user-attachments/assets/1cf377b4-4a92-41ea-b322-ae9d7fcc8bef)
![image](https://github.com/user-attachments/assets/71ab6ad0-6c2b-44dd-902a-8f5de8f32afe)


The “SetExtraData” node allows you to dynamically add extended data to the server while it is running, and then get the extended data via “GetExtraData”.

GetExtraData”. 

![image](https://github.com/user-attachments/assets/d916ce25-0512-4513-a829-2bbc542ab070)

GetExtraData” node. 

![image](https://github.com/user-attachments/assets/9c5057c4-3180-4777-965c-20758241cb96)

The “GetLocalConfig” node can get the information loaded from the configuration file.

![image](https://github.com/user-attachments/assets/322be4b1-298a-4cb0-90e6-d10cebb5df0e)


Configuration file format:
e.g. Configuration file name: DedicatedServer.config
File contents:
{
  “ShowLog":false,
  
  “ServerNativeName": ‘Chinese Server Name’,
  
  
  “GameMode": ‘PVP’, ‘MaxPlayerNum’.
  “MaxPlayerNum": 100, ‘Password’: ”,
  
  “OrderNum": 1, ‘IP’: ”127.0
  “IP": ‘127.0.0.1’,
  “ExtraDataWithConfig":{
	“test": ”test value”
  }
}

Client-side integration:
You can copy the contents of the UI folder directly into the project to use the default UI.
Call it where you need to open the server list:
Add UI to the interface, bind the server confirmation event

![image](https://github.com/user-attachments/assets/c47dd154-483b-43d5-8ccb-51f5f0a25db4)

ServerConfirm: provides the server information in the event, use OpenLevel to connect to the server

![image](https://github.com/user-attachments/assets/e67e601a-20da-47da-8268-8d7b8a4c7518)

Customize UI:
Referring to the processing in the UI, the following nodes are used to process the Search Server Request, Search Results event, Verify Password Request, Verify Password event, Ping Completed event
Search server request:

![image](https://github.com/user-attachments/assets/92e5d2c0-8b1e-46fb-83aa-5d67560f094e)

![image](https://github.com/user-attachments/assets/2a9765ee-9a91-49bc-99a4-b84dcf678081)

Search result event:

![image](https://github.com/user-attachments/assets/923e569a-c6d8-4e6c-afec-6202dfb578be)

Verify password request:

![image](https://github.com/user-attachments/assets/ea192a8e-592e-4e23-80f8-967c83265fce)

Verify password event:

![image](https://github.com/user-attachments/assets/b314fce0-42dd-4e0b-8206-0d746094a213)

Ping completion event:

! [image](https://github.com/user-attachments/assets/3845ec63-02ba-4e08-8839-08dc71531904)


