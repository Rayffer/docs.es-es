---
title: "SetAssemblyFile2 (Método)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink2.SetAssemblyFile2
api_location: alink.dll
api_type: COM
f1_keywords: SetAssemblyFile2
helpviewer_keywords: SetAssemblyFile2 method
ms.assetid: eedb9125-1ef1-4000-abfc-7de86e5a1f17
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 7363a8f633d5f447f72e27ba03055f589564bdd2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2017
---
# <a name="setassemblyfile2-method"></a>SetAssemblyFile2 (Método)
Establece el nombre y las opciones para un nuevo ensamblado. No llame a este método cuando se crean módulos no enlazados.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT SetAssemblyFile2(  
    LPCWSTR pszFilename,  
    IMetaDataEmit2* pEmitter,  
    AssemblyFlags   afFlags,  
    mdAssembly* pAssemblyID  
) PURE;  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pszFilename`  
 Nombre del archivo de manifiesto.  
  
 `pEmitter`  
 [IMetaDataEmit2 (interfaz)](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md) interfaz para este archivo.  
  
 `afFlags`  
 Opciones representadas por [AssemblyFlags (enumeración)](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md).  
  
 `pAssemblyID`  
 Recibe el identificador único para el ensamblado que se está construyendo.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK si el método tiene éxito.  
  
## <a name="requirements"></a>Requisitos  
 Requiere alink.h.  
  
## <a name="see-also"></a>Vea también  
 [IALink2 (interfaz)](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [IALink (interfaz)](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [API de ALink](../../../../docs/framework/unmanaged-api/alink/index.md)