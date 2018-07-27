---
title: 'Lync Server 2013: Pré-requisitos de configuração e segurança para Entreprise Voice'
TOCTitle: " Pré-requisitos de configuração e segurança para Entreprise Voice"
ms:assetid: 15354abe-733e-466b-bcd4-a6cfbf58caf8
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398221(v=OCS.15)
ms:contentKeyID: 49305998
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Pré-requisitos de configuração e segurança para Entreprise Voice no Lync Server 2013

 

_**Tópico modificado em:** 2012-10-18_

Verifique se a sua infraestrutura atende aos seguintes pré-requisitos de segurança, configuração do usuário e hardware específico ao cenário.

## Direitos Administrativos e Infraestrutura do Certificado

Certifique-se que o ambiente está configurado com os grupos de usuários administrativos e infraestrutura de certificado para o uso durante o processo de implantação do Enterprise Voice.

  - Os administradores responsáveis pela implantação do Enterprise Voice devem ser membros do grupo RTCUniversalServerAdmins.

  - Administradores realizando as tarefas de configuração devem ter direitos adequados:
    
      - **CsVoiceAdministrator:** Essa função de administrador pode realizar as tarefas de configuração de voz, gerenciar os aplicativos de voz e designar as políticas de voz aos usuários finais.
    
      - **CsUserAdministrator:** Essa função de administrador pode gerenciar as propriedades do usuário, como habilitar o Enterprise Voice para um usuário, pode designar políticas por usuário, com exceção da política de arquivamento, além de mover usuários e gerenciar telefones de área comum e dispositivos análogos.
    
      - **CsAdministrator:** Essa função de administrador pode realizar todas as tarefas do CsVoiceAdministrator e do CsUserAdministrator.
    
    > [!NOTE]  
    > A representação permite que mais administradores participem da sua implantação do Lync Server sem abrir acessos não necessários a recursos.

  - A infraestrutura de chave gerenciada (MKI) é implantada e configurada, usando uma infraestrutura de autoridade de certificação (CA) da Microsoft ou de um terceiro.
    
    > [!NOTE]  
    > Para obter detalhes sobre os requisitos do certificado do Lync Server, consulte <a href="lync-server-2013-certificate-infrastructure-requirements.md">Requisitos de infraestrutura de certificado para o Lync Server 2013</a> na documentação de Planejamento.

## Configuração do usuário

Se você colocou o Servidor de Mediação com cada pool de Front-Ends ou Servidor Standard Edition durante a implantação do Front-Ends, as configurações de usuário necessárias para Enterprise Voice foram configuradas automaticamente durante a instalação dos arquivos dessas funções do servidor.

Se você estiver recém implantando a carga de trabalho do Enterprise Voice, antes de iniciar o processo de implantação, designe um número de telefone principal para cada usuário que você planeja habilitar para o Enterprise Voice. Como administrador, você é responsável por certificar-se que esse número seja exclusivo. Antes da implementação, todos os números de telefone principais devem ser normalizados (corretamente formatados) e copiados para a propriedade **URI da Linha** de cada usuário, usando o Painel de Controle do Lync Server.

> [!NOTE]  
> Para obter exemplos dos números de telefone principais necessários para a implantação do Enterprise Voice, consulte a seção <a href="lync-server-2013-dial-plans-and-normalization-rules.md">Planos de discagem e regras de normalização no Lync Server 2013</a> do <a href="lync-server-2013-dial-plans-and-normalization-rules.md">Planos de discagem e regras de normalização no Lync Server 2013</a> na documentação de Planejamento.

## Próximas etapas: Instalar arquivos ou configurar a conectividade da PSTN

Depois de verificar os pré-requisitos de software e de ambiente para o Enterprise Voice, você pode usar o conteúdo a seguir para:

  - Instalar o Servidor de Mediação, conforme descrito em [Instalar os arquivos para o Servidor de Mediação no Lync Server 2013](lync-server-2013-install-the-files-for-mediation-server.md), mas se você só deseja implantar um pool ou Servidor de Mediação autônomo em razão de os Servidores de Mediação estarem instalados como partes do pool de Front-Ends ou do processo de implantação do Servidor Standard Edition quando colocado.

  - Ou, iniciar a configuração para rotear chamadas para os usuários do Enterprise Voice, conforme descrito em [Configurando troncos no Lync Server 2013](lync-server-2013-configuring-trunks.md).

