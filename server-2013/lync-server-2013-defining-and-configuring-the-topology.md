---
title: 'Lync Server 2013: Definindo e configurando a topologia'
TOCTitle: Definindo e configurando a topologia
ms:assetid: 51d1601e-4f83-48d4-ad08-3b4d5e2003aa
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398339(v=OCS.15)
ms:contentKeyID: 49306712
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Definindo e configurando a topologia no Lync Server 2013

 

_**Tópico modificado em:** 2012-09-14_

Você define e configura a topologia usando o Construtor de Topologias. O Construtor de Topologias não exige que você seja membro do grupo Administradores local nem de um grupo de domínio privilegiado (como Admins. do Domínio). Você pode definir a topologia como um usuário padrão. Quando você inicia o Construtor de Topologias para a primeira utilização e nas sessões de edição subsequentes, é solicitado o local onde você deseja que o Construtor de Topologias carregue o documento de configuração atual. As opções são:

  - Baixar a topologia da implantação existente

  - Abrir a topologia de um arquivo local

  - Nova topologia

Se você já definiu uma topologia e estabeleceu o Repositório de Gerenciamento Central, deve baixar uma topologia de uma implantação existente. O Construtor de Topologias lerá o banco de dados e recuperará a definição atual. Se você tiver um Repositório de Gerenciamento Central existente, sempre deverá escolher esta opção.

Se você não estabeleceu um Repositório de Gerenciamento Central e deseja editar uma configuração salva anteriormente, deve escolher abrir a topologia de um arquivo local. O arquivo que será aberto seria o arquivo de configuração salvo em uma sessão anterior. Você pode usar esta opção para editar a topologia salva anteriormente.


> [!WARNING]  
> Se você já tem uma topologia publicada, não deve carregar um arquivo de configuração local. Você deve baixar topologia de uma implantação existente.



Escolha para criar uma nova topologia, quando você deseja criar uma nova configuração de Construtor de Topologias. Um projeto salvo anteriormente não é substituído, a menos que você escolha salvá-lo como o mesmo arquivo criado em uma sessão anterior do design.

Em cada uma dessas opções, um local será solicitado para armazenar o arquivo de configuração de Construtor de Topologias. O local do arquivo poderia ser local, um local compartilhado em um compartilhamento de arquivos estabelecido ou uma mídia removível.

## Nesta seção

  - [Definir e configurar uma topologia no Construtor de Topologia para Lync Server 2013](lync-server-2013-define-and-configure-a-topology-in-topology-builder.md)

  - [Definir e configurar um pool Front-End ou um servidor Standard Edition no Lync Server 2013](lync-server-2013-define-and-configure-a-front-end-pool-or-standard-edition-server.md)

  - [Implantando pools Front-End emparelhados para recuperação de desastre no Lync Server 2013](lync-server-2013-deploying-paired-front-end-pools-for-disaster-recovery.md)

  - [Implantando espelhamento SQL para alta disponibilidade de Servidor Back-End no Lync Server 2013](lync-server-2013-deploying-sql-mirroring-for-back-end-server-high-availability.md)

  - [Editar ou configurar URLs simples no Lync Server 2013](lync-server-2013-edit-or-configure-simple-urls.md)

  - [Selecionar o Servidor de Gerenciamento Central no Lync Server 2013](lync-server-2013-select-the-central-management-server.md)

