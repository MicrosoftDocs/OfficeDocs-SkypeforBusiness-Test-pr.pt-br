---
title: 'Lync Server 2013: Testar o servidor de Edição Padrão'
TOCTitle: Testar o servidor de Edição Padrão
ms:assetid: b6ef67bb-9665-43e4-b8b3-eac8898eebf6
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg412890(v=OCS.15)
ms:contentKeyID: 49307889
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Testar o servidor de Edição Padrão no Lync Server 2013

 

_**Tópico modificado em:** 2012-10-01_

O seguinte procedimento descreve como testar a implantação de uma Servidor Standard Edition.

## Para testar a implantação de um servidor Standard Edition

1.  Use Computadores e Usuários do Active Directory para adicionar o objeto do usuário do Active Directory da função de administrador para a implantação do Lync Server 2013 (na qual o Painel de Controle do Lync Server está instalado) para o grupo **CSAdministrator**.

2.  Se o objeto do usuário está conectado atualmente, desconecte e conecte-se novamente para registrar a nova atribuição de grupo.
    
    > [!NOTE]  
    > A conta de usuário não pode ser o administrador local do servidor executando Lync Server 2013, Standard Edition. Se você não adicionar os usuários e grupos apropriados ao grupo CsAdministors, você receberá um erro ao abrir Painel de Controle do Lync Server 2013, que informa “Não autorizado: acesso negado devido a uma falha na autorização de RBAC (controle de acesso baseado na função).”

3.  Use a conta administrativa para fazer o login no computador onde o Painel de Controle do Lync Server está instalado.

4.  Inicie o Painel de Controle do Lync Server e forneça credenciais, se for solicitado. O Painel de Controle do Lync Server 2013 exibe informações sobre a implantação.

5.  Na barra de navegação esquerda, clique em **Topologia** e confirme que o status do serviço é um ícone de computador com uma seta verde e se há uma marca de seleção verde ao lado de cada função de servidor do Lync Server que foi implantada e colocada online.

6.  Na barra de navegação esquerda, clique em **Usuários** e habilite os dois usuários para Lync Server 2013.

7.  Faça logon de um usuário no computador que ingressou no domínio e do outro usuário em outro computador no domínio.

8.  Instale o Lync Server 2013 em cada um dos dois computadores clientes e verifique se ambos os usuários podem se conectar ao Lync Server 2013 e enviar mensagens instantâneas um para o outro.

## Consulte Também

#### Conceitos

[Implantando clientes e dispositivos no Lync Server 2013](lync-server-2013-deploying-clients-and-devices.md)

