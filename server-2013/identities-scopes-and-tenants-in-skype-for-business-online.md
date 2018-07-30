---
title: Identidades, escopos e locatários
TOCTitle: Identidades, escopos e locatários
ms:assetid: 7cfa194a-2d01-4370-9b48-ee13ff597fa5
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn362819(v=OCS.15)
ms:contentKeyID: 56270435
ms.date: 06/02/2017
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Identidades, escopos e locatários

 

_**Tópico modificado em:** 2015-06-22_

Muitos dos cmdlets do Windows PowerShell usados para gerenciar o Skype for Business Online exigem que você seja muito específico sobre o item que você está tentando gerenciar. Por exemplo, quando você executa o cmdlet [Set-CsUserAcp](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsUserAcp), deve indicar qual usuário você está tentando gerenciar. Isso faz sentido. A menos que você diga especificamente ao cmdlet qual conta de usuário gerenciar, o cmdlet **Set-CsUserAcp** não tem ideia de qual informação de audioconferência do usuário deve ser modificada. Por esse motivo, cada vez que você executar o cmdlet **Set-CsUserAcp**, precisará incluir o parâmetro Identity, seguido da Identidade da conta do usuário a ser modificada:

    Set-CsUserAcp -Identity "Ken Myer" -TollNumber "14255551298" -ParticipantPassCode 13761 -Domain "fabrikam.com" -Name "Fabrikam ACP"

Se o termo *Identidade* sempre se referiu à Identidade de uma conta de usuário, haveria pouco motivo para confusão. Quando você está lidando com pessoas (usuários, contatos e assim por diante), as Identidades referem-se aos próprios usuários individuais. Entretanto, outros itens além das contas de usuário também têm Identidades. Quando você está lidando com componentes do serviço Skype for Business Online, como políticas, definições de configuração e outros, o termo Identidade significa algo ligeiramente diferente. Por exemplo, considere este comando:

    Get-CsMeetingConfiguration -Identity "global"

Neste caso, a Identidade "global" refere-se ao escopo das definições de configuração da reunião. *Escopo* é um termo usado no Skype for Business Online (e no Lync Server) para designar esferas de gerenciamento. Por padrão, as políticas e configurações sempre têm um escopo global. Quando você configurar pela primeira vez a sua conta do Skype for Business Online, terá, por padrão, um conjunto de políticas e configurações globais: definições de configuração globais da reunião, uma política de acesso externo global, um plano de discagem global e assim por diante.

Essas configurações e políticas globais foram introduzidas no Microsoft Lync Server 2010 para ajudar a assegurar que todos os usuários e todos os componentes seriam sempre, de alguma forma, gerenciados. Isso não era necessariamente verdadeiro no Microsoft Office Communicator 2007 R2. Dependendo de como você acessava o sistema, podia potencialmente acabar em um estado em grande parte não gerenciado (em geral, porque a Política de Grupo não pôde ser aplicada à sua conta de usuário). Em contraste, no Lync Server e no Skype for Business Online, nada fica sem ser gerenciado porque, em vez de qualquer outra coisa, configurações e políticas globais serão sempre aplicadas.

O que queremos dizer com "em vez de qualquer outra coisa"? Bem, no caso do Skype for Business Online, é possível criar políticas no *escopo de marca* ou na esfera do gerenciamento. As políticas criadas no escopo de marca (também conhecido como *o escopo por usuário*) têm prioridade sobre as políticas criadas no escopo global. Em outras palavras, uma política por usuário sempre terá precedência sobre uma política global. Por exemplo, você pode ter duas políticas de acesso de usuário externo. A política global proíbe os usuários de se comunicar com pessoas que tenham contas em provedores públicos de mensagens instantâneas, como o Windows Live. A política por usuário, AllowPublicIMCommunication, permite a comunicação com provedores públicos de mensagens instantâneas.

Você pode também ter dois usuários: João Casqueiro e Paula Bento. João Casqueiro recebeu a política por usuário. Paula Bento não recebeu uma política por usuário; ou seja, ela é gerenciada pela política de acesso externo global. A tabela a seguir mostra qual usuário (se houver) pode se comunicar com provedores públicos de mensagens instantâneas:


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Configurações de política</th>
<th>João Casqueiro</th>
<th>Paula Bento</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Configuração de política global para provedores públicos de mensagens instantâneas</p></td>
<td><p>Não</p></td>
<td><p>Não</p></td>
</tr>
<tr class="even">
<td><p>Configuração de política por usuário para provedores públicos de mensagens instantâneas</p></td>
<td><p>Sim</p></td>
<td><p>Não</p></td>
</tr>
<tr class="odd">
<td><p>O usuário pode se comunicar com provedores públicos de mensagens instantâneas</p></td>
<td><p>Sim</p></td>
<td><p>Não</p></td>
</tr>
</tbody>
</table>


Como você pode ver, João Casqueiro tem permissão para se comunicar com provedores públicos de mensagens instantâneas porque as configurações da política por usuário atribuída a ele substituem as configurações da política global. Paula Bento não pode se comunicar com provedores públicos de mensagens instantâneas porque é gerenciada pela política global, que proíbe tais comunicações.

As políticas por usuário devem ser criadas para você pelo Suporte do Office 365. Depois que as políticas são criadas, é possível atribuí-las aos usuários usando o cmdlet **Grant-Cs** apropriado (por exemplo, [Grant-CsExternalAccessPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Grant-CsExternalAccessPolicy)). As políticas por usuário são fáceis de identificar porque a Identidade da política sempre começa com a marca **prefix**. Por exemplo:

    Identity : tag:AllowPublicIMCommunication

> [!NOTE]  
> A marca <strong>prefix</strong> já existia nos primórdios do desenvolvimento do Lync Server 2010. Nessa época, as políticas por usuário eram chamadas de <em>políticas de marca</em> e eram identificadas pela marca <strong>prefix</strong>. Essas políticas agora são chamadas mais precisamente de <em>políticas por usuário</em>, e o escopo de marca é chamado mais precisamente de <em>escopo por usuário</em>. Entretanto, por motivos técnicos, a marca <strong>prefix</strong> nunca foi mudada.

Outro termo importante usado ao trabalhar com o Skype for Business Online e o Windows PowerShell é *locatário*. Quando você configura uma conta do Skype for Business Online, sua nova implantação recebe um número de ID de locatário, que é um identificador global exclusivo (GUID) como este:

    bf19b7db-6960-41e5-a139-2aa373474354

Alguns dos cmdlets do Skype for Business Online exigem que você insira a ID de locatário sempre que executa o cmdlet. Você deve inserir a ID de locatário mesmo se estiver conectado a um único locatário e só tiver um. Felizmente, não é necessário memorizar a ID de locatário. Você pode recuperá-la a qualquer momento executando o seguinte comando do Windows PowerShell:

    Get-CsTenant | Select-Object TenantId

É claro que saber coisas como a diferença entre o escopo global e o escopo por usuário (ou de marca) é apenas meio caminho andado. Também é importante saber quando (ou mesmo se) você pode usar esses escopos. O mesmo vale para as Identidades e o parâmetro de locatário. Estes tópicos descrevem como os diferentes cmdlets do Skype for Business Online usam Identidades, escopos e o parâmetro de locatário:

  - [Cmdlets que usam somente o escopo global](cmdlets-in-skype-for-business-online-that-use-only-the-global-scope.md)

  - [Cmdlets que usam o escopo global e o escopo de marca](cmdlets-in-skype-for-business-online-that-use-the-global-scope-and-the-tag-scope.md)

  - [Cmdlets Que Usam Identidade de Usuário](cmdlets-in-skype-for-business-online-that-use-a-user-identity.md)

  - [Cmdlets que usam uma identidade e usuário e o escopo de marca\]](cmdlets-in-skype-for-business-online-that-use-a-user-identity-and-the-tag-scope.md)

  - [Cmdlets que usam o parâmetro Tenant](cmdlets-in-skype-for-business-online-that-use-the-tenant-parameter.md)

  - [Cmdlets que Usam uma Identidade de Provedor Audioconferência](cmdlets-in-skype-for-business-online-that-use-a-conferencing-provider-identity.md)

  - [Cmdlets que não usam um escopo nem uma identidade](cmdlets-in-skype-for-business-online-that-do-not-use-a-scope-or-an-identity.md)

