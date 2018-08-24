---
title: 'Lync Server 2013: Visão geral do ambiente híbrido do Lync Server 2013'
TOCTitle: Visão geral do ambiente híbrido do Lync Server 2013
ms:assetid: 0d16ec3a-28f0-4483-96e7-8e68f30398fa
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204669(v=OCS.15)
ms:contentKeyID: 49305869
ms.date: 06/02/2017
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Visão geral do ambiente híbrido do Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

O ambiente híbrido do Lync Server 2013 refere-se a uma implantação na qual existem alguns usuários hospedados no Lync Server 2013 local e outros, no Lync Online; porém, os usuários compartilham o mesmo domínio, como user@contoso.com.

## Sobre este guia

Este guia descreve as tarefas necessárias para configurar seu ambiente do Lync Server 2013 para que tenha interoperabilidade com o Lync Online e, em seguida, mover os usuários de sua implantação local para que usem o Lync Online.

## Pré-requisitos

Você deverá ter os seguintes aplicativos e utilitários instalados para concluir as tarefas de configuração da implantação como híbrida. Os instaladores desses arquivos estão incluídos na mídia de instalação fornecida para a implantação, bem como os links contidos na lista a seguir.

  - [Serviços de Federação de Diretório Ativo (AD FS) 2.0](http://go.microsoft.com/fwlink/p/?linkid=257305)

  - [Ferramenta de Sincronização de Diretório 9.1 da Microsoft](http://go.microsoft.com/fwlink/p/?linkid=257307)

  - [Instale o Windows PowerShell para login único com o AD FS](http://go.microsoft.com/fwlink/p/?linkid=398710)

  - O Assistente de Conexão do Microsoft Online Services (msoidcli-7.0.msi) está incluído na Configuração da Área de Trabalho do Office 365, que pode ser obtida na página Downloads vinculada ao portal de administração do Office 365.

## Credenciais do administrador

Quando você for solicitado a informar as credenciais de administrador, insira o nome de usuário e a senha da conta de administrador de seu locatário do Office 365. Essas credenciais também serão utilizadas quando você configurar os Serviços de Federação de Diretório Ativo (AD FS) 2.0, a Sincronização de Diretório, o Login Único, a federação e quando for mover usuários para o Lync Online.

## Como se conectar ao Lync Online PowerShell

Agora, os administradores têm a capacidade de usar o Windows PowerShell para gerenciarem o Lync Online e suas contas de usuário do Lync Online. Para fazer isso, primeiro é necessário baixar e instalar o Módulo Conector do Lync Online do Centro de Download da Microsoft (http://go.microsoft.com/fwlink/?LinkId=294688). Para obter mais informações sobre o download, a instalação e o uso do Módulo Conector do Lync Online e para obter informações detalhadas sobre o uso do Windows PowerShell para gerenciar o Lync Online, consulte [Usar o Windows PowerShell para gerenciar o Lync Online](https://docs.microsoft.com/en-us/SkypeForBusiness/set-up-your-computer-for-windows-powershell/set-up-your-computer-for-windows-powershell).

