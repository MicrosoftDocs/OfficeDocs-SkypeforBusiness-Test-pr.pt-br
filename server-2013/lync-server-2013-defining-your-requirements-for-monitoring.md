---
title: 'Lync Server 2013: Definindo seus requisitos de monitoramento'
TOCTitle: Definindo os requisitos de monitoramento de sua organização
ms:assetid: d587ff04-9af6-4ac1-ad42-076e7a40ac75
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205284(v=OCS.15)
ms:contentKeyID: 49886432
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Definindo seus requisitos de monitoramento no Lync Server 2013

 

_**Tópico modificado em:** 2012-09-05_

Simplificar a implantação e instalação do monitoramento no Microsoft Lync Server 2013 também simplificou os processos envolvidos na definição dos requisitos da sua organização para monitoramento. Independente disto, ainda há vários problemas que devem ser abordados antes de iniciar a instalação e configuração do Lync Server 2013:

**Quais tipos de dados deseja monitorar?** O Lync Server 2013 permite monitorar dois tipos de dados diferentes: dados CDR e dados QoE. O registro de detalhes da chamada oferece uma forma de rastrear o uso dos recursos do Lync Server como chamadas de telefone VoIP; mensagem instantânea (IM); transferências de arquivos; conferência de áudio/vídeo (A/V); e sessões de compartilhamento de aplicativos. Esta informação ajuda você a saber quais recursos do Lync Server estão sendo usados (e quais não) e também oferece informações sobre quando estes recursos estão sendo usados. Os dados de Qualidade da Experiência permite você manter um registro de qualidade de chamadas de áudio e vídeo realizadas na sua organização, incluindo coisas como o número de pacotes de rede perdidos, ruído de plano de fundo e quantidade de "jitter" (diferenças no atraso do pacote).

Se você escolher habilitar o monitoramento no Lync Server 2013, é possível habilitar o monitoramento CDR e QoE ou escolher habilitar um tipo de monitoramento deixando o outro tipo desabilitado. Por exemplo, suponha que seus usuários apenas utilizem mensagem instantânea e transferência de arquivos e não realizem chamadas de áudio ou vídeo. Neste caso, pode não haver motivo para habilitar o monitoramento QoE. Da mesma forma, o Lync Server torna fácil habilitar e desabilitar o monitoramento após ter sido implantado. Por exemplo, você pode escolher implantar o monitoramento, mas deixar inicialmente o monitoramento QoE desabilitado. Se seus usuários começam a enfrentar problemas com chamadas de áudio e vídeo, habilite o monitoramento QoE e use estes dados para ajudar você a resolver problemas.

Não há uma determinada vantagem (ou desvantagem) para instalar o monitoramento no mesmo momento que você instalar o Lync Server contra a instalação de monitoramento após o Lync Server ter sido instalado. O único ponto a lembrar é que, antes de instalar o monitoramento, você deve selecionar um computador para hospedar o repositório de monitoramento de backend e uma versão suportada do SQL Server deve ser instalada e configurada neste computador antes de que possa ser usado para monitoramento. Se você já instalou o SQL Server em um computador e este computador está pronto para uso, é possível instalar o monitoramento no mesmo momento que você instalar o Lync Server. Se você não possui um computador de backend pronto, é possível continuar a instalar o Lync Server sozinho e a instalação do monitoramento sempre que o computador backend estiver pronto para uso.

**Quando você deseja instalar o monitoramento?** O monitoramento pode ser instalado e configurado no mesmo momento que você instalar e configurar o Lync Server 2013; o Assistente de Implantação do Lync Server oferecerá a oportunidade de associar seus pools de front-end com um banco de dados de monitoramento durante a instalação. Em alternativa, é possível instalar o monitoramento após o Lync Server ter sido instalado; isto pode ser realizado usando o Construtor de Topologia para associar seus pools de front-end e servidores com um banco de dados de monitoramento e publicar a topologia revisada.

**Quantos bancos de dados de monitoramento de backend você precisa?** Um único banco de dados de monitoramento pode suportar dezenas de milhares de usuários (para o Microsoft Lync Server 2010, foi estimado que um banco de dados posicionados para monitoramento e arquivamento pode suportar 240.000 usuários). Além disso, um único banco de dados de monitoramento pode ser usado por vários pools de front-end; se você possui três pools de front-end na sua organização, é possível associar todos os três pools com o mesmo repositório de backend.

Isto apenas simplifica que, para muitas organizações, a capacidade do banco de dados não será o fator decisivo ao determinar o número de bancos de dados de monitoramento de backend que serão necessários. Ao invés disso, uma consideração mais importante pode ser a velocidade da rede. Suponha que você possui três pools de front-end, mas um destes pools está localizado em uma conexão de rede lenta. Neste caso, você pode desejar usar dois bancos de dados de monitoramento: um banco de dados para serviço dos dois pools com boa conexão de rede e um banco de dados separado para serviço do pool com a conexão de rede mais lenta.

Ao planejar sua infraestrutura de monitoramento, você deve levar em conta que o Lync Server 2013 suporta o uso de bancos de dados espelho. "Espelhamento do banco de dados" oferece uma forma de manter simultaneamente duas cópias de um banco de dados, cada banco de dados residindo em um servidor diferente. Qualquer dado de tempo é gravado no banco de dados primário que o mesmo dado também é gravado no banco de dados de espelho. Se o banco de dados primário falhar ou tornar-se indisponível, é possível realizar o "fail over" no banco de dados espelho usando um comando simples do Lync Server PowerShell. Por exemplo:

    Invoke-CsDatabaseFailover -PoolFqdn atl-cs-001.litwareinc.com -DatabaseType "Monitoring" -NewPrincipal "Mirror"

Isto é importante para fins de planejamento porque o espelhamento exigirá o dobro do número exigido de bancos de dados: além de cada banco de dados primário, você precisará de um segundo banco de dados para agir como o espelho.

**Seus sites do Lync Server precisam de suas próprias configurações de monitoramento personalizado?** Ao instalar o Lync Server 2013, você também instala conjuntos globais de definições de configuração CDR e QoE; estes conjuntos globais oferecem a capacidade de aplicar as mesmas configurações CDR e QoE em toda sua organização. Em vários casos, isto pode ser suficiente: frequentemente, digamos, se você tiver o monitoramento CDR habilitado para todos os seus usuários.

No entanto, pode haver momentos quando você deseja aplicar configurações diferentes para sites diferentes. Por exemplo, talvez você deseje usar o monitoramento CDR e QoE em seu site Redmond, mas usar apenas o monitoramento CDR em seu site Dublin. Da mesma forma, você pode desejar manter os dados de monitoramento por 60 dias no site Redmond, mas precisa apenas manter este tipo de dados por 30 dias no site Dublin. O Lync Server 2013 permite criar conjuntos separados de definições de configurações CDR e QoE no escopo do site; isto permite gerenciar cada site diferentemente. (Isto inclui a habilitação e desabilitação do monitoramento, assim como a definição das configurações de gerenciamento como quanto tempo os dados devem ser mantidos.)

Observe que você pode tomar esta decisão antes de implantar o monitoramento ou após implantar o monitoramento. Por exemplo, é possível implantar o monitoramento e gerenciar toda a organização usando as configurações globais. Se você mudar de ideia posteriormente, é possível criar um conjunto separado de configurações para, digamos, o site Redmond, e usa estas configurações para gerenciar o monitoramento para Redmond. (As configurações aplicadas no escopo do site sempre têm precedência sobre as configurações aplicadas no escopo global.) Se você mudar de ideia novamente, basta excluir as definições de configuração aplicadas ao site Redmond. Quando um conjunto de configurações de site é removido, o conjunto global de configurações será aplicado automaticamente para este site.

