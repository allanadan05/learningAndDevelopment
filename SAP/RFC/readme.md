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
| Client         | 888          |
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
| Client      | 888         |
|             |             |

2. Create RFC Destination from SM59 (Basis Consultant)
   
   | RFC Destination | ZRCON_AA                          |
   | --------------- | --------------------------------- |
   | Connection Type | 3 - RFC Connection to Abap System |
   |                 |                                   |

   ![image](/SAP/RFC/asset/draw/image5.excalidraw.png)

   **To check:**
   
   - look for record in RFCDES - Destination table for Remote Function Call in SE11.
   - Connection Test in SM59. If no, error logs, then it is successful
      ![image](/SAP/RFC/asset/draw/image6.excalidraw.png)

3. Create the RFC Client program to consume the RFC (ABAP Consultant)
   
   ```abap
      REPORT  ZDAN_RFC.

      PARAMETERS P_EMPNO TYPE I.

      DATA : V_ENAME(25) TYPE C,
      V_EMPDES(25) TYPE C.

      WRITE :/ 'HELLO ROHIT SINGH'.

      CALL FUNCTION 'ZRFC_FM1'
      DESTINATION 'ZRCON_AA'
      EXPORTING
      IP_EMPNO = P_EMPNO
      IMPORTING
      EP_ENAME = V_ENAME
      EP_EMPDES = V_EMPDES.

      WRITE :/ 'EMPLOYEE NAME IS :', V_ENAME,
      / 'EMPLOYEE DES IS :', V_EMPDES.


      WRITE :/ 'BYE AADAN'.  
   ```

   ![image](/SAP/RFC/asset/draw/image7.excalidraw.png)