---
title: 'Lync Server 2013: Gerenciamento de usuário no Exchange hospedado'
TOCTitle: Gerenciamento de usuário no Exchange hospedado
ms:assetid: e8723af5-0604-4d7d-bad2-463a9832efb4
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg399037(v=OCS.15)
ms:contentKeyID: 49308461
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Gerenciamento de usuário no Exchange hospedado no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

Para fornecer serviços de caixa postal para os usuários do Lync Server 2013 cujas caixas postais estejam localizadas em um serviço do Exchange hospedado, você deve habilitar as contas de usuário para a caixa postal hospedada.

> [!NOTE]  
> Antes de um usuário do Lync Server 2013 poder ser habilitado para caixa postal hospedada, é preciso implantar uma política de caixa postal hospedada que se aplica à conta de usuário correspondente. A política pode ser global, de site por usuário no escopo, contanto que se aplique ao usuário que você deseja habilitar. Para obter detalhes, consulte <a href="lync-server-2013-hosted-voice-mail-policies.md">Políticas de correio de voz hospedado no Lync Server 2013</a>.

## O atributo msExchUCVoiceMailSettings

O Lync Server 2013 introduz um novo atributo de usuário chamado **msExchUCVoiceMailSettings**, que é criado como parte da preparação de esquema do Active Directory do Lync Server 2013. Esse atributo com múltiplos valores armazena configurações caixa postal compartilhadas pelo Lync Server 2013 e pelo serviço Exchange hospedado.

Em alguns casos, o serviço Exchange hospedado pode definir o valor do atributo msExchUCVoiceMailSettings no processo de habilitação da UM do Exchange ou durante o processo de transferência de caixas postais para um Exchange Server hospedado. Se esse atributo não for definido pelo Exchange, o administrador do Lync Server 2013 deverá defini-lo executando o cmdlet Set-CsUser, conforme descrito anteriormente neste tópico.

Os pares de chave/valor do atributo e seus autores são exibidos na tabela a seguir.

### Os pares de chave/valor do atributo msExchUCVoiceMailSettings

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Valor</th>
<th>Autor:</th>
<th>Significado</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>ExchangeHostedVoiceMail=1</p></td>
<td><p>Exchange</p></td>
<td><p>O usuário foi habilitado para acesso a UM hospedada pelo Exchange Server. O aplicativo de Encaminhamento do UM do Exchange verificará a política de caixa postal do usuário para detalhes de roteamento.</p></td>
</tr>
<tr class="even">
<td><p>ExchangeHostedVoiceMail=0</p></td>
<td><p>Exchange</p></td>
<td><p>O usuário foi desabilitado para acesso a UM hospedada pelo Exchange Server.</p></td>
</tr>
<tr class="odd">
<td><p>CsHostedVoiceMail=1</p></td>
<td><p>Lync Server</p></td>
<td><p>O usuário foi habilitado para acesso a UM hospedada pelo Lync Server 2013. O aplicativo ExUM Routing do Lync Server 2013 verificará a política de caixa postal do usuário para detalhes de roteamento.</p></td>
</tr>
<tr class="even">
<td><p>CsHostedVoiceMail=0</p></td>
<td><p>Lync Server</p></td>
<td><p>O usuário foi desabilitado para acesso a UM hospedada pelo Lync Server 2013.</p></td>
</tr>
</tbody>
</table>


> [!NOTE]  
> Se o atributo já tiver valores diferentes de um dos pares de chave/valor do Lync Server 2013 (CSHostedVoiceMail=0 ou CSHostedVoiceMail=1), um aviso indicará que o atributo pode ser gerenciado por um aplicativo diferente. Por exemplo, um aviso é exibido se o par de chave/valor ExchangeHostedVoiceMail=0 ou ExchangeHostedVoiceMail=1 já estiver presente. Nesse caso, é possível alterar o valor editando-o no Active Directory ou executar o seguinte cmdlet para definir o valor como nulo:<br />Set-CsUser -identity user -HostedVoicemail $null

## Habilitando os usuários para caixa postal hospedada

Para habilitar o roteamento das chamadas de caixa postal de um usuário para a UM do Exchange hospedada, é necessário executar o cmdlet Set-CsUser a fim de definir o valor do parâmetro *HostedVoiceMail* . Esse parâmetro também sinaliza o Lync Server 2013 a acender o indicador “caixa postal de chamada”.

  - O exemplo a seguir habilita a conta de usuário de Pilar Ackerman para caixa postal hospedada:
    
        Set-CsUser -Identity "Pilar Ackerman" -HostedVoiceMail $True
    
    O cmdlet verifica se uma política de caixa postal hospedada (global, nível de site ou por usuário) se aplica a esse usuário. Se nenhuma política for aplicada, o cmdlet falhará.

  - O exemplo a seguir desabilita a conta de usuário de Pilar Ackerman para caixa postal hospedada:
    
        Set-CsUser -Identity "Pilar Ackerman" -HostedVoiceMail $False
    
    O cmdlet verifica se uma política de caixa postal hospedada (global, nível de site ou por usuário) se aplica a esse usuário. Se uma política se aplicar, o cmdlet falhará.

Para obter detalhes sobre como usar o cmdlet Set-CsUser, consulte a documentação do Shell de Gerenciamento do Lync Server.

