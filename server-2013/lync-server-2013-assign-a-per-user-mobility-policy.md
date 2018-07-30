---
title: Atribuir uma política de mobilidade por usuário
TOCTitle: Atribuir uma política de mobilidade por usuário
ms:assetid: d8bf997f-4bc7-48d3-973b-323505f55e9d
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ721902(v=OCS.15)
ms:contentKeyID: 49886435
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Atribuir uma política de mobilidade por usuário

 

_**Tópico modificado em:** 2013-02-22_

A política de mobilidade é uma das configurações individuais de uma conta de usuário que você pode definir no Painel de Controle do Lync Server ou Shell de Gerenciamento do Lync Server.

## Para atribuir uma política de mobilidade por usuário no Painel de Controle do Lync Server

1.  Usando uma conta de usuário atribuída à função CsUserAdministrator ou CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerda, clique em **Usuários**.

4.  Use um dos seguintes métodos para localizar um usuário:
    
      - Na caixa **Pesquisar usuários**, digite todo ou parte do nome de exibição, nome, sobrenome, nome da conta SAM, endereço SIP ou URI de linha da conta do usuário e clique em **Localizar**.
    
      - Se você salvou uma consulta, clique no ícone **Abrir consulta**, use a caixa de diálogo **Abrir** para recuperar a consulta (um arquivo .usf) e clique em **Localizar**.

5.  (Opcional) Especifique o critério de pesquisa adicional para reduzir os resultados:
    
    1.  Clique em **Adicionar filtro**.
    
    2.  Insira a propriedade do usuário digitando ou clicando na seta da lista suspensa para selecionar a propriedade.
    
    3.  Na lista suspensa **Igual a**, clique no operador (por exemplo, **Igual a** ou **Diferente de**).
    
    4.  Dependendo da propriedade do usuário selecionada, insira o critério que deseja usar para filtrar os resultados de pesquisa digitando ou clicando na seta da lista suspensa.
        

        > [!TIP]
        > Para adicionar cláusulas de pesquisa adicionais à sua consulta, clique em <STRONG>Adicionar filtro</STRONG>.

    
    5.  Clique em **Localizar**.

6.  Clique em um usuário nos resultados da pesquisa, clique em **Ação** e em **Atribuir políticas**.
    

    > [!TIP]
    > Se você deseja aplicar a mesma política de mobilidade para usuários múltiplos, selecione os usuários nos resultados da pesquisa e clique em <STRONG>Ações</STRONG> e em <STRONG>Atribuir políticas</STRONG>.



7.  Em **Atribuir políticas**, em **Política de mobilidade**, siga um destes procedimentos:
    
    > [!NOTE]  
    > Como há várias políticas que você pode configurar em <strong>Atribuir políticas</strong>, <strong>&lt;Manter&gt;</strong> é selecionado por padrão para cada política na caixa de diálogo. Continue a usar a política atribuída anteriormente ao usuário sem realizar alterações nesta configuração.    
      - Selecione **\<Automático\>** para permitir que o Lync Server 2013 escolha automaticamente a política a nível global ou, se definida, a política a nível de site.
    
      - Clique no nome de uma política de mobilidade por usuário definida anteriormente na página **Política de mobilidade**.
        

        > [!TIP]
        > Para ajudar a decidir a política que deseja atribuir, após clicar no nome da política, clique em <STRONG>Exibir</STRONG> para ver os direitos e permissões do usuário definidos na política.



8.  Ao concluir, clique em **OK**.

## Atribuir uma política de mobilidade por usuário utilizando cmdlets do Shell de Gerenciamento do Lync Server

É possível atribuir políticas de mobilidade por usuário utilizando o Shell de Gerenciamento do Lync Server e o cmdlet **Grant-CsMobilityPolicy**. É possível executar este cmdlet do Shell de Gerenciamento do Lync Server 2013 ou de uma sessão remota do Windows PowerShell. Para obter detalhes sobre como usar o Windows PowerShell remoto para conectar ao Lync Server, consulte o artigo de blog do Lync Server Windows PowerShell, "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" em [http://go.microsoft.com/fwlink/p/?linkId=255876 (em inglês)](http://go.microsoft.com/fwlink/p/?linkid=255876).

## Para atribuir uma política de mobilidade por usuário a um único usuário

  - O seguinte comando atribui a política de mobilidade por usuário RedmondMobilityPolicy ao usuário Ken Myer.
    
        Grant-CsMobilityPolicy -Identity "Ken Myer" -PolicyName "RedmondMobilityPolicy"

## Para atribuir uma política de mobilidade por usuário a vários usuários

  - O seguinte comando atribui a política de mobilidade por usuário RedmondMobilityPolicy para todos os usuários atualmente atribuídos com a política NorthAmericaMobilityPolicy. Para obter detalhes sobre o parâmetro Filter usado neste comando, consulte [Get-CsUser](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsUser).
    
        Get-CsUser -Filter {MobilityPolicy -eq "NorthAmericaMobilityPolicy"} | Grant-CsMobilityPolicy -PolicyName "RedmondMobilityPolicy"

## Para retirar a atribuição de uma política de mobilidade por usuário

  - O seguinte comando retira a atribuição de qualquer política de mobilidade por usuário atribuída anteriormente a Ken Myer. Após a política por usuário ser retirada, Ken Myer será automaticamente gerenciado utilizando a política global ou, se existir, sua política de site local. Uma política de site tem precedência sobre a política global.
    
        Grant-CsMobilityPolicy -Identity "Ken Myer" -PolicyName $Null

Para obter detalhes, consulte [Grant-CsMobilityPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Grant-CsMobilityPolicy).

## Consulte Também

#### Tarefas

[Configurando a política de mobilidade no Lync Server 2013](lync-server-2013-configuring-mobility-policy.md)

