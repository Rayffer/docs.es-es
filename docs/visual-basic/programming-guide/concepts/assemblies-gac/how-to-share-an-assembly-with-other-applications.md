---
title: 'Cómo: compartir un ensamblado con otras aplicaciones (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 5388aedc-cb42-4622-8b70-8e701eee057a
ms.openlocfilehash: 3a6a04a3aef5430eb65d0c1a7eb37f6afb9e5c86
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-share-an-assembly-with-other-applications-visual-basic"></a>Cómo: compartir un ensamblado con otras aplicaciones (Visual Basic)
Los ensamblados pueden ser privados o compartidos: de forma predeterminada, la mayoría de los programas sencillos constan de un ensamblado privado porque no se diseñaron para ser usados por otras aplicaciones.  
  
 Para compartir un ensamblado con otras aplicaciones, debe colocarse en la [caché global de ensamblados](../../../../framework/app-domains/gac.md) (GAC).  
  
### <a name="sharing-an-assembly"></a>Compartir un ensamblado  
  
1.  Cree el ensamblado. Para obtener más información, vea [Creating Assemblies](../../../../framework/app-domains/create-assemblies.md) (Crear ensamblados).  
  
2.  Asigne un nombre seguro al ensamblado. Para obtener más información, vea [Cómo: Firmar un ensamblado con un nombre seguro](../../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).  
  
3.  Asigne la información de versión al ensamblado. Para obtener más información, vea [Versiones de los ensamblados](../../../../framework/app-domains/assembly-versioning.md).  
  
4.  Agregue el ensamblado a la caché global de ensamblados. Para obtener más información, vea [Cómo: Instalar un ensamblado en la memoria caché global de ensamblados](../../../../framework/app-domains/how-to-install-an-assembly-into-the-gac.md).  
  
5.  Obtenga acceso a los tipos contenidos en el ensamblado desde las otras aplicaciones. Para obtener más información, vea [Cómo: Hacer referencia a un ensamblado con nombre seguro](http://msdn.microsoft.com/library/4c6a406a-b5eb-44fa-b4ed-4e95bb95a813).  
  
## <a name="see-also"></a>Vea también  
 [Conceptos de programación](../../../../visual-basic/programming-guide/concepts/index.md) [ensamblados y caché Global de ensamblados (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [Programar con ensamblados](../../../../framework/app-domains/programming-with-assemblies.md)
