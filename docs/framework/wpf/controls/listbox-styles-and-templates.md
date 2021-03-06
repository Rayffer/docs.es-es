---
title: Estilos y plantillas de ListBox
ms.date: 03/30/2017
helpviewer_keywords:
- styles [WPF], ListBox
- templates [WPF], ListBox
- states [WPF], ListBox
- ControlTemplate [WPF], ListBox
- parts [WPF], ListBox
- ListBox [WPF], styles and templates
ms.assetid: fc5764cb-c27b-495b-88d4-d969a8213ccb
ms.openlocfilehash: bb4fdcd8b0487d3fbd2b96bc06968dca1f65d854
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="listbox-styles-and-templates"></a>Estilos y plantillas de ListBox
En este tema se describe los estilos y plantillas para el <xref:System.Windows.Controls.ListBox> control. Puede modificar el valor predeterminado <xref:System.Windows.Controls.ControlTemplate> para dar al control una apariencia única. Para más información, consulte [Personalización de la apariencia de un control existente mediante la creación de una clase ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).  
  
## <a name="listbox-parts"></a>Elementos de ListBox  
 El <xref:System.Windows.Controls.ListBox> control no tiene los elementos con nombre.  
  
 Cuando se crea un <xref:System.Windows.Controls.ControlTemplate> para un <xref:System.Windows.Controls.ListBox>, la plantilla podría contener una <xref:System.Windows.Controls.ItemsPresenter> dentro de un <xref:System.Windows.Controls.ScrollViewer>. (El <xref:System.Windows.Controls.ItemsPresenter> muestra cada elemento de la <xref:System.Windows.Controls.ListBox>; el <xref:System.Windows.Controls.ScrollViewer> habilita el desplazamiento en el control).  Si el <xref:System.Windows.Controls.ItemsPresenter> no es el elemento secundario directo de la <xref:System.Windows.Controls.ScrollViewer>, debe asignar a la <xref:System.Windows.Controls.ItemsPresenter> el nombre `ItemsPresenter`.  
  
## <a name="listbox-states"></a>Estados de ListBox  
 La tabla siguiente enumera los estados visuales para el <xref:System.Windows.Controls.ListBox> control.  
  
|Nombre de VisualState|Nombre de VisualStateGroup|Descripción|  
|-|-|-|  
|Válido|ValidationStates|El control es válido.|  
|InvalidFocused|ValidationStates|El control no es válido y tiene el foco.|  
|InvalidUnfocused|ValidationStates|El control no es válido y no tiene el foco.|  
  
## <a name="listboxitem-parts"></a>Elementos ListBoxItem  
 El <xref:System.Windows.Controls.ListBoxItem> control no tiene los elementos con nombre.  
  
## <a name="listboxitem-states"></a>Estados de ListBoxItem  
 La tabla siguiente enumera los estados visuales para el <xref:System.Windows.Controls.ListBox> control.  
  
|Nombre de VisualState|Nombre de VisualStateGroup|Descripción|  
|-|-|-|  
|Normal|CommonStates|El estado predeterminado.|  
|MouseOver|CommonStates|El puntero del mouse se coloca sobre el control.|  
|Deshabilitado|CommonStates|El elemento está deshabilitado.|  
|Con foco|FocusStates|El elemento tiene el foco.|  
|Sin foco|FocusStates|El elemento no tiene el foco.|  
|No seleccionado|SelectionStates|El elemento no está seleccionado.|  
|Seleccionado|SelectionStates|El elemento está seleccionado actualmente.|  
|SelectedUnfocused|SelectionStates|El elemento está seleccionado, pero no tiene el foco.|  
|Válido|ValidationStates|El control usa la <xref:System.Windows.Controls.Validation> clase y la <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propiedad adjunta es `false`.|  
|InvalidFocused|ValidationStates|El <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propiedad adjunta es `true` tiene el control tiene el foco.|  
|InvalidUnfocused|ValidationStates|El <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propiedad adjunta es `true` tiene el control no tiene el foco.|  
  
## <a name="listbox-controltemplate-example"></a>Ejemplo de ControlTemplate de ListBox  
 En el ejemplo siguiente se muestra cómo definir un <xref:System.Windows.Controls.ControlTemplate> para el <xref:System.Windows.Controls.ListBox> y <xref:System.Windows.Controls.ListBoxItem> controles.  
  
 [!code-xaml[ControlTemplateExamples#ListBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/listbox.xaml#listbox)]  
  
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
