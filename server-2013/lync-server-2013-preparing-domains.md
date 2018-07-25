---
title: 'Lync Server 2013: Preparando domínios'
TOCTitle: Preparando domínios
ms:assetid: 8eea541c-5f9d-4afc-92a8-a31d6f742544
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398721(v=OCS.15)
ms:contentKeyID: 49307426
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Preparando domínios para Server 2013

 

_**Tópico modificado em:** 2012-10-29_

A preparação do domínio é a etapa final da preparação do Serviços de Domínio Active Directory para o Lync Server 2013. A etapa de preparação do domínio adiciona as ACEs (entradas de controle de acesso) necessárias aos grupos universais que concedem permissões para hospedar e gerenciar usuários no domínio. A etapa de preparação de domínio cria ACEs na raiz do domínio e três contêineres internos:

Você pode executar a preparação do domínio em qualquer computador no domínio em que estiver implantando o Lync Server. Você deve preparar cada domínio que hospedará o Lync Server ou usuários.

Se a herança de permissões estiver desabilitada ou as permissões de usuário autenticado estiverem desabilitadas em sua organização, você deve executar etapas adicionais durante a preparação do domínio. Para detalhes, consulte [Preparando Serviços de Domínio Active Directory bloqueado no Lync Server 2013](lync-server-2013-preparing-a-locked-down-active-directory-domain-services.md).

Se sua organização utiliza unidades organizacionais (UO) em vez de três contêineres internos (ou seja, Usuários, Computadores e Controladores de Domínio), você deve conceder acesso de leitura às UOs para o grupo Usuários Autenticados. O acesso de leitura aos contêineres é exigido para a preparação do domínio. Se o grupo Usuários Autenticados não tiver acesso de leitura na UO, execute o cmdlet **Grant-CsOuPermission**, conforme ilustrado nos exemplos de código a seguir, para conceder permissões de leitura para cada UO.

```
    Grant-CsOuPermission -ObjectType <User | Computer | InetOrgPerson | Contact | AppContact | Device> -OU <DN of the OU > 
```

```
    Grant-CsOuPermission -ObjectType "user","contact",inetOrgPerson" -OU "ou=Redmond,dc=contoso,dc=net"
```
Para obter detalhes sobre o cmdlet **Grant-CsOuPermission**, consulte a documentação do Shell de Gerenciamento do Lync Server.


> [!TIP]
> Para detalhes sobre as ACEs criadas na raiz do domínio e nos contêineres Usuários, Computadores e Controladores de Domínio, consulte <A href="lync-server-2013-changes-made-by-domain-preparation.md">Alterações feitas pela preparação de domínio no Lync Server 2013</A>.



## Nesta seção

  - [Executando preparação de domínio para Lync Server 2013](lync-server-2013-running-domain-preparation.md)

  - [Usando cmdlets para reverter a preparação do domínio para o Lync Server 2013](lync-server-2013-using-cmdlets-to-reverse-domain-preparation.md)

