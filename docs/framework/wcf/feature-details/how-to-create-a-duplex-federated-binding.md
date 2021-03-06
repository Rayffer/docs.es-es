---
title: Procedimiento para crear un enlace federado dúplex
ms.date: 03/30/2017
ms.assetid: 4331d2bc-5455-492a-9189-634a82597726
ms.openlocfilehash: d736d0119f3e938d81a15d57bb6d97ca2a1990fa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-duplex-federated-binding"></a>Procedimiento para crear un enlace federado dúplex
<xref:System.ServiceModel.WSFederationHttpBinding> solo admite los contratos de intercambio de mensajes de datagrama y solicitud/respuesta. Para utilizar el contrato de intercambio de mensajes dúplex, debe crear un enlace personalizado. Los procedimientos siguientes muestran cómo conseguirlo mediante configuración, utilizando la seguridad de modo de mensaje para los transportes TCP y HTTP, y la seguridad de modo mixto para el transporte TCP. El ejemplo de código donde se muestran los tres enlaces se encuentra al final de este tema.  
  
 También puede crear el enlace en el código. Para obtener una descripción de la pila de elementos de enlace para crear, vea [Cómo: crear un enlace personalizado mediante SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).  
  
### <a name="to-create-a-duplex-federated-custom-binding-with-http"></a>Para crear un enlace personalizado federado dúplex con HTTP  
  
1.  En el [ \<enlaces >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) nodo del archivo de configuración, cree un [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) elemento.  
  
2.  Dentro de la [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) elemento, crear una [ \<enlace >](../../../../docs/framework/misc/binding.md) elemento con la `name` atributo establecido en `FederationDuplexHttpMessageSecurityBinding`.  
  
3.  Dentro de la [ \<enlace >](../../../../docs/framework/misc/binding.md) elemento, crear una [ \<seguridad >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) elemento con la `authenticationMode` atributo establecido en `SecureConversation`.  
  
4.  Dentro de la [ \<seguridad >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) elemento, crear una [ \<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) elemento con la `authenticationMode` atributo establecido en `IssuedTokenForCertificate` o `IssuedTokenForSslNegotiated`.  
  
5.  Después de la [ \<seguridad >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) elemento, crear vacío [ \<compositeDuplex >](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md) elemento.  
  
6.  Después de la [ \<compositeDuplex >](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md) elemento, crear vacío [ \<oneWay >](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) elemento.  
  
7.  Después de la [ \<oneWay >](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) elemento, crear vacío [ \<httpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md) elemento.  
  
### <a name="to-create-a-duplex-federated-custom-binding-with-tcp-message-security-mode"></a>Para crear un enlace personalizado federado dúplex con el modo de seguridad de mensajes TCP  
  
1.  En el [ \<enlaces >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) nodo del archivo de configuración, cree un [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) elemento.   
  
2.  Dentro de la [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) elemento, crear una [ \<enlace >](../../../../docs/framework/misc/binding.md) elemento con la `name` atributo establecido en `FederationDuplexTcpMessageSecurityBinding`.  
  
3.  Dentro de la [ \<enlace >](../../../../docs/framework/misc/binding.md) elemento, crear una [ \<seguridad >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) elemento con la `authenticationMode` atributo establecido en `SecureConversation`.  
  
4.  Dentro de la [ \<seguridad >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) elemento, crear una [ \<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) elemento con la `authenticationMode` atributo establecido en `IssuedTokenForCertificate` o `IssuedTokenForSslNegotiated`.  
  
5.  Después de la [ \<seguridad >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) elemento, crear vacío [ \<tcpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) elemento.  
  
### <a name="to-create-a-duplex-federated-custom-binding-with-tcp-mixed-security-mode"></a>Para crear un enlace personalizado federado dúplex con el modo de seguridad mixto TCP  
  
1.  En el [ \<enlaces >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) nodo del archivo de configuración, cree un [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) elemento.   
  
2.  Dentro de la [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) elemento, crear una [ \<enlace >](../../../../docs/framework/misc/binding.md) elemento con la `name` atributo establecido en `FederationDuplexTcpTransportSecurityWithMessageCredentialBinding`.  
  
3.  Dentro de la [ \<enlace >](../../../../docs/framework/misc/binding.md) elemento, crear una [ \<seguridad >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) elemento con la `authenticationMode` atributo establecido en `SecureConversation`.  
  
4.  Dentro de la [ \<seguridad >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) elemento, crear una [ \<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) elemento con la `authenticationMode` atributo establecido en `IssuedTokenForCertificate` o `IssuedTokenForSslNegotiated`.  
  
5.  Después de la [ \<seguridad >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) elemento, crear vacío [ \<sslStreamSecurity >](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md) elemento.  
  
6.  Después de la [ \<sslStreamSecurity >](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md) elemento, crear vacío [ \<tcpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) elemento.  
  
## <a name="code-sample"></a>Ejemplo de código  
  
#### <a name="sample-with-3-bindings"></a>Ejemplo con tres enlaces  
  
1.  Inserte el código siguiente en su archivo de configuración.  
  
## <a name="example"></a>Ejemplo  
  
```xml  
<bindings>  
   <customBinding>  
      <binding name="FederationDuplexHttpMessageSecurityBinding">  
<!-- duplex contract requires secure conversation with require cancellation = true -->  
          <security authenticationMode="SecureConversation">  
              <secureConversationBootstrap authenticationMode="IssuedTokenForSslNegotiated" />  
          </security>  
          <compositeDuplex />  
          <oneWay />  
          <httpTransport />  
       </binding>  
<!-- duplex over https is not supported -->  
       <binding name="FederationDuplexTcpMessageSecurityBinding">  
<!-- duplex contract requires secure conversation with require cancellation = true -->  
          <security authenticationMode="SecureConversation">  
              <secureConversationBootstrap authenticationMode="IssuedTokenForSslNegotiated" />  
          </security>  
          <tcpTransport />  
       </binding>              
       <binding name="FederationDuplexTcpTransportSecurityWithMessageCredentialsBinding">  
<!-- duplex contract requires secure conversation with require cancellation = true -->  
          <security authenticationMode="SecureConversation">  
              <secureConversationBootstrap authenticationMode="IssuedTokenOverTransport" />  
          </security>  
<!-- requireClientCertificate = true or <windowsStreamSecurity /> can be used, but does not make sense for most scenarios -->  
          <sslStreamSecurity />  
          <tcpTransport />  
       </binding>              
    </customBinding>  
</bindings>  
```
