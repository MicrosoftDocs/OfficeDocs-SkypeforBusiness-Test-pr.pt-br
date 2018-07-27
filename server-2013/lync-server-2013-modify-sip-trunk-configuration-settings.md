---
title: Modificar as Configurações do Tronco SIP no Lync Server 2013
TOCTitle: Modificar as Configurações do Tronco SIP no Lync Server 2013
ms:assetid: 7d68b09c-9ea0-43bd-997c-df887869d607
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ688104(v=OCS.15)
ms:contentKeyID: 49886277
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Modificar as Configurações do Tronco SIP no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

As configurações do tronco SIP definem a relação e e as capacidades entre um Servidor de Mediação e o gateway da PSTN (rede telefônica pública comutada), um IP-PBX ou SBC (Controlador de Borda de Sessão) no provedor de serviços. Essas configurações fazem como especificado:

  - O bypass de mídia deve ser habilitado nos troncos.

  - As condições sob as quais os pacotes de RTCP são enviadas.

  - Se a encriptação do protocolo a tempo real (SRTP) é ou não segura é exigida em cada tronco.

Ao instalar Microsoft Lync Server 2013, uma coleção global de configurações do tronco SIP é criada. Além disso, os administradores podem criar coleções de configurações personalizadas no escopo do local ou no escopo do serviço (somente para o serviço de gateway PSTN). Quaisquer dessas coleções podem ser modificadas posteriormente usando Painel de Controle do Lync Server ou Windows PowerShell.

Ao modificar a configuração do tronco SIP usando Painel de Controle do Lync Server, as opções a seguir estão disponíveis:


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Configuração da IU</th>
<th>Parâmetro PowerShell</th>
<th>Descrição</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Nome</p></td>
<td><p>Identidade</p></td>
<td><p>Identificador exclusivo para a coleção. Esta propriedade é somente leitura; não é possível modificar a Identidade de uma coleção de configurações do tronco.</p></td>
</tr>
<tr class="even">
<td><p>Descrição</p></td>
<td><p>Descrição</p></td>
<td><p>Fornece uma forma para os administradores armazenarem informações sobre as configurações (por exemplo, o motivo da configuração do tronco).</p></td>
</tr>
<tr class="odd">
<td><p>Máximo de diálogos iniciais suportados</p></td>
<td><p>MaxEarlyDialogs</p></td>
<td><p>O número máximo de respostas bifurcadas que um Gateway PSTN, IP-PBX ou SBC no Provedor de serviços pode receber em resposta a um convite que ele enviou ao Servidor de mediação.</p></td>
</tr>
<tr class="even">
<td><p>Nível de suporte de criptografia</p></td>
<td><p>SRTPMode</p></td>
<td><p>Indica o nível de suporte para proteção do tráfego de mídia entre o Servidor de Medicação e o Gateway de PSTN, IP-PBX ou SBC no provedor de serviços. Para casos de bypass de mídia, esse valor deve ser compatível com a configuração EncryptionLevel na configuração de mídia. A configuração de mídia é definida usando <a href="https://docs.microsoft.com/en-us/powershell/module/skype/New-CsMediaConfiguration">New-CsMediaConfiguration</a> and <a href="https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsMediaConfiguration">Set-CsMediaConfiguration</a> cmdlets.</p>
<p>Os valores permitidos são:</p><ul><li><p>- Obrigatório: Deve se utilizar a criptografia SRTP.</p></li><li><p>- Optional: O SRTP será utilizado se o gateway lhe fornecer apoio.</p></li><li><p>Não suportado: A encriptação de SRTP não é suportada e, portanto, não será usada.</p></li></ul>
<p>SRTPMode é usado apenas se o gateway estiver configurado para usar a Segurança da Camada de Transporte (TLS). Se o gateway estiver configurado com o Protocolo de Controle de Transmissão (TCP) como transporte, SRTPMode será internamente definido como NotSupported.</p></td>
</tr>
<tr class="odd">
<td><p>Suporte</p></td>
<td><p>Enable3pccRefer</p>
<p>EnableReferSupport</p></td>
<td><p>Se definido como <strong>Habilitar endio ao gateway</strong>, indica que o tronco suporta receber solicitações de Refer do Servidor de Mediação.</p>
<p>Se definido como <strong>Habilitar refer usando controle de chamada terceirizado</strong>, indica que o protocolo 3pcc pode ser usado para permitir que chamadas transferidas pulem o local host. 3pcc também é conhecido como &quot;controle terceirizado&quot; e ocorre quando um terceiro é usado para conectar dois chamadores (por exemplo, um operados conectando a chamada da pessoa A à pessoa B).</p></td>
</tr>
<tr class="even">
<td><p>Habilitar bypass de mídia</p></td>
<td><p>EnableBypass</p></td>
<td><p>Selecione a opção <strong>Habilitar bypass de mídia</strong> se você deseja que que a mídia desvie do Servidor de Mediação para processamento pelo ponto do tronco.</p></td>
</tr>
<tr class="odd">
<td><p>Processamento centralizado de mídia</p></td>
<td><p>ConcentratedTopology</p></td>
<td><p>Indica se é um ponto conhecido de término de mídia (Um exemplo de ponto de terminação de mídia conhecido seria um Gateway PSTN, em que a terminação de mídia possui o mesmo IP que a terminação de sinalização.)</p></td>
</tr>
<tr class="even">
<td><p>Habilitar RTP com trava</p></td>
<td><p>EnableRTPLatching</p></td>
<td><p>Indica se os troncos SIP suportam ou não trava de RTP. Trava de RTP é uma tecnologia que habilita a conectividade de RTP/RTCP por dispositivo NAT (conversão de endereço de rede) ou firewall.</p></td>
</tr>
<tr class="odd">
<td><p>Habilitar histórico de encaminhamento de chamada</p></td>
<td><p>ForwardCallHistory</p></td>
<td><p>Indica se as informações de histórico de chamada serão encaminhadas pelo tronco.</p></td>
</tr>
<tr class="even">
<td><p>Habilitar dados de encaminhamento P-Asserted-Identity</p></td>
<td><p>ForwardPAI</p></td>
<td><p>Indica se o header de P-Asserted-Identity (PAI) será encaminhado junto com a chamada. O header PAI oferece uma forma de verificar a identidade do chamador.</p></td>
</tr>
<tr class="odd">
<td><p>Habilitar timer de failover do roteamento de saída</p></td>
<td><p>EnableFastFailoverTimer</p></td>
<td><p>Indica se chamadas de saída não atendidas pelo gateway em 10 segundos serão roteadas ao próximo tronco disponível; se não houver troncos adicionais, a chamada cairá automaticamente. Em uma empresa com redes e respostas de gateway lentas, que poderia resultar em chamadas desligadas desnecessariamente.</p></td>
</tr>
<tr class="even">
<td><p>Uso associado de PSTNsages</p></td>
<td><p>PSTNUsages</p></td>
<td><p>Coleção de usos de PSTN atribuídos ao tronco.</p></td>
</tr>
<tr class="odd">
<td><p>Número convertido para testar</p></td>
<td><p>N/D</p></td>
<td><p>Número de telefone que pode ser usado para um teste ad hoc de configurações do tronco.</p></td>
</tr>
<tr class="even">
<td><p>Regras de conversão associadas</p></td>
<td><p>OutboundTranslationRulesList</p></td>
<td><p>Coleção de regras de conversão de números de telefone que se aplicam a chamadas tratadas pelo Roteamento de saída (chamadas roteadas para destinos de PBX ou PSTN).</p></td>
</tr>
<tr class="odd">
<td><p>Regras de conversão do número chamado</p></td>
<td><p>OutboundCallingNumberTranslationRulesList</p></td>
<td><p>Coleção de regras de conversão do número de chamada de saída atribuído ao tronco.</p></td>
</tr>
<tr class="even">
<td><p>Número de telefone a ser de testado.</p></td>
<td><p>N/D</p></td>
<td><p>Número de telefone que pode ser usado para um teste ad hoc das regras de conversão.</p></td>
</tr>
<tr class="odd">
<td><p>Número de chamada</p></td>
<td><p>N/D</p></td>
<td><p>Indica que o número de telefone a ser testado é o número do chamador.</p></td>
</tr>
<tr class="even">
<td><p>Número chamado</p></td>
<td><p>N/D</p></td>
<td><p>Indica que o número de telefone a ser testado é o número da pessoa sendo chamada.</p></td>
</tr>
</tbody>
</table>


> [!NOTE]  
> Os Lync Server cmdlets CsTrunkConfiguration suportam propriedades adicionais não exibidas em Painel de Controle do Lync Server. Para mais informações, veja o tópico de ajuda para <a href="https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsTrunkConfiguration">Set-CsTrunkConfiguration</a> cmdlet.

## Modificar as Configurações do Tronco SIP Usando Painel de Controle do Lync Server

1.  Em Painel de Controle do Lync Server, clique em **Roteamento de voz** e em **Configuração de Tronco**.

2.  Na guia **Configuração de Tronco**, clique duas vezes nas configurações do tronco a ser modificado. Observe que é possível editar somente uma coleção de configurações por vez. Se quiser fazer as mesmas alterações em múltiplas coleções, use Windows PowerShell.

3.  No diálogo E**ditar Configuração do Tronco**, faça as seleções apropriadas e clique em **OK**.

4.  A propriedade **Estado** da coleção será atualizada para **Não vinculado**. Para vincular as alterações e excluir a coleção, clique em **Vincular** e em **Vincular tudo**.

5.  Na caixa de diálogo **Configurações de Voz Não Vinculadas**, clique em **OK**.

6.  Na caixa de diálogo **Painel de Controle do Microsoft Lync Server 2013**, clique em **OK**.

