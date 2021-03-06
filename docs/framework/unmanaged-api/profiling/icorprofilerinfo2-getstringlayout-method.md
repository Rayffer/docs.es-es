---
title: ICorProfilerInfo2::GetStringLayout (Método)
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetStringLayout
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetStringLayout
helpviewer_keywords:
- GetStringLayout method [.NET Framework profiling]
- ICorProfilerInfo2::GetStringLayout method [.NET Framework profiling]
ms.assetid: 43189651-a535-4803-a1d1-f1c427ace2ca
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8d1bd732a82028afe809f4c2141e1d61668eae1c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilerinfo2getstringlayout-method"></a>ICorProfilerInfo2::GetStringLayout (Método)
Obtiene información sobre la distribución de un objeto de cadena. Este método está en desuso en el [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]y se ha sustituido por la [ICorProfilerInfo3:: Getstringlayout2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getstringlayout2-method.md) método.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT GetStringLayout(  
    [out] ULONG *pBufferLengthOffset,  
    [out] ULONG *pStringLengthOffset,  
    [out] ULONG *pBufferOffset);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pBufferLengthOffset`  
 [out] Un puntero al desplazamiento de la ubicación, relativa a la `ObjectID` puntero, que almacena la longitud de la cadena. La longitud se almacena como un `DWORD`.  
  
> [!NOTE]
>  Este parámetro devuelve la longitud de la cadena, no la longitud del búfer. La longitud del búfer ya no está disponible.  
  
 `PStringLengthOffset`  
 [out] Un puntero al desplazamiento de la ubicación, relativa a la `ObjectID` puntero, que almacena la longitud de la propia cadena. La longitud se almacena como un `DWORD`.  
  
 `pBufferOffset`  
 [out] Un puntero para el desplazamiento del búfer, relativo a la `ObjectID` puntero, que almacena la cadena de caracteres anchos.  
  
## <a name="remarks"></a>Comentarios  
 El `GetStringLayout` método obtiene los desplazamientos, relativo a la `ObjectID` puntero, de las ubicaciones en que se almacenan los siguientes:  
  
-   La longitud de búfer de la cadena.  
  
-   La longitud de la propia cadena.  
  
-   Búfer que contiene la cadena real de caracteres anchos.  
  
 Pueden ser cadenas terminadas en null.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** vea [requisitos del sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Encabezado:** CorProf.idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versiones de .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [ICorProfilerInfo (interfaz)](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [ICorProfilerInfo2 (interfaz)](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
