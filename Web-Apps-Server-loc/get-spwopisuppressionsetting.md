---
title: Get-SPWOPISuppressionSetting
TOCTitle: Get-SPWOPISuppressionSetting
ms:assetid: a7924964-e16f-4eca-be91-7aff8d45e0c6
ms:mtpsurl: https://technet.microsoft.com/es-es/library/JJ219445(v=office.15)
ms:contentKeyID: 48793534
ms.date: 12/18/2017
mtps_version: v=office.15
ms.translationtype: HT
---

# Get-SPWOPISuppressionSetting

 

_**Se aplica a:**Office Web Apps, SharePoint Foundation 2013, SharePoint Server 2013_

_**Última modificación del tema:**2015-03-09_

Devuelve la configuración de supresión en la granja de servidores SharePoint actual donde se ejecuta este cmdlet.

## Sintaxis

    Get-SPWOPISuppressionSetting [-AssignmentCollection <SPAssignmentCollection>]

## Descripción detallada

El cmdlet **Get-SPWOPISuppressionSetting** devuelve la configuración de supresión de la granja actual de SharePoint en que se ejecuta el cmdlet.

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


</div></td>
</tr>
</tbody>
</table>


## Tipos de entrada

## Tipos de valores devueltos

## Ejemplo

\--------------EJEMPLO----------------

    Get-SPWOPISuppressionSetting

En este ejemplo se devuelve la configuración de supresión de la granja actual de SharePoint en que se ejecuta este cmdlet. La configuración de supresión obtenida incluye los valores de **DocType** y **WOPIAction**.

## Consulte también


[New-SPWOPISuppressionSetting](new-spwopisuppressionsetting.md)  
[Remove-SPWOPISuppressionSetting](remove-spwopisuppressionsetting.md)  


[Guía básica de contenido de Office Web Apps Server](content-roadmap-for-office-web-apps-server.md)  
[Usar Office Web Apps con SharePoint 2013](use-office-web-apps-with-sharepoint-2013.md)

