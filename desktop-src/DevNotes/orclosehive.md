﻿---
Description: 'Closes the specified offline registry hive and frees memory allocated for the hive.'
ms.assetid: 'e30a92dd-8533-406f-ad63-96306f125d78'
title: ORCloseHive function
---

# ORCloseHive function

Closes the specified offline registry hive and frees memory allocated for the hive.

## Syntax


```C++
DWORD ORCloseHive(
  _In_ ORHKEY Handle
);
```



## Parameters

<dl> <dt>

*Handle* \[in\]
</dt> <dd>

A handle to the root key of the offline registry hive to be closed.

</dd> </dl>

## Return value

If the function succeeds, the return value is ERROR\_SUCCESS.

If the function fails, the return value is a nonzero error code defined in Winerror.h. You can use the [FormatMessage](http://go.microsoft.com/fwlink/p/?linkid=128767) function with the FORMAT\_MESSAGE\_FROM\_SYSTEM flag to get a generic description of the error.

## Remarks

The **ORCloseHive** function frees all memory allocated by the offline registry functions on behalf of the specified hive.

To preserve changes to the hive, call the [**ORSaveHive**](orsavehive.md) function before calling **ORCloseHive**.

## Requirements



|                            |                                                                                       |
|----------------------------|---------------------------------------------------------------------------------------|
| Redistributable<br/> | Windows Offline Registry library version 1.0 or later<br/>                      |
| Header<br/>          | <dl> <dt>Offreg.h</dt> </dl>   |
| DLL<br/>             | <dl> <dt>Offreg.dll</dt> </dl> |



## See also

<dl> <dt>

[**OROpenHive**](oropenhive.md)
</dt> <dt>

[**ORSaveHive**](orsavehive.md)
</dt> </dl>

 

 



