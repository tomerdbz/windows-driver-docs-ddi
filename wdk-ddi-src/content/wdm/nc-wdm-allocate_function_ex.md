---
UID: NC:wdm.ALLOCATE_FUNCTION_EX
title: ALLOCATE_FUNCTION_EX (wdm.h)
description: The LookasideListAllocateEx routine allocates the storage for a new lookaside-list entry when a client requests an entry from a lookaside list that is empty.
old-location: kernel\lookasidelistallocateex.htm
tech.root: kernel
ms.date: 04/30/2018
keywords: ["ALLOCATE_FUNCTION_EX callback function"]
ms.keywords: ALLOCATE_FUNCTION_EX, DrvrRtns_a8e59075-4ed4-49d3-a516-6cee5b6390c8.xml, LookasideListAllocateEx, LookasideListAllocateEx routine [Kernel-Mode Driver Architecture], kernel.lookasidelistallocateex, wdm/LookasideListAllocateEx
req.header: wdm.h
req.include-header: Wdm.h, Ntddk.h, Ntifs.h
req.target-type: Desktop
req.target-min-winverclnt: Supported in Windows Vista and later versions of Windows.
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
req.irql: See Remarks section.
targetos: Windows
req.typenames: 
f1_keywords:
 - ALLOCATE_FUNCTION_EX
 - wdm/ALLOCATE_FUNCTION_EX
topic_type:
 - APIRef
 - kbSyntax
api_type:
 - UserDefined
api_location:
 - Wdm.h
api_name:
 - ALLOCATE_FUNCTION_EX
---

# ALLOCATE_FUNCTION_EX callback function


## -description

The <i>LookasideListAllocateEx</i> routine allocates the storage for a new lookaside-list entry when a client requests an entry from a lookaside list that is empty.

## -parameters

### -param PoolType [in]


Specifies the type of storage to allocate for the new lookaside-list entry. The caller sets this parameter to a valid <a href="/windows-hardware/drivers/ddi/wdm/ne-wdm-_pool_type">POOL_TYPE</a> enumeration value, and possibly bitwise ORs this value with one of the following flag bits:

<ul>
<li>POOL_RAISE_IF_ALLOCATION_FAILURE</li>
<li>POOL_QUOTA_FAIL_INSTEAD_OF_RAISE</li>
</ul>
For more information about the POOL_RAISE_IF_ALLOCATION_FAILURE flag, see <a href="/windows-hardware/drivers/ddi/wdm/nf-wdm-exallocatepoolwithtag">ExAllocatePoolWithTag</a>. For more information about the POOL_QUOTA_FAIL_INSTEAD_OF_RAISE flag, see <a href="/windows-hardware/drivers/ddi/wdm/nf-wdm-exallocatepoolwithquotatag">ExAllocatePoolWithQuotaTag</a>.

If, in the <a href="/windows-hardware/drivers/ddi/wdm/nf-wdm-exinitializelookasidelistex">ExInitializeLookasideListEx</a> call that initialized the lookaside list, the <i>Flags</i> parameter is zero, the <i>PoolType</i> parameter that the <i>LookasideListAllocateEx</i> routine receives is the same <i>PoolType</i> parameter value that was passed to <b>ExInitializeLookasideListEx</b>.

If, in the <b>ExInitializeLookasideListEx</b> call, <i>Flags</i> = EX_LOOKASIDE_LIST_EX_FLAGS_RAISE_ON_FAIL, the <i>PoolType</i> parameter that the <i>LookasideListAllocateEx</i> routine receives is the bitwise OR of POOL_RAISE_IF_ALLOCATION_FAILURE and the <i>PoolType</i> parameter value that was passed to <b>ExInitializeLookasideListEx</b>. The <i>LookasideListAllocateEx</i> routine can pass its <i>PoolType</i> parameter value, without modification, to the <b>ExAllocatePoolWithTag</b> routine. 

If, in the <b>ExInitializeLookasideListEx</b> call, Flags = EX_LOOKASIDE_LIST_EX_FLAGS_FAIL_NO_RAISE, the <i>PoolType</i> parameter that the <i>LookasideListAllocateEx</i> routine receives is the bitwise OR of POOL_QUOTA_FAIL_INSTEAD_OF_RAISE and the <i>PoolType</i> value that was passed to <b>ExInitializeLookasideListEx</b>.  The <i>LookasideListAllocateEx</i> routine can pass its <i>PoolType</i> parameter value, without modification, to the <b>ExAllocatePoolWithQuotaTag</b> routine.

### -param NumberOfBytes [in]


Specifies the size, in bytes, of the lookaside-list entry to allocate.

### -param Tag [in]


Specifies the four-byte pool tag to use to mark the allocated storage for the new lookaside-list entry. For more information about pool tags, see the description of the <i>Tag</i> parameter in <a href="/windows-hardware/drivers/ddi/wdm/nf-wdm-exallocatepoolwithtag">ExAllocatePoolWithTag</a>.

### -param Lookaside [in, out]


A pointer to a <a href="/windows-hardware/drivers/kernel/eprocess">LOOKASIDE_LIST_EX</a> structure that describes the lookaside list. This structure was previously initialized by the <a href="/windows-hardware/drivers/ddi/wdm/nf-wdm-exinitializelookasidelistex">ExInitializeLookasideListEx</a> routine.

## -returns

<i>LookasideListAllocateEx</i> returns a pointer to the allocated lookaside-list entry. If the routine cannot allocate an entry, it returns <b>NULL</b>.

## -remarks

A driver that creates a lookaside list can implement a <i>LookasideListAllocateEx</i> routine to dynamically allocate buffers for the list. A buffer that is not in use is stored as an entry in the list. All entries in a lookaside list are buffers of a uniform size, which the driver specifies when the list is initialized.

The driver supplies a pointer to a custom <i>LookasideListAllocateEx</i> routine as an input parameter in the <b>ExInitializeLookasideListEx</b> call that initializes the lookaside list. If the driver sets this parameter to <b>NULL</b>, the lookaside list uses a default allocation routine instead.

A driver calls the <a href="/windows-hardware/drivers/ddi/wdm/nf-wdm-exallocatefromlookasidelistex">ExAllocateFromLookasideListEx</a> routine to allocate an entry from a lookaside list. If the list is empty (contains no entries), <b>ExAllocateFromLookasideListEx</b> calls <i>LookasideListAllocateEx</i> to dynamically allocate the storage for a new entry. <i>LookasideListAllocateEx</i> returns a pointer to the newly allocated entry if the allocation is successful. Otherwise, it returns <b>NULL</b>.

The <i>PoolType</i>, <i>NumberOfBytes</i>, <i>Tag</i>, and <i>Lookaside</i> parameters contain the same values that were passed as input parameters in the <b>ExInitializeLookasideListEx</b> call that initialized the lookaside list.

The <i>LookasideListAllocateEx</i> routine can use the <i>Lookaside</i> parameter to access private context data that the driver has associated with the lookaside list. For more information, see the code example in <a href="/windows-hardware/drivers/ddi/wdm/nf-wdm-exinitializelookasidelistex">ExInitializeLookasideListEx</a>.

For more information about lookaside lists, see <a href="/windows-hardware/drivers/kernel/using-lookaside-lists">Using Lookaside Lists</a>.

The <i>LookasideListAllocateEx</i> routine is called at the same IRQL as the call to <b>ExAllocateFromLookasideListEx</b> that requests the entry. For a call that requests an entry that resides in paged memory, the caller must be running IRQL <= APC_LEVEL. For a call that requests an entry that resides in nonpaged memory, the caller must be running IRQL <= DISPATCH_LEVEL. 


#### Examples

To define a <i>LookasideListAllocateEx</i> callback routine, you must first provide a function declaration that identifies the type of callback routine you're defining. Windows provides a set of callback function types for drivers. Declaring a function using the callback function types helps <a href="/windows-hardware/drivers/devtest/code-analysis-for-drivers">Code Analysis for Drivers</a>, <a href="/windows-hardware/drivers/devtest/static-driver-verifier">Static Driver Verifier</a> (SDV), and other verification tools find errors, and it's a requirement for writing drivers for the Windows operating system.

For example, to define a <i>LookasideListAllocateEx</i> callback routine that is named <code>MyLookasideListAllocateEx</code>, use the FREE_FUNCTION_EX type as shown in this code example:


```
FREE_FUNCTION_EX MyLookasideListFreeEx;
```

Then, implement your callback routine as follows:


```
_Use_decl_annotations_
VOID
  MyLookasideListFreeEx(
    PVOID  Buffer,
    PLOOKASIDE_LIST_EX  Lookaside
    )
  {
      // Function body
  }
```

The FREE_FUNCTION_EX function type is defined in the Wdm.h header file. To more accurately identify errors when you run the code analysis tools, be sure to add the _Use_decl_annotations_ annotation to your function definition. The _Use_decl_annotations_ annotation ensures that the annotations that are applied to the FREE_FUNCTION_EX function type in the header file are used. For more information about the requirements for function declarations, see <a href="/windows-hardware/drivers/devtest/declaring-functions-using-function-role-types-for-wdm-drivers">Declaring Functions by Using Function Role Types for WDM Drivers</a>. For information about _Use_decl_annotations_, see <a href="/visualstudio/code-quality/annotating-function-behavior">Annotating Function Behavior</a>.

<div class="code"></div>

## -see-also

<a href="/windows-hardware/drivers/ddi/wdm/nf-wdm-exallocatefromlookasidelistex">ExAllocateFromLookasideListEx</a>



<a href="/windows-hardware/drivers/ddi/wdm/nf-wdm-exallocatepoolwithquotatag">ExAllocatePoolWithQuotaTag</a>



<a href="/windows-hardware/drivers/ddi/wdm/nf-wdm-exallocatepoolwithtag">ExAllocatePoolWithTag</a>



<a href="/windows-hardware/drivers/ddi/wdm/nf-wdm-exinitializelookasidelistex">ExInitializeLookasideListEx</a>



<a href="/windows-hardware/drivers/kernel/eprocess">LOOKASIDE_LIST_EX</a>



<a href="/windows-hardware/drivers/ddi/wdm/ne-wdm-_pool_type">POOL_TYPE</a>

