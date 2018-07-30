---
title: 'Lync Server 2013: Requisitos técnicos para conferência'
TOCTitle: Requisitos técnicos para conferência
ms:assetid: 3c0d89e1-53e6-46d7-bf8c-491260b292ea
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg425889(v=OCS.15)
ms:contentKeyID: 49306462
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Requisitos técnicos para conferência no Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

Para o Lync Server 2013, os recursos de conferência discada, conferência de A/V (áudio/vídeo), IM (mensagens instantâneas) e Webconferência sempre são executados no Servidores Front-End.

Esta seção detalha os requisitos de hardware e software para esses servidores, juntamente com a colocação de suporte.

A conferência discada é um recurso que contém vários componentes. Alguns dos componentes são específicos da conferência discada enquanto outros são componentes do Enterprise Voice. Esta seção descreve os requisitos dos componentes que são específicos da conferência discada. Para obter detalhes sobre os requisitos do Servidor de Mediação e do gateway PSTN (Rede Telefônica Pública Comutada), consulte [Componente do Servidor de Mediação no Lync Server 2013](lync-server-2013-mediation-server-component.md) e [Componentes e topologias para o Servidor de Mediação no Lync Server 2013](lync-server-2013-components-and-topologies-for-mediation-server.md) na documentação de planejamento.

## Requisitos de hardware

Em virtude de a Webconferência e a conferência de A/V estarem colocadas com o Servidor Front-End, os requisitos de hardware do servidor são os mesmos do Servidores Front-End. Para obter detalhes sobre os requisitos de hardware, consulte [Plataformas de hardware de servidor para Lync Server 2013](lync-server-2013-server-hardware-platforms.md) na documentação de suporte. Os componentes a seguir exigidos para conferência de discagem também têm os mesmos requisitos de hardware do Servidores Front-End:

  - Serviço de aplicativos

  - Aplicativo Atendedor de Conferência

  - Aplicativo Comunicado de Conferência

Os requisitos de hardware do Servidor Front-End são os mesmos de outras diversas funções de servidor no Lync Server 2013 e estão destacados na tabela a seguir.

## Requisitos de software

Em virtude de a Webconferência e a conferência de A/V estarem colocadas com o Servidor Front-End, os requisitos de software do servidor são os mesmos do Servidores Front-End. Para obter detalhes sobre os requisitos de software, consulte [Suporte a sistemas operacionais de servidor e de ferramentas no Lync Server 2013](lync-server-2013-server-and-tools-operating-system-support.md) na documentação de suporte.

Para Webconferências, o Lync Server 2013 também exige o Office Web Apps e o Servidor Office Web Apps (conhecido anteriormente como WAC Server) para lidar com as apresentações do PowerPoint. Para obter detalhes, consulte [Configurando a integração com servidor de Office Web Apps e Lync Server 2013](lync-server-2013-enabling-office-web-apps-server-and-lync-server-2013.md).

Para conferência discada, o Serviço de aplicativos, o Aplicativo Atendedor de Conferência e o Aplicativo Comunicado de Conferência têm os mesmos requisitos de sistema operacional do Servidores Front-End. Para obter detalhes sobre os requisitos de software, consulte [Suporte a sistemas operacionais de servidor e de ferramentas no Lync Server 2013](lync-server-2013-server-and-tools-operating-system-support.md) na documentação de suporte.

Aplicativo Atendedor de Conferência e Aplicativo Comunicado de Conferência exigem que o Tempo de execução do Windows Media Format esteja instalado em Servidores Front-End. O Tempo de execução do Windows Media Format é exigido para reproduzir arquivos WMA (áudio do Windows Media) que são usados para músicas em espera, nomes registrados e avisos. À exceção de Windows Server 2012 e Windows Server 2012 R2, o Tempo de execução do Windows Media Format é instalado automaticamente como parte da Experiência de Desktop do Windows quando a Instalação é executada, porém pode ser preciso reiniciar o computador. Portanto, é recomendável fazer a instalação como parte da Experiência de Desktop do Windows, que inclui o Tempo de execução do Windows Media Format, antes de executar a Instalação. Windows Server 2012 e Windows Server 2012 R2 exigem o Microsoft Media Foundation.

## Requisitos de porta para a conferência discada

A tabela a seguir descreve as portas que são usadas pela conferência discada. Se estiver usando um balanceador de carga, verifique se ele está configurado para as portas usadas por todos os aplicativos que serão executados no pool.

Essas portas são configurações padrão que você pode alterar utilizando o cmdlet **Set-CsApplicationServer**. Para detalhes sobre este cmdlet, consulte a documentação do Shell de Gerenciamento do Lync Server.

> [!NOTE]  
> Todas as instâncias do mesmo aplicativo em um pool usam a mesma porta de escuta SIP.

### Portas usadas pelas conferência discada

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Número da porta</th>
<th>Descrição</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>5072</p></td>
<td><p>Usada pelo Aplicativo Atendedor de Conferência para solicitações de escuta SIP</p></td>
</tr>
<tr class="even">
<td><p>5073</p></td>
<td><p>Usada pelo Aplicativo Comunicado de Conferência para solicitações de escuta SIP</p></td>
</tr>
</tbody>
</table>


## Clientes suportados para conferência discada

É possível usar o seguinte cliente para agendar conferências locais que dão suporte ao acesso discado:

  - Suplemento de Reunião Online para Lync 2013 (instalado automaticamente quando o Lync 2013 ou o Participante são instalados)

## Requisitos do Página Configurações de Conferência Discada

O Página Configurações de Conferência Discada suporta as combinações de sistemas operacionais e navegadores da web descritos na tabela a seguir.

> [!NOTE]  
> Versões de 32 bits e 64 bits dos sistemas operacionais são suportadas.

### Sistemas operacionais e navegadores da web suportados

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Sistema operacional</th>
<th>Navegador da Web</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Windows 7</p></td>
<td><p>Internet Explorer 9</p>
<p>Internet Explorer 8</p>
<p>Firefox</p></td>
</tr>
<tr class="even">
<td> </td>
<td> </td>
</tr>
<tr class="odd">
<td> </td>
<td> </td>
</tr>
<tr class="even">
<td><p>Windows Server 2008 R2</p></td>
<td><p>Internet Explorer 9</p>
<p>Internet Explorer 8</p>
<p>Internet Explorer 7</p></td>
</tr>
<tr class="odd">
<td><p>Mac OS</p></td>
<td><p>Firefox</p>
<p>Safari</p></td>
</tr>
</tbody>
</table>


## Requisitos de arquivo de áudio para conferência discada

O Lync Server 2013 não oferece suporte à personalização de prompts de voz e música para conferência discada. No entanto, caso você tenha grande necessidade comercial que requer a alteração dos arquivos de áudio padrão, consulte o artigo 961177 da Base de Dados de Conhecimento da Microsoft, [Como personalizar os prompts de voz ou arquivos de música para uma conferência de áudio discada no Microsoft Office Communications Server 2007 R2](http://go.microsoft.com/fwlink/p/?linkid=3052%26kbid=961177).

Também é possível usar o utilitário de gerenciamento de [Prompts de voz personalizados do Atendedor de Conferência do Microsoft Lync Server](http://go.microsoft.com/fwlink/p/?linkid=396880), que permite aos administradores substituir os prompts de voz padrão utilizados quando um chamador ingressa em uma reunião do Lync por prompts personalizados para oferecer uma experiência de entrada na reunião diferente. Os prompts de voz personalizados podem ser instalados em um servidor que executa o Lync Server 2010 ou Lync Server 2013, seja Enterprise ou Standard Edition.

O Aplicativo Atendedor de Conferência e o Aplicativo Comunicado de Conferência têm os seguintes requisitos para arquivos de música em espera, nomes registrados e avisos de voz:

  - Formato de arquivo WMA (áudio do Windows Media)

  - 16 bits mono

  - 48 kbps 2-pass CBR (taxa de bits constante)

  - Nível da fala a -24 DB

## Requisitos do usuário para conferência discada

Os usuários de conferências discadas devem ter um número de telefone ou extensão exclusivos atribuídos à respectiva conta. Este requisito oferece suporte à autenticação durante a conferência discada. Os usuários empresariais (isto é, usuários que têm credenciais do Serviços de Domínio Active Directory e contas do Lync Server em sua organização) digitam o respectivo número de telefone (ou extensão) e um PIN (número de identificação pessoal) para discar para conferências como um usuário autenticado.

