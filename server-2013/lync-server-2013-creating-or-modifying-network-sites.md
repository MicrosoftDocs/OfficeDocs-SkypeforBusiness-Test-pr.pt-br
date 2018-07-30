---
title: Criar ou modificar sites de rede
TOCTitle: Criar ou modificar sites de rede
ms:assetid: 358aa08a-c5bc-45fc-8017-19e6202f88c5
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg520975(v=OCS.15)
ms:contentKeyID: 49306348
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Criar ou modificar sites de rede

 

_**Tópico modificado em:** 2012-10-08_

Sites da rede são os escritórios ou locais configurados em cada região de um CAC (controle de admissão de chamadas) ou implantação do 9-1-1 Avançado. É possível usar o Painel de Controle do Microsoft Lync Server 2013 para configurar sites e associá-los a regiões. Por exemplo, uma região de rede da América do Norte pode ser associada a sites da rede, como Chicago, Redmond e Vancouver. Um site da rede do CAC deve ser criado para cada site da organização, mesmo que esse site não tenha limitações de largura de banda. No Painel de Controle do Lync Server, é possível criar, modificar e excluir sites da rede. Use os procedimentos a seguir para criar ou modificar um site da rede. Para obter detalhes sobre a exclusão de um site da rede existente, consulte [Excluir um site de rede existente](lync-server-2013-deleting-an-existing-network-site.md).

## Para criar um local de rede

1.  Usando uma conta de usuário que é membro do grupo RTCUniversalServerAdmins (ou tem direitos de usuário equivalentes), ou está atribuída à função CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerda, clique em **Configuração da Rede** e em **Local**.

4.  Na página **Local**, clique em **Novo**.

5.  Em **Novo Local**, digite um nome para este local no campo **Nome**.
    
    > [!NOTE]  
    > Os nomes de locais devem ser exclusivos dentro da implantação do Lync Server 2013.

6.  Na lista suspensa **Região**, selecione uma região da rede para associar a este local.

7.  (Opcional) Se deseja impor limitações de largura de banda em chamadas de áudio ou vídeo para este local, selecione o perfil da política da largura de banda com as configurações apropriadas na lista suspensa **Política da largura de banda**.
    
    > [!NOTE]  
    > Você pode ver os detalhes dos perfis disponíveis da política de largura de banda, ou criar um novo perfil, na página <strong>Perfil de Política</strong> do grupo <strong>Configuração de Rede</strong>. Para obter os detalhes, consulte <a href="lync-server-2013-creating-or-modifying-bandwidth-policy-profiles.md">Criar ou modificar perfis da política de largura de banda</a>.

8.  (Opcional) Se deseja fornecer configurações de localização para esse local, selecione uma política de localização na lista suspensa **Política de localização**.
    
    > [!NOTE]  
    > A política de localização atribui configurações específicas de 9-1-1 Aprimorado (E9-1-1) e de localização do cliente ao local. Você pode ver os detalhes das políticas de localização disponíveis ou criar uma política nova na página <strong>Política de localização</strong> do grupo <strong>Configuração de Rede</strong>. Para obter os detalhes, consulte <a href="lync-server-2013-viewing-location-policy-information.md">Visualizando informações de política de local</a>.

9.  (Opcional) Digite um valor no campo **Descrição** para fornecer mais informações sobre esse local, que não podem ser expressadas apenas pelo nome.

10. Clique em **Comprometer**.
    
    > [!NOTE]  
    > Você não usa a tabela <strong>Sub-redes Associadas</strong> ao criar um novo local de rede. Você associa a sub-rede ao local quando criá-la ou modificá-la. Para obter os detalhes, consulte <a href="lync-server-2013-create-or-modify-network-subnets.md">Criar ou modificar subredes</a>.

## Para modificar um local de rede

1.  Usando uma conta de usuário que é membro do grupo RTCUniversalServerAdmins (ou tem direitos de usuário equivalentes), ou está atribuída à função CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerda, clique em **Configuração da Rede** e em **Local**.

4.  Na página **Local**, clique no local que deseja modificar.

5.  No painel **Ações**, clique em **Mostrar detalhes**.

6.  Na página **Editar Local**, você pode modificar a descrição, região, perfil da política da largura de banda e política de localização associados ao novo local. Para obter os detalhes, consulte a seção "Para criar um local de rede" anteriormente neste tópico.

7.  Clique em **Comprometer**.

Você não pode modificar a tabela **Sub-redes Associadas** nesta página. A lista de sub-redes associadas é fornecida para referência, para que você saiba quais sub-redes serão afetadas quando você modificar as configurações do local.

## Para excluir um local de rede

1.  Usando uma conta de usuário que é membro do grupo RTCUniversalServerAdmins (ou tem direitos de usuário equivalentes), ou está atribuída à função CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerda, clique em **Configuração da Rede** e em **Local**.

4.  Na página **Local**, clique no local que deseja excluir.
    
    > [!NOTE]  
    > Você pode excluir mais de um local de cada vez. Para fazer isso, pressione CTRL e selecione diversos locais mantendo a tecla pressionada. Ou então, para selecionar todos os locais, clique em <strong>Selecionar Tudo</strong> no menu <strong>Editar</strong>.

5.  No menu **Editar**, clique em **Excluir**.

6.  Clique em **OK**.
    

    > [!WARNING]
    > Você não poderá remover um local de rede se ele estiver associado a uma sub-rede. Se você tentar fazer isso, receberá uma mensagem de erro. Para ver se o local está associado a alguma sub-rede, clique no local e em <STRONG>Mostrar detalhes</STRONG> no menu <STRONG>Editar</STRONG>.



## Consulte Também

#### Tarefas

[Excluir um site de rede existente](lync-server-2013-deleting-an-existing-network-site.md)  

#### Outros Recursos

[New-CsNetworkSite](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsNetworkSite)  
[Set-CsNetworkSite](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsNetworkSite)  
[Remove-CsNetworkSite](https://docs.microsoft.com/en-us/powershell/module/skype/Remove-CsNetworkSite)  
[Get-CsNetworkSite](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsNetworkSite)

