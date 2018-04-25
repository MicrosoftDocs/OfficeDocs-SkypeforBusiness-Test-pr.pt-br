---
title: Configurar página de ingresso na reunião
TOCTitle: Configurar página de ingresso na reunião
ms:assetid: a87319b7-3124-4262-8f9d-18138870ee2d
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205145(v=OCS.15)
ms:contentKeyID: 49307728
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurar página de ingresso na reunião

 

_**Tópico modificado em:** 2015-03-09_

Quando um usuário clica em um link de reunião em uma solicitação de reunião, a página de ingresso em reunião detecta se um cliente do Lync 2013 já está instalado no computador do usuário. Se um cliente já estiver instalado, esse cliente abre e participa da reunião. Se não estiver instalado, como padrão, a versão 2013 do Microsoft Lync Web App é aberta.

Você pode modificar o comportamento da página de ingresso em reunião se desejar permitir que os usuários participem de reuniões com o Office Communicator 2007 R2 ou Lync 2010 Attendant. Essas opções de configuração foram removidas do Painel de Controle do Lync Server 2013, mas você pode configurá-las usando o cmdlet CsWebServiceConfiguration.

### Parâmetros CsWebServiceConfiguration da página de ingresso em reunião

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Parâmetro CsWebServiceConfiguration</th>
<th>Descrição</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>ShowJoinUsingLegacyClientLink</p></td>
<td><p>Se definido como True, os usuários que participarem de uma reunião usando um aplicativo cliente diferente do Lync terão a oportunidade de participar da reunião usando o Office Communicator 2007 R2. O valor padrão é False.</p></td>
</tr>
<tr class="even">
<td><p>ShowAlternateJoinOptionsExpanded</p></td>
<td><p>Quando definido para True, as opções alternativas para participar de uma conferência online (como o Office Communicator 2007 R2) serão expandidas automaticamente e mostrada aos usuários. Quando definido para False (o valor padrão), essas opções estarão disponíveis, mas o usuário precisará exibir a lista de opções sozinho.</p></td>
</tr>
</tbody>
</table>


## Para configurar a página de participação da reunião usando o Shell de Gerenciamento do Lync Server 2013

1.  Inicie o Shell de Gerenciamento do Lync Server 2013: Clique em **Iniciar** , em **Todos os Programas** , em **Microsoft Lync Server 2013**, e depois em **Shell de Gerenciamento do Lync Server**.

2.  Execute o seguinte cmdlet:
    
        Get-CsWebServiceConfiguration
    
    Este cmdlet retorna as definições de configurações do serviço da Web.

3.  Execute o comando a seguir, com os parâmetros definidos para Verdadeiro ou Falso, dependendo da sua preferência (para obter detalhes sobre os parâmetros deste cmdlet, consulte a documentação do Shell de Gerenciamento do Lync Server 2013):
    
        Set-CsWebServiceConfiguration -Identity global -ShowJoinUsingLegacyClientLink $True

