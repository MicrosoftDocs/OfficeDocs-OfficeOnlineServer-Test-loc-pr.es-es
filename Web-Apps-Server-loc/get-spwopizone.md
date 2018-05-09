---
title: Get-SPWOPIZone
TOCTitle: Get-SPWOPIZone
ms:assetid: 5a37e106-272c-43e9-ae09-20888b296af0
ms:mtpsurl: https://technet.microsoft.com/es-es/library/JJ219439(v=office.15)
ms:contentKeyID: 48793526
ms.date: 12/18/2017
mtps_version: v=office.15
ms.translationtype: HT
---

# Get-SPWOPIZone

 

_**Se aplica a:**Office Web Apps, SharePoint Foundation 2013, SharePoint Server 2013_

_**Última modificación del tema:**2015-03-09_

Devuelve la zona que está configurada en la granja de SharePoint actual para la aplicación WOPI que se va a usar.

## Sintaxis

    Get-SPWOPIZone [-AssignmentCollection <SPAssignmentCollection>]

## Descripción detallada

**Get-SPWOPIZone** devuelve la zona configurada en la granja de SharePoint actual para que la use la aplicación WOPI (por ejemplo, un servidor que ejecuta Office Web Apps Server).

Shell de administración de SharePoint

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
<th>Necesario</th>
<th>Tipo</th>
<th>Descripción</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>AssignmentCollection</strong></p></td>
<td><p>Opcional</p></td>
<td><p>Microsoft.SharePoint.PowerShell.SPAssignmentCollection</p></td>
<td><p>Administra objetos para su correcta eliminación. El uso de objetos como <strong>SPWeb</strong> o <strong>SPSite</strong> puede requerir una gran cantidad de memoria y su uso en scripts de Windows PowerShell requiere una administración adecuada de la memoria. Mediante el uso del objeto <strong>SPAssignment</strong> se pueden asignar objetos a una variable y eliminar los objetos cuando ya no sean necesarios para liberar memoria. Cuando se usan los objetos <strong>SPWeb</strong>, <strong>SPSite</strong> o <strong>SPSiteAdministration</strong>, los objetos se eliminan automáticamente si no se usa una colección de asignaciones o el parámetro <strong>Global</strong>.</p>
<div class="alert">

> [!NOTE]
> Cuando se usa el parámetro <STRONG>Global</STRONG>, todos los objetos se guardan en el almacén global. Si los objetos no se usan de forma inmediata o se eliminan mediante el comando <STRONG>Stop-SPAssignment</STRONG>, puede producirse un error de memoria insuficiente.


</div>
<p></p></td>
</tr>
</tbody>
</table>


## Tipos de entrada

## Tipos de valores devueltos

## Ejemplo

\--------------EJEMPLO----------------

    Get-SPWOPIZone

En este ejemplo se devuelve la zona configurada para la aplicación WOPI (por ejemplo, un servidor que ejecute Office Web Apps Server). Los valores devueltos pueden ser “internal-http”, “internal-https”, “external-http” o “external-https.”

## Consulte también


[Set-SPWOPIZone](set-spwopizone.md)  


[Guía básica de contenido de Office Web Apps Server](content-roadmap-for-office-web-apps-server.md)  
[Usar Office Web Apps con SharePoint 2013](use-office-web-apps-with-sharepoint-2013.md)

