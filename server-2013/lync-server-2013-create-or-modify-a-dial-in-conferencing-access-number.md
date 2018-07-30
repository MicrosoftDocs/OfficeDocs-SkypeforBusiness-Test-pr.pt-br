---
title: 'Lync Server 2013: Criar ou modificar um número de acesso de conferência discada'
TOCTitle: Criar ou modificar um número de acesso de conferência discada
ms:assetid: 06f55c28-57f8-4d4e-8313-9740846796d9
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398126(v=OCS.15)
ms:contentKeyID: 49305774
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Criar ou modificar um número de acesso de conferência discada no Lync Server 2013

 

_**Tópico modificado em:** 2012-09-17_

Siga essas etapas se você quer criar ou modificar um número de acesso de discagem à conferência.

> [!IMPORTANT]  
> Antes de criar um novo número de acesso de discagem, você deve definir uma região de conferência discada no painel de discagem que está associado com o novo número de acesso de discagem. Vários planos de discagem pode usar a mesma região.

## Para criar ou modifica um número de acesso de discagem

1.  Usando uma conta de usuário atribuída à função CsUserAdministrator ou CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação à esquerda, clique em **Conferência** e, então, em **Número de acesso de discagem**.

4.  Na página **Número de Acesso de Discagem**, realize uma das ações a seguir:
    
      - Clique em **Novo** para abrir **Novo Número de Acesso de Discagem**.
    
      - Clique em um dos números de acesso de discagem na lista, clique em **Editar**, e clique em **Mostrar detalhes**.
        
        > [!NOTE]  
        > Usar o campo de busca para buscar pelos conteúdos de uma coluna na lista de números de acesso de discagem pode não apresentar os resultados esperados. Em vez disso, classifique a lista pela coluna de interesse para identificar o número de acesso de discagem a ser visualizado ou modificado.

5.  Em **Número para exibição**, digite o número de telefone que os usuários de telefone da rede telefônica pública comutada (PSTN) digitam para participar de uma conferência.
    
    > [!NOTE]  
    > Esse número é exibido em convites de reunião e na página da Web de Configurações de Conferência Discada.

6.  Em **Nome para exibição**, digite uma descrição para o número de acesso de discagem. Esse é o nome que é associado ao número de acesso de discagem nos resultados de busca do Lync.
    
    > [!NOTE]  
    > Esse nome é exibido no cliente quando um usuário disca o número de acesso.

7.  Em **URI da Linha**, digite o número E.164 do número de acesso de discagem em formato TEL URI, incluindo o símbolo + antes do número e excluindo espaços. Por exemplo, tel:+14255550200.
    
    > [!NOTE]  
    > O mesmo URI de Linha não pode ser reusada por outro número de acesso de conferência discada.

8.  Em **URI do SIP**, faça o seguinte:
    
      - Na caixa de texto, digite um único URI do SIP para o número de acesso de conferência discada. Esse URI do SIP é exibido em vários locais, incluindo, mas não limitado a, mensagens de notificação de ligações e versões anteriores dos clientes do Communicator.
        
        > [!NOTE]  
        > O mesmo URI do SIP não pode ser reusado por outro número de acesso de conferência discada. O URI do SIP não pode ser modificado depois de o número de acesso ter sido criado. A única maneira de altera o URI do SIP é excluir e recriar o número de acesso.    
      - Na caixa de listagem suspensa, clique no domínio do Aplicativo Atendedor de Conferência que dá suporte a esse número de acesso de discagem.

9.  Em **Pool**, clique no pool que está executado a instância Atendedor de Conferência que dá suporte ao número de acesso de discagem.
    
    > [!NOTE]  
    > Se foi preciso alterar o pool depois de criar o número de acesso, deve-se usar o cmdlet do <strong>Move-CsApplicationEndpoint</strong> cmdlet ou excluir e recriar o número de acesso.

10. Em **Idioma principal**, clique no idioma no qual as solicitações são reproduzidas nesse número de acesso.
    
    > [!NOTE]  
    > O idioma principal é o idioma que o Atendente de Conferência usa para atender a ligação. Os idiomas suportados são exibidos ao lado de cada número de acesso de discagem na página da Web das Configurações de Conferência Discada.

11. (Opcional) Em **Idiomas secundários (máximo de quatro)**, clique em **Adicionar**, selecione um ou mais idiomas adicionais que você quer oferecer aos chamadores para esse número de acesso de discagem, e clique em **OK**.
    
    > [!NOTE]  
    > É possível escolher até quatro idiomas secundários para cada número de acesso de discagem. Os usuários podem selecionar um idioma secundário antes de inserir o ID de conferência ao ligarem para uma.

12. Para adicionar uma região ao número de acesso de discagem, em **Regiões Associadas**, clique em **Adicionar**, clique em uma ou mais regiões associadas com os planos de discagem desse número de acesso de discagem e clique em **OK**.

13. Para excluir uma região do número de acesso de discagem, em **Regiões Associadas**, clique na região a ser excluída e clique em **Remover**.

14. Clique em **Confirmar**.

