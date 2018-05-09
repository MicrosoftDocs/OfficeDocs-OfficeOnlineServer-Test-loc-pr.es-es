---
title: Get-OfficeWebAppsFarm
TOCTitle: Get-OfficeWebAppsFarm
ms:assetid: 1f0704e1-a41d-40e6-a31b-08b1926ce811
ms:mtpsurl: https://technet.microsoft.com/es-es/library/JJ219434(v=office.15)
ms:contentKeyID: 48793519
ms.date: 12/18/2017
mtps_version: v=office.15
ms.translationtype: HT
---

# Get-OfficeWebAppsFarm

 

_**Se aplica a:**Office Web Apps Server_

_**Última modificación del tema:**2013-12-18_

Devuelve detalles acerca del objeto OfficeWebAppsFarm del que es miembro el servidor actual.

## Sintaxis

    Get-OfficeWebAppsFarm

## Descripción detallada

El cmdlet **Get-OfficeWebAppsFarm** devuelve detalles acerca del objeto OfficeWebAppsFarm del que es miembro el servidor actual. Este objecto representa un grupo de servidores que funcionan como una unidad para proporcionar presentación y edición basada en web de documentos de Office. Con el cmdlet **Get-OfficeWebAppsFarm** no se usa ningún parámetro.

## Parámetro

## Tipos de entrada

## Tipos de valores devueltos

## Ejemplo

\------------------EJEMPLO 1---------------------

    Get-OfficeWebAppsFarm

En este ejemplo se devuelven detalles acerca del objeto OfficeWebAppsFarm.

\------------------EJEMPLO 2---------------------

    (Get-OfficeWebAppsFarm).Machines

En este ejemplo se devuelven detalles acerca de los servidores que son miembro de la granja de servidores Office Web Apps Server. Estos detalles incluyen el estado de mantenimiento y los roles de cada servidor.

## Consulte también


[New-OfficeWebAppsFarm](new-officewebappsfarm.md)  
[Set-OfficeWebAppsFarm](set-officewebappsfarm.md)  
[Repair-OfficeWebAppsFarm](repair-officewebappsfarm.md)  


[Guía básica de contenido de Office Web Apps Server](content-roadmap-for-office-web-apps-server.md)  
[Implementar la infraestructura: Office Web Apps Server](deploy-the-infrastructure-office-web-apps-server.md)  
  

[](deploy-the-infrastructure-office-web-apps-server.md)

