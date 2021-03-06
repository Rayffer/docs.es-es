---
title: 'Cómo: Reproducir un sonido desde Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- playing sounds [Windows Forms], Windows Forms
- sounds [Windows Forms], playing
- sounds
- My.Computer.Audio object [Windows Forms], playing sounds
- examples [Windows Forms], sounds
ms.assetid: 3d3350b7-1ebd-4e05-a738-48ca1160a19d
ms.openlocfilehash: 853d0f78b4f6dba2dc84109270f79f4b010c27b4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-play-a-sound-from-a-windows-form"></a>Cómo: Reproducir un sonido desde Windows Forms
En este ejemplo se reproduce un sonido en una ruta de acceso determinada en tiempo de ejecución.  
  
## <a name="example"></a>Ejemplo  
  
```vb  
Sub PlaySimpleSound()  
    My.Computer.Audio.Play("c:\Windows\Media\chimes.wav")  
End Sub  
```  
  
```csharp  
private void playSimpleSound()  
{  
    SoundPlayer simpleSound = new SoundPlayer(@"c:\Windows\Media\chimes.wav");  
    simpleSound.Play();  
}  
```  
  
## <a name="compiling-the-code"></a>Compilar el código  
 Para este ejemplo se necesita:  
  
-   Que reemplace el nombre de archivo `"c:\Windows\Media\chimes.wav"` por un nombre de archivo válido.  
  
-   (C#) Una referencia a la <xref:System.Media?displayProperty=nameWithType> espacio de nombres.  
  
## <a name="robust-programming"></a>Programación sólida  
 Las operaciones de archivo se deberían agregar dentro de los bloques de control de excepciones estructurado adecuados.  
  
 Las condiciones siguientes pueden provocar una excepción:  
  
-   El nombre de la ruta de acceso es incorrecto. Por ejemplo, contiene caracteres no válidos o solo tiene espacios en blanco (clase <xref:System.ArgumentException>).  
  
-   La ruta de acceso es de solo lectura (clase <xref:System.IO.IOException>).  
  
-   El nombre de la ruta de acceso es `null` (clase <xref:System.ArgumentNullException>).  
  
-   El nombre de la ruta de acceso es demasiado largo (clase <xref:System.IO.PathTooLongException>).  
  
-   La ruta de acceso no es válida (clase <xref:System.IO.DirectoryNotFoundException>).  
  
-   La ruta de acceso es solo un signo de dos puntos ":" (<xref:System.NotSupportedException> clase).  
  
## <a name="net-framework-security"></a>Seguridad de .NET Framework  
 No tome ninguna decisión sobre el contenido del archivo basándose en su nombre. Por ejemplo, es posible que el archivo `Form1.vb` no sea un archivo de código fuente de Visual Basic. Compruebe todas las entradas antes de utilizar los datos en la aplicación.  
  
## <a name="see-also"></a>Vea también  
 <xref:System.Media.SoundPlayer>  
 [Cómo: Cargar un sonido de forma asincrónica en Windows Forms](../../../../docs/framework/winforms/controls/how-to-load-a-sound-asynchronously-within-a-windows-form.md)  
 
