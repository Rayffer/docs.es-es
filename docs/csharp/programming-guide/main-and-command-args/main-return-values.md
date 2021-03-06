---
title: Valores devueltos de Main() (Guía de programación de C#)
ms.date: 08/02/2017
helpviewer_keywords:
- Main method [C#], return values
ms.assetid: c2f5a1d8-1676-4bea-bc7e-44a97e72d5bc
ms.openlocfilehash: 51a7d821b5705c0ddda96a34663ba0288e0f1da9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="main-return-values-c-programming-guide"></a>Valores devueltos de Main() (Guía de programación de C#)

El método `Main` puede devolver el valor `void`:

[!code-csharp[csProgGuideMain#12](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/main-return-values_1.cs)]

También puede devolver un valor `int`:

[!code-csharp[csProgGuideMain#13](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/main-return-values_2.cs)]

Si el valor devuelto de `Main` no se usa, la devolución de `void` permite contar con un código ligeramente más simple. En cambio, devolver un valor entero permite que el programa comunique información de estado a otros programas o scripts que invocan el archivo ejecutable. El valor devuelto de `Main` se trata como el código de salida para el proceso. En el ejemplo siguiente se muestra cómo se puede acceder al valor devuelto de `Main`.

## <a name="example"></a>Ejemplo

En este ejemplo se usan las herramientas de línea de comandos de [.NET Core](../../../core/index.md). Si no está familiarizado con las herramientas de línea de comandos de .NET Core, puede obtener información sobre ellas en este [tema de introducción](../../../core/tutorials/using-with-xplat-cli.md).

Modifique el método `Main` en *program.cs* como se indica a continuación:

[!code-csharp[csProgGuideMain#14](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/main-return-values_3.cs)]

Cuando un programa se ejecuta en Windows, cualquier valor devuelto por la función `Main` se almacena en una variable de entorno. Esta variable de entorno se puede recuperar mediante `ERRORLEVEL` desde un archivo por lotes, o mediante `$LastExitCode` desde PowerShell.

Puede compilar la aplicación mediante el comando `dotnet build` de la [CLI de dotnet](../../../core/tools/dotnet.md).

Después, cree un script de PowerShell para ejecutar la aplicación y mostrar el resultado. Pegue el código siguiente en un archivo de texto y guárdelo como `test.ps1` en la carpeta que contiene el proyecto. Ejecute el script de PowerShell. Para ello, escriba `test.ps1` en el símbolo del sistema de PowerShell.

Dado que el código devuelve el valor cero, el archivo por lotes comunicará un resultado satisfactorio. En cambio, si cambia MainReturnValTest.cs para que devuelva un valor distinto de cero y luego vuelve a compilar el programa, la ejecución posterior del script de PowerShell informará de que se ha producido un error.

```powershell
dotnet run
if ($LastExitCode -eq 0) {
    Write-Host "Execution succeeded"
} else
{
    Write-Host "Execution Failed"
}
Write-Host "Return value = " $LastExitCode
```

## <a name="sample-output"></a>Resultados de ejemplo

```txt
Execution succeeded
Return value = 0
```

## <a name="async-main-return-values"></a>Valores devueltos asincrónicos de Main

Los valores devueltos asincrónicos de Main mueven el código reutilizable necesario para llamar a métodos asincrónicos en `Main` al código generado por el compilador. Antes, había que escribir esta construcción para llamar a código asincrónico y asegurarse de que el programa se ejecutase hasta la finalización de la operación asincrónica:

```csharp
public static void Main()
{
    AsyncConsoleWork().GetAwaiter().GetResult();
}

private static async Task<int> AsyncConsoleWork()
{
    // Main body here
    return 0;
}
```

Ahora, esto se puede reemplazar por lo siguiente:

[!code-csharp[AsyncMain](../../../../samples/snippets/csharp/main-arguments/program.cs#AsyncMain)]

La ventaja de la nueva sintaxis es que el compilador siempre genera el código correcto.

## <a name="compiler-generated-code"></a>Código generado por el compilador

Cuando el punto de entrada de la aplicación devuelve `Task` o `Task<int>`, el compilador genera un nuevo punto de entrada que llama al método de punto de entrada declarado en el código de la aplicación. Suponiendo que este punto de entrada se denomina `$GeneratedMain`, el compilador genera el código siguiente para estos puntos de entrada:

- `static Task Main()` hace que el compilador emita el equivalente de `private static void $GeneratedMain() => Main().GetAwaiter().GetResult();`
- `static Task Main(string[])` hace que el compilador emita el equivalente de `private static void $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`
- `static Task<int> Main()` hace que el compilador emita el equivalente de `private static int $GeneratedMain() => Main().GetAwaiter().GetResult();`
- `static Task<int> Main(string[])` hace que el compilador emita el equivalente de `private static int $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`

> [!NOTE]
>Si en los ejemplos se usase el modificador `async` en el método `Main`, el compilador generaría el mismo código.

## <a name="see-also"></a>Vea también
[Guía de programación de C#](../../programming-guide/index.md)
[Referencia de C#](../index.md)
[Main() y argumentos de la línea de comandos](index.md)
[Cómo: Mostrar argumentos de la línea de comandos](../../programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)
[Cómo: Obtener acceso a argumentos de la línea de comandos utilizando Foreach](../../programming-guide/main-and-command-args/how-to-access-command-line-arguments-using-foreach.md)
