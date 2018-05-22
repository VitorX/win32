---
title: Licensing and IClassFactory2
description: Licensing and IClassFactory2
ms.assetid: '2bead555-8c62-4f48-a4c6-6f0942ec75f8'
---

# Licensing and IClassFactory2

The [**IClassFactory**](iclassfactory.md) interface on a class object provides the basic object creation mechanism of COM. Using **IClassFactory**, a server can control object creation on a machine basis. The implementation of the [**IClassFactory::CreateInstance**](iclassfactory-createinstance.md) method can allow or disallow object creation based on the existence of a machine license. A machine license is a piece of information separate from the application that exists on a machine to indicate that the software was installed from a valid source, such as the vendor's installation disks. If the machine license does not exist, the server can disallow object creation. Machine licensing prevents piracy in cases where a user attempts to copy the software from one machine to another, because the license information is not copied with the software and the machine that receives the copy is not licensed.

However, in a component software industry, vendors need a finer level of control over licensing. In addition to machine license control, a vendor needs to allow some clients to create a component object while denying other clients the same capability. This requires that the client application obtain a license key from the component while the client application is still under development. The client application uses the license key at run time to create objects on an unlicensed machine.

For example, if a vendor provides a library of controls to developers, the developer who purchases the library will have a full machine license, allowing the objects to be created on the development machine. The developer can then build a client application on the licensed machine incorporating one or more of the controls. When the resulting client application is run on another machine, the controls used in the client application must be created on the other machine even if that machine does not possess a machine license for the controls from the original vendor.

The [**IClassFactory2**](iclassfactory2.md) interface provides this level of control. To allow key-based licensing for any given component, you implement **IClassFactory2** on the class factory object for that component. **IClassFactory2**is derived from [**IClassFactory**](iclassfactory.md), so by implementing **IClassFactory2**, the class factory object fulfills the basic COM requirements.

To incorporate a licensed component into your client application, use the following methods in [**IClassFactory2**](iclassfactory2.md):

-   The [**GetLicInfo**](iclassfactory2-getlicinfo.md) method fills a [**LICINFO**](licinfo.md) structure with information describing the licensing behavior of the class factory. For example, the class factory can provide license keys for run-time licensing if the **fRunTimeKeyAvail** member is **TRUE**.
-   The [**RequestLicKey**](iclassfactory2-requestlickey.md) method provides a license key for the component. A machine license must be available when the client calls this method.
-   The [**CreateInstanceLic**](iclassfactory2-createinstancelic.md) method creates an instance of the licensed component if the license key parameter (BSTRÂ bstrKey) is valid.

> [!Note]  
> In its type information, a component uses the attribute licensed to mark the coclass that supports licensing through [**IClassFactory2**](iclassfactory2.md).

 

First, you need a separate development tool that is also a client of the licensed component. The purpose of this tool is to obtain the run-time license key and save it in your client application. This tool runs only on a machine that possesses a machine license for the component. The tool calls the [**GetLicInfo**](iclassfactory2-getlicinfo.md) and [**RequestLicKey**](iclassfactory2-requestlickey.md) methods to obtain the run-time license key and then saves the license key in your client application. For example, the development tool could create a header (.h) file containing the BSTR license key, and then you would include that .h file in your client application.

To instantiate the component within your client application, first try to instantiate the object directly with [**IClassFactory::CreateInstance**](iclassfactory-createinstance.md). If **CreateInstance** succeeds, the second machine is licensed for the component and objects can be created at will. If **CreateInstance**fails with the return code CLASS\_E\_NOTLICENSED, the only way to create the object is to pass the run-time key to the [**CreateInstanceLic**](iclassfactory2-createinstancelic.md) method. **CreateInstanceLic** verifies the key and creates the object if the key is valid.

In this way, an application built with components (such as controls) can run on a machine that has no other license—only the client application containing the run-time license is allowed to create the component objects in question.

The [**IClassFactory2**](iclassfactory2.md) interface supports flexibility in licensing schemes. For example, the server implementor can encrypt license keys in the component for added security. Server implementers can also enable or disable levels of functionality in their objects by providing different license keys for different functions. For example, one key might allow a base level of functionality while another allows basic and advanced functionality, and so on.

## Related topics

<dl> <dt>

[COM Server Responsibilities](com-server-responsibilities.md)
</dt> </dl>

 

 



