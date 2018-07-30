---
title: 'Lync Server 2013: Editar ou configurar URLs simples'
TOCTitle: Editar ou configurar URLs simples
ms:assetid: 0008aeea-4ae9-4e36-83cd-ef7ff7b6e128
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398063(v=OCS.15)
ms:contentKeyID: 49305658
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Editar ou configurar URLs simples no Lync Server 2013

 

_**Tópico modificado em:** 2014-02-04_

Este procedimento não exige associação a um grupo de administradores locais ou de domínio privilegiado. Você deve fazer logon em um computador como usuário padrão.

O Lync Server 2013 usa URLs simples para chamadas internas e externas diretas a serviços no Servidor Front-End ou no Diretor, se uma URL tiver sido implantada. Para obter mais informações sobre URLs simples, consulte [Planejamento de URLs simples no Lync Server 2013](lync-server-2013-planning-for-simple-urls.md) na documentação de Planejamento. Você pode selecionar o formato de suas URL simples de várias opções. Para obter detalhes sobre essas opções, consulte [Requisitos de DNS para URLs simples no Lync Server 2013](lync-server-2013-dns-requirements-for-simple-urls.md) na documentação de Planejamento.

Por padrão, as URLs simples serão configurados no formulário (por exemplo, a URL simples de discagem): https://dialin.\<SIP Domain\>

## Para configurar URLs simples

1.  No Construtor de Topologias, clique com o botão direito do mouse no nó do **Lync Server**, depois clique em **Editar Propriedades**.

2.  No painel **URLs Simples**, selecione **URLs de acesso telefônico:** (Discagem) ou **URLs de Reunião:** (Reunião) para editar. Em seguida, clique em **Editar URL**.

3.  Atualize a URL para o valor desejado e clique em **OK** para salvar a URL editada. O exemplo mostrado aqui modificou a URL de Discagem para https://pool01.contoso.net/dialin.

4.  Edite a URL de Reunião usando as mesmas etapas, se necessário.

## Para definir a URL simples Admin opcional

1.  No Construtor de Topologias, clique com o botão direito do mouse no nó do **Lync Server**, depois clique em **Editar Propriedades**.

2.  Na caixa **URL de acesso administrativo**, digite a URL simples que você deseja para acesso administrativo ao Painel de Controle do Lync Server 2013 e clique em **OK**.
    

    > [!TIP]
    > Recomendamos usar a URL mais simples possível para a URL Admin. A opção mais simples é <STRONG>https://admin.</STRONG> <EM>&lt;domain&gt;</EM> .

    
    > [!IMPORTANT]  
    > Se você alterar uma URL simples após a implantação inicial, esteja ciente das alterações que afetam seus registros de DNS (Sistema de Nome de Domínio) e certificados para URLs simples. Se a alteração impactar a base de uma URL simples, você deverá alterar os registros DNS e certificados também. Por exemplo, a alteração de https://lync.contoso.com/Meet para https://meet.contoso.com altera a URL base de lync.contoso.com para meet.contoso.com, portanto, você precisaria alterar os registros DNS e certificados para se referir a meet.contoso.com. Se você alterou a URL simples de https://lync.contoso.com/Meet para https://lync.contoso.com/Meetings, a URL base de lync.contoso.com permanece a mesma, portanto, não são necessárias alterações de DNS ou de certificado. No entanto, sempre que você altera um nome de URL simples, deve executar <strong>Enable-CsComputer</strong> em cada Diretor e Servidor Front-End para registrar a alteração.

## Consulte Também

#### Conceitos

[Planejamento de URLs simples no Lync Server 2013](lync-server-2013-planning-for-simple-urls.md)

