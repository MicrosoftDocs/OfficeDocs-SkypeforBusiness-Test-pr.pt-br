---
title: "Usar o “Ligue p/ mim no” com um telefone habilitado p/ Lync e Lync Server 2013"
TOCTitle: "Usar o “Ligue p/ mim no” com um telefone habilitado p/ Lync e Lync Server 2013"
ms:assetid: 975a1df8-a159-4aa4-a991-5972a535998e
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn383570(v=OCS.15)
ms:contentKeyID: 56558974
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Usar o “Ligue para mim no” com um telefone habilitado para Lync e Lync Server 2013

 

_**Tópico modificado em:** 2013-08-09_

O recurso Ligue para mim no Lync fornece uma maneira de os usuários ingressarem no áudio de uma conferência usando um telefone celular, "telefone fixo" ou outro dispositivo conectado à Rede telefônica pública comutada (PSTN). Quando você tentar ingressar em uma reunião usando o Lync, normalmente aparecerá a caixa de diálogo **Ingressar no Áudio da Reunião**:

![Captura de tela da janela de áudio para ingressar na reunião do Lync](images/Dn383570.e28f17f0-9f17-44ef-b893-f4ef132f47ac(OCS.15).png "Captura de tela da janela de áudio para ingressar na reunião do Lync")

Se você selecionar **Ligue para mim no**, pode escolher um número de telefone a partir da lista suspensa. O Lync Server 2013 fará uma chamada telefônica para o número selecionado e então você pode usar o telefone para participar do áudio da conferência.

A lista suspensa é preenchida pelos números de telefone (para telefone celular, telefone residencial ou outro telefone) que você digitou na guia **Telefones**, na caixa de diálogo **Lync – Opções**:

![Captura de tela da janela de configurar opções do Lync Phones](images/Dn383570.03d2f25d-49e2-47b4-b1e9-b1614fc0c11c(OCS.15).png "Captura de tela da janela de configurar opções do Lync Phones")

Se você não inseriu nenhum número de telefone na guia **Telefones**, não terá números disponíveis na caixa suspensa. No entanto, pode clicar em **Novo número** e discar com o Lync Server qualquer número de telefone desejado:

![Captura de tela da janela ligue-me de áudio para ingressar na reunião do Lync](images/Dn383570.27f2ac7a-cc1c-465c-b145-202ad03af4f2(OCS.15).png "Captura de tela da janela ligue-me de áudio para ingressar na reunião do Lync")

O recurso Ligue para mim no funciona muito bem desde que você o use para o que ele foi criado: usando o Lync Server para ligar para um número de telefone PSTN. No entanto, você pode acabar em uma em uma experiência com menos qualidade se solicitar ao Lync Server que ligue para você em um ponto de extremidade habilitado a Lync (por exemplo, um telefone em uma sala de conferência). Em seguida, vem o problema que pode encontrar bem como duas maneiras de contornar o problema.

Para começar, veja o que acontece quando você digita no recurso Ligue para mim no o número de telefone de um telefone habilitado ao Lync. Suponha que Ken Myer tente ingressar em uma reunião através de o Lync Server ligando para ele no 1-206-555-1219, um número de telefone habilitado a Lync Server. Ken será inicialmente conectado à reunião, mas depois de alguns segundos, o Lync exibirá a mensagem **Chamada Encerrada ou Não Completada** e Ken aparecerá como se tivesse se desconectado da reunião:

![Captura de tela da janela de conferência de chamada do Lync](images/Dn383570.c2a81727-8751-41b5-946a-03a1b75b9d95(OCS.15).png "Captura de tela da janela de conferência de chamada do Lync")

Observe, entretanto, que há uma discrepância na janela de conversa Lync. Ken Myer é o único nome listado no cabeçalho **Participantes**. No entanto, se você olhar na barra de título da janela, você verá que a conferência contém um total de quatro participantes.

Da mesma forma, se você olhar na janela de conversa de qualquer um dos outros participantes da conferência, não verá Ken Myer listado em nenhum lugar:

![Captura de tela da janela de lista de participantes do Lync](images/Dn383570.fa5990cf-2694-402c-ac06-946aa66b6837(OCS.15).png "Captura de tela da janela de lista de participantes do Lync")

Entretanto, ao mesmo tempo, Ken Myer poderá participar do áudio da chamada usando seu telefone habilitado a Lync. O recurso Ligue para mim no de fato funcionou, mas a experiência do usuário é inferior à ideal.

Há pelo menos duas soluções alternativas para este problema. Se você já ingressou em uma conferência desta forma (como Ken Myer fez), normalmente pode resolver o problema entrando em uma modalidade diferente. Por exemplo, se você enviar uma mensagem instantânea, a janela de conversa agora mostrará todos os participantes da conferência, incluindo você:

![Captura de tela da janela da lista de conversas e participantes do Lync](images/Dn383570.9b5ff6d6-9f73-467c-99a7-ef3aa8bd7e7a(OCS.15).png "Captura de tela da janela da lista de conversas e participantes do Lync")

este ponto, você deve conseguir participar da reunião da forma esperada.

Como alternativa, você pode evitar esse problema por completo, mudando a maneira de ingressar da reunião. Se você precisa que o Lync Server ligue para um telefone habilitado a Lync Server, deve começar ingressando na reunião sem uma conexão de áudio . Para isso, selecione Não ingressar no áudio quando aparece a caixa de diálogo Ingressar no Áudio da Reunião:

![Captura de tela da janela de áudio para não ingressar na reunião do Lync](images/Dn383570.280a148d-cce5-4b02-87f9-9f78f17a81c1(OCS.15).png "Captura de tela da janela de áudio para não ingressar na reunião do Lync")

Após ter se conectado com êxito à reunião, pode "convidar" o telefone habilitado a Lync Server a também ingressar na reunião. Para isso, posicione o mouse sobre o ícone Pessoas e, em seguida, clique em **Convidar mais pessoas**:

![Captura de tela da janela para convidar mais participantes do Lync](images/Dn383570.69b81b29-d1d2-4ed3-acb6-e37dd18e3d86(OCS.15).png "Captura de tela da janela para convidar mais participantes do Lync")

Isso abrirá a caixa de diálogo **Enviar uma Mensagem Instantânea**. Ignore o título da caixa de diálogo (você não está realmente enviando uma mensagem instantânea) e digite o número de telefone do telefone habilitado a Lync:

![Captura de tela da caixa de diálogo Enviar uma Mensagem Instantânea](images/Dn383570.cd67a3f0-06d8-41ba-a808-c067f64bec9f(OCS.15).png "Captura de tela da caixa de diálogo Enviar uma Mensagem Instantânea")

Após clicar em **OK**, o Lync Server ligará para o número digitado na caixa de diálogo. Quando a conexão for realizada, você terá recursos de áudio completos através do telefone habilitado ao Lync e poderá ver e interagir com todos os participantes da conferência.

