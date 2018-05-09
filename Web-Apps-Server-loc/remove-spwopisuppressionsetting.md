---
title: Remove-SPWOPISuppressionSetting
TOCTitle: Remove-SPWOPISuppressionSetting
ms:assetid: cbaef5a8-e682-4166-be44-15ab1c79acca
ms:mtpsurl: https://technet.microsoft.com/es-es/library/JJ219452(v=office.15)
ms:contentKeyID: 48793543
ms.date: 12/23/2017
mtps_version: v=office.15
ms.translationtype: HT
---

# Remove-SPWOPISuppressionSetting

 

_**Se aplica a:**Office Web Apps, SharePoint Foundation 2013, SharePoint Server 2013_

_**Última modificación del tema:**2015-03-09_

Quita la configuración de supresión de una extensión de nombre de archivo o identificador de programación y una acción de la granja actual de SharePoint en la que se ejecuta el cmdlet.

## Sintaxis

    Remove-SPWOPISuppressionSetting [-Action <String>] [-AssignmentCollection <SPAssignmentCollection>] [-Confirm [<SwitchParameter>]] [-Extension <String>] [-ProgId <String>] [-WhatIf [<SwitchParameter>]]

    Remove-SPWOPISuppressionSetting [-AssignmentCollection <SPAssignmentCollection>] [-Confirm [<SwitchParameter>]] [-Identity <String>] [-WhatIf [<SwitchParameter>]]

## Descripción detallada

El cmdlet **Remove-SPWOPISuppressionSetting** quita la configuración de supresión de una extensión de nombre de archivo o identificador de programación (ProgID) y una acción de la granja actual de SharePoint en la que se ejecuta el cmdlet.

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
<td><p>Especifica la acción para una extensión de nombre de archivo o identificador de programación (ProgId) determinado. Por ejemplo, “view&quot;, “edit&quot; y “embedview&quot;.</p></td>
</tr>
<tr class="even">
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
<tr class="odd">
<td><p><strong>Confirm</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Le pide confirmación antes de ejecutar el comando. Para obtener más información, escriba el siguiente comando: <strong>get-help about_commonparameters</strong>.</p></td>
</tr>
<tr class="even">
<td><p><strong>Extension</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Especifica la extensión de nombre de archivo. Ejecute Get-SPWOPIBinding para obtener la lista de extensiones de nombre de archivo que admite la aplicación WOPI.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Identity</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Especifica una cadena que representa SPWOPISuppressionSetting. Ejecute Get-SPWOPISuppressionSetting para ver ejemplos de las cadenas.</p></td>
</tr>
<tr class="even">
<td><p><strong>ProgId</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Especifica el identificador de programación (ProgID) de una aplicación para suprimir. Ejecute Get-SPWOPIBinding para obtener la lista de ProgID que admite la aplicación WOPI.</p></td>
</tr>
<tr class="odd">
<td><p><strong>WhatIf</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Muestra un mensaje que describe el efecto del comando en lugar de ejecutar dicho comando. Para obtener más información, escriba el siguiente comando: <strong>get-help about_commonparameters</strong></p></td>
</tr>
</tbody>
</table>


## Tipos de entrada

## Tipos de valores devueltos

## Ejemplo

\--------------EJEMPLO 1-----------------

    Remove-SPWOPISuppressionSetting -Extension "XLSX" -Action "view"

En este ejemplo se quita la configuración de supresión para ver libros de Excel con la extensión de nombre de archivo “.xlsx”.

\--------------EJEMPLO 2-----------------

    Get-SPWOPISuppressionSetting | Remove-SPWOPISuppressionSetting

En este ejemplo se quita la configuración de supresión de la granja de SharePoint actual en que se ejecuta este cmdlet.

## Consulte también


[New-SPWOPISuppressionSetting](new-spwopisuppressionsetting.md)  
[Get-SPWOPISuppressionSetting](get-spwopisuppressionsetting.md)  


[Guía básica de contenido de Office Web Apps Server](content-roadmap-for-office-web-apps-server.md)  
[Usar Office Web Apps con SharePoint 2013](use-office-web-apps-with-sharepoint-2013.md)

