---
title: Criar uma Política de Arquivamento para Habilitar ou Desabilitar o Arquivamento de Comunicações Internos ou Externos para Sites ou Usuários Específicos
TOCTitle: Criar uma Política de Arquivamento para Habilitar ou Desabilitar o Arquivamento de Comunicações Internos ou Externos para Sites ou Usuários Específicos
ms:assetid: 5864793a-ba72-470c-bb5b-9fb41e968896
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398385(v=OCS.15)
ms:contentKeyID: 49306780
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Criar uma Política de Arquivamento para Habilitar ou Desabilitar o Arquivamento de Comunicações Internos ou Externos para Sites ou Usuários Específicos

 

_**Tópico modificado em:** 2013-02-23_

No Lync Server 2013, você pode utilizar políticas para habilitar e desabilitar o arquivamento para as comunicações internas e externas para usuários hospedados no Lync Server 2013. Isso inclui as seguintes políticas de arquivamento:

  - Uma política global que é criada, por padrão, quando você implanta o Lync Server 2013.

  - Políticas em nível de site e do usuário opcionais que você pode criar e utilizar para especificar como o arquivamento será implementado para sites e usuários específicos.

Inicialmente, você configurou as políticas de arquivamento quando implantou o arquivamento, mas é possível alterar, adicionar e excluir política depois da implantação. No Painel de Controle do Lync Server 2013, você pode utilizar a página **Política de arquivamento** do grupo **Arquivamento e Monitoramento** para gerenciar as políticas em nível global, de site e do usuário. Se você integrar o armazenamento do seu Lync Server ao armazenamento do Exchange 2013, as políticas do usuário do Exchange terão precedência sobre as políticas de arquivamento do Lync Server 2013.

Para obter detalhes sobre como as políticas são implementadas, incluindo a hierarquia das políticas, consulte [Como o arquivamento funciona no Lync Server 2013](lync-server-2013-how-archiving-works.md) na Documentação de planejamento, Documentação de implantação ou Documentação de operações.

> [!NOTE]  
> Para controlar a implementação do arquivamento, você deve especificar opções nas configurações de arquivamento, como se deve arquivar mensagens instantâneas ou conferências, o uso do modo crítico e as opções de limpeza. Por padrão, nenhuma opção está habilitada na configuração de arquivamento global ou em qualquer configuração de arquivamento no site ou no pool. Você deve especificar todas as opções apropriadas nas configurações de arquivamento antes de habilitar o arquivamento para as comunicações internas ou externas nas políticas de arquivamento. Para obter detalhes, consulte <a href="lync-server-2013-managing-archiving-configuration-options-for-your-organization-sites-and-pools.md">Gerenciando opções de configuração do arquivamento no Lync Server 2013 para sua empresa, sites e pools</a> na Documentação de operações.<br />Se você habilitar a integração do Microsoft Exchange para a sua implantação, as políticas do Exchange controlarão se o arquivamento estará habilitado para os usuários que estiverem hospedados no Exchange 2013 e possuírem suas caixas de correio colocadas em bloqueio In-loco. Para obter detalhes, consulte <a href="lync-server-2013-setting-up-policies-for-archiving-when-using-exchange-server-integration.md">Configurando Políticas para Arquivamento quando Usando Integração do Exchange Server</a> na Documentação de implantação.

## Para criar uma política de arquivamento para um site ou usuário

1.  Usando uma conta de usuário atribuída à função CsArchivingAdministrator ou CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação da esquerda, clique em **Monitoramento e Arquivamento**, e depois, clique em **Política de Arquivamento**.

4.  Clique em **Nova** e execute um dos seguintes procedimentos:
    
      - Para criar uma política de arquivamento em nível de site, clique em **Política de site** e em **Selecionar um site**, clique no site ao qual a política deve ser aplicada.
    
      - Para criar uma política de arquivamento em nível do usuário, clique em **Política de usuário**.

5.  Em **Nova Política de Arquivamento**, faça o seguinte:
    
      - Em **Nome**, especifique um nome para a nova política (por exemplo, externalContoso).
    
      - Em **Descrição**, forneça os detalhes sobre a política (por exemplo, a política de arquivamento de usuário externo da Contoso).
    
      - Para controlar o arquivamento das comunicações com usuários internos, marque ou desmarque a caixa de seleção **Arquivar comunicações internas**.
    
      - Para controlar o arquivamento das comunicações com usuários externos, marque ou desmarque a caixa de seleção **Arquivar comunicações externas**.

6.  Clique em **Confirmar**.
    
    > [!IMPORTANT]  
    > As configurações de uma política de usuário somente se aplicam aos usuários e grupos de usuários específicos aos quais você aplicar a política. Para obter detalhes, consulte <a href="lync-server-2013-applying-an-archiving-policy-to-users.md">Aplicar uma política de arquivamento aos usuários</a>

## Criando uma nova política de arquivamento usando cmdlets Shell de Gerenciamento do Lync Server

As políticas de arquivamento também podem ser criadas usando o Windows PowerShell e o cmdlet **Remove-CsArchivingPolicy**. Esse cmdlet pode ser executado a partir do Shell de Gerenciamento do Lync Server 2013 ou de uma sessão remota do Windows PowerShell. Para obter detalhes sobre como usar o Windows PowerShell remoto para conectar ao Lync Server, consulte o artigo de blog do Lync Server Windows PowerShell, "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" em [http://go.microsoft.com/fwlink/p/?linkId=255876 (em inglês)](http://go.microsoft.com/fwlink/p/?linkid=255876).

## Criando uma nova política de arquivamento no escopo do site

  - Este comando cria uma nova política de arquivamento para o site de Redmond:
    
        New-CsArchivingPolicy -Identity "site:Redmond"

## Criando uma nova política de arquivamento no escopo por usuário

  - Para criar uma nova política de arquivamento no escopo por usuário, basta especificar um Identity exclusivo ao criar a política:
    
        New-CsArchivingPolicy -Identity "RedmondArchivingPolicy"

## Criando uma nova política de arquivamento que habilite o arquivo em sessões de comunicação interna

  - Como nenhum parâmetros foi especificado (além do parâmetro obrigatório Identity) nos comandos anteriores, as novas políticas utilizarão os valores padrão para todas as suas propriedades. Para criar políticas que utilizam valores de propriedades diferentes, basta incluir o parâmetro e o valor de parâmetro apropriado. Por exemplo, para criar uma política de arquivamento que permita o arquivamento de mensagens instantâneas internas utilize um comando como este:
    
        New-CsArchivingPolicy -Identity "site:Redmond" -ArchiveInternal $True

## Criando uma nova política de arquivamento que habilite o arquivo em sessões de comunicação interna e externa

  - Vários valores de propriedade podem ser modificados, incluindo vários parâmetros. Por exemplo, esse comando configura a nova política de arquivamento em sessões de mensagens instantâneas internas e externas:
    
        New-CsArchivingPolicy -Identity "site:Redmond" -ArchiveInternal $True -ArchiveExternal $True

Para obter mais informações, consulte o tópico de ajuda para o cmdlet [New-CsArchivingPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsArchivingPolicy).

## Consulte Também

#### Outros Recursos

[Gerenciando o arquivamento de comunicações internas e externas no Lync Server 2013](lync-server-2013-managing-the-archiving-of-internal-and-external-communications.md)

