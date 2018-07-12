---
title: Implementar Office Web Apps Server
TOCTitle: Implementar Office Web Apps Server
ms:assetid: e4d51dc4-6460-437d-aa8e-0ae4d3aa8cc5
ms:mtpsurl: https://technet.microsoft.com/es-es/library/JJ219455(v=office.15)
ms:contentKeyID: 48793546
ms.date: 12/22/2017
mtps_version: v=office.15
ms.translationtype: HT
---

# Implementar Office Web Apps Server

 

_<strong>Se aplica a:</strong>Office Web Apps Server_

_<strong>Última modificación del tema:**2017-10-05_

**Resumen:** explica cómo implementar Office Web Apps Server de forma local para su uso por parte de SharePoint 2013 y Lync Server 2013.

**Audiencia:** profesionales de TI

Tenga en cuenta que en este artículo se explica la instalación de Office Web Apps Server para su empresa. Si está buscando ayuda con la copia personal de Office o Office Web Apps, consulte [https://support.office.com](http://support.office.com).

La implementación de [Office Web Apps Server](office-web-apps-server-overview.md) implica instalar cierto software necesario y ejecutar algunos comandos de Windows PowerShell, pero en general el proceso está diseñado para llevarse a cabo de forma muy sencilla. Este artículo lo guía a través de los procedimientos necesarios para preparar los servidores y luego le proporciona los comandos de Windows PowerShell para configurar la granja de servidores de Office Web Apps Server.

En este artículo:

  - Ver un vídeo para aprender cómo se hace

  - Revisar estos recursos antes de comenzar

  - Preparar servidores para ejecutar Office Web Apps Server

  - Implementar la granja de servidores de Office Web Apps Server

  - Si ve los mensajes “500 excepciones de servicio web” o “500.21: error interno del servidor”

## Ver un vídeo para aprender cómo se hace

Vea el siguiente vídeo para aprender a configurar Office Web Apps Server en un entorno de prueba. También obtendrá una vista previa de cómo configurar SharePoint 2013 para usar Office Web Apps Server.

**Configurar Office Web Apps Server en un entorno de prueba**

> [!VIDEO https://www.microsoft.com/es-es/videoplayer/embed/179bf96f-09e1-407a-bb1b-a8e6623eabae]

## Revisar estos recursos antes de comenzar

Asegúrese de haber leído estos recursos antes de empezar:

  - Para obtener información detallada acerca de los requisitos de hardware y software, [eche un vistazo a las instrucciones de planeación](plan-office-web-apps-server.md).

  - De manera predeterminada, Office Web Apps Server le permite ver archivos de Office, pero no editarlos. Para hacerlo, necesitará una licencia de edición, sobre la que puede obtener información en [Planificar Office Web Apps (cuando se usa con SharePoint 2013)](plan-office-web-apps-used-with-sharepoint-2013.md) y [Configurar licencias en SharePoint Server 2013](https://technet.microsoft.com/es-es/library/jj219627\(v=office.15\)).


> [!NOTE]  
> Puede completar las tareas en todo Conjuntos de aplicaciones de Office 2013 con un mouse, los métodos abreviados de teclado o el modo táctil. Para información sobre cómo usar los métodos abreviados y el modo táctil con los productos y servicios de Office, consulte <A href="http://go.microsoft.com/fwlink/p/?linkid=249150">Métodos abreviados de teclado</A> y <A href="http://go.microsoft.com/fwlink/p/?linkid=253163">Guía de tecnología táctil de Office</A>.



## Preparar servidores para ejecutar Office Web Apps Server

Realice los siguientes procedimientos en todos los servidores para ejecutar Office Web Apps Server.

**Figura: los pasos para preparar los servidores para Office Web Apps Server**

![Los tres pasos principales para preparar los servidores para Office Web Apps Server.](images/JJ219455.af2a4690-4f8b-42c3-aab5-f7066bc0a936(Office.15).gif "Los tres pasos principales para preparar los servidores para Office Web Apps Server.") 

## Paso 1: instalar el software necesario para Office Web Apps Server

Windows Server 2008 R2, Windows Server 2012 y Windows Server 2012 R2 tienen requisitos previos diferentes, así que seleccione el procedimiento adecuado a continuación para instalar los que sean correctos para su sistema operativo.

**En Windows Server 2008 R2**

1.  Instale el siguiente software:
    
      - [Windows Server 2008 R2 Service Pack 1](http://www.microsoft.com/es-es/download/details.aspx?id=5842)
    
      - [.NET Framework 4.5](https://go.microsoft.com/fwlink/p/?linkid=256560)
    
      - [Windows PowerShell 3.0](https://go.microsoft.com/fwlink/p/?linkid=244693)
    
      - [Actualización de la plataforma para Windows 7 SP1 y Windows Server 2008 R2 SP1 (KB2670838)](https://support.microsoft.com/kb/2670838/es)

2.  Abra el símbolo del sistema de Windows PowerShell como administrador y ejecute estos comandos para instalar los roles y servicios necesarios.
    
    ```PowerShell
        Import-Module ServerManager
    ```

    A continuación, ejecute este comando:
    
    ```PowerShell
        Add-WindowsFeature Web-Server,Web-WebServer,Web-Common-Http,Web-Static-Content,Web-App-Dev,Web-Asp-Net,Web-Net-Ext,Web-ISAPI-Ext,Web-ISAPI-Filter,Web-Includes,Web-Security,Web-Windows-Auth,Web-Filtering,Web-Stat-Compression,Web-Dyn-Compression,Web-Mgmt-Console,Ink-Handwriting,IH-Ink-Support,NET-Framework,NET-Framework-Core,NET-HTTP-Activation,NET-Non-HTTP-Activ,NET-Win-CFAC
    ```

    Si se le solicita, reinicie el servidor.

**En Windows Server 2012**

1.  Abra el símbolo del sistema de Windows PowerShell como administrador y ejecute este comando para instalar los roles y servicios necesarios.
    
    ```PowerShell
        Add-WindowsFeature Web-Server,Web-Mgmt-Tools,Web-Mgmt-Console,Web-WebServer,Web-Common-Http,Web-Default-Doc,Web-Static-Content,Web-Performance,Web-Stat-Compression,Web-Dyn-Compression,Web-Security,Web-Filtering,Web-Windows-Auth,Web-App-Dev,Web-Net-Ext45,Web-Asp-Net45,Web-ISAPI-Ext,Web-ISAPI-Filter,Web-Includes,InkandHandwritingServices,NET-Framework-Features,NET-Framework-Core,NET-HTTP-Activation,NET-Non-HTTP-Activ,NET-WCF-HTTP-Activation45
    ```

    Si se le solicita, reinicie el servidor.

**En Windows Server 2012 R2**

1.  Instale el siguiente software:
    
      - [.NET Framework 4.5.2](https://go.microsoft.com/fwlink/p/?linkid=510096)

2.  Abra el símbolo del sistema de Windows PowerShell como administrador y ejecute este comando para instalar los roles y servicios necesarios.
    
    ```PowerShell
        Add-WindowsFeature Web-Server,Web-Mgmt-Tools,Web-Mgmt-Console,Web-WebServer,Web-Common-Http,Web-Default-Doc,Web-Static-Content,Web-Performance,Web-Stat-Compression,Web-Dyn-Compression,Web-Security,Web-Filtering,Web-Windows-Auth,Web-App-Dev,Web-Net-Ext45,Web-Asp-Net45,Web-ISAPI-Ext,Web-ISAPI-Filter,Web-Includes,InkandHandwritingServices,NET-Framework-Features,NET-Framework-Core,NET-HTTP-Activation,NET-Non-HTTP-Activ,NET-WCF-HTTP-Activation45
    ```

    Si se le solicita, reinicie el servidor.

## Paso 2: instalar Office Web Apps Server y las actualizaciones relacionadas

Complete los siguientes pasos en todos los servidores que ejecutarán Office Web Apps Server.

1.  Descargue Office Web Apps Server desde el [Centro de servicios de licencias por volumen (VLSC)](https://go.microsoft.com/fwlink/p/?linkid=256561). Para descargar Office Web Apps Server, debe tener una licencia, según un acuerdo de licencias por volumen, para Office Professional Plus 2013, Office Standard 2013 u Office para Mac 2011. La descarga se ubica dentro de los productos de Office en el portal de VLSC.

2.  Realice una de las acciones siguientes:
    
      - En Windows Server 2012 o Windows Server 2012 R2, abra directamente el archivo .img y ejecute **Setup.exe**.
    
      - Para Windows Server 2008 R2 SP1, use un programa que pueda montar o extraer archivos .img y ejecute **Setup.exe**.

3.  En la página **Términos de licencia para software de Microsoft**, seleccione **Acepto los términos del contrato** y haga clic en **Continuar**.

4.  En la página **Elija una ubicación de archivos**, seleccione la carpeta donde desea instalar los archivos de Office Web Apps Server (por ejemplo, C:\\Archivos de programa\\Microsoft Office Web Apps) y la opción **Instalar ahora**. Si la carpeta especificada no existe, el programa de instalación la creará automáticamente.
    
    Le recomendamos que instale Office Web Apps Server en la unidad del sistema.

5.  Cuando el programa de instalación complete la instalación de Office Web Apps Server, elija **Cerrar**.

6.  Descargue e instale [Office Web Apps Server SP1](https://go.microsoft.com/fwlink/p/?linkid=510097) (Recomendado para Windows Server 2012 y Windows Server 2008 R2 SP1. Obligatorio para Windows Server 2012 R2.)
    

    > [!NOTE]  
    > Si aplica Office Web Apps Server SP1 en un momento posterior, siga las instrucciones de <A href="apply-software-updates-to-office-web-apps-server.md">Aplicar actualizaciones de software a Office Web Apps Server</A>.



7.  Compruebe si hay actualizaciones más recientes de Office Web Apps Server consultando la lista del [centro de actualizaciones de TechNet para Office, los servidores de Office y otros productos relacionados](https://go.microsoft.com/fwlink/p/?linkid=280271).
    

    > [!NOTE]  
    > Si no ha instalado Office Web Apps Server SP1, aplique <A href="https://go.microsoft.com/fwlink/p/?linkid=296579">KB2810007</A>.



## Paso 3: instalar los paquetes de idioma para Office Web Apps Server

Los paquetes de idioma de Office Web Apps Server 2013 permiten a los usuarios ver archivos de Office basados en web en varios idiomas cuando se abren desde bibliotecas de documentos de SharePoint 2013, Outlook Web Access (como vistas previas de datos adjuntos) y Lync 2013 (como difusiones de PowerPoint). Para más información sobre cómo funcionan los paquetes de idioma, vea el tema sobre la [planeación de paquetes de idioma para Office Web Apps Server](plan-office-web-apps-server.md).

Para instalar los paquetes de idioma, siga estos pasos.


1.  Descargue los paquetes de idioma de Office Web Apps Server desde el [Centro de descarga de Microsoft](https://www.microsoft.com/es-es/download/details.aspx?id=35490).

2.  Ejecute **WebAppsServerLP\_en-us\_x64.exe**.

3.  En el asistente para los paquetes de idioma de Office Web Apps Server 2013, en la página **Términos de licencia para software de Microsoft**, seleccione **Acepto los términos del contrato** y luego **Continuar**.

4.  Cuando el programa de instalación complete la instalación de Office Web Apps Server, elija **Cerrar**.

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><img src="images/JJ219448.important(Office.15).gif" title="Importante" alt="Importante" /><strong>Importante:</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><ul>
<li><p>Para instalar los paquetes de idioma después de crear la granja de servidores de Office Web Apps Server, debe quitar un servidor de la granja, instalar en él el paquete de idioma y agregarlo de nuevo a la granja.</p></li>
<li><p>Para que un paquete de idioma funcione correctamente, deberá instalarlo en todos los servidores de la granja de servidores.</p></li>
</ul></td>
</tr>
</tbody>
</table>


## Implementar la granja de servidores de Office Web Apps Server

Siga los procedimientos de una de las tres secciones siguientes, en función del tipo de granja de Office Web Apps Server que desea crear.

<table>
<thead>
<tr class="header">
<th><img src="images/JJ219455.tip(Office.15).gif" title="Sugerencia" alt="Sugerencia" /><strong>Sugerencia:</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Si Windows PowerShell no reconoce el cmdlet <strong>New-OfficeWebAppsFarm</strong> al ejecutarlo, puede que tenga que importar el módulo <strong>OfficeWebApps</strong>. Use este comando:<br />
<code>Import-Module -Name OfficeWebApps</code></td>
</tr>
</tbody>
</table>


## Implementar una granja de un solo servidor de Office Web Apps Server que usa HTTP

Si solo implementa Office Web Apps Server para uso interno o para pruebas y no necesita proporcionar las funciones de Office Web Apps Server para Lync Server 2013, este es el procedimiento correcto. En este caso, instalará una granja de un solo servidor de Office Web Apps Server que usa HTTP. Aunque no necesitará un certificado ni un equilibrador de carga, sí será necesaria una instancia de máquina virtual o de servidor físico dedicado que no ejecute ninguna otra aplicación de servidor.

Puede usar esta granja de Office Web Apps Server para proporcionar las funciones de Office Web Apps para SharePoint 2013.

**Figura: los pasos para implementar Office Web Apps Server**

![Los tres pasos principales para implementar una granja de Office Web Apps Server de un solo servidor.](images/JJ219455.de5b3ed2-d7a7-489e-9de2-f3f068ebe836(Office.15).gif "Los tres pasos principales para implementar una granja de Office Web Apps Server de un solo servidor.")

## Paso 1: crear la granja de Office Web Apps Server

Use el comando **New-OfficeWebAppsFarm** para crear una nueva granja de servidores de Office Web Apps Server que conste de un solo servidor, como se muestra en el ejemplo siguiente.

```PowerShell
    New-OfficeWebAppsFarm -InternalURL "http://servername" -AllowHttp -EditingEnabled
```

**Parámetros**

  - **–InternalURL** es el nombre del servidor que ejecuta Office Web Apps Server, como **http://nombredelservidor**.

  - **–AllowHttp** configura la granja para que use HTTP.

  - **–EditingEnabled** habilita la edición en Office Web Apps cuando se usa con SharePoint 2013. Este parámetro no se usa en Lync Server 2013 porque dicho host no admite la edición.

Los parámetros adicionales para configurar servicios de traducción, servidores proxy, compatibilidad con imágenes prediseñadas y visores en línea se describen en [New-OfficeWebAppsFarm](https://docs.microsoft.com/en-us/powershell/module/officewebapps/new-officewebappsfarm?view=officewebapps-ps).

Si ve los mensajes “500 excepciones de servicio web” o “500.21: error interno del servidor”

## Paso 2: comprobar que la granja de servidores de Office Web Apps Server se ha creado correctamente

Una vez creada la granja de servidores, los detalles correspondientes aparecen en el símbolo del sistema de Windows PowerShell. Para comprobar que Office Web Apps Server se encuentra instalado y configurado correctamente, acceda a la dirección URL de descubrimiento de Office Web Apps Server con un explorador web, tal como se muestra en el ejemplo siguiente. La dirección URL de descubrimiento es el parámetro *InternalUrl* que especificó al configurar la granja de Office Web Apps Server, seguido de **/hosting/discovery**, por ejemplo:

    http://servername/hosting/discovery

Si Office Web Apps Server funciona según lo previsto, debería ver un archivo XML de detección del protocolo de Interfaz de plataforma abierta de aplicación web (WOPI) en el explorador web. Las primeras líneas del archivo deberían ser similares a las del siguiente ejemplo.

```XML
    <?xml version="1.0" encoding="utf-8" ?> 
    - <wopi-discovery>
    - <net-zone name="internal-http">
    - <app name="Excel" favIconUrl="http://servername/x/_layouts/images/FavIcon_Excel.ico" checkLicense="true">
    <action name="view" ext="ods" default="true" urlsrc="http://servername/x/_layouts/xlviewerinternal.aspx?<ui=UI_LLCC&><rs=DC_LLCC&>" /> 
    <action name="view" ext="xls" default="true" urlsrc="http://servername/x/_layouts/xlviewerinternal.aspx?<ui=UI_LLCC&><rs=DC_LLCC&>" /> 
    <action name="view" ext="xlsb" default="true" urlsrc="http://servername/x/_layouts/xlviewerinternal.aspx?<ui=UI_LLCC&><rs=DC_LLCC&>" /> 
    <action name="view" ext="xlsm" default="true" urlsrc="http://servername/x/_layouts/xlviewerinternal.aspx?<ui=UI_LLCC&><rs=DC_LLCC&>" /> 
```    

## Paso 3: configurar el host

La granja ya está lista para proporcionar funcionalidad de Office Web Apps a hosts en HTTP. Visite [Configurar Office Web Apps para SharePoint 2013](configure-office-web-apps-for-sharepoint-2013.md) para obtener más información sobre cómo configurar hosts.

## Implementar una granja de un solo servidor de Office Web Apps Server que usa HTTPS
<a name="singlehttps"> </a>

Para la mayoría de los entornos de producción, se recomienda el uso de HTTPS para sus características de seguridad. Además, HTTPS es necesario si quiere proporcionar las funciones de Office Web Apps Server para Lync Server 2013, que permiten a los usuarios ver difusiones de PowerPoint en un explorador. Aquí se muestra cómo instalar una granja de un solo servidor de Office Web Apps Server que usa HTTPS. Deberá instalar un certificado en el servidor, tal como se describe en el tema sobre la [protección de comunicaciones de Office Web Apps Server mediante HTTPS](plan-office-web-apps-server.md).

Esta granja de servidores de Office Web Apps Server proporcionará las funciones de Office Web Apps para SharePoint 2013 y Lync Server 2013.

**Figura: los pasos para implementar Office Web Apps Server**

![Los tres pasos principales para implementar una granja de Office Web Apps Server de un solo servidor.](images/JJ219455.de5b3ed2-d7a7-489e-9de2-f3f068ebe836(Office.15).gif "Los tres pasos principales para implementar una granja de Office Web Apps Server de un solo servidor.")

## Paso 1: crear la granja de Office Web Apps Server

Use el comando **New-OfficeWebAppsFarm** para crear una nueva granja de servidores de Office Web Apps Server que conste de un solo servidor, como se muestra en el ejemplo siguiente.

```PowerShell
    New-OfficeWebAppsFarm -InternalUrl "https://server.contoso.com" -ExternalUrl "https://wacweb01.contoso.com" -CertificateName "OfficeWebApps Certificate" -EditingEnabled
```

**Parámetros**

  - **–InternalURL** es el nombre de dominio completo (FQDN) del servidor que ejecuta Office Web Apps Server, como **http://nombredelservidor.contoso.com**.

  - **–ExternalURL** es el FQDN al que se puede acceder en Internet.

  - **–CertificateName** es el nombre descriptivo del certificado.

  - **–EditingEnabled** es opcional y habilita la edición en Office Web Apps cuando se usa con SharePoint 2013. Este parámetro no se usa en Lync Server 2013 porque dicho host no admite la edición.

Los parámetros adicionales para configurar servicios de traducción, servidores proxy, compatibilidad con imágenes prediseñadas y visores en línea se describen en [New-OfficeWebAppsFarm](https://docs.microsoft.com/en-us/powershell/module/officewebapps/new-officewebappsfarm?view=officewebapps-ps).

Si ve los mensajes “500 excepciones de servicio web” o “500.21: error interno del servidor”

## Paso 2: comprobar que la granja de servidores de Office Web Apps Server se ha creado correctamente

Una vez creada la granja de servidores, los detalles correspondientes aparecen en el símbolo del sistema de Windows PowerShell. Para comprobar que Office Web Apps Server se encuentra instalado y configurado correctamente, acceda a la dirección URL de descubrimiento de Office Web Apps Server con un explorador web, tal como se muestra en el ejemplo siguiente. La dirección URL de descubrimiento es el parámetro *InternalUrl* que especificó al configurar la granja de Office Web Apps Server, seguido de **/hosting/discovery**, por ejemplo:

    https://server.contoso.com/hosting/discovery

Si Office Web Apps Server funciona según lo previsto, debería ver un archivo XML de detección del protocolo de Interfaz de plataforma abierta de aplicación web (WOPI) en el explorador web. Las primeras líneas del archivo deberían ser similares a las del siguiente ejemplo:

```XML
<?xml version="1.0" encoding="UTF-8"?>
<wopi-discovery><net-zone 
name="internal-https"><app name="Excel" checkLicense="true" 
favIconUrl="https://wac.contoso.com/x/_layouts/images/FavIcon_Excel.ico"><action 
name="view" 
urlsrc="https://wac.contoso.com/x/_layouts/xlviewerinternal.aspx?<ui=UI_LLCC&><rs=DC_LLCC&>" 
default="true" ext="ods"/><action name="view" 
urlsrc="https://wac.contoso.com/x/_layouts/xlviewerinternal.aspx?<ui=UI_LLCC&><rs=DC_LLCC&>" 
default="true" ext="xls"/><action name="view"
 
```


> [!NOTE]  
> En función de la configuración de seguridad del explorador web, puede que vea un mensaje que le indica que seleccione <STRONG>Mostrar todo el contenido</STRONG> antes de que se muestre el contenido del archivo XML de detección.



## Paso 3: configurar el host

La granja ya está lista para proporcionar las funciones de Office Web Apps a hosts en HTTPS. Visite los siguientes artículos para más información sobre cómo configurar hosts.

  - [Configurar Office Web Apps para SharePoint 2013](configure-office-web-apps-for-sharepoint-2013.md)

  - [Implementación de Office Web Apps Server y Lync Server 2013](https://technet.microsoft.com/es-es/library/3370ab55-9949-4f32-b88b-5cffed6aaad8)

## Implementar una granja de varios servidores y de carga equilibrada de Office Web Apps Server que usa HTTPS
<a name="multihttps"> </a>
Si prevé que habrá mucho tráfico en la granja de servidores de Office Web Apps Server y desea estar disponible tanto en Internet como en la red interna, este tipo de topología es el indicado. Esta sección muestra cómo instalar una granja de varios servidores de Office Web Apps Server que usa un equilibrador de carga y HTTPS. Si le interesa, [obtenga más información sobre esta topología](plan-office-web-apps-server.md).

Antes de comenzar, asegúrese de que el equilibrador de carga está configurado como se describe en el tema sobre los [Load balancer requirements for Office Web Apps Server](plan-office-web-apps-server.md). Además, deberá instalar un certificado en el equilibrador de carga, tal como se describe en el tema sobre la [protección de comunicaciones de Office Web Apps Server mediante HTTPS](plan-office-web-apps-server.md). Esta granja de Office Web Apps Server proporcionará las funciones de Office Web Apps para SharePoint 2013 y Lync Server 2013.

**Figura: los pasos para implementar Office Web Apps Server**

![Los cuatro pasos principales para implementar una granja de Office Web Apps Server de varios servidores.](images/JJ219455.4c4b31cb-961b-4efd-b755-a18bdcb5c191(Office.15).gif "Los cuatro pasos principales para implementar una granja de Office Web Apps Server de varios servidores.")

## Paso 1: crear la granja de Office Web Apps Server en el primer servidor

Use el comando **New-OfficeWebAppsFarm** para crear una nueva granja de servidores de Office Web Apps Server en el primer servidor, tal como se muestra en el ejemplo siguiente.

```PowerShell
    New-OfficeWebAppsFarm -InternalUrl "https://server.contoso.com" -ExternalUrl "https://wacweb01.contoso.com" -SSLOffloaded -EditingEnabled
```

**Parámetros**

  - **–InternalURL** es el nombre de dominio completo (FQDN) del servidor que ejecuta Office Web Apps Server, como **http://nombredelservidor.contoso.com**.

  - **–ExternalURL** es el FQDN al que se puede acceder en Internet.

  - **-SSLOffloaded** permite la descarga de terminación SSL en el equilibrador de carga.

  - **–EditingEnabled** es opcional y habilita la edición en Office Web Apps cuando se usa con SharePoint 2013. Este parámetro no se usa en Lync Server 2013 porque dicho host no admite la edición.

Otros parámetros para configurar servicios de traducción, servidores proxy, compatibilidad con imágenes prediseñadas y visores en línea se describen en [New-OfficeWebAppsFarm](https://docs.microsoft.com/en-us/powershell/module/officewebapps/new-officewebappsfarm?view=officewebapps-ps).

Si ve los mensajes “500 excepciones de servicio web” o “500.21: error interno del servidor”

## Paso 2: agregar más servidores a la granja

Una vez que el primer servidor ejecuta Office Web Apps Server, ejecute el comando **New-OfficeWebAppsMachine** en cada servidor que quiera agregar a la granja de Office Web Apps Server. Para el parámetro **–MachineToJoin**, use el nombre de equipo de un servidor que ya esté en la granja de Office Web Apps Server. Por ejemplo, si server1.contoso.com ya está en la granja, use lo siguiente:

```PowerShell
    New-OfficeWebAppsMachine -MachineToJoin "server1.contoso.com"
```

¿Desea más información sobre estos parámetros? Puede encontrarlos en [New-OfficeWebAppsMachine](https://docs.microsoft.com/en-us/powershell/module/officewebapps/new-officewebappsmachine?view=officewebapps-ps).

## Paso 3: comprobar que la granja de servidores de Office Web Apps Server se ha creado correctamente

Una vez creada la granja de servidores, los detalles correspondientes aparecen en el símbolo del sistema de Windows PowerShell. Para comprobar que Office Web Apps Server se encuentra instalado y configurado correctamente, acceda a la dirección URL de descubrimiento de Office Web Apps Server con un explorador web, tal como se muestra en el ejemplo siguiente. La dirección URL de descubrimiento es el parámetro *InternalUrl* que especificó al configurar granja de Office Web Apps Server, seguido de **/hosting/discovery**. Por ejemplo:

    https://server.contoso.com/hosting/discovery

Si Office Web Apps Server funciona según lo previsto, debería ver un archivo XML de detección del protocolo de Interfaz de plataforma abierta de aplicación web (WOPI) en el explorador web. Las primeras líneas del archivo deberían ser similares a las del siguiente ejemplo:

```XML
    <?xml version="1.0" encoding="UTF-8"?>
    <wopi-discovery><net-zone name="internal-https"><app name="Excel" checkLicense="true" favIconUrl="https://officewebapps.contoso.com/x/_layouts/images/FavIcon_Excel.ico"><action name="view" urlsrc="https://officewebapps.contoso.com/x/_layouts/xlviewerinternal.aspx?<ui=UI_LLCC&><rs=DC_LLCC&>" default="true" ext="ods"/><action name="view" urlsrc="https://officewebapps.contoso.com/x/_layouts/xlviewerinternal.aspx?<ui=UI_LLCC&><rs=DC_LLCC&>" default="true" ext="xls"/><action name="view" urlsrc="https://officewebapps.contoso.com/x/_layouts/xlviewerinternal.aspx?<ui=UI_LLCC&><rs=DC_LLCC&>" default="true" ext="xlsb"/> 
```

> [!NOTE]  
> En función de la configuración de seguridad del explorador web, puede que vea un mensaje que le indica que seleccione <STRONG>Mostrar todo el contenido</STRONG> antes de que se muestre el contenido del archivo XML de detección.



## Paso 4: configurar el host

La granja ya está lista para proporcionar las funciones de Office Web Apps a hosts en HTTPS. Visite los siguientes artículos para más información sobre cómo configurar hosts.

  - [Configurar Office Web Apps para SharePoint 2013](configure-office-web-apps-for-sharepoint-2013.md)

  - [Implementación de Office Web Apps Server y Lync Server 2013](https://technet.microsoft.com/es-es/library/3370ab55-9949-4f32-b88b-5cffed6aaad8)

## Si ve los mensajes “500 excepciones de servicio web” o “500.21: error interno del servidor”

Si las características de .NET Framework 3.5 se instalaron y posteriormente se quitaron, al ejecutar los cmdlets OfficeWebApps, pueden aparecer los mensajes “500 excepciones de servicio web” o “500.21: error interno del servidor”. Para corregir este problema, ejecute los siguientes comandos de muestra desde un símbolo del sistema con privilegios elevados. Así borrará la configuración que puede estar impidiendo que Office Web Apps Server funcione correctamente:

**Para Windows Server 2008 R2**

```PowerShell
    %systemroot%\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe -iru
```
```PowerShell
    iisreset /restart /noforce
```

**Para Windows Server 2012 o Windows Server 2012 R2**

```PowerShell
    dism /online /enable-feature /featurename:IIS-ASPNET45
```

## Consulte también


[New-OfficeWebAppsFarm](https://docs.microsoft.com/en-us/powershell/module/officewebapps/new-officewebappsfarm?view=officewebapps-ps)  
[New-OfficeWebAppsMachine](https://docs.microsoft.com/en-us/powershell/module/officewebapps/new-officewebappsmachine?view=officewebapps-ps)  


[Guía básica de contenido de Office Web Apps Server](content-roadmap-for-office-web-apps-server.md)  
[Planear Office Web Apps Server](plan-office-web-apps-server.md)  
[Configurar Office Web Apps para SharePoint 2013](configure-office-web-apps-for-sharepoint-2013.md)  


[Implementación de Office Web Apps Server y Lync Server 2013](https://go.microsoft.com/fwlink/p/?linkid=256902)  
  

[](configure-office-web-apps-for-sharepoint-2013.md)

