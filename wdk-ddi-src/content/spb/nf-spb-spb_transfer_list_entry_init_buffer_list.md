---
UID: NF:spb.SPB_TRANSFER_LIST_ENTRY_INIT_BUFFER_LIST
title: SPB_TRANSFER_LIST_ENTRY_INIT_BUFFER_LIST function (spb.h)
description: The SPB_TRANSFER_LIST_ENTRY_INIT_BUFFER_LIST function returns an SPB_TRANSFER_LIST_ENTRY structure that is initialized to describe a scatter-gather list.SPB_TRANSFER_LIST_ENTRY_INIT_BUFFER_LIST function returns an SPB_TRANSFER_LIST_ENTRY structure that is initialized to describe a scatter-gather list.
old-location: spb\spb_transfer_list_entry_init_buffer_list.htm
tech.root: SPB
ms.date: 04/30/2018
keywords: ["SPB_TRANSFER_LIST_ENTRY_INIT_BUFFER_LIST function"]
ms.keywords: SPB.spb_transfer_list_entry_init_buffer_list, SPB_TRANSFER_LIST_ENTRY_INIT_BUFFER_LIST, SPB_TRANSFER_LIST_ENTRY_INIT_BUFFER_LIST function [Buses], spb/SPB_TRANSFER_LIST_ENTRY_INIT_BUFFER_LIST
req.header: spb.h
req.include-header: 
req.target-type: Desktop
req.target-min-winverclnt: 
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
req.lib: 
req.dll: 
req.irql: Any IRQL
targetos: Windows
req.typenames: 
f1_keywords:
 - SPB_TRANSFER_LIST_ENTRY_INIT_BUFFER_LIST
 - spb/SPB_TRANSFER_LIST_ENTRY_INIT_BUFFER_LIST
topic_type:
 - APIRef
 - kbSyntax
api_type:
 - HeaderDef
api_location:
 - Spb.h
api_name:
 - SPB_TRANSFER_LIST_ENTRY_INIT_BUFFER_LIST
---

# SPB_TRANSFER_LIST_ENTRY_INIT_BUFFER_LIST function


## -description

The <b>SPB_TRANSFER_LIST_ENTRY_INIT_BUFFER_LIST</b> function returns an <a href="/windows-hardware/drivers/ddi/spb/ns-spb-spb_transfer_list_entry">SPB_TRANSFER_LIST_ENTRY</a> structure that is initialized to describe a scatter-gather list.

## -parameters

### -param Direction [in]


The direction of the transfer. The function writes this value to the <b>Direction</b> member of the <b>SPB_TRANSFER_LIST_ENTRY</b> structure.

### -param DelayInUs [in]


An optional delay in microseconds. The function writes this value to the <b>DelayInUs</b> member of the <b>SPB_TRANSFER_LIST_ENTRY</b> structure.

### -param BufferList [in]


A pointer to an array of <a href="/windows-hardware/drivers/ddi/spb/ns-spb-spb_transfer_buffer_list_entry">SPB_TRANSFER_BUFFER_LIST_ENTRY</a> structures that describes a scatter-gather list. The function writes this value to the <b>Buffer.BufferList.List</b> member of the <b>SPB_TRANSFER_LIST_ENTRY</b> structure. For more information, see the description of the <b>BufferList.List</b> member in <a href="/windows-hardware/drivers/ddi/spb/ns-spb-spb_transfer_buffer">SPB_TRANSFER_BUFFER</a>.

### -param BufferListCe [in]


The number of buffers in the scatter-gather list pointed to by <i>BufferList</i>. The function writes this value to the <b>Buffer.BufferList.ListCe</b> member of the <b>SPB_TRANSFER_LIST_ENTRY</b> structure. For more information, see the description of the <b>BufferList.ListCe</b> member in <a href="/windows-hardware/drivers/ddi/spb/ns-spb-spb_transfer_buffer">SPB_TRANSFER_BUFFER</a>.

## -returns

<b>SPB_TRANSFER_LIST_ENTRY_INIT_BUFFER_LIST</b> returns an initialized <b>SPB_TRANSFER_LIST_ENTRY</b> structure.

## -remarks

This initialization function returns an unnamed local variable of type <b>SPB_TRANSFER_LIST_ENTRY</b>. The storage for this variable is allocated in the caller's stack frame and is valid while the stack frame remains in scope.

<b>SPB_TRANSFER_LIST_ENTRY_INIT_BUFFER_LIST</b> sets the <b>Buffer.Format</b> member of the  <b>SPB_TRANSFER_LIST_ENTRY</b> structure to <b>SpbTransferBufferFormatList</b>. For more information about buffer formats, see <a href="/windows-hardware/drivers/ddi/spb/ne-spb-spb_transfer_buffer_format">SPB_TRANSFER_BUFFER_FORMAT</a>.

## -see-also

<a href="/windows-hardware/drivers/ddi/spb/ns-spb-spb_transfer_buffer">SPB_TRANSFER_BUFFER</a>



<a href="/windows-hardware/drivers/ddi/spb/ne-spb-spb_transfer_buffer_format">SPB_TRANSFER_BUFFER_FORMAT</a>



<a href="/windows-hardware/drivers/ddi/spb/ns-spb-spb_transfer_buffer_list_entry">SPB_TRANSFER_BUFFER_LIST_ENTRY</a>



<a href="/windows-hardware/drivers/ddi/spb/ns-spb-spb_transfer_list_entry">SPB_TRANSFER_LIST_ENTRY</a>
