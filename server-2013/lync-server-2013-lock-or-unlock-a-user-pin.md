---
title: Bloquear ou desbloquear um PIN de usuário
TOCTitle: Bloquear ou desbloquear um PIN de usuário
ms:assetid: 3d293a8a-e182-4547-8b06-2603c3c77329
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ688028(v=OCS.15)
ms:contentKeyID: 49886185
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Bloquear ou desbloquear um PIN de usuário

 

_**Tópico modificado em:** 2013-02-23_

Você pode bloquear ou desbloquear o PIN de um usuário a partir da seção **Usuários** de Painel de Controle do Lync Server 2013.

## Para bloquear o PIN de um usuário no Painel de Controle do Lync Server

1.  Usando uma conta de usuário atribuída à função CsUserAdministrator ou CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação à esquerda, clique em **Usuários**.

4.  Utilize um dos seguintes métodos para localizar um usuário:
    
      - Na caixa **Buscar usuários**, digite toda ou a primeira parte do nome de exibição, nome, sobrenome, nome da conta do Gerenciador de Contas de Segurança (SAM), endereço SIP ou linha do Uniform Resource Identifier (URI) da conta de usuário, e então clique em **Localizar**.
    
      - Se você tiver uma consulta salva, clique no ícone **Abrir consulta**, utilize a caixa de diálogo **Abrir** para obter a consulta (um arquivo .usf) e, então, clique em **Localizar**.

5.  (Opcional) Especifique critérios de busca adicionais para limitar os resultados:
    
    1.  Clique em **Adicionar filtro**.
    
    2.  Insira a propriedade de usuário digitando ou clicando na seta na lista suspensa para selecionar a propriedade.
    
    3.  Na lista suspensa **Igual a**, clique no operador (por exemplo, **Igual a** ou **Diferente de**).
    
    4.  Dependendo da propriedade de usuário selecionada, insira o critério que deseja utilizar para filtrar os resultados da busca digitando ou clicando na seta na lista suspensa.
        

        > [!TIP]
        > Para adicionar cláusulas de busca à sua consulta, clique em <STRONG>Adicionar filtro</STRONG>.

    
    5.  Clique em **Localizar**.
    
    6.  Clique no usuário, em **Ação** e, em seguida, em **Bloquear PIN**.

## Para desbloquear o PIN de um usuário no Painel de Controle do Lync Server

1.  Usando uma conta de usuário atribuída à função CsUserAdministrator ou CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação à esquerda, clique em **Usuários**.

4.  Utilize um dos métodos a seguir para localizar um usuário:
    
      - Na caixa **Buscar usuários**, digite toda ou a primeira parte do nome de exibição, nome, sobrenome, nome da conta do Gerenciador de Contas de Segurança (SAM), endereço SIP ou linha do Uniform Resource Identifier (URI) da conta de usuário, e então clique em **Localizar**.
    
      - Se você tiver uma consulta salva, clique no ícone **Abrir consulta**, utilize a caixa de diálogo **Abrir** para obter a consulta (um arquivo .usf) e, então, clique em **Localizar**.

5.  (Opcional) Especifique critérios de busca adicionais para limitar os resultados:
    
    1.  Clique em **Adicionar filtro**.
    
    2.  Insira a propriedade de usuário digitando ou clicando na seta na lista suspensa para selecionar a propriedade.
    
    3.  Na lista suspensa **Igual a**, clique no operador (por exemplo, **Igual a** ou **Diferente de**).
    
    4.  Dependendo da propriedade de usuário selecionada, insira o critério que deseja utilizar para filtrar os resultados da busca digitando ou clicando na seta na lista suspensa.
        

        > [!TIP]
        > Para adicionar cláusulas de pesquisa à sua consulta, clique em <STRONG>Adicionar filtro</STRONG>.

    
    5.  Clique em **Localizar**.
    
    6.  Clique no usuário, clique em **Ação** e, então, clique em **Desbloquear PIN**.

## Para bloquear e desbloquear PINs utilizando os cmdlets Shell de Gerenciamento do Lync Server

Você também pode bloquear e desbloquear PINs utilizando o Windows PowerShell e os cmdlets Lock-CsClientPin e Unlock-CsClientPin. Você pode executar tais cmdlets do Shell de Gerenciamento do Lync Server 2013 ou de uma sessão remota do Windows PowerShell. Para obter detalhes sobre como usar o Windows PowerShell remoto para conectar ao Lync Server, consulte o artigo de blog do Lync Server Windows PowerShell, "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" em [http://go.microsoft.com/fwlink/p/?linkId=255876 (em inglês)](http://go.microsoft.com/fwlink/p/?linkid=255876).

## Para bloquear um PIN de usuário

  - Para bloquear o PIN de um usuário, utilize o cmdlet Lock-CsClientPin. Por exemplo:
    
        Lock-CsClientPin -Identity "Ken Myer"

## Para desbloquear um PIN de usuário

  - Para desbloquear o PIN de um usuário, utilize o cmdlet Unlock-CsClientPin. Por exemplo:
    
        Unlock-CsClientPin -Identity "Ken Myer"

Para mais informações, consulte o tópico de ajuda para os cmdlets [Lock-CsClientPin](https://docs.microsoft.com/en-us/powershell/module/skype/Lock-CsClientPin) e [Unlock-CsClientPin](https://docs.microsoft.com/en-us/powershell/module/skype/Unlock-CsClientPin).

