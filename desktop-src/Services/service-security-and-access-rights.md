---
Description: 'The Windows security model enables you to control access to the service control manager (SCM) and service objects.'
ms.assetid: '23d1c382-6ba4-49e2-8039-c2a91471076c'
title: Service Security and Access Rights
---

# Service Security and Access Rights

The Windows security model enables you to control access to the service control manager (SCM) and service objects. The following sections provide detailed information:

-   [Access Rights for the Service Control Manager](#access-rights-for-the-service-control-manager)
-   [Access Rights for a Service](#access-rights-for-a-service)

## Access Rights for the Service Control Manager

The following are the specific access rights for the SCM.



| Access right                                   | Description                                                                                                                                                                                                                                                                                                                                                              |
|------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **SC\_MANAGER\_ALL\_ACCESS** (0xF003F)         | Includes **STANDARD\_RIGHTS\_REQUIRED**, in addition to all access rights in this table.                                                                                                                                                                                                                                                                                 |
| **SC\_MANAGER\_CREATE\_SERVICE** (0x0002)      | Required to call the [**CreateService**](createservice.md) function to create a service object and add it to the database.                                                                                                                                                                                                                                              |
| **SC\_MANAGER\_CONNECT** (0x0001)              | Required to connect to the service control manager.                                                                                                                                                                                                                                                                                                                      |
| **SC\_MANAGER\_ENUMERATE\_SERVICE** (0x0004)   | Required to call the [**EnumServicesStatus**](enumservicesstatus.md) or [**EnumServicesStatusEx**](enumservicesstatusex.md) function to list the services that are in the database.<br/> Required to call the [**NotifyServiceStatusChange**](notifyservicestatuschange.md) function to receive notification when any service is created or deleted.<br/> |
| **SC\_MANAGER\_LOCK** (0x0008)                 | Required to call the [**LockServiceDatabase**](lockservicedatabase.md) function to acquire a lock on the database.                                                                                                                                                                                                                                                      |
| **SC\_MANAGER\_MODIFY\_BOOT\_CONFIG** (0x0020) | Required to call the [**NotifyBootConfigStatus**](notifybootconfigstatus.md) function.                                                                                                                                                                                                                                                                                  |
| **SC\_MANAGER\_QUERY\_LOCK\_STATUS** (0x0010)  | Required to call the [**QueryServiceLockStatus**](queryservicelockstatus.md) function to retrieve the lock status information for the database.                                                                                                                                                                                                                         |



�

The following are the [generic access rights](https://msdn.microsoft.com/library/windows/desktop/aa446632) for the SCM.



<table>
<thead>
<tr class="header">
<th>Access right</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>GENERIC_READ</strong></td>
<td><dl> <strong>STANDARD_RIGHTS_READ</strong><br />
<strong>SC_MANAGER_ENUMERATE_SERVICE</strong><br />
<strong>SC_MANAGER_QUERY_LOCK_STATUS</strong><br />
</dl></td>
</tr>
<tr class="even">
<td><strong>GENERIC_WRITE</strong></td>
<td><dl> <strong>STANDARD_RIGHTS_WRITE</strong><br />
<strong>SC_MANAGER_CREATE_SERVICE</strong><br />
<strong>SC_MANAGER_MODIFY_BOOT_CONFIG</strong><br />
</dl></td>
</tr>
<tr class="odd">
<td><strong>GENERIC_EXECUTE</strong></td>
<td><dl> <strong>STANDARD_RIGHTS_EXECUTE</strong><br />
<strong>SC_MANAGER_CONNECT</strong><br />
<strong>SC_MANAGER_LOCK</strong><br />
</dl></td>
</tr>
<tr class="even">
<td><strong>GENERIC_ALL</strong></td>
<td><dl> <strong>SC_MANAGER_ALL_ACCESS</strong><br />
</dl></td>
</tr>
</tbody>
</table>



�

A process with the correct access rights can open a handle to the SCM that can be used in the [**OpenService**](openservice.md), [**EnumServicesStatusEx**](enumservicesstatusex.md), and [**QueryServiceLockStatus**](queryservicelockstatus.md) functions. Only processes with Administrator privileges are able to open handles to the SCM that can be used by the [**CreateService**](createservice.md) and [**LockServiceDatabase**](lockservicedatabase.md) functions.

The system creates the security descriptor for the SCM. To get or set the security descriptor for the SCM, use the [**QueryServiceObjectSecurity**](https://msdn.microsoft.com/library/windows/desktop/aa379312) and [**SetServiceObjectSecurity**](https://msdn.microsoft.com/library/windows/desktop/aa379589) functions with a handle to the SCManager object.

**Windows Server�2003 and Windows�XP:** Unlike most other securable objects, the security descriptor for the SCM cannot be modified. This behavior has changed as of Windows Server�2003 with Service Pack�1 (SP1).

The following access rights are granted.



<table>
<thead>
<tr class="header">
<th>Account</th>
<th>Access rights</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Remote authenticated users</td>
<td><dl> <strong>SC_MANAGER_CONNECT</strong><br />
</dl></td>
</tr>
<tr class="even">
<td>Local authenticated users (including LocalService and NetworkService)</td>
<td><dl> <strong>SC_MANAGER_CONNECT</strong><br />
<strong>SC_MANAGER_ENUMERATE_SERVICE</strong><br />
<strong>SC_MANAGER_QUERY_LOCK_STATUS</strong><br />
<strong>STANDARD_RIGHTS_READ</strong><br />
</dl></td>
</tr>
<tr class="odd">
<td>LocalSystem</td>
<td><dl> <strong>SC_MANAGER_CONNECT</strong><br />
<strong>SC_MANAGER_ENUMERATE_SERVICE</strong><br />
<strong>SC_MANAGER_MODIFY_BOOT_CONFIG</strong><br />
<strong>SC_MANAGER_QUERY_LOCK_STATUS</strong><br />
<strong>STANDARD_RIGHTS_READ</strong><br />
</dl></td>
</tr>
<tr class="even">
<td>Administrators</td>
<td><dl> <strong>SC_MANAGER_ALL_ACCESS</strong><br />
</dl></td>
</tr>
</tbody>
</table>



�

Notice that remote users authenticated over the network but not interactively logged on can connect to the SCM but not perform operations that require other access rights. To perform these operations, the user must be logged on interactively or the service must use one of the service accounts.

**Windows Server�2003 and Windows�XP:** Remote authenticated users are granted the **SC\_MANAGER\_CONNECT**, **SC\_MANAGER\_ENUMERATE\_SERVICE**, **SC\_MANAGER\_QUERY\_LOCK\_STATUS**, and **STANDARD\_RIGHTS\_READ** access rights. These access rights are restricted as described in the previous table as of Windows Server�2003 with SP1

When a process uses the [**OpenSCManager**](openscmanager.md) function to open a handle to a database of installed services, it can request access rights. The system performs a security check against the security descriptor for the SCM before granting the requested access rights.

## Access Rights for a Service

The following are the specific access rights for a service.



| Access right                                | Description                                                                                                                                                                                                                                                                                                                                                                          |
|---------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **SERVICE\_ALL\_ACCESS** (0xF01FF)          | Includes **STANDARD\_RIGHTS\_REQUIRED** in addition to all access rights in this table.                                                                                                                                                                                                                                                                                              |
| **SERVICE\_CHANGE\_CONFIG** (0x0002)        | Required to call the [**ChangeServiceConfig**](changeserviceconfig.md) or [**ChangeServiceConfig2**](changeserviceconfig2.md) function to change the service configuration. Because this grants the caller the right to change the executable file that the system runs, it should be granted only to administrators.                                                              |
| **SERVICE\_ENUMERATE\_DEPENDENTS** (0x0008) | Required to call the [**EnumDependentServices**](enumdependentservices.md) function to enumerate all the services dependent on the service.                                                                                                                                                                                                                                         |
| **SERVICE\_INTERROGATE** (0x0080)           | Required to call the [**ControlService**](controlservice.md) function to ask the service to report its status immediately.                                                                                                                                                                                                                                                          |
| **SERVICE\_PAUSE\_CONTINUE** (0x0040)       | Required to call the [**ControlService**](controlservice.md) function to pause or continue the service.                                                                                                                                                                                                                                                                             |
| **SERVICE\_QUERY\_CONFIG** (0x0001)         | Required to call the [**QueryServiceConfig**](queryserviceconfig.md) and [**QueryServiceConfig2**](queryserviceconfig2.md) functions to query the service configuration.                                                                                                                                                                                                           |
| **SERVICE\_QUERY\_STATUS** (0x0004)         | Required to call the [**QueryServiceStatus**](queryservicestatus.md) or [**QueryServiceStatusEx**](queryservicestatusex.md) function to ask the service control manager about the status of the service.<br/> Required to call the [**NotifyServiceStatusChange**](notifyservicestatuschange.md) function to receive notification when a service changes status.<br/> |
| **SERVICE\_START** (0x0010)                 | Required to call the [**StartService**](startservice.md) function to start the service.                                                                                                                                                                                                                                                                                             |
| **SERVICE\_STOP** (0x0020)                  | Required to call the [**ControlService**](controlservice.md) function to stop the service.                                                                                                                                                                                                                                                                                          |
| **SERVICE\_USER\_DEFINED\_CONTROL**(0x0100) | Required to call the [**ControlService**](controlservice.md) function to specify a user-defined control code.                                                                                                                                                                                                                                                                       |



�

The following are the [standard access rights](https://msdn.microsoft.com/library/windows/desktop/aa379607) for a service.



| Access right                 | Description                                                                                                                                                                                                                                                                                                                                                                                                                                  |
|------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **ACCESS\_SYSTEM\_SECURITY** | Required to call the [**QueryServiceObjectSecurity**](https://msdn.microsoft.com/library/windows/desktop/aa379312) or [**SetServiceObjectSecurity**](https://msdn.microsoft.com/library/windows/desktop/aa379589) function to access the SACL. The proper way to obtain this access is to enable the **SE\_SECURITY\_NAME**[**privilege**](https://msdn.microsoft.com/library/windows/desktop/aa379306) in the caller's current access token, open the handle for **ACCESS\_SYSTEM\_SECURITY** access, and then disable the privilege. |
| **DELETE**                   | Required to call the [**DeleteService**](deleteservice.md) function to delete the service.                                                                                                                                                                                                                                                                                                                                                  |
| **READ\_CONTROL**            | Required to call the [**QueryServiceObjectSecurity**](https://msdn.microsoft.com/library/windows/desktop/aa379312) function to query the security descriptor of the service object.                                                                                                                                                                                                                                                                                  |
| **WRITE\_DAC**               | Required to call the [**SetServiceObjectSecurity**](https://msdn.microsoft.com/library/windows/desktop/aa379589) function to modify the **Dacl** member of the service object's security descriptor.                                                                                                                                                                                                                                                                   |
| **WRITE\_OWNER**             | Required to call the [**SetServiceObjectSecurity**](https://msdn.microsoft.com/library/windows/desktop/aa379589) function to modify the **Owner** and **Group** members of the service object's security descriptor.                                                                                                                                                                                                                                                   |



�

The following are the [generic access rights](https://msdn.microsoft.com/library/windows/desktop/aa446632) for a service.



<table>
<thead>
<tr class="header">
<th>Access right</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>GENERIC_READ</strong></td>
<td><dl> <strong>STANDARD_RIGHTS_READ</strong><br />
<strong>SERVICE_QUERY_CONFIG</strong><br />
<strong>SERVICE_QUERY_STATUS</strong><br />
<strong>SERVICE_INTERROGATE</strong><br />
<strong>SERVICE_ENUMERATE_DEPENDENTS</strong><br />
</dl></td>
</tr>
<tr class="even">
<td><strong>GENERIC_WRITE</strong></td>
<td><dl> <strong>STANDARD_RIGHTS_WRITE</strong><br />
<strong>SERVICE_CHANGE_CONFIG</strong><br />
</dl></td>
</tr>
<tr class="odd">
<td><strong>GENERIC_EXECUTE</strong></td>
<td><dl> <strong>STANDARD_RIGHTS_EXECUTE</strong><br />
<strong>SERVICE_START</strong><br />
<strong>SERVICE_STOP</strong><br />
<strong>SERVICE_PAUSE_CONTINUE</strong><br />
<strong>SERVICE_USER_DEFINED_CONTROL</strong><br />
</dl></td>
</tr>
</tbody>
</table>



�

The SCM creates a service object's security descriptor when the service is installed by the [**CreateService**](createservice.md) function. The default security descriptor of a service object grants the following access.



<table>
<thead>
<tr class="header">
<th>Account</th>
<th>Access rights</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Remote authenticated users</td>
<td>Not granted by default.<strong>Windows Server�2003 with SP1:��SERVICE_USER_DEFINED_CONTROL</strong><br/> <strong>Windows Server�2003 and Windows�XP:</strong> The access rights for remote authenticated users are the same as for local authenticated users.<br/></td>
</tr>
<tr class="even">
<td>Local authenticated users (including LocalService and NetworkService)</td>
<td><dl> <strong>READ_CONTROL</strong><br />
<strong>SERVICE_ENUMERATE_DEPENDENTS</strong><br />
<strong>SERVICE_INTERROGATE</strong><br />
<strong>SERVICE_QUERY_CONFIG</strong><br />
<strong>SERVICE_QUERY_STATUS</strong><br />
<strong>SERVICE_USER_DEFINED_CONTROL</strong><br />
</dl></td>
</tr>
<tr class="odd">
<td>LocalSystem</td>
<td><dl> <strong>READ_CONTROL</strong><br />
<strong>SERVICE_ENUMERATE_DEPENDENTS</strong><br />
<strong>SERVICE_INTERROGATE</strong><br />
<strong>SERVICE_PAUSE_CONTINUE</strong><br />
<strong>SERVICE_QUERY_CONFIG</strong><br />
<strong>SERVICE_QUERY_STATUS</strong><br />
<strong>SERVICE_START</strong><br />
<strong>SERVICE_STOP</strong><br />
<strong>SERVICE_USER_DEFINED_CONTROL</strong><br />
</dl></td>
</tr>
<tr class="even">
<td>Administrators</td>
<td><dl> <strong>DELETE</strong><br />
<strong>READ_CONTROL</strong><br />
<strong>SERVICE_ALL_ACCESS</strong><br />
<strong>WRITE_DAC</strong><br />
<strong>WRITE_OWNER</strong><br />
</dl></td>
</tr>
</tbody>
</table>



�

To perform any operations, the user must be logged on interactively or the service must use one of the service accounts.

To get or set the security descriptor for a service object, use the [**QueryServiceObjectSecurity**](https://msdn.microsoft.com/library/windows/desktop/aa379312) and [**SetServiceObjectSecurity**](https://msdn.microsoft.com/library/windows/desktop/aa379589) functions. For more information, see [Modifying the DACL for a Service](modifying-the-dacl-for-a-service.md).

When a process uses the [**OpenService**](openservice.md) function, the system checks the requested access rights against the security descriptor for the service object.

Granting certain access rights to untrusted users (such as **SERVICE\_CHANGE\_CONFIG** or **SERVICE\_STOP**) can allow them to interfere with the execution of your service, and possibly allow them to run applications under the LocalSystem account.

When [**EnumServicesStatusEx function**](enumservicesstatusex.md) is called, if the caller does not have the **SERVICE\_QUERY\_STATUS** access right to a service, the service is silently omitted from the list of services returned to the client.

�

�



