---
title: 'Lync Server 2013: Configurar criptografia de mídia para fornecedores públicos'
TOCTitle: Configurar criptografia de mídia para fornecedores públicos
ms:assetid: a95814cf-c5a9-4652-8ffc-c469a2653153
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205149(v=OCS.15)
ms:contentKeyID: 49307740
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurar criptografia de mídia para fornecedores públicos no Lync Server 2013

 

_**Tópico modificado em:** 2014-12-12_

Para obter detalhes sobre requisitos de licenciamento e como concluir o processo de provisionamento, consulte o "Guia de Provisionamento de IM Público para Microsoft Lync Server, Office Communications Server e Live Communications Server" em [http://go.microsoft.com/fwlink/p/?linkId=155970](http://go.microsoft.com/fwlink/p/?linkid=155970)

Se estiver implementando federação de áudio/vídeo (A/V) com o Windows Live Messenger, há dois parâmetros que você precisará modificar: o nível de criptografia do Lync Server e a política EnablePublicCloudAccess. Como padrão, o nível de criptografia está definido como Obrigatório. Você deve mudar esse nível para Suportado. Se a política EnablePublicCloudAccess está definida como "false", ela precisa ser alterada para **True** . Isso pode ser feito a partir do Shell de Gerenciamento do Lync Server.

> [!IMPORTANT]  
> Mais do que nunca, o Lync é uma ferramenta poderosa para conexões com organizações e indivíduos ao redor do mundo. A federação com o Windows Live Messenger não requer licenças de usuário/dispositivo adicionais além da Licença de Acesso Padrão do Cliente Lync (CAL). No próximo ano, a federação do Skype será adicionada à lista, permitindo que os usuários Lync contatem milhões de pessoas via IM e voz.

## Configurar a federação para Windows Live

1.  Inicie o Shell de Gerenciamento do Lync Server no servidor de front end: Clique em **Iniciar** , clique em **Todos os Programas** , em **Microsoft Lync Server 2013**, e depois em **Shell de Gerenciamento do Lync Server**.

2.  No prompt de comando, digite os comandos a seguir:
    
    ```
        Set-CsMediaConfiguration -EncryptionLevel SupportEncryption
    ```
    ```    
        Set-CsExternalAccessPolicy Global -EnablePublicCloudAccess $true -EnablePublicCloudAudioVideoAccess $true
    ```
    
    > [!NOTE]  
    > Esta etapa é obrigatória pois o Windows Live Messenger não suporta criptografia de áudio/vídeo. O comando define sua política global para suportar uma criptografia em vez de exigir criptografia de dados de áudio/vídeo. Os clientes que suportam criptografia ainda usarão a criptografia, como o Lync 2013
