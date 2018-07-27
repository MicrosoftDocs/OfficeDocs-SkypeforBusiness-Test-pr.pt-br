---
title: 'Lync Server 2013: Instalar sistemas operacionais e software de pré-requisito nos servidores'
TOCTitle: Instalar sistemas operacionais e software de pré-requisito nos servidores
ms:assetid: 055991e0-5aeb-43fc-a7ba-d4b02316d73b
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398103(v=OCS.15)
ms:contentKeyID: 49305733
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Instalar sistemas operacionais e software de pré-requisito nos servidores para Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

Após configurar a infraestrutura de hardware e software, você precisará instalar os sistemas operacionais e as atualizações adequadas do Windows, além de todos os outros softwares de pré-requisito em cada servidor que está implantando. Isso inclui cada função de servidor do Lync Server 2013 e todos os servidores de infraestrutura adicionais e servidores baseados no SQL Server necessários para sua implantação.

> [!NOTE]  
> Esta seção descreve a instalação de sistemas operacional e software de pré-requisito para servidores internos. Se os Servidores de Borda estiverem sendo implementados para dar suporte ao acesso de usuário externo, também será preciso instalar sistemas operacionais e software de pré-requisito para esses servidores, incluindo Servidores de Borda e servidores de proxy reverso. Para obter mais detalhes sobre como preparar os servidores para darem suporte ao acesso de usuário externo, consulte <a href="lync-server-2013-preparing-for-installation-of-servers-in-the-perimeter-network.md">Preparando para instalação de servidores na rede de perímetro para Lync Server 2013</a> na documentação da Implementação.

## Como instalar os sistemas operacionais Windows em servidores

Em cada servidor que estiver sendo implantado, instale o sistema operacional Windows apropriado da seguinte maneira:

  - **Servidores executando o Lync Server 2013**   Para obter detalhes sobre os requisitos do sistema operacional para servidores executando o Lync Server 2013, consulte [Suporte a sistemas operacionais de servidor e de ferramentas no Lync Server 2013](lync-server-2013-server-and-tools-operating-system-support.md) na documentação de Suporte.

  - **Servidores de banco de dados**   Para obter detalhes sobre os requisitos de sistema operacional para servidores de banco de dados, incluindo o banco de dados back-end, o Banco de dados de arquivamento e o Banco de dados de monitoramento, consulte a documentação do SQL Server. Para SQL Server 2012, consulte o SQL Server 2012 Books Online em [http://go.microsoft.com/fwlink/?linkid=218015\&clcid=0x416](http://go.microsoft.com/fwlink/?linkid=218015%26clcid=0x416).

> [!NOTE]  
> Se você estiver instalando o Lync Server 2013 no Windows Server 2008 R2 com SP1, será necessário instalar primeiro a atualização descrita no artigo 2646886 da Base de Dados de Conhecimento da Microsoft, “CORREÇÃO: A corrupção de heap ocorre quando um módulo chama o método InsertEntityBody em IIS 7.5” em <a href="http://go.microsoft.com/fwlink/?linkid=3052%26clcid=0x416" class="uri">http://go.microsoft.com/fwlink/?linkid=3052&amp;clcid=0x416</a>.<br />Também é necessário modificar o registro conforme descrito no artigo da KB, <a href="http://go.microsoft.com/fwlink/p/?linkid=506893">IDs de Evento 32402, 61045 estão registradas nos servidores Front-End do Lync Server 2013 instalados no Windows Server 2012 R2</a>.

## Instalar o Windows Update em servidores

Instale as seguintes atualizações do Windows Update em cada servidor:

  - **Windows Update para execução de servidores Lync Server 2013**   Para obter informações sobre as atualizações em Windows Update que são necessárias para a a execução dos servidores Lync Server 2013, consulte [Requisitos adicionais de software para Lync Server 2013](lync-server-2013-additional-software-requirements.md) na documentação do Planejamento.

  - **Servidores de banco de dados**   Para obter detalhes sobre as atualizações do Windows Update necessárias para servidores de banco de dados, incluindo o banco de dados back-end, o Banco de dados de arquivamento e o Banco de dados de monitoramento, consulte a documentação do SQL Server 2012. Para o SQL Server 2012, consulte o SQL Server 2012 Books Online em [http://go.microsoft.com/fwlink/?linkid=218015\&clcid=0x416](http://go.microsoft.com/fwlink/?linkid=218015%26clcid=0x416).

## Como instalar outros pré-requisitos de softwares em servidores

O Lync Server 2013 exige a instalação dos seguintes softwares adicionais em servidores:

  - **Software de pré-requisito para execução de servidores Lync Server 2013**   Os pré-requisitos de software adicionais para a execução dos servidores Lync Server 2013 dependem da função do servidor sendo implantado. Para obter informações sobre os requisitos específicos do software para cada servidor, consulte [Requisitos adicionais de software para Lync Server 2013](lync-server-2013-additional-software-requirements.md) na documentação do Planejamento.

  - **Windows Identity Foundation**   O Lync Server 2013 exige a instalação do Windows Identity Foundation para suportar os cenários de autenticação servidor para servidor. Para verificar se ele já está instalado em seu computador, vá até Painel de Controle, clique em **Programas e Recursos**, **Exibir atualizações instaladas** e procure em **Microsoft Windows**. Para obter detalhes sobre como instalar o Windows Identity Foundation, consulte [http://go.microsoft.com/fwlink/?linkid=204657\&clcid=0x416](http://go.microsoft.com/fwlink/?linkid=204657%26clcid=0x416).

  - **Microsoft .NET Framework 4.5**   A edição de 64 bits do Microsoft .NET Framework 4.5 é necessária para Lync Server 2013.

  - **Pré-requisito de software para servidores de banco de dados** Para obter mais detalhes sobre o Windows Update requerido por servidores de bando de dados, incluindo os banco de dados de back-end, o Banco de dados de arquivamento e o Banco de dados de monitoramento, consulte a documentação do SQL Server 2012 em [http://go.microsoft.com/fwlink/?linkid=218015\&clcid=0x416](http://go.microsoft.com/fwlink/?linkid=218015%26clcid=0x416).
    
    > [!NOTE]  
    > O Lync Server 2013 instala automaticamente o Microsoft SQL Server 2012 Express em cada Servidor Standard Edition e em cada servidor executando o Lync Server 2013 no qual o repositório de configuração local está localizado.

  - **Tempo de execução do Windows Media Format**   Todos os Servidores Front-End e Servidores Standard Edition nos quais a conferência será implantada precisam ter o Tempo de execução do Windows Media Format instalado. O Tempo de execução do Windows Media Format é necessário para executar arquivos de Windows Media Audio (.wma) que os aplicativos de Estacionamento de chamada, Anúncio e Grupo de resposta reproduzem para anúncios e música.
    
    > [!NOTE]  
    > Para Windows Server 2012 e Windows Server 2012 R2, o Tempo de Execução do Windows Media Format é instalado com o Microsoft Media Foundation.    
    > [!NOTE]  
    > Para Windows Server 2008 e Windows Server 2008 R2, o Tempo de execução do Windows Media Format é instalado como parte da Experiência de Desktop do Windows. Recomenda-se instalar a Experiência de Desktop do Windows antes da instalação de Lync Server 2013. Se Lync Server 2013 não encontrar esse software no servidor, será solicitada sua instalação, a qual só será concluída quando o servidor for reiniciado.
