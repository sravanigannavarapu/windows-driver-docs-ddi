---
UID: NC:dispmprt.DXGKDDI_OPM_CREATE_PROTECTED_OUTPUT_NONLOCAL_DISPLAY
title: DXGKDDI_OPM_CREATE_PROTECTED_OUTPUT_NONLOCAL_DISPLAY
description: "Learn more about: DXGKDDI_OPM_CREATE_PROTECTED_OUTPUT_NONLOCAL_DISPLAY callback function"
tech.root: display
ms.date: 04/04/2019
keywords: ["DXGKDDI_OPM_CREATE_PROTECTED_OUTPUT_NONLOCAL_DISPLAY callback function"]
req.header: dispmprt.h
req.include-header: 
req.target-type: 
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.lib: 
req.dll: 
req.irql: 
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
targetos: Windows
ms.custom: 19H1
f1_keywords:
 - DXGKDDI_OPM_CREATE_PROTECTED_OUTPUT_NONLOCAL_DISPLAY
 - dispmprt/DXGKDDI_OPM_CREATE_PROTECTED_OUTPUT_NONLOCAL_DISPLAY
topic_type:
 - apiref
api_type:
 - UserDefined
api_location:
 - dispmprt.h
api_name:
 - DXGKDDI_OPM_CREATE_PROTECTED_OUTPUT_NONLOCAL_DISPLAY
product:
 - Windows
dev_langs:
 - c++
---

# DXGKDDI_OPM_CREATE_PROTECTED_OUTPUT_NONLOCAL_DISPLAY callback function


## -description

## -parameters

### -param MiniportDeviceContext 

### -param NewVideoOutputSemantics: 

### -param OPMEncoderContext 

### -param pActualOutputFormat: 

### -param NonLocalOutputId: 

### -param NonLocalConnectorType: 

### -param NewProtectedOutputHandle: 

## -returns

Return STATUS_SUCCESS if the operation succeeds.

## -prototype

```
//Declaration

DXGKDDI_OPM_CREATE_PROTECTED_OUTPUT_NONLOCAL_DISPLAY DxgkddiOpmCreateProtectedOutputNonlocalDisplay; 

// Definition

NTSTATUS DxgkddiOpmCreateProtectedOutputNonlocalDisplay 
(
	PVOID MiniportDeviceContext
	DXGKMDT_OPM_VIDEO_OUTPUT_SEMANTICS NewVideoOutputSemantics
	UINT64 OPMEncoderContext
	DXGKMDT_OPM_ACTUAL_OUTPUT_FORMAT *pActualOutputFormat
	UINT64 NonLocalOutputId
	DXGKMDT_OPM_CONNECTOR_TYPE NonLocalConnectorType
	PHANDLE NewProtectedOutputHandle
)
{...}

```

## -remarks

## -see-also

