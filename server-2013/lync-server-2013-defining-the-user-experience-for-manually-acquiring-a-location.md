---
title: 'Lync Server 2013: Definindo a experiência do usuário para aquisição manual de local'
TOCTitle: Definindo a experiência do usuário para aquisição manual de local
ms:assetid: d37f67d3-e248-483b-b64c-3986559ef357
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398912(v=OCS.15)
ms:contentKeyID: 49308214
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Definindo a experiência do usuário para aquisição manual de local no Lync Server 2013

 

_**Tópico modificado em:** 2012-10-03_

Se um cliente estiver localizado fora da rede ou em uma subrede indefinida, o usuário poderá inserir manualmente um local. Mas durante uma chamada de emergência, a chamada será roteada primeiro para o ECRC (Centro de resposta de chamada de emergência) de E9-1-1 nacional/regional antes de ser roteada para um PSAP (Ponto de atendimento público seguro). O ECRC consultará verbalmente o chamador por um local e encaminhará a chamada para o PSAP adequado, com base nas informações fornecidas.

  - **Os usuários devem ser solicitados a inserir um local quando isso não for obtido automaticamente pelo Serviço de Informações de Local?**  
    Por exemplo, se um cliente estiver localizado em uma sub-rede indefinida, em casa, em um hotel ou em qualquer outro lugar fora da rede, o usuário deverá inserir um local?
    
    É possível definir a configuração **Local obrigatório** na política de local para definir o comportamento do cliente. Configurar este valor para Não significa que o usuário não será solicitado por um local. Configurar este valor para Sim significa que o usuário será solicitado por um local, mas pode ignorar a solicitação. A configuração deste valor para Isenção de responsabilidade significa que o usuário será solicitado por um local e exibirá uma isenção de responsabilidade se tentar ignorar a solicitação. De qualquer forma, o usuário pode contribuir com o uso do cliente, como sempre.

Quando um usuário insere manualmente um local, o local é mapeado para o endereço MAC do gateway padrão da rede do cliente, e é armazenado em uma tabela por usuário localizada no cliente. Quando o usuário retorna a qualquer local armazenado anteriormente, o cliente Lync se define automaticamente para esse local.

> [!NOTE]  
> É possível modificar somente o local atual de seu cliente, mas você também pode excluir qualquer local armazenado na tabela dos usuários locais.
