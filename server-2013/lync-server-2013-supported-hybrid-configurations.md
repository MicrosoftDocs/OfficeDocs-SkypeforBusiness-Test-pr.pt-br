---
title: 'Lync Server 2013: Configurações híbridas com suporte'
TOCTitle: Configurações híbridas com suporte
ms:assetid: 5d456d6c-ad71-420c-b6d8-4d9cd0324f86
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ945633(v=OCS.15)
ms:contentKeyID: 52057615
ms.date: 06/02/2017
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurações híbridas do Lync Server 2013 com suporte

 

_**Tópico modificado em:** 2016-12-08_

Você pode configurar implantações do Lync Server 2013 para integração tanto com o Microsoft Exchange Server 2010 e o Microsoft Exchange Server 2013 e o SharePoint Server, no local e online. Os recursos listados na tabela a seguir têm suporte em todos os clientes, a menos que haja uma especificação diferente. Para obter mais informações sobre o suporte ao cliente, consulte [Tabelas de comparação dos clientes para o Lync Server 2013](lync-server-2013-desktop-client-comparison-tables.md) e as tabelas de comparação de cliente Lync Online em [Clientes do Lync Online](http://go.microsoft.com/fwlink/p/?linkid=281902).

## Integração com o Exchange Server

A tabela seguinte lista os recursos com suporte em uma implantação híbrida quando integrada com Microsoft Exchange Server.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th></th>
<th>Exchange no local</th>
<th>Exchange Online</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Lync Server 2013 no local</strong></p></td>
<td><ul>
<li><p>IM/presença no Outlook</p>
<p>Para obter mais informações, consulte <a href="lync-server-2013-im-and-presence.md">IM e presença no Lync Server 2013</a></p></li>
<li><p>Agende e participe de reuniões online via Outlook</p>
<p>Para obter mais informações, consulte <a href="lync-server-2013-integrating-with-microsoft-exchange-server-2013.md">Integrar Microsoft Lync Server 2013 e Microsoft Exchange Server 2013</a></p></li>
<li><p>IM/presença em Outlook Web App</p>
<p>Para obter mais informações, consulte <a href="lync-server-2013-configuring-lync-server-in-a-cross-premises-environment.md">Configurando Microsoft Lync Server 2013 em um Ambiente Entre Instalações</a></p></li>
<li><p>Agende e participe de reuniões online via Outlook Web App</p></li>
<li><p>IM/Presença em clientes de dispositivos móveis</p></li>
<li><p>Participe de reuniões online em clientes de dispositivos móveis</p>
<p>Para obter mais informações, consulte <a href="lync-server-2013-deploying-mobility.md">Implantando mobilidade no Lync Server 2013</a></p></li>
<li><p>Publique o status com base nas informações de ocupado/livre do calendário do Outlook</p></li>
<li><p>Lista de contatos (via repositório de contato unificado)</p>
<p>Para obter mais informações, consulte <a href="lync-server-2013-configuring-lync-server-to-use-the-unified-contact-store.md">Configurando Microsoft Lync Server 2013 para usar o repositório de contato unificado</a></p>

> [!NOTE]  
> Requer Exchange 2013.<br />
Um cliente de desktop do Lync 2013 é necessário.

</li>
<li><p>Foto do contato em alta resolução no cliente do Lync 2013 e Lync Web App.</p>
<p>Para obter mais informações, consulte <a href="lync-server-2013-configuring-the-use-of-high-resolution-photos.md">Configurando o Uso de Fotos de Alta Resolução no Microsoft Lync Server 2013</a></p>

> [!NOTE]  
> Requer Exchange 2013.

</li>
<li><p>Delegação da reunião</p>
<p>Com suporte apenas quando ambos os usuários estão hospedados online na mesma floresta ou quando ambos estão hospedados no local.</p></li>
<li><p>O histórico de Conversas Perdidas e Registros de Chamadas são escritos para a caixa de correio do Exchange do usuário</p></li>
<li><p>Arquivamento de conteúdo (IM e reunião) no Exchange</p>
<p>Para obter mais informações, consulte <a href="lync-server-2013-deployment-checklist-for-archiving.md">Lista de verificação da implantação para Arquivamento no Lync Server 2013</a></p>

> [!NOTE]  
> Requer Exchange 2013.

</li>
<li><p>Pesquise o conteúdo arquivado</p>

> [!NOTE]  
> Requer Exchange 2013.

</li>
<li><p>Caixa postal</p>
<p>Para obter mais informações, consulte <a href="lync-server-2013-deploying-on-premises-exchange-um-to-provide-lync-server-2013-voice-mail.md">Implantando Exchange UM no local para fornecer correio de voz do Lync Server 2013</a></p></li>
</ul></td>
<td><ul>
<li><p>IM/presença no Outlook</p>
<p>Para obter mais informações, consulte <a href="lync-server-2013-configuring-on-premises-lync-server-integration-with-exchange-online.md">Configurando integração local do Lync Server 2013 com o Exchange Online</a></p></li>
<li><p>Agende e participe de reuniões online via Outlook</p></li>
<li><p>IM/Presença em OWA</p>
<p>Para obter mais informações, consulte <a href="lync-server-2013-configuring-on-premises-lync-server-integration-with-exchange-online.md">Configurando integração local do Lync Server 2013 com o Exchange Online</a></p></li>
<li><p>Agende e participe de uma reunião online a partir do Outlook Web App</p>
<p>Para obter mais informações, consulte <a href="lync-server-2013-configuring-on-premises-lync-server-integration-with-exchange-online.md">Configurando integração local do Lync Server 2013 com o Exchange Online</a></p></li>
<li><p>IM/Presença em clientes de dispositivos móveis</p></li>
<li><p>Participe de uma reunião online em clientes de dispositivos móveis</p></li>
<li><p>Publique o status com base nas informações de ocupado/livre do calendário do Outlook</p></li>
<li><p>Lista de contatos (via repositório de contato unificado). Para mais informações, consulte <a href="lync-server-2013-configuring-lync-server-to-use-the-unified-contact-store.md">Configurando Microsoft Lync Server 2013 para usar o repositório de contato unificado</a></p>

> [!NOTE]  
> Somente Lync Server 2013. Um cliente de desktop do Lync 2013 é necessário.

</li>
<li><p>Foto do contato em alta resolução no cliente do Lync 2013 e Lync Web App.</p>
<p>Para obter mais informações, consulte <a href="lync-server-2013-configuring-the-use-of-high-resolution-photos.md">Configurando o Uso de Fotos de Alta Resolução no Microsoft Lync Server 2013</a>.</p></li>
<li><p>Delegação da reunião</p>
<p>Com suporte apenas quando ambos os usuários estão hospedados online na mesma floresta ou quando ambos estão hospedados no local.</p></li>
<li><p>O histórico de Conversas Perdidas e Registros de Chamadas são escritos para a caixa de correio do Exchange do usuário</p></li>
<li><p>Arquivamento de conteúdo (IM e reunião) no Exchange.</p>
<p>Para obter mais informações, consulte <a href="lync-server-2013-deployment-checklist-for-archiving.md">Lista de verificação da implantação para Arquivamento no Lync Server 2013</a></p></li>
<li><p>Pesquise o conteúdo arquivado. Para obter mais informações, consulte <a href="http://go.microsoft.com/fwlink/p/?linkid=285448">Configurar o Exchange para o SharePoint eDiscovery Center</a></p></li>
<li><p>Caixa postal. Para mais informações, consulte <a href="lync-server-2013-providing-lync-server-users-voice-mail-on-hosted-exchange-um.md">Fornecendo caixa postal a usuários do Lync Server 2013 no Exchange UM hospedado</a></p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><strong>Lync Online</strong></p></td>
<td><ul>
<li><p>IM e presença em Outlook</p></li>
<li><p>Agende e participe de reuniões online via Outlook</p></li>
<li><p>IM/Presença em clientes de dispositivos móveis</p></li>
<li><p>O histórico de Conversas Perdidas e Registros de Chamadas são escritos para a caixa de correio do Exchange do usuário</p></li>
<li><p>Foto do contato em alta resolução no cliente do Lync 2013.</p>

> [!NOTE]  
> Requer Microsoft Exchange Server 2013. Não é suportado no Lync Web App quando os usuários estão localizados em Skype for Business Online.

</li>
<li><p>Participe de uma reunião online em clientes de dispositivos móveis</p></li>
<li><p>Publique o status com base nas informações de ocupado/livre do calendário do Outlook</p></li>
<li><p>Delegação da reunião</p>
<p>Com suporte apenas quando ambos os usuários estão hospedados online na mesma floresta ou quando ambos estão hospedados no local.</p></li>
</ul></td>
<td><ul>
<li><p>IM/presença no Outlook</p></li>
<li><p>Agende e participe de reuniões online via Outlook</p></li>
<li><p>IM/presença em Outlook Web App</p></li>
<li><p>Agende e participe de uma reunião online a partir do Outlook Web App</p></li>
<li><p>IM/Presença em clientes de dispositivos móveis</p></li>
<li><p>Participe de uma reunião online em clientes de dispositivos móveis</p></li>
<li><p>Publique o status com base nas informações de ocupado/livre do calendário do Outlook</p></li>
<li><p>O histórico de Conversas Perdidas e Registros de Chamadas são escritos para a caixa de correio do Exchange do usuário</p></li>
<li><p>Lista de contatos (via repositório de contato unificado)</p>

> [!NOTE]  
> O cliente Lync Server 2013 é requerido

</li>
<li><p>Foto do contato em alta resolução no cliente do Lync 2013 e Lync Web App</p></li>
<li><p>Delegação da reunião</p>
<p>Com suporte apenas quando ambos os usuários estão hospedados online na mesma floresta ou quando ambos estão hospedados no local.</p></li>
<li><p>Arquivamento de conteúdo (IM e reunião) no Exchange</p></li>
<li><p>Pesquise o conteúdo arquivado</p></li>
<li><p>Caixa postal</p></li>
</ul></td>
</tr>
</tbody>
</table>


## Integração com SharePoint

A tabela seguinte lista os recursos suportados em uma implantação híbrida Lync Server 2013 quando integrada com SharePoint.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th></th>
<th>SharePoint no local</th>
<th>SharePoint online</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Lync Server 2013 no local</strong></p></td>
<td><ul>
<li><p>Pesquisa de habilidades</p></li>
<li><p>Presença no SharePoint</p></li>
</ul></td>
<td><ul>
<li><p>Presença no SharePoint</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><strong>Lync Online</strong></p></td>
<td><ul>
<li><p>Presença no SharePoint</p></li>
</ul></td>
<td><ul>
<li><p>Presença no SharePoint</p></li>
</ul></td>
</tr>
</tbody>
</table>

