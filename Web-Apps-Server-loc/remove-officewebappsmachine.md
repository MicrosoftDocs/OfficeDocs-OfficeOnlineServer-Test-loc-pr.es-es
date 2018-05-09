---
title: Remove-OfficeWebAppsMachine
TOCTitle: Remove-OfficeWebAppsMachine
ms:assetid: 5ad806f2-67c6-41ed-a708-69db800f492a
ms:mtpsurl: https://technet.microsoft.com/es-es/library/JJ219440(v=office.15)
ms:contentKeyID: 48793527
ms.date: 12/22/2017
mtps_version: v=office.15
ms.translationtype: HT
---

# Remove-OfficeWebAppsMachine

 

_**Se aplica a:**Office Web Apps Server_

_**Última modificación del tema:**2015-03-09_

Quita el servidor actual de la granja de servidores de Office Web Apps Server.

## Sintaxis

    Remove-OfficeWebAppsMachine [-Confirm [<SwitchParameter>]] [-WhatIf [<SwitchParameter>]]

## Descripción detallada

El cmdlet **Remove-OfficeWebAppsMachine** quita el servidor actual de la granja de servidores de Office Web Apps Server. Como parte de este proceso, el cmdlet quita las aplicaciones web y cierra los servicios relacionados con Office Web Apps Server. Si no puede ejecutar el cmdlet **Remove-OfficeWebAppsMachine** desde el servidor que desea quitar, use el cmdlet **Repair-OfficeWebAppsFarm** desde cualquier otro servidor de la granja de servidores de Office Web Apps.


> [!NOTE]
> Si el servidor local se designa como servidor maestro en la granja de servidores de Office Web Apps Server, no puede quitarlo de la granja hasta que asigne otro servidor como maestro mediante el cmdlet <STRONG>Set-OfficeWebAppsMachine</STRONG> o hasta que quite el resto de servidores de la granja.



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

    Remove-OfficeWebAppsMachine

En este ejemplo se quita el servidor actual de la granja de servidores de Office Web Apps Server.

## Consulte también


[Get-OfficeWebAppsMachine](get-officewebappsmachine.md)  
[New-OfficeWebAppsMachine](new-officewebappsmachine.md)  
[Set-OfficeWebAppsMachine](set-officewebappsmachine.md)  
[Repair-OfficeWebAppsFarm](repair-officewebappsfarm.md)  


[Guía básica de contenido de Office Web Apps Server](content-roadmap-for-office-web-apps-server.md)  
[Implementar la infraestructura: Office Web Apps Server](deploy-the-infrastructure-office-web-apps-server.md)  
  

[](deploy-the-infrastructure-office-web-apps-server.md)

