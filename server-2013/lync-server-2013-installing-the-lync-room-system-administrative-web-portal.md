---
title: Instalando o Portal Administrativo da Web do Lync Room System
TOCTitle: Instalando o Portal Administrativo da Web do Lync Room System
ms:assetid: dd19e368-c338-4e21-a40d-6439d46a9748
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn436326(v=OCS.15)
ms:contentKeyID: 59602789
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Instalando o Portal Administrativo da Web do Lync Room System

 

_**Tópico modificado em:** 2016-12-08_

Você pode fazer o download do Portal Web administrativo do Microsoft Lync Room System no Centro de Download da Microsoft em [http://go.microsoft.com/fwlink/p/?LinkId=324044](http://go.microsoft.com/fwlink/p/?linkid=324044).

Para instalar o Portal Web administrativo do Lync Room System, use as etapas a seguir.

1.  Configure a Porta de aplicativos confiáveis executando o seguinte cmdlet em Shell de Gerenciamento do Lync Server:
    
        Set-CsWebServer -Identity POOLFQDN -MeetingRoomAdminPortalInternalListeningPort 4456 -MeetingRoomAdminPortalExternalListeningPort 4457

2.  Para instalar o Portal da sala de reunião, faça o download de **LyncRoomAdminPortal.exe**, então, execute-o como administrador.

3.  Abra o arquivo Web.config no seguinte local:
    
    %Program Files%\\Microsoft Lync Server 2013\\Web Components\\Meeting Room Portal\\Int\\Handler\\

4.  No arquivo Web.Config, mude PortalUserName para o nome de usuário criado na Etapa 2 na seção “Configurando pré-requisigos para o Portal Lync Room System Admin” (o nome recomendado na etapa é LRSApp):
    
        <add key="PortalUserName" value="sip:LRSApp@domain.com" />

5.  Como o Portal LRS Admin Portal é um aplicativo confiável, você não precisa forencer a senha na configuração do portal. Se o usuário estiver usando um registrador diferente do registrador local, você precisará especificar o registrador para ele adicionando a seguinte linha no arquivo Web.Config:
    
        <add key="PortalUserRegistrarFQDN" value="pool-xxxx.domain.com" />

6.  Se a porta usada for diferente de   5061, adicione a seguinte linha no arquivo Web.Config:
    
        <add key="PortalUserRegistrarPort" value="5061" />

## Verificando a instalação do Portal Web administrativo do Lync Room System

Para verificar a instalação do Portal Web administrativo do Lync Room System, faça o seguinte:


1.  Em um servidor front-end, vá para a seguinte URL:
    
    https://\<fe-server\>/lrs
    
    Você não deverá ver nenhum erro, como mostrado na imagem a seguir:
    
    ![Tela de entrada no portal admin do sistema Lync Room](images/Dn436326.050bcf70-2f3b-46b2-9b96-ebd12679b713(OCS.15).png "Tela de entrada no portal admin do sistema Lync Room")

2.  Se você não vir nenhum erro, tente acessar a seguinte URL a partir de qualquer computador na topologia:
    
    https://\<fe-server\>/lrs
    
    Para acessar a página, você precisará adicionar os registros DNS, como descrito em “Registros DNS requeridos para a entrada automática do cliente” em [http://go.microsoft.com/fwlink/p/?LinkId=318056](http://go.microsoft.com/fwlink/p/?linkid=318056).

