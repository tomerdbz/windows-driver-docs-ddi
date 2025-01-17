---
UID: NS:dot11wdi._WDI_MESSAGE_HEADER
title: _WDI_MESSAGE_HEADER (dot11wdi.h)
description: The WDI_MESSAGE_HEADER structure defines the WDI message header. All WDI command messages must start with this header.
old-location: netvista\wdi_message_header.htm
tech.root: netvista
ms.date: 05/02/2018
keywords: ["WDI_MESSAGE_HEADER structure"]
ms.keywords: "*PWDI_MESSAGE_HEADER, PWDI_MESSAGE_HEADER, PWDI_MESSAGE_HEADER structure pointer [Network Drivers Starting with Windows Vista], WDI_MESSAGE_HEADER, WDI_MESSAGE_HEADER structure [Network Drivers Starting with Windows Vista], _WDI_MESSAGE_HEADER, dot11wdi/PWDI_MESSAGE_HEADER, dot11wdi/WDI_MESSAGE_HEADER, netvista.wdi_message_header"
req.header: dot11wdi.h
req.include-header: 
req.target-type: Windows
req.target-min-winverclnt: Windows 10
req.target-min-winversvr: Windows Server 2016
req.kmdf-ver: 
req.umdf-ver: 
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: 
targetos: Windows
req.typenames: WDI_MESSAGE_HEADER, *PWDI_MESSAGE_HEADER
f1_keywords:
 - _WDI_MESSAGE_HEADER
 - dot11wdi/_WDI_MESSAGE_HEADER
 - PWDI_MESSAGE_HEADER
 - dot11wdi/PWDI_MESSAGE_HEADER
 - WDI_MESSAGE_HEADER
 - dot11wdi/WDI_MESSAGE_HEADER
topic_type:
 - APIRef
 - kbSyntax
api_type:
 - HeaderDef
api_location:
 - dot11wdi.h
api_name:
 - _WDI_MESSAGE_HEADER
 - PWDI_MESSAGE_HEADER
 - WDI_MESSAGE_HEADER
---

# _WDI_MESSAGE_HEADER structure


## -description

> [!IMPORTANT]
> This topic is part of the [WDI driver model](/windows-hardware/drivers/network/wdi-miniport-driver-design-guide) released in Windows 10. The WDI driver model is now in maintenance mode and will only receive high priority fixes. [WiFiCx](/windows-hardware/drivers/netcx/wifi-wdf-class-extension-wificx) is the Wi-Fi driver model released in Windows 11. We recommend that you use WiFiCx to take advantage of the latest  features. 

The WDI_MESSAGE_HEADER structure defines the WDI message header. All WDI  command messages must start with this header.## -struct-fields

### -field PortId

Specifies the identifier for the Port object that this command is targeted for. For commands on the Adapter object, this is 0xFFFF.

### -field Reserved

This member is reserved.

### -field Status

Specifies the operation completion status for output messages. For input messages, this field is reserved.

### -field TransactionId

Specifies the transaction ID. This value is used to match host-sent messages with function responses.  This value must be unique among all outstanding transactions.  For notifications, the TransactionId must be set to 0 by the function.

### -field IhvSpecificId

Specifies an IHV-specific ID for this message. This can be used by IHVs for debugging purpose.

