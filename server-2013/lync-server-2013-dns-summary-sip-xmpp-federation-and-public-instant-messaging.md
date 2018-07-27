---
title: Resumo de DNS - SIP, federação XMPP e mensagens instantâneas públicas
TOCTitle: Resumo de DNS - SIP, federação XMPP e mensagens instantâneas públicas
ms:assetid: 1ed24fb8-a849-44c0-a52e-7aef7527e644
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ618369(v=OCS.15)
ms:contentKeyID: 49306098
ms.date: 03/09/2017
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Resumo de DNS - SIP, federação XMPP e mensagens instantâneas públicas

 

_**Tópico modificado em:** 2017-03-09_

Os registros DNS que serão necessários para definir uma federação com parceiros do Office Communications Server ou Lync Server são determinados pela sua decisão de permitir descoberta DNS automática do seu domínio por outros parceiros. Se você publicar o registro SRV \_sipfederationtls.\_tcp. *\<nome do domínio SIP\>*, qualquer outro domínio federado SIP poderá "descobrir" sua federação. É possível controlar quais domínios federados podem se comunicar com você usando as configurações de domínios Permitidos e domínios Bloqueados no Painel de Controle do Lync Server ou definindo as configurações de domínios permitidos ou bloqueados usando o Shell de Gerenciamento do Lync Server e os cmdlets **Get**, **Set**, **New**, **Remove-CsAllowedDomain** e **-CsBlockedDomain** PowerShell. Para obter mais informações sobre como definir estas configurações e usar os cmdlets do PowerShell, consulte os **Tópicos Relacionados** no final deste tópico.

A tabela de resumo dos registros DNS exibe as entradas necessárias para uma federação aberta ou descoberta. Se você não deseja implementar o Diretório de Federação, é possível decidir não configurar o registro \_sipfederationtls.\_tcp. *\<nome de domínio SIP\>*.

> [!IMPORTANT]  
> Há cenários específicos nos quais você deve ter o registro SRV _sipfederationtls._tcp. <em>&lt;nome de domínio SIP&gt;</em>, mas você não deseja ter uma federação descoberta. Em tal caso, é onde você implantou mobilidade para seus usuários. O PNCH é um tipo especial de federação usado para clientes do Microsoft Lync Mobile no Apple iPhone ou iPad usando o cliente do Lync 2010 Mobile ou o Windows Phone usando o cliente móvel do Lync 2010 Mobile ou Lync 2013. O registro SRV _sipfederationtls._tcp. <em>&lt;nome de domínio SIP&gt;</em> é usado em caso de mobilidade e notificação de push. Para reduzir este problema e controlar sua capacidade de descoberta, desmarque a configuração <strong>Habilitar descoberta de domínio parceiro</strong> para desativar a descoberta.

Para configurar o XMPP (Protocolo de Presença e Mensagem Extensível) para sua implementação, você deve criar dois registros DNS (Sistema de Nome de Domínio) em um servidor DNS externo que resolverá os registros para o Serviço de Borda de Acesso de seu Servidor de Borda ou Pool de borda.

Ao configurar o DNS (Sistema de Nome de Domínio) para a conectividade de mensagem instantânea pública, você verá que a configuração que suporta usuários externos suportará a conectividade de IM pública. Se já tiver configurado seu Servidor de Borda ou Pool de borda, você deverá ter os registros de DNS necessários para dar suporte à conectividade de IM pública.

## Resumo de DNS - Federação SIP


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Local/TIPO/Porta</th>
<th>FQDN</th>
<th>Endereço IP/registro de host FQDN</th>
<th>Mapear para/Comentários</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>DNS/SRV/5061 Externo</p></td>
<td><p>_sipfederationtls._tcp.contoso.com</p></td>
<td><p>sip.contoso.com</p></td>
<td><p>Interface externa do Serviço de Borda de Acesso necessária para descoberta DNS automática da sua federação para outros parceiros de federação em potencial e é conhecido como “Domínios SIP Permitidos” (federação avançada nas versões anteriores). Repita conforme necessário para todos os domínios SIP com usuários habilitados do Lync</p>
<div class="alert">
> [!IMPORTANT]  
> Este registro SRV é necessário para mobilidade e o push notification clearing house. Em casos onde há mais de um domínio SIP, criar e publicar um registro SRV para cada domínio que terá clientes Lync Mobile. O Serviços de Notificação por Push e o Serviços de Notificação por Push da Apple podem não funcionar como esperado se não há um registro SRV explícito para cada domínio SIP que a implantação suporta.
</div></td>
</tr>
</tbody>
</table>


## Resumo de DNS - Protocolo de Presença e Mensagem Extensível (XMPP)


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Local/TIPO/Porta</th>
<th>FQDN</th>
<th>Endereço IP/Registro de host FQDN</th>
<th>Mapeia para/Comenta</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>DNS/SRV/5269 Externa</p></td>
<td><p>_xmpp-server._tcp.contoso.com</p></td>
<td><p>xmpp.contoso.com</p></td>
<td><p>Interface externa do proxy XMPP no Serviço de Borda de Acesso ou Pool de borda. Repita, conforme necessário, para todos os domínios SIP internos com usuários habilitados para o Lync em que o contato com os contatos do XMPP é permitido pela configuração da Política de Acesso Externo por meio de uma política global, política do site em que o usuário está localizado ou a política do usuário aplicada ao usuário habilitado para o Lync. Um domínio XMPP permitido também deve ser configurado na política de Parceiros Federados do XMPP. Consulte os tópicos em <strong>Consulte Também</strong> para detalhes adicionais</p></td>
</tr>
<tr class="even">
<td><p>DNS/A externo</p></td>
<td><p>xmpp.contoso.com (por exemplo)</p></td>
<td><p>Endereço IP de Serviço de Borda de Acesso em seu Servidor de Borda ou Pool de borda hospedando o proxy XMPP</p></td>
<td><p>Aponta para o Serviço de Borda de Acesso ou Pool de borda que hospeda o serviço de proxy XMPP. Normalmente, o registro SRV que você cria aponta para esse registro de host (A ou AAAA)</p></td>
</tr>
</tbody>
</table>


## Resumo de DNS – Conectividade de mensagem instantânea pública


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Local/TIPO/Porta</th>
<th>Registro de FQDN/DNS</th>
<th>Endereço IP/FQDN</th>
<th>Mapeia para/Comenta</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>DNS/A externo</p></td>
<td><p>sip.contoso.com</p></td>
<td><p>interface Serviço de Borda de Acesso</p></td>
<td><p>Interface externa do Serviço de Borda de Acesso (Contoso). Repita, conforme necessário, para todos os domínios SIP com usuários habilitados para o Lync.</p></td>
</tr>
</tbody>
</table>


## Consulte Também

#### Tarefas

[Configurando federação de XMPP no Lync Server 2013](lync-server-2013-setting-up-xmpp-federation.md)  
[Configurando notificações por push no Lync Server 2013](lync-server-2013-configuring-for-push-notifications.md)  
[Habilitar ou desabilitar descoberta de parceiros de federação no Lync Server 2013](lync-server-2013-enable-or-disable-discovery-of-federation-partners.md)  

#### Conceitos

[Cenários de acesso de usuário externo no Lync Server 2013](lync-server-2013-scenarios-for-external-user-access.md)  
[Determinar requisitios de DNS para Lync Server 2013](lync-server-2013-determine-dns-requirements.md)  

#### Outros Recursos

[Gerenciar domínios SIP federados para sua organização no Lync Server 2013](lync-server-2013-manage-sip-federated-domains-for-your-organization.md)

