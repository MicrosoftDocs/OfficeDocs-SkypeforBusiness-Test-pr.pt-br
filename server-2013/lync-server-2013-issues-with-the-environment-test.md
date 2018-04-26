---
title: Problemas com o teste de ambiente
TOCTitle: Problemas com o teste de ambiente
ms:assetid: ff1fe0d3-35b2-41ef-87e7-6a61e9e1d2ca
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205421(v=OCS.15)
ms:contentKeyID: 49308722
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Problemas com o teste de ambiente

 

_**Tópico modificado em:** 2012-09-21_

O analisador de práticas recomendadas oferece uma forma de verificar se seu ambiente de Lync Server 2013 é uma configuração suportada. Como parte da verificação de Serviços de Domínio do Active Directory, o analisador de práticas recomendadas realiza as seguintes tarefas:

  - Verifica os Serviços de Domínio Active Directory em preparo de esquema e floresta.

  - Identifica o número dos sites e domínios dos Serviços de Domínio Active Directory na implantação.

  - Verifica os níveis de floresta e domínio.

  - Verifica a versãod o controlador de domínio.

  - Identifica o domínio, a configuração e contexto de nomenclatura de esquema.

  - Identifica o número de usuários habilitados.

  - Verifica onde as definições globais dos Serviços de Domínio Active Directory estão armazenadas.

  - Verifica os pontos de conexão de serviço (SCPs) para Lync Server.

  - Identifica a versão do banco de dados.

## Resolve problemas com oambiente

Se o teste de ambiente encontrou problemas com seu ambiente, esses problemas são provavelmente causados por problemas com sua configuração do Active Directory ou o nível do software executando em servidores específicos. Por exemplo, se o analisador de práticas recomendadas identificar quaisquer controladores de domínio em seu ambiente executando Windows Server 2000, ele emitirá o aviso e você deverá atualizar os controladores de domínio para uma versão suportada do Windows Server.

