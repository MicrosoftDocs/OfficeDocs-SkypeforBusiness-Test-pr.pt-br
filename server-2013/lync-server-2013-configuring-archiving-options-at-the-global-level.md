---
title: Configurando opções de arquivamento em nível global
TOCTitle: Configurando opções de arquivamento em nível global
ms:assetid: bfe415f7-2abf-41ee-a1cb-cf48b2d59c0c
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205233(v=OCS.15)
ms:contentKeyID: 49307977
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurando opções de arquivamento em nível global

 

_**Tópico modificado em:** 2012-10-10_

Ao adicionar Arquivamento à sua topologia e publicá-la, o Lync Server cria uma configuração global de Arquivamento. Por padrão, nenhuma opção de Arquivamento está ativada na configuração global. Os controles de configuração global que habilitam configurações para a implantação inteira, a não ser que você defina configurações de site ou pool que substituem a configuração global.

Para obter detalhes sobre como as configurações de Arquivamento funcionam, incluindo a hierarquia de configurações globais, de site e pool, consulte [Como o arquivamento funciona no Lync Server 2013](lync-server-2013-how-archiving-works.md) na documentação de Planejamento, Implantação ou Operações.

> [!NOTE]  
> Você deve especificar todas as opções apropriadas nas configurações de Arquivamento antes de habilitá-lo.

## Configurar opções de arquivamento a nível global

1.  Usando uma conta de usuário atribuída à função CsArchivingAdministrator ou CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e digite o URL do administrador para abrir o Painel de Controle do Lync Server 2013. Para obter detalhes sobre métodos diferentes que podem ser usados para iniciar o Painel de Controle do Lync Server 2013, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação da esquerda, clique em **Monitoramento e Arquivamento**, e depois, clique em **Configuração de Arquivamento**.

4.  Na página **Configuração de arquivamento**, clique em **Global**, **Editar** e **Mostrar detalhes**.

5.  Em **Editar configuração de arquivamento - global**, na lista suspensa **Configuração de arquivamento**, selecione uma das seguintes opções de arquivamento:
    
      - **Desativar arquivamento**
    
      - **Arquivar sessões de IM**
    
      - **Arquivar sessões de IM e conferência da Web**

6.  Na página **Editar configuração de arquivamento – global**, faça o seguinte:
    
      - Para bloquear a atividade quando o arquivamento não estiver disponível, marque a caixa de seleção **Bloquear sessões de IM (mensagens instantâneas) ou webconferência se ocorrer falha no arquivamento**.
    
      - Para usar Microsoft Exchange Server e armazenar dados de arquivamento, clique na caixa de seleção de integração **Microsoft Exchange**.
    
      - Para ativar a limpeza de dados, marque a caixa de seleção **Ativar a limpeza de dados de arquivamento** e faça o seguinte:
        
          - Para especificar a limpeza após um número específico de dias, clique em **Limpar dados de arquivamento exportados e armazenados após um período máximo de (dias)** e especifique o número de dias.
        
          - Para limitar a limpeza nos dados de arquivamento que foram exportados, clique em **Limpar somente dados de arquivamento**.

7.  Clique em **Confirmar**.

