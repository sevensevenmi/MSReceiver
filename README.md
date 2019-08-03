# 密钥接收器

通过websocket实现服务端远程发送密钥给客户端

客户端收到密钥后实现激活过程

V3.1 新增备份CID及激活信息 新重重建tokens 新增逐条还原激活信息

![image](https://github.com/laomms/MSReceiver/blob/master/msc.png)

Activation.dll接口说明

密钥安装及激活控件.也可用于测密钥.自动判断系统类型，自适应密钥类型.
szKey:密钥输入
szErrorCode:激活结果
函数名:Function Activating(szKey as string,ByRef szErrorCode As String) As Integer (SPPC.dll控件实现) 
函数名:Function Activation(szKey as string,ByRef szErrorCode As String) As Integer (WMI中的CIMV2搜索实现)
函数名:Function InstallCID(InstalltionID As String, ConfirmationID As String, ByRef szResult As String) As Integer
.net4.6运行库,使用说明:


vb.net:

        Dim func As New Activation.Activate
        Dim szResult As String = ""
        Dim flags = func.Activating("VK7JG-NPHTM-C97JM-9MPGT-3V66T", szResult)
        Do
            If flags <> 0 Then
                Exit Do
            End If
            Application.DoEvents()
        Loop
        Debug.Print(szResult)


c#:

            Activation.Activate func = new Activation.Activate();
            string szResult = string.Empty;
            int flags = func.Activating("VK7JG-NPHTM-C97JM-9MPGT-3V66T", ref szResult);
            do
            {
              Application.DoEvents();
            } while (flags == 0);
            Console.WriteLine(szResult);
            

![image](https://github.com/laomms/MSReceiver/blob/master/app.jpg)
