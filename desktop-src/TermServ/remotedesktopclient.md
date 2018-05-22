---
title: RemoteDesktopClient class
description: Implements the Microsoft Windows Store App Remote Desktop Client Control - version 1.
audience: developer
author: REDMOND\\markl
manager: REDMOND\\markl
ms.assetid: '0910883A-BD49-4908-8423-1FC280E0FE0C'
ms.prod: 'windows-server-dev'
ms.technology: 'remote-desktop-services'
ms.tgt_platform: multiple
keywords: ["RemoteDesktopClient class Remote Desktop Services", "RemoteDesktopClient class Remote Desktop Services , described"]
topic_type:
- apiref
api_name:
- RemoteDesktopClient
api_location:
- MsTscAx.dll
api_type:
- COM
---

# RemoteDesktopClient class

Implements the Microsoft Windows Store App Remote Desktop Client Control - version 1

This class implements the following interfaces.

-   [**IRemoteDesktopClient**](iremotedesktopclient.md)
-   [**IRemoteDesktopClientEvents**](iremotedesktopclientevents.md)

**RemoteDesktopClient** has these types of members:

-   [Methods](#methods)
-   [Properties](#properties)

### Methods

The **RemoteDesktopClient** class has these methods.



| Method                                                                                      | Description                                                                                                                                                        |
|:--------------------------------------------------------------------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [**attachEvent**](iremotedesktopclient-attachevent.md)                                     | Attaches an event handler to an event.<br/>                                                                                                                  |
| [**Connect**](iremotedesktopclient-connect.md)                                             | Initiates a connection by using the properties currently set on the Remote Desktop Protocol (RDP) app container client control.<br/>                         |
| [**DeleteSavedCredentials**](iremotedesktopclient-deletesavedcredentials.md)               | Deletes saved credentials for the specified remote computer.<br/>                                                                                            |
| [**detachEvent**](iremotedesktopclient-detachevent.md)                                     | Detaches an event handler from an event.<br/>                                                                                                                |
| [**Disconnect**](iremotedesktopclient-disconnect.md)                                       | Disconnects the active connection.<br/>                                                                                                                      |
| [**OnAdminMessageReceived**](iremotedesktopclientevents-onadminmessagereceived.md)         | Called when the client control receives an administrative message.<br/>                                                                                      |
| [**OnAutoReconnected**](iremotedesktopclientevents-onautoreconnected.md)                   | Called when the client control has automatically reconnected to a remote session.<br/>                                                                       |
| [**OnAutoReconnecting**](iremotedesktopclientevents-onautoreconnecting.md)                 | Called when the client control attempts to automatically reestablish a connection to a remote session.<br/>                                                  |
| [**OnConnected**](iremotedesktopclientevents-onconnected.md)                               | Called when the client control has connected to a remote session.<br/>                                                                                       |
| [**OnConnecting**](iremotedesktopclientevents-onconnecting.md)                             | Called when the client control attempts to establish a connection to a remote session.<br/>                                                                  |
| [**OnDialogDismissed**](iremotedesktopclientevents-ondialogdismissed.md)                   | Called after a dialog box displayed by the client control is dismissed.<br/>                                                                                 |
| [**OnDialogDisplaying**](iremotedesktopclientevents-ondialogdisplaying.md)                 | Called before the control displays a dialog box.<br/>                                                                                                        |
| [**OnDisconnected**](iremotedesktopclientevents-ondisconnected.md)                         | Called when the client control has been disconnected from a remote session.<br/>                                                                             |
| [**OnKeyCombinationPressed**](iremotedesktopclientevents-onkeycombinationpressed.md)       | Called when special key combinations are pressed in the remote session.<br/>                                                                                 |
| [**OnLoginCompleted**](iremotedesktopclientevents-onlogincompleted.md)                     | Called when the client control has successfully logged on to a remote session.<br/>                                                                          |
| [**OnNetworkStatusChanged**](iremotedesktopclientevents-onnetworkstatuschanged.md)         | Called when the network status has changed.<br/>                                                                                                             |
| [**OnRemoteDesktopSizeChanged**](iremotedesktopclientevents-onremotedesktopsizechanged.md) | Called when the remote desktop size has changed.<br/>                                                                                                        |
| [**OnStatusChanged**](iremotedesktopclientevents-onstatuschanged.md)                       | Called when the client control has updated its status.<br/>                                                                                                  |
| [**OnTouchPointerCursorMoved**](iremotedesktopclientevents-ontouchpointercursormoved.md)   | Called when the touch pointer cursor has moved and the [**EventsEnabled**](iremotedesktopclienttouchpointer-eventsenabled.md) property is set to true.<br/> |
| [**Reconnect**](iremotedesktopclient-reconnect.md)                                         | Initiates an automatic reconnection of the Remote Desktop Protocol (RDP) app container client control to fit the session to the new width and height.<br/>   |
| [**UpdateSessionDisplaySettings**](iremotedesktopclient-updatesessiondisplaysettings.md)   | Updates the width and height settings for the Remote Desktop Protocol (RDP) app container client control.<br/>                                               |



�

### Properties

The **RemoteDesktopClient** class has these properties.



| Property                                                             | Access type          | Description                                                                                                                                                            |
|:---------------------------------------------------------------------|:---------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [**Actions**](iremotedesktopclient-actions.md)<br/>           | Read-only<br/> | Retrieves the actions object for the Remote Desktop Protocol (RDP) app container client.<br/>                                                                    |
| [**Settings**](iremotedesktopclient-settings.md)<br/>         | Read-only<br/> | Retrieves the settings object for the Remote Desktop Protocol (RDP) app container client.<br/>                                                                   |
| [**TouchPointer**](iremotedesktopclient-touchpointer.md)<br/> | Read-only<br/> | Contains the [**RemoteDesktopClientTouchPointer**](iremotedesktopclienttouchpointer.md) object for the Remote Desktop Protocol (RDP) app container client.<br/> |



�

## Requirements



|                                     |                                                                                          |
|-------------------------------------|------------------------------------------------------------------------------------------|
| Minimum supported client<br/> | Windows�8<br/>                                                                     |
| Minimum supported server<br/> | Windows Server�2012<br/>                                                           |
| Type library<br/>             | <dl> <dt>MsTscAx.dll</dt> </dl>   |
| DLL<br/>                      | <dl> <dt>MsTscAx.dll</dt> </dl>   |
| CLSID<br/>                    | CLSID\_RemoteDesktopClient is defined as EAB16C5D-EED1-4E95-868B-0FBA1B42C092<br/> |



## See also

<dl> <dt>

[Remote Desktop ActiveX control classes](remote-desktop-activex-control-classes.md)
</dt> </dl>

�

�




