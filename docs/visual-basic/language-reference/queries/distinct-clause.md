---
title: Distinct (Cláusula, Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryDistinct
helpviewer_keywords:
- Distinct clause [Visual Basic]
- Distinct statement [Visual Basic]
- queries [Visual Basic], Distinct
ms.assetid: 86f42614-0d8f-4ffc-b888-ce8a37a8d36a
ms.openlocfilehash: 4b0ce12f6361d3dc6e5cc3601e96fc3a9bcf3841
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="distinct-clause-visual-basic"></a>Distinct (Cláusula, Visual Basic)
Restringe los valores de la variable de rango actual para eliminar los valores duplicados en las cláusulas de consulta subsiguientes.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
Distinct  
```  
  
## <a name="remarks"></a>Comentarios  
 Puede usar el `Distinct` cláusula para devolver una lista de elementos únicos. El `Distinct` cláusula hace que la consulta pasar por alto los resultados de consulta duplicada. El `Distinct` cláusula se aplica a valores duplicados para todos los devueltos de los campos especificados por el `Select` cláusula. Si no hay ningún `Select` se especifica la cláusula, el `Distinct` cláusula se aplica a la variable de rango de la consulta identificada en el `From` cláusula. Si la variable de rango no es un tipo inmutable, la consulta omitirá únicamente un resultado de consulta si todos los miembros del tipo coinciden con un resultado de consulta existente.  
  
## <a name="example"></a>Ejemplo  
 La siguiente expresión de consulta combina una lista de clientes y una lista de pedidos de cliente. El `Distinct` cláusula se incluye para devolver una lista de nombres de cliente único y las fechas de pedidos.  
  
 [!code-vb[VbSimpleQuerySamples#20](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/distinct-clause_1.vb)]  
  
## <a name="see-also"></a>Vea también  
 [Introducción a LINQ en Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Consultas](../../../visual-basic/language-reference/queries/queries.md)  
 [From (cláusula)](../../../visual-basic/language-reference/queries/from-clause.md)  
 [Select (cláusula)](../../../visual-basic/language-reference/queries/select-clause.md)  
 [Where (cláusula)](../../../visual-basic/language-reference/queries/where-clause.md)
