---
title: Configurar um roteamento de voz do E9-1-1 no Lync Server 2013
TOCTitle: Configurar um roteamento de voz do E9-1-1 no Lync Server 2013
ms:assetid: 6933b840-0e7b-4509-ae43-bc9065677547
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398496(v=OCS.15)
ms:contentKeyID: 49306999
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurar um roteamento de voz do E9-1-1 no Lync Server 2013

 

_**Tópico modificado em:** 2012-09-17_

Para implantar o E9-1-1, é preciso primeiro configurar uma rota de voz de chamada de emergência. Para obter detalhes sobre como criar rotas de voz, consulte [Criar um roteamento de voz no Lync Server 2013](lync-server-2013-create-a-voice-route.md). É possível definir mais de uma rota se, por exemplo, sua implantação incluir um tronco SIP primário e um secundário.

> [!NOTE]  
> Para incluir informações de localização em um E9-1-1 INVITE, você precisa configurar o tronco SIP que se conecta ao provedor de serviços de E9-1-1 para encaminhar as chamadas de emergência através do gateway. Para isso, defina o sinalizador EnablePIDFLOSupport no cmdlet <strong>Set-CsTrunkConfiguration</strong> como True. O valor padrão de EnablePIDFLOSupport é False. Por exemplo: <code>Set-CsTrunkConfiguration Service:PstnGateway:192.168.0.241 -EnablePIDFLOSupport $true.</code><br />Não é necessário habilitar o recebimento de locais para os gateways ELIN (número de identificação de local de emergência) e os gateways PSTN (rede telefônica pública comutada) de fallback.

Para obter detalhes sobre o trabalho com rotas de voz, consulte a documentação do Shell de Gerenciamento do Lync Server para verificar os seguintes cmdlets:

  - **Set-CsPstnUsage**

  - **Get-CsPstnUsage**

  - **New-CsVoiceRoute**

  - **Get-CsVoiceRoute**

  - **Set-CsVoiceRoute**

  - **Remove-CsVoiceRoute**

## Para configurar uma rota de voz de E9-1-1

1.  Faça logon no computador com uma conta que seja membro dos grupos RTCUniversalServerAdmins ou membro da função administrativa CsVoiceAdministrator.

2.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

3.  Execute o cmdlet a seguir para criar um novo registro de uso PSTN.
    
    Esse deve ser o mesmo nome que você usará para a configuração **PSTN** na política de local. Embora sua implantação tenha vários registros de uso de telefone, o exemplo a seguir adiciona "Uso de emergência" à lista atual de usos de PSTN disponíveis. Para obter detalhes, consulte [Configurando políticas de voz e registros de uso de PSTN para autorizar recursos e privilégios de chamada no Lync Server 2013](lync-server-2013-configuring-voice-policies-and-pstn-usage-records-to-authorize-calling-features-and-privileges.md).
    
        Set-CsPstnUsage -Usage @{add='EmergencyUsage'}

4.  Execute o cmdlet a seguir para criar uma nova rota de voz usando o registro de uso PSTN criado na etapa anterior.
    
    O padrão de número deve ser o mesmo usado na configuração de **Cadeia de Caracteres de Discagem de Emergência** na política de local. Um sinal de "+" é necessário porque o Lync adiciona "+" às chamadas de emergência. "Co1-pstngateway-1" é a ID de serviço do tronco SIP do provedor de serviços de E9-1-1 ou a ID de serviço do gateway ELIN. O exemplo a seguir usa "EmergencyRoute" como o nome da rota de voz.
    
        New-CsVoiceRoute -Name "EmergencyRoute" -NumberPattern "^\+911$" -PstnUsages @{add="EmergencyUsage"} -PstnGatewayList @{add="co1-pstngateway-1"}

5.  Opcionalmente, para conexões de tronco SIP, recomendamos que você execute o cmdlet a seguir para criar uma rota local para as chamadas que não são manipuladas pelo tronco SIP do provedor de serviços de E9-1-1. Essa rota será usada quando a conexão com o provedor de serviços de E9-1-1 não estiver disponível.
    
    O exemplo a seguir pressupõe que o usuário tenha o uso "Local" em sua política de voz.
    
        New-CsVoiceRoute -Name "LocalEmergencyRoute" -NumberPattern "^\+911$" -PstnUsages @{add="Local"} -PstnGatewayList @{add="co1-pstngateway-2"}

