---
title: Requisitos de webconferência no Lync Server 2013
TOCTitle: Requisitos de webconferência no Lync Server 2013
ms:assetid: 125f847c-58ab-450f-ae43-41219fd38477
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ619171(v=OCS.15)
ms:contentKeyID: 49305939
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Requisitos de webconferência no Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

Se você optou por habilitar a webconferência, será necessário planejar:

   O acesso ao repositório de arquivos, usado para armazenar conteúdo de webconferências.

   A integração com o Servidor Office Web Apps, necessária para compartilhar arquivos do PowerPoint durante uma conferência.

## Repositório de Arquivos

O serviço de webconferência do Lync Server 2013 armazena conteúdo compartilhado durante reuniões no repositório de arquivos. Como parte da implementação, você deve especificar um compartilhamento de arquivos a ser usado como repositório para o servidor do Standard Edition ou do Enterprise EditionPool de Front-Ends. Você pode usar um repositório de arquivos existente ou pode especificar um novo compartilhamento de arquivos determinando o nome de domínio totalmente qualificado (FQDN) do servidor de arquivos em que o repositório estará localizado e um nome de pasta para o novo compartilhamento de arquivos.  Para mais informações, consulte Construtor de Topologias – Definir o Repositório de Arquivos para o Front End. O serviço de webconferências criptografa o conteúdo antes de armazená-lo no repositório de arquivos.

O Lync Server 2013 oferece suporte ao uso de compartilhamentos de arquivos em armazenamento anexado direto (DAS) ou em uma rede de área de armazenamento (SAN), incluindo o Sistema de Arquivos Distribuídos (DFS) e em um RAID para repositórios de arquivos. Depois de a Assistente de Implantação do Lync Server definir a localização do repositório de arquivos, o Lync Server cria uma estrutura de pastas dentro do compartilhamento de arquivos similar a:

  - 1-ApplicationServer-1

  - 1-CentralMgmt-1

  - 1-WebServices-1
    
      - CollabContent
    
      - CollabMetadata
    
      - DataConf

O serviço de webconferências então armazena conteúdo como slides do PowerPoint, quadros de comunicações, votações e anexos nas pastas CollabContent e CollabMetadata, localizadas na pasta WebServices.

O administrador deve definir permissões no compartilhamento de arquivos para que grupos do RTC tenham o acesso de leitura e gravação necessário.


> [!WARNING]
> Se você encontrar erros com as permissões, abra o Construtor de Topologias, faça download e publique novamente a topologia existente. Publicar a topologia verificará as permissões do compartilhamento de arquivos e as redefinirá, se necessário.



Você pode usar as configurações a seguir para gerenciar como o conteúdo será armazenado para uma reunião:

  - **ContentGracePeriod**, localizada em [Set-CsConferencingConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsConferencingConfiguration), define por quanto tempo o conteúdo da webconferência permanecerá no servidor depois do término da reunião.

  - **MaxContentStorageMb**, localizada em [Set-CsConferencingConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsConferencingConfiguration), define o volume máximo de espaço para arquivo permitido para o armazenamento de conteúdo durante uma única reunião.

**MaxUploadFileSizeMb** não limita a configuração do carregamento de arquivos para o Lync Web App. O limite de tamanho para o carregamento de arquivos para o Lync Web App está definido como aproximadamente 30MB e é controlado pelo arquivo web.config do IIS: /DataCollabWeb/Int\[Ext\]/Handler/web.config. Para configurar o limite de tamanho para o carregamento de arquivos para o Lync Web App, atualize as opções `maxRequestLength` e `maxAllowedContentLength` no arquivo web.config, conforme exibido abaixo.

    <system.web>
        <!-- 
            Since this handler is used to upload files to DMCU the request size (in kilobytes) 
            has to fit max allowed file size uploaded by Lync Web App client.
            The timeout has to reflect the min client bandwidth. Timeout of 600 secs 
            and 512 Kbits of *client* bandwidth would result into aproximately 30 Mbytes 
            for Lync Web App upload size limit.
        -->
          <httpRuntime maxRequestLength="500000" executionTimeout="600" />
    
    
    
                    <security>
                    <requestFiltering>
                               <requestLimits maxAllowedContentLength="524288000" />
                    </requestFiltering>
                    </security>

Você deve atualizar o arquivo web.config para cada Servidor Front-End.

## Servidor Office Web Apps

Para usar estes novos recursos, administradores devem instalar o Servidor Office Web Apps e configurar o Lync Server 2013 para se comunicar com o Servidor Office Web Apps. Esta documentação fornece informações sobre como configurar o Lync Server 2013 para funcionar com o Servidor Office Web Apps. O que esta documentação não fornece são informações sobre como instalar o Servidor Office Web Apps. Para detalhes da instalação, consulte o site de Implantação de Web Apps do Microsoft Office em <http://go.microsoft.com/fwlink/?linkid=257525>. Este guia inclui informações completas de pré-requisitos para o Servidor Office Web Apps. Observe que o Servidor Office Web Apps deve ser instalado em um computador autônomo que não esteja executando o Lync Server, SQL Server, ou qualquer outro aplicativo de servidor (você não deve ter qualquer versão do Office instalada neste computador). Qualquer computador usado para executar o Servidor Office Web Apps também deve ter um conjunto específico de softwares instalados (incluindo o .NET Framework 4.5 e o Windows PowerShell 3.0). Estes requisitos, juntamente com as informações sobre como configurar certificados e o IIS (Serviços de Informações da Internet), são discutidos em detalhes no site de Implantação de Web Apps do Microsoft Office em <http://go.microsoft.com/fwlink/?linkid=257525>.

## Consulte Também

#### Conceitos

[Visão Geral de Webconferência no Lync Server 2013](lync-server-2013-web-conferencing-overview.md)  
[Lista de verificação de implantação para webconferência](lync-server-2013-deployment-checklist-for-web-conferencing.md)

