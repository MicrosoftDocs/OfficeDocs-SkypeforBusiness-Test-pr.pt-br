---
title: Habilitar monitoramento no Lync Server 2013
TOCTitle: Habilitar monitoramento no Lync Server 2013
ms:assetid: 244df419-d0a8-4b1d-aedd-a92114172ab6
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ687994(v=OCS.15)
ms:contentKeyID: 49886136
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Habilitar monitoramento no Lync Server 2013

 

_**Tópico modificado em:** 2012-10-17_

Embora os agentes do conjunto de dados unificados sejam instalados e ativados automaticamente em cada servidor de Front-End, isto não significa que você irá começar automaticamente a coletar dados de monitoramento no momento da finalização da instalação do Microsoft Lync Server 2013. Ao invés disso, você deve fazer duas coisas: associar seus pools de servidores de Front-End/servidores de Front-end com um banco de dados de monitoramento e deve habilitar o registro de detalhes da chamada (CDR) e/ou monitoramento da Qualidade de Experiência (QoE) no escopo global e/ou local.

Para instruções passo a passo na associação dos servidores de Front-End ou pools de Front-end com um banco de dados de monitoramento, consulte o tópico [Associando um Repositório de Monitoramento ao Pool de Front End](lync-server-2013-associating-a-monitoring-store-with-a-front-end-pool.md) no guia de Implantação. Após estas associações serem realizadas e após sua nova topologia do Lync Server ter sido publicada, você ainda não poderá coletar dados de monitoramento. Isto ocorre porque, por padrão, o conjunto de dados CDR e QoE é desabilitado ao instalar o Lync Server 2013.

Para poder começar a coletar dados necessários habilite o CDR e/ou monitoramento QoE. (Observe que você não precisa habilitar o CDR e o monitoramento QoE; se preferir, é possível habilitar um tipo de monitoramento enquanto o outro tipo permanece desabilitado.) Para habilitar o monitoramento CDR no escopo global, execute o seguinte comando dentro do Shell de Gerenciamento do Lync Server:

    Set-CsCdrConfiguration -Identity "global" -EnableCDR $True

Em alternativa, é possível habilitar o monitoramento CDR dentro do Painel de Controle do Lync Server 2013. Dentro do Painel de Controle do Lync Server, realize o seguinte procedimento:

1.  Clique em **Monitoramento**.

2.  Na guia **Registro de Detalhes da Chamada**, clique duas vezes na configuração **Global**.

3.  No painel **Editar configuração do registro de detalhe da chamada (CDR)**, selecione **Habilitar monitoramento de CDRs** e clique em **Confirmar**.

Para habilitar o monitoramento QoE no escopo global, execute este comando dentro do Shell de Gerenciamento do Lync Server:

    Set-CsQoEConfiguration -Identity "global" -EnableQoE $True

Se você preferir, também é possível habilitar o monitoramento QoE dentro do Painel de Controle do Lync Server. No Painel de Controle, conclua o seguinte procedimento:

1.  Clique em **Monitoramento**.

2.  Na guia **Dados da Qualidade da Experiência**, clique duas vezes na configuração **Global**.

3.  No painel **Editar configuração da Qualidade da Experiência (QoE)**, selecione **Habilitar monitoramento de dados QoE** e clique em **Confirmar**.

Como observado, os exemplos anteriores habilitam o monitoramento no escopo global; isto é, eles habilitam o monitoramento CDR e QoE através da sua organização. Em alternativa, é possível criar definições de configurações CDR e QoE separadas no escopo local e habilitar ou desabilitar seletivamente o monitoramento de cada local. Por exemplo, é possível habilitar o monitoramento CDR para seu local Redmond, desabilitar o monitoramento CDR para Dublin. Para obter mais informações sobre como gerenciar suas definições de configuração de monitoramento, consulte o tópico do guia de Implantação [Configurando registro de detalhes de chamada e definições de qualidade de experiência](lync-server-2013-configuring-call-detail-recording-and-quality-of-experience-settings.md).

