---
title: Configurações da política de grupo para o Lync 2013
TOCTitle: Configurações da política de grupo para o Lync 2013
ms:assetid: 5917a52b-dae0-4ec0-8548-a68dc20ab71c
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204924(v=OCS.15)
ms:contentKeyID: 49306800
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurações da política de grupo para o Lync 2013

 

_**Tópico modificado em:** 2016-12-08_

Nas versões anteriores do Lync e do Office Communicator, um modelo administrativo do Communicator.adm autônomo estava disponível para definir as configurações da política de grupo do cliente. Para o Lync 2013, novos arquivos de modelo administrativo (arquivos .admx e .adml) estão incluídos com o Modelo administrativo da política de grupo do Office. A disponibilidade dos arquivos .admx e .adml do Lync 2013 permite que você faça download dos modelos e gerencia de forma central as configurações da política de grupo para todos os programas e pacotes de idioma do seu Office. Para obter detalhes, consulte “Arquivos de modelo administrativo do Office 2013 (ADMX, ADML)” na documentação do Office 2013 em [http://go.microsoft.com/fwlink/?linkid=267516\&clcid=0x416](http://go.microsoft.com/fwlink/?linkid=267516%26clcid=0x416).

## Políticas de inicialização do cliente

Há várias políticas de inicialização do cliente que você deve configurar antes de os usuários entrarem no servidor pela primeira vez. Como essas políticas entram em vigor antes de o cliente entrar e começar a receber as configurações de provisionamento em banda do servidor, é possível usar a política de grupo para configurá-las. Para obter mais informações, consulte [Configurando políticas de bootstrap de cliente no Lync Server 2013](lync-server-2013-configuring-client-bootstrapping-policies.md) na Documentação de implantação.

