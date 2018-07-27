---
title: 'Lync Server 2013: Configurar PIN de conferência discada de um usuário'
TOCTitle: Configurar PIN de conferência discada de um usuário
ms:assetid: 4252b5a5-4267-4513-b18e-0253a8d66f72
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg520985(v=OCS.15)
ms:contentKeyID: 49306527
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurar PIN de conferência discada de um usuário no Lync Server 2013

 

_**Tópico modificado em:** 2014-06-10_

Para ingressar em uma conferência de discagem como usuário autenticado, um usuário do Lync Server 2013 com credenciais do AD DS (Serviços de Domínio Active Directory) requer um PIN (número de identificação pessoal). Se o usuário se esquecer do PIN de conferência de discagem ou não o tiver definido usando o Lync Server, você poderá configurar o PIN do usuário por meio do Painel de Controle do Lync Server. Você pode gerar automaticamente o PIN ou criá-lo manualmente.

> [!NOTE]  
> Características específicas do PIN, como seu tamanho mínimo, podem ser configuradas como uma política. Além da política global, é possível configurar uma política de PIN para sites ou usuários individuais. Para obter detalhes sobre a configuração de uma política de PIN, consulte <a href="lync-server-2013-configure-dial-in-conferencing-personal-identification-number-pin-rules.md">Configurar regras de PIN da conferência discada no Lync Server 2013</a>.

## Para definir o PIN de um usuário

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
    
    4.  Dependendo da propriedade de usuário selecionada, insira os critérios que você deseja usar para filtrar os resultados da pesquisa digitando-os ou clicando na seta da lista suspensa.
        

        > [!TIP]
        > Para adicionar cláusulas de pesquisa adicionais à sua consulta, clique em <STRONG>Adicionar filtro</STRONG>.

    
    5.  Clique em **Localizar**.
    
    > [!NOTE]  
    > Se o PIN estiver bloqueado, você deverá desbloqueá-lo para poder defini-lo. Para desbloquear o PIN, clique no usuário, clique em <strong>Ação</strong> e depois em <strong>Desbloquear PIN</strong>.

6.  Clique em um usuário nos resultados da pesquisa, clique em **Ação** e em **Definir PIN**.

7.  Na caixa de diálogo **Definir PIN**, siga um destes procedimentos:
    
      - Para permitir que o Lync Server 2013 gere o PIN do usuário, selecione **Gerar automaticamente um PIN válido** (padrão).
    
      - Para criar seu próprio PIN, clique em **Inserir manualmente um PIN específico**, clique na caixa de texto e digite um PIN na caixa de texto que atenda aos requisitos de PIN especificados nas configurações de política de PIN.

8.  Clique em **OK**.

9.  Em **Definir PIN**, siga um destes procedimentos:
    
      - Marque a caixa de seleção **Mostrar PIN** para ver o PIN e copie o PIN e comunique-o ao usuário usando o método preferencial da sua organização.
    
      - Clique em **Abrir meu aplicativo de email para enviar o novo PIN para o usuário** para enviar o novo PIN por email. Se o Microsoft Office Outlook for seu cliente de email, o PIN será copiado automaticamente para uma nova mensagem de email. Se você usar um cliente de email diferente, marque a caixa de seleção **Mostrar PIN** para ver o PIN e copiá-lo em sua mensagem de email.

10. Clique em **Fechar**.

## Atribuindo um PIN do usuário utilizando os cmdlets Windows PowerShell

Você pode atribuir números PIN utilizando o cmdlet Set-CsClientPin. Execute este cmdlet a partir do Shell de Gerenciamento do Lync Server 2013 ou de uma sessão remota do Windows PowerShell. Para obter detalhes sobre como usar o Windows PowerShell remoto para conectar ao Lync Server, consulte o artigo de blog do Lync Server Windows PowerShell, "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" em [http://go.microsoft.com/fwlink/p/?linkId=255876 (em inglês)](http://go.microsoft.com/fwlink/p/?linkid=255876).

## Para atribuir automaticamente um número PIN a um usuário

  - O comando a seguir atribui um número PIN ao usuário Ken Myer. Por o parâmetro de Pin não estar incluído, Lync Server irá gerar automaticamente e atribuir um número de PIN.
    
        Set-CsClientPin -Identity "Ken Myer" 

## Para atribuir um número PIN específico a um usuário

  - Esse comando utiliza o parâmetro PIN para atribuir o número de PIN 121989 ao usuário Ken Myer.
    
        Set-CsClientPin -Identity "Ken Myer" -Pin 121989

Para obter mais informações, consulte o tópico de ajuda referente ao cmdlet [Set-CsClientPin](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsClientPin).

## Consulte Também

#### Conceitos

[Número de Acesso Discado](https://technet.microsoft.com/pt-br/library/gg133674\(v=ocs.15\))  

#### Outros Recursos

[Configurar regras de PIN da conferência discada no Lync Server 2013](lync-server-2013-configure-dial-in-conferencing-personal-identification-number-pin-rules.md)

