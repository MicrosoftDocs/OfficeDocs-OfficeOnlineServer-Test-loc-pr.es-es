---
title: Set-SPWOPIBinding
TOCTitle: Set-SPWOPIBinding
ms:assetid: e373528f-e69b-4e25-9df4-3a5f80ab64ac
ms:mtpsurl: https://technet.microsoft.com/es-es/library/JJ219454(v=office.15)
ms:contentKeyID: 48793545
ms.date: 12/23/2017
mtps_version: v=office.15
ms.translationtype: HT
---

# Set-SPWOPIBinding

 

_**Se aplica a:**Office Web Apps, SharePoint Foundation 2013, SharePoint Server 2013_

_**Última modificación del tema:**2015-03-09_

Actualiza la acción de clic predeterminada para un enlace de extensión de nombre de archivo o aplicación.

## Sintaxis

    Set-SPWOPIBinding [-Identity] <SPWopiBindingPipeBind> -DefaultAction <SwitchParameter> [-AssignmentCollection <SPAssignmentCollection>] [-Confirm [<SwitchParameter>]] [-WhatIf [<SwitchParameter>]]

## Descripción detallada

El cmdlet **Set-SPWOPIBinding** actualiza la acción de clic predeterminada para el enlace de una aplicación o extensión de nombre de archivo. Por ejemplo, puede definir como acción de clic predeterminada la de ver para una documento de Word de una biblioteca de SharePoint. Para ello, defina la acción predeterminada como true en los enlaces “view”-“Word”.

Normalmente, se usaría la salida del comando **Get-SPWOPIBinding** como valor de la propiedad -Identity de este comando. Para más información, consulte [Get-SPWOPIBinding](get-spwopibinding.md)

<table>
<thead>
<tr class="header">
<th><img src="images/JJ219448.important(Office.15).gif" title="Importante" alt="Importante" /><strong>Importante:</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Solo se pueden establecer enlaces creados mediante el comando <strong>New-SPWOPIBinding</strong>. Para invalidar un enlace integrado (por ejemplo, la acción que tiene lugar al ver un documento de Word en una biblioteca de SharePoint), cree un nuevo enlace mediante <strong>New-SPWOPIBinding</strong> y asígneles una acción distinta. Para más información, consulte <a href="new-spwopibinding.md">New-SPWOPIBinding</a>.</td>
</tr>
</tbody>
</table>


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
<td><p>Obligatorio</p></td>
<td><p>Microsoft.SharePoint.PowerShell.SPWopiBindingPipeBind</p></td>
<td><p>Especifica el enlace. Normalmente, se usaría la salida del comando <strong>Get-SPWOPIBinding</strong> como valor de –Identity.</p></td>
</tr>
<tr class="even">
<td><p><strong>DefaultAction</strong></p></td>
<td><p>Obligatorio</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Especifica si el enlace se debe definir como acción de clic predeterminada para una aplicación o extensión de nombre de archivo del enlace.</p></td>
</tr>
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
<tr class="even">
<td><p><strong>Confirm</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Le pide confirmación antes de ejecutar el comando. Para obtener más información, escriba el siguiente comando: <strong>get-help about_commonparameters</strong>.</p></td>
</tr>
<tr class="odd">
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

\--------------EJEMPLO----------------

    Get-SPWOPIBinding -Action "view" -Application "Word"| Set-SPWOPIBinding -DefaultAction

En este ejemplo se define la acción de clic predeterminada de ver para un documento de Word de una biblioteca de SharePoint. Puede comprobar que la acción de clic predeterminada es ver para Word ejecutando el cmdlet **Get-SPWOPIBinding –Action “view” –Application “Word”**. El valor de **IsDefaultAction** se define como “True.”

## Consulte también


[Get-SPWOPIBinding](get-spwopibinding.md)  
[Remove-SPWOPIBinding](remove-spwopibinding.md)  
[New-SPWOPIBinding](new-spwopibinding.md)  


[Guía básica de contenido de Office Web Apps Server](content-roadmap-for-office-web-apps-server.md)  
[Usar Office Web Apps con SharePoint 2013](use-office-web-apps-with-sharepoint-2013.md)

