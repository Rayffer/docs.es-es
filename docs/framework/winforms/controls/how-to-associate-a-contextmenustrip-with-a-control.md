---
title: 'Cómo: Asociar un objeto ContextMenuStrip con un control'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- context menus [Windows Forms], relating
- ContextMenuStrips [Windows Forms], associating with controls
- context menus [Windows Forms], associating with controls
- ContextMenuStrips [Windows Forms], relating
ms.assetid: 6fc40a42-5d69-427f-aa30-0a146193226b
ms.openlocfilehash: 4014324d83e4de634ff7b42204d50fa11dff7ea3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-associate-a-contextmenustrip-with-a-control"></a>Cómo: Asociar un objeto ContextMenuStrip con un control
Después de crear los controles y menús contextuales, utilice los procedimientos siguientes para mostrar un menú contextual determinado cuando el usuario hace clic con el botón secundario del mouse en el control. Estos procedimientos asocian un <xref:System.Windows.Forms.ContextMenuStrip> a un Windows Forms y a un control <xref:System.Windows.Forms.ToolStrip>.  
  
### <a name="to-associate-a-contextmenustrip-with-a-windows-form"></a>Para asociar un objeto ContextMenuStrip a Windows Forms  
  
1.  Establezca la propiedad <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> al nombre del <xref:System.Windows.Forms.ContextMenuStrip> asociado.  
  
### <a name="to-associate-a-contextmenustrip-with-a-toolstrip-control"></a>Para asociar un objeto ContextMenuStrip a un control ToolStrip  
  
1.  Establezca la propiedad <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> del control en el nombre del <xref:System.Windows.Forms.ContextMenuStrip> asociado.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente, se crea un Windows Forms y un control <xref:System.Windows.Forms.ToolStrip>, y se asocia un control <xref:System.Windows.Forms.ContextMenuStrip> diferente a cada uno de ellos.  
  
 [!code-csharp[System.Windows.Forms.ContextMenuStrip#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ContextMenuStrip/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.ContextMenuStrip#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ContextMenuStrip/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilar el código  
 Para este ejemplo se necesita:  
  
-   Referencias a los ensamblados System, System.Data, System.Drawing y System.Windows.Forms.  
  
 Para obtener información acerca de cómo compilar este ejemplo desde la línea de comandos de Visual Basic o Visual C#, vea [compilar desde la línea de comandos](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) o [Command-Line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). También puede compilar este ejemplo en Visual Studio pegando el código en un nuevo proyecto.  Consulte también [Cómo: Compilar y ejecutar un ejemplo de código completo de Windows Forms en Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Vea también  
 <xref:System.Windows.Forms.ContextMenuStrip>  
 <xref:System.Windows.Forms.Control.ContextMenuStrip%2A>  
 <xref:System.Windows.Forms.ToolStrip>  
 [Agregar elementos de menú a ContextMenuStrip](../../../../docs/framework/winforms/controls/how-to-add-menu-items-to-a-contextmenustrip.md)  
 [ContextMenuStrip (Control)](../../../../docs/framework/winforms/controls/contextmenustrip-control.md)
