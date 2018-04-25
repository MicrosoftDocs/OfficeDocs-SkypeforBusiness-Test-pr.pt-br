---
title: Verificar coexistência de pool piloto com o pool herdado
TOCTitle: Verificar coexistência de pool piloto com o pool herdado
ms:assetid: 597d0fa6-ca04-4521-b1c2-72d7f35ecd08
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204914(v=OCS.15)
ms:contentKeyID: 49306798
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Verificar coexistência de pool piloto com o pool herdado

 

_**Tópico modificado em:** 2012-09-28_

## Verifique o pool na ferramenta administrativa do Office Communications Server 2007 R2

1.  Abra a ferramenta administrativa do Office Communications Server 2007 R2.

2.  Expanda o nó **Floresta**, expanda o nó dos pools dos **Servidores Standard Edition** ou **Enterprise** e expanda o pool ou o nome do servidor.

3.  Certifique-se de que os serviços do Office Communications Server 2007 R2 estejam em execução no pool.
    
    ![Console administrativo do Office Communications Server 2007 R2](images/JJ204914.76897b6d-f433-47d2-930d-0816fc30a3c2(OCS.15).jpg "Console administrativo do Office Communications Server 2007 R2")  

## Verifique o pool piloto no Painel de Controle do Lync Server 2013

1.  A partir de uma conta de usuário que seja membro da função CsAdministrator, faça logon no servidor front-end do Lync Server 2013.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Clique em **Topologia** .

4.  Verifique se os servidores implantados estão presentes no seu pool piloto.
    
    ![Página de Topologia do Painel de Controle do Lync Server](images/JJ204914.a3d1ba5f-c1a7-45e8-b9a5-7cb07b01af8c(OCS.15).jpg "Página de Topologia do Painel de Controle do Lync Server")  

## Verifique se os serviços do Lync Server 2013 foram iniciados

1.  No servidor front-end do Lync Server 2013, abra o miniaplicativo **Serviços** a partir do grupo **Ferramentas Administrativas** .

2.  Verifique se os serviços relacionados coincidem com a lista na figura a seguir.
    
    ![Página Serviços que mostra os serviços iniciados do Lync](images/JJ204914.fd35d54a-2ab6-4c09-b5e9-fd5bf10f6f51(OCS.15).jpg "Página Serviços que mostra os serviços iniciados do Lync")

