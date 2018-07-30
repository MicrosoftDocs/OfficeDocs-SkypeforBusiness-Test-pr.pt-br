---
title: Cria um novo conjunto de definições de configuração de tronco no Lync Server 2013
TOCTitle: Cria um novo conjunto de definições de configuração de tronco no Lync Server 2013
ms:assetid: 4ebd710c-38cd-4cff-9a45-df029d424580
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ688054(v=OCS.15)
ms:contentKeyID: 49886200
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Cria um novo conjunto de definições de configuração de tronco no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

As definições de configuração do tronco SIP definem o relacionamento e as capacidades entre um Servidor de Mediação e um gateway de PSTN (Rede Telefônica Pública Comutada), um IP-PBX ou um SBC (Controlador de Borda da Sessão) no provedor de serviços. Essas definições realizam funções como especificar:

  - Se o desvio de mídia deve ser ativado nos troncos.

  - As condições nas quais os pacotes RTCP (Protocolo de Controle de Transporte em Tempo Real) são enviados.

  - Se a criptografia SRTP (Protocolo em tempo real seguro) é necessária em cada tronco.

Quando você instalar o Microsoft Lync Server 2013, um conjunto global de definições de configuração do tronco SIP será criado. Além disso, os administradores podem criar conjuntos de definições personalizados no escopo do site ou no escopo do serviço (apenas para o serviço de gateway da PSTN).

Ao criar definições de configuração de tronco SIP usando Painel de Controle do Lync Server, as seguintes opções são disponibilizadas a você:


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Configuração da UI</th>
<th>Parâmetro PowerShell</th>
<th>Descrição</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Nome</p></td>
<td><p>Identidade</p></td>
<td><p>Identificador único para o conjunto. Essa propriedade é de somente leitura; você não pode modificar a Identidade do conjunto das definições de configuração do tronco.</p></td>
</tr>
<tr class="even">
<td><p>Descrição</p></td>
<td><p>Descrição</p></td>
<td><p>Oferece uma maneira de os administradores armazenarem informações adicionais sobre as definições (por exemplo, o propósito da configuração de tronco).</p></td>
</tr>
<tr class="odd">
<td><p>Máximo de caixas de diálogo iniciais com suporte</p></td>
<td><p>MaxEarlyDialogs</p></td>
<td><p>O número máximo de respostas bifurcadas que um Gateway PSTN, IP-PBX ou SBC no Provedor de serviços pode receber em resposta a um convite que ele enviou ao Servidor de mediação.</p></td>
</tr>
<tr class="even">
<td><p>Nível de suporte de criptografia</p></td>
<td><p>SRTPMode</p></td>
<td><p>Indica o nível de suporte para proteger o tráfego de mídia entre o Servidor de Mediação e o Gateway da PSTN, IP-PBX ou SBC no provedor do serviço. Nos casos de desvio de mídia, este valor deve ser compatível com a definição EncryptionLevel da configuração de mídia. A configuração de mídia é ajustada utilizando-se os cmdlets <a href="https://docs.microsoft.com/en-us/powershell/module/skype/New-CsMediaConfiguration">New-CsMediaConfiguration</a> e <a href="https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsMediaConfiguration">Set-CsMediaConfiguration</a>.</p>
<p>Os valores permitidos são:</p><ul><li><p>Requeridos: criptografia do SRTP deve ser usada.</p></li><li><p>Opcional: o SRTP será usado caso o gateway o suporte.</p></li><li><p>Não suportado: a criptografia do SRTP não é suportada, por tanto não será usada.</p></li></ul>
<p>SRTPMode é usado apenas se o gateway estiver configurado para usar a Segurança da Camada de Transporte (TLS). Se o gateway estiver configurado com o Protocolo de Controle de Transmissão (TCP) como transporte, SRTPMode será internamente definido como NotSupported.</p></td>
</tr>
<tr class="odd">
<td><p>Suporte de referência</p></td>
<td><p>Enable3pccRefer</p>
<p>EnableReferSupport</p></td>
<td><p>Se for definido para <strong>Habilitar envio de referência ao gateway</strong>, indica que o tronco suporta o recebimento de solicitações de Referência vindas do Servidor de Mediação.</p>
<p>Se for definido para <strong>Habilitar referência usando o controle de chamada de terceiros</strong>, indica que o protocolo 3pcc pode ser usado para permitir chamadas transferidas para desviar o site hospedado. O 3pcc também é conhecido como &quot;controle de terceiros&quot; e ocorre quando um terceiro é usado para conectar dois chamadores ( por exemplo, um operador estabelecendo uma chamada da pessoa A para a pessoa B).</p></td>
</tr>
<tr class="even">
<td><p>Habilitar Bypass de mídia</p></td>
<td><p>EnableBypass</p></td>
<td><p>Indica se um desvio de mídia está habilitado para esse tronco. Os desvios de mídia podem ser habilitados somente se <strong>Processamento de mídia centralizado</strong> também estiver habilitado.</p></td>
</tr>
<tr class="odd">
<td><p>Processamento de mídia centralizado</p></td>
<td><p>ConcentratedTopology</p></td>
<td><p>Indica se existe um ponto conhecido de encerramento da mídia. (Um exemplo de ponto de terminação de mídia conhecido seria um gateway PSTN, em que a terminação de mídia possui o mesmo IP que a terminação de sinalização.)</p></td>
</tr>
<tr class="even">
<td><p>Habilitar engatador RTP</p></td>
<td><p>EnableRTPLatching</p></td>
<td><p>Indica se o tronco SIP suporta o engatador RTP. O engatador RTP é uma tecnologia que habilita a conectividade RTP/RTCP através de um dispositivo NAT (conversor de endereço de rede) ou firewall.</p></td>
</tr>
<tr class="odd">
<td><p>Habilitar histórico de encaminhamento de chamada</p></td>
<td><p>ForwardCallHistory</p></td>
<td><p>Indica se as informações de histórico de chamadas serão encaminhadas através do tronco.</p></td>
</tr>
<tr class="even">
<td><p>Habilitar encaminhamento de dados P-Asserted-Identity</p></td>
<td><p>ForwardPAI</p></td>
<td><p>Indica se o cabeçalho P-Asserted-Identity (PAI) será encaminhado junto com a chamada. O cabeçalho PAI oferece uma maneira de verificar a identidade do chamador.</p></td>
</tr>
<tr class="odd">
<td><p>Habilitar timer de failover do roteamento de saída</p></td>
<td><p>EnableFastFailoverTimer</p></td>
<td><p>Indica se as chamadas de saída que não foram respondidas pelo gateway em 10 segundos serão roteadas ao próximo tronco disponível; caso não haja troncos adicionais, a chamada será automaticamente descartada. Em organizações com respostas de gateway e redes lentas que podem resultar em chamadas desnecessariamente descartadas.</p></td>
</tr>
<tr class="even">
<td><p>Usos da PSTN associadas</p></td>
<td><p>PSTNUsages</p></td>
<td><p>Os conjuntos de usos da PSTN atribuídos a um tronco.</p></td>
</tr>
<tr class="odd">
<td><p>Número convertido para fazer um teste</p></td>
<td><p>N/A</p></td>
<td><p>Número de telefone que pode ser usado para realizar um teste ad hoc das definições de configuração do tronco.</p></td>
</tr>
<tr class="even">
<td><p>Regras de conversão associadas</p></td>
<td><p>OutboundTranslationRulesList</p></td>
<td><p>Conjunto de conversões de números de telefones que se aplicam a chamadas manipuladas pelo Roteamento de Saída (chamadas roteadas a destinos PBX ou PSTN).</p></td>
</tr>
<tr class="odd">
<td><p>Regras de conversão de números chamados</p></td>
<td><p>OutboundCallingNumberTranslationRulesList</p></td>
<td><p>Conjunto de regras de conversão de números chamados de saída atribuído a um tronco.</p></td>
</tr>
<tr class="even">
<td><p>Número de telefone de teste</p></td>
<td><p>N/A</p></td>
<td><p>Número de telefone que pode ser usado para realizar um teste ad hoc das regras de conversão.</p></td>
</tr>
<tr class="odd">
<td><p>Número de chamada</p></td>
<td><p>N/A</p></td>
<td><p>Indica que o número de telefone de teste é o número de telefone do chamador.</p></td>
</tr>
<tr class="even">
<td><p>Número chamado</p></td>
<td><p>N/A</p></td>
<td><p>Indica que o número de telefone de teste é o número de telefone da pessoa que recebe a chamada.</p></td>
</tr>
</tbody>
</table>


> [!NOTE]  
> O cmdlets Lync Server CsTrunkConfiguration suporta propriedades adicionais não exibidas em Painel de Controle do Lync Server. Para obter mais informações, consulte o tópico da Ajuda do cmdlets <a href="https://docs.microsoft.com/en-us/powershell/module/skype/New-CsTrunkConfiguration">New-CsTrunkConfiguration</a> cmdlet.

## Criação de nova definição de configuração de tronco usando o Painel de Controle do Lync Server

1.  Em Painel de Controle do Lync Server, clique em **Roteamento de Voz** e, em seguida, clique em **Configuração de Tronco**.

2.  Na guia **Configuração de Tronco** , clique em **Novo** e, em seguida, clique em **Tronco do site** para criar a nova definição no escopo do site, ou **Tronco do pool** para criar as novas definições no escopo do serviço.

3.  Na caixa de diálogo **Selecionar um site** ou **Selecionar um serviço** (a caixa de diálogo que aparece depende se você está criando definições de escopo do site ou de escopo do serviço) selecione um local para a nova definição de configuração e, em seguida, clique em **OK**. Se a caixa de diálogo está em branco, significa que não há lugar para criar uma nova definição; por exemplo, se a caixa de diálogo **Selecionar um site** está em branco, significa que todos os sites já possuem um conjunto de sites de configuração de tronco atribuído, e cada site (e cada serviço) pode hospedar apenas um conjunto. Nesse caso, você pode tanto excluir o conjunto existente e criar um novo conjunto ou simplesmente modificar o conjunto existente.

4.  Na caixa de diálogo **Nova configuração de tronco**, faça as seleções apropriadas e clique em **OK**.

5.  A propriedade **Estado** do conjunto será atualizada para **Não confirmado**. Para confirmar as alterações e para excluir o conjunto, clique em **Confirmar** e, em seguida, clique em **Confirmar tudo**.

6.  Na caixa de diálogo **Definições de Configuração de Voz Não Confirmadas**, clique em **OK**.

7.  Na caixa de diálogo **Painel de Controle do Lync Server 2013 da Microsoft** clique em **OK**.

