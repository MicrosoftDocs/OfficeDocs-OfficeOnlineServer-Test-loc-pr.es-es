---
title: Establecer el comportamiento predeterminado para abrir documentos habilitados por el explorador (Office Web Apps cuando se usa con SharePoint 2013)
TOCTitle: Establecer el comportamiento predeterminado para abrir documentos habilitados por el explorador
ms:assetid: e27e0bc8-5fb5-4bb1-8157-d7c90654175e
ms:mtpsurl: https://technet.microsoft.com/es-es/library/Ee837425(v=office.15)
ms:contentKeyID: 50181350
ms.date: 12/18/2017
mtps_version: v=office.15
ms.translationtype: HT
---

# Establecer el comportamiento predeterminado para abrir documentos habilitados por el explorador (Office Web Apps cuando se usa con SharePoint 2013)

 

_**Se aplica a:**Office Web Apps, SharePoint Foundation 2013, SharePoint Server 2013_

_**Última modificación del tema:**2016-12-16_

**Resumen:**   explica cómo configurar el comportamiento predeterminado para abrir los documentos de Office en las colecciones de sitios y en las bibliotecas de documentos de SharePoint.

**Audiencia:** profesionales de TI

Para abrir un documento en una biblioteca de documentos de SharePoint 2013, simplemente haga clic en su título. Lo que sucede después (si el archivo se abre en una aplicación cliente o en el explorador) depende de varios factores, como el tipo de archivo del que se trata, la forma en que se configuró la granja de servidores de Office Web Apps Server y la forma en que se configuró la característica OpenInClient de la biblioteca o colección de sitios. Los siguientes pasos muestran cómo configurar el comportamiento de apertura predeterminado para documentos de Office donde se ha configurado SharePoint 2013 para usar Office Web Apps Server.

## Establecer cómo se abren los documentos desde las bibliotecas de SharePoint 2013

De manera predeterminada, después de configurar SharePoint 2013 para que use Office Web Apps Server, al hacer clic en un archivo de Word, PowerPoint, Excel o OneNote se abre en el explorador. Los documentos PDF se abren en Word Web App. Hay dos maneras de cambiar el comportamiento predeterminado para abrir archivos directamente:

  - **Para la granja de servidores de SharePoint 2013:** puede ajustar el comportamiento de apertura predeterminado por tipo de archivo para la granja de servidores de SharePoint 2013 con los cmdlets [New-SPWOPIBinding](https://docs.microsoft.com/en-us/powershell/module/sharepoint-server/New-SPWOPIBinding?view=sharepoint-ps) y [Set-SPWOPIBinding](https://docs.microsoft.com/en-us/powershell/module/sharepoint-server/Set-SPWOPIBinding?view=sharepoint-ps) de Windows PowerShell. Estos cmdlets también se pueden usar para [ajustar el comportamiento de los documentos PDF](http://go.microsoft.com/fwlink/p/?linkid=330246).

  - **En colecciones de sitios o bibliotecas de documentos** Los administradores y los usuarios de colecciones de sitios pueden usar la característica OpenInClient de SharePoint 2013 para especificar que los archivos de Office se abran en la aplicación cliente si está instalada. Los usuarios pueden cambiar esta configuración en las propiedades de las bibliotecas de documentos y los administradores de colecciones de sitios pueden cambiarla en Administración de colecciones de sitios o con el cmdlet [Enable-SPFeature](https://technet.microsoft.com/es-es/library/ff607803\(v=office.15\)) para habilitar la característica OpenInClient. Consulte en la sección siguiente los diferentes métodos para habilitar la característica OpenInClient.

En general, la característica OpenInClient invalida los enlaces WOPI establecidos entre SharePoint 2013 y Office Web Apps Server. En otras palabras, si se habilita la característica OpenInClient de una colección de sitios o biblioteca de SharePoint 2013, los documentos se abrirán en la aplicación cliente incluso si se ha configurado el servidor de SharePoint 2013 para usar Office Web Apps Server.


> [!NOTE]
> La configuración del comportamiento predeterminado para abrir los documentos habilitados para el explorador no afectará al hecho de que los usuarios puedan usar las características <STRONG>Desproteger</STRONG> y <STRONG>Enviar a</STRONG> en SharePoint 2013 para descargar documentos. Para obtener información sobre cómo configurar los permisos para desproteger, descargar y visualizar en SharePoint 2013, vea <A href="https://technet.microsoft.com/es-es/library/cc262939(v=office.15)">Planear los permisos para los sitios y el contenido en SharePoint 2013</A>.



## Establecer la característica OpenInClient para una biblioteca de documentos o colección de sitios

Use uno de los siguientes procedimientos para establecer la característica OpenInClient en SharePoint 2013.


> [!NOTE]
> Algunos de estos procedimientos usan el Shell de administración de SharePoint 2013 para ejecutar los cmdlets de SharePoint. Si elige usar la consola de Windows PowerShell, deberá agregar el complemento Microsoft.SharePoint.PowerShell mediante el cmdlet <STRONG>Add-PSSnapin</STRONG>. Para más información sobre cómo usar Windows PowerShell con SharePoint 2013, vea <A href="https://docs.microsoft.com/en-us/powershell/module/sharepoint-server/?view=sharepoint-ps">Usar Windows PowerShell para administrar SharePoint 2013</A>.




> [!NOTE]
> Puede completar las tareas en Conjuntos de aplicaciones de Office 2013 con un mouse, los métodos abreviados de teclado o el modo táctil. Para obtener más información sobre cómo usar los métodos abreviados del teclado o el modo táctil con los productos y servicios de Office, vea <A href="http://go.microsoft.com/fwlink/p/?linkid=249150">Métodos abreviados de teclado</A> y <A href="http://go.microsoft.com/fwlink/p/?linkid=253163">Guía táctil de Office</A>.



 **Establecer la característica OpenInClient para las colecciones de sitios**

1.  En la colección de sitios de SharePoint, elija el icono **Configuración** \> **Configuración del sitio**.

2.  En la página **Configuración del sitio**, en **Administración de colecciones de sitios**, elija **Características de la colección de sitios**.

3.  En la página **Características**, para la característica **Abrir los documentos en aplicaciones cliente de manera predeterminada**, elija **Activar** (se habilitará la característica OpenInClient) para abrir documentos en la aplicación cliente. Elija **Desactivar** (se deshabilitará la característica OpenInClient) para abrir documentos en el explorador.

 **Establecer el comportamiento de apertura predeterminado para las colecciones de sitios con Windows PowerShell**

1.  En primer lugar, asegúrese de que cumple con las pertenencias siguientes:
    
      - Rol fijo de servidor **securityadmin** en la instancia de SQL Server.
    
      - Rol fijo de base de datos **db\_owner** en todas las bases de datos que se van a cargar.
    
      - Grupo de administradores en el servidor en el que tenga los cmdlets de Windows PowerShell en funcionamiento.
    
    Además, eche un vistazo en [about\_Execution\_Policies](http://go.microsoft.com/fwlink/p/?linkid=193050) y agregue otras pertenencias necesarias.
    
    Los administradores pueden usar el cmdlet **Add-SPShellAdmin** para conceder los permisos necesarios para usar los cmdlets de SharePoint 2013.
    

    > [!NOTE]
    > Si no tiene permisos, póngase en contacto con el administrador del programa de instalación o con el administrador de SQL Server para solicitarlos. Para obtener información adicional sobre permisos de Windows PowerShell, vea <A href="https://docs.microsoft.com/en-us/powershell/module/sharepoint-server/?view=sharepoint-ps">Permissions</A> y <A href="https://technet.microsoft.com/es-es/library/ff607596(v=office.15)">Add-SPShellAdmin</A>.



2.  Abra un Shell de administración de SharePoint 2013 elevado:
    
    **En Windows Server 2008**
    
    1.  En el menú **Inicio**, seleccione **Todos los programas**.
    
    2.  Seleccione **Productos de Microsoft SharePoint 2013**.
    
    3.  Elija **Shell de administración de SharePoint 2013** y muestre el menú contextual (haga clic con el botón secundario en la opción).
    
    4.  En el menú contextual, elija **Ejecutar como administrador**.
    
    **En Windows Server 2012**
    
    1.  Haga pasar el dedo desde el borde de la pantalla para mostrar los accesos y elija **Buscar** para ver todas las aplicaciones que se encuentran instaladas en el equipo.
    
    2.  Elija (haga clic con el botón secundario en la opción) **Shell de administración de SharePoint 2013** para que aparezca la barra de la aplicación.
    
    3.  En la barra de la aplicación, seleccione **Ejecutar como administrador**.

3.  En el símbolo del sistema de Windows PowerShell, escriba uno de los siguientes comandos:
    
      - Para habilitar la característica OpenInClient para una colección de sitios específica (para abrir documentos en la aplicación cliente), escriba este comando:
        
            Enable-SPFeature 8A4B8DE2-6FD8-41e9-923C-C7C3C00F8295 -url <SiteCollURL>
        
        donde *\<SiteCollURL\>* es la dirección URL del conjunto de sitios.
    
      - Para habilitar la característica OpenInClient para todas las colecciones de sitios (para abrir documentos en la aplicación cliente), escriba este comando:
        
            Get-SPSite -limit ALL |foreach{ Enable-SPFeature 8A4B8DE2-6FD8-41e9-923C-C7C3C00F8295 -url $_.URL }
    
      - Para deshabilitar la característica OpenInClient para una colección de sitios específica (para abrir documentos en el explorador), escriba este comando:
        
            Disable-SPFeature 8A4B8DE2-6FD8-41e9-923C-C7C3C00F8295 -url <SiteCollURL>
        
        donde *\<SiteCollURL\>* es la dirección URL del conjunto de sitios.
    
      - Para deshabilitar la característica OpenInClient para todas las colecciones de sitios (para abrir documentos en el explorador), escriba este comando:
        
            Get-SPSite -limit ALL |foreach{ Disable-SPFeature 8A4B8DE2-6FD8-41e9-923C-C7C3C00F8295 -url $_.URL }

 **Establecer el comportamiento de apertura predeterminado para una biblioteca de documentos mediante la página de configuración de la biblioteca de documentos**

1.  En la página de la biblioteca de documentos, elija la pestaña **Biblioteca**.

2.  En el grupo **Configuración**, elija **Configuración de la biblioteca**.

3.  En la página **Configuración de la biblioteca de documentos**, elija **Configuración avanzada**.

4.  En la página **Configuración avanzada**, en **Abrir documento en el explorador**, seleccione una de las siguientes opciones:
    
      - **Abrir en la aplicación cliente**   Cuando un usuario elije un documento en esta biblioteca, el documento se abrirá en la aplicación cliente correspondiente, si está disponible.
    
      - **Abrir en el explorador**   Cuando un usuario elije un documento en esta biblioteca, el documento se abrirá en el explorador web en la aplicación web para ese tipo de documento. Cuando el documento se abre en la aplicación web, el usuario puede decidir si desea abrir el documento en la aplicación cliente.
    
      - **Usar el servidor predeterminado** Cuando un usuario elige un documento en esta biblioteca, el documento se abrirá según el comportamiento de apertura predeterminado que se especificó para el servidor que ejecuta SharePoint 2013.

 **Establecer el comportamiento de apertura predeterminado para bibliotecas de documentos protegidas con IRM mediante Windows PowerShell**

1.  En primer lugar, asegúrese de que cumple con las pertenencias siguientes:
    
      - Rol fijo de servidor **securityadmin** en la instancia de SQL Server.
    
      - Rol fijo de base de datos **db\_owner** en todas las bases de datos que se van a cargar.
    
      - Grupo de administradores en el servidor en el que tenga los cmdlets de Windows PowerShell en funcionamiento.
    
    Además, eche un vistazo en [about\_Execution\_Policies](http://go.microsoft.com/fwlink/p/?linkid=193050) y agregue otras pertenencias necesarias.
    
    Los administradores pueden usar el cmdlet **Add-SPShellAdmin** para conceder los permisos necesarios para usar los cmdlets de SharePoint 2013.
    

    > [!NOTE]
    > Si no tiene permisos, póngase en contacto con el administrador del programa de instalación o con el administrador de SQL Server para solicitarlos. Para obtener información adicional sobre permisos de Windows PowerShell, vea <A href="https://docs.microsoft.com/en-us/powershell/module/sharepoint-server/?view=sharepoint-ps">Permissions</A> y <A href="https://technet.microsoft.com/es-es/library/ff607596(v=office.15)">Add-SPShellAdmin</A>.



2.  Abra un Shell de administración de SharePoint 2013 elevado:
    
    **En Windows Server 2008**
    
    1.  En el menú **Inicio**, seleccione **Todos los programas**.
    
    2.  Seleccione **Productos de Microsoft SharePoint 2013**.
    
    3.  Elija **Shell de administración de SharePoint 2013** y muestre el menú contextual (haga clic con el botón secundario en la opción).
    
    4.  En el menú contextual, elija **Ejecutar como administrador**.
    
    **En Windows Server 2012**
    
    1.  Haga pasar el dedo desde el borde de la pantalla para mostrar los accesos y elija **Buscar** para ver todas las aplicaciones que se encuentran instaladas en el equipo.
    
    2.  Elija (haga clic con el botón secundario en la opción) **Shell de administración de SharePoint 2013** para que aparezca la barra de la aplicación.
    
    3.  En la barra de la aplicación, seleccione **Ejecutar como administrador**.

3.  Escriba el siguiente comando en el símbolo del sistema de Windows PowerShell:
    
        Get-SPWeb -site <SiteCollURL> | % {$_.Lists} | where {$_.IrmEnabled -eq $true} | % {$_.DefaultItemOpen =[Microsoft.Sharepoint.DefaultItemOpen]::<DefaultItemOpenSetting>; $_.Update()}
    
    donde:
    
      - *\<SiteCollURL\>* es la URL de la colección de sitios donde residen las bibliotecas de documentos.
    
      - *\<DefaultItemOpenSetting\>* es un valor de enumeración de **DefaultItemOpen** que especifica el comportamiento de apertura predeterminado. Use **PreferClient** para abrir documentos en sus aplicaciones cliente asociadas (si están disponible). Use **Browser** para abrir documentos en el explorador.

## Consulte también


[Get-SPWOPIBinding](https://docs.microsoft.com/en-us/powershell/module/sharepoint-server/Get-SPWOPIBinding?view=sharepoint-ps)  


[Guía básica de contenido de Office Web Apps Server](content-roadmap-for-office-web-apps-server.md)  
[Usar Windows PowerShell para administrar SharePoint 2013](https://docs.microsoft.com/en-us/powershell/module/sharepoint-server/?view=sharepoint-ps)  
[Office Web Apps Server](office-web-apps-server.md)  


[Get-SPWeb](https://technet.microsoft.com/es-es/library/ff607807\(v=office.15\))  
[Get-SPSite](https://technet.microsoft.com/es-es/library/ff607950\(v=office.15\))  
[Get-SPFeature](https://technet.microsoft.com/es-es/library/ff607945\(v=office.15\))

