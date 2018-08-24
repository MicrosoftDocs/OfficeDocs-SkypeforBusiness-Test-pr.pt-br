---
title: 'Lync Server 2013: Habilitar usuários para correio de voz hospedado'
TOCTitle: Habilitar usuários para correio de voz hospedado
ms:assetid: fa559f8f-ef99-43a1-b580-9e998b95efb8
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg413062(v=OCS.15)
ms:contentKeyID: 49308674
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Habilitar usuários para correio de voz hospedado no Lync Server 2013

 

_**Tópico modificado em:** 2012-09-24_

Siga o procedimento para habilitar os usuários do Lync Server 2013 para caixa postal em um serviço de UM do Exchange hospedado.

Para obter detalhes, consulte [Gerenciamento de usuário no Exchange hospedado no Lync Server 2013](lync-server-2013-hosted-exchange-user-management.md) na documentação de Planejamento.

Para obter detalhes sobre o cmdlet [Set-CsUser](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsUser), consulte a documentação do Shell de Gerenciamento do Lync Server.

> [!IMPORTANT]  
> Antes de um usuário do Lync Server 2013 poder ser habilitado para caixa postal hospedada, uma política de caixa postal hospedada que se aplica à conta de usuário deve ser implantada. Para obter detalhes, consulte <a href="lync-server-2013-hosted-voice-mail-policies.md">Políticas de correio de voz hospedado no Lync Server 2013</a>.

## Para habilitar usuários para caixa postal hospedada

1.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

2.  Execute o cmdlet Set-CsUser para configurar a conta de usuário para a caixa postal hospedada. Por exemplo, execute:
    
        Set-CsUser -HostedVoiceMail $True -Identity "contoso\kenmyer"
    
    O exemplo anterior define os seguintes parâmetros:
    
      - **HostedVoiceMail** permite que as chamadas de caixa postal do usuário sejam roteadas para o UM do Exchange hospedado. Ele também sinaliza o Microsoft Lync 2013 para acender o indicador "chamada de caixa postal".
    
      - **Identity** especifica a conta de usuário a ser modificada. O valor Identity pode ser especificado usando os seguintes formatos:
        
          - O endereço SIP do usuário
        
          - O User-Principal-Name do Active Directory do usuário
        
          - O domínio/nome de login do usuário (por exemplo, contoso\\kenmyer)
        
          - O Display-Name dos Serviços de Domínio do Active Directory do usuário (por exemplo, Ken Myer). Se usar o Display-Name como o valor Identity, é possível usar o caractere curinga asterisco (\*). Por exemplo, a Identity "\* Smith" retorna todos os usuários que podem ter um Display-Name terminando com o valor da cadeia de caracteres "Smith".
        
        > [!NOTE]  
        > O SAM-Account-Name do Active Directory do usuário não pode ser usado como um valor Identity porque o SAM-Account-Name não é necessariamente exclusivo na floresta.
