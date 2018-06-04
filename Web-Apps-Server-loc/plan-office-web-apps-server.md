---
title: Planear Office Web Apps Server
TOCTitle: Planear Office Web Apps Server
ms:assetid: 2e147f11-6f47-46bc-90bf-b2f179958d11
ms:mtpsurl: https://technet.microsoft.com/es-es/library/JJ219435(v=office.15)
ms:contentKeyID: 48793520
ms.date: 02/08/2018
mtps_version: v=office.15
ms.translationtype: MT
---

# Planear Office Web Apps Server

 

_**Se aplica a:**Office Web Apps Server_

_**Última modificación del tema:**2017-10-10_

**Resumen:** describe los requisitos y requisitos previos de Office Web Apps Server, como HTTPS, certificados, virtualización, equilibrio de carga, topologías y seguridad.

**Audiencia:** profesionales de TI

Office Web Apps Server proporciona versiones basadas en el explorador de aplicaciones de Office en un entorno local, lo que da a los usuarios más oportunidades de colaboración y flexibilidad. En este artículo se describen los requisitos y pasos que necesita seguir para instalar Office Web Apps Server en la organización.

Es importante planear cuidadosamente para que todos los hosts, como SharePoint 2013 y Lync Server 2013, pueden comunicarse con el Office Web Apps Server. Para obtener orientación adicional acerca de cómo configurar hosts, consulte los siguientes recursos:

  - [Planificar Office Web Apps (cuando se usa con SharePoint 2013)](plan-office-web-apps-used-with-sharepoint-2013.md)

  - [Implementación de Office Web Apps Server y Lync Server 2013](https://technet.microsoft.com/es-es/library/3370ab55-9949-4f32-b88b-5cffed6aaad8)


> [!NOTE]
> Productos de SharePoint 2010 no puede ser un host para Office Web Apps Server. Office Web Apps Server no es compatible con SharePoint Foundation 2010 o SharePoint Server 2010. Office Web Apps Server también no es compatible con Exchange Server 2013.



En este artículo:

  - Requisitos de software, hardware y configuración para Office Web Apps Server

  - Compatibilidad con virtualización de Office Web Apps Server

  - Requisitos de firewall para Office Web Apps Server

  - Requisitos del equilibrador de carga para Office Web Apps Server

  - Requisitos de DNS para Office Web Apps Server

  - Planeación de paquetes de idioma para Office Web Apps Server

  - Planeación de topología para Office Web Apps Server

  - Planeación de seguridad para Office Web Apps Server

  - Planeación de Visores en línea con Office Web Apps Server

  - Planeación de actualizaciones para Office Web Apps Server

## Requisitos de software, hardware y configuración para Office Web Apps Server

Puede instalar Office Web Apps Server como una granja de servidores de Office Web Apps Server de un solo servidor o como una granja de servidores de Office Web Apps Server de varios servidores y de carga equilibrada. Puede usar servidores físicos o instancias de máquina virtual, pero no puede instalar otras aplicaciones de servidor (como SharePoint 2013 o SQL Server) en el mismo servidor que Office Web Apps Server.

En entornos que contienen datos de usuario reales, siempre recomendamos que use HTTPS, para lo cual deberá obtener un certificado. Si está usando varios servidores en su granja de servidores, deberá configurar una solución de equilibrio de carga. Puede obtener más información sobre estos escenarios en las siguientes secciones.

## Requisitos de hardware para Office Web Apps Server

Office Web Apps Server usa los mismos requisitos mínimos de hardware que SharePoint Server 2013. Puede encontrar el conjunto completo de requisitos de SharePoint 2013 en [Hardware requirements—web servers, application servers, and single server installations](https://technet.microsoft.com/es-es/4d88c402-24f2-449b-86a6-6e7afcfec0cd\(office.15\)#hwforwebserver).

## Sistemas operativos compatibles con Office Web Apps Server

Puede ejecutar Office Web Apps Server en los siguientes sistemas operativos:

  - La edición de 64 bits de Windows Server 2008 R2 Service Pack 1 (SP1) estándar, Enterprise o Datacenter con la [Edición de la actualización para Windows Server 2008 R2 x64](https://go.microsoft.com/fwlink/p/?linkid=236954) instalado

  - La edición de 64 bits de Windows Server 2012 Standard o Datacenter

  - La edición de 64 bits de Windows Server 2012 R2. Para usar este sistema operativo, debe usar Office Web Apps Server con Service Pack 1 (SP1).

## Requisitos de dominio para Office Web Apps Server

Todos los servidores de la granja de servidores de Office Web Apps Server deben pertenecer a un dominio. Pueden estar en el mismo dominio (procedimiento recomendado) o en dominios del mismo bosque. Sin embargo, Office Web Apps Server no funcionará si intenta instalarlo en un controlador de dominio.

## Roles de servidor, servicios y otro software necesarios para Office Web Apps Server

En primer lugar, estas son algunas cosas que NO debe hacer al implementar Office Web Apps Server.

  - **No instale ninguna otra aplicación de servidor en el servidor que ejecuta Office Web Apps Server**. Esto incluye Exchange Server, SharePoint Server, Lync Server y SQL Server. Si tiene escasez de servidores, considere ejecutar Office Web Apps Server en una instancia de máquina virtual de uno de los servidores que tiene.

  - **No instale ningún servicio ni rol que dependa del rol de servidor web (IIS) en el puerto 80, 443 o 809** porque Office Web Apps Server quita aplicaciones web periódicamente en estos puertos.

  - **No instale ninguna versión de Office**. Si ya está instalada, tendrá que desinstalarla antes de instalar Office Web Apps Server.

  - **No instale Office Web Apps Server en un controlador de dominio**. No funcionará en un servidor con Servicios de dominio de Active Directory (AD DS).

Ahora para los elementos que SÍ tiene que instalar, consulte la siguiente tabla para obtener información.

<table>
<thead>
<tr class="header">
<th><img src="images/JJ219448.important(Office.15).gif" title="Importante" alt="Importante" /> <strong>Importante:</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>sólo está disponible para su descarga desde el <a href="https://go.microsoft.com/fwlink/p/?linkid=256561">Centro de servicio de licencias de volumen (VLSC)</a>Office Web Apps Server. Para descargar Office Web Apps Server debe tener una licencia, bajo un contrato de licencias por volumen, Office Professional Plus 2013, Office Standard 2013 o Office para Mac 2011. La descarga se encuentra en los productos de Office en el portal VLSC.</td>
</tr>
</tbody>
</table>


### Descargas, roles de servidor y características necesarios para Office Web Apps Server

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Descarga, rol de servidor o característica</th>
<th>Si va a instalar en Windows Server 2008 R2</th>
<th>Si va a instalar en Windows Server 2012</th>
<th>Si va a instalar en Windows Server 2012 R2</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Descarga:</strong> Office Web Apps Server</p></td>
<td><p><a href="https://go.microsoft.com/fwlink/p/?linkid=256561">Servidor de Office Web Apps</a></p></td>
<td><p><a href="https://go.microsoft.com/fwlink/p/?linkid=256561">Servidor de Office Web Apps</a></p></td>
<td><p><a href="https://go.microsoft.com/fwlink/p/?linkid=256561">Servidor de Office Web Apps</a></p></td>
</tr>
<tr class="even">
<td><p><strong>Descargar:</strong> Office Web Apps Server SP1</p></td>
<td><p>Recomendado</p></td>
<td><p>Recomendado</p></td>
<td><p><a href="https://go.microsoft.com/fwlink/p/?linkid=510097">Office Web Apps Server SP1</a></p></td>
</tr>
<tr class="odd">
<td><p><strong>Descargar:</strong> la versión correcta de .NET Framework</p></td>
<td><p><a href="https://go.microsoft.com/fwlink/p/?linkid=256560">.NET Framework 4.5</a></p></td>
<td><p>.NET Framework 4.5 ya está instalado</p></td>
<td><p><a href="https://go.microsoft.com/fwlink/p/?linkid=510096">.NET Framework 4.5.2</a></p></td>
</tr>
<tr class="even">
<td><p><strong>Descargar:</strong> actualización para Windows Server 2008 R2 x64 Edition</p></td>
<td><p><a href="https://go.microsoft.com/fwlink/p/?linkid=236954">Actualización para Windows Server 2008 R2 x64 Edition</a></p></td>
<td><p>No procede</p></td>
<td><p>No aplicable</p></td>
</tr>
<tr class="odd">
<td><p><strong>Descarga:</strong> Windows PowerShell 3.0</p></td>
<td><p><a href="https://go.microsoft.com/fwlink/p/?linkid=244693">Windows PowerShell 3.0</a></p></td>
<td><p>Ya instalado</p></td>
<td><p>Ya instalado</p></td>
</tr>
<tr class="even">
<td><p><strong>Rol de servidor:</strong> Servidor web (IIS)</p></td>
<td><p>Estos son los servicios de rol mínimos necesarios para el rol de servidor <strong>Servidor web (IIS)</strong>.</p>
<p><strong>Características comunes de HTTP</strong></p>
<ul>
<li><p>Contenido estático</p></li>
<li><p>Documento predeterminado</p></li>
</ul>
<p><strong>Desarrollo de aplicaciones</strong></p>
<ul>
<li><p>ASP.NET</p></li>
<li><p>Extensibilidad de .NET</p></li>
<li><p>Extensiones ISAPI</p></li>
<li><p>Filtros ISAPI</p></li>
<li><p>Inclusiones del servidor</p></li>
</ul>
<p><strong>Seguridad</strong></p>
<ul>
<li><p>Autenticación de Windows</p></li>
<li><p>Filtrado de solicitudes</p></li>
</ul>
<p><strong>Herramientas de administración</strong></p>
<ul>
<li><p>Consola de administración IIS</p></li>
</ul>
<p>Las siguientes opciones son recomendables pero no obligatorias:</p>
<p><strong>Rendimiento</strong></p>
<ul>
<li><p>Compresión de contenido estático</p></li>
<li><p>Compresión de contenido dinámico</p></li>
</ul></td>
<td><p>Estos son los servicios de rol mínimos necesarios para el rol de servidor <strong>Servidor web (IIS)</strong>.</p>
<p><strong>Herramientas de administración</strong></p>
<ul>
<li><p>Consola de administración IIS</p></li>
</ul>
<p><strong>Servidor web</strong></p>
<ul>
<li><p>Características comunes de HTTP</p></li>
<li><p>Documento predeterminado</p></li>
<li><p>Contenido estático</p></li>
</ul>
<p><strong>Seguridad</strong></p>
<ul>
<li><p>Filtrado de solicitudes</p></li>
<li><p>Autenticación de Windows</p></li>
</ul>
<p><strong>Desarrollo de aplicaciones</strong></p>
<ul>
<li><p>Extensibilidad de .NET 4.5</p></li>
<li><p>ASP.NET 4.5</p></li>
<li><p>Extensiones ISAPI</p></li>
<li><p>Filtros ISAPI</p></li>
<li><p>Inclusiones del servidor</p></li>
</ul>
<p>Las siguientes opciones son recomendables pero no obligatorias:</p>
<p><strong>Rendimiento</strong></p>
<ul>
<li><p>Compresión de contenido estático</p></li>
<li><p>Compresión de contenido dinámico</p></li>
</ul></td>
<td><p>Estos son los servicios de rol mínimos necesarios para el rol de servidor <strong>Servidor web (IIS)</strong>.</p>
<p><strong>Herramientas de administración</strong></p>
<ul>
<li><p>Consola de administración IIS</p></li>
</ul>
<p><strong>Servidor web</strong></p>
<ul>
<li><p>Características comunes de HTTP</p></li>
<li><p>Documento predeterminado</p></li>
<li><p>Contenido estático</p></li>
</ul>
<p><strong>Seguridad</strong></p>
<ul>
<li><p>Filtrado de solicitudes</p></li>
<li><p>Autenticación de Windows</p></li>
</ul>
<p><strong>Desarrollo de aplicaciones</strong></p>
<ul>
<li><p>Extensibilidad de .NET 4.5</p></li>
<li><p>ASP.NET 4.5</p></li>
<li><p>Extensiones ISAPI</p></li>
<li><p>Filtros ISAPI</p></li>
<li><p>Inclusiones del servidor</p></li>
</ul>
<p>Las siguientes opciones son recomendables pero no obligatorias:</p>
<p><strong>Rendimiento</strong></p>
<ul>
<li><p>Compresión de contenido estático</p></li>
<li><p>Compresión de contenido dinámico</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p><strong>Característica:</strong> servicios de Escritura con lápiz y Escritura a mano</p></td>
<td><p><strong>Servicios de Escritura con lápiz y Escritura a mano</strong></p>
<ul>
<li><p>Compatibilidad con entrada de lápiz</p></li>
</ul></td>
<td><p><strong>Servicios de Escritura con lápiz y Escritura a mano</strong></p>
<ul>
<li><p>No se requiere soporte de tinta.</p></li>
</ul></td>
<td><p><strong>Servicios de Escritura con lápiz y Escritura a mano</strong></p>
<ul>
<li><p>No se requiere compatibilidad con entrada de lápiz.</p></li>
</ul></td>
</tr>
</tbody>
</table>


## Compatibilidad con virtualización de Office Web Apps Server

Office Web Apps Server es totalmente compatible cuando se implementa usando tecnología Windows ServerHyper-V. Si prevé virtualizar Office Web Apps Server, siga estas instrucciones:

  - Instale Office Web Apps Server en su propia instancia de máquina virtual. No instale ninguna otra aplicación de servidor, como SharePoint 2013, en esta instancia.

  - Está bien instalar Office Web Apps Server en una instancia de máquina virtual hospedada en un servidor que ejecuta SharePoint 2013.

  - Para granjas de varios servidores de Office Web Apps Server, cada instancia debe estar en un host de máquina virtual independiente. De este modo, la granja de servidores de Office Web Apps Server sigue estando disponible si se produce un error en uno de los hosts.

## Requisitos de firewall para Office Web Apps Server

Los firewalls pueden causar problemas que bloquean la comunicación entre el explorador web, los servidores que ejecutan Office Web Apps Server y los servidores que ejecutan SharePoint 2013. Estos problemas pueden ser más complicados cuando los servidores están en partes diferentes de una red.

Asegúrese de que los siguientes puertos no están bloqueados por firewalls en ninguno de los servidores que ejecuta Office Web Apps Server ni en el equilibrador de carga:

  - Puerto 443 para tráfico HTTPS

  - Puerto 80 para tráfico HTTP

  - Puerto 809 para tráfico privado entre los servidores que ejecutan Office Web Apps Server (si está configurando una granja de varios servidores)

## Requisitos del equilibrador de carga para Office Web Apps Server

Recomendamos una solución de equilibrio de carga al ejecutar Office Web Apps Server en dos o más servidores. Prácticamente cualquier solución de equilibrio de carga funcionará, incluido un servidor que ejecuta el rol Servidor web (IIS) ejecutando el Enrutamiento de solicitud de aplicaciones (ARR). De hecho, puede ejecutar ARR en uno de los servidores que ejecuta Office Web Apps Server. Si no tiene una solución de equilibrio de carga, eche un vistazo en los siguientes recursos para usar IIS con ARR:

  - [Enrutamiento de solicitud de instalación de aplicación](https://go.microsoft.com/fwlink/?linkid=236955)

  - [Aplicación solicitar ayuda de enrutamiento](https://go.microsoft.com/fwlink/?linkid=236956)

Idealmente, intente buscar una solución de equilibrio de carga que admita las siguientes características:

  - Enrutamiento de capa 7

  - Habilitar afinidad de cliente o afinidad de front-end

  - Habilitar la descarga SSL

Si usa un equilibrador de carga, tendrá que instalar el certificado en el equilibrador de carga como se describe en Asegurar comunicaciones de Office Web Apps Server mediante HTTPS.

## Requisitos de DNS para Office Web Apps Server

En entornos que usan HTTPS y equilibro de carga, debe actualizar DNS de modo que el nombre de dominio completo (FQDN) del certificado resuelva la dirección IP del servidor que ejecuta Office Web Apps Server o la dirección IP asignada al equilibrador de carga para la granja de servidores de Office Web Apps Server.

## Planeación de paquetes de idioma para Office Web Apps Server

Los paquetes de idioma de Office Web Apps Server 2013 permiten a los usuarios ver archivos de Office basados en web en varios idiomas desde bibliotecas de documentos de SharePoint 2013, Outlook Web App (como vistas previas de documentos adjuntos) y Lync 2013 ( como difusiones de PowerPoint). Sin embargo, esto depende de los idiomas que se configuren en el host. Para ver archivos de Office basados en web de hosts en varios idiomas, se debe cumplir lo siguiente:

  - El host (como SharePoint Server 2013 o Lync Server 2013 ) está configurado para ejecutar aplicaciones en otros idiomas. El proceso de instalación y configuración de paquetes de idioma en el host es independiente de la instalación de un paquete de idioma en la explotación Office Web Apps Server.

  - Los idiomas están instalados y disponibles en todos los servidores en la granja de servidores de Office Web Apps Server.

Aquí es donde [descargar los paquetes de idioma de Office Web Apps Server](https://go.microsoft.com/fwlink/p/?linkid=263945).

## Planeación de topología para Office Web Apps Server

Como mínimo, una topología Office Web Apps Server incluirá una máquina física o virtual ejecuta Office Web Apps Server y al menos un host (por ejemplo, un servidor que ejecute Lync Server 2013 o SharePoint 2013 ). Y por supuesto, necesitará un equipo cliente o dispositivo para conectarse a uno de los hosts y utilizar la funcionalidad de Office Web Apps. Desde dicha topología mínima, puede agregar más hosts y más servidores al conjunto de Office Web Apps Server según sea necesario para satisfacer las necesidades de su organización.

La siguiente es una lista de recomendaciones que de tener en cuenta a medida que la topología de Office Web Apps Server se vuelve más compleja.

  - **Planee redundancia.** Si usa instancias de máquina virtual, asegúrese de que las coloca en hosts de máquina virtual independientes por motivos de redundancia. Está bien si las demás instancias en el host ejecutan aplicaciones de servidor; simplemente no ejecute otras aplicaciones de servidor en la misma instancia que Office Web Apps Server.

  - **Quédese con un solo centro de datos.** Los servidores en una granja de servidores de Office Web Apps Server deben estar en el mismo centro de datos. No los distribuya geográficamente. Por lo general, necesita una sola granja de servidores, a menos que tenga necesidades de seguridad que requieran una red aislada que tenga su propia granja de servidores de Office Web Apps Server.

  - **Cuanto más próximos estén los hosts, mejor.** La granja de servidores de Office Web Apps Server no tiene que estar en el mismo centro de datos que los hosts a los que sirve, pero para un uso denso de edición, se recomienda colocar la granja de servidores de Office Web Apps Server tan próxima a los hosts como sea posible. Esto es menos importante para las organizaciones que usan Office Web Apps principalmente para ver archivos de Office.

  - **Planee las conexiones.** Conecte todos los servidores en la granja de servidores de Office Web Apps Server solamente entre ellos. Para conectarlos a una red más amplia, hágalo a través de un firewall de equilibrador de carga de proxy inverso.

  - **Configure el firewall para solicitudes HTTP o HTTPS.** Asegúrese de que el firewall permite a los servidores que ejecutan Office Web Apps Server iniciar solicitudes HTTP o HTTPS en los hosts.

  - **Planee comunicaciones entrantes y salientes.** En una implementación con conexión a Internet, enrute todas las comunicaciones salientes a través de un dispositivo NAT. En una granja multiservidor, controle todas las comunicaciones entrantes con un equilibrador de carga.

  - **Asegúrese de que todos los servidores de la granja de servidores de Office Web Apps Server estén unidos a un dominio y formen parte de la misma unidad organizativa (OU).** Use el parámetro **FarmOU** en el cmdlet [New-OfficeWebAppsFarm](new-officewebappsfarm.md) para impedir que otros servidores que no están en esta OU se unan a la granja de servidores.

  - **Use el protocolo HTTPS para todas las solicitudes entrantes.**

  - **Si tiene IPsec implementado en la red, úselo para cifrar el tráfico entre los servidores.**

  - **Planee las características de Office que usan Internet.** Si se necesitan características tales como imágenes prediseñadas y servicios de traducción, y los servidores de la granja no pueden iniciar solicitudes en Internet, se debe configurar un servidor proxy para la granja de servidores de Office Web Apps Server. Esto permitirá las solicitudes HTTP en los sitios externos.

## Planeación de seguridad para Office Web Apps Server

La siguiente información incluye instrucciones de seguridad para Office Web Apps Server.

## Asegurar comunicaciones de Office Web Apps Server mediante HTTPS

Office Web Apps Server puede comunicarse con SharePoint 2013 y Lync Server 2013 mediante el protocolo HTTPS. En entornos de producción, se recomienda encarecidamente que utilice HTTPS. Tendrá que instalar un certificado de servidor de Internet que se puede asignar al servidor que ejecuta Office Web Apps Server (si está utilizando un único servidor) o al equilibrador de carga (si está utilizando varios servidores que ejecutan Office Web Apps Server ).

En entornos de prueba que no contienen ningún dato de usuario, puede utilizar HTTP para SharePoint 2013 y omitir el requisito de certificado. Lync Server 2013 admite sólo HTTPS.

Los certificados usados por Office Web Apps Server deben cumplir con los siguientes requisitos:

  - El certificado debe proceder de una entidad de certificación de confianza e incluir el nombre de dominio completo (FQDN) de la granja de servidores de Office Web Apps Server en el campo SAN (nombre alternativo del sujeto). (Si el FQDN no está en el SAN cuando intenta usar el certificado, el explorador mostrará advertencias de seguridad o no procesará la respuesta).

  - El certificado debe tener una clave privada exportable. En granjas de un solo servidor, esta opción se selecciona de manera predeterminada cuando usa el complemento Administrador de Internet Information Services (IIS) para importar el certificado.

  - El campo Nombre descriptivo debe ser único dentro del almacén de entidades de certificación raíz de confianza. Si tiene varios certificados que comparten un campo Nombre descriptivo, se producirá un error en la creación de la granja de servidores porque el cmdlet New-OfficeWebAppsFarm no sabrá cuál de los certificados usar.

  - Office Web Apps Server no necesita ninguna extensión o propiedad de certificado especial. Por ejemplo, no se necesitan extensiones de uso mejorado de clave (EKU) de cliente o extensión de EKU de servidor.

  - En Windows Server 2012 o Windows Server 2012 R2, debe instalar la característica "Permitir activación HTTP" de Windows Communication Foundation (WCF).

El certificado debe importarse de la siguiente manera:

  - **En granjas de un solo servidor** Debe importar el certificado directamente en el servidor que ejecuta Office Web Apps Server. No enlace el certificado manualmente. El cmdlet New-OfficeWebAppsFarm que ejecute posteriormente lo hará automáticamente. Si lo hace de forma manual, el certificado se eliminará cada vez que el servidor se reinicie.

  - **En granjas de servidores con equilibrio de carga:** si descarga SSL, se debe importar el certificado en el equilibrador de carga de hardware. Si no descarga SSL, debe instalar el certificado en cada servidor de la granja de servidores de Office Web Apps Server.


> [!NOTE]
> No use certificados autofirmados, salvo en entornos de prueba no críticos.



Para obtener más información acerca de los certificados, vea [cómo obtener un certificado SSL](https://go.microsoft.com/fwlink/p/?linkid=269700).

## Usar la descarga de SSL para equilibradores de carga de hardware

Al configurar una nueva granja de servidores de Office Web Apps Server, la descarga de SSL se desactiva de manera predeterminada. Si usa un equilibrador de carga de hardware, se recomienda activar la descarga de SSL para que cada servidor de Office Web Apps Server en la granja de servidores se pueda comunicar con el equilibrador de carga mediante HTTP. La activación de la descarga de SSL también ofrece las siguientes ventajas:

  - Administración de certificados simplificada

  - Afinidad de software mejorada

  - Rendimiento mejorado

Tenga en cuenta que al usar HTTP, el tráfico del equilibrador de carga a los servidores que ejecutan Office Web Apps Server no se cifra, por lo que debe asegurarse de que la red sea segura. Usar una subred privada puede ayudar a proteger el tráfico.

## Restringir qué servidores se pueden unir a una granja de servidores de Office Web Apps Server según la pertenencia a la unidad organizativa

Puede impedir que servidores no autorizados se unan a una granja de servidores de Office Web Apps Server creando una unidad organizativa para dichos servidores y especificando el parámetro FarmOU al crear la granja de servidores. Para obtener más información sobre el parámetro FarmOU, vea [New-OfficeWebAppsFarm](new-officewebappsfarm.md).

## Limitar el acceso del host para Office Web Apps Server mediante la lista Permitir

La lista Permitir es una característica de seguridad que impide a los hosts no deseados conectarse a una granja de servidores de Office Web Apps Server y usarla para operaciones de archivos sin su consentimiento. Si agrega los dominios que contienen hosts aprobados a la lista Permitir, puede limitar los hosts a los que Office Web Apps Server permite solicitudes de operaciones de archivos, como la recuperación de archivos, la recuperación de metadatos y los cambios en archivos.

Puede agregar dominios a la lista Permitir después de haber creado la granja de servidores de Office Web Apps Server. Para saber cómo agregar dominios a la lista Permitir, vea [New-OfficeWebAppsHost](new-officewebappshost.md).

<table>
<thead>
<tr class="header">
<th><img src="images/JJ219448.important(Office.15).gif" title="Importante" alt="Importante" /> <strong>Importante:</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Si no agrega dominios a la lista Permitir, Office Web Apps Server permite solicitudes de archivos a hosts en cualquier dominio. No deje esta lista en blanco si se puede tener acceso a su granja de servidores de Office Web Apps Server desde Internet. De lo contrario, cualquiera puede usar la granja de servidores de Office Web Apps Server para ver y modificar contenido.</td>
</tr>
</tbody>
</table>


## Planeación de Visores en línea con Office Web Apps Server

De manera predeterminada, la funcionalidad Visores en línea se habilita después de instalar Office Web Apps Server. Revise las siguientes instrucciones si prevé usar Visores en línea en su organización. En algunos casos, puede que desee deshabilitar algunas características en Visores en línea. Estas instrucciones hacen referencia a los parámetros que se establecen mediante los cmdlets de Windows PowerShell[New-OfficeWebAppsFarm](new-officewebappsfarm.md) y [Set-OfficeWebAppsFarm](set-officewebappsfarm.md).

## Consideraciones sobre seguridad para Visores en línea

Los archivos previstos para verse a través de un explorador web mediante Visores en línea no deben requerir la autenticación. En otras palabras, los archivos deben estar disponibles públicamente porque Visores en línea no puede realizar la autenticación cuando recupera archivos. Recomendamos encarecidamente que la granja de servidores de Office Web Apps Server que use para Visores en línea solo pueda tener acceso a la Intranet o a Internet, pero no a ambas. Esto se debe a que Office Web Apps Server no diferencia entre solicitudes de URL de la Intranet o de Internet. Alguien en Internet puede solicitar una dirección URL de intranet URL, por ejemplo, causando una fuga de seguridad si se ve un documento interno.

Por el mismo motivo, si ha configurado Office Web Apps Server para conectarse solo a Internet, recomendamos encarecidamente que deshabilite la compatibilidad con UNC en Visores en línea. Para deshabilitar la compatibilidad de UNC, establezca el parámetro OpenFromUncEnabled en False usando los cmdlets de Windows PowerShell[New-OfficeWebAppsFarm](new-officewebappsfarm.md) (para nuevas granjas de servidores) o [Set-OfficeWebAppsFarm](set-officewebappsfarm.md) (para granjas de servidores existentes).

Como precaución de seguridad adicional, Visores en línea se limita a la visualización de archivos de Office de 10 MB como máximo.

## Opciones de configuración para Visores en línea

Puede configurar Visores en línea usando los siguientes parámetros de Windows PowerShell en [New-OfficeWebAppsFarm](new-officewebappsfarm.md) (para nuevas granjas de servidores) o [Set-OfficeWebAppsFarm](set-officewebappsfarm.md) (para granjas de servidores existentes).

  - **OpenFromUrlEnabled**   Activa o desactiva Visores en línea. Este parámetro controla Visores en línea para archivos que tienen rutas de URL y UNC. De manera predeterminada, el parámetro está definido en False (deshabilitado) cuando crea una nueva granja de servidores de Office Web Apps Server.

  - **OpenFromUncEnabled**   Cuando Visores en línea está activado (establecido en True mediante OpenFromUrlEnabled), este parámetro activa o desactiva la capacidad de Visores en línea para mostrar archivos en rutas de UNC. De manera predeterminada, el parámetro está definido en True, pero asegúrese de que OpenFromUrlEnabled también esté establecido en True antes de habilitar la apertura de archivos desde rutas de UNC. Como se describe anteriormente, recomendamos que establezca el parámetro en False si ha configurado Office Web Apps Server para conectase a Internet.

  - **OpenFromUrlThrottlingEnabled**   Limita el número de solicitudes de apertura desde URL de un servidor determinado en un período de tiempo. Los valores de limitación predeterminados, que no son configurables, se aseguran de que una granja de servidores de Office Web Apps Server no inunde a un solo servidor con el envío de solicitudes para ver contenido en Visores en línea.

## Planeación de actualizaciones para Office Web Apps Server

Antes de implementar Office Web Apps Server, debe decidir cómo administrará la organización las actualizaciones de software en la granja de servidores de Office Web Apps Server. Si bien las actualizaciones de software ayudan a mejorar la seguridad, el rendimiento y la confiabilidad del servidor, si se instalan de forma incorrecta se pueden producir problemas con Office Web Apps Server.

La aplicación de actualizaciones de Office Web Apps Server con el proceso de actualizaciones automáticas de Microsoft no se admite en Office Web Apps Server. Las actualizaciones en un servidor de Office Web Apps Server se deben aplicar de un modo específico, como se describe en [Aplicar actualizaciones de software a Office Web Apps Server](apply-software-updates-to-office-web-apps-server.md). Si las actualizaciones de Office Web Apps Server se aplican automáticamente, es posible que los usuarios no puedan ver o editar documentos en Office Web Apps. Si esto ocurre, deberá recompilar la granja de servidores de Office Web Apps Server.

Le recomendamos que administre las actualizaciones con Windows Server Update Services (WSUS) o con System Center Administrador de configuración, que usa WSUS. WSUS le permite administrar por completo la distribución de las actualizaciones que se publican con Microsoft Update en cada servidor de la granja de servidores de Office Web Apps Server. Con WSUS, puede decidir qué actualizaciones se pueden aplicar en la granja de servidores de forma automática y cuáles se tienen que aplicar manualmente (por ejemplo, las actualizaciones de Office Web Apps Server). Para obtener más información sobre WSUS, vea [Windows Server Update Services](https://go.microsoft.com/fwlink/p/?linkid=294822).

Si no usa WSUS o System Center Administrador de configuración, configure las actualizaciones automáticas de Microsoft en cada servidor de la granja de servidores de Office Web Apps Server en **Descargar automáticamente, pero notificar al usuario para instalar**. Cuando se le notifique de una actualización de Office Web Apps Server, siga los pasos descritos en [Aplicar actualizaciones de software a Office Web Apps Server](apply-software-updates-to-office-web-apps-server.md). Para que las actualizaciones de Windows se apliquen y sus servidores estén protegidos, acéptelas cuando se le notifique de su disponibilidad.

## Consulte también


[Guía básica de contenido de Office Web Apps Server](content-roadmap-for-office-web-apps-server.md)  
[Introducción a Office Web Apps Server](office-web-apps-server-overview.md)  
[Implementar Office Web Apps Server](deploy-office-web-apps-server.md)  
[Aplicar actualizaciones de software a Office Web Apps Server](apply-software-updates-to-office-web-apps-server.md)  


[Office.com, (para obtener ayuda con Office Web Apps en su dispositivo móvil o de escritorio)](https://go.microsoft.com/fwlink/p/?linkid=266657)  
  

[https://technet.microsoft.com/es-es/library/jj966220](apply-software-updates-to-office-web-apps-server.md)

