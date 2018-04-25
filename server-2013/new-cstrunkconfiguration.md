---
title: New-CsTrunkConfiguration
TOCTitle: New-CsTrunkConfiguration
ms:assetid: f3958f86-3313-4929-9f9d-f796a2669aea
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg413021(v=OCS.15)
ms:contentKeyID: 49308600
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsTrunkConfiguration

 

_**Tópico modificado em:** 2015-03-09_

Cria uma nova configuração de tronco que descreve as definições de uma entidade de mesmo nível de tronco, como um gateway de rede telefônica pública comutada (PSTN), Central privada de comutação de (PBX) IP ou Controlador de borda de sessão (SBC) no provedor de serviços. Este cmdlet foi introduzido no Lync Server 2010.

## Sintaxe

    New-CsTrunkConfiguration -Identity <XdsIdentity> [-ConcentratedTopology <$true | $false>] [-Confirm [<SwitchParameter>]] [-Description <String>] [-Enable3pccRefer <$true | $false>] [-EnableBypass <$true | $false>] [-EnableFastFailoverTimer <$true | $false>] [-EnableLocationRestriction <$true | $false>] [-EnableMobileTrunkSupport <$true | $false>] [-EnableOnlineVoice <$true | $false>] [-EnablePIDFLOSupport <$true | $false>] [-EnableReferSupport <$true | $false>] [-EnableRTPLatching <$true | $false>] [-EnableSessionTimer <$true | $false>] [-EnableSignalBoost <$true | $false>] [-Force <SwitchParameter>] [-ForwardCallHistory <$true | $false>] [-ForwardPAI <$true | $false>] [-InMemory <SwitchParameter>] [-MaxEarlyDialogs <UInt32>] [-NetworkSiteID <String>] [-OutboundCallingNumberTranslationRulesList <PSListModifier>] [-OutboundTranslationRulesList <PSListModifier>] [-PstnUsages <PSListModifier>] [-RemovePlusFromUri <$true | $false>] [-RTCPActiveCalls <$true | $false>] [-RTCPCallsOnHold <$true | $false>] [-SipResponseCodeTranslationRulesList <PSListModifier>] [-SRTPMode <Required | Optional | NotSupported>] [-WhatIf [<SwitchParameter>]]

## Exemplos

## EXEMPLO 1

Esse exemplo cria uma nova configuração do tronco cuja Identidade for site:Redmond. As demais propriedades dessa nova configuração serão preenchidas com os valores padrão.

    New-CsTrunkConfiguration -Identity site:Redmond

## EXEMPLO 2

Esse exemplo cria uma nova configuração do tronco cuja Identidade for site:Redmond e habilita o desvio de mídia. O desvio de mídia é habilitado pela atribuição do valor $True ao parâmetro EnableBypass. As demais propriedades dessa nova configuração serão preenchidas com os valores padrão.

    New-CsTrunkConfiguration -Identity site:Redmond -EnableBypass $True

## EXEMPLO 3

Este exemplo cria uma nova configuração de tronco cuja Identidade é site:Redmond e, em seguida, atribui uma nova conversão de saída a esse tronco. A primeira linha do exemplo chama o cmdlet **New-CsTrunkConfiguration** para criar a nova configuração do tronco com as configurações padrão. A segunda linha chama o cmdlet **New-CsOutboundTranslationRule**. Observe o valor atribuído à Identidade: site:Redmond/OTR1. A primeira parte da Identidade (site:Redmond) define o escopo ao qual a regra é aplicada. Esse escopo corresponde à Identidade da nova configuração do tronco, indicando que essa regra será aplicada automaticamente a essa configuração. O escopo é seguido de uma barra (/) e uma cadeia de caracteres, que é simplesmente um nome exclusivo para essa regra (pode haver mais de uma regra por escopo). Depois disso, passamos os valores aos parâmetros Pattern e Translation para definir essa regra.

    New-CsTrunkConfiguration -Identity site:Redmond
    New-CsOutboundTranslationRule -Identity site:Redmond/OTR1 -Pattern '^\+(\d{8})$' -Translation '9$1'

## Descrição detalhada

Utilize esse cmdlet para criar uma nova configuração de tronco que se aplique a entidades de Gateway da PSTN. Cada configuração contém definições específicas de uma entidade de mesmo nível de tronco, como um gateway da PSTN, IP-PBX ou SBC no provedor de serviços. Essas definições configuram aspectos como a habilitação (ou não) do desvio de mídia nesse tronco, o envio (ou não) dos pacotes RTCP sob determinadas condições e a exigência de se efetuar (ou não) a criptografia SRTP (protocolo em tempo real seguro).

Quem pode executar esse cmdlet: Por padrão, membros dos seguintes grupos são autorizados a executar o cmdlet **New-CsTrunkConfiguration** localmente: RTCUniversalServerAdmins. Para retornar uma lista de todas as funções de controle de acesso baseado em função (RBAC) às quais este cmdlet tiver sido atribuído (inclusive qualquer função RBAC personalizada que tiver sido criada por você), execute o seguinte comando no prompt do Windows PowerShell:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsTrunkConfiguration"}

## Parâmetros


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Parâmetro</th>
<th>Obrigatório</th>
<th>Digite</th>
<th>Descrição</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>Identity</em></p></td>
<td><p>Obrigatório</p></td>
<td><p>XdsIdentity</p></td>
<td><p>Um identificador exclusivo que inclui o escopo da configuração de troncos. As configurações de tronco podem ser criadas no escopo de site ou de serviço, no caso de um serviço de gateway da PSTN. (por padrão, já existe uma configuração global, que não pode ser removida ou recriada). Por exemplo, site:Redmond (no escopo de site) ou PstnGateway:Redmond.litwareinc.com (no escopo de serviço).</p></td>
</tr>
<tr class="even">
<td><p><em>ConcentratedTopology</em></p></td>
<td><p>Opcional</p></td>
<td><p>Booliano</p></td>
<td><p>O valor desse parâmetro determina se há um ponto de terminação de mídia conhecido. (Um exemplo de ponto de terminação de mídia conhecido seria um Gateway da PSTN, no qual a terminação de mídia possui o mesmo IP que a terminação de sinalização). Defina esse valor como False, se o tronco não possuir um ponto de terminação de mídia conhecido.</p>
<p>Padrão: True</p></td>
</tr>
<tr class="odd">
<td><p><em>Confirm</em></p></td>
<td><p>Opcional</p></td>
<td><p>SwitchParameter</p></td>
<td><p>Solicita confirmação antes da execução do comando.</p></td>
</tr>
<tr class="even">
<td><p><em>Description</em></p></td>
<td><p>Opcional</p></td>
<td><p>Cadeia de caracteres</p></td>
<td><p>Uma cadeia de caracteres que descreve o propósito da configuração de tronco.</p></td>
</tr>
<tr class="odd">
<td><p><em>Enable3pccRefer</em></p></td>
<td><p>Opcional</p></td>
<td><p>Booliano</p></td>
<td><p>Indica se o protocolo 3pcc pode ser usado para permitir chamadas transferidas a fim de ignorar o site hospedado. 3pcc também é conhecido como &quot;controle de terceiros&quot; e ocorre quando um terceiro é usado para conectar um par de chamadores (por exemplo, um operador fazendo uma chamada da pessoa A para a pessoa B). O método REFER é um método SIP padrão que indica se o destinatário deve entrar em contato com um terceiro usando informações fornecidas pelo remetente. O valor padrão é False ($False).</p></td>
</tr>
<tr class="even">
<td><p><em>EnableBypass</em></p></td>
<td><p>Opcional</p></td>
<td><p>Booliano</p></td>
<td><p>O valor desse parâmetro determina se o desvio de mídia está habilitado nesse tronco. Defina este valor como True, para habilitar o desvio. Observe que, para que o desvio de mídia funcione corretamente, é necessário que determinadas capacidades sejam suportadas pelos gateways da PSTN, SBCs e PBXs, incluindo:</p>
<p>- a capacidade de receber respostas bifurcadas a um Convite.</p>
<p>- É necessário que os clientes do Lync Server e o ponto de terminação de mídia sejam capazes de se comunicarem diretamente, sem precisar passar por um Servidor de Mediação.</p>
<p>- a sub-rede do gateway deve ser definida como estando no mesmo site que a sub-rede do cliente ou, se estiver em um site diferente, os sites não devem ser separados por links WAN com largura de banda limitada.</p>
<p>O desvio de mídia pode ser habilitado apenas sob as seguintes circunstâncias:</p>
<p>- o parâmetro ConcentratedTopology está definido como True</p>
<p>- o parâmetro EnableReferSupport está definido como False, e RTCPActiveCalls e RTCPCallsOnHold estão definidos como False, ou EnableReferSupport está definido como True</p>
<p>Observe que se EnableBypass for True e EnableReferSupport for False, as chamadas de desvio que serão subsequentemente transferidas tornar-se-ão de não-desvio.</p>
<p>Para que o desvio de mídia funcione em um determinado tronco, é necessário que ele esteja habilitado globalmente, assim como para o tronco em questão. Use o cmdlet <strong>New-CsNetworkMediaBypassConfiguration</strong> para habilitar o desvio de mídia globalmente.</p>
<p>Padrão: False</p></td>
</tr>
<tr class="odd">
<td><p><em>EnableFastFailoverTimer</em></p></td>
<td><p>Opcional</p></td>
<td><p>Booliano</p></td>
<td><p>Quando definido como Verdadeiro, as chamadas de saída que não forem respondidas pelo gateway dentro de 10 segundos serão roteadas ao próximo tronco disponível. Caso não haja troncos adicionais, então a chamada será ignorada automaticamente. Em uma organization com respostas lentas de redes e gateway, isso poderia resultar em chamadas sendo ignoradas sem precisar.</p>
<p>O valor padrão é True.</p></td>
</tr>
<tr class="even">
<td><p><em>EnableLocationRestriction</em></p></td>
<td><p>Opcional</p></td>
<td><p>Booliano</p></td>
<td><p>Quando definido como True, o roteamento de voz baseado em local será habilitado para as chamadas que passam pelos troncos SIP gerenciados pela coleção especificada de definições de configuração de tronco SIP. Com o roteamento de voz baseado em local, os locais do usuário que faz a chamada e do que a recebe são levados em consideração quando as chamadas são roteadas. Se esta propriedade estiver definida como True (o valor padrão é False), você deverá definir também a propriedade NetworkSiteId.</p>
<p>Este parâmetro foi introduzido na versão de fevereiro de 2013 do Lync Server 2013.</p></td>
</tr>
<tr class="odd">
<td><p><em>EnableMobileTrunkSupport</em></p></td>
<td><p>Opcional</p></td>
<td><p>Booliano</p></td>
<td><p>Define se o provedor de serviços é uma operadora de telefonia celular.</p>
<p>Padrão: False</p></td>
</tr>
<tr class="even">
<td><p><em>EnableOnlineVoice</em></p></td>
<td><p>Opcional</p></td>
<td><p>Booliano</p></td>
<td><p>Indica se os troncos SIP suportam voz online. Com a voz online, os usuários têm uma conta do Lync Server local, mas suas caixas postais são hospedadas pelo Office 365. O valor padrão é False ($False).</p></td>
</tr>
<tr class="odd">
<td><p><em>EnablePIDFLOSupport</em></p></td>
<td><p>Opcional</p></td>
<td><p>Booliano</p></td>
<td><p>Define se o roteamento ou não de chamadas de emergência será efetuado com o objeto Local de formato de dados de informação de presença (PIDF-LO) no gateway definido. Defina esse parâmetro como True, se as chamadas de emergência tiverem de ser roteadas para um provedor de serviços de emergência certificado. (o local será transmitido com a chamada).</p>
<p>Padrão: False</p></td>
</tr>
<tr class="even">
<td><p><em>EnableReferSupport</em></p></td>
<td><p>Opcional</p></td>
<td><p>Booliano</p></td>
<td><p>Define se esse tronco apoia o recebimento de solicitações de Referência vindas do Servidor de Mediação.</p>
<p>O desvio de mídia pode ser habilitado apenas sob as seguintes circunstâncias:</p>
<p>- o parâmetro ConcentratedTopology está definido como True</p>
<p>- o parâmetro EnableReferSupport está definido como False, e RTCPActiveCalls e RTCPCallsOnHold estão definidos como False, ou EnableReferSupport está definido como True</p>
<p>Observe que se EnableBypass for True e EnableReferSupport for False, as chamadas de desvio que serão subsequentemente transferidas tornar-se-ão de não-desvio.</p>
<p>Padrão: True</p></td>
</tr>
<tr class="odd">
<td><p><em>EnableRTPLatching</em></p></td>
<td><p>Opcional</p></td>
<td><p>Booliano</p></td>
<td><p>Indica se os troncos SIP suportam travamento de RTP. O travamento de RTP é uma tecnologia que permite a conectividade RTP/RTCP por meio de um dispositivo NAT (conversor de endereço de rede) ou firewall. O valor padrão é False ($False).</p></td>
</tr>
<tr class="even">
<td><p><em>EnableSessionTimer</em></p></td>
<td><p>Opcional</p></td>
<td><p>Booliano</p></td>
<td><p>Especifica se o cronômetro da sessão estará habilitado. Os cronômetros de sessão são utilizados para determinar se uma determinada sessão ainda está ativa.</p>
<p>Observe que, mesmo se esse parâmetro for definido como False, os cronômetros de sessão poderão ser aplicáveis, caso a conexão remota possua um cronômetro de sessão habilitado. Nesse caso, o Servidor de Mediação responderá a testes do cronômetro de sessão da entidade remota.</p>
<p>Padrão: False</p></td>
</tr>
<tr class="odd">
<td><p><em>EnableSignalBoost</em></p></td>
<td><p>Opcional</p></td>
<td><p>Booliano</p></td>
<td><p>Quando esse parâmetro for definido como True, o gateway PSTN, IP-PBX ou SBC do provedor de serviço aumentará o volume do áudio nos fluxos de voz que forem enviados aos clientes da Servidor de Mediação ou Lync Server. Se esse valor for definido como False, o áudio será aumentado na Servidor de Mediação (nas chamadas de não-desvio) ou em clientes Lync Server (nas chamadas de desvio).</p>
<p>Padrão: False</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>Opcional</p></td>
<td><p>SwitchParameter</p></td>
<td><p>Suprime qualquer aviso de confirmação que, de outra maneira, seria exibido antes de se realizar as alterações.</p></td>
</tr>
<tr class="odd">
<td><p><em>ForwardCallHistory</em></p></td>
<td><p>Opcional</p></td>
<td><p>Booliano</p></td>
<td><p>Indica se as informações do histórico de chamada serão encaminhadas por meio do tronco. O valor padrão é False ($False).</p></td>
</tr>
<tr class="even">
<td><p><em>ForwardPAI</em></p></td>
<td><p>Opcional</p></td>
<td><p>Booliano</p></td>
<td><p>Indica se o cabeçalho P-Asserted-Identity (PAI) será encaminhado junto com a chamada. O cabeçalho PAI fornece uma forma de verificar a identidade do chamador. O valor padrão é False ($False).</p></td>
</tr>
<tr class="odd">
<td><p><em>InMemory</em></p></td>
<td><p>Opcional</p></td>
<td><p>SwitchParameter</p></td>
<td><p>Cria uma referência de objeto, sem na verdade executar o objeto como uma alteração permanente. Se a saída deste cmdlet for atribuída, chamando-o com este parâmetro a uma variável, você poderá realizar alterações às propriedades da referência do objeto e executar estas alterações, chamando-se o cmdlet coincidente Set- deste cmdlet.</p></td>
</tr>
<tr class="even">
<td><p><em>MaxEarlyDialogs</em></p></td>
<td><p>Opcional</p></td>
<td><p>UInt32</p></td>
<td><p>O número máximo de respostas bifurcadas que um Gateway PSTN, IP-PBX ou SBC no provedor de serviços pode receber a um convite que ele enviou à Servidor de Mediação.</p>
<p>Padrão: 20</p></td>
</tr>
<tr class="odd">
<td><p><em>NetworkSiteID</em></p></td>
<td><p>Opcional</p></td>
<td><p>Cadeia de caracteres</p></td>
<td><p>ID do site da rede associado à nova coleção de definições de configuração de tronco. Se a propriedade EnableLocationRestriction estiver definida como True, o roteamento de voz baseado em local através desse tronco será gerenciado usando as definições configuradas para o site especificado. IDs de site da rede podem ser recuperados usando este comando:</p>
<p>Get-CsNetworkSite | Select NetworkSiteID</p>
<p>Este parâmetro foi introduzido na versão de fevereiro de 2013 do Lync Server 2013.</p></td>
</tr>
<tr class="even">
<td><p><em>OutboundCallingNumberTranslationRulesList</em></p></td>
<td><p>Opcional</p></td>
<td><p>PSListModifier</p></td>
<td><p>Conjunto de regras de conversão de número de chamada de saída atribuídas ao tronco. É possível recuperar informações sobre as regras disponíveis executando esse comando:</p>
<p>Get-CsOutboundCallingNumberTranslationRule</p></td>
</tr>
<tr class="odd">
<td><p><em>OutboundTranslationRulesList</em></p></td>
<td><p>Opcional</p></td>
<td><p>PSListModifier</p></td>
<td><p>Uma coleção de regras de conversão de números de telefone que se aplicam a chamadas gerenciadas pelo Roteamento de Saída (chamadas roteadas para destinos de PBX ou PSTN).</p>
<p>Embora esta lista e essas regras possam ser criadas diretamente com este cmdlet, é recomendável se criar as regras de conversão de saída com o cmdlet <strong>New-CsOutboundTranslationRule</strong>, que criará a regra e a atribuirá à configuração de tronco com o escopo correspondente.</p></td>
</tr>
<tr class="even">
<td><p><em>PstnUsages</em></p></td>
<td><p>Opcional</p></td>
<td><p>PSListModifier</p></td>
<td><p>Conjunto de usos PSTN atribuídos ao tronco. É possível recuperar informações sobre os usos disponíveis executando esse comando:</p>
<p>Get-CsPstnUsage</p></td>
</tr>
<tr class="odd">
<td><p><em>RemovePlusFromUri</em></p></td>
<td><p>Opcional</p></td>
<td><p>Booliano</p></td>
<td><p>A definição deste parâmetro como True fará o Servidor de Mediação remover os sinais de adição (+) dos Identificadores de recursos uniformes (URIs) antes de enviá-los ao provedor de serviços.</p>
<p>Padrão: False</p></td>
</tr>
<tr class="even">
<td><p><em>RTCPActiveCalls</em></p></td>
<td><p>Opcional</p></td>
<td><p>Booliano</p></td>
<td><p>Esse parâmetro determina se, nas chamadas ativas, os pacotes RTCP serão enviados do gateway da PSTN, IP-PBX ou SBC no provedor de serviços. Nesse contexto, uma chamada ativa é uma chamada na qual a mídia pode partir em pelo menos uma direção. Se RTCPActiveCalls for definido como True, o cliente Servidor de Mediação ou Lync Server poderá terminar uma chamada, caso ela não receba pacotes RTCP por um período superior a 30 segundos.</p>
<p>Observe que a desabilitação das verificações para mídia RTCP recebida em chamadas ativas nos elementos do Lync Server removerá uma salvaguarda importante para a detecção de pontos perdidos e só deve ser feita se houver necessidade.</p>
<p>Padrão: True</p></td>
</tr>
<tr class="odd">
<td><p><em>RTCPCallsOnHold</em></p></td>
<td><p>Opcional</p></td>
<td><p>Booliano</p></td>
<td><p>Esse parâmetro determina se os pacotes RTCP de chamadas que foram colocadas em espera continuarão a ser enviados no tronco e nenhum pacote de mídia deverá passar nas duas direções. Se Música em espera estiver habilitado no cliente Lync Server ou no tronco, a chamada será considerada ativa e essa propriedade será ignorada. Nessas circunstâncias, utilize o cmdlet RTCPActiveCalls.</p>
<p>Observe que a desabilitação das verificações para mídia RTCP recebida em chamadas ativas nos elementos do Lync Server removerá uma salvaguarda importante para a detecção de pontos perdidos e só deve ser feita se houver necessidade.</p>
<p>Padrão: True</p></td>
</tr>
<tr class="even">
<td><p><em>SipResponseCodeTranslationRulesList</em></p></td>
<td><p>Opcional</p></td>
<td><p>PSListModifier</p></td>
<td><p>Uma lista de regras de conversão do código de resposta de SIP que se aplicam aos códigos de resposta recebidos de um gateway da PSTN, IP-PBX ou SBC no provedor de serviços. Essas regras permitem que o administrador mapeie os códigos de resposta de SIP, com valores entre 400 e 699 e recebidos através de um tronco, com novos valores, mais consistentes com Lync Server.</p>
<p>É possível criar essa lista e as regras correspondentes diretamente com esse cmdlet. No entanto, é recomendável criar as regras de conversão do código de resposta de SIP chamando-se o cmdlet <strong>New-CsSipResponseCodeTranslationRule</strong>. Esse cmdlet criará a regra e a atribuirá à configuração do tronco que apresentar o escopo correspondente.</p></td>
</tr>
<tr class="odd">
<td><p><em>SRTPMode</em></p></td>
<td><p>Opcional</p></td>
<td><p>SRTPMode</p></td>
<td><p>O valor desse parâmetro determina o nível do suporte a SRTP para proteger o tráfego de mídia entre o Servidor de Mediação e o gateway da PSTN, IP-PBX ou SBC no provedor de serviços. Nos casos de desvio de mídia, este valor deve ser compatível com a configuração EncryptionLevel da configuração de mídia. A configuração de mídia é definida utilizando os cmdlets <strong>New-CsMediaConfiguration</strong> e <strong>Set-CsMediaConfiguration</strong>.</p>
<p>Valores válidos:</p>
<p>- Required: Deve se utilizar a criptografia SRTP.</p>
<p>- Optional: O SRTP será utilizado se o gateway lhe fornecer apoio.</p>
<p>- NotSupported: Não há apoio à criptografia SRTP e, portanto, ela não será utilizada.</p>
<p>Observação: SRTPMode é utilizado apenas se o gateway estiver configurado para usar a Segurança de camada de transporte (TLS). Se o gateway estiver configurado com o Protocolo de controle de transmissão (TCP) como transporte, SRTPMode será internamente definido como NotSupported.</p>
<p>Padrão: Obrigatório</p></td>
</tr>
<tr class="even">
<td><p><em>WhatIf</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Descreve o que aconteceria se o comando fosse executado sem ser executado de fato.</p></td>
</tr>
</tbody>
</table>


## Tipos de entrada

Nenhuma.

## Tipos de retorno

Cria um objeto do tipo Microsoft.Rtc.Management.WritableConfig.Settings.TrunkConfiguration.TrunkConfiguration.

## Consulte Também

#### Outros Recursos

[Remove-CsTrunkConfiguration](remove-cstrunkconfiguration.md)  
[Set-CsTrunkConfiguration](set-cstrunkconfiguration.md)  
[Get-CsTrunkConfiguration](get-cstrunkconfiguration.md)  
[Test-CsTrunkConfiguration](test-cstrunkconfiguration.md)  
[New-CsOutboundTranslationRule](new-csoutboundtranslationrule.md)

