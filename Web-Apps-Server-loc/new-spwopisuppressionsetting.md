---
title: New-SPWOPISuppressionSetting
TOCTitle: New-SPWOPISuppressionSetting
ms:assetid: 7e6bb8f5-3124-4568-80c6-02cae46b803b
ms:mtpsurl: https://technet.microsoft.com/es-es/library/JJ219443(v=office.15)
ms:contentKeyID: 48793530
ms.date: 12/23/2017
mtps_version: v=office.15
ms.translationtype: HT
---

# New-SPWOPISuppressionSetting

 

_**Se aplica a:**Office Web Apps, SharePoint Foundation 2013, SharePoint Server 2013_

_**Última modificación del tema:**2015-03-09_

El cmdlet **New-SPWOPISuppressionSetting** desactiva Office Web Apps para la acción, extensión de nombre de archivo o identificador de programación que haya especificado en la granja de servidores actual de SharePoint.

## Sintaxis

    New-SPWOPISuppressionSetting [-Action <String>] [-AssignmentCollection <SPAssignmentCollection>] [-Confirm [<SwitchParameter>]] [-Extension <String>] [-ProgId <String>] [-WhatIf [<SwitchParameter>]]

## Descripción detallada

El cmdlet **New-SPWOPISuppressionSetting** desactiva Office Web Apps para la acción, extensión de nombre de archivo o identificador de programación (ProgId) que haya especificado en la granja de servidores actual de SharePoint. Al hacerlo, el cmdlet no quita la información de detección ni la capacidad de los usuarios de usar la característica Compartir un vínculo de SharePoint para enviar un vínculo a un documento y permitir al destinatario usar Office Web Apps para ese tipo de documento. Puede que también tenga que usar este cmdlet si quiere usar Servicios de Excel para ver libros de Excel en lugar de la aplicación WOPI (por ejemplo, Office Web Apps Server).

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
<td><p>Especifica la acción que se quiere suprimir en una extensión o un identificador de programación (ProgId) determinados. Por ejemplo, “view”, “edit” y “embedview”. Para ver la lista completa de acciones, ejecute <strong>Get-SPWOPIBinding</strong>.</p></td>
</tr>
<tr class="even">
<td><p><strong>AssignmentCollection</strong></p></td>
<td><p>Opcional</p></td>
<td><p>Microsoft.SharePoint.PowerShell.SPAssignmentCollection</p></td>
<td><p>Administra objetos para su correcta eliminación. El uso de objetos como <strong>SPWeb</strong> o <strong>SPSite</strong> puede requerir una gran cantidad de memoria y su uso en scripts de Windows PowerShell requiere una administración adecuada de la memoria. Mediante el uso del objeto <strong>SPAssignment</strong> se pueden asignar objetos a una variable y eliminar los objetos cuando ya no sean necesarios para liberar memoria. Cuando se usan los objetos <strong>SPWeb</strong>, <strong>SPSite</strong> o <strong>SPSiteAdministration</strong>, los objetos se eliminan automáticamente si no se usa una colección de asignaciones o el parámetro <strong>Global</strong>.</p>
<div class="alert">

> [!NOTE]
> Cuando se usa el parámetro <STRONG>Global</STRONG>, todos los objetos se guardan en el almacén global. Si los objetos no se usan de forma inmediata o se eliminan mediante el comando <STRONG>Stop-SPAssignment</STRONG>, puede producirse un error de memoria insuficiente.


</div></td>
</tr>
<tr class="odd">
<td><p><strong>Confirm</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Le pide confirmación antes de ejecutar el comando. Para obtener más información, escriba el siguiente comando: <strong>get-help about_commonparameters</strong></p></td>
</tr>
<tr class="even">
<td><p><strong>Extension</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Especifica la extensión de nombre de archivo que se suprimirá. Ejecute Get-SPWOPIBinding para ver la lista de extensiones de nombre de archivo que admite la aplicación WOPI.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ProgId</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Especifica el identificador de programación (ProgId) de una aplicación para suprimir. Ejecute Get-SPWOPIBinding para ver la lista de ProgId que admite la aplicación WOPI.</p></td>
</tr>
<tr class="even">
<td><p><strong>WhatIf</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Muestra un mensaje que describe el efecto del comando en lugar de ejecutar dicho comando. Para obtener más información, escriba el siguiente comando: <strong>get-help about_commonparameters</strong>.</p></td>
</tr>
</tbody>
</table>


## Tipos de entrada

## Tipos de valores devueltos

## Ejemplo

\--------------EJEMPLO 1-----------------

    New-SPWOPISuppressionSetting -Extension "XLSX" -Action "view"

    New-SPWOPISuppressionSetting -Extension "XLS" -Action "view"

En este ejemplo se desactiva la capacidad de un usuario de usar Office Web Apps para ver libros de Excel con la extensión de nombre de archivo ".xlsx" o ".xls".

## Consulte también


[Get-SPWOPISuppressionSetting](get-spwopisuppressionsetting.md)  
[Remove-SPWOPISuppressionSetting](remove-spwopisuppressionsetting.md)  


[Guía básica de contenido de Office Web Apps Server](content-roadmap-for-office-web-apps-server.md)  
[Usar Office Web Apps con SharePoint 2013](use-office-web-apps-with-sharepoint-2013.md)

