---
title: Set-CsTrunkConfiguration
TOCTitle: Set-CsTrunkConfiguration
ms:assetid: 18152388-68de-4a6b-b5a1-248534ecde72
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398238(v=OCS.15)
ms:contentKeyID: 49306017
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsTrunkConfiguration

 

_**Tópico modificado em:** 2015-02-27_

Modifica uma configuração de tronco existente que descreve as definições de uma entidade de mesmo nível de tronco, como um gateway de rede telefônica pública comutada (PSTN), Central privada de comutação (PBX) de IP ou Controlador de Borda de Sessão (SBC) no provedor de serviços. Este cmdlet foi introduzido no Lync Server 2010.

## Sintaxe

    Set-CsTrunkConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Set-CsTrunkConfiguration [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-ConcentratedTopology <$true | $false>] [-Confirm [<SwitchParameter>]] [-Description <String>] [-Enable3pccRefer <$true | $false>] [-EnableBypass <$true | $false>] [-EnableFastFailoverTimer <$true | $false>] [-EnableLocationRestriction <$true | $false>] [-EnableMobileTrunkSupport <$true | $false>] [-EnableOnlineVoice <$true | $false>] [-EnablePIDFLOSupport <$true | $false>] [-EnableReferSupport <$true | $false>] [-EnableRTPLatching <$true | $false>] [-EnableSessionTimer <$true | $false>] [-EnableSignalBoost <$true | $false>] [-Force <SwitchParameter>] [-ForwardCallHistory <$true | $false>] [-ForwardPAI <$true | $false>] [-MaxEarlyDialogs <UInt32>] [-NetworkSiteID <String>] [-OutboundCallingNumberTranslationRulesList <PSListModifier>] [-OutboundTranslationRulesList <PSListModifier>] [-PstnUsages <PSListModifier>] [-RemovePlusFromUri <$true | $false>] [-RTCPActiveCalls <$true | $false>] [-RTCPCallsOnHold <$true | $false>] [-SipResponseCodeTranslationRulesList <PSListModifier>] [-SRTPMode <Required | Optional | NotSupported>] [-WhatIf [<SwitchParameter>]]

## Exemplos

## EXEMPLO 1

Este exemplo modifica uma configuração de tronco cuja Identidade for site:Redmond, para habilitar o desvio de mídia. O desvio de mídia é habilitado pela atribuição do valor $True ao parâmetro EnableBypass. As propriedades restantes desta configuração manterão os seus valores atuais.

    Set-CsTrunkConfiguration -Identity site:Redmond -EnableBypass $True

## EXEMPLO 2

Este exemplo modifica uma regra de conversão de saída definida para a configuração de tronco cuja Identidade for site:Redmond. Observe que, para fazer esta mudança, não se realiza uma chamada ao cmdlet **Set-CsTrunkConfiguration**. As mudanças feitas utilizando-se o cmdlet **Set-CsOutboundTranslationRule** serão automaticamente refletidas na configuração do tronco cuja identidade corresponder à parte do escopo da identidade da regra de conversão de saída.

    Set-CsOutboundTranslationRule -Identity site:Redmond/OTR1 -Translation '$1'

## EXEMPLO 3

O Exemplo 3 define SRTPMode como Opcional em todas as configurações de tronco definidas no escopo do site. A primeira parte do comando é uma chamada ao cmdlet **Get-CsTrunkConfiguration**, que usa o parâmetro Filter para recuperar todas as configurações do tronco com uma Identidade que começa com site:, ou seja, todas as configurações do tronco definidas no nível do site. Esta coleção de configurações será então canalizada para o cmdlet **Set-CsTrunkConfiguration**, que definirá a propriedade SRTPMode de cada um como sendo Opcional.

    Get-CsTrunkConfiguration -Filter site:* | Set-CsTrunkConfiguration -SRTPMode "Optional"

## EXEMPLO 4

O exemplo 4 modifica uma configuração de tronco com a Identidade site:Redmond, para habilitar o suporte a PIDF-LO. Por padrão, o parâmetro EnablePIDFLOSupport é False. Neste exemplo, definimos o valor como True para habilitar o suporte ao local para chamadas de emergência. Você deve definir o EnablePIDFLOSupport como True para que as informações do local sejam enviadas para o tronco pelo aplicativo de roteamento de saída.

    Set-CsTrunkConfiguration -Identity site:Redmond -EnablePIDFLOSupport $True

## Descrição detalhada

Use esse cmdlet para remover uma configuração de tronco que se aplique a essas entidades de Gateway PSTN. Cada configuração contém definições específicas de uma entidade de mesmo nível de tronco, como um gateway PSTN, IP-PBX ou SBC do provedor de serviços. Essas definições configuram aspectos como a habilitação (ou não) do desvio de mídia nesse tronco, o envio (ou não) dos pacotes do protoco de controle de transporte em tempo real (RTCP) sob determinadas condições e a exigência de se efetuar (ou não) a criptografia SRTP (protocolo em tempo real seguro).

Quem pode executar esse cmdlet: Por padrão, membros dos seguintes grupos são autorizados a executar o cmdlet **Set-CsTrunkConfiguration** localmente: RTCUniversalServerAdmins. Para retornar uma lista de todas as funções do controle de acesso baseado em função (RBAC) que receberam a atribuição desse cmdlet (incluindo qualquer função RBAC personalizada criada por você), execute o seguinte comando do prompt Windows PowerShell:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsTrunkConfiguration"}

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
<th>Tipo</th>
<th>Descrição</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>ConcentratedTopology</em></p></td>
<td><p>Opcional</p></td>
<td><p>Boolean</p></td>
<td><p>O valor deste parâmetro determina se existe um ponto conhecido de encerramento da mídia. Um exemplo de ponto de terminação de mídia conhecido seria um Gateway PSTN, em que a terminação de mídia possui o mesmo IP que a terminação de sinalização. Defina este valor como False se o tronco não possuir um ponto conhecido de encerramento de mídia.</p>
<p>Padrão: True</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>Opcional</p></td>
<td><p>SwitchParameter</p></td>
<td><p>Solicita confirmação antes da execução do comando.</p></td>
</tr>
<tr class="odd">
<td><p><em>Description</em></p></td>
<td><p>Opcional</p></td>
<td><p>Cadeia de caracteres</p></td>
<td><p>Uma cadeia de caracteres que descreve o propósito da configuração de tronco.</p></td>
</tr>
<tr class="even">
<td><p><em>Enable3pccRefer</em></p></td>
<td><p>Opcional</p></td>
<td><p>Boolean</p></td>
<td><p>Indica se o protocolo 3pcc pode ser usado para permitir chamadas transferidas ignorem o site hospedado. O 3pcc também é conhecido como &quot;controle de terceiros&quot; e ocorre quando um terceiro é usado para conectar um par de chamadores (por exemplo, um operador colocando uma chamada da pessoa A para a pessoa B). O método REFER é um método SIP padrão que indica que o destinatário deve entrar em contato com o terceiro usando a informação fornecida pelo remetente. O valor padrão é Falso ($False).</p></td>
</tr>
<tr class="odd">
<td><p><em>EnableBypass</em></p></td>
<td><p>Opcional</p></td>
<td><p>Boolean</p></td>
<td><p>O valor deste parâmetro determina se o desvio de mídia está habilitado para este tronco. Defina este valor como True, para habilitar o desvio. Observe que, para que o desvio de mídia funcione corretamente, determinadas capacidades devem ser suportadas pelos gateways PSTN, SBCs e PBXs, inclusive:</p>
<p>- a capacidade de receber respostas bifurcadas a um convite.</p>
<p>- É necessário que os clientes do Lync Server e o ponto de terminação de mídia sejam capazes de se comunicarem diretamente, sem precisar passar por um Servidor de Mediação.</p>
<p>- a localização da sub-rede do Gateway deve ser definida como sendo no mesmo site da sub-rede do cliente ou, se definida em um site diferente, os sites não devem estar separados por links WAN com largura de banda restrita.</p>
<p>O desvio de mídia pode ser habilitado apenas sob as seguintes circunstâncias:</p>
<p>- o parâmetro ConcentratedTopology está definido como True</p>
<p>- o parâmetro EnableReferSupport está definido como False, e RTCPActiveCalls e RTCPCallsOnHold estão definidos como False, ou EnableReferSupport está definido como True</p>
<p>Observe que se EnableBypass for True e EnableReferSupport for False, as chamadas de desvio que serão subsequentemente transferidas tornar-se-ão de não-desvio.</p>
<p>Para que o desvio de mídia funcione em um determinado tronco, é necessário que ele esteja habilitado globalmente, assim como para o tronco em questão. Use o cmdlet <strong>New-CsNetworkMediaBypassConfiguration</strong> para habilitar o desvio de mídia globalmente.</p>
<p>Padrão: False</p></td>
</tr>
<tr class="even">
<td><p><em>EnableFastFailoverTimer</em></p></td>
<td><p>Opcional</p></td>
<td><p>Boolean</p></td>
<td><p>Quando definido para True, as chamadas em saída que não são respondidas pelo gateway dentro de 10 segundos serão roteadas para o próximo tronco disponível; se não há troncos adicionais, a chamada será derrubada automaticamente. Em uma organização com respostas de redes e gateway lentas, isso pode resultar em chamadas sendo derrubadas desnecessariamente.</p>
<p>O valor padrão é True.</p></td>
</tr>
<tr class="odd">
<td><p><em>EnableLocationRestriction</em></p></td>
<td><p>Opcional</p></td>
<td><p>Boolean</p></td>
<td><p>Quando definido como True, o roteamento de voz baseado em localização será habilitado para chamadas passando pelos troncos SIP gerenciados pela coleção especificada de definições de configuração de troncos SIP. Com roteamento de voz baseado em localização, os locais de ambos o usuário realizando a chamada e o usuário recebendo-a são levados em consideração quando as chamadas são roteadas. Se essa propriedade for definida como True (o valor padrão é False), você deverá também definir a propriedade NetworkSiteId.</p></td>
</tr>
<tr class="even">
<td><p><em>EnableMobileTrunkSupport</em></p></td>
<td><p>Opcional</p></td>
<td><p>Boolean</p></td>
<td><p>Define se o provedor de serviços é uma operadora de telefonia celular.</p>
<p>Padrão: False</p></td>
</tr>
<tr class="odd">
<td><p><em>EnableOnlineVoice</em></p></td>
<td><p>Opcional</p></td>
<td><p>Boolean</p></td>
<td><p>Indica se os troncos SIP suportam a voz online. Com uma voz online, os usuários possuem uma conta do Lync Server local, mas possuem uma caixa postal hospedada pelo Skype for Business Online. O valor padrão é Falso ($False).</p></td>
</tr>
<tr class="even">
<td><p><em>EnablePIDFLOSupport</em></p></td>
<td><p>Opcional</p></td>
<td><p>Boolean</p></td>
<td><p>Define se as chamadas de emergência com Objeto de Local de Formato de Dados de Informação de Presença (PIDF-LO) serão roteadas ou não através do gateway definido. Defina esse parâmetro como True, se as chamadas de emergência tiverem de ser roteadas para um provedor de serviços de emergência certificado (o local será transmitido com a chamada).</p>
<p>Padrão: False</p></td>
</tr>
<tr class="odd">
<td><p><em>EnableReferSupport</em></p></td>
<td><p>Opcional</p></td>
<td><p>Boolean</p></td>
<td><p>Define se esse tronco apoia o recebimento de solicitações de Referência vindas do Servidor de Mediação.</p>
<p>O desvio de mídia pode ser habilitado apenas sob as seguintes circunstâncias:</p>
<p>- o parâmetro ConcentratedTopology está definido como True</p>
<p>- o parâmetro EnableReferSupport está definido como False, e RTCPActiveCalls e RTCPCallsOnHold estão definidos como False, ou EnableReferSupport está definido como True</p>
<p>Observe que se EnableBypass for True e EnableReferSupport for False, as chamadas de desvio que serão subsequentemente transferidas tornar-se-ão de não-desvio.</p>
<p>Padrão: True</p></td>
</tr>
<tr class="even">
<td><p><em>EnableRTPLatching</em></p></td>
<td><p>Opcional</p></td>
<td><p>Boolean</p></td>
<td><p>Indica se os troncos SIP suportam ou não o latching RTP. O latching RTP é uma tecnologia que permite a conectividade RTP/RTCP através de um dispositivo NAT NAT (conversor de endereço de rede) ou firewall. O valor padrão é Falso ($False).</p></td>
</tr>
<tr class="odd">
<td><p><em>EnableSessionTimer</em></p></td>
<td><p>Opcional</p></td>
<td><p>Boolean</p></td>
<td><p>Especifica se o cronômetro da sessão estará habilitado. Os cronômetros de sessão são utilizados para determinar se uma determinada sessão ainda está ativa.</p>
<p>Observe que, mesmo se esse parâmetro for definido como False, os cronômetros de sessão poderão ser aplicáveis, caso o cronômetro de sessão da conexão remota estiver habilitado. Nesse caso, o Servidor de Mediação responderá a testes do cronômetro de sessão da entidade remota.</p>
<p>Padrão: False</p></td>
</tr>
<tr class="even">
<td><p><em>EnableSignalBoost</em></p></td>
<td><p>Opcional</p></td>
<td><p>Boolean</p></td>
<td><p>Quando esse parâmetro for definido como True, o gateway PSTN, IP-PBX ou SBC do provedor de serviço aumentará o volume do áudio nos fluxos de voz que forem enviados aos clientes da Servidor de Mediação ou Lync Server. Se esse valor for definido como False, o áudio será aumentado na Servidor de Mediação (nas chamadas de não-desvio) ou em clientes Lync Server (nas chamadas de desvio).</p>
<p>Padrão: False</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>Opcional</p></td>
<td><p>SwitchParameter</p></td>
<td><p>Suprime qualquer aviso de confirmação que, de outra maneira, seria exibido antes de se realizar as alterações.</p></td>
</tr>
<tr class="even">
<td><p><em>ForwardCallHistory</em></p></td>
<td><p>Opcional</p></td>
<td><p>Boolean</p></td>
<td><p>Indica se a informação de histórico de chamada será encaminhada pelo tronco. O valor padrão é Falso ($False).</p></td>
</tr>
<tr class="odd">
<td><p><em>ForwardPAI</em></p></td>
<td><p>Opcional</p></td>
<td><p>Boolean</p></td>
<td><p>Indica se o cabeçalho PAI (P-Asserted-Identity) será encaminhado com a chamada. O cabeçalho PAI oferece uma forma de verificar a identidade do chamador. O valor padrão é Falso ($False).</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>Opcional</p></td>
<td><p>XdsIdentity</p></td>
<td><p>Um identificador exclusivo que inclui o escopo da configuração de troncos. As configurações de troncos podem existir no escopo Global ou de Site, ou no escopo de Serviço, no caso de um serviço de Gateway PSTN. Por exemplo, site:Redmond (no escopo de site) ou PstnGateway:Redmond.litwareinc.com (no escopo de serviço).</p></td>
</tr>
<tr class="odd">
<td><p><em>Instance</em></p></td>
<td><p>Opcional</p></td>
<td><p>TrunkConfiguration</p></td>
<td><p>Permite passar uma referência a um objeto para o cmdlet, em vez de definir valores de parâmetros individuais.</p>
<p>Este parâmetro requer um objeto do tipo Microsoft.Rtc.Management.WritableConfig.Settings.TrunkConfiguration.TrunkConfiguration, que pode ser recuperado chamando-se o cmdlet <strong>Get-CsTrunkConfiguration</strong>.</p></td>
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
<td><p>A ID do local de rede associado à coleção de definições de configuração de tronco. Se a propriedade EnableLocationRestriction for definida como True, o roteamento de voz baseado em localização por esse tronco será gerenciado pelo uso das configurações definidas para o site especificado. IDs de locais de rede podem ser obtidas pelo uso desse comando:</p>
<p>Get-CsNetworkSite | Select NetworkSiteID</p></td>
</tr>
<tr class="even">
<td><p><em>OutboundCallingNumberTranslationRulesList</em></p></td>
<td><p>Opcional</p></td>
<td><p>PSListModifier</p></td>
<td><p>Conjunto de regras de conversão de número de chamada de saída atribuído ao tronco. É possível recuperar informações sobre as regras disponíveis executando esse comando:</p>
<p>Get-CsOutboundCallingNumberTranslationRule</p></td>
</tr>
<tr class="odd">
<td><p><em>OutboundTranslationRulesList</em></p></td>
<td><p>Opcional</p></td>
<td><p>PSListModifier</p></td>
<td><p>Uma coleção de regras de conversão de números de telefone que se aplicam a chamadas tratadas pelo Roteamento de saída (chamadas roteadas para destinos de PBX ou PSTN).</p>
<p>Embora esta lista e estas regras possam ser modificadas diretamente por deste cmdlet, recomendamos que as regras de conversão de saída sejam modificadas com o cmdlet <strong>Set-CsOutboundTranslationRule</strong>. O cmdlet <strong>Set-CsOutboundTranslationRule</strong> modificará a regra e isso se refletirá automaticamente na configuração do tronco. Para modificar a configuração do tronco pela adição de uma nova regra de conversão de saída, chame o cmdlet <strong>New-CsOutboundTranslationRule</strong>. A nova regra será adicionada à configuração do tronco que apresentar um escopo coincidente.</p></td>
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
<td><p>Boolean</p></td>
<td><p>A definição deste parâmetro como True fará a Servidor de Mediação remover os sinais de adição (+) iniciais dos URIs antes de enviá-los ao provedor de serviços.</p>
<p>Padrão: False</p></td>
</tr>
<tr class="even">
<td><p><em>RTCPActiveCalls</em></p></td>
<td><p>Opcional</p></td>
<td><p>Boolean</p></td>
<td><p>Esse parâmetro determina se, nas chamadas ativas, os pacotes RTCP serão enviados do gateway PSTN, IP-PBX ou SBC do provedor de serviços. Uma chamada ativa nesse contexto é uma chamada em que a mídia pode partir em pelo menos uma direção. Se RTCPActiveCalls for definido comoTrue, o cliente Servidor de Mediação ou Lync Server pode terminar uma chamada, caso ela não receba pacotes RTCP por um período superior a 30 segundos.</p>
<p>Observe que a desabilitação das verificações para mídia RTCP recebida em chamadas ativas nos elementos do Lync Server removerá uma salvaguarda importante para a detecção de pares descartados e só deve ser feita se houver necessidade.</p>
<p>Padrão: True</p></td>
</tr>
<tr class="odd">
<td><p><em>RTCPCallsOnHold</em></p></td>
<td><p>Opcional</p></td>
<td><p>Boolean</p></td>
<td><p>Esse parâmetro determina se os pacotes RTCP de chamadas que foram colocadas em espera continuarão a ser enviados no tronco e nenhum pacote de mídia deverá passar nas duas direções. Se Música de espera estiver habilitado no cliente Lync Server ou no tronco, a chamada será considerada ativa e essa propriedade será ignorada. Nessas circunstâncias, use o parâmetro RTCPActiveCalls.</p>
<p>Observe que a desabilitação das verificações para mídia RTCP recebida em chamadas ativas nos elementos do Lync Server removerá uma salvaguarda importante para a detecção de pares descartados e só deve ser feita se houver necessidade.</p>
<p>Padrão: True</p></td>
</tr>
<tr class="even">
<td><p><em>SipResponseCodeTranslationRulesList</em></p></td>
<td><p>Opcional</p></td>
<td><p>PSListModifier</p></td>
<td><p>Uma lista de regras de conversão do código de resposta de SIP que se aplicam aos códigos de resposta recebidos de um gateway PSTN, IP-PBX ou SBC do provedor de serviços. Essas regras permitem que o administrador mapeie os códigos de resposta SIP, com valores entre 400 e 699 e recebidos através de um tronco, com novos valores, mais consistentes com Lync Server.</p>
<p>É possível criar essa lista e as regras correspondentes diretamente com esse cmdlet. No entanto, recomendamos criar as regras de conversão do código de resposta SIP chamando o cmdlet <strong>New-CsSipResponseCodeTranslationRule</strong>. Esse cmdlet criará a regra e a atribuirá à configuração do tronco que apresentar o escopo correspondente.</p></td>
</tr>
<tr class="odd">
<td><p><em>SRTPMode</em></p></td>
<td><p>Optional</p></td>
<td><p>SRTPMode</p></td>
<td><p>O valor desse parâmetro determina o nível do suporte a SRTP para proteger o tráfego de mídia entre o Servidor de Mediação e o gateway PSTN, IP-PBX ou SBC do provedor de serviços. Nos casos de desvio de mídia, este valor deve ser compatível com a definição EncryptionLevel da configuração de mídia. A configuração de mídia é definida usando-se os cmdlets <strong>New-CsMediaConfiguration</strong> e <strong>Set-CsMediaConfiguration</strong>.</p>
<p>Valores válidos:</p>
<p>- Obrigatório: Deve se utilizar a criptografia SRTP.</p>
<p>- Opcional: O SRTP será utilizado se o provedor de serviços lhe fornecer apoio.</p>
<p>- NotSupported: Não há apoio à criptografia SRTP e, portanto, ela não será utilizada.</p>
<p>Observação: SRTPMode é usado apenas se o gateway estiver configurado para usar a Segurança da Camada de Transporte (TLS). Se o gateway estiver configurado com o Protocolo de Controle de Transmissão (TCP) como transporte, SRTPMode será internamente definido como NotSupported.</p>
<p>Padrão: Obrigatório</p></td>
</tr>
<tr class="even">
<td><p><em>WhatIf</em></p></td>
<td><p>Optional</p></td>
<td><p>SwitchParameter</p></td>
<td><p>Descreve o que aconteceria se o comando fosse executado sem ser executado de fato.</p></td>
</tr>
</tbody>
</table>


## Tipos de entrada

Objeto Microsoft.Rtc.Management.WritableConfig.Settings.TrunkConfiguration.TrunkConfiguration. Aceita entrada canalizada de objetos de configuração de tronco.

## Tipos de retorno

Esse cmdlet não retorna um valor; ele modifica um objeto do tipo Microsoft.Rtc.Management.WritableConfig.Settings.TrunkConfiguration.TrunkConfiguration.

## Consulte Também

#### Outros Recursos

[New-CsTrunkConfiguration](new-cstrunkconfiguration.md)  
[Remove-CsTrunkConfiguration](remove-cstrunkconfiguration.md)  
[Get-CsTrunkConfiguration](get-cstrunkconfiguration.md)  
[Test-CsTrunkConfiguration](test-cstrunkconfiguration.md)  
[New-CsOutboundTranslationRule](new-csoutboundtranslationrule.md)  
[Set-CsOutboundTranslationRule](set-csoutboundtranslationrule.md)

