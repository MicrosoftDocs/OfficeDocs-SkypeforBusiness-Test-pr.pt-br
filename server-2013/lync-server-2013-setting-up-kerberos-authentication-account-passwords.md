---
title: 'Lync Server 2013: Configurando senhas da conta de autenticação Kerberos'
TOCTitle: Configurando senhas da conta de autenticação Kerberos
ms:assetid: b435f88e-4a77-4be7-b7e5-c17484303b74
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg412870(v=OCS.15)
ms:contentKeyID: 49307842
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurando senhas da conta de autenticação Kerberos no Lync Server 2013

 

_**Tópico modificado em:** 2010-11-03_

Depois de criar o objeto de computador para a conta de autenticação Kerberos, você poderá configurar a senha da conta. Execute o cmdlet do Windows PowerShell para a configuração da senha de conta Kerberos em um servidor. É possível definir a senha no objeto criado para a autenticação Kerberos. A senha pode ser definida como um valor conhecido, mas por padrão é uma senha aleatória. A senha está disponível para todas as fontes de autenticação Kerberos que usam a conta. Use cmdlets do Windows PowerShell para configurar e gerenciar senhas de conta Kerberos.

> [!NOTE]  
> O objeto de conta Kerberos é um objeto de computador, mas usa o parâmetro UserAccount para operações nos cmdlets Windows PowerShell referenciados. Perceba que isso não é um erro, mas o comportamento pretendido do cmdlet quando usado com a criação e manutenção da conta Kerberos.

## Nesta seção

  - [Configurar uma senha da conta de autenticação Kerberos authentication em um servidor no Lync Server 2013](lync-server-2013-set-a-kerberos-authentication-account-password-on-a-server.md)

  - [Sincronizar uma senha de conta de autenticação Kerberos com o IIS no Lync Server 2013](lync-server-2013-synchronize-a-kerberos-authentication-account-password-to-iis.md)

