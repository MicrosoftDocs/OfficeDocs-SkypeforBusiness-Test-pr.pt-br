---
title: 'Lync Server 2013: Protegendo o IIS'
TOCTitle: Protegendo o IIS no Lync Server 2013
ms:assetid: a67171a6-6703-4e09-abb3-35d335bb674e
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn518332(v=OCS.15)
ms:contentKeyID: 60505938
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Protegendo o IIS no Lync Server 2013

 

_**Tópico modificado em:** 2013-12-05_

No Microsoft Office Communications Server 2007 e no Microsoft Office Communications Server 2007 R2, os Serviços de Informações da Internet (IIS) eram executados em uma conta de usuário padrão. Isso era uma causa potencial de problemas: se a senha expirasse, você podia perder os serviços Web, um problema que era difícil diagnosticar. Para evitar o problema de expiração das senhas, o Microsoft Lync Server 2013 permite que você crie uma conta de computador (para um computador que não existe de fato) que pode servir como a entidade de autenticação de todos os computadores em um local que esteja executando o IIS. Como essas contas utilizam o protocolo de autenticação Kerberos, elas são referidas como contas Kerberos e o novo processo de autenticação é conhecido como autenticação Kerberos de Web. Assim, você pode gerenciar todos os seus servidores IIS usando uma única conta.

Para executar os servidores sob essa entidade de autenticação, primeiro crie uma conta de computador usando o cmdlet New-CsKerberosAccount; essa conta é, então, atribuída a um ou mais locais. Após a atribuição, a associação entre a conta e o local do Lync Server 2013 é habilitada, por meio da execução do cmdlet Enable-CsTopology. Entre outras consequências, isso cria o nome da entidade de serviço (SPN) nos Serviços de Domínio Active Directory (AD DS). Os SPNs proporcionam aos aplicativos cliente uma maneira de localizar um determinado serviço. Para obter informações detalhadas, consulte [New-CsKerberosAccount](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsKerberosAccount) na documentação de operaçõesn.

## Práticas recomendadas

Para aprimorar a segurança do IIS, é recomendável implementar uma conta Kerberos para o IIS. Se você não implementar uma conta Kerberos, o IIS é executado em uma conta de usuário padrão.

