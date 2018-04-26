---
title: 'Lync Server 2013: Planejamento de URLs simples'
TOCTitle: Planejamento de URLs simples
ms:assetid: 20e4f4b6-b7ff-4297-b00d-d1211ee800ac
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398287(v=OCS.15)
ms:contentKeyID: 49306105
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Planejamento de URLs simples no Lync Server 2013

 

_**Tópico modificado em:** 2015-12-11_

URLs simples facilita o ingresso dos usuários nas reuniões e o acesso às ferramentas administrativas do Lync Server para os seus administradores.

O Lync Server suporta três URLs simples:

  - **Reunir** é usado como URL base para todas as conferências no site ou na organização. Um exemplo de URL Reunir simples é https://meet.contoso.com. Uma URL para uma determinada reunião pode ser https://meet.contoso.com/ *nome de usuário* /7322994.
    
    Com Reunião, é possível compreender, comunicar e distribuir facilmente URLs simples e links para participar de reuniões.

  - **Discar** possibilita o acesso à página da web Configurações de Conferência Discada. Esta página mostra os números de discagem de conferência com seus idiomas disponíveis, as informações de conferência atribuídas (para reuniões que não necessitam de agendamento), controles DTMF durante a conferência, suporte de gerenciamento do PIN (número de identificação pessoal) e informações atribuídas da conferência. O URL Discar é incluído em todos os convites de reuniões para que o usuário que desejar discar para ingressar na reunião possa obter acesso ao número de telefone necessário, bem como as informações do PIN. Um exemplo de URL simples Discar é https://discar.contoso.com.

  - **Admin** possibilita o acesso rápido ao Painel de Controle do Lync Server. A partir de qualquer computador dentro do firewall da sua organização, um administrador pode abrir o Painel de Controle do Lync Server digitando o URL simples Admin em um navegador. O URL simples Admin é interno para a sua organização. Um exemplo de URL simples Admin é https://admin.contoso.com

## Escopo do URL simples

Você pode configurar seus URLs simples para que tenham um escopo global ou você pode especificar URLs simples diferentes para cada site central na sua organização. Se tanto o URL simples global como o URL simples de site forem especificados, a preferência é do URL simples de site.

Na maioria dos casos, recomendamos que você defina URLs simples somente em um nível global, assim, o URL simples Reunir não é alterado se houver mudança de um site para outro. A exceção seria para organizações que precisam usar números de telefone diferentes para os usuários de discagem em locais diferentes. Observe que se você definir um URL simples (como o URL simples Discar) em um site para que ele seja um site de nível de URL simples, você deve definir também outros URLs simples para que eles também estejam no nível de site de URL simples.

Você pode definir URLs globais simples no Construtor de Topologias. Para definir um URL simples no nível do site, você deve usar o cmdlet Set-CsSimpleURLConfiguration.

## Nomeando seus URLs simples

Existem três opções recomendadas para nomear seus URLs simples. A opção escolhida implica em como configurar seus registros A de DNS e os certificados que suportam URLs simples. Em cada opção, você deve configurar um URL de Reunião simples para cada domínio SIP na sua organização.

Você sempre precisa de um URL simples para toda sua organização para Discar e um para Administração, não importa quantos domínios SIP você tenha.

Para obter detalhes sobre os registros A de DNS e certificados, consulte [Requisitos de DNS para URLs simples no Lync Server 2013](lync-server-2013-dns-requirements-for-simple-urls.md) e [Requisitos de certificado para servidores internos no Lync Server 2013](lync-server-2013-certificate-requirements-for-internal-servers.md) na documentação Planejamento.

Na Opção 1, você cria um novo nome de domínio SIP para cada URL simples.

Se usar esta opção, você precisará de um registro A de DNS separado para cada URL simples e cada URL Reunir simples deve ser nomeado em seus certificados.

### Opção 1 de nome de URL simples

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>URL simples</strong></p></td>
<td><p><strong>Exemplo</strong></p></td>
</tr>
<tr class="even">
<td><p>Reunir</p></td>
<td><p>https://meet.contoso.com, https://meet.fabrikam.com e assim por diante (um para cada domínio SIP em sua organização)</p></td>
</tr>
<tr class="odd">
<td><p>Discar</p></td>
<td><p>https://dialin.contoso.com</p></td>
</tr>
<tr class="even">
<td><p>Admin</p></td>
<td><p>https://admin.contoso.com</p></td>
</tr>
</tbody>
</table>


Com a opção 2, os URLs simples tem como base o nome de domínio lync.contoso.com. Por isso, você precisará somente de um registro A de DNS que permita todos os três tipos de URL simples. Esse registro A de DNS está relacionado a lync.contoso.com. além disso, você ainda precisa separar os registros A de DNS para os outros domínios SIP da sua organização.

### Opção 2 de nome de URL simples

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>URL simples</strong></p></td>
<td><p><strong>Exemplo</strong></p></td>
</tr>
<tr class="even">
<td><p>Reunir</p></td>
<td><p>https://lync.contoso.com/Meet, https://lync.fabrikam.com/Meet e assim por diante (um para cada domínio SIP em sua organização)</p></td>
</tr>
<tr class="odd">
<td><p>Discar</p></td>
<td><p>https://lync.contoso.com/Dialin</p></td>
</tr>
<tr class="even">
<td><p>Admin</p></td>
<td><p>https://lync.contoso.com/Admin</p></td>
</tr>
</tbody>
</table>


A opção 3 é mais útil se você tiver muitos domínios SIP e desejar que eles tenham URLs Reunir separadas, mas desejar minimizar o registro de DNS e os requisitos de certificação para esses URLs simples.

### Opção 3 de nome de URL simples

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>URL simples</strong></p></td>
<td><p><strong>Exemplo</strong></p></td>
</tr>
<tr class="even">
<td><p>Reunir</p></td>
<td><p>https://lync.contoso.com/contosoSIPdomain/Meet</p>
<p>https://lync.contoso.com/fabrikamSIPdomain/Meet</p></td>
</tr>
<tr class="odd">
<td><p>Discar</p></td>
<td><p>https://lync.contoso.com/Dialin</p></td>
</tr>
<tr class="even">
<td><p>Admin</p></td>
<td><p>https://lync.contoso.com/Admin</p></td>
</tr>
</tbody>
</table>


## Nome e regras de validação de URLs simples

Os cdmlets Construtor de Topologias e Shell de Gerenciamento do Lync Server reforçam várias regras de validação para seus URLs simples. Será solicitado que você defina URLs simples para Reunir e Discar, mas para Admin será opcional. Cada domínio SIP deve ter um URL Reunir simples, mas você precisa somente de um URL Discar simples e um URL Admin simples para toda sua organização.

Cada URL simples na sua organização deve ter um nome exclusivo e não pode ser um prefixo para outra URL simples (por exemplo, você não pode definir lync.contoso.com/Reunir como sua URL de Reunião simples e 0lync/contoso.com/Reunir/Discar como sua URL de Discar simples). Os nomes de URL simples não podem conter o FQDN de qualquer um dos seus pools ou informações de qualquer porta (por exemplo, https://FQDN:88/reunir não é permitido). Todas as URLs simples devem começar com o prefixo https://.

URLs simples podem conter somente caracteres alfanuméricos (ou seja, a-z, A-Z, 0-9 e o ponto (.). Se você utilizar outros caracteres, o URL simples pode não funcionar como esperado.

## Alteração de URLs simples após a implantação

Se você alterar uma URL simples após a implantação inicial, esteja ciente de quais alterações impactarão nos seus registros DNS e certificados para as URLs simples. Se a alteração impactar a base de uma URL simples, você precisará alterar os registros de DNS e certificados também. Por exemplo, alterar https://lync.contoso.com/Reunir para https://reunir.contoso.com altera a URL base de lync.contoso.com para meet.contoso.com, e por isso, você precisará alterar os registros DNS e certificados referentes a reunir.contoso.com. Se você alterou a URL simples de https://lync.contoso.com/Reunir para https://lync.contoso.com/Reunioes, a URL base de lync.contoso.com permanece a mesma por isso, não são necessárias alterações de DNS ou certificados.

Sempre que você alterar um nome de URL simples, no entanto, é necessário executar o **Enable-CsComputer** em cada Diretor e Servidor Front-End para registrar a alteração.

## Consulte Também

#### Conceitos

[Requisitos de DNS para URLs simples no Lync Server 2013](lync-server-2013-dns-requirements-for-simple-urls.md)

