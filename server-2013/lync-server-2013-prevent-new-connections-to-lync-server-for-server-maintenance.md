---
title: Impedir novas conexões do Lync Server para manutenção do servidor
TOCTitle: Impedir novas conexões do Lync Server para manutenção do servidor
ms:assetid: 22b27adf-a590-43bd-9306-a5789ae108d7
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg520964(v=OCS.15)
ms:contentKeyID: 49306136
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Impedir novas conexões do Lync Server para manutenção do servidor

 

_**Tópico modificado em:** 2012-11-01_

O Lync Server permite colocar um servidor offline (por exemplo, para aplicar atualizações de software ou hardware) sem que ocorra perda de serviço para os usuários.

Quando você especifica a opção para impedir novas conexões ou chamadas a um servidor em um pool, ele para de aceitar novas conexões e chamadas assim que você implementa essa opção. Estas novas conexões e chamadas são roteadas através de outros servidores no pool. Um servidor que está evitando novas conexões permite que suas sessões em conexões existentes continuem até terminarem naturalmente. Quando todas as sessões existentes terminarem naturalmente, o servidor está pronto para ser colocado offline.

Quando você impede novas conexões com um servidor de Front-Ends, alguns recursos e serviços do Lync Server contam com o balanceamento de carga DNS para garantir o funcionamento correto. Se você não estiver usando o balanceamento de carga DNS no pool, as conexões por meio desses serviços poderão não ser redirecionados para outros servidores durante o período no qual o servidor está impedindo novas conexões e, portanto, quando o servidor é colocado offline, algumas sessões e chamadas podem ser interrompidas. Estes são os recursos que dependem do balanceamento de carga DNS para garantir que esta opção funcione corretamente:

  - Atendedor

  - Aplicativo Comunicado de Conferência

  - Aplicativo Grupo de Resposta

  - Aplicativo Comunicado

  - Aplicativo de Estacionamento de Chamada

Para obter detalhes sobre o balanceamento de carga DNS, consulte [Balanceamento de carga DNS no Lync Server 2013](lync-server-2013-dns-load-balancing.md) na documentação de Planejamento.

Além para impedir novas conexões com todos os serviços em um servidor que executa o Lync Server, você também pode impedir novas conexões com serviços individuais do Lync Server. Por exemplo, esse método é útil em uma situação onde você precisa aplicar uma atualização do Lync Server que não exige o desligamento de todo o servidor. Observe que, quando você impede conexões com um serviço, deve selecionar um serviço que é agrupado e exibido na lista de serviços do Windows. Por exemplo, o serviço Front-End do Lync Server e o agente de coleta de dados do Monitoring Server são serviços separados do Lync Server, mas na lista de serviços do Windows eles serão consolidados e mostrados como o serviço de Front-End do Lync Server. Você pode impedir novas conexões com o serviço de Front-End do Lync Server, mas não pode impedir novas conexões com esses dois serviços individuais subjacentes do Lync Server separadamente.

> [!IMPORTANT]  
> Quando você configura um servidor para evitar novas conexões e o reinicia, por padrão ele imediatamente aceitará novas conexões de novo. Para que isso não ocorra, configure o servidor manualmente para que pause e retome antes de reiniciá-lo.

## Para evitar novas conexões ao Lync Server:

1.  Faça logon no computador local como membro do grupo Administradores.

2.  Abra o snap-in console Serviços: clique em **Iniciar**, **Todos os programas**, **Ferramentas administrativas** e clique em **Serviços**.

3.  Na lista, clique duas vezes, clique duas vezes no serviço Lync Server Windows com o qual você deseja evitar novas conexões.

4.  Na caixa de diálogo Propriedades, em **Status do serviço: Iniciado**, clique em **Pausar**.

5.  Opcionalmente, mas recomendado, clique em **Manual** ao lado de **Tipo de inicialização**.
    
    > [!IMPORTANT]  
    > Quando você define um servidor para impedir novas conexões e reiniciar o servidor, por padrão, o servidor começa imediatamente a aceitar novas conexões depois de ser inicializado. Para evitar isso, defina o servidor para apenas pausar e reiniciar manualmente antes de reiniciá-lo.

6.  Quando terminar, clique em **OK**.

