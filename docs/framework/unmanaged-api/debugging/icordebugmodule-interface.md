---
title: ICorDebugModule Interfaz1
ms.date: 03/30/2017
api_name:
- ICorDebugModule
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule
helpviewer_keywords:
- ICorDebugModule interface [.NET Framework debugging]
ms.assetid: 32e4d6fa-e5a3-413e-9166-d5e2871d3114
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: db4a980929a644d2862a382f147505644313da7b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugmodule-interface1"></a>ICorDebugModule Interfaz1
Representa un módulo de common language runtime (CLR), que es un archivo ejecutable o una biblioteca de vínculos dinámicos (DLL).  
  
## <a name="methods"></a>Métodos  
  
|Método|Descripción|  
|------------|-----------------|  
|[CreateBreakpoint (método)](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-createbreakpoint-method.md)|Sin implementar.|  
|[EnableClassLoadCallbacks (método)](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-enableclassloadcallbacks-method.md)|Determina si el [ICorDebugManagedCallback:: LoadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) y [ICorDebugManagedCallback:: UnloadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) las devoluciones de llamada se llama para este módulo.|  
|[EnableJITDebugging (método)](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-enablejitdebugging-method.md)|Determina si el compilador de just-in-time (JIT) conserva la información de depuración para los métodos de este módulo.|  
|[GetAssembly (método)](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getassembly-method.md)|Obtiene el ensamblado que contiene este módulo.|  
|[GetBaseAddress (método)](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getbaseaddress-method.md)|Obtiene la dirección base del módulo.|  
|[GetClassFromToken (método)](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getclassfromtoken-method.md)|Obtiene el ICorDebugClass desde los metadatos.|  
|[GetEditAndContinueSnapshot (método)](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-geteditandcontinuesnapshot-method.md)|Desusado.|  
|[GetFunctionFromRVA (método)](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getfunctionfromrva-method.md)|Sin implementar.|  
|[GetFunctionFromToken (método)](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getfunctionfromtoken-method.md)|Obtiene la función especificada por el token de metadatos.|  
|[GetGlobalVariableValue (método)](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getglobalvariablevalue-method.md)|Obtiene un objeto de valor para la variable global especificada.|  
|[GetMetaDataInterface (método)](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getmetadatainterface-method.md)|Obtiene un puntero de interfaz de metadatos que puede usarse para examinar los metadatos para el módulo.|  
|[GetName (método)](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getname-method.md)|Obtiene el nombre de archivo del módulo.|  
|[GetProcess (método)](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getprocess-method.md)|Obtiene el proceso que contiene este módulo.|  
|[GetSize (método)](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getsize-method.md)|Obtiene el tamaño del módulo en bytes.|  
|[GetToken (método)](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-gettoken-method.md)|Obtiene el token para la entrada de la tabla de este módulo.|  
|[IsDynamic (método)](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-isdynamic-method.md)|Indica si el módulo es dinámico.|  
|[IsInMemory (método)](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-isinmemory-method.md)|Indica si este módulo sólo existe en memoria.|  
  
## <a name="remarks"></a>Comentarios  
  
> [!NOTE]
>  Esta interfaz no admite que se la llame de forma remota, ya sea entre procesos o entre equipos.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** vea [requisitos del sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Encabezado:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versiones de .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [ICorDebug (interfaz)](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
 [Interfaces de depuración](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
