---
title: 'Lync Server 2013: Requisitos DNS para pool de Front-Ends'
TOCTitle: Requisitos DNS para pool de Front-Ends
ms:assetid: 02d2aa6b-9e01-437b-a2df-00590280150d
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398082(v=OCS.15)
ms:contentKeyID: 49305691
ms.date: 12/17/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Requisitos DNS para pool de Front-Ends no Lync Server 2013

 

_**Tópico modificado em:** 2016-12-15_

Para concluir com êxito este procedimento, você deve estar conectado no servidor ou domínio no mínimo como um membro do grupo de Administradores de Domínio ou membro do grupo DnsAdmins.

Você deve configurar os registros DNS (Domain Name Systems) antes de publicar sua topologia em Construtor de Topologias. Além disso, alguns dos FQDNs (nomes de domínio totalmente qualificados) usados na configuração de uma implantação Lync Server 2013 são FQDNs de servidor lógicos e não físicos, portanto, são necessárias configurações DNS adicionais antes da publicação.


> [!WARNING]
> O Lync Server 2013 não oferece suporte a domínios com rótulo único. Por exemplo, uma floresta com um domínio raiz chamado <STRONG>contoso.local</STRONG> é compatível, mas um domínio raiz chamado <STRONG>local</STRONG> não é compatível. Para obter detalhes, consulte o artigo 300684 da Base de Dados de Conhecimento da Microsoft, “Informações sobre a configuração do Windows para domínios com nomes DNS com rótulo único” em <A class=uri href="http://go.microsoft.com/fwlink/p/?linkid=3052%26kbid=300684">http://go.microsoft.com/fwlink/p/?linkid=3052&amp;kbid=300684</A>.



> [!IMPORTANT]  
> O nome especificado deve ser idêntico ao nome de computador configurado no servidor. O nome de computador de um computador que não está ingressado em um domínio é, por padrão, um nome curto, não um FQDN. Construtor de Topologias utiliza FQDNs, não nomes curtos. <strong>Utilize apenas caracteres padrão</strong> (incluindo A-Z, a-z, 0-9 e hifens) quando estiver atribuindo FQDNs de seus servidores executando Lync Server, Servidores de Borda e pools. Não use caracteres Unicode nem sublinhados. Caracteres não padrão em um FQDN normalmente não são suportados por um DNS externo e por autoridades de certificação (ACs) públicas (quando o FQDN deve ser atribuído ao SN no certificado).

Antes de operar a topologia após sua implantação, certifique-se de que os registros Active Directory e DNS a seguir estão criados (conforme suas necessidades por recursos específicos):

  - Cada função de servidor que existirá na topologia está publicada como um objeto Active Directory (ingressar o computador no domínio realizará isso).

  - Um Registro DNS A existe para cada servidor.

  - Um Registro SRV DNS existe para cada domínio SIP, se você planeja usar logon automático para clientes na forma de \_sipinternal\_tcp. *\<SIP domain\>* . Este registro não é necessário se você utilizar a configuração manual para clientes.

  - Um Registro DNS A para cada URL simples configurada, da qual normalmente existem quatro: meet, dialin, lwa e scheduler. Além dessas, há a URL simples de administrador que é uma URL especial para acesso ao Painel de Controle do Lync Server 2013.

  - O computador executando o SQL Server deve fazer parte do domínio e alcançável pelo computador do qual Construtor de Topologias está publicando.

A tabela segue as arquiteturas de referência apresentadas na seção Planejamento. Para maiores detalhes, consulte [Cenários de acesso de usuário externo no Lync Server 2013](lync-server-2013-scenarios-for-external-user-access.md) na documentação de planejamento.

### Registros DNS necessários para o Pool de Front-Ends

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Local</th>
<th>Tipo</th>
<th>FQDN</th>
<th>Mapeia para/Comenta</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>DNS Interno</p></td>
<td><p>A</p></td>
<td><p>pool01.contoso.net</p></td>
<td><p>Pool01 (balanceamento de carga DNS). Requer um registro DNS A para o endereço IP de cada Servidor Front-End no pool, mapeando para o pool FQDN.</p></td>
</tr>
<tr class="even">
<td><p>DNS Interno</p></td>
<td><p>A</p></td>
<td><p>pool01.contoso.net</p></td>
<td><p>Pool01 (IP virtual (VIP) de balanceamento de carga de hardware).</p></td>
</tr>
<tr class="odd">
<td><p>DNS Interno</p></td>
<td><p>A</p></td>
<td><p>fe01.contoso.net</p>
<p>fe02.contoso.net</p>
<p>fe03.contoso.net</p>
<p>…</p></td>
<td><p>Pool01 Servidor Front-End (NÓ 1)</p>
<p>Pool01 Servidor Front-End (NÓ 2)</p>
<p>Pool01 Servidor Front-End (NÓ 3)</p>
<p>…</p></td>
</tr>
<tr class="even">
<td><p>DNS Interno</p></td>
<td><p>A</p></td>
<td><p>fe02.contoso.net</p></td>
<td><p>Pool01 Servidor Front-End (NÓ 2)</p></td>
</tr>
<tr class="odd">
<td><p>DNS Interno</p></td>
<td><p>A</p></td>
<td><p>lsweb.contoso.net</p></td>
<td><p>Pool01 (VIP) para tráfego de web de cliente para servidor.</p></td>
</tr>
<tr class="even">
<td><p>DNS Interno</p></td>
<td><p>A</p></td>
<td><p>sqlbe.contoso.net</p></td>
<td><p>Pool01 Servidor Back-End executando SQL Server 2008 R2.</p></td>
</tr>
<tr class="odd">
<td><p>DNS Interno</p></td>
<td><p>A</p></td>
<td><p>sip.contoso.com</p></td>
<td><p>Exigido para Lync Phone Edition, ou logon automático de clientes sem registros SRV DNS e para correspondência estrita de domínios. Não é obrigatório em todos os casos.</p></td>
</tr>
<tr class="even">
<td><p>DNS Interno</p></td>
<td><p>A</p></td>
<td><p>sip.fabrikam.com</p></td>
<td><p>Presume um segundo domínio SIP. Exigido para Lync Phone Edition, logon automático de clientes sem registros SRV DNS e para correspondência estrita de domínios. Não é obrigatório em todos os casos.</p></td>
</tr>
<tr class="odd">
<td><p>DNS Interno</p></td>
<td><p>A</p></td>
<td><p>dialin.contoso.com</p></td>
<td><p>URL Simples para conferência discada publicada internamente - Servidor Front-End (ou Diretor, se instalado) responde a solicitações de URL simples</p></td>
</tr>
<tr class="even">
<td><p>DNS Interno</p></td>
<td><p>A</p></td>
<td><p>meet.contoso.com</p></td>
<td><p>URL Simples para conferência publicada internamente - Servidor Front-End (ou Diretor, se instalado) responde a solicitações de URL simples.</p></td>
</tr>
<tr class="odd">
<td><p>DNS Interno</p></td>
<td><p>A</p></td>
<td><p>admin.contoso.com</p>
<p>admin</p></td>
<td><p>Registro opcional, URL simples para Painel de Controle do Lync Server 2013 publicadas internamente - Servidor Front-End (ou Diretor, se instalado) responde a solicitações de URL simples. Apenas o nome do host (não o de domínio) é exigido.</p></td>
</tr>
</tbody>
</table>


> [!NOTE]  
> VIP = Endereço IP virtual para balanceador de carga de hardware

## Registros SRV DNS para o Pool de Front-Ends


<table style="width:100%;">
<colgroup>
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
</colgroup>
<thead>
<tr class="header">
<th>Local</th>
<th>Tipo</th>
<th>FQDN</th>
<th>FQDN Alvo</th>
<th>Porta</th>
<th>Mapeia para/Comenta</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>DNS Interno</p></td>
<td><p>SRV</p></td>
<td><p>_sipinternaltls._tcp.contoso.com</p></td>
<td><p>pool01.contoso.com</p></td>
<td><p>5061</p></td>
<td><p>Exigido para que a configuração automática de clientes Lync 2013 funcione internamente</p></td>
</tr>
<tr class="even">
<td><p>DNS Interno</p></td>
<td><p>SRV</p></td>
<td><p>_sipinternaltls._tcp.fabrikam.com</p></td>
<td><p>pool01.fabrikam.com</p></td>
<td><p>5061</p></td>
<td><p>Exigido para que a configuração automática de clientes Lync 2013 funcione internamente</p></td>
</tr>
<tr class="odd">
<td><p>DNS Interno</p></td>
<td><p>SRV</p></td>
<td><p>_ntp._udp.contoso.com</p></td>
<td><p>dc01.contoso.com</p></td>
<td><p>123</p></td>
<td><p>Fonte NTP (protocolo de tempo de rede) exigida para dispositivos executando Lync Phone Edition. Isso deve indicar o controlador de domínio, internamente. Caso o controlador de domínio não esteja definido, tentará usar o servidor NTP time.windows.com</p></td>
</tr>
</tbody>
</table>

