---
title: 'Lync Server 2013: Componentes usados pelo aplicativo Comunicado'
TOCTitle: Componentes usados pelo aplicativo Comunicado
ms:assetid: 7b1a0281-cf31-459d-a734-5f10a129089c
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398608(v=OCS.15)
ms:contentKeyID: 49307210
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Componentes usados pelo aplicativo Comunicado no Lync Server 2013

 

_**Tópico modificado em:** 2012-09-13_

No Lync Server 2013, o Aplicativo Comunicado é um componente do Aplicativo Grupo de Resposta. Quando você implanta o Enterprise Voice, o Aplicativo Comunicado é automaticamente instalado e ativado junto com o Aplicativo Grupo de Resposta. Esta seção descreve os componentes que oferecem suporte ao Aplicativo Comunicado.

## Componentes de Aplicativo de Comunicado

Os componentes do Lync Server a seguir oferecem suporte ao Aplicativo Comunicado:

  - **Serviço de aplicativos**    Serviço de aplicativos oferece uma plataforma para a implantação, hospedagem e gerenciamento de aplicativos de comunicação unificada. Serviço de aplicativos é automaticamente instalado em cada servidor Front-End em um Pool de Front-Ends e em cada servidor Standard Edition.

  - **Aplicativo Grupo de Resposta** O Aplicativo Grupo de Resposta é um dos aplicativos de comunicação unificada hospedados pelo Serviço de aplicativos. Quando um intervalo de números de telefone não atribuído é configurado para rotear para um comunicado, o Aplicativo Grupo de Resposta é necessário para rotear as chamadas feitas ao número de telefone. ( Aplicativo Grupo de Resposta não é necessário se todos os intervalos são configurados para rotear para o UM do Exchange.)

  - **Arquivos de áudio** Os arquivos de áudio são usados para os comunicados.

  - **Armazenamento de arquivos** A Aplicativo Comunicado usa o repositorio de arquivos para armazenar seus arquivos de áudio.

  - **Painel de Controle do Lync Server** Você pode usar Painel de Controle do Lync Server para configurar a tabela de números não atribuída.

  - **Shell de Gerenciamento do Lync Server** Você pode usar os cmdlets Shell de Gerenciamento do Lync Server para definir as configurações de lançamento e a tabela de número não atribuída.

