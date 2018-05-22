---
Description: 'The WSARecv, WSARecvFrom, WSARecvMsg, WSASend, WSASendMsg, and WSASendTo functions all take an array of application buffers as input parameters and can be used for scatter/gather (or vectored) I/O.'
ms.assetid: 'c42e6cea-3b40-44ad-8715-09ce57e82217'
title: 'Scatter/Gather I/O'
---

# Scatter/Gather I/O

The [**WSARecv**](wsarecv-2.md), [**WSARecvFrom**](wsarecvfrom-2.md), [**WSARecvMsg**](wsarecvmsg-2.md), [**WSASend**](wsasend-2.md), [**WSASendMsg**](wsasendmsg.md), and [**WSASendTo**](wsasendto-2.md) functions all take an array of application buffers as input parameters and can be used for scatter/gather (or vectored) I/O. This can be very useful in instances where portions of each message being transmitted consist of one or more fixed-length header components in addition to the message body. Such header components need not be concatenated by the application into a single contiguous buffer prior to sending. Likewise on receiving, the header components can be automatically split off into separate buffers, leaving the message body by itself.

When receiving into multiple buffers, completion occurs as data arrives from the network, regardless of whether all the supplied buffers are utilized.

 

 


