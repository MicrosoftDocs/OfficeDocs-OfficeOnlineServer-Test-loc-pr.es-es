---
title: Planificar Office Web Apps (cuando se usa con SharePoint 2013)
TOCTitle: Planificar Office Web Apps
ms:assetid: 3bd0a617-5f12-4a7e-bb75-b15c86c7e504
ms:mtpsurl: https://technet.microsoft.com/es-es/library/Ff431682(v=office.15)
ms:contentKeyID: 48793522
ms.date: 12/18/2017
mtps_version: v=office.15
ms.translationtype: HT
---

# Planificar Office Web Apps (cuando se usa con SharePoint 2013)

 

_**Se aplica a:** Office Web Apps, SharePoint Foundation 2013, SharePoint Server 2013_

_**Última modificación del tema:** 2016-12-16_

**Resumen:** revise la guía de planeación para Office Web Apps cuando se usa con SharePoint 2013 en implementaciones locales.

**Público:** profesionales de TI

Para planear cómo debe usarse Office Web Apps con SharePoint 2013 en implementaciones locales, es necesario revisar la compatibilidad del explorador, los requisitos de autenticación de SharePoint y otras consideraciones relacionadas con las licencias respecto a la visualización y edición de archivos de Office con Office Web Apps. A continuación, podrá decidir si SharePoint 2013 debe usar el explorador web o una aplicación cliente cuando un usuario abra archivos de Office desde una biblioteca de documentos de SharePoint 2013.

> [!IMPORTANT]
> Este artículo forma parte de <a href="content-roadmap-for-office-web-apps-server.md">Guía básica de contenido de Office Web Apps Server</a>. Use esta guía básica como punto de partida para consultar artículos, descargas y vídeos que le ayuden a implementar y administrar Office Web Apps Server.<br />
<strong>¿Necesita ayuda con Office Web Apps en su escritorio o dispositivo móvil?</strong> Puede encontrar esta información buscando &quot;Office Web Apps&quot; en <a href="http://go.microsoft.com/fwlink/p/?linkid=324961">Office.com</a>.


En este artículo:

  - Acerca de la planeación para Office Web Apps

  - Exploradores admitidos para Office Web Apps

  - Requisitos de autenticación de SharePoint para Office Web Apps

  - Concesión de licencias de Office Web Apps para la edición de archivos de Office

  - Consideraciones para los clientes que realizan la actualización desde SharePoint 2010 con el método de conexión de una base de datos

  - Comportamiento de apertura predeterminado para los documentos abiertos desde bibliotecas de documentos de SharePoint 2013

## Acerca de la planeación para Office Web Apps

La guía de este artículo es un subconjunto de la planeación general que hará cuando implemente Office Web Apps Server en local en su organización. Por ejemplo, los requisitos de hardware, software y virtualización, el tamaño y la topología de la granja de servidores y la seguridad son parte de la planeación de Office Web Apps Server. Después de realizar estas decisiones, puede planear cómo configurar la funcionalidad de Office Web Apps que es específica de SharePoint 2013. Si no ha oído hablar de Office Web Apps Server ni ha revisado sus requisitos y su guía de planeación, consulte [Introducción a Office Web Apps Server](office-web-apps-server-overview.md) y [Planear Office Web Apps Server](plan-office-web-apps-server.md).

## Exploradores admitidos para Office Web Apps

Los exploradores admitidos para Office Web Apps son los mismos que para SharePoint 2013. Consulte el artículo [Planear la compatibilidad con exploradores en SharePoint 2013](https://technet.microsoft.com/es-es/library/cc263526\(v=office.15\)) para más información.

## Requisitos de autenticación de SharePoint para Office Web Apps

Office Web Apps solo pueden usarlo aplicaciones web de SharePoint 2013 que usen autenticación basada en notificaciones. La representación y la edición de Office Web Apps no funcionará en aplicaciones web de SharePoint 2013 que usen el modo de autenticación clásico. Si migra aplicaciones web de SharePoint 2010 que usen la autenticación de modo clásico a SharePoint 2013, debe migrarlas a la autenticación basada en notificaciones para permitir que funcionen con Office Web Apps. Para más información, consulte [Migrar del modo clásico a autenticaciones basadas en notificaciones en SharePoint 2013](https://technet.microsoft.com/es-es/library/gg251985\(v=office.15\)).

## Concesión de licencias de Office Web Apps para la edición de archivos de Office

Los clientes empresariales que hayan obtenido una licencia de Office 2013 a través de un programa de licencias por volumen pueden habilitar la edición de Office Web Apps para las implementaciones locales de SharePoint 2013. De este modo se garantiza que los usuarios dispondrán de las capacidades de edición de Office, tanto en casa como en otras ubicaciones donde posiblemente no se hayan instalado clientes de Office.

Para obtener información exacta sobre su licencia, consulte los Términos de licencia del software de Microsoft que aparecen al instalar Office Web Apps Server. Para obtener más información sobre cómo funcionan las licencias en SharePoint 2013, consulte [Configurar licencias en SharePoint Server 2013](https://technet.microsoft.com/es-es/library/jj219627\(v=office.15\)).

## Consideraciones para los clientes que realizan la actualización desde SharePoint 2010 con el método de conexión de una base de datos

Si ha instalado Office Web Apps junto con SharePoint 2010, puede ocurrir que Office Web Apps deje de estar disponible cuando actualice a SharePoint 2013. En primer lugar debe implementar Office Web Apps Server y después debe conectarle SharePoint 2013 tras actualizar las bases de datos de contenido. No es necesario que espere hasta que las colecciones de sitios se actualicen, porque Office Web Apps Server es compatible con los modos de las colecciones de sitios de ambas versiones (2010 y 2013) de SharePoint 2013. Para más información sobre el método de conexión de una base de datos, consulte [Información general sobre el proceso de actualización a SharePoint 2013](https://technet.microsoft.com/es-es/library/cc262483\(v=office.15\)).

## Comportamiento de apertura predeterminado para los documentos abiertos desde bibliotecas de documentos de SharePoint 2013

Puede configurar si los archivos de Word, PowerPoint, Excel y OneNote se abren en una aplicación cliente (si está instalada) o en el explorador. De manera predeterminada, después de configurar SharePoint 2013 para usar Office Web Apps Server, los archivos de Office se abren en el explorador. Hay dos maneras de cambiar el comportamiento predeterminado para abrir archivos directamente:

  - **Para la granja de servidores de SharePoint 2013** Puede ajustar el comportamiento de apertura predeterminado por tipo de archivo para la granja de servidores de SharePoint 2013 con los cmdlets [New-SPWOPIBinding](https://docs.microsoft.com/en-us/powershell/module/sharepoint-server/New-SPWOPIBinding?view=sharepoint-ps) y [Set-SPWOPIBinding](https://docs.microsoft.com/en-us/powershell/module/sharepoint-server/Set-SPWOPIBinding?view=sharepoint-ps) de Windows PowerShell.

  - **En colecciones de sitios o bibliotecas de documentos** Los administradores y los usuarios de colecciones de sitios pueden especificar si los archivos de Office se abren en las aplicaciones cliente si están instaladas. Los usuarios pueden cambiar esta configuración en las propiedades de las bibliotecas de documentos y los administradores de colecciones de sitios pueden cambiarlo en Administración de la colección de sitios o usando el cmdlet Install-SPFeature para instalar la característica OpenInClient. Para más información, consulte [Install-SPFeature](https://technet.microsoft.com/es-es/library/ff607825\(v=office.15\)).

## Consulte también


[Guía básica de contenido de Office Web Apps Server](content-roadmap-for-office-web-apps-server.md)  
[Cómo funciona Office Web Apps en implementaciones locales con SharePoint 2013](how-office-web-apps-work-on-premises-with-sharepoint-2013.md)  


[In a test environment that uses HTTP](configure-office-web-apps-for-sharepoint-2013.md)  
  

[](how-office-web-apps-work-on-premises-with-sharepoint-2013.md)

