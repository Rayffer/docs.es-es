---
title: Estilos y plantillas de ScrollViewer
ms.date: 03/30/2017
helpviewer_keywords:
- parts [WPF], ScrollViewer
- states [WPF], ScrollViewer
- styles [WPF], ScrollViewer
- templates [WPF], ScrollViewer
- ControlTemplate [WPF], ScrollViewer
- ScrollViewer [WPF], styles and templates
ms.assetid: dffdd822-ae69-4946-abaf-710860cd65b2
ms.openlocfilehash: 2182390b47508833b8535864f2d670c194d66088
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="scrollviewer-styles-and-templates"></a>Estilos y plantillas de ScrollViewer
En este tema se describe los estilos y plantillas para el <xref:System.Windows.Controls.ScrollViewer> control. Puede modificar el valor predeterminado <xref:System.Windows.Controls.ControlTemplate> para dar al control una apariencia única. Para más información, consulte [Personalización de la apariencia de un control existente mediante la creación de una clase ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).  
  
## <a name="scrollviewer-parts"></a>Partes de ScrollViewer  
 En la tabla siguiente se enumera los elementos con nombre para el <xref:System.Windows.Controls.ScrollViewer> control.  
  
|Parte|Tipo|Descripción|  
|-|-|-|  
|PART_ScrollContentPresenter|<xref:System.Windows.Controls.ScrollContentPresenter>|El marcador de posición para el contenido en el <xref:System.Windows.Controls.ScrollViewer>.|  
|PART_HorizontalScrollBar|<xref:System.Windows.Controls.Primitives.ScrollBar>|El <xref:System.Windows.Controls.Primitives.ScrollBar> utilizado para desplazar el contenido horizontalmente.|  
|PART_VerticalScrollBar|<xref:System.Windows.Controls.Primitives.ScrollBar>|El <xref:System.Windows.Controls.Primitives.ScrollBar> utilizado para desplazar el contenido verticalmente.|  
  
## <a name="scrollviewer-states"></a>Estados de ScrollViewer  
 La tabla siguiente enumera los estados visuales para el <xref:System.Windows.Controls.ScrollViewer> control.  
  
|Nombre de VisualState|Nombre de VisualStateGroup|Descripción|  
|-|-|-|  
|Válido|ValidationStates|El control usa la <xref:System.Windows.Controls.Validation> clase y la <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propiedad adjunta es `false`.|  
|InvalidFocused|ValidationStates|El <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propiedad adjunta es `true` tiene el control tiene el foco.|  
|InvalidUnfocused|ValidationStates|El <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propiedad adjunta es `true` tiene el control no tiene el foco.|  
  
## <a name="scrollviewer-controltemplate-example"></a>Ejemplo de ControlTemplate de ScrollViewer  
 En el ejemplo siguiente se muestra cómo definir un <xref:System.Windows.Controls.ControlTemplate> para el <xref:System.Windows.Controls.ScrollViewer> control.  
  
 [!code-xaml[ControlTemplateExamples#ScrollViewer](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/scrollviewer.xaml#scrollviewer)]  
  
 En el ejemplo anterior se usa uno o varios de los recursos siguientes.  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 Para ver un ejemplo completo, consulte [Aplicación de estilos con el ejemplo ControlTemplates](http://go.microsoft.com/fwlink/?LinkID=160041).  
  
## <a name="see-also"></a>Vea también  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [Estilos y plantillas de controles](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [Control Customization](../../../../docs/framework/wpf/controls/control-customization.md) (Personalización de controles)  
 [Aplicar estilos y plantillas](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [Personalización de la apariencia de un control existente mediante la creación de una clase ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
