---
title: Remove-SPWOPIBinding
TOCTitle: Remove-SPWOPIBinding
ms:assetid: 52855c21-ee2c-497a-b308-bf5eeabe4bbe
ms:mtpsurl: https://technet.microsoft.com/es-es/library/JJ219438(v=office.15)
ms:contentKeyID: 48793524
ms.date: 12/23/2017
mtps_version: v=office.15
ms.translationtype: HT
---

# Remove-SPWOPIBinding

 

_**Se aplica a:**Office Web Apps, SharePoint Foundation 2013, SharePoint Server 2013_

_**Última modificación del tema:**2015-03-09_

Elimina enlaces para aplicaciones, extensiones de nombre de archivo y acciones asociadas en la granja de SharePoint actual donde se ejecuta este cmdlet.

## Sintaxis

    Remove-SPWOPIBinding [[-Identity] <SPWopiBindingPipeBind>] [-AssignmentCollection <SPAssignmentCollection>] [-Confirm [<SwitchParameter>]] [-WhatIf [<SwitchParameter>]]

    Remove-SPWOPIBinding [-Action <String>] [-Application <String>] [-AssignmentCollection <SPAssignmentCollection>] [-Confirm [<SwitchParameter>]] [-Extension <String>] [-ProgId <String>] [-Server <String>] [-WhatIf [<SwitchParameter>]] [-WOPIZone <String>]

    Remove-SPWOPIBinding [-All <SwitchParameter>] [-AssignmentCollection <SPAssignmentCollection>] [-Confirm [<SwitchParameter>]] [-WhatIf [<SwitchParameter>]]

## Descripción detallada

El cmdlet **Remove-SPWOPIBinding** quita los enlaces de aplicaciones, extensiones de nombre de archivo y sus acciones asociadas en la granja de SharePoint actual en que se ejecuta este cmdlet. Después de ejecutarlo, puede usar **New-SPWOPIBinding** para volver a crear los enlaces necesarios. Si quita todos los enlaces de una aplicación, los usuarios no pueden usar Office Web Apps ni la característica Compartir un vínculo de SharePoint con la aplicación. Si quita todos los enlaces de la granja de SharePoint en que se ejecuta el cmdlet, los usuarios no pueden usar Office Web Apps ni la característica Compartir un vínculo en las aplicaciones de la biblioteca de SharePoint.

Si desea dejar de usar Office Web Apps para los clics predeterminados pero debe conservar la información de detección de enlaces y la capacidad de los usuarios para usar la característica Compartir un vínculo de SharePoint para enviar un vínculo a un documento y que el destinatario pueda usar Office Web Apps para ese tipo de documento, use el cmdlet **New-SPWOPISuppression**.

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
<td><p><strong>Identity</strong></p></td>
<td><p>Opcional</p></td>
<td><p>Microsoft.SharePoint.PowerShell.SPWopiBindingPipeBind</p></td>
<td><p>Especifica el enlace.</p></td>
</tr>
<tr class="even">
<td><p><strong>Action</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Especifica la acción para la que se quitarán los enlaces. Por ejemplo, “view&quot;, “edit&quot; y “embedview&quot;. Para obtener una lista de acciones, ejecute <strong>Get-SPWOPIBinding</strong>. Normalmente, no usará este parámetro. Si especifica algunas acciones pero no especifica otras, es posible que algunas características de SharePoint no funcionen.</p></td>
</tr>
<tr class="odd">
<td><p><strong>All</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Quita todos los enlaces.</p></td>
</tr>
<tr class="even">
<td><p><strong>Application</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Especifica la aplicación para la que se quitarán los enlaces. Las aplicaciones posibles son las siguientes: “Word&quot;, “Excel&quot;, “PowerPoint&quot; o “OneNote&quot;. Ejecute <strong>Get-SPWOPIBinding</strong> para obtener la lista de aplicaciones.</p></td>
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
<td><p><strong>Confirm</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Le pide confirmación antes de ejecutar el comando. Para obtener más información, escriba el siguiente comando: <strong>get-help about_commonparameters</strong>.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Extension</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Especifica las extensiones de nombre de archivo para las que se quitarán los enlaces. Ejecute <strong>Get-SPWOPIBinding</strong> para obtener la lista de extensiones de nombre de archivo.</p></td>
</tr>
<tr class="even">
<td><p><strong>ProgId</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Especifica el identificador de programación (ProgID) de la aplicación para la que se quitarán los enlaces. Ejecute <strong>Get-SPWOPIBinding</strong> para obtener la lista de ProgID. Es recomendable usar este parámetro solo para quitar enlaces para OneNote.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Server</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Especifica el nombre de la aplicación WOPI (por ejemplo, Office Web Apps Server) para la que se quitarán los enlaces.</p></td>
</tr>
<tr class="even">
<td><p><strong>WhatIf</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Muestra un mensaje que describe el efecto del comando en lugar de ejecutar dicho comando. Para obtener más información, escriba el siguiente comando: <strong>get-help about_commonparameters</strong></p></td>
</tr>
<tr class="odd">
<td><p><strong>WOPIZone</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Especifica la zona para la que se quitarán los enlaces.</p></td>
</tr>
</tbody>
</table>


## Tipos de entrada

## Tipos de valores devueltos

## Ejemplo

\--------------EJEMPLO 1-----------------

    Remove-SPWOPIBinding -Application "Excel"

En este ejemplo se quitan todos los enlaces para Excel en la granja de SharePoint actual en que se ejecuta este cmdlet.

\--------------EJEMPLO 2-----------------

    Remove-SPWOPIBinding -All:$true

En este ejemplo se quitan todos los enlaces en la granja de SharePoint actual en que se ejecuta este cmdlet.

\--------------EJEMPLO 3-----------------

    Get-SPWOPIBinding -Action "MobileView" | Remove-SPWOPIBinding

En este ejemplo se quitan todos los enlaces para Office Mobile Web Apps en la granja de SharePoint actual en que se ejecuta este cmdlet.

## Consulte también


[New-SPWOPIBinding](new-spwopibinding.md)  
[Get-SPWOPIBinding](get-spwopibinding.md)  
[Set-SPWOPIBinding](set-spwopibinding.md)  
[New-SPWOPISuppressionSetting](new-spwopisuppressionsetting.md)  


[Guía básica de contenido de Office Web Apps Server](content-roadmap-for-office-web-apps-server.md)  
[Usar Office Web Apps con SharePoint 2013](use-office-web-apps-with-sharepoint-2013.md)

