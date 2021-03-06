---
title: IMetaDataEmit::DefineField (Método)
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineField
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineField
helpviewer_keywords:
- IMetaDataEmit::DefineField method [.NET Framework metadata]
- DefineField method, IMetaDataEmit interface [.NET Framework metadata
ms.assetid: 6b5be4fc-2e86-499c-8b09-833160bca767
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fd0ddda898911da2c96a53d941c4290af9028154
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="imetadataemitdefinefield-method"></a>IMetaDataEmit::DefineField (Método)
Crea una definición para un campo con la firma de metadatos especificada y obtiene un símbolo (token) para esa definición de campo.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT DefineField (   
    [in]  mdTypeDef   td,   
    [in]  LPCWSTR     szName,   
    [in]  DWORD       dwFieldFlags,   
    [in]  PCCOR_SIGNATURE pvSigBlob,   
    [in]  ULONG       cbSigBlob,   
    [in]  DWORD       dwCPlusTypeFlag,   
    [in]  void const  *pValue,   
    [in]  ULONG       cchValue,   
    [out] mdFieldDef  *pmd   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `td`  
 [in] El `mdTypeDef` símbolo (token) para la interfaz o clase envolvente.  
  
 `szName`  
 [in] El nombre del campo en Unicode.  
  
 `dwFieldFlags`  
 [in] Los atributos del campo. Se trata de una máscara de bits de `CorFieldAttr` valores.  
  
 `pvSigBlob`  
 [in] La firma del campo como un BLOB.  
  
 `cbSigBlob`  
 [in] El recuento de bytes en `pvSigBlob`.  
  
 `dwCPlusTypeFlage`  
 [in] El `ELEMENT_TYPE_` *\** para el valor constante. Se trata de un `CorElementType` valor. Si no define un valor constante para el campo, use `ELEMENT_TYPE_END`.  
  
 `pValue`  
 [in] El valor constante para el campo.  
  
 `cchValue`  
 [in] El tamaño en caracteres (Unicode) de `pValue`.  
  
 `pmd`  
 [out] El `mdFieldDef` token asignado.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** vea [requisitos del sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Encabezado:** Cor.h  
  
 **Biblioteca:** usada como recurso en MSCorEE.dll  
  
 **Versiones de .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [IMetaDataEmit (interfaz)](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [IMetaDataEmit2 (interfaz)](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
