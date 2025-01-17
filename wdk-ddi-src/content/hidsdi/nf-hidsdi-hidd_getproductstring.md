---
UID: NF:hidsdi.HidD_GetProductString
title: HidD_GetProductString function (hidsdi.h)
description: The HidD_GetProductString routine returns the embedded string of a top-level collection that identifies the manufacturer's product.
old-location: hid\hidd_getproductstring.htm
tech.root: hid
ms.assetid: c0627fbf-4b64-4530-8c0f-45326a83f765
ms.date: 06/19/2019
keywords: ["HidD_GetProductString function"]
ms.keywords: HidD_GetProductString, HidD_GetProductString routine [Human Input Devices], hid.hidd_getproductstring, hidfunc_4909c6a7-11b7-489c-915c-889ad3124231.xml, hidsdi/HidD_GetProductString
req.header: hidsdi.h
req.include-header: Hidsdi.h
req.target-type: Universal
req.target-min-winverclnt: Available in Windows 2000 and later versions of Windows.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Hid.lib
req.dll: Hid.dll
req.irql: 
targetos: Windows
req.typenames: 
f1_keywords:
 - HidD_GetProductString
 - hidsdi/HidD_GetProductString
topic_type:
 - APIRef
 - kbSyntax
api_type:
 - DllExport
api_location:
 - Hid.dll
api_name:
 - HidD_GetProductString
---

# HidD_GetProductString function

## -description

The **HidD_GetProductString** routine returns the embedded string of a [top-level collection](/windows-hardware/drivers/hid/top-level-collections) that identifies the manufacturer's product.

## -parameters

### -param HidDeviceObject [in]


Specifies an open handle to a top-level collection.

### -param Buffer [out]


Pointer to a caller-allocated buffer that the routine uses to return the requested product string. The routine returns a NULL-terminated wide character string.

### -param BufferLength [in]


Specifies the length, in bytes, of a caller-allocated buffer provided at *Buffer*. If the buffer is not large enough to return the entire NULL-terminated embedded string, the routine returns nothing in the buffer. The supplied buffer must be <= 4093 bytes (2^12 – 3).

## -returns

**HidD_GetProductString** returns **TRUE** if it successfully returns the entire NULL-terminated embedded string. Otherwise, the routine returns **FALSE**. Use [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) to get extended error information.

## -remarks

Only user-mode applications can call **HidD_GetProductString**. Kernel-mode drivers can use an [IOCTL_HID_GET_PRODUCT_STRING](../hidclass/ni-hidclass-ioctl_hid_get_product_string.md) request.

The maximum possible number of characters in an embedded string is device specific. For USB devices, the maximum string length is 126 wide characters (not including the terminating NULL character).

The **iProduct** member of a [USB_DEVICE_DESCRIPTOR](../usbspec/ns-usbspec-_usb_device_descriptor.md) structure for a particular interface is set by the [USB common class generic parent driver](../index.yml) based on the following rules:

- If the **iInterface** member of the [USB_INTERFACE_DESCRIPTOR](../usbspec/ns-usbspec-_usb_interface_descriptor.md) structure for the interface is nonzero, the **iProduct** member of the USB_DEVICE_DESCRIPTOR structure for the interface is set to the **iInterface** member of the USB_INTERFACE_DESCRIPTOR structure.

- If the interface is grouped by a [USB interface association descriptor](../index.yml) and the **iFunction** member of the interface association descriptor for the interface is nonzero, the **iProduct** member of the USB_DEVICE_DESCRIPTOR structure for the interface is set to the **iFunction** member of the interface association descriptor.

If the supplied buffer is not <= 4093 bytes (2^12 – 3) the call may fail (depending on the underlying protocol, HID/Bluetooth/SPI) with error code ERROR_GEN_FAILURE (0x0000001f)

For more information, see [HID Collections](/windows-hardware/drivers/hid/hid-collections).

## -see-also

[HidD_GetIndexedString](./nf-hidsdi-hidd_getindexedstring.md)

[HidD_GetPhysicalDescriptor](./nf-hidsdi-hidd_getphysicaldescriptor.md)

[HidD_GetSerialNumberString](./nf-hidsdi-hidd_getserialnumberstring.md)

[IOCTL_HID_GET_INDEXED_STRING](../hidclass/ni-hidclass-ioctl_hid_get_indexed_string.md)

[IOCTL_HID_GET_MANUFACTURER_STRING](../hidclass/ni-hidclass-ioctl_hid_get_manufacturer_string.md)

[IOCTL_HID_GET_PRODUCT_STRING](../hidclass/ni-hidclass-ioctl_hid_get_product_string.md)

[IOCTL_HID_GET_SERIALNUMBER_STRING](../hidclass/ni-hidclass-ioctl_hid_get_serialnumber_string.md)
