---
title: ICLRMetadataLocator::GetMetadata (Método)
ms.date: 03/30/2017
api_name:
- ICLRMetadataLocator.GetMetadata
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRMetadataLocator::GetMetadata
helpviewer_keywords:
- GetMetadata method, ICLRMetadataLocator interface [.NET Framework debugging]
- ICLRMetadataLocator::GetMetadata method [.NET Framework debugging]
ms.assetid: 704a8893-ac56-43b4-90ea-715f38ccb40e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4338619414c9c9ac8c5fe85479562410d1678698
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="iclrmetadatalocatorgetmetadata-method"></a>ICLRMetadataLocator::GetMetadata (Método)
Llamado por los servicios de acceso a datos de common language runtime (CLR) para recuperar los metadatos de una imagen.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT GetMetadata(  
    [in]  LPCWSTR         imagePath,  
    [in]  ULONG32         imageTimestamp,  
    [in]  ULONG32         imageSize,  
    [in]  GUID*           mvid,  
    [in]  ULONG32         mdRva,  
    [in]  ULONG32         flags,  
    [in]  ULONG32         bufferSize,  
    [out, size_is(bufferSize), length_is(*dataSize)]  
          BYTE*           buffer,  
    [out] ULONG32*        dataSize  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `imagePath`  
 [in] Una cadena que especifica la ruta de acceso del archivo de imagen.  
  
 `imageTimestamp`  
 [in] La marca de tiempo del archivo de imagen.  
  
 `imageSize`  
 [in] El tamaño del archivo de imagen.  
  
 `mvid`  
 [in] El identificador único global de la imagen.  
  
 `mdRva`  
 [in] La dirección virtual relativa (RVA) de los metadatos. La dirección es relativa a la dirección base de la imagen.  
  
 `flags`  
 [in] Reservado para uso futuro.  
  
 `bufferSize`  
 [in] El tamaño del búfer en el que se va a colocar los metadatos.  
  
 `buffer`  
 [out] El búfer en el que se va a colocar los metadatos.  
  
 `dataSize`  
 [out] El tamaño de los metadatos que se devuelven.  
  
## <a name="remarks"></a>Comentarios  
 Este método lo implementa el escritor de la aplicación de depuración.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** vea [requisitos del sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Encabezado:** ClrData.idl, ClrData.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versiones de .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [ICLRMetadataLocator (interfaz)](../../../../docs/framework/unmanaged-api/debugging/iclrmetadatalocator-interface.md)
