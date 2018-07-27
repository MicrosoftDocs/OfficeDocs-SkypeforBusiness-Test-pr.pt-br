---
title: 'Lync Server 2013: Adicionar um Aplicativo de Filial Persistente ao Active Directory'
TOCTitle: Adicionar um Aplicativo de Filial Persistente ao Active Directory
ms:assetid: 3e63507c-d60b-40ec-8bbe-586b1d707c3e
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg425906(v=OCS.15)
ms:contentKeyID: 49306479
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Adicionar um Aplicativo de Filial Persistente ao Active Directory no Lync Server 2013

 

_**Tópico modificado em:** 2012-09-23_

Se você planejar implantar um Aparelho de Filial Persistente, adicione o Aparelho de Filial Persistente aos Serviços de Domínio Active Directory. Execute este procedimento no local central.

> [!IMPORTANT]  
> Execute este procedimento somente se você estiver implantando um Aparelho de Filial Persistente. Não o execute se estiver implantando um Servidor de Filial Persistente.

## Para adicionar um Aparelho de Filial Persistente aos Serviços de Domínio do Active Directory

1.  Faça logon em um servidor membro como um membro do grupo Administração de Empresa.

2.  Clique em **Iniciar**, depois em **Ferramentas Administrativas** e, em seguida, clique em **Usuários e Computadores do Active Directory** .

3.  No menu **Ações**, clique em **Novo** e, em seguida, clique em **Computador**.

4.  Na caixa de diálogo **Novo Objeto-Computador**, digite um nome para o objeto de computador do Aparelho de Filial Persistente (por exemplo, BranchOffice1) e clique em **Alterar**.

5.  Na caixa de diálogo **Selecionar Usuário ou Grupo**, adicione o grupo RTCUniversalSBATechnicians e clique em **OK**.
    
    > [!NOTE]  
    > Um membro do grupo RTCUniversalSBATechnicians no site da filial adicionará esse dispositivo ao domínio posteriormente.

6.  Clique em **OK** para salvar o objeto de computador Aparelho de Filial Persistente.

7.  Clique em **Iniciar**, em **Ferramentas Administrativas** e em **Editor ADSI** .

8.  No **Editor ADSI**, clique com o botão direito do mouse no objeto de computador que você criou nas etapas anteriores e clique em **Propriedades**.

9.  Na lista de atributos, clique em **servicePrincipalName** e em **Editar**.

10. No campo **Valor a ser adicionado**, digite HOST/\<SBA FQDN\> em que \<SBA FQDN\> é o nome de domínio totalmente qualificado do Aparelho de Filial Persistente. Por exemplo, digite **HOST/BranchOffice1.contoso.com** .

11. Clique em **OK** para salvar a configuração do atributo **servicePrincipalName** e, em seguida, clique em **OK** para salvar as propriedades do objeto de computador.

12. Em **Usuários e Computadores do Active Directory** , clique com o botão direito do mouse em **Usuários**, clique em **Novo** e em **Usuário**.

13. Insira as informações no assistente para criar uma conta de usuário de domínio para um técnico do Aparelho de Filial Persistente.

14. Em **Usuários e Computadores do Active Directory**, clique em **Usuários**, clique com o botão direito do mouse no objeto de usuário e clique em **Adicionar a um grupo**.

15. Em **Digite os nomes de objetos a serem selecionados**, digite **RTCUniversalSBATechnicians** e clique em **OK**.

16. Repita as etapas 12 a 15 para cada técnico do site de filial.

**Próxima etapa**: [Adicionar sites de filial a sua topologia no Lync Server 2013](lync-server-2013-add-branch-sites-to-your-topology.md)

