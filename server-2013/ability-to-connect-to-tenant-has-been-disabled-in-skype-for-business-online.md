---
title: A capacidade de se conectar ao locatário foi desabilitada
TOCTitle: A capacidade de se conectar ao locatário foi desabilitada
ms:assetid: 7365d31b-173e-4339-b0a3-98ab73a9558f
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn362820(v=OCS.15)
ms:contentKeyID: 56270430
ms.date: 06/02/2017
mtps_version: v=OCS.15
ms.translationtype: HT
---

# A capacidade de se conectar ao locatário foi desabilitada

 

_**Tópico modificado em:** 2015-06-22_

Para usar o Windows PowerShell para gerenciar o Skype for Business Online, a propriedade EnableRemotePowerShellAccess da política do Windows PowerShell do seu locatário deve ser definida como Verdadeira. Se isso não for feito, sua conexão falhará e você receberá a seguinte mensagem de erro:

    New-PSSession : [admin.vdomain.com] Falha ao processar dados do servidor remoto admin.vdomain.com com a seguinte mensagem de erro: A capacidade para se conectar a esse locatário usando uma sessão remota PowerShell session foi desativada. Contacte a Ajuda do Lync para verificar a Política de Locatário Powershell desse locatário. Para mais informações, consulte o tópido Ajuda about_Remote_Troubleshooting Help topic.

Se você vir essa mensagem de erro, precisará contatar o Suporte do Office 365 e habilitar o acesso remoto do Windows PowerShell.

## Consulte Também

#### Conceitos

[Diagnosticando e resolvendo problemas de conexão com o Lync Online](diagnosing-and-resolving-connection-problems-with-skype-for-business-online.md)

