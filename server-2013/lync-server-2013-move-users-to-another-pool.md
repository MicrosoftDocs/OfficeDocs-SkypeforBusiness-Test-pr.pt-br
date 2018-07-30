---
title: Mover usuários para outro pool
TOCTitle: Mover usuários para outro pool
ms:assetid: e7b4968c-0e9d-4d56-b5f1-9edf0f7206f8
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg182600(v=OCS.15)
ms:contentKeyID: 49308451
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Mover usuários para outro pool

 

_**Tópico modificado em:** 2013-03-11_

É possível usar o Painel de Controle do Lync Server para atribuir usuários a um servidor ou pool específico.


> [!TIP]
> Mover todos os usuários existentes de um pool de recursos que está executando o Microsoft Office Communications Server 2007 R2 ou anterior para um pool de destino do Lync Server 2013 em um ambiente complexo do Active Directory pode resultar em uma replicação mais lenta do Active Directory. Para evitar isso, é possível usar os filtros de pesquisa para mover usuários de pools que estão executando o Microsoft Office Communications Server 2007 R2 ou anterior separadamente, ou é possível usar o Shell de Gerenciamento do Lync Server para mover usuários com cmdlets. Além disso, a funcionalidade de filtro funciona com usuários do Lync Server 2013.



## Para mover os usuários selecionados para um outro servidor ou pool

1.  Usando uma conta de usuário atribuída à função CsUserAdministrator ou CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerda, clique em **Usuários**.

4.  Na caixa **Pesquisar usuários**, digite todo ou parte do nome de exibição, nome, sobrenome, nome de conta do SAM (Gerenciador de contas de segurança), endereço SIP ou URI (Uniform Resource Identifier) da linha da conta de usuário que você deseja e clique em **Localizar**.

5.  Na tabela, selecione um usuário específico ou usuários na lista.

6.  No menu **Ação**, clique em **Mover usuários selecionados para o pool**.

7.  Em **Mover Usuários**, selecione o pool para o qual você deseja mover os usuários em **Pool de registradores de destino**.

8.  (Opcional) Se o pool ou o servidor de destino não estiver disponível, marque a caixa de seleção **Forçar**.
    

    > [!WARNING]
    > Se você selecionar <STRONG>Forçar</STRONG>, a conta de usuário será movida, mas nenhum dado de usuário associado será excluído (por exemplo, conferências agendadas pelo usuário). Se essa opção não for selecionada, a conta e os dados associados serão movidos.



## Para mover todos os usuários de um servidor ou pool para outro servidor ou pool

1.  Usando uma conta de usuário atribuída à função CsUserAdministrator ou CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerda, clique em **Usuários**.

4.  No menu **Ação**, clique em **Mover todos os usuários para o pool**.

5.  Em **Mover Usuários**, selecione o pool que contenha as contas de usuário que você deseja mover no **Pool de registradores de origem**.

6.  Em **Pool de registradores de destino** , selecione o pool para o qual você deseja mover os usuários.

7.  (Opcional) Se o pool ou o servidor de destino não estiver disponível, marque a caixa de seleção **Forçar**.
    

    > [!WARNING]
    > Se você selecionar <STRONG>Forçar</STRONG>, a conta de usuário será movida, mas nenhum dado de usuário associado será excluído (por exemplo, conferências agendadas pelo usuário). Se essa opção não for selecionada, a conta e os dados associados serão movidos.



## Para mover usuários de um pool para um pool diferente usando um filtro

1.  Usando uma conta de usuário atribuída à função CsUserAdministrator ou CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerda, clique em **Usuários**.

4.  Em **Pesquisa de Usuário**, clique em **Pesquisar** e em **Adicionar Filtro**.

5.  Nos Critérios de pesquisa, selecione **Pool de Registradores**, selecione **Igual a**, selecione **FQDN Atual do Pool** e clique em **Localizar**.

6.  No menu **Ação**, clique em **Mover todos os usuários para o pool**.
    
    > [!NOTE]  
    > Quando um filtro é aplicado a um conjunto de usuário existente, a opção <strong>Mover todos os usuários para o pool</strong> está no contexto do subconjunto de usuários filtrados, não em <strong><em>todos</em></strong> os usuários possíveis.

7.  Em **Mover Usuários**, selecione o pool que contenha as contas de usuário que você deseja mover no **Pool de registradores de origem**.

8.  Em **Pool de registradores de destino** , selecione o pool para o qual você deseja mover os usuários.

9.  (Opcional) Se o pool ou o servidor de destino não estiver disponível, marque a caixa de seleção **Forçar**.
    

    > [!WARNING]
    > Se você selecionar <STRONG>Forçar</STRONG>, a conta de usuário será movida, mas nenhum dado de usuário associado será excluído (por exemplo, conferências agendadas pelo usuário e os contatos). Se essa opção não for selecionada, a conta e os dados associados serão movidos.



## Para mover usuários de um pool para outro usando o Shell de Gerenciamento do Lync

1.  Dependendo de como você executa comandos do Windows PowerShell (ou seja, local ou remotamente), é necessário fazer logon como membro das funções administrativas corretas do Lync Server 2013, da seguinte maneira:
    
    1.  Se você estiver executando os comandos no computador local (por exemple, faça logon diretamente em um Servidor Front-End): Faça logon no computador onde o Shell de Gerenciamento do Lync Server está instalado como um membro do grupo RTCUniversalServerAdmins ou com os direitos de usuário necessários, conforme descrito em [Delegar permissões de configuração no Lync Server 2013](lync-server-2013-delegate-setup-permissions.md).
    
    2.  Se você estiver executando os comandos remotamente em outro computador (por exemplo, você faz logon em seu computador e executa os comandos remotamente no Standard Edition Servidor Front-End): Usando uma conta de usuário atribuída à função CsUserAdministrator ou CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

3.  Para mover usuários único, use o cmdlet Move-CsUser da seguinte maneira:
    
        Move-CsUser -Identity "Pilar Ackerman" -Target "pool01.contoso.net"
    
    Quando o usuário a ser movido for Pilar Ackerman, e for movido de seu pool doméstico atribuído atualmente para o pool pool01.contoso.net

4.  Para mover muitos usuários, use os filtros com o cmdlet **Get-CsUser** e passe o conjunto resultante de usuários para **Move-CsUser**:
    
        Get-CsUser -Filter {RegistrarPool -eq "CurrentPoolFqdn"} | Move-CsUser -Target "TargetPoolFQDN"
    
    Os comandos combinados do **Get-CsUser** e do **Move-CsUser** podem resultar nisto:
    
        Get-CsUser -Filter {RegistrarPool -eq "pool02.contoso.net"} | Move-CsUser -Target "pool01.contoso.net"

## Consulte Também

#### Outros Recursos

[Modificando as Propriedades da Conta do Usuário](lync-server-2013-modifying-user-account-properties.md)

