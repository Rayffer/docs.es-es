---
title: 'Cómo: Crear un StackPanel'
ms.date: 03/30/2017
helpviewer_keywords:
- StackPanel control [WPF], creating
ms.assetid: e7ce65cb-720a-4bb6-95b6-286b74488a58
ms.openlocfilehash: 30f24d8dba7c09271a5957822439af6b64e05aca
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-stackpanel"></a>Cómo: Crear un StackPanel
Este ejemplo muestra cómo crear un <xref:System.Windows.Controls.StackPanel>.  
  
## <a name="example"></a>Ejemplo  
 Un <xref:System.Windows.Controls.StackPanel> permite apilar elementos en una dirección especificada. Mediante las propiedades que se definen en <xref:System.Windows.Controls.StackPanel>, el contenido puede fluir ambos verticalmente, que es la configuración predeterminada, horizontal o verticalmente.  
  
 En el ejemplo siguiente se apila verticalmente cinco <xref:System.Windows.Controls.TextBlock> controla, cada uno con otro <xref:System.Windows.Controls.Border> y <xref:System.Windows.Controls.Border.Background%2A>, mediante el uso de <xref:System.Windows.Controls.StackPanel>. Los elementos secundarios que haya especificado <xref:System.Windows.FrameworkElement.Width%2A> ajustar para rellenar la ventana primaria; sin embargo, los elementos secundarios que tienen un determinado <xref:System.Windows.FrameworkElement.Width%2A>, se centra en la ventana.  
  
 La dirección de la pila predeterminada en un <xref:System.Windows.Controls.StackPanel> es vertical. Flujo de control contenido en un <xref:System.Windows.Controls.StackPanel>, use el <xref:System.Windows.Controls.StackPanel.Orientation%2A> propiedad. Puede controlar la alineación horizontal mediante la <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> propiedad.  
  
```xaml  
<Page xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation" WindowTitle="StackPanel Sample">  
  <StackPanel>  
    <Border Background="SkyBlue" BorderBrush="Black" BorderThickness="1">  
      <TextBlock Foreground="Black" FontSize="12">Stacked Item #1</TextBlock>  
    </Border>  
    <Border Width="400" Background="CadetBlue" BorderBrush="Black" BorderThickness="1">  
      <TextBlock Foreground="Black" FontSize="14">Stacked Item #2</TextBlock>  
    </Border>  
    <Border Background="LightGoldenRodYellow" BorderBrush="Black" BorderThickness="1">  
      <TextBlock Foreground="Black" FontSize="16">Stacked Item #3</TextBlock>  
    </Border>  
    <Border Width="200" Background="PaleGreen" BorderBrush="Black" BorderThickness="1">  
      <TextBlock Foreground="Black" FontSize="18">Stacked Item #4</TextBlock>  
    </Border>  
    <Border Background="White" BorderBrush="Black" BorderThickness="1">  
      <TextBlock Foreground="Black" FontSize="20">Stacked Item #5</TextBlock>  
    </Border>  
  </StackPanel>  
</Page>  
```  
  
## <a name="see-also"></a>Vea también  
 <xref:System.Windows.Controls.StackPanel>  
 [Información general sobre elementos Panel](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [Temas "Cómo..."](../../../../docs/framework/wpf/controls/stackpanel-how-to-topics.md)
