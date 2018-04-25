---
title: Modificar configurações de Web Service existentes
TOCTitle: Modificar configurações de Web Service existentes
ms:assetid: bd9c7aa5-d31c-4fab-b31d-8baae26b1296
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg182580(v=OCS.15)
ms:contentKeyID: 49307973
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Modificar configurações de Web Service existentes

 

_**Tópico modificado em:** 2012-11-01_

É possível usar a página **Serviço Web** para configurar os métodos de autenticação para acessar os servidores e serviços Web relacionados ao Lync Server 2013.

Execute estas etapas para modificar uma política de Serviço Web existente.

## Para modificar um Serviço Web existente

1.  Usando uma conta de usuário que é membro do grupo RTCUniversalServerAdmins (ou tem direitos de usuário equivalentes), ou está atribuída à função CsServerAdministrator ou CsAdministrator, faça logon em qualquer computador que está na rede na qual você implantou o Lync Server 2013.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerda, clique em **Segurança** e em **Serviço Web**.

4.  Na página **Serviço Web**, clique em uma configuração, em **Editar** e clique em **Mostrar detalhes**.

5.  Em **Editar Configuração do Serviço Web**, em **Autenticação do Windows Integrada**, selecione **Negociar**, **NTLM** ou **Nenhum**.

6.  Selecione uma ou mais das seguintes opções, dependendo dos recursos dos clientes do e suporte em seu ambiente:
    
      - **Habilitar Autenticação de PIN** para permitir que os clientes sejam autenticados usando números PIN.
    
      - **Habilitar autenticação de certificado** para que os servidores no pool emitam certificados aos clientes.
    
      - **Habilitar download da cadeia de certificados** para que os servidores com um certificado de autenticação baixem a cadeia de certificados para esse certificado.

7.  Clique em **Confirmar**.

## Consulte Também

#### Outros Recursos

[Configurando a segurança no Lync Server 2013](lync-server-2013-configuring-authentication-in-the-lync-server-control-panel.md)

