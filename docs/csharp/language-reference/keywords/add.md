---
title: add (Referencia de C#)
ms.date: 07/20/2015
f1_keywords:
- add_CSharpKeyword
helpviewer_keywords:
- add event accessor [C#]
ms.assetid: faf30b99-10e8-45cd-ab9a-57585d4d1d8d
ms.openlocfilehash: c1fa8c130475a67ac175205fe3491a32654ea475
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="add-c-reference"></a>add (Referencia de C#)
La palabra clave contextual `add` se usa para definir un descriptor de acceso de eventos personalizado que se invoca cuando el código de cliente se suscribe a su [evento](../../../csharp/language-reference/keywords/event.md). Si proporciona un descriptor de acceso `add` personalizado, también debe proporcionar un descriptor de acceso [remove](../../../csharp/language-reference/keywords/remove.md).  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra un evento que tiene descriptores de acceso `add` y [remove](../../../csharp/language-reference/keywords/remove.md) personalizados. Para obtener el ejemplo completo, vea [Cómo: Implementar eventos de interfaz](../../../csharp/programming-guide/events/how-to-implement-interface-events.md).  
  
 [!code-csharp[csrefKeywordsContextual#15](../../../csharp/language-reference/keywords/codesnippet/CSharp/add_1.cs)]  
  
 Normalmente, no necesita proporcionar sus propios descriptores de acceso de eventos personalizados. Los descriptores de acceso que se generan automáticamente mediante el compilador cuando declara un evento son suficientes para la mayoría de escenarios.  
  
## <a name="see-also"></a>Vea también  
 [Eventos](../../../csharp/programming-guide/events/index.md)
