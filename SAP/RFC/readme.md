# SAP RFC

## Synchronous RFC
![image](/SAP/RFC/asset/img/RFC_Normal_vs_Remote.jpg)

### Processing Type
![image](/SAP/RFC/asset/draw/image1.excalidraw.png)
1. Normal Function Module
   - can be called anywhere within the same server.
2. Remote-Enabled Module
   - can be accessed from remote server. 

### Creating the RFC Server and Client

![image](/SAP/RFC/asset/img/RFC_Server_and_Client.jpg)

#### RFC Server
is the server where our Remote FM is created and stored.

| Function Group | ZAA_RFCTESTS |
| -------------- | ------------ |
| DB Table       | ZROHIT_TB1   |
| Remote FM      | ZRFC_FM1     |
| IP Address     | 10.10.14.88  |
| Instance ID    | 00           |
| Username       | developer4   |
| Password       | @Access05    |
|                |              |

1. Create the Function Group
   - ![image](/SAP/RFC/asset/draw/image2.excalidraw.png)
   - **LZAA_RFCTESTSTOP** - we can declare global variables that can be accessed  from all the function modules within this function group.
   - **LZAA_RFCTESTSUXX** - SAP internal use. Do not make any change. 
2. Analyze the Requirement for the remote FM
   - Create DB table ZROHIT_TB1
3. Create the Remote FM
   - ![image](/SAP/RFC/asset/draw/image3.excalidraw.png)
4. Test the Remote FM
   - ![image](/SAP/RFC/asset/draw/image4.excalidraw.png)

#### RFC Client
is the server from where we want to access our remote FM.

1. Collect info from RFC server

| IP Address  | 10.10.14.88 |
| ----------- | ----------- |
| Instance ID | 00          |
| Username    | developer4  |
| Password    | @Access05   |
|             |             |

2. Create RFC Destination from SM59 (Basis Consultant)