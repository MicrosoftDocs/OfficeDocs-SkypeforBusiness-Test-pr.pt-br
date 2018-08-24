---
title: 'Lync Server 2013: Iniciar serviços nos servidores'
TOCTitle: Iniciar serviços nos servidores
ms:assetid: fa26eaed-0529-4f32-9f3f-f32c4bd4b1c8
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg413059(v=OCS.15)
ms:contentKeyID: 49308670
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Iniciar serviços nos servidores para o Lync Server 2013

 

_**Tópico modificado em:** 2014-09-03_

Para concluir este procedimento com êxito, você deve fazer login como um usuário membro do grupo RTCUniversalServerAdmins ou ter as permissões corretas delegadas. Para obter informações detalhadas sobre como delegar permissões, consulte o tópico [Delegar permissões de configuração no Lync Server 2013](lync-server-2013-delegate-setup-permissions.md).

Após instalar o repositório de Configuração Local nos seus servidores, instalar os componentes do Lync Server 2013 e configurar os certificados em um Servidor Front-End ou Servidor Front-End, é necessário iniciar os serviços do Lync Server 2013 no servidor. Use o seguinte procedimento para iniciar os serviços em cada Servidor Front-End da sua implantação.

## Para iniciar os serviços em um Servidor Front-end ou Edição Standard

1.  No Assistente de Implantação do Lync Server, na página **Lync Server 2013**, clique em **Executar** próximo a **Etapa 4: Iniciar serviços** .

2.  Na página **Serviços iniciais** , clique em **Avançar** para iniciar os serviços do Lync Server no servidor.

3.  Na página **Executando comandos** , após todos os serviços serem iniciados com sucesso, clique em **Finalizar** .
    
    > [!IMPORTANT]  
    > O comando para iniciar os serviços no servidor é um método de esforço melhor para relatar que os serviços foram iniciados de fato. Ele pode não refletir o estado real do serviço. Recomendamos que você use a etapa <strong>Status do serviço (opcional)</strong> imediatamente após <strong>Iniciar serviços</strong> para abrir o Console de Gerenciamento da Microsoft (MMC) e confirmar que os serviços foram iniciados com êxito. Se qualquer serviço do Lync Server não iniciar, clique com o botão direito no serviço do MMC e clique em <strong>Iniciar</strong> .
