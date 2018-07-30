---
title: Atribuir uma política de local por usuário
TOCTitle: Atribuir uma política de local por usuário
ms:assetid: 343f2de3-a0ae-4403-8456-6e520b579d32
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg520974(v=OCS.15)
ms:contentKeyID: 49306333
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Atribuir uma política de local por usuário

 

_**Tópico modificado em:** 2013-02-22_

A política de local é uma das configurações individuais de uma conta de usuário que você pode definir no Painel de Controle do Lync Server.

Implantar uma ou mais políticas de local por usuário é opcional. Você também pode implantar somente uma política local nos níveis global ou de sub-rede. Se você implantar políticas por usuário, deverá atribui-las explicitamente a usuários, grupos ou objetos de contato. As configurações aprimoradas do 9-1-1 (E9-1-1) usam por padrão automaticamente as definidas na política de local de nível global, quando nenhuma política específica no nível da sub-rede ou por usuário é atribuída.

Depois de criar pelo menos uma política de local por usuário, use os procedimentos deste tópico para atribuir à política que determina as configurações que o servidor deverá aplicar às chamadas de emergência feitas por um usuário específico.

Para obter uma lista de todas as configurações da política de local disponíveis, consulte [Definindo a política de local para Lync Server 2013](lync-server-2013-defining-the-location-policy.md).

Para ver os detalhes sobre criar as políticas de local, consulte [Criar políticas de localização no Lync Server 2013](lync-server-2013-create-location-policies.md).

## Para atribuir uma política de local por usuário

1.  Usando uma conta de usuário atribuída à função CsUserAdministrator ou CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação da esquerda, clique em **Usuários**.

4.  Use um dos métodos a seguir para localizar um usuário:
    
      - Na caixa **Pesquisar usuários**, digite tudo ou a primeira parte do por nome para exibição, nome, sobrenome, nome da conta do SAM (Gerenciador de Contas de Segurança), endereço SIP ou linha de URI (Uniform Resource Identifier) da conta de usuário, e clique em **Localizar**.
    
      - Se você tem uma consulta salva, clique no ícone **Abrir consulta**, use a caixa de diálogo **Abrir** para recuperar a consulta (um arquivo .usf), e clique em **Localizar**.

5.  (Opcional) Especifique critérios de pesquisa adicionais para reduzir os resultados:
    
    1.  Clique em **Adicionar filtro**.
    
    2.  Insira a propriedade do usuário, digitando-a ou clicando na seta na lista suspensa para selecioná-la.
    
    3.  Na lista suspensa **Igual a** clique no operador (por exemplo, **Igual a** ou **Não igual a**).
    
    4.  Dependendo da propriedade do usuário selecionada, insira os critérios que você deseja usar para filtrar os resultados pesquisa, digitando-os ou clicando na seta na lista suspensa.
        

        > [!TIP]
        > Para adicionar cláusulas de pesquisa à sua consulta, clique em <STRONG>Adicionar filtro</STRONG>.

    
    5.  Clique em **Localizar**.

6.  Clique em um usuário nos resultados da pesquisa, clique em **Ação** e em **Atribuir políticas**.
    

    > [!TIP]
    > Se você deseja aplicar a mesma política de local para usuários múltiplos, selecione os usuários nos resultados da pesquisa e clique em <STRONG>Ações</STRONG> e em <STRONG>Atribuir políticas</STRONG>.



7.  Em **Atribuir políticas**, em **Política de local**, siga um destes procedimentos:
    
    > [!NOTE]  
    > Uma vez que há várias políticas que podem ser configuradas na caixa de diálogo <strong>Atribuir políticas</strong>, <strong>&lt;Manter como está&gt;</strong> é selecionado por padrão para cada política na caixa de diálogo. Para continuar usando a política previamente atribuída ao usuário, basta não fazer nenhuma alteração nessa configuração.    
      - Permita Lync Server 2013 para escolher a política de nível global automaticamente ou, se definido, a política de nível de sub-rede.
    
      - Clique no nome de uma política de local por usuário que você definiu previamente, executando o cmdlet **New-CsLocationPolicy**.
        

        > [!TIP]
        > Para ajudar a decidir qual política você deseja atribuir, depois de clicar no nome da política, clique em <STRONG>Exibir</STRONG> para ver os direitos de usuário e as permissões definidas.



8.  Quando terminar, clique em **OK**.

## Para atribuir uma política de local por usuário usando o Shell de Gerenciamento do Lync Server

É possível atribuir políticas de local por usuário usando o cmdlet Grant-CsLocationPolicy. É possível executar esse cmdlet no Shell de Gerenciamento do Lync Server 2013 ou em uma sessão remota do Windows PowerShell. Para obter detalhes sobre como usar o Windows PowerShell remoto para conectar ao Lync Server, consulte o artigo de blog do Lync Server Windows PowerShell, "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" em [http://go.microsoft.com/fwlink/p/?linkId=255876 (em inglês)](http://go.microsoft.com/fwlink/p/?linkid=255876).

## Para atribuir um política de local por usuário a um único usuário

  - O comando a seguir atribui a política de local por usuário RedmondLocationPolicy ao usuário Ken Myer.
    
        Grant-CsLocationPolicy -Identity "Ken Myer" -PolicyName "RedmondLocationPolicy"

## Para atribuir uma política de local por usuário a vários usuários

  - Este comando atribui a política de local por usuário AccountingDepartmentLocationPolicy a todos os usuários que trabalham no departamento contábil. Para obter mais informações sobre o parâmetro LdapFilter usado nesse comando, consulte a documentação do cmdlet [Get-CsUser](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsUser).
    
        Get-CsUser -LdapFilter "Department=Accounting" | Grant-CsLocationPolicy -PolicyName "AccountingDepartmentLocationPolicy"

## Para desfazer a atribuição de uma política de local por usuário

  - O comando a seguir desfaz a atribuição de qualquer política de local por usuário atribuída a Ken Myer. Depois que a atribuição da política for desfeita, Ken Myer será automaticamente gerenciado usando a política global ou, se houver, sua política de site local. Uma política de site tem preferência sobre a política global.
    
        Grant-CsLocationPolicy -Identity "Ken Myer" -PolicyName $Null

Para obter mais informações, consulte o tópico de ajuda do cmdlet [Grant-CsLocationPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Grant-CsLocationPolicy).

