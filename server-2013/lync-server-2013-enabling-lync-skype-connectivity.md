---
title: 'Lync Server 2013: Habilitando conectividade Lync-Skype'
TOCTitle: Habilitando conectividade Lync-Skype
ms:assetid: 34c4db3e-582f-41fb-85c4-3438ae02f09f
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn440170(v=OCS.15)
ms:contentKeyID: 59602790
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Habilitando conectividade Lync-Skype no Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

Depois de ter enviado a solicitação de provisionamento, você poderá se concentrar no ambiente do Lync Server e em tarefas administrativas necessárias para a configuração da conectividade Lync-Skype. Nesta seção, supomos que o administrador do Lync Server tenha implantado o Lync Server e configurado o acesso externo. Para obter informações adicionais sobre a configuração de acesso externo para o Lync Server, consulte [Planejamento para acesso de usuário externo no Lync Server 2013](lync-server-2013-planning-for-external-user-access.md) e [Implantação de acesso do usuário externo no Lync Server 2013](lync-server-2013-deploying-external-user-access.md).

Para preparar o ambiente do Lync Server para conectividade Lync-Skype, o administrador do Lync Server deve concluir estas três tarefas:

## 1\. Configurar a federação e o PIC

A federação é necessária para permitir que os usuários do Skype se comuniquem com os usuários do Lync em sua organização. A Conectividade a Redes Públicas de Mensagens Instantâneas (PIC) é uma classe de federação e deve ser configurada para permitir que seus usuários do Lync se comuniquem com os usuários do Skype. A federação e o PIC são configurados usando o Painel de Controle do Lync Server, mostrado abaixo.

![Mostrando PIC](images/Dn440170.451b94e3-0b38-488c-835f-1f25690e8074(OCS.15).jpg "Mostrando PIC")

> [!IMPORTANT]  
> A federação de PIC não tem mais suporte no Live Communication Server 2005 SP1 ou no Office Communications Server 2007. As plataformas que dão suporte à federação de PIC incluem o Lync Server 2013, o Lync Server 2010 e o Office Communications Server 2007 R2.

## 2\. Configurar pelo menos uma política para dar suporte ao acesso de usuário federado

Usando o Painel de Controle do Lync Server, um administrador deve configurar uma ou mais políticas de usuário externo para controlar se os usuários do Skype podem colaborar com usuários internos do Lync Server.

![Poíticas](images/Dn440170.8fd46ad1-9749-422c-8c47-c16ac9032cdb(OCS.15).jpg "Poíticas")

## 3\. Configurar a configuração do provedor de PIC do Skype para o Lync

Usando o Shell de Gerenciamento do Lync Server, um administrador deve configurar a política de cliente do Lync para exibir o Skype como um provedor de PIC adicional.

> [!NOTE]  
> Usuários de provedores de serviço do PIC (Conectividade a Redes Públicas de IM) não podem participar de conferências de áudio, de vídeo ou por mensagem instantânea em sua organização até que você também configure pelo menos uma política (etapa 2, previamente neste procedimento) para suportar conectividade a redes públicas de mensagens instantâneas.

1.  Para configurar a federação e o PIC, consulte "Habilitar ou desabilitar a federação e a Conectividade a Redes Públicas de Mensagens Instantâneas" em [http://go.microsoft.com/fwlink/p/?LinkId=306063](http://go.microsoft.com/fwlink/p/?linkid=306063).

2.  Para configurar pelo menos uma política para dar suporte ao acesso de usuário federado, consulte "Configurar políticas para controlar o acesso de usuário público" em [http://go.microsoft.com/fwlink/p/?LinkId=306064](http://go.microsoft.com/fwlink/p/?linkid=306064).

**Para editar um provedor de Messenger PIC e configurá-lo para o Skype**

1.  De um Servidor Front-End do Lync Server, abra o Shell de Gerenciamento do Lync Server.

2.  Execute estes dois comandos:
    
    `Remove-CsPublicProvider -Identity Messenger`
    
    `New-CsPublicProvider -Identity Skype -ProxyFqdn federation.messenger.msn.com -IconUrl "https://images.edge.messenger.live.com/Messenger_16x16.png" -VerificationLevel 2 -Enabled 1`

3.  De um cliente Lync, agora você pode selecionar Skype como provedor PIC e adicionar um cliente Skype ao especificar a conta da Microsoft deles. Além disso, um usuário do Skype que mesclou e entrou com uma conta da Microsoft pode enviar solciitação de contato a usuários do Lync. Para mais informações sobre contas da Microsoft, consulte [O que é uma conta da Microsoft?](https://support.skype.com/pt-br/faq/fa12059/what-is-a-microsoft-account). Para mais informações sobre como adicionar clientes ao Lync, consulte [Usando a conectividade Lync-Skype no Lync Server 2013 como usuário final](lync-server-2013-using-lync-skype-connectivity-as-an-end-user.md).
    
    ![Adicionar Contato do Skype](images/Dn440170.df0e6ed9-2374-4dfa-a815-87281989487c(OCS.15).jpg "Adicionar Contato do Skype")

4.  Para obter informações detalhadas sobre como modificar provedores hospedados, consulte "Criar ou editar provedores federados SIP hospedados" em [http://go.microsoft.com/fwlink/p/?LinkId=306065](http://go.microsoft.com/fwlink/p/?linkid=306065).

Isso conclui as tarefas administrativas que devem ser executadas no servidor. Agora você está pronto para a conectividade Lync-Skype.

