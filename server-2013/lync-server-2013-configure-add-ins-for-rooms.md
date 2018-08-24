---
title: 'Lync Server 2013: Configurar suplementos para salas'
TOCTitle: Configurar suplementos para salas
ms:assetid: 4eeaf19e-8369-4f6f-af65-a283cf7daa1c
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204878(v=OCS.15)
ms:contentKeyID: 49306679
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurar suplementos para salas no Lync Server 2013

 

_**Tópico modificado em:** 2013-02-21_

Em Painel de Controle do Lync Server 2013, você pode usar a seção **Suplemento** da página **Chat Persistente** para associar os URLs com as salas Chat Persistente. Essas URLs aparecem no cliente Lync 2013 na sala de chat no painel de extensibilidade da conversa. Um administrador deve adicionar os suplementos na lista de suplementos registrados e os gerentes/Criadores da sala de chat devem associar as salas comum dos suplementos registrados antes que os os usuários possam ver esse upgrade nos seus clientes Lync 2013 .

Os suplementos são usados para estender a experiência na sala. Um suplemento típico pode incluir um URL apontando para um aplicativo Silverlight que intercepta quando um cotação da bolsa é postada em uma sala de chat e exibe o histórico de ações no painel de extensibilidade. Outros exemplos incluem o URL do OneNote 2013 na sala de chat como um suplemento para incluir algum contexto compartilhado, como o "Mais lembrado" ou "Assunto do dia."

## Para configurar Suplementos para as salas de chat

1.  A partir de uma conta de usuário com a função CsPersistentChatAdministrator ou CsAdministrator atribuída, faça o logon em qualquer computador na sua implementação interna.

2.  No menu **Iniciar** , selecione o Painel de Controle do Lync Server ou abra uma janela de navegador e depois insira o URL de Admin. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).
    
    > [!IMPORTANT]  
    > Você também pode usar o cmdlets Windows PowerShell. Para obter detalhes, consulte <a href="configuring-persistent-chat-server-by-using-windows-powershell-cmdlets.md">Configurando Servidor de Chat Persistente usando cmdlets do Windows PowerShell</a> na documentação de Implantação.

3.  Na barra de navegação esquerda, clique em **Chat Persistente** e, em seguida, clique em **Suplementos** .
    
    Para múltiplas implantações Pool de Servidor de Chat Persistente, selecione o pool apropriado na lista suspensa.

4.  Na página **Suplementos** , clique em **Novo** .

5.  Em **Selecionar um serviço** , selecione o serviço correspondente ao Pool de Servidor de Chat Persistente onde você precisa criar o Suplemento. Os Suplementos não podem ser movidos de um pool a outro nem compartilhado entre pools diferentes.

6.  Em **Suplementos novos** , faça o seguinte:
    
      - Em **Nome** , especifique um nome para o novo suplemento.
    
      - Em **URL** , especifique o URL que deve ser associada ao suplemento. Os URLs são limitados aos protocolos http e https.

7.  Clique em **Confirmar** .

## Consulte Também

#### Tarefas

[Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md)  

#### Conceitos

[Configurando Servidor de Chat Persistente usando cmdlets do Windows PowerShell](configuring-persistent-chat-server-by-using-windows-powershell-cmdlets.md)

