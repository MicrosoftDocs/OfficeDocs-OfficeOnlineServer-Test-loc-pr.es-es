---
title: Set-OfficeWebAppsFarm
TOCTitle: Set-OfficeWebAppsFarm
ms:assetid: 6b0b434f-5d19-4e63-9296-cf104b2f3da8
ms:mtpsurl: https://technet.microsoft.com/es-es/library/JJ219442(v=office.15)
ms:contentKeyID: 48793529
ms.date: 12/22/2017
mtps_version: v=office.15
ms.translationtype: HT
---

# Set-OfficeWebAppsFarm

 

_**Se aplica a:**Office Web Apps Server_

_**Última modificación del tema:**2015-03-09_

Configura las opciones de una granja de servidores de Office Web Apps Server existente.

## Sintaxis

    Set-OfficeWebAppsFarm [-AllowCEIP <SwitchParameter>] [-AllowHttp <SwitchParameter>] [-AllowHttpSecureStoreConnections <SwitchParameter>] [-CacheLocation <String>] [-CacheSizeInGB <Nullable>] [-CertificateName <String>] [-ClipartEnabled <SwitchParameter>] [-Confirm [<SwitchParameter>]] [-DocumentInfoCacheSize <Nullable>] [-EditingEnabled <SwitchParameter>] [-ExcelAllowExternalData <SwitchParameter>] [-ExcelConnectionLifetime <Nullable>] [-ExcelExternalDataCacheLifetime <Nullable>] [-ExcelPrivateBytesMax <Nullable>] [-ExcelRequestDurationMax <Nullable>] [-ExcelSessionTimeout <Nullable>] [-ExcelWarnOnDataRefresh <SwitchParameter>] [-ExcelWorkbookSizeMax <Nullable>] [-ExternalURL <String>] [-FarmOU <String>] [-Force <SwitchParameter>] [-InternalURL <String>] [-LogLocation <String>] [-LogRetentionInDays <Nullable>] [-LogVerbosity <String>] [-MaxMemoryCacheSizeInMB <Nullable>] [-MaxTranslationCharacterCount <Nullable>] [-OpenFromUncEnabled <SwitchParameter>] [-OpenFromUrlEnabled <SwitchParameter>] [-OpenFromUrlThrottlingEnabled <SwitchParameter>] [-PicturePasteDisabled <SwitchParameter>] [-Proxy <String>] [-RecycleActiveProcessCount <Nullable>] [-RemovePersonalInformationFromLogs <SwitchParameter>] [-RenderingLocalCacheLocation <String>] [-SSLOffloaded <SwitchParameter>] [-TranslationEnabled <SwitchParameter>] [-TranslationServiceAddress <String>] [-TranslationServiceAppId <String>] [-WhatIf [<SwitchParameter>]]

## Descripción detallada

El cmdlet **Set-OfficeWebAppsFarm** configura las opciones de una granja de servidores de Office Web Apps Server existente.

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
<td><p><strong>AllowCEIP</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Habilita la elaboración de informes del Programa para la mejora de la experiencia del usuario (CEIP) en todos los servidores de la granja de servidores de Office Web Apps Server.</p>
<div class="alert">
<table>
<thead>
<tr class="header">
<th><img src="images/JJ219448.important(Office.15).gif" title="Importante" alt="Importante" /><strong>Importante:</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Para aplicar el cambio, es necesario reiniciar todos los servidores de la granja de servidores de Office Web Apps Server.</td>
</tr>
</tbody>
</table>

</div></td>
</tr>
<tr class="even">
<td><p><strong>AllowHttp</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Indica que los sitios de IIS se deben aprovisionar en el puerto 80 para el acceso HTTP. Use <strong>AllowHTTP</strong> solo en entornos en los que todos los PC necesiten IPSEC (cifrado completo) o en entornos de prueba que no contengan archivos confidenciales.</p>
<p>Se habilita automáticamente al habilitar <strong>SSLOffloaded</strong>.</p>
<div class="alert">
<table>
<thead>
<tr class="header">
<th><img src="images/JJ219448.important(Office.15).gif" title="Importante" alt="Importante" /><strong>Importante:</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Debe reiniciar todos los servidores de la granja de servidores para que este cambio tenga efecto.</td>
</tr>
</tbody>
</table>

</div></td>
</tr>
<tr class="odd">
<td><p><strong>AllowHttpSecureStoreConnections</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Indica que se pueden establecer conexiones seguras con el almacén usando conexiones sin SSL (como HTTP). El valor predeterminado es <strong>False</strong>.</p>
<p>Use <strong>AllowHTTPSecureStoreConnections</strong> solo en entornos en que todos los PC requieran IPSEC (cifrado completo) o en entornos de prueba que no contengan archivos confidenciales.</p></td>
</tr>
<tr class="even">
<td><p><strong>CacheLocation</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Especifica la ubicación de la caché de disco global que se usa para almacenar archivos de imagen representados. La ubicación predeterminada es <strong>%programdata%\Microsoft\OfficeWebApps\Working\d\</strong>.</p></td>
</tr>
<tr class="odd">
<td><p><strong>CacheSizeInGB</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.Nullable</p></td>
<td><p>Especifica el tamaño máximo de la caché de disco global en gigabytes.</p>
<p>El tipo debe ser un valor entero entre <strong>0</strong> y cualquier entero positivo. El tamaño predeterminado es <strong>15</strong> GB.</p></td>
</tr>
<tr class="even">
<td><p><strong>CertificateName</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Especifica el nombre descriptivo del certificado que usa Office Web Apps Server para crear enlaces HTTPS.</p>
<p>Si el certificado especificado no se encuentra o ha expirado, o si el valor especificado está asociado a más de un certificado, se registra un error y no se crea la granja de servidores.</p>
<div class="alert">
<table>
<thead>
<tr class="header">
<th><img src="images/JJ219448.important(Office.15).gif" title="Importante" alt="Importante" /><strong>Importante:</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Este valor se usa en todos los servidores que se unen a la granja de servidores de Office Web Apps Server. Por lo tanto, todos los servidores de la granja de servidores deben tener un certificado que tenga este nombre descriptivo.</td>
</tr>
</tbody>
</table>

</div>
<p>No es necesario que especifique el parámetro <strong>CertificateName</strong> si usa el parámetro <strong>AllowHttp</strong> o <strong>SSLOffloaded</strong>.</p>
<div class="alert">
<table>
<thead>
<tr class="header">
<th><img src="images/JJ219448.important(Office.15).gif" title="Importante" alt="Importante" /><strong>Importante:</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Debe reiniciar todos los servidores de la granja de servidores para que este cambio tenga efecto.</td>
</tr>
</tbody>
</table>

</div></td>
</tr>
<tr class="odd">
<td><p><strong>ClipartEnabled</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Habilita la compatibilidad para insertar imágenes prediseñadas desde documentos de Office.com a Office. Esta característica requiere una comunicación entre servidor y web configurada directamente o con un proxy que especifique con el parámetro <strong>Proxy</strong>.</p></td>
</tr>
<tr class="even">
<td><p><strong>Confirm</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Le pide confirmación antes de ejecutar el comando. Para obtener más información, escriba el siguiente comando: <strong>get-help about_commonparameters</strong>.</p></td>
</tr>
<tr class="odd">
<td><p><strong>DocumentInfoCacheSize</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.Nullable</p></td>
<td><p>Especifica el número máximo de registros de conversión de documentos que hay almacenados en una caché de memoria.</p>
<p>El valor predeterminado es <strong>5000</strong> registros.</p></td>
</tr>
<tr class="even">
<td><p><strong>EditingEnabled</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Habilita la compatibilidad para editar en el explorador. El valor predeterminado es <strong>False</strong>. Solo puede definirlo como <strong>True</strong> si tiene la licencia adecuada para usar la función de edición.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ExcelAllowExternalData</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Habilita la actualización de datos externos compatibles en libros de Excel Web App con conexiones a datos externos. El valor predeterminado es <strong>True</strong>.</p></td>
</tr>
<tr class="even">
<td><p><strong>ExcelConnectionLifetime</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.Nullable</p></td>
<td><p>Especifica la duración, en segundos, de las conexiones de datos externos para Excel Web App. El valor predeterminado es de <strong>1800</strong> segundos.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ExcelExternalDataCacheLifetime</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.Nullable</p></td>
<td><p>Especifica la duración, en segundos, de la caché de datos externos de Excel Web App. El valor predeterminado es de <strong>300</strong> segundos.</p></td>
</tr>
<tr class="even">
<td><p><strong>ExcelPrivateBytesMax</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.Nullable</p></td>
<td><p>Especifica el máximo de bytes privados, en megabytes, que usa Excel Web App. Cuando se establece en <strong>-1</strong>, el máximo de bytes privados usa el 50 por ciento de la memoria física del PC.</p>
<p>El tipo debe ser <strong>-1</strong> o cualquier entero positivo. El valor predeterminado es <strong>-1.</strong></p>
<div class="alert">
<table>
<thead>
<tr class="header">
<th><img src="images/JJ219448.important(Office.15).gif" title="Importante" alt="Importante" /><strong>Importante:</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Debe reiniciar todos los servidores de la granja de servidores para que este cambio tenga efecto.</td>
</tr>
</tbody>
</table>

</div></td>
</tr>
<tr class="odd">
<td><p><strong>ExcelRequestDurationMax</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.Nullable</p></td>
<td><p>Especifica la duración máxima, en segundos, para una única solicitud en una sesión. Transcurrido este tiempo, expira la solicitud.</p>
<p>El tipo debe ser <strong>-1</strong> (sin límite) o un entero entre <strong>1</strong> y <strong>2073600</strong>. El valor predeterminado es <strong>300</strong>.</p></td>
</tr>
<tr class="even">
<td><p><strong>ExcelSessionTimeout</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.Nullable</p></td>
<td><p>Especifica el tiempo, en segundos, que permanece activa una sesión en Excel Web App cuando no hay ninguna actividad del usuario. Los valores válidos incluyen los siguientes:</p>
<p><strong>-1</strong> : la sesión nunca expira.</p>
<p><strong>0</strong> : la sesión expira al final de una única solicitud</p>
<p>De <strong>1</strong> a <strong>2073600</strong>: la sesión permanece activa de 1 segundo a 24 días. El valor predeterminado es <strong>450</strong>.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ExcelWarnOnDataRefresh</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Desactiva o activa el cuadro de diálogo de advertencia que se muestra al actualizar los datos de Excel Web App.</p></td>
</tr>
<tr class="even">
<td><p><strong>ExcelWorkbookSizeMax</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.Nullable</p></td>
<td><p>Especifica el tamaño máximo en megabytes de un libro que se puede cargar.</p>
<p>El tipo debe ser un valor entero entre <strong>1</strong> y <strong>2000</strong>. El valor predeterminado es <strong>10</strong>.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ExternalURL</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Especifica la raíz de la dirección URL que usan los clientes para acceder a la granja de servidores de Office Web Apps Server desde Internet. En el caso de una granja de servidores de Office Web Apps Server de carga equilibrada y multiservidor, la URL externa se enlaza a la dirección IP del equilibrador de carga orientado externamente.</p>
<p>Una granja de servidores de Office Web Apps Server necesita al menos una dirección URL, que se establece usando <strong>ExternalURL</strong> o <strong>InternalURL</strong>. Puede definir URL internas y externas.</p></td>
</tr>
<tr class="even">
<td><p><strong>FarmOU</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Especifica el nombre de la unidad organizativa (OU) de Active Directory a la que deben pertenecer los servidores para unirse a la granja de servidores de Office Web Apps Server. Use este parámetro para impedir que servidores no autorizados (es decir, servidores que no están en la OU) se unan a una granja de servidores de Office Web Apps Server.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Force</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Suprime los mensajes de los usuarios respondiendo &quot;Sí&quot;.</p></td>
</tr>
<tr class="even">
<td><p><strong>InternalURL</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Especifica la raíz de la dirección URL que deben usar los clientes para acceder a la granja de servidores Office Web Apps Server desde la intranet.</p>
<p>Una granja de servidores de Office Web Apps Server necesita al menos una dirección URL, que se establece con <strong>ExternalURL</strong> o <strong>InternalURL</strong>. Puede definir URL internas y externas.</p></td>
</tr>
<tr class="odd">
<td><p><strong>LogLocation</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Especifica la ubicación del PC local en la que se almacenan los registros de actividad.</p>
<p>La ubicación sirve para todos los servidores de la granja y no se puede personalizar en cada servidor. La ubicación predeterminada es <strong>%programdata%\Microsoft\OfficeWebApps\Data\Logs\ULS\.</strong></p>
<p>Asegúrese de dejar el suficiente espacio en disco en la unidad en la que se almacenan los registros.</p>
<div class="alert">
<table>
<thead>
<tr class="header">
<th><img src="images/JJ219448.important(Office.15).gif" title="Importante" alt="Importante" /><strong>Importante:</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Debe reiniciar todos los servidores de la granja de servidores para que este cambio tenga efecto.</td>
</tr>
</tbody>
</table>

</div></td>
</tr>
<tr class="even">
<td><p><strong>LogRetentionInDays</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.Nullable</p></td>
<td><p>Especifica el número de días que se almacenan las entradas del registro. Las que son anteriores a la fecha configurada se recortan.</p>
<p>El tipo debe ser un valor entero entre <strong>0</strong> y <strong>365</strong>. El valor predeterminado es <strong>7</strong> días.</p>
<div class="alert">
<table>
<thead>
<tr class="header">
<th><img src="images/JJ219448.important(Office.15).gif" title="Importante" alt="Importante" /><strong>Importante:</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Debe reiniciar todos los servidores de la granja de servidores para que este cambio tenga efecto.</td>
</tr>
</tbody>
</table>

</div></td>
</tr>
<tr class="odd">
<td><p><strong>LogVerbosity</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Especifica cuánta información se almacena en los archivos del registro de seguimiento. Los valores son los siguientes:</p>
<p><strong>VerboseEX</strong> escribe detalle de bajo nivel en el archivo del registro de seguimiento. Es útil para seguimientos que puedan tener un gran volumen.</p>
<p><strong>Verbose</strong> escribe detalle de bajo nivel en el archivo del registro de seguimiento.</p>
<p><strong>Medium</strong> escribe detalle de nivel medio en el archivo del registro de seguimiento.</p>
<p><strong>High</strong> escribe detalle de alto nivel en el archivo del registro de seguimiento.</p>
<p><strong>Monitorable</strong> escribe seguimientos que representan una ruta de acceso de código poco habitual y acciones que deben supervisarse.</p>
<p><strong>Unexpected</strong> escribe seguimientos que representan una ruta de acceso de código inesperada que debe supervisarse.</p>
<p><strong>None</strong> no escribe ninguna información de seguimiento en el archivo del registro de seguimiento.</p>
<div class="alert">
<table>
<thead>
<tr class="header">
<th><img src="images/JJ219448.important(Office.15).gif" title="Importante" alt="Importante" /><strong>Importante:</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Si deja <strong>LogVerbosity</strong> en un nivel bajo durante un período de tiempo prolongado, el rendimiento se verá afectado de manera negativa.</td>
</tr>
</tbody>
</table>

</div>
<div class="alert">
<table>
<thead>
<tr class="header">
<th><img src="images/JJ219448.important(Office.15).gif" title="Importante" alt="Importante" /><strong>Importante:</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Debe reiniciar todos los servidores de la granja de servidores para que este cambio tenga efecto.</td>
</tr>
</tbody>
</table>

</div></td>
</tr>
<tr class="even">
<td><p><strong>MaxMemoryCacheSizeInMB</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.Nullable</p></td>
<td><p>Especifica, en megabytes, la cantidad máxima de memoria que puede usar la caché de representación.</p>
<p>El tipo debe ser un valor entero entre <strong>0</strong> y cualquier entero positivo. El tamaño predeterminado es <strong>1024</strong> MB.</p></td>
</tr>
<tr class="odd">
<td><p><strong>MaxTranslationCharacterCount</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.Nullable</p></td>
<td><p>Especifica la cantidad máxima de caracteres que puede tener un documento para traducirse.</p>
<p>El tipo debe ser un valor entero. Se puede establecer en 0 para indicar que no hay ningún límite o entre <strong>2000</strong> y <strong>2.000.000</strong>. El valor predeterminado es <strong>125.000</strong>.</p></td>
</tr>
<tr class="even">
<td><p><strong>OpenFromUncEnabled</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Activa o desactiva la capacidad de usar visores en línea pera ver archivos de Office de una ruta de acceso UNC.</p>
<p>Para que los visores en línea puedan mostrar los archivos de rutas de acceso UNC, es necesario definir OpenFromUrlEnabled en True.</p></td>
</tr>
<tr class="odd">
<td><p><strong>OpenFromUrlEnabled</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Activa o desactiva la capacidad de usar visores en línea pera ver archivos de Office desde una dirección URL o ruta de acceso UNC.</p></td>
</tr>
<tr class="even">
<td><p><strong>OpenFromUrlThrottlingEnabled</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Limita el número de solicitudes de apertura desde direcciones URL de un servidor específico en un período de tiempo determinado. Los valores de limitación predeterminados, que no se pueden configurar, garantizan que ninguna granja de servidores de Office Web Apps Server sobrecargue a un solo servidor con solicitudes para mostrar contenido en los visores en línea.</p></td>
</tr>
<tr class="odd">
<td><p><strong>PicturePasteDisabled</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Desactiva la capacidad de que los usuarios peguen imágenes de una páginas web enOffice Web Apps. El valor predeterminado es <strong>False</strong>. Si <strong>OpenFromURLEnabled</strong> se establece en <strong>True</strong> y <strong>PicturePasteDisabled</strong> no se establece o se establece en <strong>False</strong>, los usuarios pueden pegar imágenes en Office Web Apps.</p></td>
</tr>
<tr class="even">
<td><p><strong>Proxy</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Especifica la dirección URL del servidor proxy que se configura para permitir solicitudes HTTP a sitios externos. Por lo general, se configura con los parámetros <strong>ClipartEnabled</strong> y <strong>TranslationEnabled</strong>.</p></td>
</tr>
<tr class="odd">
<td><p><strong>RecycleActiveProcessCount</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.Nullable</p></td>
<td><p>Especifica el número de archivos que un único proceso de Word o PowerPoint puede representar antes de que se recicle el proceso.</p>
<p>El tipo debe ser un valor entero entre <strong>1</strong> y <strong>1000</strong>. El valor predeterminado es <strong>5</strong>.</p>
<div class="alert">
<table>
<thead>
<tr class="header">
<th><img src="images/JJ219448.important(Office.15).gif" title="Importante" alt="Importante" /><strong>Importante:</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Debe reiniciar todos los servidores de la granja de servidores para que este cambio tenga efecto.</td>
</tr>
</tbody>
</table>

</div></td>
</tr>
<tr class="even">
<td><p><strong>RemovePersonalInformationFromLogs</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Ofrece la mejor validación posible de información personal de registros de Office Web Apps Server y sustituye valores por un hash SHA256. La información potencialmente validada puede ser:</p>
<ul>
<li><p>Nombres de documentos y direcciones URL</p></li>
<li><p>Direcciones IP</p></li>
<li><p>Dirección de correo</p></li>
<li><p>Nombres de usuario</p></li>
</ul>
<p>El valor predeterminado es <strong>False</strong>. Habilitar este parámetro no garantiza que la información personal no se vaya a registrar en los registros de Office Web Apps Server.</p></td>
</tr>
<tr class="odd">
<td><p><strong>RenderingLocalCacheLocation</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Especifica la ubicación de la caché temporal para que la usen los servicios de visualización de Word y PowerPoint.</p>
<p>La ubicación predeterminada es <strong>%programdata%\Microsoft\OfficeWebApps\Working\waccache\</strong>.</p></td>
</tr>
<tr class="even">
<td><p><strong>SSLOffloaded</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Indica a los servidores de la granja de servidores de Office Web Apps Server que la SSL está descargada del equilibrador de carga. Cuando <strong>SSLOffloaded</strong> está habilitado, las aplicaciones web están enlazadas al puerto 80 (HTTP) del servidor local. Sin embargo, el HTML que hace referencia a otros recursos, como CSS o imágenes, usa direcciones URL de HTTPS para dichas referencias.</p>
<div class="alert">
<table>
<thead>
<tr class="header">
<th><img src="images/JJ219448.important(Office.15).gif" title="Importante" alt="Importante" /><strong>Importante:</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Debe reiniciar todos los servidores de la granja de servidores para que este cambio tenga efecto.</td>
</tr>
</tbody>
</table>

</div></td>
</tr>
<tr class="odd">
<td><p><strong>TranslationEnabled</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><div class="alert">
<table>
<thead>
<tr class="header">
<th><img src="images/JJ219448.important(Office.15).gif" title="Importante" alt="Importante" /><strong>Importante:</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Habilita la compatibilidad para la traducción automática de documentos usando Microsoft Translator, un servicio en línea que traduce texto entre idiomas. El archivo traducido se muestra en Word Web App. Como Microsoft Translator es un servicio en línea, debe habilitar la comunicación entre servidor y web directamente o usando un proxy que puede especificar con el parámetro <strong>Proxy</strong>.<br />
Microsoft Translator puede recopilar datos para mejorar la calidad de las traducciones.</td>
</tr>
</tbody>
</table>

</div></td>
</tr>
<tr class="even">
<td><p><strong>TranslationServiceAddress</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Especifica la dirección URL del servidor de traducción al que se envían las solicitudes de traducción. El valor predeterminado es el servicio en línea de Microsoft Translator. Normalmente, este parámetro no se usa a menos que deba cambiar los servicios de traducción.</p>
<div class="alert">
<table>
<thead>
<tr class="header">
<th><img src="images/JJ219448.important(Office.15).gif" title="Importante" alt="Importante" /><strong>Importante:</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Para aplicar el cambio, es necesario reiniciar todos los servidores de la granja de Office Web Apps Server.</td>
</tr>
</tbody>
</table>

</div></td>
</tr>
<tr class="odd">
<td><p><strong>TranslationServiceAppId</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Especifica el identificador de la aplicación del servicio de traducción. El valor predeterminado es el identificador de la aplicación pública de Office Web Apps. Normalmente, este parámetro no se usa a menos que haya negociado servicios adicionales con Microsoft Translator y le hayan dado un identificador de aplicación privada.</p></td>
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

    Set-OfficeWebAppsFarm -ClipartEnabled:$true

En este ejemplo se habilita la inserción de imágenes prediseñadas desde Office.com.

\------------------EJEMPLO 2---------------------

    Set-OfficeWebAppsFarm -EditingEnabled:$true

En este ejemplo se habilita la función de edición de Office Web Apps.

\------------------EJEMPLO 3---------------------

    Set-OfficeWebAppsFarm -OpenFromUncEnabled:$false

En este ejemplo se desactiva la capacidad de ver cualquier archivo de Office desde una ruta de acceso UNC.

## Consulte también


[New-OfficeWebAppsFarm](new-officewebappsfarm.md)  
[Get-OfficeWebAppsFarm](get-officewebappsfarm.md)  


[Guía básica de contenido de Office Web Apps Server](content-roadmap-for-office-web-apps-server.md)  
[Implementar la infraestructura: Office Web Apps Server](deploy-the-infrastructure-office-web-apps-server.md)  
  

[](deploy-the-infrastructure-office-web-apps-server.md)

