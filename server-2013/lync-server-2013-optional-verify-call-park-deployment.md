---
title: 'Lync Server 2013: (Opcional) Verificar implantação de Estacionamento de Chamadas'
TOCTitle: (Opcional) Verificar implantação de Estacionamento de Chamadas
ms:assetid: fcfe0962-1a9c-4cbd-847c-fed40e3b1480
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg413076(v=OCS.15)
ms:contentKeyID: 49308705
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# (Opcional) Verificar implantação de Estacionamento de Chamadas no Lync Server 2013

 

_**Tópico modificado em:** 2012-09-11_

Após instalar e configurar o Estacionamento de Chamadavocê precisará verificar a configuração para garantir que o estacionamento e a recuperação de chamadas funcionam conforme o esperado. No mínimo, verifique o seguinte:

  - Ligue para um usuário que tenha Estacionamento de Chamada ativado e faça com que o usuário estacione a chamada.
    
    > [!NOTE]  
    > Se você habilitou o Estacionamento de Chamada na política de voz antes de executar esse teste, o usuário estacionando a chamada precisa sair do Lync Server e entrar novamente para poder ver a opção Estacionamento de Chamada na lista de chamada em transferência.

  - Disque o número de órbita para recuperar a chamada.

  - Estacione outra chamada, permita que o tempo da chamada estacionada esgote e não pegue o retorno de chamada. Verifique se a chamada que atingiu o tempo limite será corretamente roteada para o destino de fallback especificado para **OnTimeoutURI** .

