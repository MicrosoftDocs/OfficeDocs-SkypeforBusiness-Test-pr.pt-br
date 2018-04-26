---
title: Entendendo os relatórios criados pelo Analisador de Práticas Recomendadas
TOCTitle: Entendendo os relatórios criados pelo Analisador de Práticas Recomendadas
ms:assetid: 1386dd6c-7f3e-4da9-905b-cef1468bf14a
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg591344(v=OCS.15)
ms:contentKeyID: 49305955
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Entendendo os relatórios criados pelo Analisador de Práticas Recomendadas

 

_**Tópico modificado em:** 2012-10-10_

O Analisador de Práticas Recomendadas fornece vários tipos de relatórios, organizados para facilitar a análise e a solução de problemas. O Analisador identifica problemas como erros, avisos e outras informações.

## Relatórios

Você pode acessar os resultados de uma varredura exibindo cada um dos seguintes relatórios:

  - **Relatórios de lista**   Relatórios de lista são organizados por um critério específico. Você pode organizar os resultados por classe, gravidade ou problema. Por exemplo, se você organizar os resultados por classe, os problemas relacionados a Diretores serão incluídos sob a seção Diretores do relatório. Você pode exibir todos os problemas ou somente os itens informativos. Você pode pesquisar um relatório de lista por itens específicos, como memória e também pode imprimir ou exportar o relatório.

  - **Relatórios em árvore**   Relatórios em árvore são organizados pelas regras usadas para executar a varredura e outras opções especificadas no momento em que a varredura foi executada. Por exemplo, problemas relacionados a regras da Topologia de Teste são incluídos sob a seção Topologia de Teste do relatório. Você pode exibir detalhes de todos os problemas ou somente um resumo. Você pode pesquisar um relatório em lista por itens específicos, como memória e também pode imprimir ou exportar o relatório.

  - **Outros relatórios**   Itens em outros relatórios incluem o log do tempo de execução das tarefas incluídas na varredura. Você pode pesquisar os itens em outros relatórios por itens específicos, como memória e também pode imprimir ou exportar o relatório.

## Problemas

Os relatórios gerados pelo Analisador de Práticas Recomendadas indicam problemas específicos identificados durante a varredura do seu ambiente, incluindo os seguintes tipos:

  - **Erros**   Problemas críticos que exigem uma alteração no ambiente. Por exemplo, se os Componentes Principais do Lync Server 2013 não estiverem instalados, um erro é registrado no log.
    
    Problemas classificados como erros são identificados no relatório por um símbolo X vermelho. Erros são exibidos na guia **Todos os Problemas** do modo de exibição **Relatórios de Lista** e nas guias **Exibição Detalhada** e **Exibição de Resumo** do modo de exibição **Relatórios em Árvore**. Se você não deseja ver um erro específico em um relatório, pode especificar que o erro não seja exibido para uma única instância ou para todas as instâncias do erro no relatório. O erro é então exibido somente na guia **Itens Ocultos** do modo de exibição **Outros Relatórios**, a menos que você altere a configuração e especifique que o erro seja exibido no relatório.

  - **Avisos**   Problemas que não são consistentes com a implementação de uma prática recomendada. Isso pode ou não indicar a necessidade de uma alteração no ambiente. O problema pode ser conhecido com uma configuração específica que não precisa ser alterada. Por exemplo, serviços que não são iniciados em um servidor são registrados em log como avisos.
    
    Problemas classificados como avisos são identificados no relatório com um símbolo de aviso triangular amarelo. Avisos são exibidos na guia **Todos os Problemas** do modo de exibição **Relatórios de Lista**, bem como nas guias **Exibição Detalhada** e **Exibição de Resumo** do modo de exibição **Relatórios em Árvore**. Se você não deseja ver um erro específico em um relatório, pode especificar que o erro não seja exibido para uma única instância ou para todas as instâncias do erro no relatório. O aviso é então exibido somente na guia **Itens Ocultos** do modo de exibição **Outros Relatórios**, a menos que você altere a configuração e especifique que o aviso seja exibido no relatório.

  - **Informações**   Inclui todos os problemas que não são classificados como erros ou avisos. Por exemplo, o número de objetos de servidor Lync Server 2013 Standard Edition no Serviços de Domínio Active Directory é classificado como informação.
    
    Informações são exibidas na guia **Todos os Problemas** do modo de exibição **Relatórios de Lista** e na guia **Exibição Detalhada** do modo de exibição **Relatórios em Árvore**.

O Analisador de Práticas Recomendadas do Lync Server 2013 não faz alterações no ambiente para resolver problemas. A varredura somente detecta possíveis problemas e fornece relatórios que contêm informações sobre como resolver cada um deles.

Ao clicar em um problema, uma explicação e algumas opções são exibidas para problemas específicos. Assim, você pode:

  - Encontrar informações mais detalhadas sobre o problema e sobre como resolvê-lo.

  - Interromper a exibição de problemas em relatórios:
    
      - Interromper a exibição de problemas para a instância selecionada.
    
      - Interromper a exibição de problemas para todas as instâncias daquele problema.
    
    Para ver os problemas para os quais a exibição nos relatórios foi interrompida, vá até a guia **Itens Ocultos** do modo de exibição **Outros Relatórios**. Neste local você pode especificar para iniciar a exibição de problemas nos relatórios novamente.

Para detalhes sobre como resolver problemas específicos, consulte [Analisando e Resolvendo Problemas Identificados pelo Analisador de Práticas Recomendadas](lync-server-2013-analyzing-and-resolving-issues-identified-by-best-practices-analyzer.md).

