---
title: "Lync Server 2013: Ferram. de gerenc. do Windows PowerShell e do Lync Server"
TOCTitle: Ferramentas de gerenciamento do Windows PowerShell e do Lync Server 2013
ms:assetid: 6a285f7c-0ef5-4cab-9976-d03be276e35d
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn481130(v=OCS.15)
ms:contentKeyID: 59679345
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Ferramentas de gerenciamento do Windows PowerShell e do Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

No Microsoft Lync Server 2013, as ferramentas de gestão são implementadas usando Windows PowerShell. O Windows PowerShell inclui um ambiente de linha de comando, comandos específicos dos produtos e uma linguagem de script completa. As ferramentas do Lync Server 2013 que são implementadas usando o Windows PowerShell incluem:

  - **Construtor de Topologias**.Você pode utilizar o Construtor de Topologias para criar, ajustar e publicar sua topologia planejada, sendo que ele também valida sua topologia antes de iniciar as instalações de servidor. Ao instalar o Lync Server 2013 em servidores individuais, os servidores leem a topologia publicada como parte do processo de instalação, e o programa de instalação implanta o servidor conforme indicado na topologia. Depois da configuração, as informações de configuração são automaticamente replicadas a todos os servidores. Os componentes podem ser adicionados à sua implantação apenas usando o Construtor de Topologias.

  - **Shell de Gerenciamento do Lync Server**. Você pode utilizar o Shell de Gerenciamento do Lync Server para gerenciamento completo de linha de comando de sua implantação.

  - **Painel de Controle do Lync Server**. Você pode utilizar a interface de usuário do Painel de Controle do Microsoft Lync Server 2013 para gerenciar as tarefas mais comuns em sua implantação.

Essas ferramentas usam cmdlets do Windows PowerShell para gerenciamento de sua implantação, incluindo cerca de 550 cmdlets específicos de produtos. Os cmdlets de segurança incluídos no Lync Server 2013 são principalemente utilizados para gerenciar a autenticação e os direitos e permissões de usuário. Uma grande variedade de cmdlets está disponível para autenticação, incluindo cmdlets para autenticação de certificados e do número de identificação pessoal (PIN). Além disso, vários cmdlets permitem que você utilize o novo recurso de Controle de acesso baseado em função (RBAC) para delegar o controle administrativo do Lync Server 2013. Para obter mais detalhes sobre os cmdlets do Lync Server, consulte [Shell de gerenciamento do Lync Server](lync-server-2013-lync-server-management-shell.md) na Documentação da operação. Para obter mais detalhes sobre como usar o Construtor de Topologias e o Painel de Controle do Lync Server 2013 para gerenciar sua implantação, consulte [Painel de Controle do Lync Server 2013](https://technet.microsoft.com/pt-br/library/gg133224\(v=ocs.15\)) na Documentação da operação.

Os recursos de segurança de script para Windows PowerShell são designados especificamente para impedir alguns problemas de segurança relacionados a script de tecnologias mais antigas, incluindo o Microsoft Visual Basic Scripting Edition (VBScript). Os recursos de segurança do Windows PowerShell visam criar um ambiente em que os usuários não possam executar scripts fácil ou inconscientemente. Por padrão, os recursos de segurança do Windows PowerShell estão habilitados. Você pode modificar o estado desses recursos para adequá-los à sua necessidade de script e vários objetivos de segurança. Isso não quer dizer que o shell impossibilite os usuários de executar scripts. Em vez disso, o shell dificulta, por padrão, que os usuários executem scripts sem perceber. Para obter mais detalhes, consulte Segurança de Scripts do Windows PowerShell em [http://go.microsoft.com/fwlink/p/?LinkId=213145](http://go.microsoft.com/fwlink/p/?linkid=213145).

