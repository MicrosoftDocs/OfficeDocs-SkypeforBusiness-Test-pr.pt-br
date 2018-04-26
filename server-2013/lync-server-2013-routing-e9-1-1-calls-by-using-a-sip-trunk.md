---
title: 'Lync Server 2013: Roteamento de chamadas E9-1-1 usando tronco SIP'
TOCTitle: Roteamento de chamadas E9-1-1 usando tronco SIP
ms:assetid: 157753c3-fe74-4e2c-81da-ee06911d4cc2
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204701(v=OCS.15)
ms:contentKeyID: 49305980
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Roteamento de chamadas E9-1-1 usando tronco SIP no Lync Server 2013

 

_**Tópico modificado em:** 2012-09-29_

Usar um tronco SIP para conectar a um provedor de serviço de E9-1-1 qualificado é um modo pelo qual você pode implantar E9-1-1. Para detalhes sobre usar um gateway ELIN para conectar a um provedor de serviço de E9-1-1 baseado em PSTN (rede telefônica pública comutada), consulte [Roteamento de chamadas E9-1-1 usando um gateway ELIN no Lync Server 2013](lync-server-2013-routing-e9-1-1-calls-by-using-an-elin-gateway.md).

O diagrama a seguir mostra como uma chamada de emergência é encaminhada do Lync Server ao PSAP (ponto de atendimento público seguro) quando você usa um tronco SIP e um provedor de serviço de E9-1-1 qualificado.

**Roteando chamadas E9-1-1 através de um tronco SIP**

![Roteamento da chamada de emergência do Lync Server para PSAP](images/JJ204701.0637a9d4-2ca7-438a-8ed0-19090a4b992d(OCS.15).jpg "Roteamento da chamada de emergência do Lync Server para PSAP")

Quando uma chamada de emergência é feita de um cliente compatível do Lync Server:

1.  Um SIP INVITE que contém o local, o número de retorno de chamada do chamador e a URL de notificação (opcional) e número de retorno de chamada de conferência são encaminhados ao Lync Server.

2.  O Lync Server faz uma correspondência com o número de emergência e encaminha a chamada (com base no valor de **Uso de PSTN** que é definido na política aplicável de local) para um Servidor de Mediação, e a partir deste, via um tronco SIP ao provedor de serviço E9-1-1.

3.  O provedor de serviço E9-1-1 encaminha a chamada de emergência ao PSAP correto baseado no local que é fornecido com a chamada. Quando o cliente inclui um ERL (local de resposta de emergência) com a chamada de emergência, o provedor automaticamente encaminha a chamada ao PSAP adequado. Caso o local tenha sido manualmente inserido pelo usuário, o ECRC (centro de resposta de chamadas de emergência) primeiro verifica verbalmente a precisão do local com o chamador antes de encaminhar a chamada de emergência ao PSAP.

4.  Se você tiver configurado a política de local para notificações, um ou mais funcionários de segurança da sua organização receberão uma mensagem instantânea de notificação de emergência especial do Lync. Essa mensagem sempre aparecerá na(s) tela(s) dos funcionários de segurança e contém o nome, o número de telefone, a hora e o local do chamador, permitindo que o pessoal de segurança atenda rapidamente o chamador de emergência usando uma mensagem instantânea ou voz.

5.  Caso tenha configurado a política de local para conferências e ela seja suportada pelo provedor de serviço de E9-1-1, um Suporte de Segurança é colocado na chamada com áudio uni ou bidirecional.

6.  Caso a chamada seja interrompida prematuramente, o PSAP usa o número de retorno de chamada para entrar em contato diretamente com o chamador.

