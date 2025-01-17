---
UID: NF:ntifs.RtlInitUTF8StringEx
title: RtlInitUTF8StringEx function (ntifs.h)
description: RtlInitUTF8StringEx initializes a counted string of UTF-8 characters.
tech.root: ifsk
ms.date: 03/24/2020
ms.keywords: RtlInitUTF8StringEx
req.header: ntifs.h
req.include-header: 
req.target-type: 
req.target-min-winverclnt: Windows 10, version 2004
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
f1_keywords:
 - RtlInitUTF8StringEx
 - ntifs/RtlInitUTF8StringEx
topic_type:
 - apiref
api_type:
 - DllExport
api_location:
 - NtosKrnl.exe
api_name:
 - RtlInitUTF8StringEx
product:
 - Windows
---

# RtlInitUTF8StringEx function (ntifs.h)


## -description

**RtlInitUTF8StringEx** initializes a counted string of UTF-8 characters.

## -parameters

### -param DestinationString

Pointer to the UTF8_STRING structure to be initialized. The *ntdef.h* header file defines this structure to be identical to the [ANSI_STRING](/windows/win32/api/ntdef/ns-ntdef-string) structure.

### -param SourceString

Pointer to a null-terminated character string. *SourceString* is used to initialize the counted string that *DestinationString* points to.

## -returns

**RtlInitUTF8StringEx** returns STATUS_NAME_TOO_LONG if the *SourceString* is too long. Otherwise, this routine returns STATUS_SUCCESS.

## -remarks

**RtlInitUTF8StringEx** sets the members of the UTF8_STRING structure that *DestinationString* points to as follows:

- Copies the pointer value of *SourceString* into the **Buffer** member.

- Sets the **Length** member to the length, in bytes, of the source string, excluding the terminating null.

- Sets the **MaximumLength** member to the length, in bytes, of the source string, including the terminating null.

If *SourceString* is **NULL**, **Length** and **MaximumLength** are both set to zero.

**RtlInitStringEx** does not alter the source string pointed to by *SourceString*.

Callers of **RtlInitStringEx** can be running at IRQL <= DISPATCH_LEVEL if the *DestinationString* buffer is nonpageable. Usually, callers run at IRQL = PASSIVE_LEVEL because most other **Rtl*Xxx*String** routines cannot be called at IRQL > PASSIVE_LEVEL.

## -see-also

[ANSI_STRING](/windows/win32/api/ntdef/ns-ntdef-string)
