---
title: Actividad personalizada Hello World
ms.date: 03/30/2017
ms.assetid: 72b1dd0a-9aad-47d5-95a9-a1024ee1d0a1
ms.openlocfilehash: 35ae5933515b3280b0d8d95157c8dd5f40f7b320
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="hello-world-custom-activity"></a>Actividad personalizada Hello World
Este ejemplo muestra varias características fundamentales de Windows Workflow Foundation (WF), incluido cómo crear una actividad personalizada simple. Algunas de las características mostradas en este ejemplo crean una actividad personalizada en C# y utilizan argumentos `in` y `out`(<xref:System.Activities.InArgument> y <xref:System.Activities.OutArgument>).  
  
> [!IMPORTANT]
>  Puede que los ejemplos ya estén instalados en su equipo. Compruebe el siguiente directorio (predeterminado) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si este directorio no existe, vaya a [Windows Communication Foundation (WCF) y ejemplos de Windows Workflow Foundation (WF) para .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para descargar todos los Windows Communication Foundation (WCF) y [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ejemplos. Este ejemplo se encuentra en el siguiente directorio.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\HelloWorld`  
  
## <a name="creating-a-workflow-in-code"></a>Crear un flujo de trabajo en código  
 En este ejemplo, se crean dos actividades personalizadas utilizando el código de C#. Ambas actividades personalizadas heredan directa o indirectamente de <xref:System.Activities.Activity%601> para devolver un único valor. La ventaja de utilizar el valor devuelto genérico, en lugar de heredar de la clase <xref:System.Activities.Activity> no genérica, es que algunas actividades (como <xref:System.Activities.Statements.Assign>) pueden tener acceso al valor devuelto cuando se usa como parte de una actividad compuesta.  
  
 AppendString  
 Esta actividad hereda de <xref:System.Activities.Activity%601> y utiliza una actividad <xref:System.Activities.Statements.Assign> que concatena dos cadenas.  
  
 PrependString  
 Esta actividad hereda directamente de <xref:System.Activities.CodeActivity%601> y crea funcionalidad similar a la actividad `AppendString`, que utiliza lógica implementada en código en lugar de crearse a partir de una actividad ya existente.  
  
 Este proyecto incluye los siguientes archivos.  
  
 AppendString.cs  
 La actividad personalizada que anexa las cadenas. Toma una cadena y combina con una cadena de texto literal "says hello world" para formar un mensaje completo como salida.  
  
 PrependString.cs  
 Esta actividad agrega una cadena predefinida como prefijo a una cadena de entrada.  
  
 Sequence1.xaml  
 Flujo de trabajo que utiliza las actividades personalizadas `AppendString` y `PrependString`.  
  
 Program.cs  
 Programa que ejecuta el flujo de trabajo.  
  
#### <a name="to-use-this-sample"></a>Para utilizar este ejemplo  
  
1.  Con [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], abra el archivo de solución HelloWorld.sln.  
  
2.  Para compilar la solución, presione Ctrl+MAYÚS+B.  
  
3.  Presione F5 para ejecutar la solución.