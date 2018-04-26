---
title: Get-CsTenantHybridConfiguration
TOCTitle: Get-CsTenantHybridConfiguration
ms:assetid: 4b2e6781-8f46-4ba3-be76-3a95460e3132
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ994034(v=OCS.15)
ms:contentKeyID: 52057623
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsTenantHybridConfiguration

 

_**Tópico modificado em:** 2015-03-09_

Retorna valores das configurações híbridas que permitem aos usuários hospedados no Microsoft Lync Online terem acesso aos recursos do Enterprise Voice, como bypass de mídia, Enhanced 9-1-1 e estacionamento de chamada. Um cenário híbrido (também conhecido como cenário de domínio dividido) é uma implantação do Lync Server em que alguns usuários têm contas hospedadas no local, enquanto outros usuários têm contas hospedadas no Lync Online.

O cmdlet Get-CsTenantHybridConfiguration só pode ser usado com o Skype for Business Online.

## Sintaxe

    Get-CsTenantHybridConfiguration [[-Identity] <XdsIdentity>] [-Tenant <guid>] [-LocalStore] [<CommonParameters>]Get-CsTenantHybridConfiguration [-Tenant <guid>] [-Filter <string>] [-LocalStore] [<CommonParameters>]

## Exemplos

## Exemplo 1

O comando mostrado no Exemplo 1 retorna os valores de propriedade da coleção global de configurações híbridas de locatário.

    Get-CsTenantHybridConfiguration -Identity "Global"

## Exemplo 2

No Exemplo 2, os valores de propriedade retornados referem-se às configurações híbridas de locatário personalizadas aplicadas ao locatário com a TenantId "bf19b7db-6960-41e5-a139-2aa373474354".

    Get-CsTenantHybridConfiguration -Tenant "bf19b7db-6960-41e5-a139-2aa373474354"

## Exemplo 3

O Exemplo 3 retorna informações da configuração híbrida de todos os locatários disponíveis. Para fazer isso, o comando primeiro chama o cmdlet **Get-CsTenant**para retornar uma coleção de todos esses locatários. Essa coleção, então, se conecta ao cmdlet **ForEach-Object**, que executa duas tarefas em cada locatário da coleção, um a um. Primeiro, o cmdlet imprime o nome de exibição do Active Directory do locatário; isso garante que cada coleção de configurações poderá ser imediatamente identificada. Depois, o cmdlet **ForEach-Object** executa o cmdlet **Get-CsTenantHybridConfiguration** para retornar as configurações híbridas do locatário em questão.

    Get-CsTenant | ForEach-Object {$_.DisplayName; Get-CsTenantHybridConfiguration -Tenant $_.TenantId}

## Descrição detalhada

Em uma implantação híbrida ou de "domínio dividido", uma organização tem alguns usuários com contas hospedadas no Lync Online e, ao mesmo tempo, usuários com contas hospedadas na versão local do Lync Server. Por padrão, os usuários hospedados no Lync Online não têm acesso à gama completa de recursos oferecidos pelo Enterprise Voice; isso acontece porque os servidores Lync Online não têm acesso direto à implantação do Lync Server e às informações da configuração da rede. Entre outras coisas, os usuários do Lync Online não têm acesso padrão a recursos como:

  - 9-1-1 Avançado, o serviço do Lync Server usado para fazer chamadas telefônicas de emergência.

  - Estacionamento de chamadas, o serviço do Lync Server que possibilita aos usuários colocar uma chamada em espera no telefone A e recuperar essa mesma chamada no telefone B.

  - Bypass de mídia, que possibilita que chamadas de e para a rede telefônica pública comutada (PSTN) desviem do Servidor de Mediação, ajudando a minimizar a transcodificação e a latência da rede.

  - A discagem para conferência por PSTN, que permite aos usuários participar da parte de áudio de uma conferência online, usando qualquer telefone PSTN ou dispositivo móvel.

  - O aplicativo de Grupo de Resposta, que fornece uma maneira para você rotear automaticamente as chamadas telefônicas para entidades como um suporte técnico ou uma linha de suporte ao cliente. Por padrão, os usuários do Lync Server não podem funcionar como agentes do Grupo de Resposta.

Para fornecer aos usuários do Lync Online acesso a esses recursos do Enterprise Voice, os administradores precisam atribuir os valores apropriados às definições de configuração híbridas, como as URLs de serviços Web internos e externos e o nome de domínio totalmente qualificado do servidor de Borda de Acesso da organização. Esses valores, que podem ser configurados apenas usando o cmdlet **Set-CsTenantHybridConfiguration**, fornecem aos servidores do Lync Online as informações necessárias para fazer uso desses recursos avançados do Enterprise Voice.

Você pode retornar informações sobre as configurações híbridas de locatário atualmente em uso na sua organização usando o cmdlet **Get-CsTenantHybridConfiguration**.

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
<td><p><em>Filter</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Permite que você use caracteres curinga para retornar uma coleção de configurações híbridas de locatário. Como você está limitado a uma coleção global única de configurações híbridas, não é necessáro usar o parâmetro Filter. No entanto, esta é a sintaxe válida para o cmdlet <strong>Get-CsTenantHybridConfiguration</strong>:</p>
<p>Get-CsTenantHybridConfiguration –Filter &quot;g*&quot;</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>Opcional</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>A identidade exclusiva das configurações híbridas de locatário a serem retornadas. Como você está limitado a uma coleção global única de configurações híbridas, a única coleção que pode ser retornada por meio do parâmetro Identity é a coleção global:</p>
<p>-Identity global</p>
<p>Para modificar as configurações de um locatário individual, use o parâmetro Tenant em vez do parâmetro Identity.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Recupera os dados de configuração híbrida de locatário na réplica local do Repositório de Gerenciamento Central, e não no próprio Repositório de Gerenciamento Central.</p></td>
</tr>
<tr class="even">
<td><p><em>Tenant</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Guid</p></td>
<td><p>Identificador global exclusivo (GUID) da conta de locatário cujas configurações híbridas estão sendo retornadas. Por exemplo:</p>
<p>–Tenant &quot;38aad667-af54-4397-aaa7-e94c79ec2308&quot;</p>
<p>É possível retornar o ID do locatário para cada um de seus locatários, executando este comando:</p>
<p>Get-CsTenant | Select-Object DisplayName, TenantID</p>
<p>Se você estiver usando uma sessão remota do Windows PowerShell e estiver conectado apenas ao Skype for Business Online, não terá que incluir o parâmetro Tenant. Ao contrário, o ID do locatário será preenchido automaticamente para você com base nas informações de sua conexão. O parâmetro Tenant é basicamente para usar em uma implantação híbrida.</p></td>
</tr>
</tbody>
</table>


## Tipos de entrada

Nenhum. O cmdlet **Get-CsTenantHybridConfiguration** não aceita a entrada por pipeline.

## Tipos de retorno

O cmdlet **Get-CsTenantHybridConfiguration** retorna instâncias do objeto Microsoft.Rtc.Management.WritableConfig.Settings.HybridConfiguration.TenantHybridConfiguration.

## Consulte Também

#### Outros Recursos

[Set-CsTenantHybridConfiguration](set-cstenanthybridconfiguration.md)

