---
title: "Comunicaci&#243;n en cola vol&#225;til | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0d012f64-51c7-41d0-8e18-c756f658ee3d
caps.latest.revision: 28
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 28
---
# Comunicaci&#243;n en cola vol&#225;til
Este ejemplo muestra cómo realizar la comunicación en cola volátil sobre el transporte de Message Queuing \(MSMQ\).Este ejemplo utiliza <xref:System.ServiceModel.NetMsmqBinding>.El servicio en este caso es una aplicación de consola hospedada a sí misma que le permite observar el servicio que recibe los mensajes en cola.  
  
> [!NOTE]
>  El procedimiento de instalación y las instrucciones de compilación de este ejemplo se encuentran al final de este tema.  
  
 En la comunicación con colas, el cliente se comunica con el servicio mediante una cola.Más exactamente, el cliente envía los mensajes a una cola.El servicio recibe los mensajes de la cola.El servicio y el cliente no se tienen que estar ejecutando simultáneamente para comunicarse mediante una cola.  
  
 Al enviar un mensaje sin garantías, MSMQ solo realiza un esfuerzo para entregar el mensaje, a diferencia de las garantías de tipo "exactamente una vez" donde MSMQ garantiza que se entrega el mensaje o, si no se puede, le informa de que el mensaje no puede entregarse.  
  
 En ciertos escenarios, puede desear enviar un mensaje volátil sin garantías sobre una cola, cuando una entrega a tiempo es más importante que perder los mensajes.Los mensajes volátiles no sobreviven a los bloqueos del administrador de la cola.Por consiguiente, si el administrador de cola se bloquea, la cola no transaccional utilizada para almacenar los mensajes volátiles sobrevive pero los mensajes no porque no están almacenados en el disco.  
  
> [!NOTE]
>  No puede enviar mensajes volátiles sin garantías dentro del ámbito de una transacción utilizando MSMQ.También debe crear una cola no transaccional para enviar mensajes volátiles.  
  
 El contrato de servicios en este ejemplo es `IStockTicker` que define servicios unidireccionales que se adaptan mejor a su uso con la cola.  
  
```  
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]  
public interface IStockTicker  
{  
    [OperationContract(IsOneWay = true)]  
    void StockTick(string symbol, float price);  
}  
  
```  
  
 La operación de servicio muestra el símbolo y precios del tablero de cotizaciones, tal y como se muestra en el código de ejemplo siguiente:  
  
```  
public class StockTickerService : IStockTicker  
{  
    public void StockTick(string symbol, float price)  
    {  
        Console.WriteLine("Stock Tick {0}:{1} ", symbol, price);  
     }  
     …  
}  
  
```  
  
 El servicio se hospeda en sí mismo.Al utilizar el transporte de MSMQ, se debe crear la cola utilizada de antemano.Esto se puede hacer manualmente o a través de código.En este ejemplo, el servicio contiene el código para comprobar la existencia de la cola y crearla si fuera necesario.El nombre de la cola se lee desde el archivo de configuración.[Herramienta de utilidad de metadatos de ServiceModel \(Svcutil.exe\)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) utiliza la dirección base para generar el proxy para el servicio.  
  
```  
// Host the service within this EXE console application.  
public static void Main()  
{  
    // Get MSMQ queue name from app settings in configuration.  
    string queueName = ConfigurationManager.AppSettings["queueName"];  
  
    // Create the transacted MSMQ queue if necessary.  
    if (!MessageQueue.Exists(queueName))  
        MessageQueue.Create(queueName);  
  
    // Create a ServiceHost for the StockTickerService type.  
    using (ServiceHost serviceHost = new ServiceHost(typeof(StockTickerService)))  
    {  
        // Open the ServiceHost to create listeners and start listening for messages.  
        serviceHost.Open();  
  
        // The service can now be accessed.  
        Console.WriteLine("The service is ready.");  
        Console.WriteLine("Press <ENTER> to terminate service.");  
        Console.WriteLine();  
        Console.ReadLine();  
  
        // Close the ServiceHost to shutdown the service.  
        serviceHost.Close();  
    }  
}  
  
```  
  
 El nombre de cola de MSMQ se especifica en la sección appSettings del archivo de configuración.El extremo para el servicio se define en la sección system.ServiceModel del archivo de configuración y especifica el enlace `netMsmqBinding`.  
  
> [!NOTE]
>  El nombre de la cola usa un punto \(.\) para el equipo local y separadores con barra diagonal inversa en su ruta de acceso al crear una cola mediante <xref:System.Messaging>.La dirección de extremo de [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] especifica un esquema net.msmq:, utiliza "localhost" para el equipo local y utiliza barras diagonales en su ruta de acceso.  
  
 Las garantías y duración o la volatilidad de los mensajes también se especifican en la configuración.  
  
```  
<appSettings>  
  <!-- use appSetting to configure MSMQ queue name -->  
  <add key="queueName" value=".\private$\ServiceModelSamplesVolatile" />  
</appSettings>  
  
<system.serviceModel>  
  <services>  
    <service name="Microsoft.ServiceModel.Samples.StockTickerService"  
             behaviorConfiguration="CalculatorServiceBehavior">  
    ...  
      <!-- Define NetMsmqEndpoint -->  
      <endpoint address="net.msmq://localhost/private/ServiceModelSamplesVolatile"  
                binding="netMsmqBinding"  
                bindingConfiguration="volatileBinding"   
                contract="Microsoft.ServiceModel.Samples.IStockTicker" />  
    ...  
          </service>  
  </services>  
  
  <bindings>  
    <netMsmqBinding>  
      <binding name="volatileBinding"   
             durable="false"  
           exactlyOnce="false"/>  
    </netMsmqBinding>  
  </bindings>  
  ...  
</system.serviceModel>  
  
```  
  
 Dado que el ejemplo envía los mensajes en cola utilizando una cola no transaccional, los mensajes con transacciones no se pueden enviar a la cola.  
  
```  
// Create a client.  
Random r = new Random(137);  
  
StockTickerClient client = new StockTickerClient();  
  
float price = 43.23F;  
for (int i = 0; i < 10; i++)  
{  
    float increment = 0.01f * (r.Next(10));  
    client.StockTick("zzz" + i, price + increment);  
}  
  
//Closing the client gracefully cleans up resources.  
client.Close();  
  
```  
  
 Al ejecutar el ejemplo, las actividades del servicio y del cliente se muestran en las ventanas de la consola del cliente y del servicio.Puede ver los mensajes recibidos por el servicio desde el cliente.Presione Entrar en cada ventana de la consola para cerrar el servicio y el cliente.Observe que debido a que se está usando el proceso de poner en cola, el cliente y el servicio no tienen que estar activados y ejecutándose simultáneamente.Puede ejecutar el cliente, cerrarlo e iniciar el servicio y seguir recibiendo mensajes.  
  
```  
The service is ready.  
Press <ENTER> to terminate service.  
  
Stock Tick zzz0:43.25  
Stock Tick zzz1:43.23  
Stock Tick zzz2:43.28  
Stock Tick zzz3:43.3  
Stock Tick zzz4:43.23  
Stock Tick zzz5:43.25  
Stock Tick zzz6:43.25  
Stock Tick zzz7:43.24  
Stock Tick zzz8:43.32  
Stock Tick zzz9:43.3  
```  
  
### Para configurar, compilar y ejecutar el ejemplo  
  
1.  Asegúrese de realizar los [Procedimiento de instalación única para los ejemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Para compilar el código C\# o Visual Basic .NET Edition de la solución, siga las instrucciones de [Compilación de los ejemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Para ejecutar el ejemplo en una configuración de equipos única o cruzada, siga las instrucciones de [Ejecución de los ejemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
 De forma predeterminada, con <xref:System.ServiceModel.NetMsmqBinding> la seguridad de transporte está habilitada.Hay dos propiedades pertinentes para la seguridad de transporte de MSMQ, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> y <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>`.` De forma predeterminada, el modo de autenticación está establecido en `Windows` y el nivel de protección está definido en `Sign`.Para que MSMQ proporcione la autenticación y la característica de firma, debe formar parte de un dominio y debe instalarse la opción de integración de directorio activo para MSMQ.Si ejecuta este ejemplo en un equipo que no cumple estos criterios, recibirá un error.  
  
### Para ejecutar el ejemplo en un equipo unido a un grupo de trabajo o sin la integración del directorio activo  
  
1.  Si su equipo no es parte de un dominio o no tiene la integración del directorio activo instalada, desactive la seguridad de transporte estableciendo el modo de autenticación y el nivel de protección en `None`, tal y como se muestra en el código de configuración de ejemplo siguiente:  
  
    ```  
    <system.serviceModel>  
        <services>  
          <service name="Microsoft.ServiceModel.Samples.StockTickerService"  
                   behaviorConfiguration="StockTickerServiceBehavior">  
            <host>  
              <baseAddresses>  
                <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
              </baseAddresses>  
            </host>  
  
            <!-- Define NetMsmqEndpoint -->  
            <endpoint address="net.msmq://localhost/private/ServiceModelSamplesVolatile"  
                      binding="netMsmqBinding"  
                      bindingConfiguration="volatileBinding"   
                      contract="Microsoft.ServiceModel.Samples.IStockTicker" />  
            <!-- the mex endpoint is explosed at http://localhost:8000/ServiceModelSamples/service/mex -->  
            <endpoint address="mex"  
                      binding="mexHttpBinding"  
                      contract="IMetadataExchange" />  
  
          </service>  
        </services>  
  
        <bindings>  
          <netMsmqBinding>  
            <binding name="volatileBinding"   
                  durable="false"  
                  exactlyOnce="false">  
              <security mode="None" />  
            </binding>  
          </netMsmqBinding>  
        </bindings>  
  
        <behaviors>  
          <serviceBehaviors>  
            <behavior name="StockTickerServiceBehavior">  
              <serviceMetadata httpGetEnabled="True"/>  
            </behavior>  
          </serviceBehaviors>  
        </behaviors>  
  
      </system.serviceModel>  
  
    ```  
  
2.  Asegúrese de que cambia la configuración en el servidor y el cliente antes de ejecutar el ejemplo.  
  
    > [!NOTE]
    >  Establecer `security mode` en `None` es equivalente a definir las propiedades <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> y <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>, y la seguridad de `Message` en `None`.  
  
> [!IMPORTANT]
>  Puede que los ejemplos ya estén instalados en su equipo.Compruebe el siguiente directorio \(valor predeterminado\) antes de continuar.  
>   
>  `<>InstallDrive:\WF_WCF_Samples`  
>   
>  Si no existe este directorio, vaya a la página de [ejemplos de Windows Communication Foundation \(WCF\) y Windows Workflow Foundation \(WF\) Samples para .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para descargar todos los ejemplos de [!INCLUDE[wf1](../../../../includes/wf1-md.md)] y [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].Este ejemplo se encuentra en el siguiente directorio.  
>   
>  `<unidadDeInstalación>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Volatile`  
  
## Vea también