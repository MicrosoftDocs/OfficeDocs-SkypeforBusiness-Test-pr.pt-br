---
title: 'Lync Server 2013: Exportar casos de teste de roteamento de voz'
TOCTitle: Exportar casos de teste de roteamento de voz
ms:assetid: 489ac472-1a35-4755-b390-48f7cdf31e94
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg425957(v=OCS.15)
ms:contentKeyID: 49306599
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Exportar casos de teste de roteamento de voz no Lync Server 2013

 

_**Tópico modificado em:** 2012-11-01_

Os casos de teste oferecem uma maneira de testar rotas de voz em sua organização: você define elementos como o número a ser discado e o plano de discagem e a política de voz a serem aplicados. Em seguida, o Lync Server pode verificar se, dadas as condições, o número fornecido pode ser encaminhado com êxito para a rede PSTN.

Os casos de teste, que podem ser criados com o uso do Painel de Controle do Lync Server, geralmente são salvos apenas no servidor em que o caso foi originalmente criado e executado. No entanto, eles podem ser exportados como arquivos XML (com a extensão .vtest) e importados em outros servidores. Isso permite executar os mesmos testes em vários computadores localizados em diferentes pontos da sua topologia.

## Para exportar um caso de teste de roteamento de voz

1.  Em Painel de Controle do Lync Server, clique em **Roteamento de voz** e, então, em **Testar roteamento de voz** .

2.  Na guia **Testar roteamento de voz** , selecione o caso de teste (ou casos) a ser exportado. Para selecionar vários casos de teste, clique no primeiro caso a ser exportado e, então, mantenha a tecla Ctrl pressionada e selecione os casos adicionais a serem exportados.

3.  Clique em **Ações** e, então, em **Exportar casos de teste** .

4.  Na caixa de diálogo **Salvar como** , selecione uma pasta para armazenar os casos de teste exportados e digite um nome para o arquivo XML resultante na caixa **Nome do arquivo** . Observe que, se você estiver exportando vários casos de testes, todos eles serão salvos em um único arquivo XML.

5.  Para salvar os casos de teste, clique em **Salvar** .

## Consulte Também

#### Tarefas

[Importar casos de teste de roteamento de voz no Lync Server 2013](lync-server-2013-import-voice-routing-test-cases.md)

