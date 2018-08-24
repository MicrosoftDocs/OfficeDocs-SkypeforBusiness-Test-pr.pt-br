---
title: Implantando o monitoramento no Lync Server 2013
TOCTitle: Implantando o monitoramento no Lync Server 2013
ms:assetid: 117f4a3e-0670-4388-a553-b9854921145f
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398199(v=OCS.15)
ms:contentKeyID: 49305926
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Implantando o monitoramento no Lync Server 2013

 

_**Tópico modificado em:** 2013-12-17_

Grandes alterações foram feitas na infraestrutura de monitoramento do Microsoft Lync Server 2013, começando com o fato de que a função Servidor de Monitoramento foi substituída. Em vez de separar funções Servidor de Monitoramento (o que normalmente exigia que as organizações definissem computadores dedicados para agir como servidores de Monitoramento), os serviços de monitoramento são agora colocados em cada servidor de Front End. Juntamente com outras coisas, essa alteração ajuda a:

  - Diminuir o numero de funções de servidor necessárias ao implementar o Lync Server 2013. Neste caso, reduzir a função de servidor Servidor de Monitoramento também ajuda a reduzir custos, eliminando a necessidade de manter servidores dedicados para monitoramento.

  - Reduzir a complexidade da instalação e administração do Lync Server. Colocando automaticamente os serviços de monitoramento em cada servidor de Front End, não é mais necessário instalar, configurar e gerenciar a função Servidor de Monitoramento.

> [!NOTE]  
> O Servidor de Arquivamento também foi substituído no Lync Server 2013. Assim como os serviços de monitoramento, os serviços de arquivamento do Lync Server 2013 agora são colocados em cada servidor de Front End. Isso é importante observar simplesmente porque o monitoramento e o arquivamento frequentemente compartilham a mesma instância de banco de dados do SQL Server.

Como você pode imaginar, essas alterações provocam um impacto significativo sobre como os serviços de monitoramento são instalados e gerenciados. Por exemplo, como a função Servidor de Monitoramento não existe mais, o nó Servidor de Monitoramento foi removido do Construtor de Topologias do Lync Server; por sua vez, isso significa que o Assistente do Novo Servidor de Monitoramento do Construtor de Topologias não é mais usado para adicionar um novo Servidor de Monitoramento à sua topologia (o assistente não existe mais). Em vez disso, você implementará serviços de monitoramento dentro da sua topologia concluindo duas etapas a seguir:

1.  Habilitando o monitoramento ao mesmo tempo em que define um novo pool do Lync Server (no Lync Server 2013, o monitoramento é habilitado ou desabilitado pool por pool). Observe que você pode habilitar o monitoramento para um pool sem coletar dados de monitoramento, um processo explicado na seção Como Configurar o Registro de Detalhes de Chamadas e Configurações de Qualidade da Experiência, neste documentação.

2.  Associando um repositório de monitoramento (ou seja, um banco de dados de monitoramento) ao novo pool. Observe que um único repositório pode ser associado a vários pools. Dependendo do número de usuários hospedados em seus pools de registradores, isso significa que não é necessário configurar um banco de dados de monitoramento separado para cada um dos seus pools. Em vez disso, um único repositório de monitoramento pode ser usado por vários pools.

Embora normalmente seja mais fácil habilitar o monitoramento ao mesmo tempo em que o novo pool é criado, também é possível criar um novo pool com o monitoramento desabilitado. Se o fizer, você pode usar o Construtor de Topologias mais tarde para habilitar o serviço: o Construtor de Topologias fornece uma maneira de habilitar ou desabilitar o monitoramento para um pool ou de associar um pool a um repositório de monitoramento diferente. Tenha em mente que embora não exista mais uma função Servidor de Monitoramento, ainda será necessário criar um ou mais repositórios de monitoramento: bancos de dados de backend usados para armazenar os dados reunidos pelo serviço de monitoramento. Esses bancos de dados de backend podem ser criados usando o Microsoft SQL Server 2008 R2 ou o Microsoft SQL Server 2012.

> [!NOTE]  
> Se o monitoramento foi habilitado para um pool, você pode desabilitar o processo de coletar dados de monitoramento sem a necessidade de alterar sua topologia: o Shell de Gerenciamento do Lync Server fornece uma maneira de desabilitar (e reabilitar mais tarde) o registro de detalhes de chamadas (CDR) ou a coleta de dados de Qualidade de Experiência (QoE). Para mais informações, consulte a seção Como Configurar o Registro de Detalhes de Chamadas e Configurações de Qualidade de Experiência deste documento.

Outro aprimoramento importante no monitoramento do Lync Server 2013 é o fato de que os Relatórios de Monitoramento do Lync Server agora suportam IPv6: relatórios que usam o campo Endereço IP exibirão endereços IPv4 ou IPv6 dependendo: 1) da consulta SQL que estiver sendo usada e 2) se o endereço IPv6 está sendo armazenado ou não no banco de dados de monitoramento.

> [!NOTE]  
> Verifique se o Tipo de inicialização do serviço SQL Server Agent é Automático e se o serviço SQL Server Agent está sendo executado para a Instância SQL que está mantendo os bancos de dados de Monitoramento para que os Trabalhos de manutenção do SQL de monitoramento padrão possam ser executados com base em seu agendamento sob o controle do Serviço SQL Server Agent.

Esta documentação o guiará pelo processo de instalação e configuração do monitoramento e de Relatórios de Monitoramento para o Lync Server 2013. A documentação fornece instruções passo a passo que o ajudarão a:

  - Habilitar o monitoramento na sua topologia e associar um repositório de monitoramento a um pool de Front End.

  - Instalar o SQL Server Reporting Services e os Relatórios de Monitoramento do Lync Server. Relatórios de Monitoramento são relatórios pré-configurados que fornecem visões diferentes das informações armazenadas em um banco de dados de monitoramento.

  - Configurar o registro de detalhes de chamadas (CDR) e a coleta de dados de Qualidade de Experiência (QoE). O registro de detalhes de chamadas fornece uma maneira de rastrear o uso dos recursos do Lync Server, como chamadas telefônicas via Voice over IP (VoIP); mensagens instantâneas (IM); transferências de arquivos; conferências de áudio/vídeo (A/V) e sessões de compartilhamento de aplicativos. Métricas de QoE rastreiam a qualidade de chamadas de áudio/vídeo feitas em sua organização, incluindo itens como o número de pacotes de rede perdidos, ruídos de fundo e o volume de "tremulação" (diferenças no intervalo de pacotes).

  - Limpar manualmente registros de CDR e/ou QoE do banco de dados de monitoramento.

