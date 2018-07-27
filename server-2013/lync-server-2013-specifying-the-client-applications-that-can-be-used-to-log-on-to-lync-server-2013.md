---
title: Especificando aplicativos de client que podem ser usados para fazer logon no Lync Server 2013
TOCTitle: Especificando aplicativos de client que podem ser usados para fazer logon no Lync Server 2013
ms:assetid: d256a581-9a48-4d1a-82cc-2e1f520d7d2e
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg182591(v=OCS.15)
ms:contentKeyID: 49308205
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Especificando aplicativos de client que podem ser usados para fazer logon no Lync Server 2013

 

_**Tópico modificado em:** 2012-12-11_

O Lync Server 2013 permite especificar a versão dos clientes que são compatíveis com o seu ambiente. Quando dois clientes que executam versões diferentes interagem, os recursos disponíveis de um cliente podem ficar limitados devido às capacidade do outro cliente. Para maximizar a utilização dos recursos incluídos no Lync Server 2013 e para melhorar a experiência geral do usuário, é possível usar o filtro de versão do cliente para restringir as versões do cliente que são usadas no seu ambiente do Lync Server 2013. Usando o filtro de versão do cliente, também é possível reduzir os custos associados ao suporte de várias versões de clientes.

Além de criar uma política global, é possível criar políticas de versão do cliente para um serviço ou site específico ou políticas com escopo no usuário que podem ser atribuídas a usuários individuais. A política de versão cliente com escopo no usuário pode ser atribuída a usuários individuais a partir do grupo **Usuários** no Painel de Controle do Lync Server.

> [!NOTE]  
> Como os usuários anônimos não são associados a um usuário, site ou serviço, eles são afetados somente por políticas de nível global.

> [!IMPORTANT]  
> Os filtros são listados em ordem de precedência. Por exemplo, se você tiver um filtro que permite a conexão de clientes que executam a versão 1.5 ou mais recente, seguido por um filtro que bloqueia os clientes executando uma versão anterior a 2.0, o primeiro filtro terá precedência e os clientes que executam a versão 1.5 terão permissão para se conectar.

## Para editar a política de versão de cliente padrão

1.  Usando uma conta de usuário atribuída à função CsUserAdministrator ou CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerda, clique em **Clientes**.
    
    > [!NOTE]  
    > A guia <strong>Política de Versões de Clientes</strong> está selecionada por padrão.

4.  Na página **Política de Versões de Clientes**, clique duas vezes na política **Global** na lista.

5.  Em **Editar Política de Versões de Clientes**, execute uma das seguintes ações:
    
      - Clique em **Nova** para criar uma nova regra de versão de cliente.
    
      - Clique em um dos tipos de cliente definidos na lista e em **Mostrar detalhes**.
    
    > [!NOTE]  
    > É possível usar caracteres curinga para indicar o tipo de cliente.

6.  Em **Agente do usuário**, selecione um tipo de cliente.

7.  Em **Número de versão**, faça o seguinte:
    
      - Em **Versão principal**, digite o número que corresponde à versão principal do cliente.
    
      - Em **Versão secundária**, digite o número que corresponde à versão secundária do cliente.
    
      - Em **Compilação**, digite o número que corresponde à versão principal e secundária do cliente.
    
      - Em **Atualização**, digite o número que corresponde à versão atualizada do cliente.
    
    > [!NOTE]  
    > Você pode usar caracteres curinga para indicar o número da versão do cliente.

8.  Para especificar a operação correspondente para a versão do cliente especificada nas etapas anteriores, em **Operação de comparação**, clique em um dos seguintes:
    
      - **Igual a**
    
      - **Não é**
    
      - **Mais novo que**
    
      - **Mais novo ou igual a**
    
      - **Mais antigo que**
    
      - **Mais antigo ou igual a**

9.  Para especificar a ação a ser executada quando os critérios nas etapas anteriores forem atendidos, clique em uma das seguintes opções em **Ação**:
    
      - Para permitir o logon do cliente, clique em **Permitir**.
    
      - Para permitir que o cliente faça o login e receba atualizações do Windows Server Update Service ou Microsoft Update, clique em **Permitir e atualizar**. Esta seção está disponível apenas quando o agente de usuário **OC** é selecionado.
        
        > [!NOTE]  
        > Selecionar esta ação faz com que uma notificação seja exibida na próxima vez que o usuário fizer o login em um Lync 2013. A notificação declara que uma atualização está disponível, mesmo se as atualizações ainda não tiverem sido lançadas pelo Windows Server Update Service ou Microsoft Update. Para evitar confusão, você deve escolher esta ação apenas após as atualizações se tornarem disponíveis.    
      - Para permitir que o cliente faça logon e exiba uma mensagem sobre onde baixar outra versão de cliente, clique em **Permitir com URL**. Você especifica a URL posteriormente neste procedimento.
    
      - Para impedir que o cliente faça logon, clique em **Bloquear**.
    
      - Para evitar que o cliente faça o login e permitir que ele receba atualizações do Windows Server Update Service ou Microsoft Update, clique em **Bloquear e atualizar**. Esta ação está disponível apenas quando o agente do usuário **OC** é selecionado.
    
      - Para impedir o cliente de fazer logon e exibir uma mensagem sobre onde baixar outra versão de cliente, clique em **Bloquear com URL**. Você especifica a URL posteriormente neste procedimento.

10. (Opcional) se você clicou em **Permitir com URL** ou **Bloquear com URL** na etapa anterior, digite a URL de download do cliente para incluir na mensagem em **URL**.

11. Clique em **OK** e clique em **Confirmar**.

## Consulte Também

#### Outros Recursos

[Gerenciando dispositivos, telefones e aplicativos do cliente no Lync Server 2013](lync-server-2013-managing-devices-phones-and-client-applications.md)

