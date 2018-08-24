---
title: 'Lync Server 2013: Requisitos adicionais de software'
TOCTitle: Requisitos adicionais de software
ms:assetid: 87b318e3-03ae-41f7-af5e-29bb294f6af0
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398686(v=OCS.15)
ms:contentKeyID: 49307363
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Requisitos adicionais de software para Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

Além dos requisitos de hardware e sistema operacional para plataformas de servidor, o Lync Server 2013 requer a instalação de software adicional nos servidores implantados.

> [!NOTE]  
> Para obter detalhes sobre os requisitos de plataforma para os servidores executando Lync Server, consulte <a href="lync-server-2013-server-hardware-platforms.md">Plataformas de hardware de servidor para Lync Server 2013</a> e <a href="lync-server-2013-server-and-tools-operating-system-support.md">Suporte a sistemas operacionais de servidor e de ferramentas no Lync Server 2013</a>. Para obter detalhes sobre os requisitos de sistema para dispositivos e computadores de cliente, consulte <a href="lync-server-2013-planning-for-clients-and-devices.md">Planejando clientes e dispositivos no Lync Server 2013</a> na documentação de Planejamento. Para obter detalhes sobre os requisitos de software para ferramentas administrativas, consulte <a href="lync-server-2013-administrative-tools-software-requirements.md">Requisitos de software de ferramentas administrativas no Lync Server 2013</a>.

## Software adicional necessário para todas as funções de servidor interno

Esta seção lista o software necessário em todas as funções de servidores internos, que são todas as funções de servidores do Lync Server, exceto para Servidor de borda. Os requisitos para os Servidores de Borda e Pools de borda são listados posteriormente neste tópico em **Software adicional para servidores de borda**.

## Windows PowerShell 3.0

Todos os servidores em que o Lync Server 2013 é executado devem ter a versão correta do Windows PowerShell 3.0 instalada. Para obter detalhes, consulte [Instalando Windows PowerShell 3.0 para Lync Server 2013](lync-server-2013-installing-windows-powershell-3-0.md).

## Microsoft.NET Framework 4.5

O Lync Server requer o Microsoft .NET Framework 4.5 em todas as funções de servidor interno e em qualquer computador em que você executará as ferramentas administrativas do Lync Server ou Microsoft Lync Server 2013, Ferramenta de Planejamento. Para o Lync Server 2013, instale manualmente o Microsoft .NET Framework 4.5 de 64 bits no servidor antes de instalar o Lync Server 2013. Para instalá-lo manualmente, baixe o Microsoft .NET 4.5 Framework do Centro de Download da Microsoft em [http://go.microsoft.com/fwlink/p/?LinkId=268529](http://go.microsoft.com/fwlink/p/?linkid=268529)

## Instalando o Microsoft .NET Framework 4.5 em servidores que executam Windows Server 2012

Quando você instala o Microsoft .NET Framework 4.5 em servidores que executarão o Lync Server 2013 e o Windows Server 2012, você deve executar uma etapa adicional. Após a instalação do .NET Framework 4.5, use o Gerenciador de Servidores para instalar a ativação HTTP.

**Para instalar a ativação HTTP do .NET 4.5 no Windows Server 2012**

1.  No menu **Iniciar**, clique em **Programas**, **Ferramentas Administrativas** e **Gerenciador de Servidores**.

2.  No Gerenciador de Servidores, em **Resumo dos Recursos**, selecione **Adicionar Recursos**

3.  Expanda **.NET Framework 4.5**.

4.  Selecione a opção **Ativação de WCF** caso ainda não esteja selecionada. Em seguida, selecione **Ativação HTTP**.

5.  Clique em **Avançar** e siga os prompts para concluir a instalação.

## Windows Identity Foundation

**Windows Identity Foundation** no Lync Server 2013 requer a instalação do Windows Identity Foundation para suportar cenários de autenticação servidor a servidor. Windows Server 2008 R2 e Windows Server 2012 exigem procedimentos diferentes para instalação do Windows Identify Foundation. Selecione o sistema operacional do seu servidor a partir da lista a seguir:

  - Windows Server 2008 R2   Para Windows Server 2008 R2, verifique se ele já foi instalado em seu computador. Para fazer isso, vá até **Adicionar/Remover Programas**, **Exibir Atualizações Instaladas**, então em **Windows** procure pela entrada **Windows Identity Foundation (KB974405)**. Para obter detalhes sobre como instalar o Windows Identity Foundation, consulte [http://go.microsoft.com/fwlink/?linkid=204657\&clcid=0x416](http://go.microsoft.com/fwlink/?linkid=204657%26clcid=0x416).

  - Windows Server 2012   Para o Windows Server 2012, você usa o **Gerenciador de Servidores** para instalar o Windows Identity Foundation. No **Assistente Adicionar Funções e Recursos** do Gerenciador de Servidores, selecione **Recursos**. Selecione **Windows Identity Foundation 3.5** a partir da lista. Clique em **Avançar**, e depois em **Instalar**.

## Software adicional para servidores front-end e servidores Standard Edition

Todos os servidores front-end e Standard Edition também devem executar o IIS (Serviços de Informações da Internet) com determinados módulos. Além disso, todos os servidores front-end e Standard Edition em que é implantado o Aplicativo de Estacionamento de Chamada de conferência, comunicados ou grupos de resposta devem executar o Tempo de execução do Windows Media Format.

## IIS (Serviços de Informações da Internet)

Os Servidores Front-End e Standard Edition devem executar o IIS (Serviços de Informações da Internet), com os seguintes módulos:

  - Conteúdo estático

  - Documento padrão

  - Erros HTTP

  - ASP.NET

  - Extensibilidade .NET

  - Extensões Internet Server API (ISAPI)

  - Filtros ISAPI

  - Log HTTP

  - Ferramentas de log

  - Rastreamento

  - Autenticação do Windows

  - Requisição de filtro

  - Compressão de conteúdo estático

  - Compactação de conteúdo dinâmico

  - Console de gerenciamento IIS

  - Ferramentas e scripts de gerenciamento IIS

  - Autenticação anônima (instalada por padrão quando o IIS é instalado.)

  - Autenticação de mapeamento de certificado de cliente

## Tempo de Execução do Windows Media Format e Experiência Desktop do Windows

**Windows Desktop Experience** O Tempo de execução do Windows Media Format deve ser instalado em todos os servidores front-end e Standard Edition nos quais a conferência será implantada que, exceto no caso do Windows Server 2012, é instalada como parte da Experiência de desktop do Windows . O Windows Server 2012 requer o Microsoft Media Foundation. O Tempo de execução do Windows Media Format é necessário para executar arquivos Windows Media Audio (.wma) que os aplicativos de Estacionamento de Chamada, comunicados e grupos de resposta reproduzem para comunicados e músicas.

Recomendamos que você instale a Experiência de desktop do Windows antes de instalar o Lync Server 2013. Se o Lync Server 2013 não localizar o software no servidor, ele solicitará a instalação e será necessário reiniciar o servidor para concluí-la.

## Software adicional para servidores de borda e Standard Edition que executem o Windows Server 2012

O Servidores Front-End requer o .NET 3.5, que não está instalado por padrão no Windows Server 2012. Para instalá-lo, insira a mídia de instalação do Windows Server 2012 na unidade D e digite:

    Add-WindowsFeature RSAT-ADDS, Web-Server, Web-Static-Content, Web-Default-Doc, Web-Http-Errors, Web-Asp-Net, Web-Net-Ext, Web-ISAPI-Ext, Web-ISAPI-Filter, Web-Http-Logging, Web-Log-Libraries, Web-Request-Monitor, Web-Http-Tracing, Web-Basic-Auth, Web-Windows-Auth, Web-Client-Auth, Web-Filtering, Web-Stat-Compression, Web-Dyn-Compression, NET-WCF-HTTP-Activation45, Web-Asp-Net45, Web-Mgmt-Tools, Web-Scripting-Tools, Web-Mgmt-Compat, Desktop-Experience, Telnet-Client, BITS -Source D:\sources\sxs

Para obter detalhes sobre a instalação do .NET 3.5 em servidores que executam o Windows Server 2012, consulte "Considerações de implantação do Microsoft .NET Framework 3.5" em <http://go.microsoft.com/fwlink/p/?linkid=275032>.

## Software adicional para Diretores

Os Diretores devem executar o IIS (Serviços de Informações da Internet) com os seguintes módulos:

  - Conteúdo estático

  - Documento padrão

  - Erros HTTP

  - ASP.NET

  - Extensibilidade .NET

  - Extensões Internet Server API (ISAPI)

  - Filtros ISAPI

  - Log HTTP

  - Ferramentas de log

  - Rastreamento

  - Autenticação do Windows

  - Requisição de filtro

  - Compressão de conteúdo estático

  - Console de gerenciamento IIS

  - Ferramentas e scripts de gerenciamento IIS

  - Autenticação anônima (Isto é instalado por padrão quando o IIS é instalado.)

  - Autenticação de mapeamento de certificado de cliente

## Software adicional para servidores front-end de chat persistente

Os servidores front-end de chat persistente devem executar o Enfileiramento de mensagens (também conhecido como MSMQ), que é um componente do Windows Server.

Para obter informações sobre habilitação do MSMQ, [clique aqui.](http://technet.microsoft.com/en-us/library/cc771474.aspx)

## Software adicional para servidores de borda

O Servidores de Borda requer o software a seguir:

  - Todos os servidores em que o Lync Server 2013 é executado devem ter a versão correta do Windows PowerShell 3.0 instalada. Para obter detalhes, consulte [Instalando Windows PowerShell 3.0 para Lync Server 2013](lync-server-2013-installing-windows-powershell-3-0.md).

  - O Lync Server requer o Microsoft .NET Framework 4.5. Para Lync Server 2013 instalado no Windows Server 2008 R2, instale manualmente a edição de 64 bits do Microsoft .NET Framework 4.5 no servidor antes de instalar o Lync Server 2013. Para instalá-lo manualmente, baixe o Microsoft .NET 4.5 Framework no Centro de Download da Microsoft em [http://go.microsoft.com/fwlink/p/?LinkId=268529](http://go.microsoft.com/fwlink/p/?linkid=268529)

  - **Windows Identity Foundation** no Lync Server 2013 requer a instalação do Windows Identity Foundation para suportar cenários de autenticação servidor a servidor. Windows Server 2008 R2 e Windows Server 2012 exigem procedimentos diferentes para instalação do Windows Identify Foundation. Selecione o sistema operacional do seu servidor a partir da lista a seguir:
    
      - Windows Server 2008 R2   Para Windows Server 2008 R2, verifique se ele já foi instalado em seu computador. Para fazer isso, vá até **Adicionar/Remover Programas**, **Exibir Atualizações Instaladas**, então em **Windows** procure pela entrada **Windows Identity Foundation (KB974405)**. Para obter detalhes sobre como instalar o Windows Identity Foundation, consulte [http://go.microsoft.com/fwlink/?linkid=204657\&clcid=0x416](http://go.microsoft.com/fwlink/?linkid=204657%26clcid=0x416).
    
      - Windows Server 2012   Para o Windows Server 2012, você usa o **Gerenciador de Servidores** para instalar o Windows Identity Foundation. No **Assistente Adicionar Funções e Recursos** do Gerenciador de Servidores, selecione **Recursos**. Selecione **Windows Identity Foundation 3.5** a partir da lista. Clique em **Avançar**, e depois em **Instalar**.

## Não instale Provedores de soquete em camada em Servidores de Mídia

Não instale nenhum software cliente do Microsoft Internet Security and Acceleration (ISA) Server ou qualquer outro software de LSP (provedor de serviço em camadas Winsock) em quaisquer servidores front-end ou de mediação independentes. A instalação desse software pode resultar em desempenho ruim do tráfego de mídia.

## Consulte Também

#### Conceitos

[Requisitos de software de ferramentas administrativas no Lync Server 2013](lync-server-2013-administrative-tools-software-requirements.md)

