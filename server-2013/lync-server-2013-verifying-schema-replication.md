---
title: 'Lync Server 2013: Verificando a replicação de esquema'
TOCTitle: Verificando a replicação de esquema
ms:assetid: ad01a7cf-aa79-4648-ba5a-a7a09172db36
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg412822(v=OCS.15)
ms:contentKeyID: 49307778
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Verificando a replicação de esquema do Active Directory no Lync Server 2013

 

_**Tópico modificado em:** 2012-10-29_

Antes de executar a preparação da floresta, verifique manualmente se a partição do esquema foi replicada.

## Para verificar manualmente a replicação do esquema

1.  Faça logon no controlador de domínio como membro do grupo Administradores de Empresa.

2.  Abra o Editor ADSI clicando em **Iniciar** , **Ferramentas Administrativas** e em **Editor ADSI** .
    

    > [!TIP]  
    > Se desejar, você pode executar <STRONG>adsiedit.msc</STRONG> na linha de comando.



3.  Na árvore do Console de Gerenciamento Microsoft (MMC), se já não estiver selecionado, clique em **Editor ADSI** .

4.  No menu **Ação** , clique em **Conectar-se a** .

5.  Na caixa de diálogo **Configurações de Conexão** em **Selecione um Contexto de Nomenclatura bem conhecido** , selecione **Esquema** e clique em **OK** .

6.  No contêiner de esquema, pesquisa por CN=ms-RTC-SIP-SchemaVersion. Se esse objeto existir e o valor do atributo **rangeUpper** for 1150 e o valor de **rangeLower** for 3, então o esquema foi atualizado e replicado com êxito. Se esse objeto não existe ou os valores dos atributos **rangeUpper** e **rangeLower** são forem especificados, então o esquema não foi modificado ou replicado.

## Consulte Também

#### Tarefas

[Executando preparação de esquema de Active Directory no Lync Server 2013](lync-server-2013-running-schema-preparation.md)  

#### Conceitos

[Preparando o esquema do Active Directory no Lync Server 2013](lync-server-2013-preparing-the-active-directory-schema.md)

