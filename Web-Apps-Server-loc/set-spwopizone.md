---
title: Set-SPWOPIZone
TOCTitle: Set-SPWOPIZone
ms:assetid: bc751cc4-8ac8-45f7-b6ea-da6fcb5473ac
ms:mtpsurl: https://technet.microsoft.com/es-es/library/JJ219451(v=office.15)
ms:contentKeyID: 48793541
ms.date: 12/23/2017
mtps_version: v=office.15
ms.translationtype: HT
---

# Set-SPWOPIZone

 

_**Se aplica a:**Office Web Apps, SharePoint Foundation 2013, SharePoint Server 2013_

_**Última modificación del tema:**2015-03-09_

Configura la zona que la granja de SharePoint actual usará para desplazarse con el explorador a la aplicación WOPI.

## Sintaxis

    Set-SPWOPIZone [[-Zone] <String>] [-AssignmentCollection <SPAssignmentCollection>] [-Confirm [<SwitchParameter>]] [-WhatIf [<SwitchParameter>]]

## Descripción detallada

El cmdlet **Set-SPWOPIZone** configura la zona que usará la granja actual de SharePoint para navegar con el explorador hasta la aplicación WOPI (por ejemplo, un servidor que ejecute Office Web Apps Server). La página SharePoint Server del explorador crea un marco que contiene una página en la aplicación WOPI. Este parámetro de configuración determina la zona de la URL de la página de la aplicación WOPI.

Si no define la zona, el valor predeterminado es “internal-HTTPS”. Si selecciona una zona que no es compatible con la aplicación WOPI, Office Web Apps no funcionará. Use solo HTTP si se encuentra en una red totalmente segura que usa IPSEC (cifrado total) o en un entorno de prueba que no contenga datos confidenciales.

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
<td><p><strong>Zone</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Especifica la zona. Para obtener una lista de las zonas que admite la aplicación WOPI, ejecute <strong>Get-SPWOPIBinding</strong>.</p>
<p>Si tiene una granja de SharePoint que es interna y externa, especifique que es externa. Si tiene una grana de SharePoint que es solo interna, especifique que es interna. Use solo HTTP si se encuentra en una red totalmente segura que usa IPSEC (cifrado total) o en un entorno de prueba que no contenga datos confidenciales. A continuación se indican las opciones posibles:</p>
<p>- Internal-HTTP</p>
<p>- Internal-HTTPS</p>
<p>- External-HTTP</p>
<p>- External-HTTPS</p></td>
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
<td><p>Le pide confirmación antes de ejecutar el comando. Para obtener más información, escriba el siguiente comando: <strong>get-help about_commonparameters</strong>.</p></td>
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

\--------------EJEMPLO----------------

    Set-SPWOPIZone -Zone "external-https"

En este ejemplo se configura la granja actual de SharePoint para usar conexiones externas en HTTPS a la aplicación WOPI (por ejemplo, un servidor que ejecute Office Web Apps Server).

## Consulte también


[Get-SPWOPIZone](get-spwopizone.md)  


[Guía básica de contenido de Office Web Apps Server](content-roadmap-for-office-web-apps-server.md)  
[Usar Office Web Apps con SharePoint 2013](use-office-web-apps-with-sharepoint-2013.md)

