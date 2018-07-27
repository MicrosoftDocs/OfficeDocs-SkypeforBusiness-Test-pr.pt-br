---
title: Problemas com o teste de topologia
TOCTitle: Problemas com o teste de topologia
ms:assetid: 821e8916-7b5d-4f64-8fb0-e5cc392ec1bb
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205045(v=OCS.15)
ms:contentKeyID: 49307295
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Problemas com o teste de topologia

 

_**Tópico modificado em:** 2012-09-21_

Como o cmdlet **Test-CsTopology**, o Analisador de Prática Recomendada oferece uma forma de verificar se o Lync Server 2013 está funcionando corretamente em um nível global. Por padrão, o Analisador de Prática Recomendada, como o cmdlet, verifica toda a sua infraestrutura do Lync Server 2013, verificando se os serviços necessários estão em execução e se as permissões apropriadas foram definidas para estes serviços e para os grupos de segurança universal criados quando você instalou o Lync Server 2013.

Além de verificar a validade de Lync Server como um todo, **Test-CsTopology** também verifica a valididade de um serviço específico. Para detalhes sobre como usar o cmdlet para testar serviços específicos, consulte a documentação [Test-CsTopology](https://docs.microsoft.com/en-us/powershell/module/skype/Test-CsTopology) in the Shell de Gerenciamento do Lync Server. Use as informações a seguir para ajudar a resolver problemas com sua topologia.

> [!NOTE]  
> Dependendo da configurçaão de seus servidores de borda e quasquer definições de rede de perímetro relacionada, incluindo de firewall e permissões, o Analisar de Práticas Recomendadas pode não conseguir acessar e escanear seus servidores de borda. Se incluir servidores de borda no escaneamento e os relatórios indicarem que há um problema no acesso aos servidores de borda, remova a seleção da caixa <strong>Servidores de Borda</strong> e execute o scan novamente para evitar que o problema conste nos relatórios.

## Resolver problemas com sua topologia

Se o teste de topologia encontrar problemas com sua topologia, esses problemas são provavelmente causados por problemas que ocorreram quando você publicou ou habilitou sua topologia.

Ao fazer modificações em sua topologia, elas entrarão em efeito somente quando forem publicadas e habilitadas. Você deve usar Construtor de Topologias para fazer modificações na topologia. Após fazê-las, você pode publicá-las e habilitá-las usando Construtor de Topologias.

Ao publicar as mudanças, as novas informações (por exemplo, um novo site ou uma nova função de servidor) são gravadas no Repositório de Gerenciamento Central. Contudo, esses novos (ou recém-modificados) objetos não entrarão imediatamente em sua topologia. Os objetivos entram em sua topologia somente quando você permite a atualização da topologia. Se você selecionar a opção Publicar em Construtor de Topologias, ocorrerá o seguinte: as modificações são publicadas (ou seja, elas são gravadas no Repositório de Gerenciamento Central) e a nova topologia é habilitada.

Por padrão, membros do grupo RTCUniversalServerAdmins estão autorizados a executar os cmdlets **Publish-CsTopology** e **Enable-CsTopology**. Contudo, se permissões de configuração não foram delegadas, você estar logado como administrador do domínio para executar **Publish-CsTopology**. Para atribuir a RTCUniversalServerAdmins o direito de realmente usar o cmdlet **Publish-CsTopology**, você deve executar o cmdlet **Grant-CsSetupPermission** em cada recipiente do Active Directory que contém os computadores executando serviços de Lync Server. Para atribuir a RTCUniversalServerAdmins o direito de usar o cmdlet **Enable-CsTopology**, você deve executar o cmdlet **Set-CsSetupPermission** em cada recipiente dos Serviços de Domínio do Active Directory com computadores executando serviços do Lync Server. Observe que isso se aplica à habilitação e publicação de uma topologia usando Construtor de Topologias. Se não tiver delegado permissões usando **Set-CsSetupPermission**, somente o administrador de domínio poderá habilitar e publicar uma topologia por Construtor de Topologias.

