---
title: Clases estáticas y sus miembros (Guía de programación de C#)
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, static members
- static members [C#]
- static classes [C#]
- C# language, static classes
- static class members [C#]
ms.assetid: 235614b5-1371-4dbd-9abd-b406a8b0298b
ms.openlocfilehash: f3e64d975d2845d8317b37f43c3811af6be03b55
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="static-classes-and-static-class-members-c-programming-guide"></a>Clases estáticas y sus miembros (Guía de programación de C#)
Una clase [estática](../../../csharp/language-reference/keywords/static.md) es básicamente lo mismo que una clase no estática, con la diferencia de que no se pueden crear instancias de una clase estática. En otras palabras, no puede usar la palabra clave [new](../../../csharp/language-reference/keywords/new.md) para crear una variable del tipo de clase. Dado que no hay ninguna variable de instancia, para tener acceso a los miembros de una clase estática, debe usar el nombre de la clase. Por ejemplo, si tiene una clase estática denominada `UtilityClass` que tiene un método público denominado `MethodA`, llame al método tal como se muestra en el ejemplo siguiente:  
  
```csharp  
UtilityClass.MethodA();  
```  
  
 Es posible usar una clase estática como un contenedor adecuado para conjuntos de métodos que solo funcionan en parámetros de entrada y que no tienen que obtener ni establecer campos de instancias internas. Por ejemplo, en la biblioteca de clases .NET Framework, la clase estática <xref:System.Math?displayProperty=nameWithType> contiene métodos que realizan operaciones matemáticas, sin ningún requisito para almacenar o recuperar datos que sean únicos de una instancia concreta de la clase <xref:System.Math>. Es decir, para aplicar los miembros de la clase, debe especificar el nombre de clase y el nombre de método, como se muestra en el ejemplo siguiente.  
  
```csharp  
double dub = -3.14;  
Console.WriteLine(Math.Abs(dub));  
Console.WriteLine(Math.Floor(dub));  
Console.WriteLine(Math.Round(Math.Abs(dub)));  
  
// Output:  
// 3.14  
// -4  
// 3  
```  
  
 Como sucede con todos los tipos de clase, Common Language Runtime (CLR) de [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] carga la información de tipo para una clase estática cuando se carga el programa que hace referencia a la clase. El programa no puede especificar exactamente cuándo se carga la clase, pero existe la garantía de que se cargará, de que sus campos se inicializarán y de que se llamará a su constructor estático antes de que se haga referencia a la clase por primera vez en el programa. Solo se llama una vez a un constructor estático, y una clase estática permanece en memoria durante la vigencia del dominio de aplicación en el que reside el programa.  
  
> [!NOTE]
>  Para crear una clase no estática que solo permita la creación de una instancia de sí misma, vea [Implementing Singleton in C#](https://msdn.microsoft.com/library/ms998558.aspx) (Implementar un singleton en C#).  
  
 La siguiente lista contiene las características principales de una clase estática:  
  
-   Solo contiene miembros estáticos.  
  
-   No se pueden crear instancias de ella.  
  
-   Está sellada.  
  
-   No puede contener [constructores de instancias](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md).  
  
 Por lo tanto, crear una clase estática es básicamente lo mismo que crear una clase que contiene solo miembros estáticos y un constructor privado. Un constructor privado impide que se creen instancias de la clase. La ventaja de usar una clase estática es que el compilador puede comprobar que no se agregue accidentalmente ningún miembro de instancia. El compilador garantizará que no se creen instancias de esta clase.  
  
 Las clases estáticas están selladas y, por lo tanto, no pueden heredarse. No pueden heredar de ninguna clase excepto <xref:System.Object>. Las clases estáticas no pueden contener un constructor de instancias, pero pueden contener un constructor estático. Las clases no estáticas también deben definir un constructor estático si la clase contiene miembros estáticos que requieren inicialización no trivial. Para obtener más información, vea [Constructores estáticos](../../../csharp/programming-guide/classes-and-structs/static-constructors.md).  
  
## <a name="example"></a>Ejemplo  
 A continuación se muestra un ejemplo de una clase estática que contiene dos métodos que convierten la temperatura de grados Celsius a grados Fahrenheit y viceversa:  
  
 [!code-csharp[csProgGuideObjects#31](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/static-classes-and-static-class-members_1.cs)]  
  
## <a name="static-members"></a>Miembros estáticos  
 Una clase no estática puede contener métodos, campos, propiedades o eventos estáticos. El miembro estático es invocable en una clase, incluso si no se ha creado ninguna instancia de la clase. Siempre se tiene acceso al miembro estático con el nombre de clase, no con el nombre de instancia. Solo existe una copia de un miembro estático, independientemente del número de instancias de la clase que se creen. Los métodos y las propiedades estáticos no pueden tener acceso a campos y eventos no estáticos en su tipo contenedor, y tampoco pueden tener acceso a una variable de instancia de un objeto a menos que se pase explícitamente en un parámetro de método.  
  
 Es más habitual declarar una clase no estática con algunos miembros estáticos que declarar toda una clase como estática. Dos usos habituales de los campos estáticos son llevar la cuenta del número de objetos de los que se han creado instancias y almacenar un valor que se debe compartir entre todas las instancias.  
  
 Los métodos estáticos se pueden sobrecargar pero no invalidar, ya que pertenecen a la clase y no a una instancia de la clase.  
  
 Aunque un campo no se puede declarar como `static const`, el campo [const](../../../csharp/language-reference/keywords/const.md) es básicamente estático en su comportamiento. Pertenece al tipo, no a las instancias del tipo. Por lo tanto, se puede tener acceso a campos const mediante la misma notación `ClassName.MemberName` que se usa para los campos estáticos. No se requiere ninguna instancia de objeto.  
  
 C# no admite variables locales estáticas (variables que se declaran en el ámbito del método).  
  
 Para declarar miembros de clases estáticas, use la palabra clave `static` antes del tipo de valor devuelto del miembro, como se muestra en el ejemplo siguiente:  
  
 [!code-csharp[csProgGuideObjects#29](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/static-classes-and-static-class-members_2.cs)]  
  
 Los miembros estáticos se inicializan antes de que se obtenga acceso por primera vez al miembro estático y antes de que se llame al constructor estático, en caso de haberlo. Para tener acceso a un miembro de clase estática, use el nombre de la clase en lugar de un nombre de variable para especificar la ubicación del miembro, como se muestra en el ejemplo siguiente:  
  
 [!code-csharp[csProgGuideObjects#30](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/static-classes-and-static-class-members_3.cs)]  
  
 Si la clase contiene campos estáticos, proporcione un constructor estático que los inicialice al cargar la clase.  
  
 Una llamada a un método estático genera una instrucción de llamada en Lenguaje Intermedio de Microsoft (MSIL), mientras que una llamada a un método de instancia genera una instrucción `callvirt`, que también comprueba si hay referencias a un objeto NULL, pero la mayoría de las veces la diferencia de rendimiento entre las dos no es significativo.  
  
## <a name="c-language-specification"></a>Especificación del lenguaje C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [Guía de programación de C#](../../../csharp/programming-guide/index.md)  
 [static](../../../csharp/language-reference/keywords/static.md)  
 [Clases](../../../csharp/programming-guide/classes-and-structs/classes.md)  
 [class](../../../csharp/language-reference/keywords/class.md)  
 [Constructores estáticos](../../../csharp/programming-guide/classes-and-structs/static-constructors.md)  
 [Constructores de instancias](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md)
