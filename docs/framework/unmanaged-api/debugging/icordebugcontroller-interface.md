---
title: ICorDebugController Interfaz1
ms.date: 03/30/2017
api_name:
- ICorDebugController
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController
helpviewer_keywords:
- ICorDebugController interface [.NET Framework debugging]
ms.assetid: dbb1c4dc-269a-459b-ab1d-6c70788782ce
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 230488201b637c5a53f41dd4c3f204b37e8984fd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugcontroller-interface1"></a>ICorDebugController Interfaz1
Representa un ámbito, <xref:System.Diagnostics.Process> o <xref:System.AppDomain>, en el que se puede controlar el contexto de ejecución de código.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descripción|  
|------------|-----------------|  
|`ICorDebugController::CanCommitChanges`|Este método está obsoleto.|  
|`ICorDebugController::CommitChanges`|Este método está obsoleto.|  
|[Continue (método)](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)|Reanuda la ejecución de subprocesos administrados después de llamar a [ICorDebugController:: Stop](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md).|  
|[Detach (método)](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-detach-method.md)|Desasocia al depurador desde el proceso o dominio de aplicación.|  
|[EnumerateThreads (método)](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-enumeratethreads-method.md)|Obtiene un enumerador para los subprocesos administrados activos en el proceso.|  
|[HasQueuedCallbacks (método)](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-hasqueuedcallbacks-method.md)|Obtiene un valor que indica si las devoluciones de llamada administradas actualmente están en cola para el subproceso especificado.|  
|[IsRunning (método)](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-isrunning-method.md)|Obtiene un valor que indica si los subprocesos del proceso se están ejecutando libremente.|  
|[SetAllThreadsDebugState (método)](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-setallthreadsdebugstate-method.md)|Establece el estado de depuración de todos los subprocesos administrados en el proceso.|  
|[Stop (método)](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md)|Realiza una detención cooperativa en todos los subprocesos que ejecutan código administrado en el proceso.|  
|[Terminate (método)](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-terminate-method.md)|Finaliza el proceso con el código de salida especificado.|  
  
## <a name="remarks"></a>Comentarios  
 Si `ICorDebugController` es controlar un proceso, el ámbito incluye todos los subprocesos del proceso. Si `ICorDebugController` es controlar un dominio de aplicación, el ámbito incluye solo los subprocesos de ese dominio de aplicación determinado.  
  
> [!NOTE]
>  Esta interfaz no admite que se la llame de forma remota, ya sea entre procesos o entre equipos.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** vea [requisitos del sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Encabezado:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versiones de .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [Interfaces de depuración](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
