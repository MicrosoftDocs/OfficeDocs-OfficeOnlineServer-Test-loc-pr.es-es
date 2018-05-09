---
title: New-OfficeWebAppsHost
TOCTitle: New-OfficeWebAppsHost
ms:assetid: f1d523ab-45c6-4e3c-b274-22c0d229a6a0
ms:mtpsurl: https://technet.microsoft.com/es-es/library/JJ219459(v=office.15)
ms:contentKeyID: 48793551
ms.date: 12/18/2017
mtps_version: v=office.15
ms.translationtype: HT
---

# New-OfficeWebAppsHost

 

_**Se aplica a:**Office Web Apps Server_

_**Última modificación del tema:**2015-03-09_

Agrega un dominio de host a la lista de permitidos para una granja de Office Web Apps Server.

## Sintaxis

    New-OfficeWebAppsHost -Domain <String>

## Descripción detallada

El cmdlet **New-OfficeWebAppsHost** agrega un dominio de host a la lista de dominios de host para la que Office Web Apps Server permite solicitudes de operaciones con archivos, como la recuperación de archivos, la recuperación de metadatos y los cambios de archivos. Esta lista, conocida como la lista de permitidos, es una característica de seguridad que impide que hosts no deseados se conecten a una granja de servidores de Office Web Apps Server y la usen para realizar operaciones con archivos sin su conocimiento.

<table>
<thead>
<tr class="header">
<th><img src="images/JJ219455.tip(Office.15).gif" title="Sugerencia" alt="Sugerencia" /><strong>Sugerencia:</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Puede utilizar cualquier tipo de dominio, incluidos público, grupo, granja y los nombres de dominio de Active Directory. Solo debe asegurarse de que el dominio al que concede acceso cumple los requisitos de seguridad que haya establecido.</td>
</tr>
</tbody>
</table>


El carácter comodín \* se asume para cualquier dominio que se agregue a la lista de permitidos para que se permitan también las solicitudes a todos los subdominios. Por ejemplo, si agrega el dominio contoso.com a la lista de permitidos, Office Web Apps Server también solicita a los dominios corp.contoso.com y dev.contoso.com. Las solicitudes a otros dominios (como fabrikam.com) no se permiten.

<table>
<thead>
<tr class="header">
<th><img src="images/JJ219453.Caution(Office.15).gif" title="Precaución" alt="Precaución" /><strong>Precaución:</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Si no existe ningún dominio en la lista de permitidos, Office Web Apps Server permite las solicitudes de archivos a los hosts en cualquier dominio. No deje esta lista en blanco si se puede acceder a su granja de servidores Office Web Apps Server desde Internet. De lo contrario, cualquier persona puede usar su granja de servidores Office Web Apps Server para ver y editar contenido.</td>
</tr>
</tbody>
</table>


## Parámetro


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Parámetro</th>
<th>Obligatorio</th>
<th>Tipo</th>
<th>Descripción</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Domain</strong></p></td>
<td><p>Obligatorio</p></td>
<td><p>System.String</p></td>
<td><p>Especifica el dominio que se debe agregar a la lista de permitidos. No especifique un asterisco ni empiece con un punto.</p></td>
</tr>
</tbody>
</table>


## Tipos de entrada

## Tipos de valores devueltos

## Ejemplo

\------------------EJEMPLO 1---------------------

    New-OfficeWebAppsHost -domain "contoso.com"

En este ejemplo se agrega el dominio contoso.com a la lista de permitidos.


> [!NOTE]
> No se pueden agregar al mismo tiempo varios dominios de host a la lista de permitidos. Para cada dominio de host que desee agregar a esta lista, deberá ejecutar el cmdlet New-OfficeWebAppsHost.



## Consulte también


[Get-OfficeWebAppsHost](get-officewebappshost.md)  
[Remove-OfficeWebAppsHost](remove-officewebappshost.md)  


[Guía básica de contenido de Office Web Apps Server](content-roadmap-for-office-web-apps-server.md)  
[Implementar la infraestructura: Office Web Apps Server](deploy-the-infrastructure-office-web-apps-server.md)  
  

[](deploy-the-infrastructure-office-web-apps-server.md)

