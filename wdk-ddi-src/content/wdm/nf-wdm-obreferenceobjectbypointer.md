---
UID: NF:wdm.ObReferenceObjectByPointer
title: ObReferenceObjectByPointer function (wdm.h)
description: The ObReferenceObjectByPointer routine increments the pointer reference count for a given object.
old-location: kernel\obreferenceobjectbypointer.htm
tech.root: kernel
ms.date: 04/30/2018
keywords: ["ObReferenceObjectByPointer function"]
ms.keywords: ObReferenceObjectByPointer, ObReferenceObjectByPointer routine [Kernel-Mode Driver Architecture], k107_2846f148-4ad5-472a-aa74-4f03c5251aee.xml, kernel.obreferenceobjectbypointer, wdm/ObReferenceObjectByPointer
req.header: wdm.h
req.include-header: Wdm.h, Ntddk.h, Ntifs.h
req.target-type: Universal
req.target-min-winverclnt: Available starting with Windows 2000.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.ddi-compliance: TargetRelationNeedsRef, HwStorPortProhibitedDDIs
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: NtosKrnl.lib
req.dll: NtosKrnl.exe
req.irql: <= DISPATCH_LEVEL
targetos: Windows
req.typenames: 
f1_keywords:
 - ObReferenceObjectByPointer
 - wdm/ObReferenceObjectByPointer
topic_type:
 - APIRef
 - kbSyntax
api_type:
 - DllExport
api_location:
 - NtosKrnl.exe
api_name:
 - ObReferenceObjectByPointer
---

# ObReferenceObjectByPointer function


## -description

The <b>ObReferenceObjectByPointer</b> routine increments the pointer reference count for a given object.

## -parameters

### -param Object [in]


Pointer to the object's body.

### -param DesiredAccess [in]


Specifies a mask representing the requested access to the object.

### -param ObjectType [in, optional]


Pointer to the object type. <i>ObjectType</i> can be <b>*ExEventObjectType</b>, <b>*ExSemaphoreObjectType</b>, <b>*IoFileObjectType</b>, <b>*PsProcessType</b>, <b>*PsThreadType</b>, <b>*SeTokenObjectType</b>, <b>*TmEnlistmentObjectType</b>, <b>*TmResourceManagerObjectType</b>, <b>*TmTransactionManagerObjectType</b>, or <b>*TmTransactionObjectType</b>. 

<div class="alert"><b>Note</b>    The <b>SeTokenObjectType</b> object type is supported in Windows XP and later versions of Windows.</div>
<div> </div>
This parameter can also be <b>NULL</b> if <i>AccessMode</i> is <b>KernelMode</b>.

### -param AccessMode [in]


Indicates the access mode to use for the access check. It must be either <b>UserMode</b> or <b>KernelMode</b>. Lower-level drivers should specify <b>KernelMode</b>.

## -returns

<b>ObReferenceObjectByPointer</b> returns STATUS_SUCCESS when the routine has successfully incremented the reference count of the target object's body. The routine performs object type validation if the call is being performed in user mode and if the type requested by the caller doesn't match with the one from the object's body, STATUS_OBJECT_TYPE_MISMATCH is returned.
The same NTSTATUS code is returned if the requested type is a symbolic link type (<b>ObpSymbolicLinkObjectType</b>) which is not allowed by the routine, regardless of what kind of access mode is.

## -remarks

Calling this routine prevents the object from being deleted, possibly by another component's call to <a href="/windows-hardware/drivers/ddi/wdm/nf-wdm-obdereferenceobject">ObDereferenceObject</a> or <a href="/windows-hardware/drivers/ddi/ntifs/nf-ntifs-ntclose">ZwClose</a>. The caller must decrement the reference count with <b>ObDereferenceObject</b> as soon as it is done with the object.

## -see-also

<a href="/windows-hardware/drivers/ddi/wdm/nf-wdm-obdereferenceobject">ObDereferenceObject</a>



<a href="/windows-hardware/drivers/ddi/wdm/nf-wdm-obfreferenceobject">ObReferenceObject</a>



<a href="/windows-hardware/drivers/ddi/wdm/nf-wdm-obreferenceobjectbyhandle">ObReferenceObjectByHandle</a>



<a href="/windows-hardware/drivers/ddi/ntifs/nf-ntifs-ntclose">ZwClose</a>
