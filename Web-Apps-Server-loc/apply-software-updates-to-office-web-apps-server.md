---
title: Aplicar actualizaciones de software a Office Web Apps Server
TOCTitle: Aplicar actualizaciones de software a Office Web Apps Server
ms:assetid: 5d15dbd9-374e-422a-a870-43270dd0a2db
ms:mtpsurl: https://technet.microsoft.com/es-es/library/JJ966220(v=office.15)
ms:contentKeyID: 56631592
ms.date: 12/18/2017
mtps_version: v=office.15
ms.translationtype: HT
---

# Aplicar actualizaciones de software a Office Web Apps Server

 

_**Se aplica a:**Office Web Apps Server_

_**Última modificación del tema:**2016-12-16_

**Resumen:** se explica cómo se aplican las actualizaciones de software en una granja de Office Web Apps Server.

**Público:** profesionales de TI

Tras una nueva versión de Office Web Apps Server, Microsoft ofrece una serie de actualizaciones de software para tratar de mejorar la seguridad del servidor, el rendimiento y la fiabilidad. En este artículo se describe cómo se aplican las actualizaciones de software a los servidores individuales en una granja de Office Web Apps Server.

<table>
<thead>
<tr class="header">
<th><img src="images/JJ219448.important(Office.15).gif" title="Importante" alt="Importante" /><strong>Importante:</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Este artículo forma parte de <a href="content-roadmap-for-office-web-apps-server.md">Guía básica de contenido de Office Web Apps Server</a>. Use esta guía básica como punto de partida para consultar artículos, descargas y vídeos que le ayuden a implementar y administrar Office Web Apps Server.<br />
<strong>¿Necesita ayuda con Office Web Apps en su escritorio o dispositivo móvil?</strong> Puede encontrar esta información buscando &quot;Office Web Apps&quot; en <a href="http://go.microsoft.com/fwlink/p/?linkid=324961">Office.com</a>.</td>
</tr>
</tbody>
</table>


<table>
<thead>
<tr class="header">
<th><img src="images/JJ966220.warning(Office.15).gif" title="Advertencia" alt="Advertencia" /><strong>Advertencia:</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>La aplicación de actualizaciones de Office Web Apps Server mediante el proceso de actualizaciones automáticas no es compatible con Office Web Apps Server. Esto se debe a que las actualizaciones a un Office Web Apps Server se deben aplicar de una forma específica, como se describe en este artículo. Si las actualizaciones de Office Web Apps Server se aplican de forma automática, es posible que los usuarios no puedan ver o editar documentos en Office Web Apps y, en ese caso, tendrá que recompilar su granja de Office Web Apps Server. Para ello, debe quitar el Office Web Apps Server de la granja mediante <a href="remove-officewebappsmachine.md">Remove-OfficeWebAppsMachine</a>, desinstalar Office Web Apps Server con Agregar o quitar programas y, después, volver a instalar Office Web Apps Server siguiendo los pasos que se describen en <a href="deploy-office-web-apps-server.md">Implementar Office Web Apps Server</a>. Tras completar la nueva instalación, aplique la actualización siguiendo los pasos que se describen en este artículo.<br />
Es importante que revise las instrucciones de <a href="plan-office-web-apps-server.md">Planeación de actualizaciones para Office Web Apps Server</a> y establezca un proceso de actualización para la granja de Office Web Apps Server.</td>
</tr>
</tbody>
</table>


## Antes de empezar

Puede encontrar la lista de actualizaciones más recientes disponibles para Office Web Apps Server en el [blog de actualizaciones de Microsoft Office](http://go.microsoft.com/fwlink/p/?linkid=280269) y en [Centro de actualizaciones de TechNet para Office, servidores de Office y productos relacionados](http://go.microsoft.com/fwlink/p/?linkid=280271).

Las actualizaciones que se publican para Office Web Apps Server actualizarán Office Web Apps Server y cualquier otro paquete de idiomas de Office Web Apps Server que esté instalado. No existen actualizaciones por separado para los paquetes de idiomas de Office Web Apps Server.

Como parte del proceso de actualización, tendrá que volver a crear la granja de Office Web Apps Server. Para prepararse para volver a crear la granja de Office Web Apps Server, revise las propiedades de su granja de Office Web Apps Server actual ejecutando el cmdlet **Get-OfficeWebAppsFarm** de Windows PowerShell y revise los parámetros para [New-OfficeWebAppsFarm](new-officewebappsfarm.md). Los parámetros que utilice para **New-OfficeWebAppsFarm** deben ser los mismos que los que haya usado al configurar por primera vez la granja de Office Web Apps Server.


> [!NOTE]
> Para completar las tareas de este artículo, use un mouse, métodos abreviados de teclado u opciones táctiles. Para obtener más información, consulte los siguientes recursos: 
> <UL>
> <LI>
> <P><A href="http://go.microsoft.com/fwlink/p/?linkid=249150">Métodos abreviados de teclado</A></P>
> <LI>
> <P><A href="http://go.microsoft.com/fwlink/p/?linkid=249151">Tecnología táctil</A></P></LI></UL>



## Aplicar actualizaciones de software a una granja de Office Web Apps Server de un solo servidor

Para aplicar actualizaciones de software a una granja de Office Web Apps Server de un solo servidor, quite el Office Web Apps Server de la granja, aplique la actualización de software y vuelva a crear la granja de Office Web Apps Server. Si solo tiene un servidor en la granja de Office Web Apps Server, los usuarios no podrán utilizar Office Web Apps mientras el servidor se esté actualizando. Por este motivo, quizá sería conveniente que actualizase Office Web Apps Server en horas que no sean críticas o en horario no laboral.

**Para aplicar actualizaciones de software en una granja de un solo servidor**

1.  Si aún no ha descargado la actualización al Office Web Apps Server, descargue la actualización de Office Web Apps Server que desee aplicar del [Centro de descarga de Microsoft](http://go.microsoft.com/fwlink/p/?linkid=280274).

2.  En el Office Web Apps Server en el que desee aplicar la actualización de software, abra el mensaje de Windows PowerShell como administrador y ejecute el siguiente comando.
    
        Remove-OfficeWebAppsMachine

3.  Instale la actualización de Office Web Apps Server en ese servidor. Si se le solicita, reinicie el servidor.

4.  Abra el mensaje de Windows PowerShell como administrador y ejecute el cmdlet **New-OfficeWebAppsFarm** para volver a crear una granja de Office Web Apps Server. La dirección URL que especifique para **–InternalURL** es el nombre del servidor que ejecuta Office Web Apps Server; por ejemplo, **http://Contoso-WAC**. En este caso, usaría el mismo nombre que ha utilizado en la granja de Office Web Apps Server anterior. Utilice los mismos parámetros adicionales que utilizó la primera vez que creó la granja de Office Web Apps Server. Por ejemplo, el parámetro **–AllowHttp** configura la granja para que utilice HTTP y el parámetro **–EditingEnabled** habilita la edición en Office Web Apps cuando se utiliza junto a SharePoint 2013. El parámetro **–EditingEnabled** no lo utilizan Lync Server 2013 o Exchange Server 2013 porque esos hosts no admiten la edición.
    
    El código del siguiente ejemplo crea una granja de servidores de Office Web Apps Server nueva llamada http://Contoso-WAC.
    
        New-OfficeWebAppsFarm -InternalURL "http://Contoso-WAC" -AllowHttp -EditingEnabled
    
    En [New-OfficeWebAppsFarm](new-officewebappsfarm.md) se describen otros parámetros que configuran los servicios de traducción, los servidores proxy, la compatibilidad con las imágenes prediseñadas y los visores en línea.

## Aplicar actualizaciones de software a una granja de Office Web Apps Server de varios servidores

Para aplicar actualizaciones de software en una granja de Office Web Apps Server múltiple, debe quitar primero uno de los servidores del grupo de equilibrador de carga y de la granja, aplicar la actualización de software y crear una granja de Office Web Apps Server actualizada. Entonces, quite y actualice los otros servidores de la granja de Office Web Apps Server y únalos a la nueva granja actualizada. El equilibrio en la carga de tráfico con la granja nueva se produce cuando tiene suficientes servidores en la granja nueva para soportar el tráfico actual. Al utilizar este proceso de adaptación, los usuarios pueden abrir y editar documentos en Office Web Apps sin interrupción.

**Para aplicar actualizaciones de software en una granja de varios servidores**

1.  Descargue la actualización de Office Web Apps Server que desee aplicar del [Centro de descarga de Microsoft](http://go.microsoft.com/fwlink/p/?linkid=280274) a una ubicación de red disponible en la granja de Office Web Apps Server.

2.  Quite el Office Web Apps Server en el que desee aplicar la actualización de software del grupo de equilibrador de carga.

3.  En ese Office Web Apps Server, abra el mensaje de Windows PowerShell como administrador y ejecute el siguiente comando.
    
        Remove-OfficeWebAppsMachine

4.  Instale la actualización de Office Web Apps Server en ese servidor. Si se le solicita, reinicie el servidor.

5.  Abra el mensaje de Windows PowerShell como administrador y cree una granja de Office Web Apps Server con el cmdlet **New-OfficeWebAppsFarm**. La dirección URL que especifique para **–InternalURL** es el nombre del servidor que ejecuta Office Web Apps Server; por ejemplo, **http://Contoso-WAC**. En este caso, usaría el mismo nombre que ha utilizado en la granja de Office Web Apps Server. Utilice los mismos parámetros adicionales que utilizó al crear la granja de Office Web Apps Server. Por ejemplo, el parámetro **–AllowHttp** configura la granja para usar HTTP y el parámetro **–EditingEnabled** habilita la edición en Office Web Apps cuando se utiliza junto a SharePoint 2013. El parámetro **–EditingEnabled** no se utiliza para Lync Server 2013 o Exchange Server 2013 porque esos hosts no admiten la edición.
    
    El código del siguiente ejemplo crea una granja de servidores de Office Web Apps Server nueva llamada http://Contoso-WAC.
    
        New-OfficeWebAppsFarm -InternalURL "http://Contoso-WAC" -AllowHttp -EditingEnabled
    
    En [New-OfficeWebAppsFarm](new-officewebappsfarm.md) se describen otros parámetros que configuran los servicios de traducción, los servidores proxy, la compatibilidad con las imágenes prediseñadas y los visores en línea.

6.  En función del número de servidores que tenga en la granja de Office Web Apps Server, equilibre el tráfico de carga de la nueva granja. Puede aplazar este paso hasta que disponga de más servidores actualizados que se unirán a la granja.

7.  Para cada servidor restante de la granja, siga estos pasos.
    
    1.  Quite el siguiente Office Web Apps Server del grupo equilibrador de carga.
    
    2.  Instale la actualización de Office Web Apps Server en ese servidor. Si se le solicita, reinicie el servidor.
    
    3.  Abra el mensaje de Windows PowerShell como administrador y ejecute el siguiente comando. El parámetro **–MachineToJoin** agrega el servidor actual a una granja de Office Web Apps Server existente. En este caso, desea agregar el servidor a la granja de Office Web Apps Server actualizada. Igualmente, utilice el nombre de equipo del servidor de la granja de Office Web Apps Server actualizada.
        
            New-OfficeWebAppsMachine -MachineToJoin "server1.contoso.com"

## Consulte también


[Remove-OfficeWebAppsMachine](remove-officewebappsmachine.md)  
[New-OfficeWebAppsMachine](new-officewebappsmachine.md)  
[New-OfficeWebAppsFarm](new-officewebappsfarm.md)  
[Get-OfficeWebAppsFarm](get-officewebappsfarm.md)  


[Guía básica de contenido de Office Web Apps Server](content-roadmap-for-office-web-apps-server.md)  
  

[](content-roadmap-for-office-web-apps-server.md)

