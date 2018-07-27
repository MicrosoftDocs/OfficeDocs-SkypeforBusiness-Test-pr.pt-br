---
title: Resumo do DNS – descoberta automática no Lync Server 2013
TOCTitle: Resumo do DNS – descoberta automática no Lync Server 2013
ms:assetid: b336a2ae-0e58-4b74-b606-aedbbd411587
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ945644(v=OCS.15)
ms:contentKeyID: 52057713
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Resumo do DNS – descoberta automática no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

Descoberta Automática é um serviço flexível por aceitar comunicação via HTTP ou HTTPS. Para isso ser possível, o Sistema de Nome de Domínio (DNS) e os certificados utilizados pelos servidores que utilizam o serviço de Descoberta Automática precisam ser configurados automaticamente. Requisitos de certificado são abordados em [Resumo do certificado – descoberta automática](lync-server-2013-certificate-summary-autodiscover.md).

> [!IMPORTANT]  
> A lógica de pesquisa de DNS para os clientes do Lync Server utiliza uma ordem de resolução específica. Você deve sempre incluir ambos o lyncdiscoverinternal.&lt;domain&gt; e o lyncdiscover.&lt;domain&gt; no seu DNS. Excluir o registro lyncdiscoverinternal.&lt;domain&gt; causará falha nos clientes internos ao conectarem-se aos serviços desejados ou fará com que esses clientes recebam uma resposta incorreta de Descoberta Automática.

### Registros de DNS interno

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Tipo do registro</th>
<th>Nome do host</th>
<th>É resolvido para</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>CNAME</p></td>
<td><p>Lyncdiscoverinternal.<em>&lt;nome de domínio interno&gt;</em></p></td>
<td><p>Serviços Internos Web FQDN para o seu Pool de diretores, caso você tenha um; ou então para o seu Pool de Front-Ends, caso você não tenha um Diretor.</p></td>
</tr>
<tr class="even">
<td><p>A (host, se for IPv6, AAAA)</p></td>
<td><p>lyncdiscoverinternal.<em>&lt;nome de domínio interno&gt;</em></p></td>
<td><p>O IP dos serviços Web internos (endereço de IP virtual - VIP - se você utilizar um balanceador de carga) do seu Pool de diretores, caso você tenha um; ou do seu Pool de Front-Ends, caso você não tenha um Diretor.</p></td>
</tr>
</tbody>
</table>


Você precisa criar um dos registros de DNS externo a seguir:

### Registros de DNS externo

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Tipo do registro</th>
<th>Nome do host</th>
<th>É resolvido para</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>CNAME</p></td>
<td><p>lyncdiscover.<em>&lt;sipdomain&gt;</em></p></td>
<td><p>Serviços Web externos FQDN para o seu Pool de diretores, caso você possua um, podendo ser para seu Pool de Front-Ends caso você não possua um Diretor.</p></td>
</tr>
<tr class="even">
<td><p>A (host, se for IPv6, AAAA)</p></td>
<td><p>lyncdiscover.<em>&lt;sipdomain&gt;</em></p></td>
<td><p>Endereço IP público ou externo do proxy reverso.</p></td>
</tr>
</tbody>
</table>


> [!NOTE]  
> Tráfego externo passa pelo proxy reverso.

> [!NOTE]  
> Clientes de dispositivos móveis não suportam múltiplos certificados de camada de soquetes de segurança (SSL) de diferentes domínios. Assim, o redirecionamento de CNAME para diferentes domínios não é suportado via HTTPS. Por exemplo, um registro CNAME de DNS para lyncdiscover.contoso.com que é redirecionado para um endereço em director.contoso.net não é suportado via HTTPS. Em tal tipologia, um cliente de dispositivo móvel precisaria utilizar HTTP para a primeira solicitação, de modo que o redirecionamento de CNAME fosse resolvido via HTTP. As solicitações subsequentes então utilizariam HTTPS. Para dar suporte a esse cenário, você precisa configurar seu proxy reverso com uma regra de publicação Web para a porta 80 (HTTP). Para detalhes, consulte &quot;Para criar uma regra de publicação Web para a porta 80&quot; em <a href="lync-server-2013-configuring-the-reverse-proxy-for-mobility.md">Configurando o proxy reverso para mobilidade no Lync Server 2013</a>. Redirecionamento CNAME para o mesmo domínio é suportado via HTTPS. Nesse caso, o certificado do domínio de destino cobre o domínio originador.

## Consulte Também

#### Tarefas

[Configurando o proxy reverso para mobilidade no Lync Server 2013](lync-server-2013-configuring-the-reverse-proxy-for-mobility.md)  

#### Conceitos

[Resumo do certificado – descoberta automática](lync-server-2013-certificate-summary-autodiscover.md)

