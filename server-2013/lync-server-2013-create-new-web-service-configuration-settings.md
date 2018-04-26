---
title: Criar novas configurações de Web Service
TOCTitle: Criar novas configurações de Web Service
ms:assetid: f3f04d81-8a1f-427f-bd0f-fb659024e096
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg182605(v=OCS.15)
ms:contentKeyID: 49308587
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Criar novas configurações de Web Service

 

_**Tópico modificado em:** 2012-11-01_

É possível usar a página **Web Services** para configurar os métodos de autenticação para acessar os servidores da Web e Web Services relacionados ao Lync Server 2013.

Siga estas etapas para criar a nova política de Web Service.

## Para criar uma política de Web Service

1.  Usando uma conta de usuário que é membro do grupo RTCUniversalServerAdmins (ou tem direitos de usuário equivalentes), ou está atribuída à função CsServerAdministrator ou CsAdministrator, faça logon em qualquer computador que está na rede na qual você implantou o Lync Server 2013.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerda, clique em **Segurança** e em **Web Service**.

4.  Na página **Web Service**, clique em **Novo** e faça um dos seguintes:
    
      - Para configurar o Web Service para um site, clique em **Configuração do site**. Em **Selecionar um site**, clique em um site no qual a política de Web Service será aplicada e clique em **OK**.
    
      - Para configurar o Web Service para um pool, clique em **Configuração do pool**. Em **Selecionar um serviço**, clique no serviço no qual a política de Web Service será aplicada e clique em **OK**.

5.  Em **Nova configuração do Web Service**, em **Autenticação integrada do Windows**, selecione **Negociar**, **Autenticação integrada do Windows** ou **Nenhum**.

6.  Selecione um ou mais dos seguintes dependendo das capacidades dos clientes e do suporte no seu ambiente:
    
      - **Habilitar autenticação de PIN** para habilitar os clientes a autenticarem usando números PIN.
    
      - **Habilitar autenticação de certificado** para que os servidores no pool emitam certificados para os clientes.
    
      - **Habilitar download da cadeia de certificados** para que os servidores sejam apresentados com um download de certificado de autenticação da cadeia de certificados para aquele certificado.

7.  Clique em **Confirmar**.

