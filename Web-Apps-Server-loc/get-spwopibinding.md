---
title: Get-SPWOPIBinding
TOCTitle: Get-SPWOPIBinding
ms:assetid: b757301b-f6c5-43a5-a8ca-2ef33ede0ae8
ms:mtpsurl: https://technet.microsoft.com/es-es/library/JJ219450(v=office.15)
ms:contentKeyID: 48793540
ms.date: 12/18/2017
mtps_version: v=office.15
ms.translationtype: HT
---

# Get-SPWOPIBinding

 

_**Se aplica a:**Office Web Apps, SharePoint Foundation 2013, SharePoint Server 2013_

_**Última modificación del tema:**2015-03-09_

Devuelve una lista de enlaces creados con **New-SPWOPIBinding** en la granja de SharePoint actual donde se ejecuta este cmdlet.

## Sintaxis

    Get-SPWOPIBinding [-Action <String>] [-Application <String>] [-AssignmentCollection <SPAssignmentCollection>] [-Extension <String>] [-ProgId <String>] [-Server <String>] [-WOPIZone <String>]

## Descripción detallada

**Get-SPWOPIBinding** devuelve una lista de enlaces creados mediante **New-SPWOPIBinding** en la granja actual de SharePoint en que se ejecuta el cmdlet. Los resultados incluyen acciones, aplicaciones, tipos de archivo y zonas configurados para una aplicación WOPI (por ejemplo, un servidor que ejecute Office Web Apps Server).

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
<td><p><strong>Action</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Especifica la acción para la que se devolverán los enlaces.</p></td>
</tr>
<tr class="even">
<td><p><strong>Application</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Especifica la aplicación para la que se devolverán los enlaces.</p></td>
</tr>
<tr class="odd">
<td><p><strong>AssignmentCollection</strong></p></td>
<td><p>Opcional</p></td>
<td><p>Microsoft.SharePoint.PowerShell.SPAssignmentCollection</p></td>
<td><p>Administra objetos para su correcta eliminación. El uso de objetos como <strong>SPWeb</strong> o <strong>SPSite</strong> puede requerir una gran cantidad de memoria y su uso en scripts de Windows PowerShell requiere una administración adecuada de la memoria. Mediante el uso del objeto <strong>SPAssignment</strong> se pueden asignar objetos a una variable y eliminar los objetos cuando ya no sean necesarios para liberar memoria. Cuando se usan los objetos <strong>SPWeb</strong>, <strong>SPSite</strong> o <strong>SPSiteAdministration</strong>, los objetos se eliminan automáticamente si no se usa una colección de asignaciones o el parámetro <strong>Global</strong>.</p>
<div class="alert">

> [!NOTE]
> Cuando se usa el parámetro <STRONG>Global</STRONG>, todos los objetos se guardan en el almacén global. Si los objetos no se usan de forma inmediata o se eliminan mediante el comando <STRONG>Stop-SPAssignment</STRONG>, puede producirse un error de memoria insuficiente.


</div></td>
</tr>
<tr class="even">
<td><p><strong>Extension</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Especifica las extensiones de nombre de archivo para las que se devolverán los enlaces.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ProgId</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Especifica el identificador de programación (ProgID) de la aplicación para la que se devolverán los enlaces.</p></td>
</tr>
<tr class="even">
<td><p><strong>Server</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Especifica el nombre de la aplicación WOPI (por ejemplo, un servidor que ejecute Office Web Apps Server) para la que se devolverán los enlaces.</p></td>
</tr>
<tr class="odd">
<td><p><strong>WOPIZone</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Especifica la zona para la que se devolverán los enlaces.</p></td>
</tr>
</tbody>
</table>


## Tipos de entrada

## Tipos de valores devueltos

## Ejemplo

\--------------EJEMPLO 1-----------------

    Get-SPWOPIBinding -Server "Server.corp.Contoso.com"

En este ejemplo se devuelve una lista de enlaces creados en la granja actual de SharePoint en que se ejecuta el cmdlet para la aplicación WOPI "Server.corp.Contoso.com". La aplicación WOPI puede ser el servidor que ejecuta Office Web Apps Server.

\--------------EJEMPLO 2-----------------

    Get-SPWOPIZone | Get-SPWOPIBinding

En este ejemplo se devuelve una lista de enlaces creados en la granja actual de SharePoint en que se ejecuta el cmdlet para la zona configurada para la aplicación WOPI.

## Consulte también


[New-SPWOPIBinding](new-spwopibinding.md)  
[Set-SPWOPIBinding](set-spwopibinding.md)  
[Remove-SPWOPIBinding](remove-spwopibinding.md)  


[Guía básica de contenido de Office Web Apps Server](content-roadmap-for-office-web-apps-server.md)  
[Usar Office Web Apps con SharePoint 2013](use-office-web-apps-with-sharepoint-2013.md)

