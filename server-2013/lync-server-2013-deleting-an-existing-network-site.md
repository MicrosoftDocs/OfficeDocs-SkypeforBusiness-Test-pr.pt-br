---
title: Excluir um site de rede existente
TOCTitle: Excluir um site de rede existente
ms:assetid: 2762149b-3572-4513-b838-beda7fa9e81e
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ688001(v=OCS.15)
ms:contentKeyID: 49886145
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Excluir um site de rede existente

 

_**Tópico modificado em:** 2012-11-01_

Sites de rede são escritórios ou locais configurados dentro de cada região de um controle de admissão de chamada (CAC) ou implantação de 9-1-1 Avançado. É possível usar o Painel de Controle do Lync Server 2013 para configurar locais e associá-los com regiões. Por exemplo, uma região de rede para América do Norte pode ser associada com locais de rede como Chicago, Redmond e Vancouver. Um local de rede CAC deve ser criado para cada local dentro de uma organização, mesmo se este local não possui limitações de largura de banda. Do Painel de Controle do Lync Server é possível criar, modificar e excluir locais de rede. Use o seguinte procedimento para excluir um local de rede existente. Para obter detalhes sobre a criação ou modificação de locais de rede, consulte [Criar ou modificar sites de rede](lync-server-2013-creating-or-modifying-network-sites.md)

## Para excluir um local de rede

1.  Usando uma conta de usuário que é membro do grupo RTCUniversalServerAdmins (ou tem direitos de usuário equivalentes), ou está atribuída à função CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerda, clique em **Configuração de rede** e em **Local**.

4.  Na página **Local**, clique no local que deseja excluir.
    
    > [!NOTE]  
    > Você pode excluir mais de um local de cada vez. Para fazer isso, pressione CTRL e selecione diversos locais mantendo a tecla pressionada. Ou então, para selecionar todos os locais, clique em <strong>Selecionar Tudo</strong> no menu <strong>Editar</strong>.

5.  No menu **Editar**, clique em **Excluir**.

6.  Clique em **OK**.
    

    > [!WARNING]
    > Você não poderá remover um local de rede se ele estiver associado a uma sub-rede. Se você tentar fazer isso, receberá uma mensagem de erro. Para ver se o local está associado a alguma sub-rede, clique no local e em <STRONG>Mostrar detalhes</STRONG> no menu <STRONG>Editar</STRONG>.


