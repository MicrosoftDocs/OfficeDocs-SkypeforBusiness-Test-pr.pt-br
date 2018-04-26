---
title: 'Lync Server 2013: Configurando a autenticação Kerberos'
TOCTitle: Configurando a autenticação Kerberos
ms:assetid: dd8009ef-6265-4cc0-b2c7-e474cd1f4b09
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398976(v=OCS.15)
ms:contentKeyID: 49308341
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurando a autenticação Kerberos no Lync Server 2013

 

_**Tópico modificado em:** 2013-02-21_

O Lync Server 2013 dá suporte à autenticação NTLM e Kerberos para Serviços Web. O Office Communications Server 2007 e o Office Communications Server 2007 R2 usavam o RTCComponentService e o RTCService padrão como contas de usuário para executar pools de aplicativos dos Serviços Web, permitindo que um SPN (nome da entidade de serviço) fosse atribuído às contas de usuário para atuarem como entidade de autenticação. O Lync Server usa o NetworkService para executar Serviços Web, e o NetworkService não pode ter SPNs atribuídos a ele.

Para resolver o problema de não ter objetos do Active Directory para armazenar os SPNs, o Painel de Controle do Lync Server pode usar objetos de conta de computador para essa finalidade. Os objetos de conta de computador podem armazenar os SPNs e não estão sujeitos à expiração da senha, que era um problema com as contas de usuário de versões anteriores.

Use os cmdlets do Windows PowerShell para configurar os objetos de computador a fim de fornecer a autenticação Kerberos.

## Nesta seção

  - [Pré-requisitos para habilitar autenticação Kerberos no Lync Server 2013](lync-server-2013-prerequisites-for-enabling-kerberos-authentication.md)

  - [Criar uma conta de autenticação Kerberos no Lync Server 2013](lync-server-2013-create-a-kerberos-authentication-account.md)

  - [Atribuir uma conta de autenticação Kerberos a um site no Lync Server 2013](lync-server-2013-assign-a-kerberos-authentication-account-to-a-site.md)

  - [Configurando senhas da conta de autenticação Kerberos no Lync Server 2013](lync-server-2013-setting-up-kerberos-authentication-account-passwords.md)

  - [No Lync Server 2013, adicionar autenticação Kerberos a outros sites](lync-server-2013-add-kerberos-authentication-to-other-sites.md)

  - [No Lync Server 2013, remover autenticação Kerberos de um site](lync-server-2013-remove-kerberos-authentication-from-a-site.md)

  - [Testando e relatando status e atribuição de autenticação Kerberos no Lync Server 2013](lync-server-2013-testing-and-reporting-the-status-and-assignment-of-kerberos-authentication.md)

