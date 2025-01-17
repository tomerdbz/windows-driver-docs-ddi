---
UID: NE:ucmtypes._UCM_TYPEC_PARTNER
title: _UCM_TYPEC_PARTNER (ucmtypes.h)
description: Defines the state of the Type-C connector.
old-location: buses\ucm_type_c_port_state.htm
tech.root: usbref
ms.date: 05/07/2018
keywords: ["UCM_TYPEC_PARTNER enumeration"]
ms.keywords: UCM_TYPEC_PARTNER, UCM_TYPEC_PARTNER enumeration [Buses], UcmTypeCPartnerStateAudioAccessory, UcmTypeCPartnerStateDebugAccessory, UcmTypeCPartnerStateDfp, UcmTypeCPartnerStateInvalid, UcmTypeCPartnerStatePoweredCableNoUfp, UcmTypeCPartnerStatePoweredCableWithUfp, UcmTypeCPartnerStateUfp, _UCM_TYPEC_PARTNER, buses.ucm_type_c_port_state, ucmtypes/UCM_TYPEC_PARTNER, ucmtypes/UcmTypeCPartnerStateAudioAccessory, ucmtypes/UcmTypeCPartnerStateDebugAccessory, ucmtypes/UcmTypeCPartnerStateDfp, ucmtypes/UcmTypeCPartnerStateInvalid, ucmtypes/UcmTypeCPartnerStatePoweredCableNoUfp, ucmtypes/UcmTypeCPartnerStatePoweredCableWithUfp, ucmtypes/UcmTypeCPartnerStateUfp
req.header: ucmtypes.h
req.include-header: Ucmcx.h
req.target-type: Windows
req.target-min-winverclnt: Windows 10
req.target-min-winversvr: Windows Server 2016
req.kmdf-ver: 1.15
req.umdf-ver: 2.15
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
req.typenames: UCM_TYPEC_PARTNER
f1_keywords:
 - _UCM_TYPEC_PARTNER
 - ucmtypes/_UCM_TYPEC_PARTNER
 - UCM_TYPEC_PARTNER
 - ucmtypes/UCM_TYPEC_PARTNER
topic_type:
 - APIRef
 - kbSyntax
api_type:
 - HeaderDef
api_location:
 - Ucmtypes.h
api_name:
 - _UCM_TYPEC_PARTNER
 - UCM_TYPEC_PARTNER
---

# _UCM_TYPEC_PARTNER enumeration


## -description

Defines the state of the Type-C connector.

## -enum-fields

### -field UcmTypeCPartnerInvalid

### -field UcmTypeCPartnerUfp

### -field UcmTypeCPartnerDfp

### -field UcmTypeCPartnerPoweredCableNoUfp

### -field UcmTypeCPartnerPoweredCableWithUfp

### -field UcmTypeCPartnerAudioAccessory

### -field UcmTypeCPartnerDebugAccessory

### -field UcmTypeCPartnerStateAudioAccessory

The partner is used as an audio accessory.


### -field UcmTypeCPartnerStateDebugAccessory

The partner is a debug accessory.


### -field UcmTypeCPartnerStateDfp

The partner is a Downstream Facing Port (DFP).


### -field UcmTypeCPartnerStateInvalid

The partner port state is invalid.


### -field UcmTypeCPartnerStatePoweredCableNoUfp

The partner is a powered cable that requires VConn, that currently does not have a UFP attached on the other end.


### -field UcmTypeCPartnerStatePoweredCableWithUfp

The partner is a powered and upstream facing.


### -field UcmTypeCPartnerStateUfp

The partner is an Upstream Facing Port (UFP).

## -see-also

<a href="/windows-hardware/drivers/ddi/ucmmanager/ns-ucmmanager-_ucm_connector_typec_attach_params">UCM_CONNECTOR_TYPEC_ATTACH_PARAMS</a>



<a href="/windows-hardware/drivers/ddi/ucmmanager/nf-ucmmanager-ucmconnectortypecattach">UcmConnectorTypeCAttach</a>

