---
title: ".Res. de porta - b. consol. em esc., balanc. carga de DNS c/ end. IP priv. usando NAT"
TOCTitle: Resumo de porta - borda consolidada em escala, balanceamento de carga de DNS com endereços IP privados usando NAT
ms:assetid: a296c2af-54d4-4b4f-9795-9191baf688cb
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg412756(v=OCS.15)
ms:contentKeyID: 49307666
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Resumo de porta - borda consolidada em escala, balanceamento de carga de DNS com endereços IP privados usando NAT no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

A funcionalidade do Servidor de Borda do Lync Server 2013 descrita nesta arquitetura de cenário é muito parecida com a que foi implantada no Lync Server 2010. O acréscimo mais notável é a entrada **5269 sobre TCP** de porta para XMPP (extensible messaging and presence protocol). O Lync Server 2013 implanta opcionalmente um proxy XMPP no Servidor de Borda ou Pool de borda e o servidor de gateway XMPP no Servidor Front-End ou Pool de Front-Ends.

Além do IPv4, o Servidor de Borda agora tem suporte para IPv6. Para não confundir, apenas o IPv4 é usado nos cenários.

**Rede de perímetro empresarial para borda consolidada em escala com endereços IP privados usando NAT**

![Borda Consolidada em Escala](images/Gg412756.96f5a8f5-16d2-464d-b86e-7c7ecfc89ead(OCS.15).jpg "Borda Consolidada em Escala")

## Detalhes de protocolo e porta

Recomenda-se abrir apenas as portas necessárias para dar suporte à funcionalidade para a qual você está fornecendo acesso externo.

Para que o acesso remoto funcione para qualquer serviço de borda, é imprescindível que o tráfego SIP seja permitido bi-direcionalmente, conforme mostra a figura do tráfego de borda de entrada/saída. Dito de outra forma, as mensagens SIP de e para o serviço de Borda de Acesso está envolvido em sistemas de mensagens instantâneas (IM), presença, webconferências, áudio/vídeo (A/V) e federação.

### Resumo do firewall para borda consolidada em escala, balanceamento de carga de DNS com endereços IP privados usando NAT: interface externa - nó 1 e nó 2 (exemplo)

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Função/Protocolo/TCP ou UDP/Porta</th>
<th>Endereço IP de Origem</th>
<th>Endereço IP de Destino</th>
<th>Notas</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>XMPP/TCP/5269</p></td>
<td><p>Qualquer um</p></td>
<td><p>Serviço de proxy XMPP (compartilha IP com Serviço de Borda de Acesso)</p></td>
<td><p>O serviço de proxy XMPP aceita tráfego de contatos XMPP em federações XMPP definidas</p></td>
</tr>
<tr class="even">
<td><p>XMPP/TCP/5269</p></td>
<td><p>Serviço de proxy XMPP (compartilha IP com Serviço de Borda de Acesso)</p></td>
<td><p>Qualquer um</p></td>
<td><p>O serviço de proxy XMPP envia tráfego a contatos XMPP em federações XMPP definidas</p></td>
</tr>
<tr class="odd">
<td><p>Acesso/HTTP/TCP/80</p></td>
<td><p>Servidor de Borda Serviço de Borda de Acesso</p></td>
<td><p>Qualquer um</p></td>
<td><p>Revocação de certificado/verificação e recuperação CRL</p></td>
</tr>
<tr class="even">
<td><p>Acesso/DNS/TCP/53</p></td>
<td><p>Servidor de Borda Serviço de Borda de Acesso</p></td>
<td><p>Qualquer um</p></td>
<td><p>Consulta DNS sobre TCP</p></td>
</tr>
<tr class="odd">
<td><p>Acesso/DNS/UDP/53</p></td>
<td><p>Servidor de Borda Serviço de Borda de Acesso</p></td>
<td><p>Qualquer um</p></td>
<td><p>Consulta DNS sobre UDP</p></td>
</tr>
<tr class="even">
<td><p>Acesso/SIP(TLS)/TCP/443</p></td>
<td><p>Qualquer um</p></td>
<td><p>Servidor de Borda Serviço de Borda de Acesso</p></td>
<td><p>Tráfego SIP do cliente para o servidor para acesso de usuário externo</p></td>
</tr>
<tr class="odd">
<td><p>Acesso/SIP(MTLS)/TCP/5061</p></td>
<td><p>Qualquer um</p></td>
<td><p>Serviço de borda de acesso do servidor de borda</p></td>
<td><p>Para conectividade a redes públicas e federadas de IM usando SIP</p></td>
</tr>
<tr class="even">
<td><p>Acesso/SIP(MTLS)/TCP/5061</p></td>
<td><p>Servidor de Borda Serviço de Borda de Acesso</p></td>
<td><p>Qualquer um</p></td>
<td><p>Para conectividade a redes públicas e federadas de IM usando SIP</p></td>
</tr>
<tr class="odd">
<td><p>Webconferência/PSOM (TLS)/TCP/443</p></td>
<td><p>Qualquer um</p></td>
<td><p>Servidor de Borda Serviço de Borda de Webconferência</p></td>
<td><p>Mídia da webconferência</p></td>
</tr>
<tr class="even">
<td><p>A/V/RTP/TCP/50.000-59.999</p></td>
<td><p>Servidor de Borda Serviço de Borda A/V</p></td>
<td><p>Qualquer um</p></td>
<td><p>Necessário para federar com parceiros que executem o Office Communications Server 2007, Office Communications Server 2007 R2, Lync Server 2010 e Lync Server 2013.</p></td>
</tr>
<tr class="odd">
<td><p>A/V/RTP/UDP/50.000-59.999</p></td>
<td><p>Servidor de Borda Serviço de Borda A/V</p></td>
<td><p>Qualquer um</p></td>
<td><p>Necessário somente para federação com parceiros que estejam executando o Office Communications Server 2007.</p></td>
</tr>
<tr class="even">
<td><p>A/V/RTP/TCP/50.000-59.999</p></td>
<td><p>Qualquer um</p></td>
<td><p>Servidor de Borda Serviço de Borda A/V</p></td>
<td><p>Necessário somente para federação com parceiros que estejam executando o Office Communications Server 2007</p></td>
</tr>
<tr class="odd">
<td><p>A/V/RTP/UDP/50.000-59.999</p></td>
<td><p>Qualquer um</p></td>
<td><p>Servidor de Borda Serviço de Borda A/V</p></td>
<td><p>Necessário somente para federação com parceiros que estejam executando o Office Communications Server 2007</p></td>
</tr>
<tr class="even">
<td><p>A/V/STUN,MSTURN/UDP/3478</p></td>
<td><p>Servidor de Borda Serviço de Borda A/V</p></td>
<td><p>Qualquer um</p></td>
<td><p>A saída 3478 é usada para determinar a versão do Servidor de Borda com que o Lync Server está se comunicando e também para tráfego de mídia de Servidor de Borda a Servidor de Borda. Necessária para federação com Lync Server 2010, Windows Live Messenger e Office Communications Server 2007 R2, necessária também se diversos Pools de borda forem implantados em uma empresa.</p></td>
</tr>
<tr class="odd">
<td><p>A/V/STUN,MSTURN/UDP/3478</p></td>
<td><p>Qualquer um</p></td>
<td><p>Servidor de Borda Serviço de Borda A/V</p></td>
<td><p>Negociação de candidatos STUN/TURN através de UDP/3478</p></td>
</tr>
<tr class="even">
<td><p>A/V/STUN,MSTURN/TCP/443</p></td>
<td><p>Qualquer um</p></td>
<td><p>Servidor de Borda Serviço de Borda A/V</p></td>
<td><p>Negociação de candidatos STUN/TURN através de TCP/443</p></td>
</tr>
<tr class="odd">
<td><p>A/V/STUN,MSTURN/TCP/443</p></td>
<td><p>Serviço de Borda A/V da Servidor de Borda</p></td>
<td><p>Qualquer um</p></td>
<td><p>Negociação de candidatos STUN/TURN através de TCP/443</p></td>
</tr>
</tbody>
</table>


### Resumo do firewall para borda consolidada em escala, balanceamento de carga de DNS com endereços IP privados usando NAT: interface interna - nó 1 e nó 2 (exemplo)

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
<th>Comentários</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>XMPP/MTLS/TCP/23456</p></td>
<td><p>Qualquer (pode ser definido como endereço da Servidor Front-End, endereço IP do Pool de Front-Ends executando o serviço de gateway XMPP)</p></td>
<td><p>Endereço IP da interface interna do Servidor de Borda</p></td>
<td><p>Tráfego XMPP de saída do serviço de gateway XMPP sendo executado no Servidor Front-End ou Pool de Front-Ends</p></td>
</tr>
<tr class="even">
<td><p>SIP/MTLS/TCP/5061</p></td>
<td><p>Qualquer (pode ser definido como Diretor, endereço IP do Pool de diretores, Servidor Front-End ou endereço IP do Pool de Front-Ends)</p></td>
<td><p>Interface interna do Servidor de Borda</p></td>
<td><p>Tráfego SIP de saída (da Diretor, endereço IP do Pool de diretores, Servidor Front-End ou endereço IP do Pool de Front-Ends) para a interface interna da Servidor de Borda</p></td>
</tr>
<tr class="odd">
<td><p>SIP/MTLS/TCP/5061</p></td>
<td><p>Interface interna do Servidor de Borda</p></td>
<td><p>Qualquer (pode ser definido como Diretor, endereço IP do Pool de diretores, Servidor Front-End ou endereço IP do Pool de Front-Ends)</p></td>
<td><p>Tráfego SIP de entrada (para a Diretor, endereço IP do Pool de diretores, Servidor Front-End ou endereço IP do Pool de Front-Ends) da interface interna da Servidor de Borda</p></td>
</tr>
<tr class="even">
<td><p>PSOM/MTLS/TCP/8057</p></td>
<td><p>Qualquer (pode ser definido como endereço IP da Servidor Front-End ou cada endereço IP da Servidor Front-End em um Pool de Front-Ends)</p></td>
<td><p>Interface interna do Servidor de Borda</p></td>
<td><p>Tráfego de webconferência da Servidor Front-End ou de cada Servidor Front-End, caso estejam em um pool, parar a interface interna da Servidor de Borda</p></td>
</tr>
<tr class="odd">
<td><p>SIP/MTLS/TCP/5062</p></td>
<td><p>Qualquer um (pode ser definido como IP do Servidor Front-End ou do Pool de Front-Ends, ou então como qualquer Aparelho de Filial Persistente ou Servidor de Filial Persistente utilizando esse Servidor de Borda)</p></td>
<td><p>Interface interna do Servidor de Borda</p></td>
<td><p>Autenticação de usuários A/V (serviço de autenticação A/V) de Servidor Front-End ou endereço IP do Pool de Front-Ends ou qualquer Aparelho de Filial Persistente ou Servidor de Filial Persistente utilizando esse Servidor de Borda</p></td>
</tr>
<tr class="even">
<td><p>STUN/MSTURN/UDP/3478</p></td>
<td><p>Qualquer um</p></td>
<td><p>Interface interna do Servidor de Borda</p></td>
<td><p>Caminho preferencial para transferência de mídia A/V entre usuários internos e externos, Aparelho de Filial Persistente ou Servidor de Filial Persistente</p></td>
</tr>
<tr class="odd">
<td><p>STUN/MSTURN/TCP/443</p></td>
<td><p>Qualquer um</p></td>
<td><p>Interface interna do Servidor de Borda</p></td>
<td><p>Caminho de fallback para transferência de mídia A/V entre usuários internos e externos, Aparelho de Filial Persistente ou Servidor de Filial Persistente; se a comunicação UDP não pode ser estabelecida, TCP é usado para transferência de arquivos e compartilhamento de área de trabalho</p></td>
</tr>
<tr class="even">
<td><p>HTTPS/TCP/4443</p></td>
<td><p>Qualquer (pode ser definido como o endereço IP da Servidor Front-End ou pool que mantém o Repositório de Gerenciamento Central)</p></td>
<td><p>Interface interna do Servidor de Borda</p></td>
<td><p>Replicação de alterações do Repositório de Gerenciamento Central para o Servidor de Borda</p></td>
</tr>
<tr class="odd">
<td><p>MTLS/TCP/50001</p></td>
<td><p>Qualquer um</p></td>
<td><p>Interface interna do Servidor de Borda</p></td>
<td><p>Controlador Serviço de Log Centralizado usando cmdlets Shell de Gerenciamento do Lync Server e Serviço de Log Centralizado, linha de comando ClsController (ClsController.exe) ou comandos e conjunto de log do agente (ClsAgent.exe)</p></td>
</tr>
<tr class="even">
<td><p>MTLS/TCP/50002</p></td>
<td><p>Qualquer um</p></td>
<td><p>Interface interna do Servidor de Borda</p></td>
<td><p>Controlador Serviço de Log Centralizado usando cmdlets Shell de Gerenciamento do Lync Server e Serviço de Log Centralizado, linha de comando ClsController (ClsController.exe) ou comandos e conjunto de log do agente (ClsAgent.exe)</p></td>
</tr>
<tr class="odd">
<td><p>MTLS/TCP/50003</p></td>
<td><p>Qualquer um</p></td>
<td><p>Interface interna do Servidor de Borda</p></td>
<td><p>Controlador Serviço de Log Centralizado usando cmdlets Shell de Gerenciamento do Lync Server e Serviço de Log Centralizado, linha de comando ClsController (ClsController.exe) ou comandos e conjunto de log do agente (ClsAgent.exe)</p></td>
</tr>
</tbody>
</table>


## Resumo de firewall para federação


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Função/Protocolo/TCP ou UDP/Porta</th>
<th>Endereço IP de Origem</th>
<th>Endereço IP de Destino</th>
<th>Notas</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Acesso/SIP(MTLS)/TCP/5061</p></td>
<td><p>Endereço IP público do Serviço de Borda de Acesso</p></td>
<td><p>Qualquer um</p></td>
<td><p>Para conectividade a redes públicas e federadas de IM usando SIP</p></td>
</tr>
</tbody>
</table>


## Resumo do firewall - Conectividade pública de mensagens instantâneas


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Função/Protocolo/TCP ou UDP/Porta</th>
<th>Endereço IP de Origem</th>
<th>Endereço IP de Destino</th>
<th>Notas</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Acesso/SIP(MTLS)/TCP/5061</p></td>
<td><p>Parceiros de conectividade pública de IM</p></td>
<td><p>Servidor de Borda Serviço de Borda de Acesso</p></td>
<td><p>Para conectividade a redes públicas e federadas de IM usando SIP</p></td>
</tr>
<tr class="even">
<td><p>Acesso/SIP(MTLS)/TCP/5061</p></td>
<td><p>Servidor de Borda Serviço de Borda de Acesso</p></td>
<td><p>Parceiros de conectividade pública de IM</p></td>
<td><p>Para conectividade a redes públicas e federadas de IM usando SIP</p></td>
</tr>
<tr class="odd">
<td><p>Acesso/SIP(TLS)/TCP/443</p></td>
<td><p>Clientes</p></td>
<td><p>Servidor de Borda Serviço de Borda de Acesso</p></td>
<td><p>Tráfego SIP do cliente para o servidor para acesso de usuário externo</p></td>
</tr>
<tr class="even">
<td><p>A/V/RTP/TCP/50.000-59.999</p></td>
<td><p>Servidor de Borda Serviço de Borda A/V</p></td>
<td><p>Clientes Live Messenger</p></td>
<td><p>Usado para sessões A/V com o Windows Live Messenger se a conectividade pública de IM estiver configurada.</p></td>
</tr>
<tr class="odd">
<td><p>A/V/STUN,MSTURN/UDP/3478</p></td>
<td><p>Servidor de Borda Serviço de Borda A/V</p></td>
<td><p>Clientes Live Messenger</p></td>
<td><p>Obrigatório para conectividade pública de IM com o Windows Live Messenger</p></td>
</tr>
<tr class="even">
<td><p>A/V/STUN,MSTURN/UDP/3478</p></td>
<td><p>Clientes Live Messenger</p></td>
<td><p>Servidor de Borda Serviço de Borda A/V</p></td>
<td><p>Obrigatório para conectividade pública de IM com o Windows Live Messenger</p></td>
</tr>
</tbody>
</table>


## Resumo de Firewall para protocolo XMPP (Extensible Messaging and Presence Protocol)


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
<th>Origem (endereço IP)</th>
<th>Destino (endereço IP)</th>
<th>Comentários</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>XMPP/TCP/5269</p></td>
<td><p>Qualquer um</p></td>
<td><p>Endereço IP da interface do Servidor de Borda  Serviço de Borda de Acesso</p></td>
<td><p>Porta padrão de comunicação entre servidores para XMPP. Permite comunicação para o proxy XMPP do Servidor de Borda de parceiros XMPP federados.</p></td>
</tr>
<tr class="even">
<td><p>XMPP/TCP/5269</p></td>
<td><p>Endereço IP da interface do Servidor de Borda  Serviço de Borda de Acesso</p></td>
<td><p>Qualquer um</p></td>
<td><p>Porta padrão de comunicação entre servidores para XMPP. Permite comunicação do proxy XMPP do Servidor de Borda para parceiros XMPP federados.</p></td>
</tr>
<tr class="odd">
<td><p>XMPP/MTLS/TCP/23456</p></td>
<td><p>Qualquer um</p></td>
<td><p>Cada IP da interface interna do Servidor de Borda</p></td>
<td><p>Tráfego XMPP interno do gateway XMPP na Servidor Front-End ou no Pool de Front-Ends para o endereço IP interno da Servidor de Borda ou cada endereço IP interno do membro do Pool de borda</p></td>
</tr>
</tbody>
</table>

