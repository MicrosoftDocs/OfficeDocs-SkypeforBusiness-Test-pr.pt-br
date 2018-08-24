---
title: Criar ou modificar uma nova regra da política de versão do cliente
TOCTitle: Criar ou modificar uma nova regra da política de versão do cliente
ms:assetid: 6f879d99-8401-41e0-a562-195c890d63ea
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ898478(v=OCS.15)
ms:contentKeyID: 52057633
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Criar ou modificar uma nova regra da política de versão do cliente

 

_**Tópico modificado em:** 2013-01-21_

As regras de diretiva de versão de cliente definem as ações que devem ser executadas quando o usuário tenta fazer logon com clientes e versões de clientes específicas. Você pode criar ou modificar regras específicas para a versão de cliente do Painel de Controle do Lync Server 2013.

> [!IMPORTANT]  
> As regras foram listadas em ordem de precedência. Por exemplo, se você tiver uma regra que permita aos clientes executarem a versão 1.5 para se conectar, seguida pela regra que bloqueia os clientes que estiverem executando uma versão anterior à 2.0, a primeira regra tem precedência e os clientes que estiverem executando a versão 1.5 podem se conectar.

## Para criar ou modificar a versão das regras de diretiva de versão de cliente com o Painel de Controle do Lync Server

1.  [Criar ou modificar uma nova política de versão do cliente](lync-server-2013-create-or-modify-a-new-client-version-policy.md) com Painel de Controle do Lync Server.

2.  Na página **Editar Política de Versões de Clientes**, faça o seguinte:
    
      - Clique em **Nova** para criar uma nova regra de versão de cliente.
    
      - Clique em um dos tipos de cliente definidos na lista e em **Mostrar detalhes**.
    
    > [!NOTE]  
    > É possível usar caracteres curinga para indicar o tipo de cliente.

3.  Em **Agente do usuário**, selecione um tipo de cliente.

4.  Em **Número de versão**, faça o seguinte:
    
      - Em **Versão principal**, digite o número que corresponde à versão principal do cliente.
    
      - Em **Versão secundária**, digite o número que corresponde à versão secundária do cliente.
    
      - Em **Compilação**, digite o número que corresponde à versão principal e secundária do cliente.
    
      - Em **Atualização**, digite o número que corresponde à versão atualizada do cliente.
    
    > [!NOTE]  
    > Você pode usar caracteres curinga para indicar o número da versão do cliente.

5.  Para especificar a operação correspondente para a versão do cliente especificada nas etapas anteriores, em **Operação de comparação**, clique em um dos seguintes:
    
      - **Igual a**
    
      - **Não é**
    
      - **Mais novo que**
    
      - **Mais novo ou igual a**
    
      - **Mais antigo que**
    
      - **Mais antigo ou igual a**

6.  Para especificar a ação a ser executada quando os critérios nas etapas anteriores forem atendidos, clique em uma das seguintes opções em **Ação**:
    
      - Para permitir o logon do cliente, clique em **Permitir**.
    
      - Para permitir que o cliente faça o login e receba atualizações do Windows Server Update Service ou Microsoft Update, clique em **Permitir e atualizar**. Esta seção está disponível apenas quando o agente de usuário **OC** é selecionado.
        
        > [!NOTE]  
        > Selecionar esta ação faz com que uma notificação seja exibida na próxima vez que o usuário fizer o login em um Lync 2013. A notificação declara que uma atualização está disponível, mesmo se as atualizações ainda não tiverem sido lançadas pelo Windows Server Update Service ou Microsoft Update. Para evitar confusão, você deve escolher esta ação apenas após as atualizações se tornarem disponíveis.    
      - Para permitir que o cliente faça logon e exiba uma mensagem sobre onde baixar outra versão de cliente, clique em **Permitir com URL**. Você especifica a URL posteriormente neste procedimento.
    
      - Para impedir que o cliente faça logon, clique em **Bloquear**.
    
      - Para evitar que o cliente faça o login e permitir que ele receba atualizações do Windows Server Update Service ou Microsoft Update, clique em **Bloquear e atualizar**. Esta ação está disponível apenas quando o agente do usuário **OC** é selecionado.
    
      - Para impedir o cliente de fazer logon e exibir uma mensagem sobre onde baixar outra versão de cliente, clique em **Bloquear com URL**. Você especifica a URL posteriormente neste procedimento.

7.  (Opcional) se você clicou em **Permitir com URL** ou **Bloquear com URL** na etapa anterior, digite a URL de download do cliente para incluir na mensagem em **URL**.

8.  Clique em **OK** e clique em **Confirmar**.

