---
title: Repair-OfficeWebAppsFarm
TOCTitle: Repair-OfficeWebAppsFarm
ms:assetid: 083d8e25-ce82-4884-9bbc-06375185011c
ms:mtpsurl: https://technet.microsoft.com/es-es/library/JJ219433(v=office.15)
ms:contentKeyID: 48793518
ms.date: 12/22/2017
mtps_version: v=office.15
ms.translationtype: HT
---

# Repair-OfficeWebAppsFarm

 

_**Se aplica a:**Office Web Apps Server_

_**Última modificación del tema:**2015-03-09_

Quita todos los servidores marcados como en mal estado de una granja de servidores de Office Web Apps Server.

## Sintaxis

    Repair-OfficeWebAppsFarm [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## Descripción detallada

El cmdlet **Repair-OfficeWebAppsFarm** quita todos los servidores marcados como en mal estado de una granja de servidores de Office Web Apps Server. Este cmdlet actualiza la topología de la granja de servidores pero no limpia los servicios y las aplicaciones web de los servidores que se quitan. Por este motivo, se recomienda realizar un esfuerzo para ejecutar el cmdlet **Remove-OfficeWebAppsMachine** desde los servidores en mal estado para quitarlos de la granja de servidores de forma limpia. Use el cmdlet **Repair-OfficeWebAppsFarm** solo si los servidores en mal estado han generado problemas y no puede ejecutar en ellos directamente el cmdlet **Remove-OfficeWebAppsMachine**.

Si existen varios servidores en mal estado, se le pregunta antes de que quitar cada servidor. Si no existen servidores en mal estado, este cmdlet no hace nada.

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
<td><p><strong>Force</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Asume que la respuesta a cualquier mensaje de usuario es Sí.</p></td>
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

    (Get-OfficeWebAppsFarm).Machines

En este ejemplo se muestra el estado de mantenimiento de todos los servidores en la granja de servidores de Office Web Apps Server.

\------------------EJEMPLO 2---------------------

    Repair-OfficeWebAppsFarm

En este ejemplo se quitan todos los servidores en mal estado de la granja de servidores de Office Web Apps Server.

## Consulte también


[New-OfficeWebAppsFarm](new-officewebappsfarm.md)  
[Set-OfficeWebAppsFarm](set-officewebappsfarm.md)  
[Get-OfficeWebAppsFarm](get-officewebappsfarm.md)  


[Guía básica de contenido de Office Web Apps Server](content-roadmap-for-office-web-apps-server.md)  
[Implementar la infraestructura: Office Web Apps Server](deploy-the-infrastructure-office-web-apps-server.md)  
  

[](deploy-the-infrastructure-office-web-apps-server.md)

