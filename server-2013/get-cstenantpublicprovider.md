---
title: Get-CsTenantPublicProvider
TOCTitle: Get-CsTenantPublicProvider
ms:assetid: 0d949ec2-206d-4979-a3be-a5578ae93ed3
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ994016(v=OCS.15)
ms:contentKeyID: 52057554
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsTenantPublicProvider

 

_**Tópico modificado em:** 2015-03-09_

Retorna informações sobre como indicar se os usuários do Microsoft Lync Online têm permissão para se comunicar com pessoas que têm contas em provedores de presença e de mensagens instantâneas de terceiros, como Windows Live, AOL e Yahoo.

Este cmdlet pode ser usado apenas com o Skype for Business Online.

## Sintaxe

    Get-CsTenantPublicProvider -Tenant <String> [-Verbose]

## Exemplos

## Exemplo 1

O comando mostrado no Exemplo 1 retorna informações do provedor público referente ao locatário com a ID "bf19b7db-6960-41e5-a139-2aa373474354".

    Get-CsTenantPublicProvider -Tenant "bf19b7db-6960-41e5-a139-2aa373474354"

Observe que o parâmetro Tenant é opcional. Você também pode chamar Get-CsTenantPublicProvider usando esta sintaxe:

    Get-CsTenantPublicProvider

## Exemplo 2

O comando anterior retorna informações detalhadas sobre o status de todos os provedores públicos atribuídos ao locatário bf19b7db-6960-41e5-a139-2aa373474354. Para fazer isso, o comando usa primeiro o cmdlet **Get-CsTenantPublicProvider** para retornar informações do provedor público referentes ao locatário especificado. Essas informações são, então, conectadas ao cmdlet **Select-Object**, que usa o parâmetro ExpandProperty para "expandir" o valor da propriedade DomainPICStatus. A expansão de uma propriedade significa simplesmente a exibição de todos os valores armazenados na tela dessa propriedade, em um formato de fácil leitura.

    Get-CsTenantPublicProvider -Tenant "bf19b7db-6960-41e5-a139-2aa373474354" | Select-Object -ExpandProperty DomainPICStatus

Um comando como seria útil em uma implantação híbrida do Lync Server 2013.

## Exemplo 3

O comando exibido no Exemplo 3 é uma variação do comando do Exemplo 2. No Exemplo 3, no entanto, as informações do provedor público retornadas com a "expansão" do valor da propriedade DomainPICStatus são, por sua vez, conectadas ao cmdlet **Where-Object**. Em seguida, o cmdlet **Where-Object** separa somente os provedores em que a propriedade Status é definida como Enabled. O resultado será a exibição somente dos provedores públicos habilitados para uso.

    Get-CsTenantPublicProvider -Tenant "bf19b7db-6960-41e5-a139-2aa373474354" | Select-Object -ExpandProperty DomainPICStatus | Where-Object {$_.Status -eq "Enabled"}

## Descrição detalhada

Os provedores públicos são organizações que fornecem serviços de comunicação SIP para o público geral. Ao estabelecer um relacionamento entre federações com um provedor público, você estabelece a federação com qualquer usuário que tem uma conta hospedada por esse provedor. Por exemplo, se você federar com o Windows Live, os usuários poderão trocar mensagens instantâneas e informações de presença com qualquer pessoa que tenha um conta de mensagem instantânea do Windows Live.

O Lync Online oferece aos administradores a opção de configurar a federação com um ou mais dos seguintes provedores de serviços públicos de mensagens instantâneas e provedores de presença:

  - Windows Live

  - AOL

  - Yahoo\!

Os administradores podem usar o cmdlet **Get-CsTenantPublicProvider** para determinar quais desses provedores (se houver) foram habilitados para federação. Quando você chamar o cmdlet **Get-CsTenantPublicProvider**, informações semelhantes às seguintes serão retornadas:

    PublicProviderSet     DomainPicStatus
    ------------------    ------------------------
    True                  {Microsoft.Rtc.Management.Hosted.DomainPICStatus}

A propriedade PublicProviderSet indica se a federação foi habilitada ou não para um ou mais provedores públicos. Se PublicProviderSet for True, isso significa que a federação foi habilitada com, pelo menos, um provedor. Se PublicProviderSet for False, isso significa que a federação está desabilitada para os três provedores públicos (Windows Live, AOL e Yahoo). Para determinar o status real de cada provedor, use esse comando.

    Get-CsTenantPublicProvider -Tenant "bf19b7db-6960-41e5-a139-2aa373474354" | Select-Object -ExpandProperty DomainPICStatus

Observe que simplesmente habilitar o status de um provedor público não significa que os usuários podem trocar mensagens instantâneas e informações de presença com usuários que têm contas nesse provedor. Além de habilitar a federação com o próprio provedor, os administradores também devem definir a propriedade AllowPublicUsers das configurações de federação para True. Se essa propriedade for definida como False, não será permitida comunicação com nenhum provedor público, independentemente das configurações do provedor público.

Para obter mais informações, consulte o tópico de ajuda referente ao cmdlet **Set-CsTenantFederationConfiguration**.

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
<td><p><em>Tenant</em></p></td>
<td><p>Obrigatório</p></td>
<td><p>System.String</p></td>
<td><p>Identificador global exclusivo (GUID) da conta de locatário cujas configurações de provedor público estão sendo retornadas. Por exemplo:</p>
<p>–Tenant &quot;38aad667-af54-4397-aaa7-e94c79ec2308&quot;</p>
<p>É possível retornar o ID do locatário para cada um de seus locatários, executando este comando:</p>
<p>Get-CsTenant | Select-Object DisplayName, TenantID</p>
<p>Se você estiver usando uma sessão remota do Windows PowerShell e estiver conectado apenas ao Skype for Business Online, não terá que incluir o parâmetro Tenant. Ao contrário, o ID do locatário será preenchido automaticamente para você com base nas informações de sua conexão. O parâmetro Tenant é basicamente para usar em uma implantação híbrida.</p></td>
</tr>
</tbody>
</table>


## Tipos de entrada

Nenhum. O cmdlet **Get-CsTenantPublicProvider** não aceita a entrada por pipeline.

## Tipos de retorno

O cmdlet **Get-CsTenantPublicProvider** retorna instâncias do objeto Microsoft.Rtc.Management.Hosted.TenantPICStatus.

## Consulte Também

#### Outros Recursos

[Set-CsTenantPublicProvider](set-cstenantpublicprovider.md)

