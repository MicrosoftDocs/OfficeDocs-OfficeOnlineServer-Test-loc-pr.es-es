---
title: Introducción a Office Web Apps Server
TOCTitle: 'Introducción: Office Web Apps Server'
ms:assetid: 4b199a88-387f-4121-820d-7af580e2a3e8
ms:mtpsurl: https://technet.microsoft.com/es-es/library/JJ219437(v=office.15)
ms:contentKeyID: 48793523
ms.date: 02/08/2018
mtps_version: v=office.15
ms.translationtype: MT
---

# Introducción a Office Web Apps Server

 

_<strong>Se aplica a:</strong>Office Web Apps Server_

_<strong>Última modificación del tema:**2017-05-26_

**Resumen:** descubra Office Web Apps Server y la funcionalidad de Office basada en explorador que ofrece para hosts compatibles.

**Público:** profesionales de TI

Office Web Apps Server es un nuevo producto de servidor de Office que ofrece versiones basadas en el Explorador de Word, PowerPoint, Excel y OneNote. Un único conjunto de servidor de Office Web Apps puede admitir usuarios que tienen acceso los archivos de OfficeSharePoint 2013, Lync Server 2013, carpetas compartidas y sitios Web. El nuevo modelo de implementación independiente significa que puede administrar actualizaciones al conjunto de servidor de Office Web Apps independientemente de otros productos de servidor de Office que se implementan en la organización.

<table>
<thead>
<tr class="header">
<th><img src="images/JJ219448.important(Office.15).gif" title="Importante" alt="Importante" /> <strong>Importante:</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Este artículo forma parte de <a href="content-roadmap-for-office-web-apps-server.md">Guía básica de contenido de Office Web Apps Server</a>. Use esta guía básica como punto de partida para consultar artículos, descargas y vídeos que le ayuden a implementar y administrar Office Web Apps Server.<br />
<strong>¿Necesita ayuda con Office Web Apps en su escritorio o dispositivo móvil?</strong> Para obtener información, busque &quot;Office Web Apps&quot; en <a href="https://go.microsoft.com/fwlink/p/?linkid=324961">Office.com</a>.</td>
</tr>
</tbody>
</table>


En este artículo:

  - Acerca de Office Web Apps Server

  - Cómo SharePoint 2013 usa Office Web Apps Server para ver y editar documentos de Office

  - Cómo Lync Server 2013 usa Office Web Apps Server para la visualización de difusiones de PowerPoint

  - Cómo Office Web Apps Server habilita la visualización de archivos de Office en carpetas compartidas y sitios web usando Visores en línea

## Acerca de Office Web Apps Server

Office Web Apps Server es un producto de servidor de Office que proporciona el archivo de explorador visualización y edición de servicios para los archivos de Office. Office Web Apps Server trabaja con productos y servicios que admiten WOPI, protocolo de interfaz de plataforma abierta de la aplicación Web. Estos productos, conocidos como hosts, incluyen SharePoint 2013 y Lync Server 2013. Una granja de servidores de Office Web Apps puede proporcionar servicios de Office a varios hosts local y se puede escalar la granja de servidores desde un servidor a varios servidores como aumentan las necesidades de su organización. Aunque Office Web Apps Server requiere servidores dedicados que no se ejecutan otras aplicaciones de servidor, puede instalar Office Web Apps Server en las instancias de la máquina virtual.

Es más fácil de implementar y administrar Office Web Apps dentro de su organización ahora que es un producto independiente. Si implementa SharePoint 2013, por ejemplo, ya no tendrá que optimizar la infraestructura de SharePoint para admitir Office Web Apps, que en versiones anteriores se integra estrechamente con SharePoint Server 2010. También puede aplicar las actualizaciones al conjunto de servidores de Office Web Apps por separado y a una frecuencia distinta de actualizar SharePoint o Lync Server. También tiene un conjunto independiente de Office Web Apps Server significa que los usuarios pueden ver o editar los archivos Office que están almacenados fuera SharePoint Server, como los de las carpetas compartidas o de otros sitios Web. Esta funcionalidad se proporciona mediante una característica conocida como visores en línea.

En la siguiente ilustración se muestran las diferencias entre el anterior modelo de implementación de Office Web Apps y el nuevo modelo independiente de Office Web Apps.

**Diferencias entre los modelos de implementación de Office Web Apps**

![Muestra la diferencia entre el modelo de implementación anterior y el nuevo modelo de implementación independiente para Office Web Apps Server](images/JJ219437.f16dd9d1-c9b7-4c8b-a8de-f1f82c0ee1e2(Office.15).gif "Muestra la diferencia entre el modelo de implementación anterior y el nuevo modelo de implementación independiente para Office Web Apps Server")

## Cómo SharePoint 2013 usa Office Web Apps Server para ver y editar documentos de Office

Cuando se usa con SharePoint Server 2013, Office Web Apps Server proporciona las versiones actualizadas de Word Web App, Excel Web App, PowerPoint Web App y OneNote Web App. Los usuarios pueden ver y, en algunos casos, editar documentos de Office en bibliotecas de SharePoint, con un explorador web compatible en equipos y diversos dispositivos móviles (como Windows Phone, iPhone, iPad y tabletas con Windows 8). Entre las muchas características nuevas de Office Web Apps, las capacidades mejoradas de edición y compatibilidad con tecnología táctil permiten a los usuarios de dispositivos iPad y tabletas con Windows 8 disfrutar de la edición y visualización de documentos de Office directamente desde sus dispositivos.

La siguiente ilustración resume las capacidades de visualización y edición de Office Web Apps en distintos tipos de dispositivos.

**Capacidades de edición y visualización de Office Web Apps**

![Un gráfico en el que se resumen las capacidades de edición y visualización de Office Web Apps en distintos tipos de dispositivos. Se destacan aquellos que están optimizados para las pantallas táctiles.](images/Ff431685.8bf76669-f511-4e02-8ed3-d658e9e746f0(Office.15).gif "Un gráfico en el que se resumen las capacidades de edición y visualización de Office Web Apps en distintos tipos de dispositivos. Se destacan aquellos que están optimizados para las pantallas táctiles.")


> [!NOTE]
> Aunque la difusión de PowerPoint se ha quitado de SharePoint 2013, todavía se encuentra disponible a través de OneDrive y Lync Server 2013.



Para más información sobre las novedades en Office Web Apps, consulte [Cómo funciona Office Web Apps en implementaciones locales con SharePoint 2013](how-office-web-apps-work-on-premises-with-sharepoint-2013.md).

## Cómo Lync Server 2013 usa Office Web Apps Server para la visualización de difusiones de PowerPoint

En Lync Server 2010, las presentaciones de PowerPoint se ven de dos maneras. Para usuarios que ejecutan Lync 2010, las presentaciones de PowerPoint se muestran usando el formato 97-2003 de PowerPoint y se visualizan usando una copia incrustada del visor de PowerPoint. Para usuarios que ejecutan Lync Web App, las presentaciones de PowerPoint se convierten en archivos HTML dinámicos que se visualizan después usando una combinación de los archivos DHTML personalizados y Silverlight. Aunque normalmente es efectivo, este enfoque tenía algunas limitaciones:

  - El Visor incrustado de PowerPoint (que proporcionaba una experiencia de visualización más óptima) solo está disponible en la plataforma de Windows.

  - Muchos dispositivos móviles (incluidos algunos de los teléfonos móviles más populares) no admiten Silverlight.
    
    Ni el enfoque del Visor de PowerPoint ni el del DHTML/Silverlight admiten todas las características (incluyendo las transiciones de diapositivas y el vídeo incrustado) que se encuentran en las ediciones más recientes de PowerPoint.

Para ayudar a abordar estas cuestiones y para mejorar la experiencia general de cualquier usuario que presente o vea presentaciones de PowerPoint, Lync Server 2013 usa Office Web Apps Server para administrar las presentaciones de PowerPoint. Entre otras ventajas, este nuevo enfoque permite las siguientes capacidades:

  - Capacidades de visualización de mayor resolución y mejor compatibilidad con PowerPoint como animaciones, transiciones de diapositivas y vídeo incrustado.

  - Otros dispositivos móviles pueden tener acceso a estas presentaciones. Esto se debe a que Lync Server 2013 usa DHTML estándar y JavaScript para retransmitir presentaciones de PowerPoint en lugar de DHTML personalizado y Silverlight.

  - Los usuarios que tienen privilegios adecuados pueden desplazarse por una presentación de PowerPoint independiente de la propia presentación. Por ejemplo, mientras Ken Myer hace la presentación con diapositivas, Pilar Ackerman puede desplazarse y ver cualquier diapositiva que desee, sin que ello afecte a la presentación de Ken.

Para obtener más información acerca de cómo configurar Lync Server 2013 para usar Office Web Apps Server, vea [implementación de servidor de Office Web Apps y Lync Server 2013](https://go.microsoft.com/fwlink/p/?linkid=256902).

## Cómo Office Web Apps Server permite a los usuarios ver archivos de Office en carpetas compartidas y sitios web usando Visores en línea

Visores en línea permite a los usuarios hacer uso de un explorador web para ver archivos de Excel, PowerPoint y Word que están almacenados en servidores web o carpetas compartidas de una organización. Los usuarios pueden ver archivos de Office en un explorador web sin tener que abrir una aplicación por separado. Además, Visores en línea, no requiere la instalación de Office 2013 en los equipos de los usuarios. Visores en línea también genera el código necesario para vincular o incrustar la dirección URL en una página web. Puede usar Visores en línea en su Intranet o en Internet.

Office Web Apps Server proporciona una página en la dirección http://*OfficeWebAppsServername*/op/generate.aspx que permite generar vínculos a los documentos disponibles públicamente que disponen de direcciones UNC o URL. Cuando un usuario selecciona una de las direcciones URL que se han generado, Visores en línea habilita Office Web Apps Server para obtener el archivo desde su ubicación y representarlo con Office Web Apps. El usuario puede ver el archivo de Word, Excel o PowerPoint en un explorador con características de Office intactas. El formato y el diseño en los documentos de Word se mantienen, los datos de los libros de Excel se pueden filtrar y ordenar, y se reproducen las animaciones de las presentaciones de PowerPoint. Sin embargo, debe tener en cuenta que Visores en línea permite a los usuarios ver archivo, pero no editarlos, y que no podrá abrir archivos que requieran autenticación.

Encontrará más información sobre Visores en línea en [Planeación de Visores en línea](plan-office-web-apps-server.md).


> [!NOTE]
> Microsoft hospeda una versión orientada solo a Internet de Crear dirección URL en <A href="http://go.microsoft.com/fwlink/?linkid=256548">Office.com</A>.



## Consulte también


[Guía básica de contenido de Office Web Apps Server](content-roadmap-for-office-web-apps-server.md)  
[Planear Office Web Apps Server](plan-office-web-apps-server.md)  
[Implementar Office Web Apps Server](deploy-office-web-apps-server.md)  
  

[https://technet.microsoft.com/es-es/library/jj219455](deploy-office-web-apps-server.md)

