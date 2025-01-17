---
UID: NC:ucxendpoint.EVT_UCX_ENDPOINT_ABORT
title: EVT_UCX_ENDPOINT_ABORT (ucxendpoint.h)
description: The client driver's implementation that UCX calls to abort the queue associated with the endpoint.
old-location: buses\evt_ucx_endpoint_abort.htm
tech.root: usbref
ms.date: 05/07/2018
keywords: ["EVT_UCX_ENDPOINT_ABORT callback function"]
ms.keywords: EVT_UCX_ENDPOINT_ABORT, EVT_UCX_ENDPOINT_ABORT callback, EvtUcxEndpointAbort, EvtUcxEndpointAbort callback function [Buses], PEVT_UCX_ENDPOINT_ABORT, PEVT_UCX_ENDPOINT_ABORT callback function pointer [Buses], buses.evt_ucx_endpoint_abort, ucxendpoint/EvtUcxEndpointAbort
req.header: ucxendpoint.h
req.include-header: Ucxclass.h, Ucxendpoint.h
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 1.0
req.umdf-ver: 2.0
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: DISPATCH_LEVEL
targetos: Windows
req.typenames: 
f1_keywords:
 - EVT_UCX_ENDPOINT_ABORT
 - ucxendpoint/EVT_UCX_ENDPOINT_ABORT
topic_type:
 - APIRef
 - kbSyntax
api_type:
 - UserDefined
api_location:
 - ucxendpoint.h
api_name:
 - EVT_UCX_ENDPOINT_ABORT
---

# EVT_UCX_ENDPOINT_ABORT callback function


## -description

The client driver's implementation that UCX calls to abort the queue associated with the endpoint.

## -parameters

### -param UcxController [in]


 A handle to the UCX controller that the client driver received in a previous call to  the <a href="/previous-versions/windows/hardware/drivers/mt188033(v=vs.85)">UcxControllerCreate</a> method.

### -param UcxEndpoint

### -param Endpoint [in]

A handle to a UCXENDPOINT object.

## -remarks

The client driver registers this callback function with the USB host controller extension (UCX) by calling the <a href="/windows-hardware/drivers/ddi/ucxendpoint/nf-ucxendpoint-ucxendpointcreate">UcxEndpointCreate</a>
 method.

This function completes all requests associated with the endpoint, typically by calling <a href="/windows-hardware/drivers/ddi/wdfio/nf-wdfio-wdfioqueuestopandpurge">WdfIoQueueStopAndPurge</a>.


#### Examples


```
VOID
Endpoint_UcxEvtEndpointAbort(
    UCXCONTROLLER   UcxController,
	   UCXENDPOINT     UcxEndpoint
	  )
	{
	            WdfIoQueueStopAndPurge(endpointContext->WdfQueue,
	                                   Endpoint_WdfEvtAbortComplete,
	                                   UcxEndpoint);
	}

```

