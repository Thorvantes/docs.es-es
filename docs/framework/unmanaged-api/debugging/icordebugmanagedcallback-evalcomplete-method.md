---
title: "ICorDebugManagedCallback::EvalComplete (Método)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback.EvalComplete
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback::EvalComplete
helpviewer_keywords:
- ICorDebugManagedCallback::EvalComplete method [.NET Framework debugging]
- EvalComplete method [.NET Framework debugging]
ms.assetid: f74ab4eb-cd1b-407c-a66d-8ec0d85647f3
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6211a5f0038c6244f7732e0c0ba854aaa1e6092e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmanagedcallbackevalcomplete-method"></a>ICorDebugManagedCallback::EvalComplete (Método)
Notifica al depurador que se ha completado una evaluación.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT EvalComplete (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread,  
    [in] ICorDebugEval      *pEval  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pAppDomain`  
 [in] Un puntero a un objeto ICorDebugAppDomain que representa el dominio de aplicación en el que se realizó la evaluación.  
  
 `pThread`  
 [in] Un puntero a un objeto ICorDebugThread que representa el subproceso en el que se realizó la evaluación.  
  
 `pEval`  
 [in] Un puntero a un objeto ICorDebugEval que representa el código que realiza la evaluación.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** vea [requisitos del sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Encabezado:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versiones de .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [ICorDebugManagedCallback (interfaz)](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)