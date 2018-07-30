---
title: Exibir informações de PIN do uusário
TOCTitle: Exibir informações de PIN do uusário
ms:assetid: 59e38117-8112-4851-82ac-a746ffa0f89d
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ688067(v=OCS.15)
ms:contentKeyID: 49886231
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Exibir informações de PIN do uusário

 

_**Tópico modificado em:** 2013-02-23_

Para ingressar em uma conferência de discagem como usuário autenticado, um usuário do Lync Server 2013 com credenciais do AD DS (Serviços de Domínio Active Directory) precisa de um PIN (número de identificação pessoal). Você pode exibir as informações de PIN de um usuário no Painel de Controle do Lync Server 2013.

> [!NOTE]  
> Você pode exibir as informações de status de PIN, como se o PIN foi definido ou quando ele foi alterado pela última vez, mas não pode ver o PIN atual consultando o status de PIN. Se um usuário perder seu PIN, você poderá redefini-lo seguindo os procedimentos em <a href="lync-server-2013-set-a-user-s-dial-in-conferencing-pin.md">Configurar PIN de conferência discada de um usuário no Lync Server 2013</a>

## Para exibir o PIN de um usuário no Painel de Controle do Lync Server

1.  Usando uma conta de usuário atribuída à função CsUserAdministrator ou CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerda, clique em **Usuários**.

4.  Use um dos seguintes métodos para localizar um usuário:
    
      - Na caixa **Pesquisar usuários**, digite todo ou parte do nome de exibição, nome, sobrenome, nome da conta de SAM (Gerente de Contas de Segurança), endereço SIP ou URI de linha da conta do usuário e clique em **Localizar**.
    
      - Se você salvou uma consulta, clique no ícone **Abrir consulta**, use a caixa de diálogo **Abrir** para recuperar a consulta (um arquivo .usf) e clique em **Localizar**.

5.  (Opcional) Especifique critérios de pesquisa adicionais para restringir os resultados:
    
    1.  Clique em **Adicionar filtro**.
    
    2.  Insira a propriedade do usuário digitando-a ou clicando na seta da lista suspensa para selecionar a propriedade.
    
    3.  Na lista suspensa **Igual a**, clique em um operador (por exemplo, **Igual a** ou **Diferente de**).
    
    4.  Dependendo da propriedade de usuário selecionada, insira os critérios que você deseja usar para filtrar os resultados da pesquisa digitando-os ou clicando na seta da lista suspensa.
        

        > [!TIP]
        > Para inserir cláusulas de pesquisa adicionais à sua consulta, clique em <STRONG>Adicionar filtro</STRONG>.

    
    5.  Clique em **Localizar**.
    
    > [!NOTE]  
    > Se o PIN estiver bloqueado, você deverá desbloqueá-lo para poder defini-lo. Para desbloquear o PIN, clique no usuário, clique em <strong>Ação</strong> e depois em <strong>Desbloquear PIN</strong>.

6.  Clique em um usuário nos resultados da pesquisa, em **Ação** e depois em **Exibir status do PIN**.

## Para exibir as informações de PIN do usuário usando cmdlets do Shell de Gerenciamento do Lync Server

Você pode exibir as informações de PIN do usuário usando o cmdlet Get-CsClientPinInfo. Esse cmdlet pode ser executado a partir do Shell de Gerenciamento do Lync Server 2013 ou de uma sessão remota do Windows PowerShell. Para obter detalhes sobre como usar o Windows PowerShell remoto para conectar ao Lync Server, consulte o artigo de blog do Lync Server Windows PowerShell, "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" em [http://go.microsoft.com/fwlink/p/?linkId=255876 (em inglês)](http://go.microsoft.com/fwlink/p/?linkid=255876).

## Para exibir as informações de PIN do usuário

  - Para exibir as informações de PIN de um usuário, digite um comando semelhante ao seguinte no Shell de Gerenciamento do Lync Server e pressione ENTER:
    
        Get-CsClientPinInfo -Identity "Ken Myer"
    
    Isso retornará informações semelhantes às seguintes:
    
        Identity          : sip:kenmyer@litwareinc.com
        IsPinSet          : False
        IsLockedOut       : False
        LastPinChangeTime : 9/25/2012 1:35:03 PM
        PinExpirationTime :

Para obter mais informações, consulte o tópico de ajuda do cmdlet [Get-CsConferenceDisclaimer](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsConferenceDisclaimer).

## Consulte Também

#### Tarefas

[Configurar PIN de conferência discada de um usuário no Lync Server 2013](lync-server-2013-set-a-user-s-dial-in-conferencing-pin.md)  
[Bloquear ou desbloquear um PIN de usuário](lync-server-2013-lock-or-unlock-a-user-pin.md)

