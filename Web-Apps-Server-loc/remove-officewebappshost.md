---
title: Remove-OfficeWebAppsHost
TOCTitle: Remove-OfficeWebAppsHost
ms:assetid: d0f7b5c2-da0f-421a-8478-c39b247c3ac5
ms:mtpsurl: https://technet.microsoft.com/es-es/library/JJ219453(v=office.15)
ms:contentKeyID: 48793544
ms.date: 12/18/2017
mtps_version: v=office.15
ms.translationtype: HT
---

# Remove-OfficeWebAppsHost

 

_**Se aplica a:**Office Web Apps Server_

_**Última modificación del tema:**2015-03-09_

Quita un dominio de host de la Lista de permitidos para una granja de servidores de Office Web Apps Server.

## Sintaxis

    Remove-OfficeWebAppsHost -Domain <String>

## Descripción detallada

El cmdlet **Remove-OfficeWebAppsHost** quita el dominio de host especificado de la lista de permitidos. La lista de permitidos contiene los dominios de host a los que Office Web Apps Server permite solicitudes de operaciones con archivos.

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
<td><p>Especifica el dominio de host que se debe quitar de la lista de permitidos.</p></td>
</tr>
</tbody>
</table>


## Tipos de entrada

## Tipos de valores devueltos

## Ejemplo

\------------------EJEMPLO 1---------------------

    Remove-OfficeWebAppsHost -domain "contoso.com"

En este ejemplo se quita el dominio contoso.com de la lista de permitidos.

## Consulte también


[New-OfficeWebAppsHost](new-officewebappshost.md)  
[Get-OfficeWebAppsHost](get-officewebappshost.md)  


[Guía básica de contenido de Office Web Apps Server](content-roadmap-for-office-web-apps-server.md)  
[Implementar la infraestructura: Office Web Apps Server](deploy-the-infrastructure-office-web-apps-server.md)  
  

[](deploy-the-infrastructure-office-web-apps-server.md)

