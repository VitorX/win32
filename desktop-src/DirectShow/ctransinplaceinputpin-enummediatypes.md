---
Description: The EnumMediaTypes method enumerates the pin's preferred media types. This method implements the IPin::EnumMediaTypes method.
ms.assetid: 0c28b4b0-a45f-400f-a6d7-7668458f9642
title: CTransInPlaceInputPin.EnumMediaTypes method
ms.technology: desktop
ms.prod: windows
ms.author: windowssdkdev
ms.topic: article
ms.date: 05/31/2018
---

# CTransInPlaceInputPin.EnumMediaTypes method

The `EnumMediaTypes` method enumerates the pin's preferred media types. This method implements the [**IPin::EnumMediaTypes**](/windows/desktop/api/Strmif/nf-strmif-ipin-enummediatypes) method.

## Syntax


```C++
HRESULT EnumMediaTypes(
   IEnumMediaTypes **ppEnum
);
```



## Parameters

<dl> <dt>

*ppEnum* 
</dt> <dd>

Receives a pointer to the [**IEnumMediaTypes**](/windows/desktop/api/Strmif/nn-strmif-ienummediatypes) interface.

</dd> </dl>

## Return value

Returns an **HRESULT** value. Possible values include those shown in the following table.



| Return code                                                                                           | Description                                 |
|-------------------------------------------------------------------------------------------------------|---------------------------------------------|
| <dl> <dt>**S\_OK**</dt> </dl>                  | Success.<br/>                         |
| <dl> <dt>**E\_OUTOFMEMORY**</dt> </dl>         | Insufficient memory.<br/>             |
| <dl> <dt>**E\_POINTER**</dt> </dl>             | **NULL** pointer.<br/>                |
| <dl> <dt>**VFW\_E\_NOT\_CONNECTED**</dt> </dl> | The output pin is not connected.<br/> |



 

## Remarks

This method returns the **IEnumMediaTypes** interface from downstream input pin.

## Requirements



|                    |                                                                                                                                                                                            |
|--------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Header<br/>  | <dl> <dt>Transip.h (include Streams.h)</dt> </dl>                                                                                   |
| Library<br/> | <dl> <dt>Strmbase.lib (retail builds); </dt> <dt>Strmbasd.lib (debug builds)</dt> </dl> |



## See also

<dl> <dt>

[**CTransInPlaceInputPin Class**](ctransinplaceinputpin.md)
</dt> </dl>

 

 



