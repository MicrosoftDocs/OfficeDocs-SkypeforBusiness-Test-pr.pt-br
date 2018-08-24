---
title: Resumo da porta – descoberta automática no Lync Server 2013
TOCTitle: Resumo da porta – descoberta automática no Lync Server 2013
ms:assetid: 8bd16363-5e18-4e4b-be99-b3e6457b4c99
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ945642(v=OCS.15)
ms:contentKeyID: 52057675
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Resumo da porta – descoberta automática no Lync Server 2013

 

_**Tópico modificado em:** 2016-04-06_

O serviço de Descoberta Automática do Lync Server 2013 é executado em servidores Diretor e pool de Front-Ends e, quando publicado em DNS usando registros de host do `lyncdiscover.<domain>` e do `lyncdiscoverinternal.<domain>`, pode ser usado por clientes para localizar recursos do Lync Server. Para dispositivos móveis executando o Lync Mobile para usar a Descoberta Automática, você pode primeiro precisar modificar as listas de nome alternativo de entidade do certificado em qualquer Diretor e Servidor Front-End executando o serviço de Descoberta Automática. Além disso, pode ser necessário modificar as listas de nome alternativo de entidade nos certificados usados pelas regras de publicação de serviços de Web externa em proxies reversos.

A decisão sobre usar as listas de nomes alternativos de entidade em proxies reversos é baseada em se o serviço de Descoberta Automática foi publicado na porta 80 ou na porta 443:

  - **Publicado na porta 80**   Não são necessárias alterações de certificado se a consulta inicial ao serviço de Descoberta Automática ocorrer na porta 80. Isso é porque os dispositivos que executam o Lync acessarão o proxy reverso na porta 80 externamente e depois serão redirecionados a um Diretor ou Servidor Front-End na porta 8080 internamente.

  - **Publicado na porta 443**   A lista de nomes alternativos de entidade nos certificados usados por meio da regra de publicação de serviços Web externos deve conter uma entrada do `lyncdiscover.<sipdomain>` para cada domínio SIP na sua organização.
    
    > [!IMPORTANT]  
    > Para novas instalações ou atualizações do Lync Server 2010 nas quais você tiver implantado Mobilidade, é possível usar a Porta 80 para a Descoberta Automática do serviço de Mobilidade ou reemitir certificados com o nome de entidade correto e nomes alternativos de entidade no lugar. Analise os certificados no seu Diretor e Servidor Front-End para confirmar qual caminho você quer escolher.

### Detalhes de firewall do servidor de proxy reverso: Interface externa

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Protocolo/TCP ou UDP/Porta</th>
<th>Endereço IP de Origem</th>
<th>Endereço IP de Destino</th>
<th>Notas</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>HTTP/TCP/80</p></td>
<td><p>Qualquer</p></td>
<td><p>Ouvinte do proxy reverso</p></td>
<td><p>(Opcional) Redirecionamento para HTTPS se o usuário inserir http://<em>&lt;publishedSiteFQDN&gt;</em>. Também é requerido se estiver usando o Office Web Apps para conferência e o serviço de Descoberta Automática para dispositivos móveis executando o Lync em situações nas quais a organização não deseja modificar o certificado de regra de publicação de serviço Web externo.</p></td>
</tr>
<tr class="even">
<td><p>HTTPS/TCP/443</p></td>
<td><p>Qualquer</p></td>
<td><p>Ouvinte do proxy reverso</p></td>
<td><p>Downloads do Catálogo de Endereços, serviço de consulta à Web do Catálogo de Endereços, Descoberta Automática, atualizações de cliente, conteúdo da reunião, atualizações de dispositivo, expansão de grupo, Office Web Apps para conferência, conferência de discagem e reuniões.</p></td>
</tr>
</tbody>
</table>


### Detalhes de firewall do servidor de proxy reverso: Interface interna

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Protocolo/TCP ou UDP/Porta</th>
<th>Endereço IP de Origem</th>
<th>Endereço IP de Destino</th>
<th>Notas</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>HTTP/TCP/8080</p></td>
<td><p>Interface interna do proxy reverso</p></td>
<td><p>Servidor Front-End, Pool de Front-Ends, Diretor, Pool de diretores, Office Web Apps para conferência</p></td>
<td><p>Necessário se o serviço Descoberta Automática estiver sendo usado para dispositivos móveis que executam o Lync em situações nas quais a organização não deseja modificar o certificado de regra de publicação de serviço Web externo. O tráfego enviado para a porta 80 na interface externa do proxy reverso é redirecionado para um pool na porta 8080 a partir da interface interna do proxy reverso, assim os serviços Web do pool podem diferenciá-lo do tráfego Web interno.</p></td>
</tr>
<tr class="even">
<td><p>HTTPS/TCP/4443</p></td>
<td><p>Interface interna do proxy reverso</p></td>
<td><p>Servidor Front-End, Pool de Front-Ends, Diretor, Pool de diretores, Office Web Apps para conferência</p></td>
<td><p>O tráfego enviado para a porta 443 na interface externa do proxy reverso é redirecionado para um pool na porta 4443 a partir da interface interna do proxy reverso, assim os serviços Web do pool podem diferenciá-lo do tráfego Web interno.</p></td>
</tr>
</tbody>
</table>

