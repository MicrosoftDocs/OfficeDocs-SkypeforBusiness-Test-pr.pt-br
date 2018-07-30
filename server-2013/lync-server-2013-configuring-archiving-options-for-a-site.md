---
title: Configurando opções de arquivamento para um local
TOCTitle: Configurando opções de arquivamento para um local
ms:assetid: 59b48fd9-d5fc-40b4-abae-e9cf89ee5573
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204930(v=OCS.15)
ms:contentKeyID: 49306808
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurando opções de arquivamento para um local

 

_**Tópico modificado em:** 2012-10-09_

Você pode especificar opções de arquivamento para serem aplicadas a sites específicos criando e definindo opções em uma configuração de arquivamento para cada um desses sites. Uma configuração de site substitui a configuração global, mas só se aplica ao site específico definido na configuração de site. As configurações de pool substituem as configurações de site

Para obter detalhes sobre como as configurações de arquivamento funcionam, incluindo a hierarquia das configurações globais, de site e de pool, consulte [Como o arquivamento funciona no Lync Server 2013](lync-server-2013-how-archiving-works.md) nas documentações de planejamento, implantação e operações.

> [!NOTE]  
> Você deve especificar todas as opções adequadas nas configurações de arquivamento antes de habilitar o arquivamento.

> [!IMPORTANT]  
> Para habilitar o arquivamento, você deve especificar políticas de arquivamento para controlar o arquivamento de comunicações externas e internas ao nível global e, caso seja apropriado, nos níveis de site e usuário. Caso configure políticas de nível de usuário, você também deve atribuir as políticas de usuários para usuários específicos. Para maiores detalhes sobre criar e configurar políticas de arquivamento, consulte <a href="lync-server-2013-managing-the-archiving-of-internal-and-external-communications.md">Gerenciando o arquivamento de comunicações internas e externas no Lync Server 2013</a> na documentação de Operações.

## Para configurar as opções de arquivamento no nível do site

1.  A partir de uma conta de usuário atribuída à função CsArchivingAdministrator ou CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e digite a URL do administrador para abrir o Painel de Controle do Lync Server 2013. Para obter detalhes sobre os diferentes métodos que podem ser usados para iniciar o Painel de Controle do Lync Server 2013, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação da esquerda, clique em **Monitoramento e Arquivamento**, e depois, clique em **Configuração de Arquivamento**.

4.  Na página **Configuração do Arquivamento**, clique em **Novo** e depois em **Configuração do site**.

5.  Em **Selecionar um Site**, selecione o site a ser configurado para arquivamento.

6.  Em **Nova Configuração de Arquivamento**, na caixa da lista suspensa **Configuração do Arquivamento**, execute um dos seguintes procedimentos:
    
      - Para habilitar o arquivamento apenas para sessões de mensagens instantâneas (IM), clique em **Arquivar sessões de IM**.
    
      - Para habilitar o arquivamento para sessões de IM e conferências, clique em **Arquivar sessões de IM e webconferências**.
    
      - Para desabilitar o arquivamento para a política, clique em **Desabilitar arquivamento**.

7.  Além disso, em **Nova Configuração de Arquivamento**, faça o seguinte:
    
      - Para bloquear a atividade quando o arquivamento não estiver disponível, marque a caixa de seleção **Bloquear sessões de mensagens instantâneas (IM) ou Webconferência se ocorrer falha no arquivamento**.
    
      - Para usar o Microsoft Exchange Server para arquivar dados, clique na caixa de seleção **Integração do Microsoft Exchange**.
    
      - Para habilitar a limpeza de dados, marque a caixa de seleção **Habilitar limpeza de dados de arquivamento** e execute um dos seguintes procedimentos:
        
          - Para definir a limpeza após um número específico de dias, clique em **Limpar dados de arquivamento exportados e armazenados após um período máximo de (dias)** e especifique o número de dias.
        
          - Para limitar a limpeza a dados de arquivamento que foram exportados, clique em **Limpar somente dados de arquivamento exportados**.

8.  Clique em **Confirmar**.

