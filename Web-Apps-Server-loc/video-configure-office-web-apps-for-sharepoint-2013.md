---
title: 'Vídeo: Configurar Office Web Apps para SharePoint 2013'
TOCTitle: 'Vídeo: Configurar Office Web Apps para SharePoint 2013'
ms:assetid: 0c02633f-3839-448b-ae83-24f24c254179
ms:mtpsurl: https://technet.microsoft.com/es-es/library/Dn455088(v=office.15)
ms:contentKeyID: 59152174
ms.date: 12/18/2017
mtps_version: v=office.15
ms.translationtype: HT
---

# Vídeo: Configurar Office Web Apps para SharePoint 2013

 

_**Se aplica a:**Office Web Apps, Office Web Apps Server, SharePoint Foundation 2013, SharePoint Server 2013_

_**Última modificación del tema:**2016-12-16_

**Resumen:** lo guía a través de los nueve pasos principales para configurar una granja de servidores de Office Web Apps Server para que funcione con SharePoint 2013.

Configurar Office Web Apps para SharePoint 2013 es un proceso bastante simple. En este vídeo se muestra cómo instalar Office Web Apps Server y configurar SharePoint 2013 para usar Office Web Apps Server en un entorno de prueba.


**Vea el vídeo sobre cómo configurar Office Web Apps para SharePoint 2013.**

> [!VIDEO https://www.microsoft.com/es-es/videoplayer/embed/179bf96f-09e1-407a-bb1b-a8e6623eabae]

En este vídeo se abordan los procedimientos realizados en dos servidores: el que ejecuta Office Web Apps Server y el que ejecuta SharePoint 2013. Estos deben ser servidores independientes, tal como se describe en el tema sobre los [requisitos de software, hardware y configuración para Office Web Apps Server](plan-office-web-apps-server.md).

**En el servidor que ejecuta Office Web Apps Server, el vídeo muestra cómo:**

1\. Abrir el símbolo del sistema de Windows PowerShell e instalar los roles y servicios necesarios para Office Web Apps Server. Vea el tema sobre cómo [Prepare servers to run Office Web Apps Server](deploy-office-web-apps-server.md). Esto es necesario porque Office Web Apps Server no se instalará si faltan los roles y servicios necesarios.  
2\. Instalar el software de Office Web Apps Server desde el [Centro de servicios de licencias por volumen de Microsoft (VLSC)](http://go.microsoft.com/fwlink/p/?linkid=256561). Para descargar Office Web Apps Server, debe tener una licencia, según un acuerdo de licencias por volumen, para Office Professional Plus 2013, Office Standard 2013 u Office para Mac 2011. La descarga se ubica dentro de los productos de Office en el portal de VLSC.  
3\. Crear la granja de servidores de Office Web Apps Server con [New-OfficeWebAppsFarm](new-officewebappsfarm.md).  
4\. Comprobar que la granja de servidores de Office Web Apps Server se creó correctamente abriendo una ventana del explorador y navegando a http://*NombreDelServidor*/hosting/discovery.

**En el servidor que ejecuta SharePoint 2013, el vídeo muestra cómo:**

5\. Abrir el Shell de administración de SharePoint 2013.  
6\. Crear el enlace entre Office Web Apps Server y SharePoint 2013 con [New-SPWOPIBinding](new-spwopibinding.md). Esto configura la comunicación entre el servidor que ejecuta SharePoint 2013 y el que ejecuta Office Web Apps Server.  
7\. Ver la zona WOPI de SharePoint 2013 con [Get-SPWOPIZone](get-spwopizone.md). Este paso resalta el hecho de que los dos servidores usan distintas zonas WOPI: SharePoint 2013 usa internal-https y Office Web Apps Server usa internal-http. La zona debe coincidir para que Office Web Apps funcione correctamente.  
8\. Cambiar la zona WOPI de SharePoint 2013 a internal-http con [Set-SPWOPIZone](set-spwopizone.md).  
9\. Comprobar que Office Web Apps funciona correctamente abriendo un documento de Office en una biblioteca de documentos de SharePoint 2013.

Para obtener más detalles sobre cada uno de estos pasos, consulte las siguientes secciones en los artículos [Implementar Office Web Apps Server](deploy-office-web-apps-server.md) y [Configurar Office Web Apps para SharePoint 2013](configure-office-web-apps-for-sharepoint-2013.md).

  - [Prepare servers to run Office Web Apps Server](deploy-office-web-apps-server.md)

  - [Deploy a single-server Office Web Apps Server farm that uses HTTP](deploy-office-web-apps-server.md)

  - [Before you configure SharePoint 2013 to use Office Web Apps Server](configure-office-web-apps-for-sharepoint-2013.md)

  - [In a test environment that uses HTTP](configure-office-web-apps-for-sharepoint-2013.md)

## Consulte también


[Guía básica de contenido de Office Web Apps Server](content-roadmap-for-office-web-apps-server.md)  
[Planificar Office Web Apps (cuando se usa con SharePoint 2013)](plan-office-web-apps-used-with-sharepoint-2013.md)  
[Cómo funciona Office Web Apps en implementaciones locales con SharePoint 2013](how-office-web-apps-work-on-premises-with-sharepoint-2013.md)  
  

[](how-office-web-apps-work-on-premises-with-sharepoint-2013.md)

