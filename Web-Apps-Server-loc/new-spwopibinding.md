---
title: New-SPWOPIBinding
TOCTitle: New-SPWOPIBinding
ms:assetid: 696f01b4-a144-431b-9bae-1c3ede78609d
ms:mtpsurl: https://technet.microsoft.com/es-es/library/JJ219441(v=office.15)
ms:contentKeyID: 48793528
ms.date: 12/23/2017
mtps_version: v=office.15
ms.translationtype: HT
---

# New-SPWOPIBinding

 

_**Se aplica a:**Office Web Apps, SharePoint Foundation 2013, SharePoint Server 2013_

_**Última modificación del tema:**2015-03-09_

Crea un nuevo enlace para asociar las extensiones de nombre de archivo o las aplicaciones con acciones en la granja de servidores de SharePoint actual donde se ejecuta este cmdlet.

## Sintaxis

    New-SPWOPIBinding -ServerName <String> [-Action <String>] [-AllowHTTP <SwitchParameter>] [-Application <String>] [-AssignmentCollection <SPAssignmentCollection>] [-Confirm [<SwitchParameter>]] [-Extension <String>] [-FileName <String>] [-ProgId <String>] [-WhatIf [<SwitchParameter>]]

## Descripción detallada

El cmdlet **New-SPWOPIBinding** asocia las extensiones de nombre de archivo o las aplicaciones con acciones de la granja de servidores actual de SharePoint en que se ejecuta este cmdlet. Cada enlace permite usar la aplicación WOPI para ver o editar archivos de la biblioteca de SharePoint. Por ejemplo, si un usuario ve un documento de Word en una lista de documentos de SharePoint, la lista muestra las opciones disponibles para ver o editar el documento en función de las acciones enlazadas con Word en la granja de servidores de SharePoint.

Para usar una aplicación WOPI, como un servidor que ejecute Office Web Apps Server, para Office Web Apps, debe ejecutar este cmdlet en la granja de servidores de SharePoint para poder usar Office Web Apps.

Si ejecuta **New-SPWOPIBinding** para una aplicación o extensión de nombre de archivo para la que ya existe un enlace (o asociación), el cmdlet fallará.

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
<td><p><strong>ServerName</strong></p></td>
<td><p>Obligatorio</p></td>
<td><p>System.String</p></td>
<td><p>Especifica el nombre o nombre de dominio completo (FQDN) de la aplicación WOPI (por ejemplo, un servidor que ejecute Office Web Apps Server).</p></td>
</tr>
<tr class="even">
<td><p><strong>Action</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Especifica la acción que se enlazará. Por ejemplo, “view&quot;, “edit&quot; y “embedview&quot;. Para ver la lista de acciones compatibles con la aplicación WOPI, ejecute <strong>Get-SPWOPIBinding</strong>. Normalmente, no usará este parámetro. Si especifica algunas acciones pero no especifica otras, es posible que algunas características de SharePoint no funcionen.</p></td>
</tr>
<tr class="odd">
<td><p><strong>AllowHTTP</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Especifica que el cmdlet puede usar HTTP para detectar los elementos compatibles con la aplicación WOPI. Si se especifica como True, la información de detección de la aplicación WOPI se enviará a través de una conexión no segura.</p></td>
</tr>
<tr class="even">
<td><p><strong>Application</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Especifica aplicaciones para enlazarlas. Las aplicaciones posibles son las siguientes: “Word&quot;, “Excel&quot;, “PowerPoint&quot; o “OneNote&quot;. Ejecute <strong>Get-SPWOPIBinding</strong> para ver la lista completa de las aplicaciones compatibles con la aplicación WOPI.</p></td>
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
<td><p>Le pide confirmación antes de ejecutar el comando. Para obtener más información, escriba el siguiente comando: <strong>get-help about_commonparameters</strong></p></td>
</tr>
<tr class="odd">
<td><p><strong>Extension</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Especifica las extensiones de nombre de archivo que se enlazarán. Ejecute <strong>Get-SPWOPIBinding</strong> para ver la lista de extensiones de nombre de archivo que admite la aplicación WOPI.</p></td>
</tr>
<tr class="even">
<td><p><strong>FileName</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Especifica la ruta de acceso del archivo xml que contiene la información de detección para la aplicación WOPI. Puede cargar la información de detección de un archivo xml en lugar de pedírsela directamente a la aplicación WOPI.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ProgId</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Especifica el identificador de programación (ProgID) de una aplicación para la que se crearán enlaces. Ejecute <strong>Get-SPWOPIBinding</strong> para ver la lista de ProgID compatibles con la aplicación WOPI. También puede usar este parámetro solo para asociar una acción a una carpeta de OneNote.</p></td>
</tr>
<tr class="even">
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

    New-SPWOPIBinding -ServerName "Server.corp.Contoso.com"

En este ejemplo se crean enlaces para todas las aplicaciones y extensiones de nombre de archivo que admite la aplicación WOPI en la granja de servidores actual de SharePoint en que se ejecuta el cmdlet.

\--------------EJEMPLO 2-----------------

    New-SPWOPIBinding -ServerName "Server.corp.Contoso.com" -Application "Excel"

En este ejemplo se asocia Excel a todas las acciones que la aplicación WOPI admite para Excel en la granja de servidores actual de SharePoint en que se ejecuta el cmdlet.

## Consulte también


[Get-SPWOPIBinding](get-spwopibinding.md)  
[Set-SPWOPIBinding](set-spwopibinding.md)  
[Remove-SPWOPIBinding](remove-spwopibinding.md)  


[Guía básica de contenido de Office Web Apps Server](content-roadmap-for-office-web-apps-server.md)  
[Usar Office Web Apps con SharePoint 2013](use-office-web-apps-with-sharepoint-2013.md)

