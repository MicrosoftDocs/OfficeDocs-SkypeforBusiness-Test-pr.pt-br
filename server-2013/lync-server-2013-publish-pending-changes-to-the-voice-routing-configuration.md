---
title: 'Lync Server 2013: Publicar alterações pendentes na configuração de roteamento de voz'
TOCTitle: Publicar alterações pendentes na configuração de roteamento de voz
ms:assetid: ff941d0b-fb4b-47d2-b866-6d990ac66b81
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg413088(v=OCS.15)
ms:contentKeyID: 49308727
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Publicar alterações pendentes na configuração de roteamento de voz no Lync Server 2013

 

_**Tópico modificado em:** 2012-08-07_

Após fazer alterações em qualquer uma das definições de configuração nas páginas do grupo **Roteamento de Voz** , execute este procedimento para examinar, publicar ou cancelar as alterações pendentes.

> [!IMPORTANT]  
> Certifique-se de que somente um usuário por vez modifique as definições de configurações do Roteamento de voz.<br />Todas as alterações pendentes devem ser publicadas ao mesmo tempo, executando o comando <strong>Confirmar todos</strong> . Não é possível publicar seletivamente as alterações pendentes. Antes de publicar as alterações pendentes, execute o comando <strong>Revisar alterações não confirmadas</strong> e cancele qualquer alteração de configuração que não deseja publicar.<br />Se você navegar longe das páginas do grupo <strong>Roteamento de voz</strong> antes de confirmar as alterações pendentes, todas as alterações pendentes serão perdida. No entanto, é possível exportar a configuração atual (incluindo quaisquer alterações pendentes) para um arquivo de configuração de voz e, em seguida, importar e publicar a configuração atualizada. Para obter detalhes, consulte <a href="lync-server-2013-export-a-voice-route-configuration-file.md">Exportar um arquivo de configuração de rota de voz no Lync Server 2013</a>.

## Para revisar, publicar ou cancelar as alterações de configuração do roteamento de voz

1.  Faça logon no computador como um membro do grupo RTCUniversalServerAdmins ou como um membro da função CsVoiceAdministrator, CsServerAdministrator ou CsAdministrator. Para obter detalhes, consulte [Delegar permissões de configuração no Lync Server 2013](lync-server-2013-delegate-setup-permissions.md).

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerdo, clique em **Roteamento de voz** .

4.  Faça as alterações de configuração que deseja para as configurações em cada página do grupo **Roteamento de voz** .

5.  Para revisar as alterações pendentes sem publicá-las, selecione **Revisar alterações não confirmadas** no menu **Confirmar** .

6.  Se você deseja cancelar qualquer alteração pendente, siga um destes procedimentos:
    
      - Selecione **Cancelar todas as alterações não confirmadas** no menu **Confirmar** .
    
      - Navegue até a guia da página **Roteamento de voz** que possui as alterações pendente que deseja cancelar, selecione o item com as alterações pendentes, clique em **Confirmar** e em **Cancelar alterações selecionadas** .

7.  Após revisar todas as alterações pendentes e cancelar qualquer uma que não deseja publicar, clique em **Confirmar** e em **Confirmar todas** .

8.  Na caixa de diálogo **Definições da configuração de voz não confirmadas** que exibe uma lista de todas as alterações pendentes, clique em **OK** .
    
    Quando o Painel de Controle do Lync Server confirmar as alterações, a mensagem **Configuração de roteamento de voz publicada com êxito** é exibida.

