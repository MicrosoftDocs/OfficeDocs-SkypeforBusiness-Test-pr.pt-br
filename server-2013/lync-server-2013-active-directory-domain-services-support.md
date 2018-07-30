---
title: 'Lync Server 2013: Suporte a Serviços de Domínio Active Directory'
TOCTitle: Suporte a Serviços de Domínio Active Directory
ms:assetid: aeb62d5e-e424-473a-b795-9452150c98dd
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg412831(v=OCS.15)
ms:contentKeyID: 49307788
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Suporte a Serviços de Domínio Active Directory no Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

O Lync Server 2013 usa o Repositório de Gerenciamento Central para armazenar dados de configuração para servidores e serviços, em vez de dependerem do Serviços de Domínio Active Directory para essas informações, como no passado. O Lync Server 2013 ainda armazena o seguinte no AD DS:

  - **Extensões de esquema**
    
      - Extensões de objetos de usuário
    
      - Extensões para classes do Lync Server 2010 e Office Communications Server 2007 R2 para manter a compatibilidade com versões anteriores com suporte

  - **Dados** (armazenados no esquema estendido do Lync Server 2013 e em classes existentes)
    
      - URI do SIP do usuário e outras configurações de usuário
    
      - Objetos de contato para aplicativos (por exemplo, o Aplicativo Grupo de Resposta e o Aplicativo Atendedor de Conferência)
    
      - Dados publicados para compatibilidade com versões anteriores
    
      - Um ponto de controle de serviço (SCP) do Repositório de Gerenciamento Central
    
      - Conta de Autenticação Kerberos (um objeto computador opcional)

Esta seção descreve os requisitos de suporte do AD DS para o Lync Server 2013. Para detalhes sobre o suporte de topologias, consulte [Topologias do Active Directory suportadas no Lync Server 2013](lync-server-2013-supported-active-directory-topologies.md) na documentação de Suporte.

## Sistemas Operacionais do Controlador de Domínio com Suporte

O Lync Server 2013 oferece suporte a controladores de domínio executando os seguintes sistemas operacionais:

  - Windows Server 2012 R2nm-win-2012-server

  - Sistema operacional Windows Server 2012

  - Sistema operacional Windows Server 2008 R2

  - Sistema operacional Windows Server 2008

  - Windows Server 2008 Enterprise 32 bits

  - As versões de 32 ou 64 bits do sistema operacional Windows Server 2003 R2

  - As versões de 32 ou 64 bits do sistema operacional Windows Server 2003

## Nível Funcional de Floresta e de Domínio

Você deve elevar todos os domínios em que o Lync Server 2013 for implantado para um nível funcional de domínio do Windows Server 2012 R2, Windows Server 2008 R2, Windows Server 2008, ou pelo menos Windows Server 2003.

Todas as florestas em que você implantar o Lync Server 2013 devem ser elevadas para um nível funcional de floresta do Windows Server 2012 R2, Windows Server 2008 R2, Windows Server 2008, ou pelo menos Windows Server 2003.

## Suporte a Controladores de Domínio Somente para Leitura

O Lync Server 2013 oferece suporte a implantações do Serviços de Domínio Active Directory que incluem controladores de domínio somente leitura ou servidores de catálogo global somente leitura, desde que hajam controladores de domínio graváveis disponíveis.

## Nomes de Domínio

O Lync Server não oferece suporte a domínios de rótulo único. Por exemplo, uma floresta com um domínio raiz chamado **contoso.local** é compatível, mas um domínio raiz chamado **local** não é compatível. Para obter detalhes, consulte o artigo 300684 da Base de Dados de Conhecimento Microsoft, “Informações sobre como configurar os domínios do Active Directory por meio de nomes DNS de rótulo único”, em <http://go.microsoft.com/fwlink/?linkid=143752>.

> [!NOTE]  
> O Lync Server não suporta renomeação de domínios. Se você precisar renomear um domínio onde o Lync Server estiver implantado, você precisará primeiro desinstalar o Lync Server, em seguida renomear o domínio, e por fim reinstalar o Lync Server.

## Ambientes AD DS Bloqueados

Em um ambiente AD DS bloqueado, objetos Usuários e Computadores são geralmente colocados em unidades organizacionais (UOs) específicas com a herança de permissões desabilitada para ajudar a proteger a delegação administrativa e para habilitar o uso de objetos de Política de Grupo (GPOs) para reforçar políticas de segurança. O Lync Server 2013 pode ser implantado em um ambiente bloqueado do Active Directory. Para detalhes sobre os requisitos para implantar o Lync Server em um ambiente bloqueado, consulte [Preparando Serviços de Domínio Active Directory bloqueado no Lync Server 2013](lync-server-2013-preparing-a-locked-down-active-directory-domain-services.md) na documentação de Implantação.

