---
title: Fazendo backup de repositórios de arquivos
TOCTitle: Fazendo backup de repositórios de arquivos
ms:assetid: 1a7f4e93-aa3d-461e-878e-2c572baa1293
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Hh202167(v=OCS.15)
ms:contentKeyID: 52057565
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Fazendo backup de repositórios de arquivos

 

_**Tópico modificado em:** 2013-02-17_

O backup dos Repositórios de Arquivos do Lync Server incluem todos os arquivos e pastas usados pelos componentes do Lync Server.

## Para fazer o backup dos Repositórios de Arquivos

1.  Para encontrar locais específicos do Repositório de Arquivos do Lync Server, abra o Construtor de Topologias e procure no nó **Repositórios de arquivos**.

2.  Utilize o Robocopy ou outra ferramenta de gerenciamento de sistema de arquivos para copiar cada Repositório de Arquivos para $Backup\\filestore.

