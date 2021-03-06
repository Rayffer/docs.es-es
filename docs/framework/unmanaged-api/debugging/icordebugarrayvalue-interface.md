---
title: ICorDebugArrayValue Interfaz1
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue interface
helpviewer_keywords:
- ICorDebugArrayValue interface [.NET Framework debugging]
ms.assetid: dc437751-7093-44e2-bfdc-191d9ce3c192
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a96f2b21e524f03ea3290be268244eaceeb5c7f7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugarrayvalue-interface1"></a>ICorDebugArrayValue Interfaz1
Una subclase de ICorDebugHeapValue que representa una matriz unidimensional o multidimensional.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetBaseIndicies (método)](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getbaseindicies-method.md)|Obtiene el índice de base de cada dimensión de la matriz.|  
|[GetCount (método)](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getcount-method.md)|Obtiene el número total de elementos de la matriz.|  
|[GetDimensions (método)](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getdimensions-method.md)|Obtiene las dimensiones de la matriz.|  
|[GetElement (método)](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelement-method.md)|Obtiene un valor que representa el elemento especificado de la matriz.|  
|[GetElementAtPosition (método)](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelementatposition-method.md)|Obtiene el elemento en la posición determinada, tratando la matriz como una matriz unidimensional de base cero.|  
|[GetElementType (método)](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelementtype-method.md)|Obtiene el tipo simple de los elementos de la matriz.|  
|[GetRank (método)](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getrank-method.md)|Obtiene el número de dimensiones de la matriz.|  
|[HasBaseIndicies (método)](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-hasbaseindicies-method.md)|Determina si la matriz tiene índices de base.|  
  
## <a name="remarks"></a>Comentarios  
 `ICorDebugArrayValue` admite matrices unidimensionales y multidimensionales.  
  
> [!NOTE]
>  Esta interfaz no admite que se la llame de forma remota, ya sea entre procesos o entre equipos.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** vea [requisitos del sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Encabezado:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versiones de .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [Interfaces de depuración](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
