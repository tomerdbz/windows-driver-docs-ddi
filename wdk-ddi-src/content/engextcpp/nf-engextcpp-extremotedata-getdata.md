---
UID: NF:engextcpp.ExtRemoteData.GetData
title: ExtRemoteData::GetData (engextcpp.h)
description: The GetData method returns the contents of the target's memory, represented by the ExtRemoteData object.
old-location: debugger\extremotedata_getdata.htm
tech.root: debugger
ms.date: 05/03/2018
keywords: ["ExtRemoteData::GetData"]
ms.keywords: EngExtCpp_Ref_a440fb76-5d7c-4e77-9d1e-61c0b7002493.xml, ExtRemoteData class [Windows Debugging],GetData method, ExtRemoteData.GetData, ExtRemoteData::GetData, GetData, GetData method [Windows Debugging], GetData method [Windows Debugging],ExtRemoteData class, debugger.extremotedata_getdata
req.header: engextcpp.hpp
req.include-header: Engextcpp.hpp
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
req.irql: 
targetos: Windows
req.typenames: 
f1_keywords:
 - ExtRemoteData::GetData
 - engextcpp/ExtRemoteData::GetData
topic_type:
 - APIRef
 - kbSyntax
api_type:
 - COM
api_location:
 - engextcpp.hpp
api_name:
 - ExtRemoteData::GetData
---

# ExtRemoteData::GetData


## -description

The <b>GetData</b> method returns the contents of the target's memory, represented by the <a href="/windows-hardware/drivers/ddi/engextcpp/nf-engextcpp-extremotedata-extremotedata(pcstr_ulong64_ulong)">ExtRemoteData</a> object.

## -parameters

### -param Request [in]


Number of bytes requested.  This must be the same as the size of the memory specified by the <a href="/windows-hardware/drivers/ddi/engextcpp/nf-engextcpp-extremotedata-extremotedata">ExtRemoteData::ExtRemoteData</a> constructor or the <a href="/windows-hardware/drivers/ddi/engextcpp/nf-engextcpp-extremotedata-set(constdebug_typed_data)">ExtRemoteData::Set(Typed)</a> or <a href="/windows-hardware/drivers/ddi/engextcpp/nf-engextcpp-extremotedata-set">ExtRemoteData::Set(Offset Bytes)</a> methods.  If it is not the same, <b>ExtRemoteException</b> is thrown.

## -returns

<b>GetData</b> returns the cached contents of the target's memory, represented by the <a href="/windows-hardware/drivers/ddi/engextcpp/nf-engextcpp-extremotedata-extremotedata(pcstr_ulong64_ulong)">ExtRemoteData</a> object.

## -remarks

The contents of the region of memory represented by an <a href="/windows-hardware/drivers/ddi/engextcpp/nf-engextcpp-extremotedata-extremotedata(pcstr_ulong64_ulong)">ExtRemoteData</a> object are only cached if the size of the region is less than 8 bytes.  If the size of the region is greater than 8 bytes, the <b>GetData</b> method does not return a meaningful value.

A number of convenience methods are available for various primitive types. These methods will automatically provide the size of the type and cast the return value to that type.  These methods are listed in the See Also section.

## -see-also

<a href="/windows-hardware/drivers/ddi/engextcpp/nf-engextcpp-extremotedata-extremotedata(pcstr_ulong64_ulong)">ExtRemoteData</a>



<a href="/windows-hardware/drivers/ddi/engextcpp/nf-engextcpp-extremotedata-extremotedata">ExtRemoteData::ExtRemoteData</a>



<a href="/windows-hardware/drivers/ddi/engextcpp/nf-engextcpp-extremotedata-set">ExtRemoteData::Set(Offset Bytes)</a>



<a href="/windows-hardware/drivers/ddi/engextcpp/nf-engextcpp-extremotedata-set(constdebug_typed_data)">ExtRemoteData::Set(Typed)</a>



<a href="/windows-hardware/drivers/ddi/engextcpp/nf-engextcpp-extremotedata-getboolean">GetBoolean</a>



<a href="/windows-hardware/drivers/ddi/engextcpp/nf-engextcpp-extremotedata-getchar">GetChar</a>



<a href="/windows-hardware/drivers/ddi/engextcpp/nf-engextcpp-extremotedata-getdouble">GetDouble</a>



<a href="/windows-hardware/drivers/ddi/engextcpp/nf-engextcpp-extremotedata-getfloat">GetFloat</a>



<a href="/windows-hardware/drivers/ddi/engextcpp/nf-engextcpp-extremotedata-getlong">GetLong</a>



<a href="/windows-hardware/drivers/ddi/engextcpp/nf-engextcpp-extremotedata-getlong64">GetLong64</a>



<a href="/windows-hardware/drivers/ddi/engextcpp/nf-engextcpp-extremotedata-getlongptr">GetLongPtr</a>



<a href="/windows-hardware/drivers/ddi/engextcpp/nf-engextcpp-extremotedata-getptr">GetPtr</a>



<a href="/windows-hardware/drivers/ddi/engextcpp/nf-engextcpp-extremotedata-getshort">GetShort</a>



<a href="/windows-hardware/drivers/ddi/engextcpp/nf-engextcpp-extremotedata-getstdbool">GetStdBool</a>



<a href="/windows-hardware/drivers/ddi/engextcpp/nf-engextcpp-extremotedata-getuchar">GetUchar</a>



<a href="/windows-hardware/drivers/ddi/extsfns/nf-extsfns-idebugfailureanalysis2-getulong">GetUlong</a>



<a href="/windows-hardware/drivers/ddi/extsfns/nf-extsfns-idebugfailureanalysis2-getulong64">GetUlong64</a>



<a href="/windows-hardware/drivers/ddi/engextcpp/nf-engextcpp-extremotedata-getulongptr">GetUlongPtr</a>



<a href="/windows-hardware/drivers/ddi/engextcpp/nf-engextcpp-extremotedata-getushort">GetUshort</a>



<a href="/windows-hardware/drivers/ddi/engextcpp/nf-engextcpp-extremotedata-getw32bool">GetW32Bool</a>

