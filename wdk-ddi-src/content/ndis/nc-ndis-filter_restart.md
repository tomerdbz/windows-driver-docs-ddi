---
UID: NC:ndis.FILTER_RESTART
title: FILTER_RESTART (ndis.h)
description: The FilterRestart function initiates a restart operation for the specified filter module.Note  You must declare the function by using the FILTER_RESTART type.
old-location: netvista\filterrestart.htm
tech.root: netvista
ms.date: 05/02/2018
keywords: ["FILTER_RESTART callback function"]
ms.keywords: FILTER_RESTART, FILTER_RESTART callback, FilterRestart, FilterRestart callback function [Network Drivers Starting with Windows Vista], filter_functions_ref_784a21e4-a3d3-4ada-9555-b712595f0a24.xml, ndis/FilterRestart, netvista.filterrestart
req.header: ndis.h
req.include-header: Ndis.h
req.target-type: Windows
req.target-min-winverclnt: Supported in NDIS 6.0 and later.
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
req.irql: PASSIVE_LEVEL
targetos: Windows
req.typenames: 
f1_keywords:
 - FILTER_RESTART
 - ndis/FILTER_RESTART
topic_type:
 - APIRef
 - kbSyntax
api_type:
 - UserDefined
api_location:
 - Ndis.h
api_name:
 - FILTER_RESTART
---

# FILTER_RESTART callback function


## -description

The 
  <i>FilterRestart</i> function initiates a restart operation for the specified filter module.
<div class="alert"><b>Note</b>  You must declare the function by using the <b>FILTER_RESTART</b> type. For more
   information, see the following Examples section.</div><div> </div>

## -parameters

### -param FilterModuleContext [in]


A handle to the context area for the filter module that the filter driver should restart. The
     filter driver created and initialized this context area in the 
     <a href="/windows-hardware/drivers/ddi/ndis/nc-ndis-filter_attach">FilterAttach</a> function.

### -param RestartParameters

### -param FilterRestartParameters 
[in]
A pointer to an 
     <a href="/windows-hardware/drivers/ddi/ndis/ns-ndis-_ndis_filter_restart_parameters">
     NDIS_FILTER_RESTART_PARAMETERS</a> structure that defines the restart parameters for the filter
     module.

## -returns

<i>FilterRestart</i> returns one of the following status values:

<table>
<tr>
<th>Return code</th>
<th>Description</th>
</tr>
<tr>
<td width="40%">
<dl>
<dt><b>NDIS_STATUS_SUCCESS</b></dt>
</dl>
</td>
<td width="60%">
<i>FilterRestart</i> successfully restarted the specified filter module.

</td>
</tr>
<tr>
<td width="40%">
<dl>
<dt><b>NDIS_STATUS_PENDING</b></dt>
</dl>
</td>
<td width="60%">
The filter driver will complete the request asynchronously with a call to the 
       <a href="/windows-hardware/drivers/ddi/ndis/nf-ndis-ndisfrestartcomplete">NdisFRestartComplete</a> function
       after it completes the restart operation.

</td>
</tr>
<tr>
<td width="40%">
<dl>
<dt><b>NDIS_STATUS_RESOURCES</b></dt>
</dl>
</td>
<td width="60%">
<i>FilterRestart</i> failed because of insufficient resources.

</td>
</tr>
<tr>
<td width="40%">
<dl>
<dt><b>NDIS_STATUS_FAILURE</b></dt>
</dl>
</td>
<td width="60%">
None of the preceding status values applies. The filter driver should call the 
       <a href="/windows-hardware/drivers/ddi/ndis/nf-ndis-ndiswriteeventlogentry">NdisWriteEventLogEntry</a> function
       together with parameters that specify the reason for the failure.

</td>
</tr>
</table>

## -remarks

<i>FilterRestart</i> is a required function for filter drivers. NDIS can call 
    <i>FilterRestart</i> when a filter module is in the 
    <i>Paused</i> state. The filter module enters the 
    <i>Restarting</i> state at the start of the execution of 
    <i>FilterRestart</i>.

When NDIS calls 
    <i>FilterRestart</i>, a filter driver:

<ul>
<li>
Must complete the operations that are required to restart normal send and receive operations.

</li>
<li>
Optionally reads or writes configuration parameters.

</li>
<li>
Optionally reallocates buffer pools.

</li>
<li>
Optionally modifies the restart attributes that are specified in the 
      <b>RestartAttributes</b> member of the 
      <a href="/windows-hardware/drivers/ddi/ndis/ns-ndis-_ndis_filter_restart_parameters">
      NDIS_FILTER_RESTART_PARAMETERS</a> structure. If the pointer in 
      <b>RestartAttributes</b> is <b>NULL</b>, the filter driver should not modify or add to the restart attributes
      list. If the pointer in 
      <b>RestartAttributes</b> is non-<b>NULL</b>, it points to the first 
      <a href="/windows-hardware/drivers/ddi/ndis/ns-ndis-_ndis_restart_attributes">NDIS_RESTART_ATTRIBUTES</a> structure
      in the list of restart attributes. If a filter driver does not restart, it should not modify any
      attributes.

</li>
<li>
Optionally uses OID requests to query or set information in the underlying drivers. Filter drivers
      should not issue OID requests for information that is already provided in the list of restart
      attributes.

</li>
<li>
Returns NDIS_STATUS_SUCCESS or a failure status.

</li>
</ul>
If a filter driver modifies the list of restart attributes, the filter driver:

<ul>
<li>
Should not modify any media-specific attributes if it does not recognize the OID in the 
      <b>Oid</b> member of the 
      <a href="/windows-hardware/drivers/ddi/ndis/ns-ndis-_ndis_restart_attributes">
      NDIS_RESTART_ATTRIBUTES</a> structure.

</li>
<li>
Can add new media-specific attributes to the list of restart attributes. In this situation, the
      filter driver must allocate a new NDIS_RESTART_ATTRIBUTES structure--for example, with the 
      <a href="/windows-hardware/drivers/ddi/ndis/nf-ndis-ndisallocatememorywithtagpriority">
      NdisAllocateMemoryWithTagPriority</a> function--and provide memory space for the new attributes.
      After propagating the restart attributes to overlying drivers, NDIS frees the attributes memory for
      filter drivers.

</li>
<li>
Can modify the media-specific attributes in the list of restart attributes. If the filter driver
      requires more memory space, it can free the 
      <a href="/windows-hardware/drivers/ddi/ndis/ns-ndis-_ndis_restart_attributes">NDIS_RESTART_ATTRIBUTES</a> structure
      with the 
      <a href="/windows-hardware/drivers/ddi/ndis/nf-ndis-ndisfreememory">NdisFreeMemory</a> function and allocate a
      new structure to contain the modified information. After propagating the restart attributes to
      overlying drivers, NDIS frees the attributes memory for filter drivers.

</li>
<li>
Should, if the 
      <b>Oid</b> member in the NDIS_RESTART_ATTRIBUTES structure is 
      <a href="/windows-hardware/drivers/network/oid-gen-miniport-restart-attributes">
      OID_GEN_MINIPORT_RESTART_ATTRIBUTES</a>, make sure that the 
      <a href="/windows-hardware/drivers/ddi/ndis/ns-ndis-_ndis_restart_general_attributes">
      NDIS_RESTART_GENERAL_ATTRIBUTES</a> structure contains the information that the filter driver
      requires. To make sure that the NDIS_RESTART_GENERAL_ATTRIBUTES structure contains the required
      information, you should check the 
      <b>Revision</b> member in the 
      <a href="/windows-hardware/drivers/ddi/objectheader/ns-objectheader-ndis_object_header">NDIS_OBJECT_HEADER</a> structure that is
      specified in the 
      <b>Header</b> member of the NDIS_RESTART_GENERAL_ATTRIBUTES structure.

<div class="alert"><b>Note</b>  A filter driver can modify any member in the NDIS_RESTART_GENERAL_ATTRIBUTES
      structure. If some attributes that the filter driver should modify are not included in the revision of
      the structure that NDIS provided, the filter driver should rely on overlying drivers to issue OID
      requests for the missing attributes. The filter driver can modify the attributes when it completes the
      OID request.</div>
<div> </div>
</li>
<li>
Must, if the filter driver changes restart attributes, provide a 
      <a href="/windows-hardware/drivers/ddi/ndis/nc-ndis-filter_oid_request">FilterOidRequest</a> function. The
      filter driver must make sure that the information that overlying drivers receive in the restart
      attributes is consistent with the information that they receive in response to OID requests.

</li>
</ul>
After the filter driver returns its status or calls the 
    <a href="/windows-hardware/drivers/ddi/ndis/nf-ndis-ndisfrestartcomplete">NdisFRestartComplete</a> function, the
    restart operation is complete. If the operation completed successfully, the filter module is in the 
    <i>Running</i> state and normal send and receive processing is resumed. If the restart operation failed,
    the filter module returns to the 
    <i>Paused</i> state.

NDIS calls 
    <i>FilterRestart</i> at IRQL = PASSIVE_LEVEL.

<h3><a id="Examples"></a><a id="examples"></a><a id="EXAMPLES"></a>Examples</h3>
To define a <i>FilterRestart</i> function, you must first provide a function declaration that identifies the type of function you're defining. Windows provides a set of function types for drivers. Declaring a function using the function types helps <a href="/windows-hardware/drivers/devtest/code-analysis-for-drivers">Code Analysis for Drivers</a>, <a href="/windows-hardware/drivers/devtest/static-driver-verifier">Static Driver Verifier</a> (SDV), and other verification tools find errors, and it's a requirement for writing drivers for the Windows operating system.

For example, to define a <i>FilterRestart</i> function that is named "MyRestart", use the <b>FILTER_RESTART</b> type as shown in this code example:


```
FILTER_RESTART MyRestart;
```

Then, implement your function as follows:


```
_Use_decl_annotations_
NDIS_STATUS
 MyRestart(
    NDIS_HANDLE  FilterModuleContext,
    PNDIS_FILTER_RESTART_PARAMETERS  FilterRestartParameters
    )
  {...}
```

The <b>FILTER_RESTART</b> function type is defined in the Ndis.h header file. To more accurately identify errors when you run the code analysis tools, be sure to add the _Use_decl_annotations_ annotation to your function definition.  The _Use_decl_annotations_ annotation ensures that the annotations that are applied to the <b>FILTER_RESTART</b> function type in the header file are used.  For more information about the requirements for function declarations, see <a href="/windows-hardware/drivers/devtest/declaring-functions-by-using-function-role-types-for-ndis-drivers">Declaring Functions by Using Function Role Types for NDIS Drivers</a>.

For information about  _Use_decl_annotations_, see <a href="/visualstudio/code-quality/annotating-function-behavior">Annotating Function Behavior</a>.

## -see-also

<a href="/windows-hardware/drivers/ddi/ndis/nc-ndis-filter_attach">FilterAttach</a>



<a href="/windows-hardware/drivers/ddi/ndis/nc-ndis-filter_oid_request">FilterOidRequest</a>



<a href="/windows-hardware/drivers/ddi/ndis/nc-ndis-filter_status">FilterStatus</a>



<a href="/windows-hardware/drivers/ddi/ndis/ns-ndis-_ndis_filter_restart_parameters">
   NDIS_FILTER_RESTART_PARAMETERS</a>



<a href="/windows-hardware/drivers/ddi/objectheader/ns-objectheader-ndis_object_header">NDIS_OBJECT_HEADER</a>



<a href="/windows-hardware/drivers/ddi/ndis/ns-ndis-_ndis_restart_attributes">NDIS_RESTART_ATTRIBUTES</a>



<a href="/windows-hardware/drivers/ddi/ndis/ns-ndis-_ndis_restart_general_attributes">
   NDIS_RESTART_GENERAL_ATTRIBUTES</a>



<a href="/windows-hardware/drivers/network/ndis-status-link-state">NDIS_STATUS_LINK_STATE</a>



<a href="/windows-hardware/drivers/ddi/ndis/nf-ndis-ndisallocatememorywithtagpriority">
   NdisAllocateMemoryWithTagPriority</a>



<a href="/windows-hardware/drivers/ddi/ndis/nf-ndis-ndisfregisterfilterdriver">NdisFRegisterFilterDriver</a>



<a href="/windows-hardware/drivers/ddi/ndis/nf-ndis-ndisfrestartcomplete">NdisFRestartComplete</a>



<a href="/windows-hardware/drivers/ddi/ndis/nf-ndis-ndisfreememory">NdisFreeMemory</a>



<a href="/windows-hardware/drivers/ddi/ndis/nf-ndis-ndiswriteeventlogentry">NdisWriteEventLogEntry</a>



<a href="/windows-hardware/drivers/network/oid-gen-link-state">OID_GEN_LINK_STATE</a>



<a href="/windows-hardware/drivers/network/oid-gen-miniport-restart-attributes">
   OID_GEN_MINIPORT_RESTART_ATTRIBUTES</a>

