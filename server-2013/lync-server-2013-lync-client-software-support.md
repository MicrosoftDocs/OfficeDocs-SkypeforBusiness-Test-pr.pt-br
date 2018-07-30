---
title: 'Lync Server 2013: Suporte a software do cliente do Lync'
TOCTitle: Suporte a software do cliente do Lync
ms:assetid: a6851e38-ba9a-4f19-9aa7-d8accf4d62b3
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg412781(v=OCS.15)
ms:contentKeyID: 49307699
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Suporte a software do cliente do Lync no Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

Esta seção resume o suporte de software para Lync 2013 e o Suplemento de Reunião Online para Lync 2013.

> [!NOTE]  
> O Suplemento de Reunião Online para Lync 2013, que dá suporte ao gerenciamento de reuniões no cliente de mensagem e colaboração do Outlook, é instalado automaticamente com o Lync 2013.

### Requisitos de software para Lync 2013 e o Suplemento de Reunião Online para Lync 2013

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Componente do sistema</th>
<th>Requisitos mínimos</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Sistema operacional do Windows</p></td>
<td><p>Windows 8.1</p>
<p>Windows 8</p>
<p>Sistema operacional Windows 7</p>
<p>Windows Server 2008 R2 com o service pack mais recente</p>
<div class="alert">
> [!NOTE]  
> O Lync 2013 e o Suplemento de Reunião Online para Lync 2013 não têm suporte no Windows Vista ou no Windows XP (nenhuma versão).
</div></td>
</tr>
<tr class="even">
<td><p>Instalação e atualizações</p></td>
<td><p>Direitos e permissões de administrador</p></td>
</tr>
<tr class="odd">
<td><p>Navegador</p></td>
<td><p>Navegador de Internet Windows Internet Explorer 10</p>
<p>Navegador de Internet Internet Explorer 9</p>
<p>Internet Explorer 8nm-ie-9</p>
<p>Navegador de Internet Internet Explorer 7</p>
<p>Navegador web Mozilla Firefox</p>
<div class="alert">
> [!NOTE]  
> Se você estiver usando o Lync com Microsoft Exchange Online e sua organização tiver implantado um proxy HTTP de autenticação, Internet Explorer 9 ou Internet Explorer 8 é obrigatório.
</div></td>
</tr>
<tr class="even">
<td><p>Integração com o Microsoft Office</p></td>
<td><p>Para o conjunto completo de recursos de integração:</p><ul><li><p>Cliente de mensagem e colaboração do Outlook 2013</p></li><li><p>Outlook 2010nm-outlk-15</p></li></ul></td>
</tr>
<tr class="odd">
<td><p>Integração com o Microsoft Exchange</p></td>
<td><p>Para o conjunto completo de recursos de integração:</p><ul><li><p>Microsoft Exchange Server 2013</p></li><li><p>Microsoft Exchange Server 2010</p></li></ul></td>
</tr>
</tbody>
</table>


## Sistemas operacionais Macintosh

O Lync 2013 está disponível apenas para Windows. No entanto, o Lync Server 2013 suporta os seguintes clientes em computadores que executam o Mac OS 10.5.8 ou service pack ou versões de sistema operacional (Intel) mais recentes (sistema operacional Mac OS 10.9 não possui suporte atualmente). Para mais detalhes sobre recursos suportados, consulte [Tabelas de comparação dos clientes para o Lync Server 2013](lync-server-2013-desktop-client-comparison-tables.md).

  - Microsoft Lync para Mac 2011 (consulte “Guia de implantação do Lync para Mac 2011” em [http://go.microsoft.com/fwlink/p/?LinkId=268786](http://go.microsoft.com/fwlink/p/?linkid=268786))

  - Microsoft Communicator para Mac 2011 (consulte “Guia de implantação Communicator para Mac 2011” em [http://go.microsoft.com/fwlink/p/?LinkId=268787](http://go.microsoft.com/fwlink/p/?linkid=268787))

## Navegadores do Lync Web App

O Lync Web App suporta combinações específicas de sistemas operacionais e navegadores. Para obter detalhes, consulte [Plataformas compatíveis com o Lync Web App para Lync Server 2013](lync-server-2013-lync-web-app-supported-platforms.md) na documentação de Planejamento.

## Ajuste de Suporte do Microsoft Office

Os clientes do Lync Server 2013 suportam integração com várias versões do Microsoft Office, como resumido nesta seção.

  - Os recursos de integração do Lync 2013 são suportados no Outlook 2013 e Microsoft Outlook 2010.

  - Os recursos de integração do Lync 2013 são suportados no Microsoft Exchange Server 2013 e Microsoft Exchange Server 2010.

  - O complemento Online Meeting para Lync 2013 tem suporte do Office 2013 e do Microsoft Office 2010.

## Usando perfis obrigatórios

Se os usuários estiverem planejando usar os recursos de conferência do Lync 2013 , eles não deverão usar os perfis obrigatórios do Serviços de Domínio Active Directory para entrar no cliente do Lync 2013. Como os perfis obrigatórios são perfis de usuário somente leitura, as chaves PKI (infraestrutura de chave pública) necessárias para conferências do Lync 2013 não podem ser salvas no perfil. Para obter detalhes, consulte o artigo 2552221 da Base de Dados de Conhecimento Microsoft, "O recurso de conferência do Lync 2010 falha quando o usuário é conectado usando um perfil de usuário obrigatório" em [http://go.microsoft.com/fwlink/?linkid=3052\&clcid=0x416](http://go.microsoft.com/fwlink/?linkid=3052%26clcid=0x416).

## Consulte Também

#### Conceitos

[Suporte a hardware de cliente do Lync no Lync Server 2013](lync-server-2013-lync-client-hardware-support.md)  
[Requisitos de vídeo do cliente Lync para o Lync Server 2013](lync-server-2013-lync-client-video-requirements.md)  
[Clientes com suporte de implantações anteriores no Lync Server 2013](lync-server-2013-supported-clients-from-previous-deployments.md)

