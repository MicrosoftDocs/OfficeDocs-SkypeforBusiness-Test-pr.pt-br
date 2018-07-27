---
title: 'Lync Server 2013: Configurar FQDNs da web farm'
TOCTitle: Configurar FQDNs da web farm
ms:assetid: cb25dbbd-dcea-4997-8e14-e5007dd7d3ca
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg429722(v=OCS.15)
ms:contentKeyID: 49308119
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurar FQDNs da web farm para Lync Server 2013

 

_**Tópico modificado em:** 2013-03-29_

Ao definir a configuração do servidor Standard Edition, Pool de Front-Ends, Diretor ou Pool de diretores no Construtor de Topologias, você configura um FQDN dos serviços da Web externos. Durante o processo de login de um cliente hospedado no servidor do Standard Edition ou Pool de Front-Ends, os FQDNs dos serviços da Web configurados são enviados através de um provisionamento em banda. Se você precisar adicionar ou alterar a URL dos serviços da Web externos, você usa o Construtor de Topologias para configurar ou reconfigurar as definições dos serviços da Web usando o procedimento neste tópico.

## Para configurar um FQDN de pool externo para serviços da Web

1.  Inicie o Construtor de Topologias: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Construtor de Topologias do Lync Server**.

2.  No Construtor de Topologias, na árvore de console em **Front-ends do Standard Edition** , **Front-ends do Enterprise Edition** e **Diretores** , clique com o botão direito no nome do pool que você precisa editar e clique em **Editar propriedades** .

3.  Na seção **Serviços da Web** , adicione ou edite o **FQDN de serviços da Web externos** .

4.  Revise e ajuste as **Portas do ouvinte** para HTTP e HTTPS. Os padrões serão:
    
      - **Portas do ouvinte:** HTTP 8080, HTTPS 4443
    
      - **Portas publicadas:** HTTP 80, HTTPS 443
    
    Onde as **Portas do ouvinte** são as portas onde os serviços da Web externos serão configurados para receber solicitações do proxy inverso e as **Portas publicadas** são as portas publicadas externamente pelo proxy inverso e são comunicadas para clientes durante o provisionamento em banda.

5.  Ao concluir as adições e atualizações, clique em **OK** para continuar.

6.  Clique com o botão direito em **Lync Server 2013** e clique em **Publicar** .
    
    > [!IMPORTANT]  
    > Após a publicação concluir com sucesso, um link pode ser apresentado informando que existem etapas adicionais que precisam ser realizadas. O link, se clicado, abre uma lista de servidores afetados pelas alterações realizadas no Construtor de Topologias que exigem a nova execução do Assistente de Implantação do Lync Server em cada servidor listado para atualizar a configuração de componentes adicionados, removidos ou alterados.

7.  Repita essas etapas para cada servidor Standard Edition, Pool de Front-Ends, Diretor ou Pool de diretores na organização.

