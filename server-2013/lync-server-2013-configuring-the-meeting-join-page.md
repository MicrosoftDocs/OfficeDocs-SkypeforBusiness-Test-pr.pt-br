---
title: 'Lync Server 2013: Configurando a página de ingresso na reunião'
TOCTitle: Configurando a página de ingresso na reunião
ms:assetid: 45880423-47f4-49af-b825-cbd8e3fc1046
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204861(v=OCS.15)
ms:contentKeyID: 49306580
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurando a página de ingresso na reunião no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

Quando um usuário clica em um link de reunião em uma solicitação de reunião, a página de participação da reunião detecta se um cliente Lync 2013 já está instalado no computador do usuário. Se um cliente já estiver instalado, ele abre e participa da reunião. Caso não esteja instalado, por padrão a versão 2013 do Lync Web App se abre.

Você pode modificar o comportamento da página de participação de reunião se quiser permitir que os usuários participem de reuniões com Office Communicator 2007 R2 ou Lync 2010 Attendant. Essas opções de configuração foram removidas do Painel de Controle do Lync Server 2013, mas você pode configurá-las utilizando o cmdlet Set-CsWebServiceConfiguration.

### Parâmetros do Set-CsWebServiceConfiguration da página de participação de reunião

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Parâmetro Set-CsWebServiceConfiguration</th>
<th>Descrição</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>ShowJoinUsingLegacyClientLink</p></td>
<td><p>Se definido para Verdadeiro, os usuários participam de uma reunião utilizando um aplicativo de cliente em vez de o Lync ter a oportunidade de participar da reunião utilizando o Office Communicator 2007 R2. O valor padrão é Falso.</p></td>
</tr>
<tr class="even">
<td><p>ShowAlternateJoinOptionsExpanded</p></td>
<td><p>Quando definido para True, as opções alternativas para participar de uma conferência online (como o Office Communicator 2007 R2) serão expandidas automaticamente e mostrada aos usuários. Quando definido para False (o valor padrão), essas opções estarão disponíveis, mas o usuário precisará exibir a lista de opções sozinho.</p></td>
</tr>
</tbody>
</table>


## Para configurar a página de participação da reunião usando o Shell de Gerenciamento do Lync Server 2013

1.  Inicie o Shell de Gerenciamento do Lync Server 2013: Clique em **Iniciar** , em **Todos os Programas** , em **Microsoft Lync Server 2013**, e depois em **Shell de Gerenciamento do Lync Server**.

2.  Para visualizar as definições de configuração do serviço da web, execute o seguinte cmdlet:
    
        Get-CsWebServiceConfiguration

3.  Execute o comando a seguir, com os parâmetros definidos para Verdadeiro ou Falso, dependendo da sua preferência (para obter informações sobre os parâmetros do cmdlet, consulte [Set-CsWebServiceConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsWebServiceConfiguration) in the Shell de Gerenciamento do Lync Server 2013 documentation):
    
        Set-CsWebServiceConfiguration -Identity global -ShowJoinUsingLegacyClientLink $True

## Consulte Também

#### Outros Recursos

[Set-CsWebServiceConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsWebServiceConfiguration)

