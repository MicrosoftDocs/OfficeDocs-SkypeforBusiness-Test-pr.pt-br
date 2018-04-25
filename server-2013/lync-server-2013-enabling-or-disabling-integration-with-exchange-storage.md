---
title: Habilitando uo Desabilitando Integração com Exchange Storage
TOCTitle: Habilitando uo Desabilitando Integração com Exchange Storage
ms:assetid: c08b9ba5-04f6-452a-b44c-c130f1564a34
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205228(v=OCS.15)
ms:contentKeyID: 49308001
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Habilitando uo Desabilitando Integração com Exchange Storage

 

_**Tópico modificado em:** 2012-10-09_

No Painel de Controle do Lync Server 2013, você usa as configurações de Arquivamento para habilitar e desabilitar a integração com o armazenamento do Exchange. Isto inclui as seguintes configurações de Arquivamento:

  - Uma configuração global criada por padrão ao implantar o Lync Server 2013.

  - Configurações a nível do pool e a nível local opcionais que você pode criar e usar para especificar como o arquivamento é implementado para locais e pools específicos.

Para obter detalhes sobre como as configurações de Arquivamento são implementadas, incluindo quais opções é possível especificar e a hierarquia das configurações de Arquivamento, consulte [Como o arquivamento funciona no Lync Server 2013](lync-server-2013-how-archiving-works.md) na documentação de Planejamento, de Implantação ou Operações.

## Para habilitar ou desabilitar a integração com o armazenamento do Microsoft Exchange

1.  Usando uma conta de usuário atribuída à função CsArchivingAdministrator ou CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação da esquerda, clique em **Monitoramento e Arquivamento**, e depois, clique em **Configuração de Arquivamento**.

4.  Clique no nome da configuração do pool, local ou global adequada na lista de configurações de arquivamento, clique em **Editar**, em **Exibir detalhes** e faça o seguinte:
    
      - Para habilitar a integração com o armazenamento do Exchange 2013, marque a caixa de seleção **Integração do Microsoft Exchange**.
    
      - Para desabilitar a integração com o armazenamento do Exchange 2013, desmarque a caixa de seleção **Integração do Microsoft Exchange**.

5.  Clique em **Confirmar**.

## Consulte Também

#### Conceitos

[Como o arquivamento funciona no Lync Server 2013](lync-server-2013-how-archiving-works.md)  

#### Outros Recursos

[Gerenciando opções de configuração do arquivamento no Lync Server 2013 para sua empresa, sites e pools](lync-server-2013-managing-archiving-configuration-options-for-your-organization-sites-and-pools.md)

