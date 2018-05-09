---
title: Get-OfficeWebAppsMachine
TOCTitle: Get-OfficeWebAppsMachine
ms:assetid: 02fadf5e-0382-4e73-8d07-e67d088b1a02
ms:mtpsurl: https://technet.microsoft.com/es-es/library/JJ219432(v=office.15)
ms:contentKeyID: 48793517
ms.date: 12/18/2017
mtps_version: v=office.15
ms.translationtype: HT
---

# Get-OfficeWebAppsMachine

 

_**Se aplica a:**Office Web Apps Server_

_**Última modificación del tema:**2013-12-18_

Devuelve información detallada sobre el servidor actual que se encuentra en una granja de servidores de Office Web Apps Server.

## Sintaxis

    Get-OfficeWebAppsMachine

## Descripción detallada

El cmdlet **Get-OfficeWebAppsMachine** devuelve información detallada sobre el servidor actual que se encuentra en una granja de servidores de Office Web Apps Server. Esta información incluye los roles y el estado de mantenimiento del servidor actual, y el nombre del servidor maestro de la granja de servidores.

## Parámetro

## Tipos de entrada

## Tipos de valores devueltos

## Ejemplo

\------------------EJEMPLO 1---------------------

    Get-OfficeWebAppsMachine

Este ejemplo devuelve información detallada sobre el servidor actual que se encuentra en una granja de servidores de Office Web Apps Server.

\------------------EJEMPLO 2---------------------

    (Get-OfficeWebAppsFarm).Machines

Este ejemplo devuelve información detallada sobre todos los servidores que se encuentran en una granja de servidores de Office Web Apps Server.

## Consulte también


[New-OfficeWebAppsMachine](new-officewebappsmachine.md)  
[Remove-OfficeWebAppsMachine](remove-officewebappsmachine.md)  
[Set-OfficeWebAppsMachine](set-officewebappsmachine.md)  


[Guía básica de contenido de Office Web Apps Server](content-roadmap-for-office-web-apps-server.md)  
[Implementar la infraestructura: Office Web Apps Server](deploy-the-infrastructure-office-web-apps-server.md)  
  

[](deploy-the-infrastructure-office-web-apps-server.md)

