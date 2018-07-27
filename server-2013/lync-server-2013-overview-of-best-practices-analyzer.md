---
title: Visão Geral do Analisador de Práticas Recomendadas
TOCTitle: Visão Geral do Analisador de Práticas Recomendadas
ms:assetid: c5fcaa05-eb1c-4092-90ad-177b127e795b
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg591349(v=OCS.15)
ms:contentKeyID: 49308067
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Visão Geral do Analisador de Práticas Recomendadas

 

_**Tópico modificado em:** 2012-09-19_

É possível usar o Lync Server 2013, Analisador de Prática Recomendada para identificar e resolver problemas com sua implantação do Lync Server 2013. O Lync Server 2013, Analisador de Prática Recomendada reúne informações de configuração dos componentes do Lync Server 2013.

Com o acesso de rede adequado, o Analisador de Prática Recomendada pode examinar servidores executando os Serviços de Domínio do Active Directory, o Exchange Server Unified Messaging (UM) e Lync Server 2013. É possível usar o Analisador de Prática Recomendada para fazer o seguinte:

  - Realize proativamente verificações, analisando se a configuração está definida de acordo com as práticas recomendadas.

  - Detectar automaticamente exige atualizações para o Lync Server 2013.

  - Gerar uma lista de problemas, como as definições de configuração inadequadas, opções não suportadas, atualizações ausentes ou práticas não recomendadas.

  - Ajuda para resolver problema e corrigir problemas específicos.

O Analisador de Prática Recomendada oferece os seguintes recursos:

  - Pré-requisitos de instalação mínimos.

  - Documentação online sobre problemas relatados, incluindo dicas de resolução de problemas.

  - Informação de configuração que você pode salvar para revisão posterior.

  - Análise do sistema de tecnologia de ponta.

O Analisador de Prática Recomendada usa um conjunto de arquivos de configuração XML para determinar a informação a reunir do seu ambiente do Lync Server 2013. Além de verificar os Serviços de Domínio do Active Directory, verifica as fontes como o registro do sistema operacional do Windows Server e as configurações no Windows Management Instrumentation (WMI).

O Analisador de Prática Recomendada compara os dados reunidos com um conjunto de regras pré-definidas para definições e configurações das implantações do Lync Server 2013.

Após comparar os dados coletados com as regras pré-definidas, a ferramenta relata problemas. Para cada problema relatado, o Analisador de Prática Recomendada oferece informações sobre o que foi encontrado no ambiente do Lync Server 2013 verificado e a configuração recomendada. O Analisador de Prática Recomendada também oferece links para informações mais detalhadas sobre problemas específicos.

> [!NOTE]  
> O Lync Server 2013, Analisador de Prática Recomendada reúne as informações de configuração apenas de componentes do Lync Server 2013. É possível usar versões anteriores da ferramenta para verificar ambientes anteriores. Para obter detalhes, consulte <a href="lync-server-2013-requirements-for-running-best-practices-analyzer.md">Requisitos para Excutar o Analisador de Práticas Recomendadas</a>.
