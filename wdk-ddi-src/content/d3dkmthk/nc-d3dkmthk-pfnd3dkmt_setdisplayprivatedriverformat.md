---
UID: NC:d3dkmthk.PFND3DKMT_SETDISPLAYPRIVATEDRIVERFORMAT
title: PFND3DKMT_SETDISPLAYPRIVATEDRIVERFORMAT
author: windows-driver-content
description: The PFND3DKMT_SETDISPLAYPRIVATEDRIVERFORMAT callback function changes the private-format attribute of a video present source.
ms.assetid: 4d9010e6-7243-420a-933d-330cfca11f89
ms.author: windowsdriverdev
ms.date: 
ms.topic: callback
ms.prod: windows-hardware
ms.technology: windows-devices
req.header: d3dkmthk.h
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
topic_type: 
-	apiref
api_type: 
-	UserDefined
api_location: 
-	d3dkmthk.h
api_name: 
-	PFND3DKMT_SETDISPLAYPRIVATEDRIVERFORMAT
product:
-	Windows
targetos: Windows
---

# PFND3DKMT_SETDISPLAYPRIVATEDRIVERFORMAT callback function

## -description

The PFND3DKMT_SETDISPLAYPRIVATEDRIVERFORMAT callback function changes the private-format attribute of a video present source.

## -prototype

```
//Declaration

PFND3DKMT_SETDISPLAYPRIVATEDRIVERFORMAT Pfnd3dkmtSetdisplayprivatedriverformat; 

// Definition

NTSTATUS Pfnd3dkmtSetdisplayprivatedriverformat 
(
	const D3DKMT_SETDISPLAYPRIVATEDRIVERFORMAT *
)
{...}

```

## -parameters

### -param * 

Pointer to a [D3DKMT_SETDISPLAYPRIVATEDRIVERFORMAT](ns-d3dkmthk-_d3dkmt_setdisplayprivatedriverformat.md) structure.

## -returns

Returns NTSTATUS.


## -remarks




## -see-also