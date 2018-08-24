---
title: Habilitar ou Desabilitar o Arquivamento de Sessões de Conferência ou IM
TOCTitle: Habilitar ou Desabilitar o Arquivamento de Sessões de Conferência ou IM
ms:assetid: aa4b5983-dbe1-4d64-8a18-fe2c33994e94
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg182567(v=OCS.15)
ms:contentKeyID: 49307745
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Habilitar ou Desabilitar o Arquivamento de Sessões de Conferência ou IM

 

_**Tópico modificado em:** 2012-10-10_

No Painel de Controle do Lync Server 2013, você usa configurações de arquivamento para ativar e desativar o arquivamento de IM, sessões de conferência, ou ambas. Isso inclui as seguintes configurações de arquivamento:

  - Uma configuração global que é criada como padrão ao implantar o Lync Server 2013.

  - Configurações opcionais no nível do site e do pool que você pode criar e usar para especificar como o arquivamento é implementado para sites ou pools específicos.

Inicialmente, você define as configurações de Arquivamento ao implantar o Arquivamento, mas você pode alterar, adicionar ou excluir configurações após a implantação. Para obter detalhes sobre como as configurações de Arquivamento são implementadas, incluindo quais opções você pode especificar e a hierarquia das configurações de Arquivamento, consulte [Como o arquivamento funciona no Lync Server 2013](lync-server-2013-how-archiving-works.md) na documentação de Planejamento, documentação de Implantação ou documentação de Operações.

> [!NOTE]  
> Para usar o arquivamento, é necessário configurar as políticas de arquivamento para especificar se o arquivamento será ativado para comunicações internas, para comunicações externas ou ambas, para os usuários hospedados no Lync Server 2013. Como padrão, o arquivamento não é ativado para comunicações internas ou externas. Antes de ativar o arquivamento em qualquer política, você deverá especificar as configurações de arquivamento da sua implantação e, opcionalmente, especificar sites e pools, conforme descritos nesta seção. Para detalhes sobre a ativação de arquivamento, consulte <a href="lync-server-2013-configuring-and-assigning-archiving-policies.md">Configurando e atribuindo políticas de arquivamento</a>na documentação de Implantação.<br />Se você decidir usar a integração do Microsoft Exchange, após implantar o Arquivamento, para armazenar dados e arquivos de arquivamento nos servidores do Exchange 2013 e todos seus usuários estiverem hospedados em seus servidores do Exchange 2013, você deverá remover a configuração de banco de dados do SQL Server da sua topologia. Será necessário usar a Construtor de Topologias para isso. Para obter detalhes, consulte <a href="lync-server-2013-changing-archiving-database-options.md">Modificando opções do banco de dados de arquivamento no Lync Server 2013</a> na documentação de Operações.

## Para ativar ou desativar o arquivamento de IM ou sessões de conferência

1.  Usando uma conta de usuário atribuída à função CsArchivingAdministrator ou CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação da esquerda, clique em **Monitoramento e Arquivamento**, e depois, clique em **Configuração de Arquivamento**.

4.  Selecione a configuração global, de site ou de pool apropriada na lista de configurações de arquivo, clique em **Editar**, **Exibir detalhes** e execute o seguinte procedimento:
    
      - Para habilitar o arquivamento apenas para sessões de IM (mensagem instantânea), clique em **Arquivar sessões de IM**.
    
      - Para habilitar o arquivamento para as sessões de IM e conferências, clique em **Arquivar sessões de IM e conferências**.
    
      - Para desabilitar o arquivamento para a política, clique em **Desabilitar arquivamento**.

5.  Clique em **Confirmar**.

## Consulte Também

#### Outros Recursos

[Gerenciando opções de configuração do arquivamento no Lync Server 2013 para sua empresa, sites e pools](lync-server-2013-managing-archiving-configuration-options-for-your-organization-sites-and-pools.md)  
[Configurando e atribuindo políticas de arquivamento](lync-server-2013-configuring-and-assigning-archiving-policies.md)

