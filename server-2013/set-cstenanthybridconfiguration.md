---
title: Set-CsTenantHybridConfiguration
TOCTitle: Set-CsTenantHybridConfiguration
ms:assetid: 805ac9ee-df40-40e1-baaa-adffb6bd8cf6
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ994046(v=OCS.15)
ms:contentKeyID: 52057641
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsTenantHybridConfiguration

 

_**Tópico modificado em:** 2015-03-09_

Usado em um cenário híbrido para dar aos usuários hospedados em Microsoft Lync Online acesso aos recursos locais do Enterprise Voice, como bypass de mídia, 9-1-1 Avançado e estacionamento de chamadas. Um cenário híbrido (também conhecido como cenário de domínio dividido) é uma implantação do Lync Server na qual alguns usuários têm contas hospedadas localmente, enquanto outros têm contas hospedadas no Lync Online.

Este cmdlet pode ser usado apenas com o Skype for Business Online.

## Sintaxe

    Set-CsTenantHybridConfiguration [[-Identity] <XdsIdentity>] [-Tenant <guid>] [-PeerDestination <string>] [-HybridConfigServiceInternalUrl <string>] [-HybridConfigServiceExternalUrl <string>] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]Set-CsTenantHybridConfiguration [-Tenant <guid>] [-PeerDestination <string>][-HybridConfigServiceInternalUrl <string>] [-HybridConfigServiceExternalUrl <string>] [-Instance <psobject>] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]

## Exemplos

## Exemplo 1

O comando mostrado no Exemplo 1 define a URL do serviço interno para o conjunto global de definições de configuração híbridas do locatário. Para definir uma configuração global, inclua o parâmetro Identity junto com o valor do parâmetro "global".

    Set-CsTenantHybridConfiguration -Identity "global" - HybridConfigServiceInternalUrl "https://internal.litwareinc.com"

## Exemplo 2

No Exemplo 2, a URL do serviço interno é configurada para um locatário específico; neste exemplo, o locatário que tem a TenantID "bf19b7db-6960-41e5-a139-2aa373474354". Quando um valor de propriedade for atribuído explicitamente a um locatário individual, o locatário será regido por suas definições de configuração híbridas de locatário individual, em vez das configurações globais.

    Set-CsTenantHybridConfiguration -Tenant "bf19b7db-6960-41e5-a139-2aa373474354" HybridConfigServiceInternalUrl "https://internal.litwareinc.com"

## Exemplo 3

O comando mostrado no Exemplo 3 configura a URL do serviço interno para todos os locatários da sua organização. Para fazer isso, o comando primeiro usa o cmdlet **Get-CsTenant** para retornar um conjunto de todos os locatários disponíveis; esse conjunto é então canalizado para o cmdlet **ForEach-Object**. Por sua vez, o cmdlet **ForEach-Object** executa o cmdlet **Set-CsTenantHybridConfiguration** para cada locatário do conjunto, definindo a URL do serviço interno para cada um desses locatários como "https://internal.litwareinc.com".

    Get-CsTenant | ForEach-Object {Set-CsTenantHybridConfiguration -Tenant $_.TenantID -HybridConfigServiceInternalUrl "https://internal.litwareinc.com"}

## Descrição Detalhada

Em uma implantação híbrida ou de "domínio dividido", uma organização tem alguns usuários que têm contas hospedadas no Lync Online e, simultaneamente, tem outros usuários que têm contas hospedadas no Lync Server. Por padrão, os usuários hospedados no Lync Online não têm acesso à gama completa de recursos oferecida pelo Enterprise Voice, porque os servidores do Lync Online não têm acesso direto às informações de implantação local do Lync Server e de configuração da rede. Entre outras coisas, os usuários do Lync Online não têm acesso padrão a recursos como:

  - 9-1-1 Avançado, o serviço do Lync Server usado para fazer chamadas telefônicas de emergência.

  - Estacionamento de chamadas, o serviço do Lync Server que possibilita aos usuários colocar uma chamada em espera no telefone A e recuperar essa mesma chamada no telefone B.

  - Bypass de mídia, que possibilita que chamadas de e para a rede telefônica pública comutada (PSTN) desviem do Servidor de Mediação, ajudando a minimizar a transcodificação e a latência da rede.

  - A discagem para conferência por PSTN, que permite aos usuários participar da parte de áudio de uma conferência online, usando qualquer telefone PSTN ou dispositivo móvel.

  - O aplicativo de Grupo de Resposta, que fornece uma maneira para você rotear automaticamente as chamadas telefônicas para entidades como um suporte técnico ou uma linha de suporte ao cliente. Por padrão, os usuários do Lync Online não podem funcionar como agentes do Grupo de Resposta.

Para fornecer aos usuários do Lync Online acesso a esses recursos do Enterprise Voice, os administradores precisam atribuir os valores apropriados às definições de configuração híbridas, como as URLs de serviços Web internos e externos e o nome de domínio totalmente qualificado do servidor de Borda de Acesso da organização. Esses valores, que podem ser configurados apenas usando o cmdlet **Set-CsTenantHybridConfiguration**, fornecem aos servidores do Lync Online as informações necessárias para fazer uso desses recursos avançados do Enterprise Voice.

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
<td><p><em>Confirm</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Solicita confirmação antes da execução do comando.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p></p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Suprime a exibição de qualquer mensagem de erro não fatal que pode ocorrer ao executar o comando.</p></td>
</tr>
<tr class="odd">
<td><p><em>HybridConfigServiceExternalUrl</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>URL do serviço Web externo.</p></td>
</tr>
<tr class="even">
<td><p><em>HybridConfigServiceInternalUrl</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>URL do serviço Web interno.</p></td>
</tr>
<tr class="odd">
<td><p><em>Identity</em></p></td>
<td><p>Opcional</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>Identidade exclusiva das definições de configuração híbridas do locatário a serem modificadas. Como você está limitado a um único conjunto global de definições de configuração híbridas, o único conjunto que pode ser modificado usando o parâmetro Identity é o conjunto global:</p>
<p>-Identity global</p>
<p>Para modificar as configurações de um locatário individual, use o parâmetro Tenant em vez do parâmetro Identity.</p></td>
</tr>
<tr class="even">
<td><p><em>Instance</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.PSObject</p></td>
<td><p>Permite passar uma referência a um objeto para o cmdlet, em vez de definir valores de parâmetros individuais.</p></td>
</tr>
<tr class="odd">
<td><p><em>PeerDestination</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Nome de domínio totalmente qualificado do seu servidor de Borda de Acesso local.</p></td>
</tr>
<tr class="even">
<td><p><em>Tenant</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Guid</p></td>
<td><p>Identificador global exclusivo (GUID) da conta do locatário cujas definições de configuração híbridas estão sendo modificadas. Por exemplo:</p>
<p>–Tenant &quot;38aad667-af54-4397-aaa7-e94c79ec2308&quot;</p>
<p>É possível retornar o ID do locatário para cada um de seus locatários, executando este comando:</p>
<p>Get-CsTenant | Select-Object DisplayName, TenantID</p>
<p>Se você está usando uma sessão remota do Windows PowerShell e está conectado apenas ao Skype for Business Online, não precisa incluir o parâmetro Tenant. Em vez disso, a ID de locatário será preenchida automaticamente para você com base em suas informações de conexão. O parâmetro Tenant destina-se principalmente ao uso em uma implantação híbrida.</p></td>
</tr>
<tr class="odd">
<td><p><em>WhatIf</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Descreve o que aconteceria se o comando fosse executado sem ser executado de fato.</p></td>
</tr>
</tbody>
</table>


## Tipos de Entrada

Nenhuma. O cmdlet **Set-CsTenantHybridConfiguration** não aceita a entrada por pipeline.

## Tipos de Retorno

Nenhum. Em vez disso, o cmdlet **Set-CsTenantHybridConfiguration** modifica as instâncias existentes do objeto Microsoft.Rtc.Management.WritableConfig.Settings.HybridConfiguration.TenantHybridConfiguration.

## Consulte Também

#### Outros Recursos

[Get-CsTenantHybridConfiguration](get-cstenanthybridconfiguration.md)

