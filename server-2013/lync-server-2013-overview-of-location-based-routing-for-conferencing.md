---
title: Visão geral do roteamento com base no local para conferência
TOCTitle: Visão geral do roteamento com base no local para conferência
ms:assetid: 8b86740e-db95-4304-bb83-64d0cbb91d47
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn362815(v=OCS.15)
ms:contentKeyID: 56270443
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Visão geral do roteamento com base no local para conferência

 

_**Tópico modificado em:** 2015-03-09_

O aplicativo de Conferência com roteamento com base no local fornece às Conferências do Lync um mecanismo para a prevenção de desvio de tarifas (toll bypass) de PSTN. O aplicativo monitora as conferências ativas e impõe restrições de roteamento com base no local de acordo com o local dos usuários do Lync participantes.

O aplicativo de Conferência com roteamento com base no local determines determina se o Roteamento com base no local deve ser imposto em uma reunião do Lync se os seguintes critérios forem cumpridos:

  - O organizador da reunião está habilitado para roteamento com base no local. As restrições de roteamento com base no local serão aplicadas apenas para as conferências que são organizadas por usuários que estão habilitados para roteamento com base no local.

  - Pelo menos um participante da reunião é um ponto de extremidade PSTN. As restrições de roteamento com base no local são aplicáveis ​​apenas para as conferências que incluem pontos de extremidade PSTN.

  - O site da rede onde o gateway PSTN usado para fazer a ligação da conferência com o PSTN está localizado, bem como os locais de rede de onde os organizadores e participantes estão se conectando.

O aplicativo de Conferência com roteamento com base no local impede a participação de usuários do Lync e pontos de extremidade PSTN a partir de diversos sites de rede para a mesma conferência. Se o organizador de uma reunião estiver habilitado para Roteamento com base no local, o aplicativo de Conferência impõe as seguintes restrições:

  - Os pontos de extremidade que podem ingressar em uma reunião do Lync dependem dos parâmetros que já aderiram à conferência e esta restrição é ajustada conforme os pontos de extremidade ingressados saem e novos pontos de extremidade ingressam na conferência. Se os organizadores e participantes estiverem ingressando em uma reunião do Lync a partir do mesmo site de rede, em seguida, um ponto de extremidade PSTN, outro participante do mesmo site de rede, outro participante de um site de rede diferente ou um participante de um site de rede desconhecido são autorizados a ingressar.

  - Se os organizadores e os participantes estiverem ingressando na reunião de diferentes ou desconhecidos sites de rede, um ponto de extremidade PSTN não tem autorização para participar da reunião, se a chamada PSTN ingressar a partir de um tronco SIP habilitado para roteamento com base no local.

  - Se os organizadores e os participantes todos estiverem ingressando na reunião a partir do mesmo site da rede e houver participantes ingressando na mesma reunião a partir do PSTN, um ponto de extremidade do Lync de um site de rede diferente não tem permissão para participar da reunião.

Estas restrições de conferência de Roteamento com base no local estão resumidas na tabela a seguir.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Usuário(s) em uma conferência em um determinado ponto</p></td>
<td><p>Usuário(s) autorizados a ingressar na conferência</p></td>
<td><p>Usuário(s) não autorizados a ingressar na conferência</p></td>
</tr>
<tr class="even">
<td><p>Usuário(s) de cliente VoIP Lync de um site de rede única</p></td>
<td><p>Usuário de cliente VoIP Lync do mesmo site de rede</p>
<p>Usuário de cliente VoIP Lync de um site de rede diferente</p>
<p>Usuário de cliente VoIP Lync de um site de rede desconhecido</p>
<p>Usuário de cliente VoIP Lync federado</p>
<p>Usuário ingressando a partir de um ponto de extremidade PSTN</p></td>
<td><p>Nenhum</p>
<p></p></td>
</tr>
<tr class="odd">
<td><p>Usuário(s) de cliente VoIP Lync a partir de um site de rede desconhecido site</p></td>
<td><p>Usuário de cliente VoIP Lync a partir de qualquer site</p>
<p>Usuário de cliente VoIP Lync a partir de um site desconhecido</p>
<p>Usuário de cliente VoIP Lync federado</p></td>
<td><p>Usuário ingressando por meio de um ponto de extremidade PSTN</p>
<p></p></td>
</tr>
<tr class="even">
<td><p>Usuários de cliente VoIP Lync a partir de sites de rede diferentes</p></td>
<td><p>Usuário de cliente VoIP Lync a partir de qualquer site de rede</p>
<p>Usuário de cliente VoIP Lync a partir de um site de rede desconhecido</p>
<p>Usuário de cliente VoIP Lync federado</p></td>
<td><p>Usuário ingressando por meio de um ponto de extremidade PSTN</p></td>
</tr>
<tr class="odd">
<td><p>Usuário(s) de cliente VoIP Lync a partir de um site de rede única e usuários ingressando por meio de um ponto de extremidade PSTN</p></td>
<td><p>Usuário de cliente VoIP Lync a partir do mesmo site de rede</p>
<p></p></td>
<td><p>Usuário de cliente VoIP Lync de um site de rede diferente</p>
<p>Usuário de cliente VoIP Lync de um site de rede desconhecido</p>
<p>Usuário de cliente VoIP Lync federado</p></td>
</tr>
</tbody>
</table>


Vejamos a seguir características adicionais do aplicativo de Conferência com roteamento com base no local:

  - Quando um usuário não tiver permissão para ingressar em uma conferência dadas as restrições de roteamento com base em local, as chamadas dos usuários à conferência serão rejeitadas e seu cliente Lync irá informar que a chamada não foi concluída ou que foi encerrada.

  - Um ponto de extremidade PSTN ingressando em uma conferência com imposições de roteamento com base no local não será impedido de participar da conferência, independentemente do seu estado, se o ponto de extremidade ingressar através de um tronco que não está habilitado para roteamento com base no local.

  - Um sistema PBX conectado a um Servidor de Mediação por meio de um tronco SIP que não faz chamadas para o PSTN terão as mesmas imposições como usuários do Lync localizados no mesmo site da rede onde o tronco SIP está definida. Por exemplo, um ponto de extremidade PSTN conseguirá ingressar em uma conferência com um usuário de PBX e um usuário do Lync se eles estiverem localizados no mesmo site de rede; caso contrário, o ponto de extremidade PSTN não será autorizado a ingressar na conferência se o usuário de PBX estiver em um site de rede diferente do do usuário do Lync.

