---
title: 'Lync Server 2013: Usuários domésticos em um Home users on a Aparelho de Filial Persistente ou Servidor'
TOCTitle: Usuários domésticos em um Home users on a Aparelho de Filial Persistente ou Servidor
ms:assetid: faf1ebb9-6d7d-4a58-8ff7-801b7b31d3ba
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg413066(v=OCS.15)
ms:contentKeyID: 49308680
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Usuários domésticos em um Home users on a Aparelho de Filial Persistente ou Servidor no Lync Server 2013

 

_**Tópico modificado em:** 2014-12-10_

O processo de hospedar usuários em uma função Aparelho de Filial Persistente ou Servidor de Filial Persistente é semelhante ao processo de hospedá-los em um Pool de Front-Ends. Execute o procedimento do Aparelho de Filial Persistente ou Servidor de Filial Persistente no local central.

## Para usuários domésticos no Servidor ou Aplicativo de Filial Persistente ou Servidor de Filial Persistente

1.  Antes de mover usuários para o Servidor de Filial Persistente ou Servidor de Filial Persistente, abra o Shell de Gerenciamento do Lync Server e faça o seguinte:
    
      - Execute o cmdlet **Test-CsPstnOutboundCall** para verificar se o Servidor de Filial Persistente é executado e a conectividade PSTN está configurada. Se você precisar modificar as propriedades do gateway PSTN, use o cmdlet **Set-CsPstnGateway**.
    
      - Execute o cmdlet **Get-CsVoicePolicy** para verificar se os usuários serão hospedados no Servidor de Filial Persistente com a política de roteamento VoIP adequada. Se você precisar modificar a política VoIP, use o cmdlet **Set-CsVoicePolicy**.
    
      - Execute o cmdlet **Get-CsVoicemailReroutingConfiguration** para verificar se as configurações de redirecionamento de caixa postal estão configuradas. Se você precisar modificar o configurações de redirecionamento de caixa postal, use o cmdlet **Set-CsVoicemailReroutingConfiguration**.

2.  No Shell de Gerenciamento do Lync Server, execute o cmdlet **Move-CsUser** para mover usuários domésticos.

> [!NOTE]  
> Você também pode usar o Painel de Controle do Lync Server para verificar os pré-requisitos e os usuários domésticos.

## Consulte Também

#### Outros Recursos

[Test-CsPstnOutboundCall](https://docs.microsoft.com/en-us/powershell/module/skype/Test-CsPstnOutboundCall)  
[Get-CsVoicePolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsVoicePolicy)  
[Get-CsVoicemailReroutingConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsVoicemailReroutingConfiguration)  
[Move-CsUser](https://docs.microsoft.com/en-us/powershell/module/skype/Move-CsUser)

