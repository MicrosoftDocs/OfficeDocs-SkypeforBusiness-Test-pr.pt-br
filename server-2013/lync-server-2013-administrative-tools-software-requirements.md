---
title: 'Lync Server 2013: Requisitos de software de ferramentas administrativas'
TOCTitle: Requisitos de software de ferramentas administrativas
ms:assetid: 2fb172c3-7b84-4e49-981c-2a17e7a00a29
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg195653(v=OCS.15)
ms:contentKeyID: 49306275
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Requisitos de software de ferramentas administrativas no Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

Este tópico descreve o software necessário para instalar e usar as ferramentas administrativas do Lync Server 2013, além dos requisitos de sistema operacional.

## Microsoft.NET Framework 4.5

A edição de 64 bits do Microsoft .NET Framework 4.5 é necessária para o Lync Server 2013.

## Windows PowerShell 3.0

O Windows PowerShell 3.0 é necessário para executar qualquer componente do Microsoft Lync Server 2013. Para obter mais informações, consulte [Instalando Windows PowerShell 3.0 para Lync Server 2013](lync-server-2013-installing-windows-powershell-3-0.md).

## Windows Installer versão 4.5

Lync Server 2013 usa a tecnologia do Windows Installer para instalar, desinstalar e manter determinadas funções de servidor. O Windows Installer versão 4.5 está disponível como um componente redistribuível para o sistema operacional Windows Server. O Windows Installer 4.5 é fornecido com Windows Server 2012 R2, Windows Server 2012 e Windows Server 2008 R2, o que significa que não é necessário baixar o utilitário em nenhum computador que está executando Lync Server 2013. ( Lync Server 2013 só pode ser instalado em computadores que executam Windows Server 2012 R2, Windows Server 2012 ou Windows Server 2008 R2.)

No entanto, se você deseja instalar o Construtor de Topologias de Shell de Gerenciamento do Lync Server ou Lync Server em uma estação de trabalho de administrador, será necessário baixar o Windows Installer 4.5. Esse utilitário é fornecido com o Windows 7 e Windows 2008 R2, mas não com nenhuma versão anterior do sistema operacional Windows. É possível baixar o Windows Installer 4.5 a partir do Centro de download da Microsoft em <http://go.microsoft.com/fwlink/p/?linkid=197395>.

## Plug-in do navegador Microsoft Silverlight 5

O Painel de Controle do Lync Server 2013 é uma ferramenta baseada na Web e exige que você instale a versão mais atual do plug-in do navegador Microsoft Silverlight 5. Ao iniciar o Painel de Controle do Lync Server 2013, se este software não estiver instalado ou se uma versão anterior estiver instalada, o Painel de Controle do Lync Server 2013 solicita a instalação da versão solicitada.

## Consulte Também

#### Conceitos

[Suporte a sistemas operacionais de servidor e de ferramentas no Lync Server 2013](lync-server-2013-server-and-tools-operating-system-support.md)  

#### Outros Recursos

[Requisitos de infraestrutura das ferramentas administrativas no Lync Server 2013](lync-server-2013-administrative-tools-infrastructure-requirements.md)  
[Direitos e permissões de administrador necessários para configuração e administração do Lync Server 2013](lync-server-2013-administrator-rights-and-permissions-required-for-setup-and-administration.md)

