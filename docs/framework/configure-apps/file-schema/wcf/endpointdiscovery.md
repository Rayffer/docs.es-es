---
title: '&lt;endpointDiscovery&gt;'
ms.date: 03/30/2017
ms.assetid: 70812717-888a-4748-9640-0df6715ff029
ms.openlocfilehash: c5971ce79ac2f03fbdc91653d5d282804e98cf8a
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="ltendpointdiscoverygt"></a>&lt;endpointDiscovery&gt;
Especifica las distintas configuraciones de detección para un punto de conexión, como su detectabilidad, ámbitos y cualquier extensión personalizada a sus metadatos.  
  
\<system.ServiceModel>  
\<comportamientos >  
\<endpointBehaviors >  
\<comportamiento >  
\<endpointDiscovery >  
  
## <a name="syntax"></a>Sintaxis  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="String">
      <endpointDiscovery enabled="Boolean">
        <scopes>
          <add scope="URI"/>
        </scopes>
        <extensions />
      </endpointDiscovery>
    </behavior>
  </endpointBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a>Atributos y elementos  
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|enabled|Valor booleano que especifica si la detectabilidad está habilitada en este extremo. De manera predeterminada, es `false`.|  
  
### <a name="child-elements"></a>Elementos secundarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[\<ámbitos >](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)|Colección de URI de ámbito para el punto de conexión. Se puede asociar más de un URI de ámbito a un único punto de conexión.|  
|[\<las extensiones >](../../../../../docs/framework/configure-apps/file-schema/wcf/extensions.md) [de \<endpointDiscovery >]|Colección de elementos XML que le permite especificar metadatos personalizados que se van a publicar para un punto de conexión.|  
|\<tipos >|Una colección de interfaces para buscar.|  
  
### <a name="parent-elements"></a>Elementos primarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[\<comportamiento >](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Especifica un elemento de comportamiento.|  
|||  
  
## <a name="remarks"></a>Comentarios  
 Cuando se agrega a la configuración de comportamiento del extremo y con el atributo `enabled` establecido en `true`, este elemento de configuración habilita su detectabilidad. Además, puede usar el [ \<ámbitos >](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)elemento secundario para especificar el URI que pueden usarse para filtrar los puntos de conexión de servicio durante la consulta, del ámbito personalizado así como el [ \<extensiones >](../../../../../docs/framework/configure-apps/file-schema/wcf/extensions.md) elemento secundario al especificar metadatos personalizados que deben publicarse junto con los metadatos detectables estándar (EPR, ContractTypeName, BindingName, ámbito y ListenURI).  
  
 Este elemento de configuración es dependiente de la [ \<serviceDiscovery >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md) elemento que proporciona el control de nivel de servicio de detectabilidad. Esto significa que la configuración de este elemento se omite si [ \<serviceDiscovery >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md) no está presente en la configuración.  
  
## <a name="example"></a>Ejemplo  
 El siguiente ejemplo de configuración especifica los ámbitos del filtrado y metadatos de la extensión que se van a publicar para un punto de conexión.  
  
```xml  
<services>  
  <service name="CalculatorService"  
           behaviorConfiguration="CalculatorServiceBehavior">  
     <endpoint binding="basicHttpBinding"  
              address="calculator"  
              contract="ICalculatorService"  
              behaviorConfiguration="calculatorEndpointBehavior" />  
  </service>  
</services>  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="CalculatorServiceBehavior">  
      <serviceDiscovery />  
    </behavior>  
  </serviceBehaviors>  
  <endpointBehaviors>  
    <behavior name="calculatorEndpointBehavior">  
      <endpointDiscovery enabled="true">  
        <scopes>  
          <add scope="http://contoso/test1"/>  
          <add scope="http://contoso/test2"/>  
        </scopes>  
        <extensions>  
          <e:Publisher xmlns:e="http://example.org">  
            <e:Name>The Example Organization</e:Name>  
            <e:Address>One Example Way, ExampleTown, EX 12345</e:Address>  
            <e:Contact>support@example.org</e:Contact>  
          </e:Publisher>  
          <AnotherCustomMetadata>Custom Metadata</AnotherCustomMetadata>  
        </extensions>  
      </endpointDiscovery>  
    </behavior>  
  </endpointBehaviors>  
</behaviors>  
```  
  
## <a name="see-also"></a>Vea también  
 <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
