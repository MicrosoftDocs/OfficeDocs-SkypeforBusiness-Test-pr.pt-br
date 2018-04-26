---
title: 'Lync Server 2013: Componentes usados pelo Grupo de Respostas'
TOCTitle: Componentes usados pelo Grupo de Resposta
ms:assetid: 2b058785-47ca-43b7-b3de-6928a60dc685
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg425768(v=OCS.15)
ms:contentKeyID: 49306229
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Componentes usados pelo Grupo de Resposta no Lync Server 2013

 

_**Tópico modificado em:** 2012-09-11_

O Aplicativo Grupo de Resposta é habilitado automaticamente ao implantar o Enterprise Voice. esta seção descreve os componentes que suportam o Aplicativo Grupo de Resposta.

## Componentes do Grupo de Resposta

Os componentes do Microsoft Lync Server 2013 a seguir oferecem suporte ao Aplicativo Grupo de Resposta:

  - **Serviço de aplicativos**    Serviço de aplicativos fornece uma plataforma para implantação, hospedagem e gerenciamento de aplicativos do unified messaging, como Grupo de Resposta. O Serviço de aplicativos é automaticamente instalado em cada Servidor Front-End em um Pool de Front-Ends e em todos os servidores Standard Edition.

  - **Aplicativo Grupo de Resposta**   O Aplicativo Grupo de Resposta é um dos aplicativos do unified communications hospedados pelo Serviço de aplicativos. É incluído automaticamente ao implantar o Grupo de Resposta. O Aplicativo Grupo de Resposta direciona e enfileira as chamadas em entrada para grupos de agentes.

  - **Pacote de idiomas**   Um pacote de idiomas é necessário para suportar a conversão de texto em fala e o reconhecimento de fala. Essas tecnologias de fala são usadas ao configurar mensagens, como a mensagem de boas-vindas e outros prompts, e questões e respostas de IVR (resposta interativa de voz). Por padrão, os 26 pacotes de idioma suportados são instalados quando você implanta o Lync Server 2013.

  - **Arquivos de áudio**   Arquivos de áudio são usados para mensagens e música de espera.

  - **Repositório de Arquivos**    Grupo de Resposta usa o Repositório de arquivos para armazenar arquivos de áudio. Diversos pools do Grupo de Resposta podem usar a mesma instância do Repositório de arquivos.

  - **Ferramenta de Configuração de Grupo de Resposta**   O Ferramenta de Configuração de Grupo de Resposta é uma ferramenta baseada na web usada para criar e configurar grupos de resposta. O Ferramenta de Configuração de Grupo de Resposta é incluído quando você instala Serviços Web.

  - **Painel de Controle do Microsoft Lync Server 2013**   É possível usar o Painel de Controle do Lync Server para instalar e configurar grupos de agentes e filas para grupos de respostas.

  - **Shell de Gerenciamento do Lync Server**   Todas as configurações do Grupo de Resposta podem ser definidas usando os cmdlets do Shell de Gerenciamento do Lync Server.

  - **Microsoft Lync 2013**   Agentes formais (agentes que precisam fazer o login no grupo antes de poder aceitar chamadas do grupo) usam o Lync 2013 para fazer o login e logout do grupo. Se um grupo de agentes está configurado para agentes formais, os agentes clicam em um item de menu no Lync 2013 para abrir o Internet Explorer e exibir um console da página da Web para login e logout do grupo.

  - **Serviços Web**   Os Serviços Web são necessários para o Ferramenta de Configuração de Grupo de Resposta, o console de entrada e saída dos agentes, o Painel de Controle do Lync Server e o serviço web do cliente do Grupo de Resposta.

  - **Serviço Web de Cliente do Grupo de Resposta**    Aplicativo Grupo de Resposta fornece um serviço web de cliente, que pode ser usado por aplicativos de terceiros para recuperar informações sobre agentes, associação no grupo de agente, status de logon do agente, status da chamada para grupos e os grupos que suportam chamadas anônimas. O Lync 2013 e o Lync 2010 Attendant usam o serviço Web cliente do Grupo de Resposta para recuperar a lista de grupos de reposta que os agentes podem usar para fazer chamadas anônimas. O serviço web de cliente é incluído durante a instalação dos Serviços Web.

