---
title: IMetaDataImport::EnumMethodsWithName (Método)
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMethodsWithName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMethodsWithName
helpviewer_keywords:
- IMetaDataImport::EnumMethodsWithName method [.NET Framework metadata]
- EnumMethodsWithName method [.NET Framework metadata]
ms.assetid: a8624913-2e23-46ad-a0c1-bb8eccbbf20f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cea47f8300c57362abae0c10223559319ecb2469
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="imetadataimportenummethodswithname-method"></a>IMetaDataImport::EnumMethodsWithName (Método)
Enumera los métodos que tienen el nombre especificado y que están definidos por el tipo al que hace referencia el token de TypeDef especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT EnumMethodsWithName (  
   [in, out] HCORENUM    *phEnum,  
   [in]  mdTypeDef       cl,  
   [in]  LPCWSTR         szName,  
   [out] mdMethodDef     rMethods[],  
   [in]  ULONG           cMax,  
   [out] ULONG           *pcTokens  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `phEnum`  
 [entrada, salida] Un puntero para el enumerador. Esto debe ser NULL para la primera llamada de este método.  
  
 `cl`  
 [in] Un token de TypeDef que representa el tipo cuyos métodos para enumerar.  
  
 `szName`  
 [in] El nombre que limita el ámbito de la enumeración.  
  
 `rMethods`  
 [out] Matriz utilizada para almacenar los tokens de MethodDef.  
  
 `cMax`  
 [in] Tamaño máximo de la matriz `rMethods`.  
  
 `pcTokens`  
 [out] El número de tokens de MethodDef devueltos en `rMethods`.  
  
## <a name="remarks"></a>Comentarios  
 Este método enumera campos y métodos, pero no propiedades o eventos. A diferencia de [IMetaDataImport:: EnumMethods](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummethods-method.md), `EnumMethodsWithName` descarta todos los tokens de método que no tiene el nombre especificado.  
  
## <a name="return-value"></a>Valor devuelto  
  
|HRESULT|Descripción|  
|-------------|-----------------|  
|`S_OK`|`EnumMethodsWithName` se devolvió correctamente.|  
|`S_FALSE`|No hay ningún tokens para enumerar. En ese caso, `pcTokens` es cero.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** vea [requisitos del sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Encabezado:** Cor.h  
  
 **Biblioteca:** incluye como recurso en MsCorEE.dll  
  
 **Versiones de .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [IMetaDataImport (interfaz)](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [IMetaDataImport2 (interfaz)](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
