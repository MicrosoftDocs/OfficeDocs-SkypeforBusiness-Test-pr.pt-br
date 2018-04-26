---
title: 'Lync Server 2013: Permissões de usuário autenticado são removidas'
TOCTitle: Permissões de usuário autenticado são removidas
ms:assetid: 5fcd70a5-813a-4076-9bb6-5b0d47505038
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398425(v=OCS.15)
ms:contentKeyID: 49306867
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Permissões de usuário autenticado são removidas no Lync Server 2013

 

_**Tópico modificado em:** 2013-02-21_

Em um ambiente bloqueado do Active Directory, as ACEs (entradas de controle de acesso) de usuário autenticado são removidas dos contêineres padrão do Active Directory, incluindo Usuários, Configuração ou Sistema, e de unidades organizacionais em que objetos de Usuário e Computador estão armazenados. A remoção das ACEs de usuário autenticado impede o acesso de leitura às informações do Active Directory. Entretanto, a remoção das ACEs cria problemas para o Lync Server 2013, pois ele depende das permissões de leitura nesses contêineres para permitir que os usuários executem a preparação do domínio.

Nessa situação, o membro do grupo Admins. do Domínio, que é necessário para executar a preparação do domínio, a ativação do servidor e a criação de pool, não concede acesso de leitura às informações do Active Directory armazenadas em contêineres padrão. Você deve conceder manualmente as permissões de acesso de leitura em vários contêineres no domínio raiz da floresta para verificar se o procedimento de pré-requisito de preparação da floresta foi concluído.

Para permitir que um usuário execute a preparação do domínio, a ativação do servidor e a criação do pool em qualquer domínio raiz que não seja da floresta, você tem as seguintes opções:

  - Use uma conta que seja membro do grupo Admins. do Domínio para executar a preparação de domínio.

  - Usar uma conta que seja membro do grupo Admins. do Domínio e conceder a essa conta permissões de acesso de leitura em cada um dos seguintes contêineres no domínio raiz da floresta:
    
      - Domínio
    
      - Configuração ou Sistema

Se você não deseja usar uma conta que seja membro do grupo Administradores de Empresa para executar a preparação do domínio ou outras tarefas de instalação, conceda explicitamente acesso de leitura à conta que você deseja usar nos contêineres relevantes da raiz da floresta.

## Para conceder permissões de acesso de leitura a usuários em contêineres do domínio raiz da floresta

1.  Faça logon no computador associado ao domínio raiz da floresta com uma conta que seja membro do grupo Admins. do Domínio para o domínio raiz da floresta.

2.  Execute adsiedit.msc para o domínio raiz da floresta.
    
    Se as ACEs de usuário autenticado tiverem sido removidas do contêiner Domínio, Configuração ou Sistema, você deverá conceder permissões somente leitura no contêiner, conforme descrito nas etapas a seguir.

3.  Clique com o botão direito do mouse no contêiner e clique em **Propriedades**.

4.  Clique na guia **Segurança**.

5.  Clique em **Avançado**.

6.  Na guia **Permissões**, clique em **Adicionar**.

7.  Digite o nome do usuário ou grupo recebe permissões usando o seguinte formato: `domain\account name` e clique em **OK**.

8.  Na guia **Objetos**, em **Aplica-se a**, clique em **Somente Este Objeto**.

9.  Em **Permissões**, selecione as seguintes ACEs permitidas clicando na coluna **Permitir** : **Listar Conteúdo**, **Ler Todas as Propriedades** e **Permissões de Leitura**.

10. Clique em **OK** duas vezes.

11. Repita essas etapas para qualquer contêiner relevante listado na Etapa 2.

