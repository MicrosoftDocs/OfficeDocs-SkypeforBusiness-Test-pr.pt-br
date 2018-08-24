---
title: 'Lync Server 2013: Testar a implantação de pool '
TOCTitle: 'Testar a implantação de pool '
ms:assetid: ffd80617-155a-4041-bbeb-74503e7938dd
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg413092(v=OCS.15)
ms:contentKeyID: 49308729
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Testar a implantação de pool no Lync Server 2013

 

_**Tópico modificado em:** 2013-09-25_

The following procedure describes how to test the deployment of the Pool de Front-Ends.

## Para testar a implantação do pool

1.  Use Computadores e Usuários do Active Directory para adicionar o objeto do usuário do Active Directory da função de administrador para a implantação do Lync Server 2013 (na qual o Painel de Controle do Lync Server 2013 está instalado) para o grupo **CSAdministrator** .
    
    > [!IMPORTANT]  
    > Se você não adicionar os usuários e grupos apropriados ao grupo CsAdministors, receberá um erro ao abrir o Painel de Controle do Lync Server, afirmando que &quot;Não autorizado: acesso negado devido a uma falha de autorização do controle de acesso baseado em função (RBAC).&quot;

2.  Se o objeto do usuário está conectado atualmente, desconecte e conecte-se novamente para registrar a nova atribuição de grupo.
    
    > [!NOTE]  
    > A conta de usuário não pode ser o administrador local de qualquer servidor executando o Lync Server 2013.

3.  Use a conta administrativa para fazer o login no computador onde o Painel de Controle do Lync Server está instalado.

4.  Inicie o Painel de Controle do Lync Server e forneça as credenciais se solicitado. O Painel de Controle do Lync Server exibe as informações sobre a implantação.

5.  Na barra de navegação esquerda, clique em **Topologia** e confirme se o status do serviço mostra um computador com uma seta verde e que uma marca de seleção verde para status de replicação está próxima a cada função do servidor do Lync Server que foi implantada e colocada online.

6.  Na barra de navegação esquerda, clique em **Usuários** e em **Habilitar usuários** .

7.  Na página **Novo usuário do Lync Server** , clique em **Adicionar** .

8.  Para definir os parâmetros de pesquisa para os objetos que deseja localizar, na página **Selecionar do Active Directory** , você pode selecionar **Pesquisa** e, opcionalmente, clique em **Adicionar filtro** . Também é possível selecionar **Pesquisa LDAP** e inserir uma expressão LDAP para filtrar ou limitar os objetos que serão retornados. Após decidir suas opções de pesquisa, clique em **Localizar** .

9.  No painel de resultados da pesquisa, selecione todos os objetos para esta sessão de pesquisa e clique em **OK** .

10. Na página **Novo usuário do Lync Server** , o objeto ou objetos selecionados estão na tela **Usuários** . Em **Atribuir usuários a uma lista de pools** , selecione o servidor onde os objetos devem ser hospedados.
    
    A seguir estão várias opções para configurar os objetos.
    
      - **Gerar o URI SIP do usuário**
    
      - **Telefonia**
    
      - **URI de linha**
    
      - **Política de conferência**
    
      - **Política de versão do cliente**
    
      - **Política de PIN**
    
      - **Política de acesso externo**
    
      - **Política de arquivamento**
    
      - **Política local**
    
      - **Política do cliente**
    
    Para fins de teste da funcionalidade básica, selecione a opção que preferir para a configuração **Gerar URI SIP do usuário** (as outras opções na configuração usarão as configurações padrões) e clique em **Habilitar** .

11. Será exibida uma página de resumo mostrando uma marca de verificação na coluna **Habilitado** coluna para indicar que os objetos agora estão prontos para uso. A coluna **Endereço SIP** exibe o endereço necessário para a configuração de login do usuário.

12. Faça o login de um usuário em um computador que esteja conectado ao domínio e outro usuário em outro computador no domínio.

13. Instale o Lync 2013 em cada um dos dois computadores clientes e verifique se ambos os usuários podem se conectar ao Lync Server 2013 e enviar mensagens instantâneas um para o outro.

## Consulte Também

#### Conceitos

[Implantando clientes e dispositivos no Lync Server 2013](lync-server-2013-deploying-clients-and-devices.md)

