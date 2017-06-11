---
title: "Obtener acceso a los servicios WCF con una aplicaci&#243;n cliente de la Tienda Windows | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e2002ef4-5dee-4a54-9d87-03b33d35fc52
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# Obtener acceso a los servicios WCF con una aplicaci&#243;n cliente de la Tienda Windows
Windows 8 presenta un nuevo tipo de aplicaciones denominadas aplicaciones de la Tienda Windows. Estas aplicaciones están diseñadas para una interfaz de pantalla táctil. .NET Framework 4.5 permite que las aplicaciones de la Tienda Windows llamen a servicios WCF.  
  
## Compatibilidad de WCF en aplicaciones de la Tienda Windows  
 Un subconjunto de funcionalidad de WCF está disponible en una aplicación de la Tienda Windows; vea las secciones siguientes para obtener más detalles.  
  
> [!IMPORTANT]
>  Use las API de distribución de WinRT en lugar de las expuestas por WCF. Para obtener más información, vea [API de distribución de WinRT](http://go.microsoft.com/fwlink/?LinkId=236265)  
  
> [!WARNING]
>  No se admite el uso de Agregar referencia de servicio para agregar una referencia de servicio web a un componente de Windows en tiempo de ejecución.  
  
### Enlaces admitidos  
 Los siguientes enlaces de WCF se admiten en aplicaciones de la Tienda Windows:  
  
1.  <xref:System.ServiceModel.BasicHttpBinding>  
  
2.  <xref:System.ServiceModel.NetTcpBinding>  
  
3.  <xref:System.ServiceModel.NetHttpBinding>  
  
4.  <xref:System.ServiceModel.CustomBinding>  
  
 Los elementos de enlace siguientes se admiten en aplicaciones de la Tienda Windows  
  
1.  <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>  
  
2.  <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>  
  
3.  <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement>  
  
4.  <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>  
  
5.  <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>  
  
6.  <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
  
7.  <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
  
8.  <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
9. <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>  
  
 Se admiten las codificaciones de texto y binarias. Se admiten todos los modos de transferencia de WCF. Para obtener más información, vea [Transferencia de mensajes por secuencias](../../../../docs/framework/wcf/feature-details/streaming-message-transfer.md).  
  
### Agregar referencia de servicio  
 Para llamar a un servicio WCF desde una aplicación de la Tienda Windows, use la característica Agregar referencia de servicio de Visual Studio 2012. Observará algunos cambios en la funcionalidad de Agregar referencia de servicio cunado se lleva a cabo desde una aplicación de la Tienda Windows. Primero no se genera ningún archivo de configuración. Las aplicaciones de la Tienda Windows no usan archivos de configuración, por lo que deben configurarse en el código. Este código de configuración se puede encontrar en el archivo References.cs que genera Agregar referencia de servicio. Para ver este archivo, asegúrese de seleccionar "Mostrar todos los archivos" en el explorador de soluciones. El archivo se encuentra en los nodos Referencias de servicio y Reference.svcmap en el proyecto. Todas las operaciones generadas para los servicios WCF en una aplicación de la Tienda Windows serán asincrónicas mediante el patrón asincrónico basado en tareas. Para obtener más información, vea [Patrón asincrónico basado en tareas](http://msdn.microsoft.com/magazine/ff959203.aspx).  
  
 Debido a que la configuración ahora se genera en el código, cualquier cambio realizado en el archivo Reference.cs se sobrescribirá cada vez que se actualice la referencia de servicio. Para solucionar esta situación, el código de configuración se genera en un método parcial, que puede implementar en la clase de proxy cliente. El método parcial se declara de la siguiente manera:  
  
```csharp  
static partial void Configure(System.ServiceModel.Description.ServiceEndpoint serviceEndpoint, System.ServiceModel.Description.ClientCredentials clientCredentials);  
  
```  
  
 Puede implementar este método parcial y cambiar el enlace o el extremo en la clase de proxy de cliente de la manera siguiente:  
  
```csharp  
public partial class Service1Client : System.ServiceModel.ClientBase<MetroWcfClient.ServiceRefMultiEndpt.IService1>, MetroWcfClient.ServiceRefMultiEndpt.IService1 { static partial void Configure(System.ServiceModel.Description.ServiceEndpoint serviceEndpoint, System.ServiceModel.Description.ClientCredentials clientCredentials) { if (serviceEndpoint.Name == ServiceRefMultiEndpt.Service1Client.EndpointConfiguration.BasicHttpBinding_IService1.ToString()) { serviceEndpoint.Binding.SendTimeout = new System.TimeSpan(0, 1, 0); } else if (serviceEndpoint.Name == ServiceRefMultiEndpt.Service1Client.EndpointConfiguration.BasicHttpBinding_IService11.ToString()) { serviceEndpoint.Binding.SendTimeout = new System.TimeSpan(0, 1, 0); clientCredentials.UserName.UserName = "username1"; clientCredentials.UserName.Password = "password"; } else if (serviceEndpoint.Name == ServiceRefMultiEndpt.Service1Client.EndpointConfiguration.NetTcpBinding_IService1.ToString()) { serviceEndpoint.Binding.Name = "MyTcpBinding"; serviceEndpoint.Address = new System.ServiceModel.EndpointAddress("net.tcp://localhost/tcp"); } } }  
  
```  
  
### Serialización  
 Los siguientes serializadores se admiten en aplicaciones de la Tienda Windows:  
  
1.  DataContractSerializer  
  
2.  DataContractJsonSerializer  
  
3.  XmlSerializer  
  
> [!WARNING]
>  XmlDictionaryWriter.Write\(DateTime\) ahora escribe el objeto DateTime como una cadena.  
  
### Seguridad  
 Se admiten los siguientes modos de seguridad en las aplicaciones de la Tienda Windows  
  
1.  <xref:System.ServiceModel.SecurityMode>  
  
2.  <xref:System.ServiceModel.SecurityMode>  
  
3.  <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredentials>  
  
4.  <xref:System.ServiceModel.SecurityMode.TransportCredentialOnly>  
  
 Se admiten los tipos de credenciales de cliente siguientes en las aplicaciones de la Tienda Windows  
  
1.  Ninguna  
  
2.  Básico  
  
3.  Implícita  
  
4.  Negociar  
  
5.  NTLM  
  
6.  Windows  
  
7.  Nombre de usuario \(seguridad de mensaje\)  
  
8.  Windows \(seguridad de transporte\)  
  
 Para que las aplicaciones de la Tienda Windows tengan acceso y envíen las credenciales de Windows predeterminadas, debe habilitar esta funcionalidad en el archivo Package.appmanifest. Abra este archivo y seleccione la pestaña Capacidades y seleccione "Credenciales de Windows predeterminadas". Esto permite que la aplicación se conecte a recursos de la intranet que necesitan credenciales de dominio.  
  
> [!IMPORTANT]
>  Para que las aplicaciones de la Tienda Windows realicen llamadas entre equipos debe habilitar otra función denominada “Redes domésticas o de trabajo”. Este valor se encuentra también en el archivo Package.appmanifest en la pestaña Capacidades. Seleccione la casilla Redes domésticas o de trabajo. Esto permite el acceso de entrada y de salida de la aplicación a redes de ubicaciones de confianza del usuario como domésticas y de trabajo. Los puertos críticos de entrada siempre se bloquean. Para tener acceso a servicios de Internet también debe habilitar la capacidad de Internet \(cliente\).  
  
### Varios  
 El uso de las clases siguientes se admite para las aplicaciones de la Tienda Windows:  
  
1.  <xref:System.ServiceModel.ChannelFactory>  
  
2.  <xref:System.ServiceModel.DuplexChannelFactory>  
  
3.  <xref:System.ServiceModel.CallbackBehaviorAttribute>  
  
### Definir contratos de servicio  
 Se recomienda definir solo operaciones de servicio asincrónicas mediante el patrón asincrónico basado en tareas. Esto garantiza que las aplicaciones de la Tienda Windows sigan respondiendo mientras se llama a una operación de servicio.  
  
> [!WARNING]
>  Aunque no se producirá ninguna excepción si define una operación sincrónica, se recomienda definir solamente operaciones asincrónicas.  
  
### Llamar a servicios WCF desde aplicaciones de la Tienda Windows  
 Como se mencionó antes, toda la configuración se debe hacer en el código en el método GetBindingForEndpoint de la clase de proxy generada. La llamada a una operación de servicio se realiza igual que la llamada a cualquier método asincrónico basado en tareas, tal como se muestra en el fragmento de código siguiente.  
  
```csharp  
void async SomeMethod() { ServiceClient proxy = new ServiceClient(); Task<T> results = await proxy.CallAsync(param1, param2); T result = results.Result; if (result.Success) { // Do something with result } }  
  
```  
  
 Observe el uso de la palabra clave async en el método que realiza la llamada asincrónica y la palabra clave await al llamar al método asincrónico.  
  
## Vea también  
 [Blog sobre WCF en aplicaciones de la Tienda Windows](http://blogs.msdn.com/b/piyushjo/archive/2011/09/22/wcf-in-win8-metro-styled-apps-absolutely-supported.aspx)   
 [Seguridad y clientes de la Tienda Windows de WCF](http://blogs.msdn.com/b/piyushjo/archive/2011/10/11/calling-a-wcf-service-from-a-metro-application-adding-security.aspx)   
 [Aplicaciones de la tienda Windows y llamadas entre equipos](http://blogs.msdn.com/b/piyushjo/archive/2011/10/22/calling-a-wcf-service-from-a-metro-application-cross-machine-scenario.aspx)   
 [Llamar a un servicio WCF implementado en Azure desde una aplicación de la Tienda Windows](http://blogs.msdn.com/b/piyushjo/archive/2011/10/22/calling-a-wcf-service-from-a-metro-application-cross-machine-scenario.aspx)   
 [Programación de la seguridad de WCF](../../../../docs/framework/wcf/feature-details/programming-wcf-security.md)   
 [Enlaces](../../../../docs/framework/wcf/bindings.md)