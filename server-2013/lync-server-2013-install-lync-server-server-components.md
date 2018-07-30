---
title: 'Lync Server 2013: Instalar componentes de servidor do Lync Server'
TOCTitle: Instalar componentes de servidor do Lync Server
ms:assetid: 186aed6e-7adf-4a92-9f2e-f9a4de5ff202
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398239(v=OCS.15)
ms:contentKeyID: 49306020
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Instalar componentes de servidor para o Lync Server 2013

 

_**Tópico modificado em:** 2014-05-05_

Antes de seguir estas etapas, verifique se você está conectado ao servidor com uma conta de usuário do domínio que seja tanto um administrador local quanto um membro do grupo RTCUniversalReadOnlyAdmins no Active Directory.

O Assistente de Implantação do Lync Server é usado para instalar os componentes necessários para cada função do Lync Server e para ativar o servidor. Este artigo descreve as etapas de implantação de um Servidor Standard Edition ou um Servidor Front-End na infraestrutura do Lync.

## Instalação dos componentes do Lync Server

1.  Se o Assistente de Implantação do Lync Server não estiver em execução, inicie-o no servidor em que você deseja instalar o Lync.

2.  Clique em **Instalar ou Atualizar o Lync Server Sistema**.

3.  No Assistente para Implantação, confirme se a **Etapa 1: Instalar Repositório de Configuração Local** tem uma marca de seleção verde, o que significa que este servidor tem uma cópia local do repositório instalado com sucesso. Caso não esteja marcada, é necessário instalar o repositório de configuração local no servidor. Sig as etapas em [Instalar o repositório de Configuração Local no Lync Server 2013](lync-server-2013-install-the-local-configuration-store.md) e volte para cá.

4.  Quando você estiver pronto para instalar os componentes do Lync Server 2013 no servidor, clique em **Executar** ao lado da **Etapa 2: Instalar ou Remover Componentes do Lync Server**.

5.  Na página **Instalar Componentes do Lync Server**, clique em **Avançar** para instalar componentes conforme definido na topologia publicada.

6.  A página **Executando Comandos** exibirá um resumo dos comandos e informações de instalação conforme ocorre a instalação. Quando terminar, use a lista para selecionar um log para exibição e clique em **Exibir Log**.

7.  Quando a instalação dos componentes do Lync Server 2013 for concluída e você já tiver revisto os logs conforme necessário, clique em **Concluir** para concluir esta etapa na instalação.
    
    > [!NOTE]  
    > Caso você seja solicitado a reiniciar o servidor (o que pode acontecer caso seja necessário instalar a Experiência de Desktop do Windows), siga a instrução. Quando o computador voltar a funcionar, é necessário repetir estas etapas, começando da etapa 3 listada acima (basicamente execute a Etapa 2 no Assistente para Implantação mais uma vez).
