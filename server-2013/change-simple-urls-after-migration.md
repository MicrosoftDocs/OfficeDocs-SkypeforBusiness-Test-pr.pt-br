---
title: Alterar URLs simples após migração
TOCTitle: Alterar URLs simples após migração
ms:assetid: addb0dc8-8324-42b1-9a00-f4bd14fdf5c0
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ721844(v=OCS.15)
ms:contentKeyID: 49886361
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Alterar URLs simples após migração

 

_**Tópico modificado em:** 2012-09-22_

O Lync Server suporta três URLs simples:

  - **Reunião** é usado como URL de base para todas as conferências no site ou na organização. Com Reunião, é possível compreender, comunicar e distribuir facilmente URLs simples e links para participar de reuniões.

  - **Discar** permite o acesso à página de Configurações de conferência discada. A URL simples discado é incluído em todos os convites de reunião para que os usuário que desejam discar para a reunião possam acessar o número de telefone e as informações de PIN necessárias.

  - **Admin** permite o acesso rápido ao Painel de Controle do Lync Server. A URL simples de Admin é parte interna da sua organização.

Depois de migrar para o Lync Server 2013, você deve estar ciente do impacto da mudança em seus registros de DNS e certificados para URLs simples. Se o Diretor herdado do Lync Server 2010 permanecer em uso na topologia, não é necessário alterar suas URLs simples. Se o Diretor do Lync Server 2010 for removido da topologia depois da migração, os registros de DNS simples da URL devem ser atualizados para que apontem para um dos pools do Lync Server 2013. No entanto, se você alterar um nome de URL simples, é necessário executar Enable-CsComputer em cada Diretor e Servidor Front-End para registrar a alteração.

## Alterando URLs simples após a migração

**Para atualizar a URL simples de Reunião**

1.  No Construtor de Topologias, clique com o botão direito no nó superior do **Lync Server** e em **Editar propriedades** .

2.  Selecione **URLs simples** no painel esquerdo, em seguida, abaixo de **URLs de reunião:** selecione a URL de Reunião e clique em **Editar URL** .

3.  Atualize a URL para o valor desejado e clique em **OK** para salvar a URL editada.

**Para atualizar a URL simples de Admin**

1.  No Construtor de Topologias, clique com o botão direito no nó superior do **Lync Server** e em **Editar propriedades** .

2.  Selecione **URLs simples** no painel esquerdo, em seguida, abaixo da caixa **URL de acesso administrativo** , insira a URL simples que deseja como acesso administrativo para o Painel de Controle do Lync Server 2013 e clique em **OK** .
    

    > [!TIP]  
    > Recomendamos usar a URL mais simples possível para a URL Admin. A opção mais simples é <STRONG>https://admin.</STRONG> <EM>&lt;domain&gt;</EM> .



## Consulte Também

#### Conceitos

[Planejamento de URLs simples no Lync Server 2013](lync-server-2013-planning-for-simple-urls.md)

