---
title: New-OfficeWebAppsMachine
TOCTitle: New-OfficeWebAppsMachine
ms:assetid: b0385c4e-61fc-4607-a48c-64d8f4e80651
ms:mtpsurl: https://technet.microsoft.com/es-es/library/JJ219449(v=office.15)
ms:contentKeyID: 48793539
ms.date: 12/22/2017
mtps_version: v=office.15
ms.translationtype: HT
---

# New-OfficeWebAppsMachine

 

_**Se aplica a:**Office Web Apps Server_

_**Última modificación del tema:**2015-03-09_

Agrega el servidor actual a una granja de servidores Office Web Apps Server existente.

## Sintaxis

    New-OfficeWebAppsMachine [-MachineToJoin] <String> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-Roles <String[]>] [-WhatIf [<SwitchParameter>]]

## Descripción detallada

El cmdlet **New-OfficeWebAppsMachine** agrega el servidor actual a una granja de servidores Office Web Apps Server existente y ofrece la opción de establecer uno o más roles en el nuevo servidor.

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
<td><p><strong>MachineToJoin</strong></p></td>
<td><p>Obligatorio</p></td>
<td><p>System.String</p></td>
<td><p>Especifica el nombre de cualquier servidor que ya es miembro de la granja de servidores Office Web Apps Server.</p></td>
</tr>
<tr class="even">
<td><p><strong>Confirm</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Le pide confirmación antes de ejecutar el comando. Para obtener más información, escriba el siguiente comando: <strong>get-help about_commonparameters</strong></p></td>
</tr>
<tr class="odd">
<td><p><strong>Force</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Asume que la respuesta a cualquier mensaje de usuario es Sí.</p></td>
</tr>
<tr class="even">
<td><p><strong>Roles</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.String[]</p></td>
<td><p>Especifica uno o más roles de servidor, separados por comas, para asignar al nuevo servidor. Si no se especifica ningún rol, se asignan todos los roles al servidor.</p>
<p>Los tipos de rol son los siguientes:</p>
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

\------------------EJEMPLO 1---------------------

    New-OfficeWebAppsMachine -MachineToJoin server1.contoso.com

En este ejemplo se agrega el servidor actual a la granja de servidores Office Web Apps Server que se ejecuta en el servidor llamado server1.contoso.com.

## Consulte también


[Get-OfficeWebAppsMachine](get-officewebappsmachine.md)  
[Remove-OfficeWebAppsMachine](remove-officewebappsmachine.md)  
[Set-OfficeWebAppsMachine](set-officewebappsmachine.md)  


[Guía básica de contenido de Office Web Apps Server](content-roadmap-for-office-web-apps-server.md)  
[Implementar la infraestructura: Office Web Apps Server](deploy-the-infrastructure-office-web-apps-server.md)  
  

[](deploy-the-infrastructure-office-web-apps-server.md)

