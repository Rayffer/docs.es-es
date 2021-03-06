---
title: '&lt;dateTimeSerialization&gt; (Elemento)'
ms.date: 03/30/2017
helpviewer_keywords:
- dateTimeSerialization element
- XML serialization, configuration
- <dateTimeSerialization> element
ms.assetid: 90fda55c-7730-41e9-bc4b-6423a4b920af
ms.openlocfilehash: 5e48753b5e8383a1ad946a29636e30ef07ceee9c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="ltdatetimeserializationgt-element"></a>&lt;dateTimeSerialization&gt; (Elemento)
Determina el modo de serialización XML de los objetos <xref:System.DateTime>.  
  
 \<configuration>  
\<dateTimeSerialization>  
  
## <a name="syntax"></a>Sintaxis  
  
```xml  
<dateTimeSerialization  
    mode = "Roundtrip" | "Local"  
/>  
```  
  
## <a name="attributes-and-elements"></a>Atributos y elementos  
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### <a name="attributes"></a>Atributos  
  
|Atributos|Descripción|  
|----------------|-----------------|  
|`mode`|Opcional. Especifica el modo de serialización. Establece uno de los valores de <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode> . El valor predeterminado es **RoundTrip**.|  
  
### <a name="child-elements"></a>Elementos secundarios  
 Ninguno.  
  
### <a name="parent-elements"></a>Elementos primarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|system.xml.serialization|El elemento de nivel superior para controlar la serialización XML.|  
  
## <a name="remarks"></a>Comentarios  
 En las versiones 1.0, 1.1, 2.0 y posteriores de .NET Framework, cuando esta propiedad se establece en **Local**, los objetos <xref:System.DateTime> siempre reciben formato según la hora local. Es decir, la información de zona horaria local siempre se incluye con los datos serializados. Establezca esta propiedad en **Local** para garantizar la compatibilidad con las versiones anteriores de .NET Framework.  
  
 En la versión 2.0 y posteriores de .NET Framework que tienen esta propiedad establecida en **Roundtrip**, los objetos <xref:System.DateTime> se examinan para determinar si están en la zona horaria local, UTC o una no especificada. Los objetos <xref:System.DateTime> se serializan a continuación de este tipo de manera que esta información se conserva. Éste es el comportamiento predeterminado y el que se recomienda para todas las aplicaciones nuevas que no funcionan con versiones anteriores de .Net Framework.  
  
## <a name="see-also"></a>Vea también  
 <xref:System.DateTime>  
 <xref:System.Xml.Serialization.XmlSchemaImporter>  
 <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>  
 [Esquema de los archivos de configuración](../../../docs/framework/configure-apps/file-schema/index.md)  
 [Elemento \<schemaImporterExtensions>](../../../docs/standard/serialization/schemaimporterextensions-element.md)  
 [Elemento \<add> de \<xmlSchemaImporterExtensions>](../../../docs/standard/serialization/add-element-for-xmlschemaimporterextensions.md)  
 [Elemento \<system.xml.serialization>](../../../docs/standard/serialization/system-xml-serialization-element.md)
