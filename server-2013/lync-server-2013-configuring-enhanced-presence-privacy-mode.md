---
title: Configurando o modo de privacidade de presença avançada
TOCTitle: Configurando o modo de privacidade de presença avançada
ms:assetid: e7a6b873-486d-4dfb-a967-c48f61f237f3
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg399028(v=OCS.15)
ms:contentKeyID: 49308445
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurando o modo de privacidade de presença avançada

 

_**Tópico modificado em:** 2016-12-08_

Com o modo de privacidade de presença avançada, os usuários podem restringir as informações de presença para que elas fiquem visíveis somente aos contatos listados na lista de Contatos do Lync 2013. O parâmetro EnablePrivacyMode do cmdlet **New-CsPrivacyConfiguration** do **Set-CsPrivacyConfiguration** controla essa opção. Quando EnablePrivacyMode está definido como True, a opção para restringir as informações de presença para os contatos se torna disponível nas opções de status do Lync 2013. Quando EnablePrivacyMode está definido como False, os usuários podem optar por sempre permitir que qualquer pessoa veja as informações de presença ou aderir a qualquer mudança futura que o administrador faça no modo de privacidade.

> [!IMPORTANT]  
> Lync 2013 e Lync 2010 não são atendidas pelas versões anteriores (Microsoft Office Communicator 2007 R2 ou Microsoft Office Communicator 2007). Se as versões anteriores do Office Communicator tiverem permissão para fazer logon, o status, informações de contato ou foto de um usuário do Lync 2013 poderão ser vistas por alguém que não foi autorizado. Além disso, as configurações de privacidade de um usuário do Lync 2013 serão redefinidas se ele ou ela fizer logon posteriormente com a versão anterior do Communicator.<br />Por esses motivos, em um cenário de migração, antes de habilitar o modo de privacidade de presença avançada:<ul>
> 
> <li><p>Certifique-se de que cada usuário tenha o Lync 2013 instalado.</p></li>
> 
> 
> <li><p>Defina uma regra de política de versão do cliente para impedir que as versões anteriores do Communicator faça logon.</p></li></ul>


## Para habilitar o modo de privacidade de presença avançada

1.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

2.  Execute o seguinte comando:
    
        Get-CsPrivacyConfiguration | Set-CsPrivacyConfiguration -EnablePrivacyMode $True
    
    Esse comando habilita o modo de privacidade para todas as definições de configuração da privacidade em uso na organização.

## Consulte Também

#### Outros Recursos

[Get-CsPrivacyConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsPrivacyConfiguration)  
[New-CsPrivacyConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsPrivacyConfiguration)  
[Set-CsPrivacyConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsPrivacyConfiguration)

