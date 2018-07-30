---
title: Atribuir uma política de caixa postal hospedada por usuário no Lync Server 2013
TOCTitle: Atribuir uma política de caixa postal hospedada por usuário no Lync Server 2013
ms:assetid: d44c71a0-4407-4ab4-b7e0-d671dde3425f
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398919(v=OCS.15)
ms:contentKeyID: 49308227
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Atribuir uma política de caixa postal hospedada por usuário no Lync Server 2013

 

_**Tópico modificado em:** 2010-11-07_

A implantação de uma ou mais políticas de caixa postal hospedada por usuário é opcional. Se você implantar políticas por usuário, deverá atribui-las explicitamente a usuários, grupos ou objetos de contato.

Para obter detalhes sobre como atribuir ou remover a atribuição de políticas de caixa postal hospedada por usuário, consulte a documentação do Shell de Gerenciamento do Lync Server para os seguintes cmdlets:

  - Grant-CsHostedVoicemailPolicy

  - Remove-CsHostedVoicemailPolicy

## Para atribuir uma política de caixa postal hospedada por usuário

1.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

2.  Execute o cmdlet Grant-CsHostedVoicemailPolicy para atribuir a política de caixa postal hospedada por usuário a usuários individuais, grupos e objetos de contato. Por exemplo, execute:
    
        Grant-CsHostedVoicemailPolicy -Identity "Ken Myer" -PolicyName ExRedmond
    
    Esse exemplo atribuiu a política de caixa postal hospedada ExRedmond ao usuário Ken Myer.
    
    **Identidade** especifica a conta de usuário a ser modificada. O valor de Identidade pode ser especificado usando qualquer um dos seguintes formatos:
    
      - O endereço SIP do usuário
    
      - O nome UPN do Active Directory do usuário
    
      - O nome de domínio\\logon do usuário (por exemplo, contoso\\kenmyer)
    
      - O Nome de exibição de serviços de domínio do Active Directory do usuário (por exemplo, Ken Myer). se estiver usando o Nome de exibição como o valor de Identidade, será possível usar o caractere curinga asterisco (\*). Por exemplo, a Identidade "\* Smith" retorna todos os usuários que tem um Nome de exibição que termina com o valor de string "Smith".
    
    > [!NOTE]  
    > O Nome de conta SAM do Active Directory do usuário não pode ser usado como o valor de Identidade, pois o Nome de conta SAM não é necessariamente exclusivo na floresta.
