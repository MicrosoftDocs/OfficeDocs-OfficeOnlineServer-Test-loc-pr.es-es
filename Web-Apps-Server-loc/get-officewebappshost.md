---
title: Get-OfficeWebAppsHost
TOCTitle: Get-OfficeWebAppsHost
ms:assetid: a9b766a7-a15c-4bbf-9750-31719406d65f
ms:mtpsurl: https://technet.microsoft.com/es-es/library/JJ219446(v=office.15)
ms:contentKeyID: 48793535
ms.date: 12/18/2017
mtps_version: v=office.15
ms.translationtype: HT
---

# Get-OfficeWebAppsHost

 

_**Se aplica a:**Office Web Apps Server_

_**Última modificación del tema:**2013-12-18_

Devuelve una lista de dominios de host que se encuentran en la Lista de permitidos para una granja de servidores de Office Web Apps Server.

## Sintaxis

    Get-OfficeWebAppsHost

## Descripción detallada

El cmdlet **Get-OfficeWebAppsHost** devuelve la lista de dominios de host a los que Office Web Apps Server permite realizar solicitudes de operaciones con archivos, como la recuperación de archivos, la recuperación de metadatos y los cambios de archivos. Esta lista, conocida como la lista de permitidos, es una característica de seguridad que impide que hosts no deseados se conecten a una granja de servidores Office Web Apps Server y la usen para realizar operaciones con archivos sin su conocimiento.

El carácter comodín \* se asume para cualquier dominio que aparezca en la lista de permitidos para que se permitan también las solicitudes a todos los subdominios. Por ejemplo, si el dominio contoso.com está en la lista de permitidos, Office Web Apps Server también solicita a los dominios corp.contoso.com y dev.contoso.com. Las solicitudes a otros dominios (como fabrikam.com) no se permiten.

<table>
<thead>
<tr class="header">
<th><img src="images/JJ219453.Caution(Office.15).gif" title="Precaución" alt="Precaución" /><strong>Precaución:</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Si no existe ningún dominio en la lista de permitidos, Office Web Apps Server permite que los hosts de cualquier dominio realicen solicitudes de archivos. No deje esta lista en blanco si su granja de servidores Office Web Apps Server es accesible desde Internet. De lo contrario, cualquier persona puede usar su granja de servidores Office Web Apps Server para ver y editar contenido.</td>
</tr>
</tbody>
</table>


## Parámetro

## Tipos de entrada

## Tipos de valores devueltos

## Ejemplo

\------------------EJEMPLO 1---------------------

    Get-OfficeWebAppsHost

En este ejemplo se devuelven los dominios de host que están en la lista de permitidos.

## Consulte también


[New-OfficeWebAppsHost](new-officewebappshost.md)  
[Remove-OfficeWebAppsHost](remove-officewebappshost.md)  


[Guía básica de contenido de Office Web Apps Server](content-roadmap-for-office-web-apps-server.md)  
[Implementar la infraestructura: Office Web Apps Server](deploy-the-infrastructure-office-web-apps-server.md)  
  

[](deploy-the-infrastructure-office-web-apps-server.md)

