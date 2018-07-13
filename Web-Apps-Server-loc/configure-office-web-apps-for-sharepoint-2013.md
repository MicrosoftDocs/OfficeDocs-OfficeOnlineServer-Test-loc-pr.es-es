---
title: Configurar Office Web Apps para SharePoint 2013
TOCTitle: Configurar Office Web Apps para SharePoint 2013
ms:assetid: a5276781-133b-413c-beca-b851e17c2081
ms:mtpsurl: https://technet.microsoft.com/es-es/library/Ff431687(v=office.15)
ms:contentKeyID: 48793533
ms.date: 12/24/2017
mtps_version: v=office.15
ms.translationtype: HT
---

# Configurar Office Web Apps para SharePoint 2013

 

_**Se aplica a:** Office Web Apps, SharePoint Foundation 2013, SharePoint Server 2013_

_**Última modificación del tema:** 2016-12-16_

**Resumen:** explica cómo configurar SharePoint 2013 para usar Office Web Apps.

**Audiencia:** profesionales de TI

Este artículo es una continuación de [Implementar Office Web Apps Server](deploy-office-web-apps-server.md), que explicaba cómo configurar el servidor que ejecuta Office Web Apps Server. Ahora configurará SharePoint 2013 para usar Office Web Apps Server. Primero, deberá ejecutar algunos cmdlets de Windows PowerShell desde SharePoint 2013, después de lo cual los usuarios podrán abrir los archivos de Office desde bibliotecas de documentos de SharePoint 2013 en un explorador.

Si no está familiarizado con las características de Office Web Apps Server, [consulte el tema de información general](office-web-apps-server-overview.md).

En este artículo:

  - Antes de configurar SharePoint 2013 para usar Office Web Apps Server

  - Configurar SharePoint 2013 para usar Office Web Apps Server

  - Solucionar problemas en Office Web Apps cuando se usa con SharePoint 2013

  - Desconectar SharePoint 2013 de Office Web Apps Server

## Antes de configurar SharePoint 2013 para usar Office Web Apps Server

Algunas cosas que debe comprobar antes de empezar:

  - Instale SharePoint 2013. Consulte [Instalación de SharePoint 2013](https://technet.microsoft.com/es-es/library/cc303424\(v=office.15\)) para obtener instrucciones.

  - Asegúrese de que todas las aplicaciones web de SharePoint 2013 usan la autenticación basada en notificaciones. Si se recurre a aplicaciones web de SharePoint 2013 que usan la autenticación de modo clásico, no funcionarán ni la edición ni la representación de Office Web Apps. Para más información, vea el tema sobre los [requisitos de autenticación de SharePoint para Office Web Apps](plan-office-web-apps-used-with-sharepoint-2013.md).

  - Para permitir a los usuarios editar (y no solo leer) documentos de Office en un explorador web, necesitará una licencia de edición. Además, deberá habilitar la edición en la granja de servidores de Office Web Apps Server. Para más información sobre los requisitos de las licencias, vea el tema acerca de la [Licensing Office Web Apps for editing Office files](plan-office-web-apps-used-with-sharepoint-2013.md).

  - Si inicia sesión en SharePoint 2013 con la cuenta del sistema, no podrá probar la conexión entre SharePoint 2013 y Office Web Apps Server. Si desea hacerlo, inicie sesión con otra cuenta.

  - Si la memoria resulta insuficiente, pueden producirse errores en las vistas previas de los documentos de Office en Office Web Apps. Consulte el artículo sobre los [Hardware requirements—web servers, application servers, and single server installations](https://technet.microsoft.com/es-es/4d88c402-24f2-449b-86a6-6e7afcfec0cd\(office.15\)#hwforwebserver) para SharePoint 2013. Los requisitos son los mismos que para Office Web Apps Server.

## Configurar SharePoint 2013 para usar Office Web Apps Server

Elija una de las secciones siguientes, en función de si desea usar HTTP o HTTPS. HTTP se suele recomendar únicamente para entornos de prueba. En entornos de producción, el protocolo HTTPS más seguro es la mejor opción.

## En un entorno de prueba que usa HTTP

Para esta configuración, asegúrese de que ha configurado Office Web Apps Server siguiendo los pasos descritos en el tema sobre cómo [Deploy a single-server Office Web Apps Server farm that uses HTTP](deploy-office-web-apps-server.md). Asegúrese de configurar la granja de Office Web Apps Server para que use HTTP y una dirección URL interna. El artículo [Vídeo: Configurar Office Web Apps para SharePoint 2013](video-configure-office-web-apps-for-sharepoint-2013.md) muestra cómo instalar Office Web Apps Server y cómo configurar SharePoint 2013 para usar Office Web Apps Server en un entorno de prueba.

## Paso 1: abrir una Consola de administración de SharePoint 2013 con privilegios elevados

Elija el procedimiento que corresponda al sistema operativo de su servidor.

**En Windows Server 2008 R2**

1.  Haga clic en **Inicio** \> **Todos los programas** \> **Productos de Microsoft SharePoint 2013**.

2.  Haga clic con el botón secundario en **Consola de administración de SharePoint 2013** y haga clic en **Ejecutar como administrador**.

**En Windows Server 2012**

1.  Presione la tecla del logotipo de Windows+Q o deslice rápidamente desde el borde de la pantalla para mostrar los accesos y haga clic en **Buscar** para ver todas las aplicaciones que se encuentran instaladas en el equipo.

2.  Haga clic con el botón secundario en **Consola de administración de SharePoint 2013** para mostrar la barra de la aplicación.

3.  En la barra de la aplicación, haga clic en **Ejecutar como administrador**.

## Paso 2: crear el enlace entre SharePoint 2013 y Office Web Apps Server

Ejecute el comando siguiente, donde \<WacServerName\> es el nombre de dominio completo (FQDN) de la dirección URL que ha establecido como URL interna. Este será el punto de entrada para el tráfico de Office Web Apps Server. En este entorno de prueba, debe especificar el parámetro –AllowHTTP para que SharePoint 2013 pueda recibir la información de detección de la granja de servidores de Office Web Apps Server con HTTP. Si no lo hace, SharePoint 2013 intentará usar HTTPS para comunicarse con la granja de servidores de Office Web Apps Server, y el comando no funcionará.

```PowerShell
    New-SPWOPIBinding -ServerName <WacServerName> -AllowHTTP
```

Después de ejecutar este comando, verá una lista de enlaces en el símbolo del sistema de Windows PowerShell.

Si necesita ayuda, vea [New-SPWOPIBinding](https://docs.microsoft.com/en-us/powershell/module/sharepoint-server/New-SPWOPIBinding?view=sharepoint-ps).

## Paso 3: ver las zonas WOPI para los enlaces de SharePoint

Office Web Apps Server usa zonas para determinar la dirección URL (interna o externa) y el protocolo (HTTP o HTTPS) que deben usarse para establecer la comunicación con el host, en este caso, SharePoint 2013. La zona predeterminada que usa SharePoint Server 2013 es **internal-https**. Ejecute el siguiente comando para ver su zona actual.

```PowerShell
    Get-SPWOPIZone
```

La zona WOPI mostrada por este comando debe ser **internal-http**. Si se muestra correctamente, vaya al paso 5. De lo contrario, vea el siguiente paso.

Si necesita ayuda, vea [Get-SPWOPIZone](https://docs.microsoft.com/en-us/powershell/module/sharepoint-server/Get-SPWOPIZone?view=sharepoint-ps).

## Paso 4: cambiar la zona WOPI a internal-http

Si el resultado del paso 3 es **internal-https**, ejecute el comando siguiente para cambiar la zona a **internal-http**. Este cambio es imprescindible, ya que las zonas de SharePoint 2013 y de la granja de servidores de Office Web Apps Server deben coincidir.

```PowerShell
    Set-SPWOPIZone -zone "internal-http"
```

Para comprobar que la nueva zona es **internal-http**, vuelva a ejecutar **Get-SPWOPIZone**.

Si necesita ayuda, vea [Set-SPWOPIZone](https://docs.microsoft.com/en-us/powershell/module/sharepoint-server/Set-SPWOPIZone?view=sharepoint-ps) y [Get-SPWOPIZone](https://docs.microsoft.com/en-us/powershell/module/sharepoint-server/Get-SPWOPIZone?view=sharepoint-ps).

## Paso 5: cambiar el valor AllowOAuthOverHttp a True en SharePoint 2013

Si desea usar Office Web Apps con SharePoint 2013 sobre HTTP en un entorno de prueba, establezca AllowOAuthOverHttp en **True**. De lo contrario, Office Web Apps no funcionará. Para comprobar el estado actual, ejecute el ejemplo siguiente.

```PowerShell
    (Get-SPSecurityTokenServiceConfig).AllowOAuthOverHttp
```

Si este comando devuelve **False**, ejecute los comandos siguientes para establecerlo en **True**.

```PowerShell
    $config = (Get-SPSecurityTokenServiceConfig)
```
```PowerShell
    $config.AllowOAuthOverHttp = $true
```
```PowerShell
    $config.Update()
```

Ejecute de nuevo el comando siguiente para comprobar que el valor AllowOAuthOverHttp ya se encuentra establecido en **True**.

```PowerShell
    (Get-SPSecurityTokenServiceConfig).AllowOAuthOverHttp
```

Si necesita ayuda, vea [Get-SPSecurityTokenServiceConfig](https://technet.microsoft.com/es-es/library/ff607642\(v=office.15\)).

## Paso 6: comprobar que Office Web Apps está funcionando

En SharePoint 2013, asegúrese de que no ha iniciado sesión en la cuenta del sistema, ya que no podrá editar ni ver documentos con Office Web Apps. Vaya a una biblioteca de documentos de SharePoint 2013 que contenga documentos de Office y vea un archivo de Word, PowerPoint, Excel u OneNote. El documento debe abrirse en un explorador que muestre el archivo con Office Web Apps.

Si este paso genera errores, vea el tema sobre cómo Solucionar problemas en Office Web Apps cuando se usa con SharePoint 2013.

## En un entorno de producción que usa HTTPS

Antes de iniciar los procedimientos siguientes, realice los pasos de los temas sobre cómo [Deploy a single-server Office Web Apps Server farm that uses HTTPS](deploy-office-web-apps-server.md#singlehttps) o sobre cómo [Deploy a multi-server, load-balanced Office Web Apps Server farm that uses HTTPS](deploy-office-web-apps-server.md#multihttps) para comprobar que ha configurado Office Web Apps Server.

## Paso 1: abrir la Consola de administración de SharePoint 2013

Elija el procedimiento que corresponda al sistema operativo de su servidor.

**En Windows Server 2008 R2**

1.  Seleccione **Inicio** \> **Todos los programas** \> **Productos de Microsoft SharePoint 2013**.

2.  Haga clic con el botón secundario en **Consola de administración de SharePoint 2013** para mostrar el menú contextual y haga clic en **Ejecutar como administrador**.

**En Windows Server 2012**

1.  Presione la tecla del logotipo de Windows+Q o deslice rápidamente desde el borde de la pantalla para mostrar los accesos y haga clic en **Buscar** para ver todas las aplicaciones que se encuentran instaladas en el equipo.

2.  Haga clic con el botón secundario en **Consola de administración de SharePoint 2013** para mostrar la barra de la aplicación.

3.  En la barra de la aplicación, haga clic en **Ejecutar como administrador**.

## Paso 2: crear el enlace entre SharePoint 2013 y Office Web Apps Server

Ejecute el comando siguiente, donde \<WacServerName\> es el nombre de dominio completo (FQDN) de la dirección URL que ha establecido como URL interna. Este será el punto de entrada para el tráfico de Office Web Apps Server.

```PowerShell
    New-SPWOPIBinding -ServerName <WacServerName> 
```

Si necesita ayuda, vea [New-SPWOPIBinding](https://docs.microsoft.com/en-us/powershell/module/sharepoint-server/New-SPWOPIBinding?view=sharepoint-ps).

## Paso 3: ver la zona WOPI de SharePoint 2013

Office Web Apps Server usa zonas para determinar la dirección URL (interna o externa) y el protocolo (HTTP o HTTPS) que deben usarse para establecer la comunicación con el host, en este caso, SharePoint 2013. La zona predeterminada que usa SharePoint Server 2013 es **internal-https**. Para comprobar que esta es la zona activa, ejecute el comando siguiente.

```PowerShell
    Get-SPWOPIZone
```

Anote la zona WOPI que aparece.

Si necesita ayuda, vea [Get-SPWOPIZone](https://docs.microsoft.com/en-us/powershell/module/sharepoint-server/Get-SPWOPIZone?view=sharepoint-ps).

## Paso 4: cambiar la zona WOPI si es necesario

En función del entorno, es posible que deba cambiar la zona WOPI. Si la granja de servidores de SharePoint es tanto interna como externa, especifique que es externa. Si solo es interna, especifíquelo.

Si el resultado del paso 3 es **internal-https** y la granja de servidores de SharePoint es solo interna, puede omitir este paso. Si es interna y externa, ejecute el comando siguiente para cambiar la zona a **external-https**.

```PowerShell
    Set-SPWOPIZone -zone "external-https"
```

Si necesita ayuda, vea [Set-SPWOPIZone](https://docs.microsoft.com/en-us/powershell/module/sharepoint-server/Set-SPWOPIZone?view=sharepoint-ps).

## Paso 5: comprobar que Office Web Apps está funcionando

En SharePoint 2013, asegúrese de que no ha iniciado sesión en la cuenta del sistema, ya que no podrá editar ni ver documentos con Office Web Apps. Vaya a una biblioteca de documentos de SharePoint 2013 que contenga documentos de Office y vea un archivo de Word, PowerPoint, Excel u OneNote. El documento debe abrirse en un explorador que muestre el archivo con Office Web Apps.

Si este paso genera errores, vea el tema sobre cómo Solucionar problemas en Office Web Apps cuando se usa con SharePoint 2013.

## Solucionar problemas en Office Web Apps cuando se usa con SharePoint 2013

Si Office Web Apps no funciona correctamente cuando se usa con SharePoint 2013, busque el síntoma entre las posibilidades que se indican a continuación y expanda el encabezado correspondiente para ver los pasos necesarios para solucionar el problema.

## Problema: al seleccionar el vínculo "Nuevo documento" en una biblioteca de SharePoint, se solicita cargar un documento y no se da opción de crear un nuevo documento de Office. Al elegir (o hacer clic en) un documento de Office, se abre el archivo en la aplicación cliente. No se muestran vistas previas de los documentos de Office.

Intente solucionar el problema con las opciones siguientes.

**Compruebe que la aplicación web de SharePoint usa la autenticación basada en notificaciones para crear el nuevo documento.**

Solo pueden abrir archivos en Office Web Apps las aplicaciones web que usan la autenticación basada en notificaciones. Para determinar el proveedor de autenticación que usa la aplicación web, siga estos pasos:

1.  En Administración central de SharePoint 2013, haga clic en **Administrar aplicaciones de web**.

2.  Seleccione la aplicación web que desea comprobar y haga clic en **Proveedores de autenticación** en la cinta de opciones.

Para que Office Web Apps funcione correctamente con la aplicación web, el proveedor de autenticación debe establecerse en **Autenticación basada en notificaciones**. Para resolver este problema, puede eliminar la aplicación web y crearla de nuevo con este tipo de autenticación o bien puede cambiar el método de autenticación de la aplicación. Para más información, vea el tema sobre los [requisitos de autenticación de SharePoint para Office Web Apps](plan-office-web-apps-used-with-sharepoint-2013.md).

**Asegúrese de que las zonas WOPI coinciden en SharePoint 2013 y en la granja de servidores de Office Web Apps.**

Para ello, ejecute el comando siguiente en SharePoint Server:

```PowerShell
    Get-SPWopiZone 
```

Obtendrá uno de los siguientes resultados:

  - internal-https

  - internal-http

  - external-https

  - external-http

A continuación, ejecute el comando siguiente en SharePoint Server.

```PowerShell
    Get-SPWOPIBinding
```

En los resultados, busque **WopiZone: *zone***. Si los resultados de Get-SPWopiZone no coinciden con la zona que devuelve Get-SPWOPIBinding, ejecute el cmdlet **Set-SPWOPIZone -Zone** en SharePoint Server para cambiar la zona WOPI y hacerla coincidir con el resultado de Get-SPWOPIBinding. Para más información sobre cómo usar estos cmdlets, vea [Get-SPWOPIBinding](https://docs.microsoft.com/en-us/powershell/module/sharepoint-server/Get-SPWOPIBinding?view=sharepoint-ps), [Set-SPWOPIBinding](https://docs.microsoft.com/en-us/powershell/module/sharepoint-server/Set-SPWOPIBinding?view=sharepoint-ps) y [Get-SPWOPIZone](https://docs.microsoft.com/en-us/powershell/module/sharepoint-server/Get-SPWOPIZone?view=sharepoint-ps).

## Problema: recibe un error que indica que el documento no se puede abrir para editarlo cuando intenta editar un documento de Office en Office Web Apps.

En algunos casos, es posible que los usuarios que pertenecen a los grupos de seguridad de Active Directory (AD) no puedan editar documentos en el explorador. La solución es garantizar que la Aplicación de servicio de perfiles de usuario (UPA) esté configurada correctamente y sincronizada completamente con pertenencias de grupo y usuarios. Para obtener más información, vea el artículo de Knowledge Base sobre la [incapacidad de SharePoint 2013 para editar archivos de Office Web Apps 2013 con usuarios que pertenecen a grupos de seguridad](https://support.microsoft.com/es-es/kb/2908321).

## Problema: cuando intenta ver un documento de Office en Office Web Apps, aparece el error "Lo sentimos, se ha producido un problema".

Asegúrese de que no ha iniciado sesión en la cuenta del sistema, ya que no podrá editar ni ver documentos. Inicie sesión como otro usuario e intente obtener acceso de nuevo a Office Web Apps.

## Problema: cuando intenta ver un documento de Office en Office Web Apps, aparece el error "Se ha producido un problema y no se puede abrir este documento".

Si configuró Office Web Apps en un entorno de prueba con HTTP, compruebe que el valor AllowOAuthOverHttp se encuentra establecido en **True**, tal como se describe en el Paso 5: cambiar el valor AllowOAuthOverHttp a True en SharePoint 2013.

Si agregó dominios a la lista de permitidos con el cmdlet [New-OfficeWebAppsHost](https://docs.microsoft.com/en-us/powershell/module/officewebapps/new-officewebappshost?view=officewebapps-ps), asegúrese de estar accediendo a Office Web Apps desde un dominio de host que se encuentre en la lista de permitidos. Para ver los dominios de host en la lista de permitidos, en el Office Web Apps Server abra el símbolo del sistema de Windows PowerShell como administrador y ejecute el cmdlet [Get-OfficeWebAppsHost](https://docs.microsoft.com/en-us/powershell/module/officewebapps/get-officewebappshost?view=officewebapps-ps). Para agregar un dominio a la lista de permitidos, use el cmdlet [New-OfficeWebAppsHost](https://docs.microsoft.com/en-us/powershell/module/officewebapps/new-officewebappshost?view=officewebapps-ps).

## Problema: ve el error "Lo sentimos. Word Web App no puede abrir este documento porque el servicio está ocupado. Vuelva a intentarlo más tarde" cuando intenta ver un documento de Office en Office Web Apps.

  - ¿Por casualidad, instaló Office Web Apps Server en un controlador de dominio? Desafortunadamente, Office Web Apps Server no se puede ejecutar en un controlador de dominio. Office Web Apps Server debe instalarse en un servidor separado que forme parte de un dominio. Para más información, vea el tema sobre los [requisitos de software, hardware y configuración para Office Web Apps Server](plan-office-web-apps-server.md).

  - Asegúrese de que ejecuta SharePoint 2013 versión 15.0.4420.1017 o posterior. En el servidor de SharePoint 2013, siga estos pasos para comprobar el número de versión de compilación:
    
    1.  Vaya a **Inicio** \> **Todos los programas** \> **Productos de Microsoft SharePoint 2013** \> **Administración central de SharePoint 2013**.
    
    2.  Elija **Configuración del sistema** \> **Administrar servidores en esta granja de servidores**.
    
    Compruebe que la **versión de la base de datos de configuración** sea **15.0.4420.1017** o posterior. Si no es así, vaya al [Centro de actualización para Office, servidores de Office y productos relacionados](https://go.microsoft.com/fwlink/p/?linkid=160585) para obtener más información.

## Problema: ve el error "Archivo no encontrado. La dirección URL del archivo original no es válida o el documento no es accesible de forma pública. Verifique que la dirección URL sea correcta y comuníquese con el propietario del documento" cuando intenta ver un documento de Office en Office Web Apps mediante una dirección URL generada por el usuario.

¿Intenta abrir un documento que tiene un tamaño de archivo superior a 10 megabytes desde una dirección URL generada por el usuario? Asegúrese de que el documento no supere los 10 megabytes.

## Problema: no se muestran vistas previas de los documentos de Office en SharePoint 2013. En su lugar, aparece el error "Este contenido no se puede mostrar en un marco".

Si la memoria resulta insuficiente, pueden producirse errores en las vistas previas de los documentos de Office. Vea el tema sobre los [Hardware requirements—web servers, application servers, and single server installations](https://technet.microsoft.com/es-es/4d88c402-24f2-449b-86a6-6e7afcfec0cd\(office.15\)#hwforwebserver) para comprobar los requisitos de memoria para SharePoint 2013. Los requisitos son los mismos que para Office Web Apps Server.

## Problema: ve el error "Una conexión de datos está configurada para usar siempre el archivo de conexión y {0:ExcelWebApp} no admite archivos de conexión externos. No se pudo actualizar la siguiente conexión: Conexiones de datos".

Esto ocurre porque Office Web Apps Server no admite el archivo de conexión de datos de Office (ODC) que almacena la información de conexión de datos. Para solucionar este problema, siga estos pasos:

1.  Abra el libro en una aplicación cliente de Excel.

2.  Haga clic en **Datos** \> **Conexiones**.

3.  Seleccione las conexiones de datos que aparecen en el mensaje y haga clic en **Propiedades**.

4.  Haga clic en la pestaña **Definición**.

5.  Desactive la casilla **Utilizar siempre archivo de conexión**.

6.  Vuelva a cargar el libro en la biblioteca de documentos de SharePoint.

Para permitir que las personas interactúen con libros que contienen un modelo de datos o vistas de Power View en una ventana del explorador, configure Servicios de Excel en SharePoint Server para que se muestren los libros. Esto requiere que un administrador de SharePoint ejecute el cmdlet New-SPWOPISupressionSetting en el servidor donde está instalado SharePoint Server. Para más información, vea [New-SPWOPISuppressionSetting](https://docs.microsoft.com/en-us/powershell/module/sharepoint-server/New-SPWOPISuppressionSetting?view=sharepoint-ps) y [Administrar Servicios de Excel en SharePoint Server 2013](https://technet.microsoft.com/es-es/library/ee681487\(v=office.15\)).

## Desconectar SharePoint 2013 de Office Web Apps Server

Si por cualquier motivo desea desconectar SharePoint 2013 de Office Web Apps Server, use el siguiente ejemplo de comando.

```PowerShell
    Remove-SPWOPIBinding -All:$true
```

Si necesita ayuda, vea [Remove-SPWOPIBinding](https://docs.microsoft.com/en-us/powershell/module/sharepoint-server/Remove-SPWOPIBinding?view=sharepoint-ps).

## Consulte también


[New-SPWOPIBinding](https://docs.microsoft.com/en-us/powershell/module/sharepoint-server/New-SPWOPIBinding?view=sharepoint-ps)  
[Set-SPWOPIZone](https://docs.microsoft.com/en-us/powershell/module/sharepoint-server/Set-SPWOPIZone?view=sharepoint-ps)  


[Guía básica de contenido de Office Web Apps Server](content-roadmap-for-office-web-apps-server.md)  
[Implementar Office Web Apps Server](deploy-office-web-apps-server.md)  
  

[](deploy-office-web-apps-server.md)

