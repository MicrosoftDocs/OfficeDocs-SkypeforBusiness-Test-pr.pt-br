---
title: 'Lync Server 2013: Pré-requisitos de software para Enterprise Voice'
TOCTitle: Pré-requisitos de software para Enterprise Voice
ms:assetid: 41172119-9631-46c7-9d9f-386d951c650b
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg425916(v=OCS.15)
ms:contentKeyID: 49306507
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Pré-requisitos de software para Enterprise Voice no Lync Server 2013

 

_**Tópico modificado em:** 2012-10-03_

Verifique se a infraestrutura em que você pretende implantar o Enterprise Voice atende aos seguintes pré-requisitos de software:

  - O Lync Server 2013 Standard Edition ou Enterprise Edition está instalado e funcionando na sua rede.

  - Todos os Servidores de Borda são implantados e estão operacionais na rede de perímetro, incluindo Servidores de Borda executando Serviço de Borda de Acesso, Serviço de Borda A/V, Serviço de Borda de Webconferência e um proxy reverso.

  - O Microsoft Exchange Server 2007 Service Pack 3 (SP3), o Microsoft Exchange Server 2010 ou o Microsoft Exchange Server 2013 é necessário para integrar a Unificação de Mensagens do Exchange com o Lync Server e para fornecer notificações completas e informações do log de chamadas para os pontos de extremidade do Lync.

  - Um ou mais usuários foram criados e habilitados para o Lync Server.

  - Clientes e dispositivos do Lync foram implantados com êxito.

  - O Construtor de Topologias é instalado em um servidor na rede.

## Próximas etapas: Verificar pré-requisitos de segurança e configuração

Depois de verificar os pré-requisitos de software para o Enterprise Voice, você pode usar a documentação para continuar a preparação para a implantação do Enterprise Voice:

1.  Verifique os pré-requisitos de hardware, configuração do usuário e segurança, conforme descrito em [Pré-requisitos de configuração e segurança para Entreprise Voice no Lync Server 2013](lync-server-2013-security-and-configuration-prerequisites-for-enterprise-voice.md).

2.  Instale o Servidor de Mediação, conforme descrito em [Instalar os arquivos para o Servidor de Mediação no Lync Server 2013](lync-server-2013-install-the-files-for-mediation-server.md), mas *somente* se você desejar implantar um Servidor de Mediação autônomo ou pool, porque os Servidores de Mediação estão instalados como parte do pool de Front-End ou do processo de implantação do Servidor Standard Edition quando colocados.

3.  Configure as conexões de tronco para fornecer conectividade PSTN para usuários, conforme descrito em [Configurando troncos no Lync Server 2013](lync-server-2013-configuring-trunks.md).

