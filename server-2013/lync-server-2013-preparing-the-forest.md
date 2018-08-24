---
title: 'Lync Server 2013: Preparando a floresta'
TOCTitle: Preparando a floresta
ms:assetid: 3d188fcb-c64e-46cf-a3a7-9e3ebefed7fd
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg425898(v=OCS.15)
ms:contentKeyID: 49306457
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Preparando a floresta para Lync Server 2013

 

_**Tópico modificado em:** 2013-02-21_

A preparação da floresta cria objetos e configurações globais do Active Directory, bem como grupos universais do Active Directory, para uso pelo Lync Server 2013, além de conceder permissões de acesso adequadas aos objetos do Active Directory. Para ver uma descrição de grupos universais e dos objetos e configurações globais criados pela preparação da floresta, consulte [Alterações feitas pela preparação da floresta no Lync Server 2013](lync-server-2013-changes-made-by-forest-preparation.md).

A preparação da floresta também cria objetos que contêm conjuntos de propriedades e especificadores de exibição usados pelo Lync Server 2013 e os armazena no contêiner Configuração.

> [!IMPORTANT]  
> Certifique-se de que as alterações na preparação de esquema foram replicadas em todos os controladores de domínio antes de executar o procedimento de preparação de floresta. Se não for concluída a replicação, ocorrerá um erro.

Se você estiver executando uma nova implantação do Lync Server, armazene as configurações globais no contêiner Configuração. Se você estiver atualizando de uma versão mais antiga e ainda armazenar configurações globais no contêiner Sistema, poderá continuar usando o contêiner Sistema.

Você deve ser membro do grupo Administração de Empresa ou Admins. do Domínio no domínio raiz da floresta para executar esse procedimento.

## Nesta seção

  - [Executando preparação de floresta para Lync Server 2013](lync-server-2013-running-forest-preparation.md)

  - [Usando cmdlets para reverter preparação da floresta no Lync Server 2013](lync-server-2013-using-cmdlets-to-reverse-forest-preparation.md)

