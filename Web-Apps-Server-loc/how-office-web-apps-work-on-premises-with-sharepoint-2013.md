---
title: Cómo funciona Office Web Apps en implementaciones locales con SharePoint 2013
TOCTitle: Office Web Apps en implementaciones locales con SharePoint 2013
ms:assetid: 8480064e-14a4-4b46-ad6b-0c836b192af2
ms:mtpsurl: https://technet.microsoft.com/es-es/library/Ff431685(v=office.15)
ms:contentKeyID: 48793531
ms.date: 01/30/2018
mtps_version: v=office.15
ms.translationtype: HT
---

# Cómo funciona Office Web Apps en implementaciones locales con SharePoint 2013

 
_<strong>Se aplica a:</strong>Office Web Apps, SharePoint Foundation 2013, SharePoint Server 2013_

_<strong>Última modificación del tema:</strong>2016-12-16_


**Resumen:** proporciona información acerca de Office Web Apps, Office Web Apps Server y su funcionamiento en implementaciones locales con SharePoint 2013.

**Audiencia**: profesionales de TI

Cuando se usa con SharePoint Server 2013, Office Web Apps Server ofrece versiones actualizadas de Word Web App, Excel Web App, PowerPoint Web App y OneNote Web App. Los usuarios pueden ver y, en algunos casos, editar documentos de Office en bibliotecas de SharePoint con un explorador web compatible en equipos y en diversos dispositivos móviles, como Windows Phone, iPhone, iPad, tabletas Windows 8 y dispositivos Android.


**Figura: capacidades de edición y visualización de Office Web Apps en distintos tipos de dispositivos.**

![Un gráfico en el que se resumen las capacidades de edición y visualización de Office Web Apps en distintos tipos de dispositivos. Se destacan aquellos que están optimizados para las pantallas táctiles.](images/Ff431685.8bf76669-f511-4e02-8ed3-d658e9e746f0(Office.15).gif "Un gráfico en el que se resumen las capacidades de edición y visualización de Office Web Apps en distintos tipos de dispositivos. Se destacan aquellos que están optimizados para las pantallas táctiles.")

## Office Web Apps Server ahora se instala como un servidor independiente

Office Web Apps no se instala en los mismos servidores que ejecutan SharePoint 2013. Lo que se hace es implementar uno o varios servidores físicos o virtuales que ejecutan Office Web Apps Server. Después se configura la granja de servidores de SharePoint 2013 para que use la granja de servidores de Office Web Apps Server y ofrezca las funciones de Office Web Apps a los usuarios que creen o abran archivos de Office desde las bibliotecas de SharePoint. Para más información, vea [Introducción a Office Web Apps Server](office-web-apps-server-overview.md).

## Opciones de licencias de Office Web Apps cuando se usa con SharePoint 2013

Las licencias de Office Web Apps ofrecen dos opciones:

  - **Solo visualización:** de manera predeterminada, Office Web Apps es de solo visualización. La función de solo visualización se ofrece de forma gratuita.

  - **Editar y ver:** deberá comprar una licencia de edición para usar las características de edición de Office Web Apps con SharePoint 2013. La edición se habilita al crear la granja de servidores de Office Web Apps Server.

Si su organización ha obtenido una licencia de Office 2013 con un programa de licencias por volumen, puede habilitar la edición de Office Web Apps para las implementaciones locales de SharePoint 2013. De este modo, se garantiza que los usuarios dispondrán de las capacidades de edición de Office tanto en casa como en otras ubicaciones donde no haya instalados clientes de Office. Las licencias de edición de Office Web Apps no pueden comprarse por separado.

Si quiere detalles exactos sobre su licencia, lea los Términos de licencia del software de Microsoft que aparecen al instalar Office Web Apps Server.

SharePoint 2013 ofrece un nuevo cumplimiento de licencia que funciona con Office Web Apps. Si habilita la licencia de SharePoint y, después, la edición de Office Web Apps, solo los usuarios con la licencia adecuada podrán editar archivos de Office en un explorador. Si no se aplican licencias de edición de Office Web Apps a los usuarios, solo se permitirá la visualización.

Para más información sobre cómo funcionan las licencias de SharePoint 2013, vea [Configurar licencias en SharePoint Server 2013](https://technet.microsoft.com/es-es/library/jj219627\(v=office.15\)). El parámetro EditingEnabled que habilita la edición se describe en [New-OfficeWebAppsFarm](https://docs.microsoft.com/en-us/powershell/module/officewebapps/new-officewebappsfarm?view=officewebapps-ps) y en [Set-OfficeWebAppsFarm](https://docs.microsoft.com/en-us/powershell/module/officewebapps/set-officewebappsfarm?view=officewebapps-ps).

Los archivos que se envían con la característica Compartir un vínculo de SharePoint 2013 pueden editarse en Office Web Apps aunque no haya ninguna licencia de edición y la edición esté deshabilitada en la granja de servidores de Office Web Apps Server.

## Usar visores de Office Mobile para acceder a los archivos de sitios de SharePoint

Office Web Apps Server proporciona visores de Office Mobile para poner Office Web Apps a disposición de los usuarios móviles que acceden a sitios de SharePoint Server. De manera predeterminada, estos visores están habilitados, pero el administrador del sitio de SharePoint Server los puede deshabilitar. Cuando están habilitados, los usuarios pueden navegar al sitio de SharePoint Server con el explorador del dispositivo móvil y pulsar el documento que quieren abrir en la biblioteca de SharePoint Server. El documento se abrirá en el explorador móvil.

Puede encontrar más detalles sobre las bibliotecas de SharePoint en dispositivos móviles en [What's new for mobile devices in SharePoint 2013](https://technet.microsoft.com/es-es/library/fp161352\(v=office.15\)) y en [Introducción a los dispositivos móviles y SharePoint Server 2013](https://technet.microsoft.com/es-es/library/fp161351\(v=office.15\)). Los usuarios pueden obtener más información sobre cómo usar los visores de Office Mobile en su dispositivo móvil en el tema acerca de cómo [usar Office Web Apps en Android, iPhone o Windows Phone](http://office.microsoft.com/es-es/web-apps-help/usar-office-web-apps-en-android-iphone-o-windows-phone-ha010389583.aspx). Si decide deshabilitar los visores de Office Mobile en SharePoint 2013, use el cmdlet [Remove-SPWOPIBinding](https://docs.microsoft.com/en-us/powershell/module/sharepoint-server/Remove-SPWOPIBinding?view=sharepoint-ps).

## Diferencias entre Excel Web App y Servicios de Excel en SharePoint

Excel Web App y Servicios de Excel en SharePoint tienen mucho en común, pero no son iguales. Servicios de Excel solo se encuentra disponible en la edición Enterprise de SharePoint Server 2013. Excel Web App está disponible en SharePoint Server 2013 y en SharePoint Foundation 2013. Ambas aplicaciones permiten ver libros en una ventana del explorador, interactuar con datos y explorarlos.

Pero hay algunas diferencias entre Excel Web App y Servicios de Excel en SharePoint. Por ejemplo, Servicios de Excel es compatible con conexiones de datos externas, con modelos de datos y con la capacidad de interactuar con los elementos que los usan (como informes de gráfico dinámico o de tabla dinámica y controles de escala de tiempo). Servicios de Excel ofrece más funciones de inteligencia empresarial que Excel Web App, pero en Servicios de Excel los usuarios no pueden crear ni editar libros en una ventana del explorador.

Para obtener información detallada sobre las diferencias entre Excel Web App y Servicios de Excel, vea [Información general sobre Servicios de Excel en SharePoint Server 2013](https://technet.microsoft.com/es-es/library/ee424405\(v=office.15\)) y el tema sobre la [comparación entre Servicios de Excel en SharePoint y Excel Web App](http://office.microsoft.com/es-es/comparing-excel-services-in-sharepoint-to-excel-web-app-ha102832426.aspx).

Si la organización decide usar Servicios de Excel en lugar de Excel Web App para ver libros en el explorador, puede usar el cmdlet de Windows PowerShell **New-SPWOPISuppressionSettings** para desactivar Excel Web App para libros de Excel. Para más información, vea [New-SPWOPISuppressionSetting](https://docs.microsoft.com/en-us/powershell/module/sharepoint-server/New-SPWOPISuppressionSetting?view=sharepoint-ps).

## Consulte también


[Guía básica de contenido de Office Web Apps Server](content-roadmap-for-office-web-apps-server.md)  
[Planificar Office Web Apps (cuando se usa con SharePoint 2013)](plan-office-web-apps-used-with-sharepoint-2013.md)  
  

[](plan-office-web-apps-used-with-sharepoint-2013.md)

