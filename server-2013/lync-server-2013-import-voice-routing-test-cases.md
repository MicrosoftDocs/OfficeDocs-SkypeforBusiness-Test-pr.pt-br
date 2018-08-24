---
title: 'Lync Server 2013: Importar casos de teste de roteamento de voz'
TOCTitle: Importar casos de teste de roteamento de voz
ms:assetid: 6546e24c-9ad2-428b-92b2-63948ed0f884
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398460(v=OCS.15)
ms:contentKeyID: 49306931
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Importar casos de teste de roteamento de voz no Lync Server 2013

 

_**Tópico modificado em:** 2013-02-21_

Os casos de teste oferecem uma maneira de testar rotas de voz em sua organização: você define elementos como o número a ser discado e o plano de discagem e a política de voz a serem aplicados. Em seguida, o Lync Server 2013 pode verificar se, dadas as condições, o número fornecido pode ser encaminhado com êxito para a rede PSTN.

Os casos de teste, que podem ser criados com o uso do Painel de Controle do Lync Server, geralmente são salvos apenas no servidor em que o caso foi originalmente criado e executado. No entanto, eles podem ser exportados como arquivos XML (com a extensão .vtest) e importados em outros servidores. Isso permite executar os mesmos testes em vários computadores localizados em diferentes pontos da sua topologia.

## Para importar um caso de teste de roteamento de voz

1.  Faça logon no computador como um membro do grupo RTCUniversalServerAdmins ou como um membro da função CsVoiceAdministrator, CsServerAdministrator ou CsAdministrator. Para obter detalhes, consulte [Delegar permissões de configuração no Lync Server 2013](lync-server-2013-delegate-setup-permissions.md).

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerdo, clique em **Roteamento de voz**.

4.  No menu **Ações**, clique em **Importar casos de teste**.

5.  Localize o arquivo de caso de teste (.vtest) que você deseja importar e clique em **Abrir**.

6.  Clique em **Confirmar** e, em seguida, clique em **Confirmar tudo**.
    
    > [!NOTE]  
    > Sempre que você importa um arquivo .vtest, deve executar o comando <strong>Confirmar todos</strong> para publicar o caso de teste. Para obter detalhes, consulte <a href="lync-server-2013-publish-pending-changes-to-the-voice-routing-configuration.md">Publicar alterações pendentes na configuração de roteamento de voz no Lync Server 2013</a> na documentação de operações.

## Consulte Também

#### Tarefas

[Exportar casos de teste de roteamento de voz no Lync Server 2013](lync-server-2013-export-voice-routing-test-cases.md)

