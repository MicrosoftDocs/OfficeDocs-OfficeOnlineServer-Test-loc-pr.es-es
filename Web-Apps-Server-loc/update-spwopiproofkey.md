---
title: Update-SPWOPIProofKey
TOCTitle: Update-SPWOPIProofKey
ms:assetid: fe7f3a87-082e-4a43-a5f3-7be41d8e91a3
ms:mtpsurl: https://technet.microsoft.com/es-es/library/JJ219460(v=office.15)
ms:contentKeyID: 48793552
ms.date: 12/18/2017
mtps_version: v=office.15
ms.translationtype: HT
---

# Update-SPWOPIProofKey

 

_**Se aplica a:**Office Web Apps, SharePoint Foundation 2013, SharePoint Server 2013_

_**Última modificación del tema:**2015-03-09_

Actualiza la clave pública que se usa para establecer una conexión con la aplicación WOPI en la granja de SharePoint actual donde se ejecuta este cmdlet.

## Sintaxis

```PowerShell
Update-SPWOPIProofKey [-AssignmentCollection <SPAssignmentCollection>] [-ServerName <String>]
```

## Descripción detallada

El cmdlet **Update-SPWOPIProofKey** actualiza la clave pública que se usa para establecer una conexión con la aplicación WOPI (que puede ser un servidor que ejecuta Office Web Apps Server) en la granja actual de SharePoint en que se ejecuta este cmdlet. Puede usar este cmdlet si las claves de la granja de SharePoint y la aplicación WOPI no están sincronizadas. Si no lo están, es posible que los documentos no se abran en el explorador y que se muestren mensajes del tipo “Firma de prueba no válida para el archivo…” o “Firma de prueba no válida para la carpeta...” en los registros del Servicio de registro unificado (ULS).

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
<td><p><strong>ServerName</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Especifica la aplicación WOPI de la que se obtendrá la clave. Puede ser un servidor que ejecute Office Web Apps Server. Si falta este parámetro, se actualizarán las claves públicas de todas las aplicaciones WOPI conectadas a la granja actual de SharePoint.</p></td>
</tr>
</tbody>
</table>


## Tipos de entrada

## Tipos de valores devueltos

## Ejemplo

\--------------EJEMPLO-----------------

    Update-SPWOPIProofKey -ServerName "Server.corp.Contoso.com"

En este ejemplo se obtiene la clave pública actual de la aplicación WOPI (por ejemplo, un servidor que ejecuta Office Web Apps Server) y se actualiza la clave almacenada en la granja de SharePoint.

## Consulte también


[Guía básica de contenido de Office Web Apps Server](content-roadmap-for-office-web-apps-server.md)  
[Usar Office Web Apps con SharePoint 2013](use-office-web-apps-with-sharepoint-2013.md)

