---
title: Crear el servicio de datos
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 34d1d971-5e18-4c22-9bf6-d3612e27ea59
ms.openlocfilehash: bb6e2f7c1160fa51cd897cc953ad0ed721559294
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="creating-the-data-service"></a>Crear el servicio de datos
En esta tarea, creará un servicio de datos de ejemplo que usa [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] para exponer un [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] fuente que se basa en la base de datos de ejemplo Northwind. Esta tarea supone la realización de los siguientes pasos básicos:  
  
1.  Crear una aplicación web de [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)].  
  
2.  Definir el modelo de datos usando las herramientas de [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)].  
  
3.  Agregar el servicio de datos a la aplicación web.  
  
4.  Habilitar el acceso al servicio de datos.  
  
> [!NOTE]
>  El [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplicación Web que se crea al completar esta tarea se ejecuta en el [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] servidor de desarrollo de Visual Studio. El servidor de desarrollo de [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] solo admite el acceso desde el equipo local. Para facilitar también la comprobación y solución de problemas del servicio de datos durante el desarrollo, puede ejecutar la aplicación que hospeda el servicio de datos mediante Internet Information Services (IIS). Para obtener más información, consulta [Cómo: Desarrollar un servicio de datos WCF que se ejecuta en IIS](../../../../docs/framework/data/wcf/how-to-develop-a-wcf-data-service-running-on-iis.md).  
  
### <a name="to-create-the-aspnet-web-application"></a>Para crear la aplicación web ASP.NET  
  
1.  En Visual Studio, en el **archivo** menú, seleccione **New**y, a continuación, seleccione **proyecto**.  
  
2.  En el **nuevo proyecto** cuadro de diálogo, en Visual Basic o Visual C#, seleccione la **Web** plantilla y, a continuación, seleccione **aplicación Web ASP.NET**.  
  
    > [!NOTE]
    >  Si usa Visual Studio Web Developer, tendrá que crear un nuevo sitio web en lugar de una nueva aplicación web.  
  
3.  Tipo `NorthwindService` como el nombre del proyecto.  
  
4.  Haga clic en **Aceptar**.  
  
5.  (Opcional) Especifique un número de puerto específico para la aplicación web. Nota: en el resto del tutorial rápido se usa el número de puerto `12345`.  
  
    1.  En **el Explorador de soluciones**, haga clic en el nombre de la [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] proyecto recién creado y, a continuación, haga clic en **propiedades**.  
  
    2.  Seleccione el **Web** y a establecer el valor de la **puerto específico** cuadro de texto para `12345`.  
  
### <a name="to-define-the-data-model"></a>Para definir el modelo de datos  
  
1.  En **el Explorador de soluciones**, haga clic en el nombre de la [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] del proyecto y, a continuación, haga clic en **Agregar nuevo elemento.**  
  
2.  En el **Agregar nuevo elemento** cuadro de diálogo, haga clic en el **datos** plantilla y, a continuación, seleccione **ADO.NET Entity Data Model**.  
  
3.  Para el nombre del modelo de datos, escriba `Northwind.edmx`.  
  
4.  En el [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)] asistente, seleccione **generar desde la base de datos**y, a continuación, haga clic en **siguiente**.  
  
5.  Conectar el modelo de datos a la base de datos, realice uno de los pasos siguientes y, a continuación, haga clic en **siguiente**:  
  
    -   Si no tiene una conexión de base de datos ya configurada, haga clic en **nueva conexión** y crear una nueva conexión. Para obtener más información, consulte [Cómo: crear conexiones a bases de datos de SQL Server](http://go.microsoft.com/fwlink/?LinkId=123631). Esta instancia de SQL Server debe tener asociada la base de datos de ejemplo Northwind.  
  
         \- o -  
  
    -   Si tiene una conexión de base de datos ya configurada para conectarse a la base de datos Northwind, seleccione esa conexión de la lista de conexiones.  
  
6.  En la página final del asistente, seleccione las casillas de todas las tablas de la base de datos y desactive las casillas correspondientes a las vistas y procedimientos almacenados.  
  
7.  Haga clic en **finalizar** para cerrar el asistente.  
  
    > [!NOTE]
    >  Este modelo de datos generado expone las propiedades de clave externa en los tipos de entidad. Los modelos de datos creados mediante Visual Studio 2008 no incluyen estas propiedades de clave externa. Debido a esto, debe actualizar las clases del servicio de datos de cliente de cualquier aplicación cliente que se haya creado para tener acceso al servicio de datos de Northwind que se creó con Visual Studio 2008 antes de intentar tener acceso a esta versión del servicio de datos de Northwind.  
  
### <a name="to-create-the-data-service"></a>Para crear el servicio de datos  
  
1.  En **el Explorador de soluciones**, haga clic en el nombre de su [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] del proyecto y, a continuación, haga clic en **Agregar nuevo elemento**.  
  
2.  En el **Agregar nuevo elemento** cuadro de diálogo, seleccione **servicio de datos de WCF**.  
  
3.  Para el nombre del servicio, escriba `Northwind`.  
  
     Visual StudioVisual Studio crea los archivos de código y marcado XML para el nuevo servicio. De forma predeterminada, se abre la ventana del editor de código. En **el Explorador de soluciones**, el servicio tendrá el nombre Northwind, con la extensión. svc.cs o. svc.vb.  
  
4.  En el código para el servicio de datos, reemplace el comentario `/* TODO: put your data source class name here */` de la definición de la clase que define el servicio de datos por el tipo que es el contenedor de entidades del modelo de datos, que en este caso es `NorthwindEntities`. La definición de la clase debería ser como la siguiente:  
  
     [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart service/cs/northwind.svc.cs#servicedefinition)]
     [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart service/vb/northwind.svc.vb#servicedefinition)]  
  
### <a name="to-enable-access-to-data-service-resources"></a>Para habilitar el acceso a los recursos del servicio de datos  
  
1.  En el código del servicio de datos, reemplace el código de marcador de posición de la función `InitializeService` por el siguiente:  
  
     [!code-csharp[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart service/cs/northwind.svc.cs#allreadconfig)]
     [!code-vb[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart service/vb/northwind.svc.vb#allreadconfig)]  
  
     De esta forma, los clientes autorizados pueden tener acceso de lectura y escritura a los recursos para los conjuntos de entidades especificados.  
  
    > [!NOTE]
    >  Cualquier cliente que pueda tener acceso a la aplicación [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] también puede tener acceso a los recursos expuestos por el servicio de datos. En un servicio de datos de producción, para evitar el acceso no autorizado a los recursos también debería proteger la aplicación. Para obtener más información, consulta [Securing WCF Data Services](../../../../docs/framework/data/wcf/securing-wcf-data-services.md).  
  
## <a name="next-steps"></a>Pasos siguientes  
 Ha creado correctamente un nuevo servicio de datos que expone un [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] fuente que se basa en la base de datos de ejemplo Northwind y se ha habilitado el acceso a la fuente para los clientes que tienen permisos en el [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplicación Web. A continuación, iniciará el servicio de datos desde Visual Studio y tendrá acceso a la fuente de [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] enviando solicitudes HTTP GET a través de un explorador web:  
  
 [Acceso al servicio desde un explorador web](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)  
  
## <a name="see-also"></a>Vea también  
 [Herramientas de Entity Data Model de ADO.NET](http://msdn.microsoft.com/library/91076853-0881-421b-837a-f582f36be527)
