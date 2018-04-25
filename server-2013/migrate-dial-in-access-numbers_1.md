---
title: Migrar números de acesso discado
TOCTitle: Migrar números de acesso discado
ms:assetid: 568a94b7-a697-4ab2-9008-dc9ecc1c87c8
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204898(v=OCS.15)
ms:contentKeyID: 49306755
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Migrar números de acesso discado

 

_**Tópico modificado em:** 2012-09-26_

A migração dos números de acesso de discagem requer duas etapas: execução do cmdlet **Import-CsLegacyConfiguration** concluído anteriormente em [Importar políticas e configurações](import-policies-and-settings.md)) para migrar planos de discagem e outras configurações de número de acesso de discagem, e execução do cmdlet **Move-CsApplicationEndpoint** para migrar os objetos de contato.

## Para migrar os números de acesso de discagem

1.  Abra a ferramenta administrativa do Office Communications Server 2007 R2.

2.  Na árvore do console, clique com o botão direito do mouse no nó de floresta, clique em **Propriedades** e, em seguida, clique em **Propriedades do Atendedor de Conferência** .

3.  Na guia **Números de Telefone de Acesso** , clique em **Atendido pelo Pool** para classificar os números de telefone de acesso pelo pool associado e identificar todos os números de acesso para o pool a partir do qual você está migrando.

4.  Para identificar URI do SIP para cada número de acesso de discagem, clique duas vezes no número de acesso para abrir a caixa de seleção **Editar Número do Atendedor de Conferência** e verifique **URI do SIP** .

5.  Abra o Shell de Gerenciamento do Lync Server.

6.  Para move cada número de acesso de discagem para um pool hospedado no Lync Server 2013, execute:
    
        Move-CsApplicationEndpoint -Identity <SIP URI of the access number to be moved> -Target <FQDN of the pool to which the access number is moving>

7.  Na ferramenta administrativa do Office Communications Server 2007 R2, na guia **Números de Telefone de Acesso** , verifique se os números de acesso de discagem permanecem no pool do Office Communications Server 2007 R2 a partir do qual você está migrando.

