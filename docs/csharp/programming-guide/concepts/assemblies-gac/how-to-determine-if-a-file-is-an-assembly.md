---
title: 'Cómo: Determinar si un archivo es un ensamblado (C#)'
ms.date: 07/20/2015
ms.assetid: ea5186bb-5bff-4dcb-bde9-d6ba4e2edd00
ms.openlocfilehash: 0557f42d42e42606c3d1b2a2ad71bd797a159e8c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-determine-if-a-file-is-an-assembly-c"></a>Cómo: Determinar si un archivo es un ensamblado (C#)
Un archivo es un ensamblado únicamente si está administrado y contiene una entrada de ensamblado en sus metadatos. Para más información sobre ensamblados y metadatos, vea el tema [Manifiesto del ensamblado](../../../../../docs/framework/app-domains/assembly-manifest.md).  
  
### <a name="how-to-manually-determine-if-a-file-is-an-assembly"></a>Cómo determinar manualmente si un archivo es un ensamblado  
  
1.  Inicie [Ildasm.exe (el desensamblador de lenguaje intermedio)](https://msdn.microsoft.com/library/f7dy01k1).  
  
2.  Cargue el archivo que quiere probar.  
  
3.  Si **ILDASM** notifica que el archivo no es un archivo ejecutable portable (PE), entonces no es un ensamblado. Para obtener más información, vea el tema [Cómo: Ver el contenido de un ensamblado](../../../../framework/app-domains/how-to-view-assembly-contents.md).  
  
### <a name="how-to-programmatically-determine-if-a-file-is-an-assembly"></a>Cómo determinar mediante programación si un archivo es un ensamblado  
  
1.  Llame al método <xref:System.Reflection.AssemblyName.GetAssemblyName%2A>; para ello, pase el nombre y la ruta de acceso de archivo completa del archivo que está probando.  
  
2.  Si se genera una excepción <xref:System.BadImageFormatException>, el archivo no es un ensamblado.  
  
## <a name="example"></a>Ejemplo  
 En este ejemplo se prueba un archivo DLL para ver si es un ensamblado.  
  
```  
class TestAssembly  
{  
    static void Main()  
    {  
  
        try  
        {  
            System.Reflection.AssemblyName testAssembly =  
                System.Reflection.AssemblyName.GetAssemblyName(@"C:\Windows\Microsoft.NET\Framework\v3.5\System.Net.dll");  
  
            System.Console.WriteLine("Yes, the file is an assembly.");  
        }  
  
        catch (System.IO.FileNotFoundException)  
        {  
            System.Console.WriteLine("The file cannot be found.");  
        }  
  
        catch (System.BadImageFormatException)  
        {  
            System.Console.WriteLine("The file is not an assembly.");  
        }  
  
        catch (System.IO.FileLoadException)  
        {  
            System.Console.WriteLine("The assembly has already been loaded.");  
        }  
    }  
}  
/* Output (with .NET Framework 3.5 installed):  
    Yes, the file is an assembly.  
*/  
```  
  
 El método <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> carga el archivo de prueba y, después, lo libera cuando se lee la información.  
  
## <a name="see-also"></a>Vea también  
 <xref:System.Reflection.AssemblyName>  
 [Guía de programación de C#](../../../../csharp/programming-guide/index.md)  
 [Assemblies and the Global Assembly Cache (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/index.md) (Ensamblados y caché global de ensamblados [C#])
