---
title: 'Lync Server 2013: Visão geral dos tipos de endereços IP'
TOCTitle: Visão geral dos tipos de endereços IP para Lync Server
ms:assetid: ee9a695f-5cf5-441e-94fb-6adeca50e8d8
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205363(v=OCS.15)
ms:contentKeyID: 49308524
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Visão geral dos tipos de endereços IP para Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

Você tem três opções ao configurar endereços IP no Lync Server 2013. Você pode configurar o Lync Server 2013 para oferecer suporte somente a IP versão 4 (IPv4), somente o IP versão 6 (IPv6), ou a uma combinação dos dois (conhecido como uma *pilha dupla* ). Vários problemas devem ser considerados para cada tipo de configuração:

  - **Somente IPv4**   O IPv6 foi criado porque os endereços IPv4 estão acabando. No fim das contas, o IPv6 será completamente suportado em todo o mundo, mas no momento, várias empresas e dispositivos aos quais sua empresa pode precisar se comunicar ainda não oferecem suporte ao IPv6, e poderão não oferecer por algum tempo. Uma configuração somente IPv4 ajudará a garantir que a sua implementação do Lync Server possa se comunicar com a maioria dos dispositivos existentes.

  - **Somente IPv6**   Por outro lado, uma implementação completamente IPv6, neste momento, excluirá a comunicação com vários dispositivos existentes.

  - **Pilha dupla**   A pilha dupla é uma rede em que estão ativados endereços IPv4 e IPv6. Esta configuração é suportada no Lync Server 2013 porque, na maioria dos casos, a transição de IPv4 completo para IPv6 completo levará vários anos.

As seções a seguir destacam a compatibilidade entre essas três configurações e os vários recursos do Lync Server.

> [!NOTE]  
> Configuração de cliente ou servidor com somente IPv6 é suportada apenas para fins de validação ou utilização em laboratório. A configuração somente IPv6 não é suportada na implantação de produção.

## Registro de cliente


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Extremidade de rede de cliente</th>
<th>Rede de servidor</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>IPv4</p></td>
<td><p>IPv4</p></td>
</tr>
<tr class="even">
<td><p>IPv4</p></td>
<td><p>Pilha dupla</p></td>
</tr>
<tr class="odd">
<td><p>Pilha dupla</p></td>
<td><p>IPv4</p></td>
</tr>
<tr class="even">
<td><p>Pilha dupla</p></td>
<td><p>Pilha dupla</p></td>
</tr>
<tr class="odd">
<td><p>Pilha dupla</p></td>
<td><p>IPv6</p></td>
</tr>
<tr class="even">
<td><p>IPv6</p></td>
<td><p>Pilha dupla</p></td>
</tr>
<tr class="odd">
<td><p>IPv6</p></td>
<td><p>IPv6</p></td>
</tr>
</tbody>
</table>


## Cliente ponto a ponto

As comunicações ponto a ponto incluem áudio, áudio/vídeo, compartilhamento de aplicativos e transferência de arquivos. Após o registro bem sucedido de ambos os clientes, as combinações a seguir são suportadas.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Extremidade de cliente 1</th>
<th>Extremidade de cliente 2</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>IPv4</p></td>
<td><p>IPv4</p></td>
</tr>
<tr class="even">
<td><p>IPv4</p></td>
<td><p>Pilha dupla</p></td>
</tr>
<tr class="odd">
<td><p>Pilha dupla</p></td>
<td><p>Pilha dupla</p></td>
</tr>
<tr class="even">
<td><p>IPv6</p></td>
<td><p>Pilha dupla</p></td>
</tr>
<tr class="odd">
<td><p>IPv6</p></td>
<td><p>IPv6</p></td>
</tr>
</tbody>
</table>


## Conferência

As conferências incluem áudio/vídeo, compartilhamento de aplicativos e colaboração de dados (uso de quadros interativos e compartilhamento de arquivos).


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Extremidade de rede de cliente</th>
<th>Rede de servidor</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>IPv4</p></td>
<td><p>IPv4</p></td>
</tr>
<tr class="even">
<td><p>IPv4</p></td>
<td><p>Pilha dupla</p></td>
</tr>
<tr class="odd">
<td><p>Pilha dupla</p></td>
<td><p>IPv4</p></td>
</tr>
<tr class="even">
<td><p>Pilha dupla</p></td>
<td><p>Pilha dupla</p></td>
</tr>
<tr class="odd">
<td><p>Pilha dupla</p></td>
<td><p>IPv6</p></td>
</tr>
<tr class="even">
<td><p>IPv6</p></td>
<td><p>Pilha dupla</p></td>
</tr>
<tr class="odd">
<td><p>IPv6</p></td>
<td><p>IPv6</p></td>
</tr>
</tbody>
</table>


## Servidor de Mediação/PSTN

Lync Server 2013 não oferece suporte ao desvio de mídia para camadas de redes de telefone públicas comutadas (PSTN) se o tráfego ocorre através de uma interface IPv6. Se o desvio de mídia é necessário, recomendamos que o gateway PSTN seja configurado para IPv4.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Interface principal*</th>
<th>Interface PSTN (no Servidor de Mediação)</th>
<th>Configuração do gateway PSTN</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>IPv4</p></td>
<td><p>Pilha dupla</p></td>
<td><p>IPv4</p></td>
</tr>
<tr class="even">
<td><p>Pilha dupla</p></td>
<td><p>Pilha dupla</p></td>
<td><p>IPv4</p></td>
</tr>
<tr class="odd">
<td><p>Pilha dupla</p></td>
<td><p>Pilha dupla</p></td>
<td><p>IPv6</p></td>
</tr>
</tbody>
</table>


\* A interface principal é a interface que se comunica com os componentes do Lync Server.

## Comunicações ponto a ponto de usuário remoto

As comunicações ponto a ponto com usuários remotos incluem mensagens instantâneas, áudio/vídeo, compartilhamento de aplicativos e transferência de arquivos.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Rede de usuários remotos</th>
<th>Servidor de borda (Borda externa)</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>IPv4</p></td>
<td><p>IPv4</p></td>
</tr>
<tr class="even">
<td><p>Pilha dupla</p></td>
<td><p>IPv4</p></td>
</tr>
<tr class="odd">
<td><p>Pilha dupla</p></td>
<td><p>Pilha dupla</p></td>
</tr>
<tr class="even">
<td><p>IPv6</p></td>
<td><p>Pilha dupla</p></td>
</tr>
<tr class="odd">
<td><p>IPv6</p></td>
<td><p>IPv6</p></td>
</tr>
</tbody>
</table>


## Configuração do pool de Front End e do pool do Servidor de Borda

A tabela a seguir mostra a matriz de suporte entre o pool Servidor Front-End e o pool interno Servidor de Borda.

### Matriz do Pool de Front End e do Pool de Borda (Borda interna)

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p></p></td>
<td><p><strong>Pool de borda: IPv4</strong></p></td>
<td><p><strong>Pool de borda: Pilha dupla</strong></p></td>
<td><p><strong>Pool de borda: IPv6</strong></p></td>
</tr>
<tr class="even">
<td><p><strong>Pools de Front-End: IPv4</strong></p></td>
<td><p>Sim</p></td>
<td><p>Sim</p></td>
<td><p>Não</p></td>
</tr>
<tr class="odd">
<td><p><strong>Pool de Front End: Pilha dupla</strong></p></td>
<td><p>Sim</p></td>
<td><p>Sim</p></td>
<td><p>Não</p></td>
</tr>
<tr class="even">
<td><p><strong>Pool de Front End: IPv6</strong></p></td>
<td><p>Não</p></td>
<td><p>Não</p></td>
<td><p>Sim*</p></td>
</tr>
</tbody>
</table>


\* Use essa combinação somente em um ambiente de laboratório.

A tabela a seguir descreve a matriz de combinações suportadas das interfaces de borda interna e externa.

### Matriz do Pool de borda (Borda interna) e do Pool de borda (Borda externa)

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p></p></td>
<td><p><strong>Pool de borda (Borda externa): IPv4</strong></p></td>
<td><p><strong>Pool de borda (Borda externa): Pilha dupla</strong></p></td>
<td><p><strong>Pool de borda (Borda externa): IPv6</strong></p></td>
</tr>
<tr class="even">
<td><p><strong>Pool de borda (Borda interna): IPv4</strong></p></td>
<td><p>Sim</p></td>
<td><p>Sim</p></td>
<td><p>Não</p></td>
</tr>
<tr class="odd">
<td><p><strong>Pool de borda (Borda interna): Pilha dupla</strong></p></td>
<td><p>Não</p></td>
<td><p>Sim</p></td>
<td><p>Não</p></td>
</tr>
<tr class="even">
<td><p><strong>Pool de borda (Borda interna): IPv6</strong></p></td>
<td><p>Não</p></td>
<td><p>Não</p></td>
<td><p>Sim*</p></td>
</tr>
</tbody>
</table>


\* Use essa combinação somente em um ambiente de laboratório.

## Suporte avançado do Enterprise Voice para IPv6

Implantações que incluem controle de admissão de chamadas (CAC), Enhanced 9-1-1 (E9-1-1) ou passagem livre de mídia devem ser configurados como implementações somente IPv4 ou de pilha dupla.

> [!NOTE]  
> Em uma implantação de pilha dupla, mesmo que um cliente Lync se conecte a um Lync Server usando IPv6, o Lync fará o possível para mapear um endereço IPv4 apropriado para oferecer suporte ao E9-1-1.

O Serviço de Informações de Local com endereços IPv6 não é suportado.

O Unified Messaging (UM) do Exchange não suporta IPv6. Para o UM do Exchange, certifique-se de que a resolução do DNS não retorna um endereço IPv6. A utilização de IPv6 pode provocar falhas ao enviar chamadas para correios de voz.

## Suporte de outros recursos do Lync Server 2013 ao IPv6

Além dos recursos e componentes mencionados anteriormente, o Lync Server 2013 suporta IPv6 para os seguintes recursos:

  - **Chat Persistente**
    
    O IPv6 é configurado para o Chat Persistente utilizando o Construtor de Topologias. Para obter detalhes sobre como configurar um Chat Persistente, consulte a documentação de Implantação do Servidor de Chat Persistente.

  - **Relatórios de CDR (registro de detalhes de chamada) e QoE (Qualidade de experiência)**
    
    Os relatórios de monitoramento incluem o endereço IP conforme é armazenado no banco de dados do Servidor de Monitoramento, independente de ser do tipo IPv4 ou IPv6.

