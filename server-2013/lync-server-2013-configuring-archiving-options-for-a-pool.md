---
title: Configurando opções de arquivamento para um pool
TOCTitle: Configurando opções de arquivamento para um pool
ms:assetid: b7cb0fd8-3d31-4858-a75c-c66a7742556e
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205200(v=OCS.15)
ms:contentKeyID: 49307887
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurando opções de arquivamento para um pool

 

_**Tópico modificado em:** 2012-10-10_

Você deve especificar as opções de Arquivamento que serão aplicadas a pools específicos criando e configurando opções em uma configuração de Arquivamento para cada um desses pools. Uma configuração de pool substitui a configuração global e de site, mas somente para o pool especificado na configuração de pool.

Para obter detalhes sobre como as configurações de Arquivamento funcionam, incluindo a hierarquia de configurações globais, de site e de pool, consulte [Como o arquivamento funciona no Lync Server 2013](lync-server-2013-how-archiving-works.md) na documentação de Planejamento, Implantação ou Operações.

> [!NOTE]  
> Você deve especificar todas as opções apropriadas nas configurações de Arquivamento antes de habilitá-lo. Para obter detalhes, consulte <a href="lync-server-2013-configuring-archiving-options.md">Configurando opções de arquivamento</a> na documentação de Implantação.

## Configurar opções de arquivamento no nível do pool

1.  Usando uma conta de usuário atribuída à função CsArchivingAdministrator ou CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e digite o URL do administrador para abrir o Painel de Controle do Lync Server 2013. Para obter detalhes sobre métodos diferentes que você pode usar para iniciar o Painel de Controle do Lync Server 2013, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação da esquerda, clique em **Monitoramento e Arquivamento**, e depois, clique em **Configuração de Arquivamento**.

4.  Na página **Configuração de arquivamento**, clique em **Nova** e em **Configuração de pool**.

5.  Em **Selecionar um serviço**, selecione o pool que será configurado para arquivamento.

6.  Em **Nova configuração de arquivamento**, na lista suspensa **Configuração de arquivamento**, selecione uma das seguintes opções de arquivamento:
    
      - **Desativar arquivamento**
    
      - **Arquivar sessões de IM**
    
      - **Arquivar sessões de IM e conferência da Web**

7.  Na página **Nova configuração de arquivamento**, faça o seguinte:
    
      - Para bloquear a atividade quando o arquivamento não estiver disponível, marque a caixa de seleção **Bloquear sessões de IM (mensagens instantâneas) ou webconferência se ocorrer falha no arquivamento**.
    
      - Para usar Microsoft Exchange Server e armazenar dados de arquivamento, clique na caixa de seleção de integração **Microsoft Exchange**.
    
      - Para ativar a limpeza de dados, marque a caixa de seleção **Ativar a limpeza de dados de arquivamento** e faça o seguinte:
        
          - Para especificar a limpeza após um número específico de dias, clique em **Limpar dados de arquivamento exportados e armazenados após um período máximo de (dias)** e especifique o número de dias.
        
          - Para limitar a limpeza nos dados de arquivamento que foram exportados, clique em **Limpar somente dados de arquivamento**.

8.  Clique em **Confirmar**.

