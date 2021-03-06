---
title: ICorProfilerInfo::BeginInprocDebugging (Método)
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.BeginInprocDebugging
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::BeginInprocDebugging
helpviewer_keywords:
- BeginInprocDebugging method [.NET Framework profiling]
- ICorProfilerInfo::BeginInprocDebugging method [.NET Framework profiling]
ms.assetid: c5c82c69-99f8-4447-aee0-42cca0a5eb5c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 82e798e1a31f771c63e71f2a85f8cbb684b237bd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilerinfobegininprocdebugging-method"></a>ICorProfilerInfo::BeginInprocDebugging (Método)
Inicializa la compatibilidad con la depuración en proceso. Este método está obsoleto en la versión 2.0 de .NET Framework.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT BeginInprocDebugging(  
    [in]  BOOL   fThisThreadOnly,  
    [out] DWORD *pdwProfilerContext);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `fThisThreadOnly`  
 [in] Establezca este valor en `true` para inicializar la compatibilidad con la depuración para el actual subproceso; establézcalo en `false` para inicializar la compatibilidad con la depuración en todos los subprocesos.  
  
 `pdwProfilerContext`  
 [out] Puntero a un valor devuelto que identifica la sesión de depuración.  
  
## <a name="remarks"></a>Comentarios  
 Los servicios de depuración de CLR admiten la depuración en proceso limitada en las versiones 1.0 y 1.1 de .NET Framework. Un generador de perfiles usar las partes de inspección de la API de depuración habilita la depuración en curso. Sin embargo, debido a los comentarios de clientes, depuración en proceso se ha quitado de la versión 2.0 de .NET Framework y reemplazan con un conjunto de funciones que está más en línea con la API de generación de perfiles.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** vea [requisitos del sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Encabezado:** CorProf.idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versión de .NET framework:** 1.0  
  
## <a name="see-also"></a>Vea también  
 [ICorProfilerInfo (interfaz)](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
