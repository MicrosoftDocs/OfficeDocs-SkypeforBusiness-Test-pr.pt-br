---
title: 'Lync Server 2013: Instalar ferramentas administrativas do Lync Server'
TOCTitle: Instalar ferramentas administrativas do Lync Server
ms:assetid: 842b85e4-2eeb-464f-b1c1-ceb8cc04f8d5
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398665(v=OCS.15)
ms:contentKeyID: 49307309
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Instalar ferramentas administrativas do Lync Server 2013

 

_**Tópico modificado em:** 2013-02-21_

Este tópico descreve como instalar as ferramentas administrativas necessárias para usar na implantação e gerenciamento do Lync Server 2013. As ferramentas administrativas são instaladas por padrão em cada servidor que executa o Lync Server 2013. Além disso, você pode instalar as ferramentas administrativas em outros computadores, como consoles administrativos dedicados. Recomendamos que você instale as ferramentas administrativas em um computador que esteja no mesmo domínio ou floresta que a implantação do Lync Server 2013 que você está criando porque, ao fazê-lo, você se certifica de que as etapas de preparação do Serviços de Domínio Active Directory já estão concluídas, o que permite utilizar as ferramentas administrativas nesse computador posteriormente para publicar sua topologia.

Verifique a infraestrutura, o sistema operacional, o software e os requisitos de direitos de administrador antes de instalar ou usar as ferramentas administrativas do Lync Server 2013. Para obter detalhes sobre os requisitos de infra-estrutura, consulte [Requisitos de infraestrutura das ferramentas administrativas no Lync Server 2013](lync-server-2013-administrative-tools-infrastructure-requirements.md). Para obter detalhes sobre os requisitos de software e sistema operacional para instalar as ferramentas administrativas do Lync Server 2013, consulte [Suporte a sistemas operacionais de servidor e de ferramentas no Lync Server 2013](lync-server-2013-server-and-tools-operating-system-support.md), [Requisitos adicionais de software para Lync Server 2013](lync-server-2013-additional-software-requirements.md) e [Suporte adicional e requisitos de servidor no Lync Server 2013](lync-server-2013-additional-server-support-and-requirements.md). Para obter detalhes sobre direitos de usuário e permissões necessárias para instalar e usar as ferramentas, consulte [Direitos e permissões de administrador necessários para configuração e administração do Lync Server 2013](lync-server-2013-administrator-rights-and-permissions-required-for-setup-and-administration.md).

> [!IMPORTANT]  
> Se a sua organização requer a localização de Serviços de Informações da Internet (IIS) e de todos os serviços web em uma unidade diferente da unidade do sistema, você pode alterar o caminho do local de instalação para os arquivos do Lync Server na caixa de diálogo de instalação. Se você instalar os arquivos de instalação nesse caminho, incluindo OCSCore.msi, o restante dos arquivos do Lync Server 2013 será implantado também nesta unidade.

## Para instalar as ferramentas administrativas do Lync Server 2013

1.  Faça logon como um administrador local (requisito mínimo) no computador onde você deseja instalar as ferramentas administrativas. Se você estiver conectado como um usuário padrão no sistema operacional Windows Vista ou Windows 7 e o UAC (Controle da Conta de Usuário) estiver habilitado, será solicitado para informar o nome de usuário e a senha do administrador local ou de um domínio equivalente.

2.  Localize a mídia de instalação no seu computador e clique duas vezes em \\Setup\\amd64\\Setup.exe.

3.  Se você é solicitado a instalar o Microsoft Visual C++ 2008 distribuível, clique em **Sim**.

4.  Na página **Microsoft Lync Server 2013 Local de Instalação**, clique em **OK**. Altere este caminho para outro local ou unidade se precisa instalar os arquivos em outro local.
    
    > [!IMPORTANT]  
    > Se a sua organização requer que você localize o IIS (Serviços de Informações da Internet) e todos os Serviços Web em uma unidade diferente da unidade do sistema, você pode alterar o caminho do local de instalação para os arquivos do Lync Server 2013 na caixa de diálogo Instalação. Se você instalar os arquivos de Instalação para esse caminho, incluindo OCSCore.msi, o restante dos arquivos do Lync Server 2013 também serão implantados nesta unidade.

5.  Na página **Acordo de licença do usuário final**, revise os termos de licença, clique em **Eu aceito** e em **OK**. Esta etapa é obrigatória antes de continuar.

6.  Na página **Microsoft Lync Server 2013 - Assistente de implantação**, clique em **Instalar ferramentas do administrador**.

7.  Quando a instalação for concluída com êxito, clique em **Sair**.

## Consulte Também

#### Tarefas

[Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md)  

#### Conceitos

[Ferramentas administrativas do Lync Server 2013](lync-server-2013-lync-server-administrative-tools.md)

