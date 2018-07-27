---
title: Modificar a política de caixa postal hospedada global no Lync Server 2013
TOCTitle: Modificar a política de caixa postal hospedada global no Lync Server 2013
ms:assetid: f059b3ce-a7d8-4ea9-b10b-0052222ec2ce
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg412994(v=OCS.15)
ms:contentKeyID: 49308560
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Modificar a política de caixa postal hospedada global no Lync Server 2013

 

_**Tópico modificado em:** 2012-09-24_

A política de caixa postal hospedada *global* é instalada com o Lync Server 2013. É possível modificá-la para corresponder às suas necessidades, mas não é possível renomear ou exclui-la. Para modificar a política global, deve usar o cmdlet Set-CsHostedVoicemailPolicy para definir os parâmetros para os valores adequados da sua implantação específica.

Para obter detalhes sobre o cmdlet [Set-CsHostedVoicemailPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsHostedVoicemailPolicy), consulte a documentação do Shell de Gerenciamento do Lync Server.

## Para modificar a política de caixa postal hospedada global

1.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

2.  Execute o Set-CsHostedVoicemailPolicy para definir os parâmetros da política global do seu ambiente. Por exemplo, execute:
    
        Set-CsHostedVoicemailPolicy -Destination ExUM.fabrikam.com -Organization "corp1.litwareinc.com"
    
    Como este comando não especifica o parâmetro Identidade da política, o Interface da linha de comando do Windows PowerShell define os seguintes valores na política de caixa postal hospedada global:
    
      - **Destino** especifica o FQDN do serviço UM do Exchange hospedado. Este parâmetro é opcional, mas se você tentar habilitar um usuário para a caixa postal hospedada e a política atribuída do usuário não possui um valor de Destino, a habilitação falhará.
    
      - **Organização** especifica a lista separada por vírgulas dos inquilinos do Exchange que hospedam os usuários do Lync Server. Cada inquilino deve ser especificado como o FQDN daquele inquilino no serviço UM do Exchange hospedado.
    
    > [!NOTE]  
    > No cmdlet de exemplo anterior, o valor “corp1.litwareinc.com” substitui qualquer valor que pode já estar presente no parâmetro Organização. Por exemplo, se a política já contém uma lista separada por vírgulas da organização, a lista completa seria substituída. Se deseja adicionar uma organização à lista ao invés de substituir toda a lista, execute um comando similar ao seguinte. 

      ```
        $a = Get-CsHostedVoicemailPolicy
        $a.Organization += ",corp3.litwareinc.com"
        Set-CsHostedVoicemailPolicy -Organization $a.Organization
      ```

