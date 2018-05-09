---
title: Set-OfficeWebAppsMachine
TOCTitle: Set-OfficeWebAppsMachine
ms:assetid: aeba2638-be88-4030-80fe-7e4bcd30309b
ms:mtpsurl: https://technet.microsoft.com/es-es/library/JJ219448(v=office.15)
ms:contentKeyID: 48793538
ms.date: 12/22/2017
mtps_version: v=office.15
ms.translationtype: HT
---

# Set-OfficeWebAppsMachine

 

_**Se aplica a:**Office Web Apps Server_

_**Última modificación del tema:**2015-03-09_

Cambia la configuración del servidor actual que se encuentra en una granja de servidores de Office Web Apps Server.

## Sintaxis

    Set-OfficeWebAppsMachine [-Confirm [<SwitchParameter>]] [-Master <String>] [-Roles <String[]>] [-WhatIf [<SwitchParameter>]]

## Descripción detallada

El cmdlet **Set-OfficeWebAppsMachine** cambia la configuración del servidor actual que está en una granja de servidores Office Web Apps Server. La configuración incluye los roles del servidor actual y del servidor maestro designado para la granja de servidores.

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
<td><p><strong>Confirm</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Le pide confirmación antes de ejecutar el comando. Para obtener más información, escriba el siguiente comando: <strong>get-help about_commonparameters</strong></p></td>
</tr>
<tr class="even">
<td><p><strong>Master</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p></p>
<p>Especifica el servidor que almacena los archivos de configuración de la granja de servidores maestra.</p>
<p>Si establece el servidor local como maestro, debe ejecutar <strong>Set-OfficeWebAppsMachine -Master</strong> en todos los servidores restantes de la granja de servidores Office Web Apps Server para que señalen al nuevo maestro.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Roles</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.String[]</p></td>
<td><p>Especifica la lista de roles de servidor para asignar al servidor local, separados por comas.</p>
<p>Los tipos de rol son los siguientes:</p>
<p><strong>All</strong></p>
<p><strong>FrontEnd</strong></p>
<p><strong>WordBackEnd</strong></p>
<p><strong>ExcelBackEnd</strong></p>
<p><strong>PowerPointBackEnd</strong></p>
<div class="alert">
<table>
<thead>
<tr class="header">
<th><img src="images/JJ219448.important(Office.15).gif" title="Importante" alt="Importante" /><strong>Importante:</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Como procedimiento recomendado, aconsejamos que todos los servidores de una granja de servidores Office Web Apps Server ejecuten todos los roles. La asignación de roles no es útil hasta que la granja de servidores Office Web Apps Server contenga aproximadamente 50 servidores.</td>
</tr>
</tbody>
</table>

</div></td>
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

\------------------EJEMPLO 1---------------------

    (Get-OfficeWebAppsFarm).Machines

En este ejemplo se muestran los roles de cada servidor de la granja de servidores Office Web Apps Server.

\------------------EJEMPLO 2---------------------

    Set-OfficeWebAppsMachine -Roles FrontEnd

En este ejemplo se configura el servidor actual como servidor front-end.

\------------------EJEMPLO 3---------------------

    Set-OfficeWebAppsMachine -Roles All

En este ejemplo se configura el servidor actual para hospedar todos los roles.

## Consulte también


[Get-OfficeWebAppsMachine](get-officewebappsmachine.md)  
[New-OfficeWebAppsMachine](new-officewebappsmachine.md)  
[Remove-OfficeWebAppsMachine](remove-officewebappsmachine.md)  


[Guía básica de contenido de Office Web Apps Server](content-roadmap-for-office-web-apps-server.md)  
[Implementar la infraestructura: Office Web Apps Server](deploy-the-infrastructure-office-web-apps-server.md)  
  

[](deploy-the-infrastructure-office-web-apps-server.md)

