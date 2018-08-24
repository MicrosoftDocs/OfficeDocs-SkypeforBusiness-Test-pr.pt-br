---
title: 'Lync Server 2013: Processo de implantação para mobilidade'
TOCTitle: Processo de implantação para mobilidade
ms:assetid: 5a1cebda-c14b-4ff4-9c36-f7caa868160f
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Hh690023(v=OCS.15)
ms:contentKeyID: 49306803
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Processo de implantação para mobilidade no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

    Some information in this topic pertains to Cumulative Updates for Lync Server 2013: February 2013. It is noted accordingly.

Esta seção descreve a sequência de etapas necessárias para implantar o recurso de mobilidade do Lync Server 2013.

### Processo de implantação de mobilidade

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Fase</th>
<th>Etapas</th>
<th>Permissões</th>
<th>Documentação de implantação</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Criar registros do DNS (Sistema de Nomes de Domínio)</p></td>
<td><ul>
<li><p>Crie um registro CNAME DNS interno ou um registro A (host, se IPv6, AAAA) para resolver a URL interna do serviço Descoberta Automática.</p></li>
<li><p>Crie um registro CNAME DNS externo ou um registro A (host, se IPv6, AAAA) para resolver a URL externa do serviço Descoberta Automática.</p></li>
</ul></td>
<td><p>Admins. do Domínio</p>
<p>DnsAdmins</p></td>
<td><p><a href="lync-server-2013-creating-dns-records-for-the-autodiscover-service.md">Criando registros de DNS para o Serviço de Autodiscover no Lync Server 2013</a></p></td>
</tr>
<tr class="even">
<td><p>Modificar certificados</p></td>
<td><p>Adicione entradas de nome alternativo de entidade aos seguintes certificados para oferecer suporte a conexões seguras para usuários móveis:</p>
<ul>
<li><p>Certificado do Diretor</p></li>
<li><p>Certificado do Pool de Front-Ends</p></li>
<li><p>Certificado de proxy reverso</p></li>
</ul></td>
<td><p>Administrador local</p></td>
<td><p><a href="lync-server-2013-modifying-certificates-for-mobility.md">Modificando certificados para mobilidade no Lync Server 2013</a></p></td>
</tr>
<tr class="odd">
<td><p>Configurar o proxy inverso</p></td>
<td><ul>
<li><p>Atribua certificados atualizados com nomes alternativos de entidade ao Ouvinte SSL.</p></li>
<li><p>Reconfigure a regra de publicação na Web para a URL externa do serviço Descoberta Automática.</p></li>
<li><p>Certifique-se que exista uma regra de publicação na Web para a URL externa dos Serviços Web do Lync Server 2013 no seu Pool de Front-Ends.</p></li>
</ul>
<p>Ou</p>
<ul>
<li><p>Se você optar por usar HTTP para a solicitação inicial de Descoberta Automática e não atualizar as listas de nomes alternativos de entidade nos certificados, configure uma nova regra de publicação na Web ou reconfigure uma regra de publicação existente para HTTP na porta 80.</p></li>
</ul></td>
<td><p>Administrador local</p></td>
<td><p><a href="lync-server-2013-configuring-the-reverse-proxy-for-mobility.md">Configurando o proxy reverso para mobilidade no Lync Server 2013</a></p></td>
</tr>
<tr class="even">
<td><p>Teste sua implantação de mobilidade para Lync 2010 Mobile utilizando o serviço de mobilidade Mcx</p></td>
<td><p>Execute o <strong>Test-CsMcxP2PIM</strong> para enviar uma mensagem instantânea de uma pessoa para outra.</p>
<p>Veja a documentação do cmdlet Shell de Gerenciamento do Lync Server para <a href="https://docs.microsoft.com/en-us/powershell/module/skype/Test-CsMcxP2PIM">Test-CsMcxP2PIM</a> para obter uma lista completa de opções.</p></td>
<td><p>CsAdministrator</p></td>
<td><p><a href="lync-server-2013-verifying-your-mobility-deployment.md">Verificando sua implantação de mobilidade no Lync Server 2013</a></p></td>
</tr>
<tr class="odd">
<td><p>Teste sua implantação de mobilidade para clientes móveis Lync 2013 utilizando os componentes Web UCWA</p></td>
<td><p>Utilize o cmdlet <strong>Test-CsUcwaConference</strong> para testar e verificar se os usuários de teste pré-definidos ou um par de usuários efetivos podem utilizar o UCWA para criar uma conferência e participar dela.</p>
<p>Veja a documentação do cmdlet Shell de Gerenciamento do Lync Server para <a href="https://docs.microsoft.com/en-us/powershell/module/skype/Test-CsUcwaConference">Test-CsUcwaConference</a> para obter uma lista completa de opções.</p></td>
<td><p>CsAdministrator</p></td>
<td><p><a href="lync-server-2013-verifying-your-mobility-deployment.md">Verificando sua implantação de mobilidade no Lync Server 2013</a></p></td>
</tr>
<tr class="even">
<td><p>Configurar para notificações por push</p></td>
<td><ul>
<li><p>Para Lync Server 2013Servidores de Borda, adicione um provedor de hospedagem online do Lync Server e configure a federação do provedor de hospedagem.</p></li>
<li><p>Para Lync Server 2010  Servidores de Borda, adicione um provedor de hospedagem online do Lync Server e configure a federação do provedor de hospedagem.</p></li>
<li><p>Para Office Communications Server 2007 R2Servidores de Borda, adicione um parceiro federado.</p></li>
<li><p>Se você desejar oferecer suporte a notificações por push em uma rede Wi-Fi, configure uma regra de firewall de saída para a porta TCP 5223.</p></li>
<li><p>Use o cmdlet <strong>Set-CsPushNotificationConfiguration</strong> para habilitar as notificações de envio por push para o APNS (Apple Push Notification Service) e o MPNS (Microsoft Push Notification Service). Este recurso está desabilitado por padrão.</p></li>
<li><p>Use o cmdlet <strong>Test-CsFederatedPartner</strong> para testar a configuração da federação e o cmdlet <strong>Test-CsMCXPushNotification</strong> para testar as notificações de envio por push.</p>

> [!NOTE]  
> Notificações push são utilizadas para clientes Lync 2010 Mobile em dispositivos Apple e Windows Phone<br />
Notificações push são exigidas para clientes móveis Lync 2013 somente com Windows Phone

</li>
</ul></td>
<td><p>RtcUniversalServerAdmins</p></td>
<td><p><a href="lync-server-2013-configuring-for-push-notifications.md">Configurando notificações por push no Lync Server 2013</a></p></td>
</tr>
<tr class="odd">
<td><p>Configurar a política de mobilidade</p></td>
<td><p>Use o cmdlet <strong>Set-CsMobilityPolicy</strong> para permitir ou impedir:</p>
<ul>
<li><p>Chamada via Trabalho</p></li>
<li><p>Habilitação de áudio e vídeo por IP</p></li>
<li><p>Requer WiFi para áudio e/ou vídeo por IP</p></li>
</ul></td>
<td><p>CsAdministrator</p></td>
<td><p><a href="lync-server-2013-configuring-mobility-policy.md">Configurando a política de mobilidade no Lync Server 2013</a></p></td>
</tr>
</tbody>
</table>

