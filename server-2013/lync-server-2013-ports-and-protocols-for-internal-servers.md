---
title: 'Lync Server 2013: portas e protocolos para servidores internos'
TOCTitle: Portas e protocolos para servidores internos
ms:assetid: c94063f1-e802-4a61-be90-022fc185335e
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398833(v=OCS.15)
ms:contentKeyID: 49308078
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Portas e protocolos para servidores internos no Lync Server 2013

 

_**Tópico modificado em:** 2016-04-06_

Esta seção resume as portas e os protocolos usados por servidores, balanceadores de carga e clientes em uma implantação do Lync Server.

> [!IMPORTANT]  
> Os clientes do Lync e do Communicator quando envolvidos em uma comunicação exclusiva, é geralmente referida como de ponto a ponto. Tecnicamente, os dois clientes estão se comunicando em uma conversa exclusiva, com a unidade de controle de multipontos de Mensagens Instantâneas (IMMCU) no meio. O IMMCU é um componente do Servidor Front-End. Colocar o IMMCU no fluxo de trabalho de comunicação necessário permite a gravação de detalhes da chamada e outros recursos que o Servidor Front-End habilita. A comunicação parte de uma porta de fonte dinâmica no cliente para a porta do Servidor Front-End TLS/TCP/5061 (pressupondo o uso da camada de segurança de transporte recomendada). Conforme projetada, a comunicação de ponto a ponto (assim como as IMs de várias partes) só é possível quando o Lync Server e o IMMCU estão ativos e disponíveis.

## Detalhes de protocolo e porta

> [!NOTE]  
> O Firewall do Windows precisa estar em execução antes de você iniciar os serviços do Lync Server em um servidor, pois é nesse momento que o Lync Server abre as portas necessárias no firewall.

Para obter detalhes sobre a configuração do firewall para componentes de borda, consulte [Determinar firewall A/V externo e requisitos de porta para Lync Server 2013](lync-server-2013-determine-external-a-v-firewall-and-port-requirements.md).

A tabela a seguir lista as portas que precisam ser abertas em cada função de servidor interno.

### Portas do servidor necessárias (por Função de servidor)

<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
</colgroup>
<thead>
<tr class="header">
<th>Função de servidor</th>
<th>Nome do serviço</th>
<th>Porta</th>
<th>Protocolo</th>
<th>Notas</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Todos os servidores</p></td>
<td><p>Navegador do SQL</p></td>
<td><p>1434</p></td>
<td><p>UDP</p></td>
<td><p>Navegador SQL para a cópia replicada local do banco de dados do Repositório de Gerenciamento Central.</p></td>
</tr>
<tr class="even">
<td><p>Servidores Front-End</p></td>
<td><p>Serviço de front-end do Lync Server</p></td>
<td><p>5060</p></td>
<td><p>TCP</p></td>
<td><p>Usada como opção pelos servidores Standard Edition e Servidores Front-End para rotas estáticas para serviços confiáveis, como servidores de controle de chamada remota.</p></td>
</tr>
<tr class="odd">
<td><p>Servidores Front-End</p></td>
<td><p>Serviço Front-End do Lync Server</p></td>
<td><p>5061</p></td>
<td><p>TCP (TLS)</p></td>
<td><p>Usada pelos servidores Standard Edition e pools Front-End para todas as comunicações SIP internas entre servidores (MTLS), para comunicações SIP entre o Servidor e o Cliente (TLS) e para comunicações SIP entre os Servidores Front-End e os Servidores de Mediação (MTLS). Também é usada para comunicações com o Monitoring Server.</p></td>
</tr>
<tr class="even">
<td><p>Servidores Front-End</p></td>
<td><p>Serviço de front-end do Lync Server</p></td>
<td><p>444</p></td>
<td><p>HTTPS</p>
<p>TCP</p></td>
<td><p>Usada para comunicação HTTPS entre o Foco (o componente do Lync Server que gerencia o estado de conferência) e os servidores individuais.</p>
<p>Essa porta também é usada para comunicação TCP entre Servidores Front-End e Aparelho de Filial Persistente.</p></td>
</tr>
<tr class="odd">
<td><p>Servidores Front-End</p></td>
<td><p>Serviço de front-end do Lync Server</p></td>
<td><p>135</p></td>
<td><p>DCOM e RPC (controle de procedimento remoto)</p></td>
<td><p>Usada para operações com base em DCOM, como Movendo Usuários, Sincronização do Replicador do Usuário e Sincronização do Catálogo de Endereços.</p></td>
</tr>
<tr class="even">
<td><p>Servidores Front-End</p></td>
<td><p>Conferência de IM do Lync Server</p></td>
<td><p>5062</p></td>
<td><p>TCP</p></td>
<td><p>Usado para solicitações SIP de entrada para conferência de IM (mensagem instantânea).</p></td>
</tr>
<tr class="odd">
<td><p>Servidores Front-End</p></td>
<td><p>Conferência da Web do Lync Server</p></td>
<td><p>8057</p></td>
<td><p>TCP (TLS)</p></td>
<td><p>Usada para escutar conexões PSOM (Modelo de Objeto Compartilhado Persistente) do cliente.</p></td>
</tr>
<tr class="even">
<td><p>Servidores Front-End</p></td>
<td><p>Serviço de compatibilidade de conferência da Web do Lync Server</p></td>
<td><p>8058</p></td>
<td><p>TCP (TLS)</p></td>
<td><p>Usada para escutar conexões PSOM do cliente Live Meeting e de versões anteriores do Lync Server.</p></td>
</tr>
<tr class="odd">
<td><p>Servidores Front-End</p></td>
<td><p>Serviço de conferência de áudio/vídeo do Lync Server</p></td>
<td><p>5063</p></td>
<td><p>TCP</p></td>
<td><p>Usada para solicitações SIP de entrada para conferência de áudio/vídeo (A/V).</p></td>
</tr>
<tr class="even">
<td><p>Servidores Front-End</p></td>
<td><p>Serviço de conferência de áudio/vídeo do Lync Server</p></td>
<td><p>57501-65535</p></td>
<td><p>TCP/UDP</p></td>
<td><p>Intervalo de porta de mídia usado para videoconferência.</p></td>
</tr>
<tr class="odd">
<td><p>Servidores Front-End</p></td>
<td><p>Serviço de compatibilidade da Web do Lync Server</p></td>
<td><p>80</p></td>
<td><p>HTTP</p></td>
<td><p>Usada para comunicação dos Servidores Front-End com os FQDNs do farm da web (as URLs usadas pelos componentes da web IIS) quando HTTPS não é usado.</p></td>
</tr>
<tr class="even">
<td><p>Servidores Front-End</p></td>
<td><p>Serviço de compatibilidade da Web do Lync Server</p></td>
<td><p>443</p></td>
<td><p>HTTPS</p></td>
<td><p>Usado para comunicação dos servidores front-End no farm da web FQDNs (as URLs usadas pelos componentes da web do IIS).</p></td>
</tr>
<tr class="odd">
<td><p>Servidores Front-End</p></td>
<td><p>Serviço de compatibilidade da Web do Lync Server</p></td>
<td><p>8080</p></td>
<td><p>TCP e HTTP</p></td>
<td><p>Usado pelos componentes da Web para acesso externo.</p></td>
</tr>
<tr class="even">
<td><p>Servidores Front-End</p></td>
<td><p>Servidor de componentes da Web</p></td>
<td><p>4443</p></td>
<td><p>HTTPS</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Servidores Front-End</p></td>
<td><p>Servidor de componentes da Web</p></td>
<td><p>8060</p></td>
<td><p>TCP (MTLS)</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Servidores Front-End</p></td>
<td><p>Servidor de componentes da Web</p></td>
<td><p>8061</p></td>
<td><p>TCP (MTLS)</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Servidores Front-End</p></td>
<td><p>Componente dos serviços de mobilidade</p></td>
<td><p>5086</p></td>
<td><p>TCP (MTLS)</p></td>
<td><p>Porta SIP usada pelos processos internos dos Serviços de Mobilidade.</p></td>
</tr>
<tr class="even">
<td><p>Servidores Front-End</p></td>
<td><p>Componente dos serviços de mobilidade</p></td>
<td><p>5087</p></td>
<td><p>TCP (MTLS)</p></td>
<td><p>Porta SIP usada pelos processos internos dos Serviços de Mobilidade.</p></td>
</tr>
<tr class="odd">
<td><p>Servidores Front-End</p></td>
<td><p>Componente dos serviços de mobilidade</p></td>
<td><p>443</p></td>
<td><p>HTTPS</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Servidores Front-End</p></td>
<td><p>Serviço Atendedor de Conferência do Lync Server (conferência discada)</p></td>
<td><p>5064</p></td>
<td><p>TCP</p></td>
<td><p>Usada para solicitações SIP de entrada para conferência discada.</p></td>
</tr>
<tr class="odd">
<td><p>Servidores Front-End</p></td>
<td><p>Serviço Atendedor de Conferência do Lync Server (conferência discada)</p></td>
<td><p>5072</p></td>
<td><p>TCP</p></td>
<td><p>Usada para solicitações SIP de entrada para o Atendedor (conferência discada).</p></td>
</tr>
<tr class="even">
<td><p>Servidores Front-End que também executam o Servidor de Mediação Colocado</p></td>
<td><p>Serviço de mediação do Lync Server</p></td>
<td><p>5070</p></td>
<td><p>TCP</p></td>
<td><p>Usada pelo Servidor de Mediação para solicitações de entrada do Servidor Front-End para o Servidor de Mediação.</p></td>
</tr>
<tr class="odd">
<td><p>Servidores Front-End que também executam um Servidor de Mediação Colocado</p></td>
<td><p>Serviço de mediação do Lync Server</p></td>
<td><p>5067</p></td>
<td><p>TCP (TLS)</p></td>
<td><p>Usada para solicitações SIP de entrada do gateway PSTN para o Servidor de Mediação.</p></td>
</tr>
<tr class="even">
<td><p>Servidores Front-End que também executam um Servidor de Mediação Colocado</p></td>
<td><p>Serviço de mediação do Lync Server</p></td>
<td><p>5068</p></td>
<td><p>TCP</p></td>
<td><p>Usada para solicitações SIP de entrada do gateway PSTN para o Servidor de Mediação.</p></td>
</tr>
<tr class="odd">
<td><p>Servidores Front-End que também executam um Servidor de Mediação Colocado</p>
<p></p></td>
<td><p>Serviço de mediação do Lync Server</p>
<p></p></td>
<td><p>5081</p></td>
<td><p>TCP</p></td>
<td><p>Usada para solicitações SIP de saída do Servidor de Mediação para o gateway PSTN.</p></td>
</tr>
<tr class="even">
<td><p>Servidores Front-End que também executam um Servidor de Mediação Colocado</p>
<p></p></td>
<td><p>Serviço de mediação do Lync Server</p>
<p></p></td>
<td><p>5082</p></td>
<td><p>TCP (TLS)</p></td>
<td><p>Usada para solicitações SIP de saída do Servidor de Mediação para o gateway PSTN.</p></td>
</tr>
<tr class="odd">
<td><p>Servidores Front-End</p></td>
<td><p>Serviço de compartilhamento de aplicativos do Lync Server</p></td>
<td><p>5065</p></td>
<td><p>TCP</p></td>
<td><p>Usada para solicitações de escuta do SIP de entrada para compartilhamento de aplicativos.</p></td>
</tr>
<tr class="even">
<td><p>Servidores Front-End</p></td>
<td><p>Serviço de compartilhamento de aplicativos do Lync Server</p></td>
<td><p>49152-65535</p></td>
<td><p>TCP</p></td>
<td><p>Intervalo de porta de mídia usado para compartilhamento de aplicativo.</p></td>
</tr>
<tr class="odd">
<td><p>Servidores Front-End</p></td>
<td><p>Serviço de anúncio de conferência do Lync Server</p></td>
<td><p>5073</p></td>
<td><p>TCP</p></td>
<td><p>Usada para solicitações SIP de entrada para o serviço de Anúncio de Conferência do Lync Server (ou seja, para conferência discada).</p></td>
</tr>
<tr class="even">
<td><p>Servidores Front-End</p></td>
<td><p>Serviço de estacionamento de chamadas do Lync Server</p></td>
<td><p>5075</p></td>
<td><p>TCP</p></td>
<td><p>Usada para solicitações SIP de entrada para o aplicativo Estacionamento de Chamadas.</p></td>
</tr>
<tr class="odd">
<td><p>Servidores Front-End</p></td>
<td><p>Serviço de teste de áudio do Lync Server</p></td>
<td><p>5076</p></td>
<td><p>TCP</p></td>
<td><p>Usada para solicitações SIP de entrada para o serviço Teste de Áudio.</p></td>
</tr>
<tr class="even">
<td><p>Servidores Front-End</p></td>
<td><p>NA (Not applicable)</p></td>
<td><p>5066</p></td>
<td><p>TCP</p></td>
<td><p>Usada para o gateway de E9-1-1 (9-1-1 Avançado) de saída.</p></td>
</tr>
<tr class="odd">
<td><p>Servidores Front-End</p></td>
<td><p>Serviço do grupo de resposta do Lync Server</p></td>
<td><p>5071</p></td>
<td><p>TCP</p></td>
<td><p>Usada para solicitações SIP de entrada para o aplicativo Grupo de Respostas.</p></td>
</tr>
<tr class="even">
<td><p>Servidores Front-End</p></td>
<td><p>Serviço do grupo de resposta do Lync Server</p></td>
<td><p>8404</p></td>
<td><p>TCP (MTLS)</p></td>
<td><p>Usada para solicitações SIP de entrada para o aplicativo Grupo de Respostas.</p></td>
</tr>
<tr class="odd">
<td><p>Servidores Front-End</p></td>
<td><p>Serviço de política de largura de banda do Lync Server</p></td>
<td><p>5080</p></td>
<td><p>TCP</p></td>
<td><p>Usada para controle de admissão de chamada pelo serviço Política de Largura de banda para tráfego TURN de Borda A/V.</p></td>
</tr>
<tr class="even">
<td><p>Servidores Front-End</p></td>
<td><p>Serviço de política de largura de banda do Lync Server</p></td>
<td><p>448</p></td>
<td><p>TCP</p></td>
<td><p>Usada para controle de admissão de chamada pelo serviço Política de Largura de Banda do Lync Server.</p></td>
</tr>
<tr class="odd">
<td><p>Servidores Front-End nos quais o Repositório de Gerenciamento Central reside</p></td>
<td><p>Serviço Agente Replicador Mestre do Lync Server</p></td>
<td><p>445</p></td>
<td><p>TCP</p></td>
<td><p>Usada para enviar dados de configuração do Repositório de Gerenciamento Central para os servidores que executam o Lync Server.</p></td>
</tr>
<tr class="even">
<td><p>Todos os servidores</p></td>
<td><p>Navegador do SQL</p></td>
<td><p>1434</p></td>
<td><p>UDP</p></td>
<td><p>Navegador do SQL para cópia local replicada dos dados do Repositório de Gerenciamento Central na instância local do SQL Server.</p></td>
</tr>
<tr class="odd">
<td><p>Todos os servidores internos</p></td>
<td><p>Vários</p></td>
<td><p>49152-57500</p></td>
<td><p>TCP/UDP</p></td>
<td><p>Intervalo de porta de mídia usado para audioconferência em todos os servidores internos. Usada por todos os servidores que encerram o áudio: Servidores Front-End (para o serviço Atendedor de Conferência do Lync Server, serviço Anúncio de Conferência do Lync Server e serviço Conferência de Áudio/Vídeo do Lync Server) e Servidor de Mediação.</p></td>
</tr>
<tr class="even">
<td><p>Servidor Office Web Apps</p></td>
<td><p></p></td>
<td><p>443</p></td>
<td><p></p></td>
<td><p>Utilizado pelo Lync Server 2013 para conexão ao Servidor Office Web Apps.</p></td>
</tr>
<tr class="odd">
<td><p>Diretores</p></td>
<td><p>Serviço de front-end do Lync Server</p></td>
<td><p>5060</p></td>
<td><p>TCP</p></td>
<td><p>Usada como opção para rotas estáticas até os serviços confiáveis, como servidores de controle de chamada remota.</p></td>
</tr>
<tr class="even">
<td><p>Diretores</p></td>
<td><p>Serviço de front-end do Lync Server</p></td>
<td><p>444</p></td>
<td><p>HTTPS</p>
<p>TCP</p></td>
<td><p>Comunicação entre servidores entre Front-End e Diretor. Além disso, o certificado cliente publica (para Servidores Front-End) ou valida se o certificado cliente já foi publicado.</p></td>
</tr>
<tr class="odd">
<td><p>Diretores</p></td>
<td><p>Serviço de compatibilidade da Web do Lync Server</p></td>
<td><p>80</p></td>
<td><p>TCP</p></td>
<td><p>Usada para comunicação inicial dos Diretores com os FQDNs de farm da web (as URLs usadas pelos componentes da web IIS). Em uma operação normal, trocará para tráfego HTTPS, usando a porta 443 e o tipo de protocolo TCP.</p></td>
</tr>
<tr class="even">
<td><p>Diretores</p></td>
<td><p>Serviço de compatibilidade da Web do Lync Server</p></td>
<td><p>443</p></td>
<td><p>HTTPS</p></td>
<td><p>Usada para comunicação dos Diretores com os FQDNs de farm da web (as URLs usadas pelos componentes da web IIS).</p></td>
</tr>
<tr class="odd">
<td><p>Diretores</p></td>
<td><p>Serviço de front-end do Lync Server</p></td>
<td><p>5061</p></td>
<td><p>TCP</p></td>
<td><p>Usada para comunicações internas entre os servidores e para conexões do cliente.</p></td>
</tr>
<tr class="even">
<td><p>Servidores de mediação</p></td>
<td><p>Serviço de mediação do Lync Server</p></td>
<td><p>5070</p></td>
<td><p>TCP</p></td>
<td><p>Usada pelo Servidor de mediação para solicitações de entrada do Servidor Front-End.</p></td>
</tr>
<tr class="odd">
<td><p>Servidores de mediação</p></td>
<td><p>Serviço de mediação do Lync Server</p></td>
<td><p>5067</p></td>
<td><p>TCP (TLS)</p></td>
<td><p>Usada para solicitações SIP de entrada do gateway PSTN.</p></td>
</tr>
<tr class="even">
<td><p>Servidores de mediação</p></td>
<td><p>Serviço de mediação do Lync Server</p></td>
<td><p>5068</p></td>
<td><p>TCP</p></td>
<td><p>Usada para solicitações SIP de entrada do gateway PSTN.</p></td>
</tr>
<tr class="odd">
<td><p>Servidores de mediação</p></td>
<td><p>Serviço de mediação do Lync Server</p></td>
<td><p>5070</p></td>
<td><p>TCP (MTLS)</p></td>
<td><p>Usada para solicitações SIP dos Servidores Front-End.</p></td>
</tr>
<tr class="even">
<td><p>Servidor de front-end de bate-papo persistente</p></td>
<td><p>SIP de bate-papo persistente</p></td>
<td><p>5041</p></td>
<td><p>TCP (MTLS)</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Servidor de front-end de bate-papo persistente</p></td>
<td><p>Bate-papo persistente do Windows Communication Foundation (WCF)</p></td>
<td><p>881</p></td>
<td><p>TCP (TLS) e TCP (MTLS)</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Servidor de front-end de bate-papo persistente</p></td>
<td><p>Serviço de transferência de arquivos de bate-papo persistente</p></td>
<td><p>443</p></td>
<td><p>TCP (TLS)</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>


> [!NOTE]  
> Alguns cenários de controle de chamada remota exigem uma conexão TCP entre o Servidor Front-End ou o Diretor e o PBX. Embora o Lync Server não use mais a porta TCP 5060, durante a implantação do controle de chamada remota você cria uma configuração de servidor confiável, que associa o FQDN do Servidor de linha RCC com a porta TCP que o Servidor Front-End ou o Diretor usará para se conectar ao sistema PBX. Para obter detalhes, consulte o cmdlet <strong>CsTrustedApplicationComputer</strong> na documentação do Shell de Gerenciamento do Lync Server.

Para os seus pools que usam somente o balanceamento de carga de hardware (não o balanceamento de carga DNS), a tabela a seguir mostra as portas que precisam abrir os balanceadores de carga de hardware.

### Portas do balanceador de carga de hardware se estiver usando somente o balanceador de carga de hardware

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Balanceador de carga</th>
<th>Porta</th>
<th>Protocolo</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Balanceador de carga do Servidor Front-End</p></td>
<td><p>5061</p></td>
<td><p>TCP (TLS)</p></td>
</tr>
<tr class="even">
<td><p>Balanceador de carga do Servidor Front-End</p></td>
<td><p>444</p></td>
<td><p>HTTPS</p></td>
</tr>
<tr class="odd">
<td><p>Balanceador de carga do Servidor Front-End</p></td>
<td><p>135</p></td>
<td><p>DCOM e RPC (controle de procedimento remoto)</p></td>
</tr>
<tr class="even">
<td><p>Balanceador de carga do Servidor Front-End</p></td>
<td><p>80</p></td>
<td><p>HTTP</p></td>
</tr>
<tr class="odd">
<td><p>Balanceador de carga do Servidor Front-End</p></td>
<td><p>8080</p></td>
<td><p>TCP - Recuperação por parte do cliente e do dispositivo do certificado raiz do Servidor Front-End – clientes e dispositivos autenticados por NTLM</p></td>
</tr>
<tr class="even">
<td><p>Balanceador de carga do Servidor Front-End</p></td>
<td><p>443</p></td>
<td><p>HTTPS</p></td>
</tr>
<tr class="odd">
<td><p>Balanceador de carga do Servidor Front-End</p></td>
<td><p>4443</p></td>
<td><p>HTTPS (do proxy reverso)</p></td>
</tr>
<tr class="even">
<td><p>Balanceador de carga do Servidor Front-End</p></td>
<td><p>5072</p></td>
<td><p>TCP</p></td>
</tr>
<tr class="odd">
<td><p>Balanceador de carga do Servidor Front-End</p>
<p></p></td>
<td><p>5073</p></td>
<td><p>TCP</p></td>
</tr>
<tr class="even">
<td><p>Balanceador de carga do Servidor Front-End</p>
<p></p></td>
<td><p>5075</p></td>
<td><p>TCP</p></td>
</tr>
<tr class="odd">
<td><p>Balanceador de carga do Servidor Front-End</p>
<p></p></td>
<td><p>5076</p></td>
<td><p>TCP</p></td>
</tr>
<tr class="even">
<td><p>Balanceador de carga do Servidor Front-End</p>
<p></p></td>
<td><p>5071</p></td>
<td><p>TCP</p></td>
</tr>
<tr class="odd">
<td><p>Balanceador de carga do Servidor Front-End</p>
<p></p></td>
<td><p>5080</p></td>
<td><p>TCP</p></td>
</tr>
<tr class="even">
<td><p>Balanceador de carga do Servidor Front-End</p>
<p></p></td>
<td><p>448</p></td>
<td><p>TCP</p></td>
</tr>
<tr class="odd">
<td><p>Balanceador de carga do Servidor de mediação</p>
<p></p></td>
<td><p>5070</p></td>
<td><p>TCP</p></td>
</tr>
<tr class="even">
<td><p>Balanceador de carga do Servidor Front-End (se o pool também executa o Servidor de mediação)</p>
<p></p></td>
<td><p>5070</p></td>
<td><p>TCP</p></td>
</tr>
<tr class="odd">
<td><p>Balanceador de carga do Diretor</p></td>
<td><p>443</p></td>
<td><p>HTTPS</p></td>
</tr>
<tr class="even">
<td><p>Balanceador de carga do Diretor</p></td>
<td><p>444</p></td>
<td><p>HTTPS</p></td>
</tr>
<tr class="odd">
<td><p>Balanceador de carga do Diretor</p>
<p></p></td>
<td><p>5061</p></td>
<td><p>TCP</p></td>
</tr>
<tr class="even">
<td><p>Balanceador de carga do Diretor</p></td>
<td><p>4443</p></td>
<td><p>HTTPS (do proxy reverso)</p></td>
</tr>
</tbody>
</table>


Seus pools do Front-End e do Diretor que usam o balanceamento de carga DNS também precisam ter um balanceador de carga de hardware implantado. A tabela a seguir mostra as portas que precisam ser abertas nesses balanceadores de carga de hardware.

### Portas do balanceador de carga de hardware se estiver usando o balanceamento de carga DNS

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Balanceador de carga</th>
<th>Porta</th>
<th>Protocolo</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Balanceador de carga do Servidor Front-End</p></td>
<td><p>80</p></td>
<td><p>HTTP</p></td>
</tr>
<tr class="even">
<td><p>Balanceador de carga do Servidor Front-End</p></td>
<td><p>443</p></td>
<td><p>HTTPS</p></td>
</tr>
<tr class="odd">
<td><p>Balanceador de carga do Servidor Front-End</p></td>
<td><p>8080</p></td>
<td><p>TCP - Recuperação por parte do cliente e do dispositivo do certificado raiz do Servidor Front-End – clientes e dispositivos autenticados por NTLM</p></td>
</tr>
<tr class="even">
<td><p>Balanceador de carga do Servidor Front-End</p></td>
<td><p>4443</p></td>
<td><p>HTTPS (do proxy reverso)</p></td>
</tr>
<tr class="odd">
<td><p>Balanceador de carga do Diretor</p></td>
<td><p>443</p></td>
<td><p>HTTPS</p></td>
</tr>
<tr class="even">
<td> </td>
<td> </td>
<td> </td>
</tr>
<tr class="odd">
<td><p>Balanceador de carga do Diretor</p></td>
<td><p>4443</p></td>
<td><p>HTTPS (do proxy reverso)</p></td>
</tr>
</tbody>
</table>


### Portas do cliente necessárias

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Componente</th>
<th>Porta</th>
<th>Protocolo</th>
<th>Notas</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Clientes</p></td>
<td><p>67/68</p></td>
<td><p>DHCP</p></td>
<td><p>Usada pelo Lync Server para encontrar o FQDN do Registrador (ou seja, se o DNS SRV falhar e as configurações manuais não forem definidas).</p></td>
</tr>
<tr class="even">
<td><p>Clientes</p>
<p></p></td>
<td><p>443</p></td>
<td><p>TCP (TLS)</p></td>
<td><p>Usada para tráfego SIP do cliente para o servidor para acesso de usuário externo.</p></td>
</tr>
<tr class="odd">
<td><p>Clientes</p></td>
<td><p>443</p></td>
<td><p>TCP (PSOM/TLS)</p></td>
<td><p>Usada para acesso de usuário externo às sessões de webconferência.</p></td>
</tr>
<tr class="even">
<td><p>Clientes</p></td>
<td><p>443</p></td>
<td><p>TCP (STUN/MSTURN)</p></td>
<td><p>Usada para acesso de usuário externa às sessões de A/V e mídia (TCP).</p></td>
</tr>
<tr class="odd">
<td><p>Clientes</p></td>
<td><p>3478</p></td>
<td><p>UDP (STUN/MSTURN)</p></td>
<td><p>Usada para acesso de usuário externo às sessões de A/V e mídia (UDP).</p></td>
</tr>
<tr class="even">
<td><p>Clientes</p></td>
<td><p>5061</p></td>
<td><p>TCP (MTLS)</p></td>
<td><p>Usada para tráfego SIP do cliente para o servidor para acesso de usuário externo.</p></td>
</tr>
<tr class="odd">
<td><p>Clientes</p></td>
<td><p>6891-6901</p></td>
<td><p>TCP</p></td>
<td><p>Usada para transferência de arquivo entre clientes e antigos clientes do Lync (clientes do Microsoft Office Communications Server 2007 R2, Microsoft Office Communications Server 2007 e do Live Communications Server 2005).</p></td>
</tr>
<tr class="even">
<td><p>Clientes</p></td>
<td><p>1024-65535 *</p></td>
<td><p>TCP/UDP</p></td>
<td><p>Intervalo de porta de áudio (mínimo de 20 portas necessárias).</p></td>
</tr>
<tr class="odd">
<td><p>Clientes</p></td>
<td><p>1024-65535 *</p></td>
<td><p>TCP/UDP</p>
<p></p></td>
<td><p>Intervalo de porta de vídeo (mínimo de 20 portas necessárias).</p></td>
</tr>
<tr class="even">
<td><p>Clientes</p></td>
<td><p>1024-65535 *</p></td>
<td><p>TCP</p></td>
<td><p>Transferência de arquivos ponto a ponto (para transferência de arquivo de conferência, clientes que usam PSOM).</p></td>
</tr>
<tr class="odd">
<td><p>Clientes</p></td>
<td><p>1024-65535 *</p></td>
<td><p>TCP</p></td>
<td><p>Compartilhamento de aplicativos.</p></td>
</tr>
<tr class="even">
<td><p>Telefone de área comum Aastra 6721ip</p>
<p>Telefone de mesa Aastra 6725ip</p>
<p>Telefone IP HP 4110 (telefone de área comum)</p>
<p>Telefone IP HP 4120 (telefone de mesa)</p>
<p>Telefone de área comum IP Polycom CX500</p>
<p>Telefone de mesa IP Polycom CX600</p>
<p>Telefone de mesa IP Polycom CX700</p>
<p>Telefone de conferência IP Polycom CX3000</p></td>
<td><p>67/68</p></td>
<td><p>DHCP</p></td>
<td><p>Usada pelos dispositivos listados para encontrar o certificado do Lync Server, fornecendo FQDN e FQDN do Registrador.</p></td>
</tr>
</tbody>
</table>


**\*** Para configurar portas específicas para esses tipos de mídia, use o cmdlet CsConferencingConfiguration (parâmetros ClientMediaPortRangeEnabled, ClientMediaPort e ClientMediaPortRange).

> [!NOTE]  
> Os programas de configuração para clientes do Lync criam automaticamente as exceções de firewall necessárias para o sistema operacional no computador cliente.

> [!NOTE]  
> As portas usadas para acesso de usuário externo são necessárias para qualquer cenário no qual o cliente precisa atravessar o firewall da organização (por exemplo, quaisquer comunicações externas ou reuniões hospedadas por outras organizações).
