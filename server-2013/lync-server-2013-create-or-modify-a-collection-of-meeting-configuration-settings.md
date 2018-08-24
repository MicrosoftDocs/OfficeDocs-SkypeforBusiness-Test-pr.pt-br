---
title: Criar ou Modificar um Conjunto de Configurações de Reunião no Lync Server 2013
TOCTitle: Criar ou Modificar um Conjunto de Configurações de Reunião no Lync Server 2013
ms:assetid: ce6773c1-a0d5-4405-8e32-33a6f3a46a1a
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ721889(v=OCS.15)
ms:contentKeyID: 49886417
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Criar ou Modificar um Conjunto de Configurações de Reunião no Lync Server 2013

 

_**Tópico modificado em:** 2013-02-23_

É possível usar as configurações na página Configuração da Reunião para definir várias características da experiência de participação da reunião. Por padrão, as configurações globais definem a experiência de participação. Você também pode criar configurações de participação de reuniões a nível local e a nível de pool. Se você criar configurações a nível de pool, elas se aplicarão a todas as reuniões hospedadas pelo pool. Se você não criar configurações a nível de pool, as configurações a nível local serão aplicadas, caso existam. Se você não definir as configurações a nível local, as configurações globais serão aplicadas a todas as reuniões.

## Para criar novas configurações de participação de reunião

1.  Usando uma conta de usuário atribuída à função CsUserAdministrator ou CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerda, clique em **Conferência** e em **Configuração da reunião**.

4.  Na página **Configuração de reunião** , clique em **Novo** e siga um destes procedimentos:
    
      - Para criar uma política a nível local, clique em **Configuração local**. No campo de pesquisa **Selecionar um local**, digite todo ou parte do nome do local para o qual você deseja definir as configurações de participação de reunião. Na lista resultante de locais, clique no local desejado e em **OK**.
    
      - Para criar uma política a nível de pool, clique em **Configuração do pool**. No campo de pesquisa **Selecionar um serviço**, digite todo ou parte do nome do serviço do pool para o qual você deseja definir as configurações de participação de reunião. Na lista resultante de serviços, clique no pool desejado e em **OK**.

5.  Para direcionar os participantes que ligam por um PSTN através do lobby, desmarque a caixa de seleção **Os chamadores PSTN ignoram o lobby**. Por padrão, os participantes discando pelo PSTN vão diretamente para a reunião.

6.  Para configurar quem pode ser um apresentador na reunião, em **Designar como apresentador**, faça um dos seguintes:
    
      - Para não permitir que qualquer pessoa além do organizador seja o apresentador, clique em **Nenhum**.
    
      - Para permitir que apenas participantes membros da sua organização sejam apresentadores, clique em **Empresa**. Esta é a configuração padrão.
    
      - Para permitir qualquer participante ser o apresentador, clique em **Todos**.

7.  Para que o organizador selecione um tipo de conferência ao programar uma reunião, desmarque a caixa de seleção **Tipo de conferência atribuída por padrão**. Por padrão, o tipo de conferência é atribuído automaticamente.

8.  Para evitar que usuários anônimos (não autenticados) sejam aceitos automaticamente, desmarque a caixa de seleção **Aceitar usuários anônimos por padrão**. Por padrão, os usuários anônimos são aceitos automaticamente nas reuniões.

9.  Para personalizar o convite da reunião enviado para os participantes, faça o seguinte. Observe que o comprimento máximo das URLs e o texto do rodapé padrão é de 1KB. Exceto para a **URL de ajuda**, se você não especificar um valor para as personalizações, não serão incluídas na reunião. Se você não incluir uma URL de ajuda personalizada, a URL de ajuda padrão para Lync será exibida no convite.
    
      - Para personalizar o logotipo exibido no convite da reunião, em **URL do logotipo**, insira o local do logotipo.
        
        > [!NOTE]  
        > O logotipo deve ser uma imagem GIF ou JPG com um tamanho de 188 por 30 pixels.    
      - Para personalizar o texto de ajuda exibido no convite da reunião, na **URL de ajuda**, insira o local do texto de ajuda.
    
      - Para personalizar o texto legal exibido no convite da reunião, na **URL do texto legal**, insira o local do logotipo.
    
      - Para personalizar o texto do rodapé exibido no convite da reunião, em **Texto do rodapé personalizado**, insira o texto.

10. Clique em **Confirmar**.

## Para modificar uma coletânea existente de configurações de reunião

1.  Usando uma conta de usuário atribuída à função CsUserAdministrator ou CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerda, clique em **Conferência** e em **Configuração da reunião**.

4.  Na lista de configurações da reunião, clique na configuração que deseja alterar, em **Editar** e em **Exibir detalhes**.

5.  Em **Editar configuração de reunião**, modifique qualquer definição da configuração, exceto o nome da configuração, que não pode ser modificado.

6.  Clique em **Confirmar**.

## Criando novas definições de configuração da reunião usando os cmdlets do Windows PowerShell

As definições de configuração da reunião podem ser criadas (apenas no escopo local) utilizando o Windows PowerShell e o cmdlet New-CsMeetingConfiguration. Este cmdlet pode ser executado do Shell de Gerenciamento do Lync Server 2013 ou de uma sessão remota do Windows PowerShell. Para obter detalhes sobre como usar o Windows PowerShell remoto para conectar ao Lync Server, consulte o artigo de blog do Lync Server Windows PowerShell, "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" em [http://go.microsoft.com/fwlink/p/?linkId=255876 (em inglês)](http://go.microsoft.com/fwlink/p/?linkid=255876).

## Para criar novas configurações de reunião que usem os valores padrão

  - Este comando cria um novo conjunto de configurações de reunião para o site Redmond:
    
        New-CsMeetingConfiguration -Identity "site:Redmond"
    
    Como não há parâmetros (além do parâmetro obrigatório Identity) onde especificado no comando anterior, as novas definições de configuração de reunião usarão os valores padrões para todas as suas propriedades.

## Para alterar o valor de uma propriedade ao criar novas configurações de reunião

  - Para criar configurações que usam valores de propriedades diferentes, basta incluir o parâmetro e o valor de parâmetro adequados. Por exemplo, para criar um conjunto de reuniões de configuração da reunião que, por padrão, permite todos em uma reunião serem apresentadores a usarem um comando como este:
    
        New-CsMeetingConfiguration -Identity "site:Redmond" -DesignateAsPresenter "Everyone"

## Para alterar valores de várias propriedades ao criar novas configurações de reunião

  - Os valores de várias propriedades podem ser modificados, incluindo vários parâmetros. Por exemplo, este comando permite que todos em uma reunião serem apresentadores e também força os usuários PSTN a aguardar enquanto são formalmente admitidos na reunião:
    
        New-CsMeetingConfiguration -Identity "site:Redmond" -DesignateAsPresenter "Everyone" -PSTNUCallersBypassLobby $True

Para obter mais informações, consulte o tópico de ajuda do cmdlet [New-CsMeetingConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsMeetingConfiguration).

