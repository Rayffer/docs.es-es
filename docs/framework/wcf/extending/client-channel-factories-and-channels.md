---
title: "Cliente: generadores de canales y canales | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ef245191-fdab-4468-a0da-7c6f25d2110f
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# Cliente: generadores de canales y canales
Este tema describe la creación de generadores de canales y de canales.  
  
## Generadores de canales y canales  
 Los generadores de canales son responsables de la creación de canales.  Los canales creados por los generadores de canales se utilizan para enviar mensajes.  Estos canales son responsables de obtener el mensaje de la capa anterior, realizando cualquier procesamiento necesario, y, a continuación, de enviar el mensaje a la capa inferior.  El siguiente gráfico ilustra este proceso.  
  
 ![Generadores cliente y canales](../../../../docs/framework/wcf/extending/media/wcfc-wcfchannelsigure2highlevelfactgoriesc.gif "wcfc\_WCFChannelsigure2HIghLevelFactgoriesc")  
Un generador de canales crea canales.  
  
 Cuando se cierran, los generadores de canales son responsables de cerrar cualquier canal creado por ellos que aún no se haya cerrado.  Tenga en cuenta que, en el ejemplo, el modelo es asimétrico debido a que cuando se cierra un agente de escucha del canal solo detiene la aceptación de nuevos canales, pero mantiene abiertos los canales existentes de modo que pueden continuar recibiendo mensajes.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] proporciona los elementos auxiliares de clase base para este proceso.  \(Para consultar un diagrama de las clases auxiliares de canal descritas en este tema, vea [Información general del modelo de canales](../../../../docs/framework/wcf/extending/channel-model-overview.md)\).  
  
-   La clase <xref:System.ServiceModel.Channels.CommunicationObject> implementa <xref:System.ServiceModel.ICommunicationObject> y exige el estado de equipo descrito en el paso 2 de [Desarrollo de canales](../../../../docs/framework/wcf/extending/developing-channels.md).  
  
-   La clase  `` <xref:System.ServiceModel.Channels.ChannelManagerBase> implementa <xref:System.ServiceModel.Channels.CommunicationObject> y proporciona una clase base unificada para <xref:System.ServiceModel.Channels.ChannelFactoryBase?displayProperty=fullName> y <xref:System.ServiceModel.Channels.ChannelListenerBase?displayProperty=fullName>.  La clase <xref:System.ServiceModel.Channels.ChannelManagerBase> trabaja junto con <xref:System.ServiceModel.Channels.ChannelBase>, que es una clase base que implementa <xref:System.ServiceModel.Channels.IChannel>.  
  
-   La clase  `` <xref:System.ServiceModel.Channels.ChannelFactoryBase> implementa <xref:System.ServiceModel.Channels.ChannelManagerBase> y <xref:System.ServiceModel.Channels.IChannelFactory>, y consolida las sobrecargas de `CreateChannel` en un método abstracto `OnCreateChannel`.  
  
-   La clase  `` <xref:System.ServiceModel.Channels.ChannelListenerBase> implementa <xref:System.ServiceModel.Channels.IChannelListener>.  Se encarga de la administración de estados básica.  
  
 La siguiente descripción está basada en el ejemplo [Transporte: UDP](../../../../docs/framework/wcf/samples/transport-udp.md).  
  
### Creación de un generador de canales  
 La clase `UdpChannelFactory` se deriva de la clase <xref:System.ServiceModel.Channels.ChannelFactoryBase>.  El ejemplo invalida <xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A> para proporcionar acceso a la versión del mensaje del codificador de mensajes.  El ejemplo también invalida <xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A> para anular nuestra instancia de <xref:System.ServiceModel.Channels.BufferManager> cuando se realizan las transiciones del equipo de estados.  
  
#### Canal de salida UDP  
 La clase `UdpOutputChannel` implementa la interfaz <xref:System.ServiceModel.Channels.IOutputChannel>.  El constructor valida los argumentos y construye un objeto de destino <xref:System.Net.EndPoint> basado en la <xref:System.ServiceModel.EndpointAddress> a la que se pasa.  
  
 La invalidación de <xref:System.ServiceModel.Channels.CommunicationObject.OnOpen%2A> crea un socket que se utiliza para enviar los mensajes a <xref:System.Net.EndPoint>.  
  
 `this.socket = new Socket(`  
  
 `this.remoteEndPoint.AddressFamily,`  
  
 `SocketType.Dgram,`  
  
 `ProtocolType.Udp`  
  
 `);`  
  
 El canal puede cerrarse de forma correcta o incorrecta.  Si el canal se cierra correctamente, el socket se cierra y se realiza una llamada al método `OnClose` de la clase base.  Si se inicia una excepción, la infraestructura llama a `Abort` para garantizar que se limpia el canal.  
  
```  
this.socket.Close();  
base.OnClose(timeout);  
  
```  
  
 Implemente `Send()` y `BeginSend()`\/`EndSend()`.  De este modo se divide en dos secciones principales.  Primero se serializa el mensaje en una matriz de bytes:  
  
```  
ArraySegment<byte> messageBuffer = EncodeMessage(message);  
  
```  
  
 A continuación, se envían los datos resultantes en la conexión:  
  
```  
this.socket.SendTo(  
  messageBuffer.Array,   
  messageBuffer.Offset,   
  messageBuffer.Count,   
  SocketFlags.None,   
  this.remoteEndPoint  
);  
```  
  
## Vea también  
 [Desarrollo de canales](../../../../docs/framework/wcf/extending/developing-channels.md)