---
title: Usar Windows PowerShell para administrar SharePoint 2013
TOCTitle: Usar Windows PowerShell para administrar SharePoint 2013
ms:assetid: ae4901b4-505a-42a9-b8d4-fca778abc12e
ms:mtpsurl: https://technet.microsoft.com/es-es/library/Ee806878(v=office.15)
ms:contentKeyID: 48793537
ms.date: 12/23/2017
mtps_version: v=office.15
ms.translationtype: HT
---

# Usar Windows PowerShell para administrar SharePoint 2013

 

_**Se aplica a:**SharePoint Foundation 2013, SharePoint Server 2013 Enterprise, SharePoint Server 2013 Standard_

_**Última modificación del tema:**2016-12-16_

**Resumen:**obtenga información sobre los conceptos y los cmdlets básicos de Windows PowerShell y descubra cómo usar Windows PowerShell con SharePoint 2013.

En este artículo:

  - Información general

  - Acceso a Windows PowerShell para SharePoint 2013

  - Permisos

  - Scripts y directivas de ejecución

  - Aprendizaje de Windows PowerShell

## Información general

Windows PowerShell es un shell de comandos y lenguaje de secuencia de comandos que facilita a los administradores acceso a las interfaces de programación de aplicaciones (API) correspondientes. Los administradores pueden interactuar directamente con SharePoint 2013 para manipular aplicaciones web, colecciones de sitios, sitios, listas y mucho más. Además, los administradores pueden crear secuencias de comandos de cmdlets (que equivale a "command-lets").

Windows PowerShell 3.0 es un requisito previo para instalar SharePoint 2013. Se instalará al iniciar la Herramienta de preparación de Productos de Microsoft SharePoint en caso de que no esté instalada. De forma predeterminada Windows PowerShell se encuentra en la siguiente ruta de acceso: \<%SystemRoot%\>\\System32\\WindowsPowerShell\\v1.0\\PowerShell.exe.

Para obtener una lista de las nuevas características de Windows PowerShell 3.0, vea [Windows Management Framework 3.0](http://go.microsoft.com/fwlink/p/?linkid=272782).

Para una herramienta interactiva y guía que lo ayude a aprender la sintaxis de Windows PowerShell, vea [Generador de comandos de Windows PowerShell](http://go.microsoft.com/fwlink/p/?linkid=229854) y la [Guía de introducción](http://www.microsoft.com/download/en/details.aspx?id=27588).

Se recomienda usar Windows PowerShell para realizar tareas administrativas de línea de comandos. La herramienta de línea de comandos Stsadm ya no se usa, pero se ha incluido para ofrecer compatibilidad con las versiones anteriores del producto.

## Acceso a Windows PowerShell para SharePoint 2013

Tras instalar SharePoint 2013, los cmdlets de Windows PowerShell correspondientes estarán disponibles en Shell de administración de SharePoint 2013. En la Shell de administración de SharePoint podrá administrar la mayoría de los aspectos de SharePoint 2013. De este modo, podrá crear nuevas colecciones de sitios, aplicaciones web, cuentas de usuario, aplicaciones de servicio, proxies y mucho más. Los comandos que escriba en Shell de administración de SharePoint devuelven objetos de SharePoint basados en Microsoft .NET Framework. Puede aplicar estos objetos como entradas de comandos subsiguientes o para almacenar los objetos en variables locales para usarlos más tarde.

Con la Shell de administración de SharePoint, no es necesario registrar el complemento que contiene los cmdlets. El registro del módulo Microsoft.SharePoint.PowerShell.dll para los cmdlets de SharePoint 2013 es automático, como resultado de la línea `Add-PSSnapin Microsoft.SharePoint.PowerShell` del archivo SharePoint.ps1 ubicado en *%CommonProgramFiles%*\\Microsoft Shared\\Web Server Extensions\\15\\Config\\PowerShell\\Registration. Si decide usar la consola de Windows PowerShell, deberá registrar el complemento de forma manual.

Independientemente de si usa la Shell de administración de SharePoint o la consola de Windows PowerShell, podrá cargar complementos adicionales. Para más información, vea [Personalización de perfiles](http://go.microsoft.com/fwlink/p/?linkid=183166).

**Para obtener acceso a la Shell de administración de SharePoint**

1.  Inicie el Shell de administración de SharePoint.
    
      - Para Windows Server 2008 R2:
        
          - Haga clic en **Inicio**, en **Productos de Microsoft SharePoint 2013** y en **Shell de administración de SharePoint**.
    
      - Para Windows Server 2012:
        
          - En la pantalla **Inicio**, haga clic en **Shell de administración de SharePoint**.
            
            Si **Shell de administración de SharePoint** no aparece en la pantalla **Inicio**:
        
        <!-- end list -->
        
          - Haga clic con el botón secundario en **PC**, y haga clic en **Todas las aplicaciones** y en **Shell de administración de SharePoint**.
    
    Para más información sobre cómo interactuar con Windows Server 2012, vea [Navegación y tareas de administración comunes en Windows Server 2012](http://technet.microsoft.com/es-es/library/hh831491.aspx).


> [!NOTE]
> La Shell de administración de SharePoint 2013 y la consola de Windows PowerShell también difieren en el uso de la opción <CODE>ReuseThread</CODE>, que define el modo en que se usa el modelo de subprocesos. El uso de la Shell de administración de SharePoint 2013 se define con esta línea, <CODE>{Host.Runspace.ThreadOptions = "ReuseThread"}</CODE>, que se encuentra en el archivo SharePoint.ps1. Para más información, vea <A href="http://go.microsoft.com/fwlink/p/?linkid=183145">Opciones de subproceso PS</A>.



## Permisos

## Locales

Antes de poder usar el cmdlet **Add-SPShellAdmin** para conceder permisos a los usuarios para usar cmdlets de SharePoint 2013, asegúrese de que cumple todos los requisitos mínimos siguientes:

  - Debe ser miembro del rol de servidor fijo **securityadmin** en la instancia de SQL Server.

  - Debe ser miembro del rol de base de datos fija **db\_owner** en todas las bases de datos que se van a actualizar.

  - Debe pertenecer al grupo Administradores en el servidor donde vaya a usar el cmdlet de Windows PowerShell.


> [!NOTE]
> Si no dispone de estos permisos, póngase en contacto con el administrador del programa de instalación o con el administrador de SQL Server para solicitar los permisos.



Para información adicional sobre permisos de Windows PowerShell, vea Permisos y [Add-SPShellAdmin](https://technet.microsoft.com/es-es/library/ff607596\(v=office.15\))

Si no es miembro del rol **SharePoint\_Shell\_Access** o del grupo local **WSS\_Admin\_WPG**, use el cmdlet **Add-SPShellAdmin** para agregar el grupo **WSS\_Admin\_WPG** a todos los servidores web front-end de la granja de servidores de SharePoint y al rol **SharePoint\_Shell\_Access**. Si la base de datos de SQL Server no tiene el rol **SharePoint\_Shell\_Access**, dicho rol se creará automáticamente cuando inicie el cmdlet **Add-SPShellAdmin**. Tras iniciar el cmdlet **Add-SPShellAdmin**, los usuarios podrá usar los cmdlets de Windows PowerShell de SharePoint en entornos de granjas de varios servidores.


> [!NOTE]
> Cuando instale SharePoint 2013, la cuenta de usuario desde la que se inicie la instalación dispondrá de los permisos necesarios para usar los cmdlets de Windows PowerShell. En caso de que no se haya agregado algún usuario para usar un cmdlet de Windows PowerShell, use el cmdlet <STRONG>Add-SPShellAdmin</STRONG> para agregar usuarios.



Debe usar el cmdlet **Add-SPShellAdmin** para todas las bases de datos a las que desea otorgar acceso. Si no se especifica ninguna base de datos, se usará la base de datos de configuración de la granja de servidores. Si se especifica una base de datos, se incluirá la base de datos de contenido de la granja de servidores además de la base de datos de configuración de la granja especificada.

Para ver una lista de todos los cmdlets **SPShellAdmin**, en un símbolo del sistema de Windows PowerShell, escriba `Get-Command -Noun SPShellAdmin`.

## SharePoint Online

Asegúrese de que dispone de los siguientes permisos administrativos:

  - Debe tener asignado el rol de administrador global del sitio de SharePoint Online en el que use el cmdlet de Windows PowerShell. Para más información, vea [Grupos de usuarios y roles administrativos predeterminados](http://go.microsoft.com/fwlink/p/?linkid=242451).
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/JJ219448.important(Office.15).gif" title="Importante" alt="Importante" /><strong>Importante:</strong></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>Puede usar un grupo específico de Windows PowerShell con SharePoint Online. Para más información, vea <a href="https://technet.microsoft.com/es-es/library/fp161362(v=office.15)">PowerShell de Office 365 para SharePoint Online</a>.</td>
    </tr>
    </tbody>
    </table>


## Secuencias de comandos y directivas de ejecución

Aunque puede usar Windows PowerShell para realizar una tarea administrativa, también puede usar una secuencia de comandos para automatizar una serie de tareas. Una secuencia de comandos es un archivo de texto que contiene uno o más comandos de Windows PowerShell. Los nombres de archivo de las secuencias de comandos de Windows PowerShell tienen la extensión .ps1.

Para iniciar scripts, la directiva de ejecución mínima requerida para SharePoint 2013 es RemoteSigned, aunque la directiva predeterminada para Windows PowerShell es Restricted. Si la directiva se deja como Restricted, la Shell de administración de SharePoint 2013 cambiará la directiva de Windows PowerShell a RemoteSigned. Esto implica que debe seleccionar la opción **Ejecutar como administrador** para iniciar la Shell de administración de SharePoint 2013 con permiso administrativo elevado. Este cambio se aplicará a todas las sesiones de Windows PowerShell. Para más información, vea [Enumeración de ExecutionPolicy](http://go.microsoft.com/fwlink/p/?linkid=242452).

Para obtener información adicional sobre scripts y directivas de ejecución, vea [about\_scripts](http://go.microsoft.com/fwlink/p/?linkid=144310) y [about\_Execution\_Policies](http://go.microsoft.com/fwlink/p/?linkid=193050) respectivamente.

## Aprendizaje de Windows PowerShell

Existen varios recursos de aprendizaje de Windows PowerShell para profesionales de TI de SharePoint.

**Centro de secuencias de comandos de TechNet**

En el Centro de secuencias de comandos de TechNet se incluyen varios recursos que le ayudarán a aprender conceptos básicos del uso de Windows PowerShell. También se incluyen repositorios de secuencias de comandos con ejemplos usados frecuentemente con diversos productos de Microsoft. En la siguiente tabla se muestran los recursos de aprendizaje principales.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Página</th>
<th>Descripción</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="http://go.microsoft.com/fwlink/p/?linkid=187813">Documentación de Windows PowerShell en TechNet</a></p></td>
<td><p>En esta sección de la biblioteca de TechNet se incluyen copias web de los temas de Ayuda principales de Windows PowerShell. También se incluyen copias web del documento de introducción a Windows PowerShell, la ayuda de PowerShell.exe y un manual de Windows PowerShell.</p></td>
</tr>
<tr class="even">
<td><p><a href="http://go.microsoft.com/fwlink/p/?linkid=187815">Scripting con Windows PowerShell</a></p></td>
<td><p>Página principal de los recursos de aprendizaje de secuencias de comandos de Windows PowerShell.</p></td>
</tr>
<tr class="odd">
<td><p><a href="http://go.microsoft.com/fwlink/p/?linkid=187817">Manual del usuario de Windows PowerShell</a></p></td>
<td><p>Guía basada en web de introducción a Windows PowerShell.</p></td>
</tr>
<tr class="even">
<td><p><a href="http://go.microsoft.com/fwlink/p/?linkid=187819">Referencia rápida de Windows PowerShell</a></p></td>
<td><p>Copia descargable del documento de referencia rápida instalado con Windows PowerShell.</p></td>
</tr>
</tbody>
</table>


Al leer estos recursos, tenga en cuenta que resulta conveniente obtener información sobre los siguientes conceptos y cmdlets antes de usar Windows PowerShell para SharePoint 2013:

  - [Get-Command](http://go.microsoft.com/fwlink/p/?linkid=171069)

  - [Get-Member](http://go.microsoft.com/fwlink/p/?linkid=171070)

  - [Get-Help](http://go.microsoft.com/fwlink/p/?linkid=171068)

  - [Creación de alias](http://go.microsoft.com/fwlink/p/?linkid=113207)

  - [Canalizaciones de Windows PowerShell](http://go.microsoft.com/fwlink/p/?linkid=187808)

  - [Conjuntos de parámetros de cmdlet](http://go.microsoft.com/fwlink/p/?linkid=187810)

  - [Foreach-Object](http://go.microsoft.com/fwlink/p/?linkid=187812)

  - [Where-Object](http://go.microsoft.com/fwlink/p/?linkid=187811)

