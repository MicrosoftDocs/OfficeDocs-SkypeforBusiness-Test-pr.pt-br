---
title: Implantando clientes Lync no Lync Server 2013
TOCTitle: Implantando clientes Lync no Lync Server 2013
ms:assetid: 3d10abf2-d484-4fa0-8f10-4a5f9dfba4f5
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204827(v=OCS.15)
ms:contentKeyID: 49306456
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Implantando clientes Lync no Lync Server 2013

 

_**Tópico modificado em:** 2012-10-03_

Lync 2013 introduz uma abordagem diferente para a implantação de cliente.introduces Em uma partida de versões anteriores, Lync 2013 não mais possui um instalador próprio. Em vez disso, o Lync está incluído no programa de instalação do Office 2013. Para implantar o Lync 2013 nos seus usuários, você pode utilizar métodos de instalação do Office 2013 e ferramentas de personalização.

  - **Office 2013 Windows Installer** é um pacote de instalação com base Windows que consiste em vários arquivos MSI. Um pacote de núcleo MSI de linguagem neutra é combinado com um ou mais pacotes de linguagem específica para fazer um produto completo. A instalação reúne os pacotes individuais e efetua a personalização e tarefas de manutenção durante e após a instalação do Office nos computadores dos usuários. Os tópicos nesta seção descrevem como utilizar e personalizar o Office 2013 Windows Installer para implantar Lync 2013.

  - **Office 2013 Clique para Executar** é um programa de instalação que guia os arquivos de instalação do Office para o usuário a partir do portal Microsoft Office 365. Os administradores podem personalizar a instalação utilizando a Ferramenta de Implantação do Office para Clique para Executar. Por o Office 2013 Clique para Executar ser primariamente utilizado no ambiente Microsoft Office 365, este método de instalação não é descrito em detalhes nessa seção. Informações detalhadas sobre como utilizar e personalizar a instalação Clique para Executar está disponível na documentação do Kit de Recursos do Office 2013. Os administradores também podem baixar o programa Clique para Executar Office 2013 e os arquivos fonte de linguagem para uma área local, o que é útil quando você deseja minimizar a demanda na rede ou evitar que os usuários instalem software da internet devido a requisitos de segurança corporativos.

Os tópicos nessa seção focam em como implantar clientes utilizando o instalador com base MSI Office 2013. Sua referência primária deve ser a documentação do Kit de Recursos do Office 2013, que descreve em detalhes como preparar sua infraestrutura, personalizar a instalação e implantar o Office 2013. Entretanto, você deve utilziar a documentação do Office em conjunto com os tópicos nesta seção, que apontam considerações de implantação específicas para o Lync 2013.

> [!NOTE]  
> <ul>
> 
> <li><p>O Suplemento de Reunião Online para Lync 2013, que suporta o gerenciamento de reuniões de dentro do cliente de colaboração e mensagem do Outlook, é instalado automaticamente com Lync 2013.</p></li>
> 
> 
> <li><p>O programa de instalação Office 2013 não desinstala versões anteriores do Lync ou Office Communicator. O cliente Lync 2013 instala lado a lado com outros clientes Lync ou Office Communicator</p></li></ul>


## Nesta seção

  - [Personalizando a instalação do cliente](lync-server-2013-customizing-client-installation.md)

  - [Personalizando o Comportamento do Lync e a Interface de Usuário](lync-server-2013-customizing-lync-behavior-and-the-user-interface.md)

  - [Personalizando o suplemento Online Meeting no Lync Server 2013](lync-server-2013-customizing-the-online-meeting-add-in.md)

  - [Configurando a página de ingresso na reunião no Lync Server 2013](lync-server-2013-configuring-the-meeting-join-page.md)

  - [Configurando versões de cliente suportadas](lync-server-2013-configuring-supported-client-versions.md)

  - [Configurando o modo de privacidade de presença avançada](lync-server-2013-configuring-enhanced-presence-privacy-mode.md)

