---
title: 'Lync Server 2013: Importar um arquivo de configuração de rota de voz'
TOCTitle: Importar um arquivo de configuração de rota de voz
ms:assetid: 4bac05e5-ed8b-4f10-96b0-b8a65ff356ec
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398301(v=OCS.15)
ms:contentKeyID: 49306639
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Importar um arquivo de configuração de rota de voz no Lync Server 2013

 

_**Tópico modificado em:** 2012-11-01_

Se quiser salvar sua configuração de roteamento de voz sem publicá-la, siga as etapas deste tópico para usar os comandos de exportação e importação de configuração do Painel de Controle do Lync Server para salvar e recuperar um instantâneo da sua configuração de roteamento de voz. Quando você importa um arquivo de configuração de roteamento de voz (.vcfg), mas fez alterações na configuração de roteamento de voz no servidor nesse tempo, as páginas do grupo **Roteamento de Voz** do Painel de Controle do Lync Server indicarão que há alterações não confirmadas para o roteamento de voz. Essas alterações não confirmadas são as diferenças entre as duas configurações que exigem reconciliação.

Se você tiver feito qualquer alteração não confirmada na configurações de qualquer página dentro do grupo, as alterações serão salvas no arquivo de configuração de voz exportado (.vcfg). Isso permite que você faça alterações na configuração de roteamento de voz durante múltiplas sessões antes de publicar as alterações.

## Para importar uma configuração de roteamento de voz

1.  Faça logon no computador como um membro do grupo RTCUniversalServerAdmins ou como um membro da função CsVoiceAdministrator, CsServerAdministrator ou CsAdministrator. Para obter detalhes, consulte [Delegar permissões de configuração no Lync Server 2013](lync-server-2013-delegate-setup-permissions.md).

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerdo, clique em **Roteamento de voz** .

4.  No menu **Ações** , clique em **Importar Configuração** .

5.  Localize o arquivo de configuração que você deseja importar e clique em **Abrir** .

6.  Clique em **Confirmar** e, em seguida, clique em **Confirmar tudo** .
    
    > [!NOTE]  
    > Sempre que importar um arquivo de configuração de voz, você deve executar o comando <strong>Confirmar tudo</strong> para publicar a alteração na configuração. Para obter detalhes, consulte <a href="lync-server-2013-publish-pending-changes-to-the-voice-routing-configuration.md">Publicar alterações pendentes na configuração de roteamento de voz no Lync Server 2013</a> na documentação de Operações.

## Consulte Também

#### Tarefas

[Exportar um arquivo de configuração de rota de voz no Lync Server 2013](lync-server-2013-export-a-voice-route-configuration-file.md)  
[Publicar alterações pendentes na configuração de roteamento de voz no Lync Server 2013](lync-server-2013-publish-pending-changes-to-the-voice-routing-configuration.md)

