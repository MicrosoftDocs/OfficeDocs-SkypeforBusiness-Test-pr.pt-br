---
title: 'Lync Server 2013: Requisitos técnicos do Servidor de Chat Persistente'
TOCTitle: Requisitos técnicos do Servidor de Chat Persistente
ms:assetid: 692b7d99-1bc9-4c99-a050-2bc2be8688b2
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398495(v=OCS.15)
ms:contentKeyID: 49306989
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Requisitos técnicos do Servidor de Chat Persistente no Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

Cada computador que hospeda o Servidor de Chat Persistente deve ter acesso a uma topologia existente do Lync Server 2013 com os seguintes componentes:

  - **Lync Server 2013, Servidor Front-End.** O Servidor Front-End é a base para o encaminhamento SIP, que possibilita a comunicação entre os computadores que executam o Servidor de Chat Persistente e a funcionalidade do Chat Persistente. Antes de começar a implantar o Servidor de Chat Persistente, verifique a implantação do Lync Server 2013 Standard Edition ou de um Lync ServerPool de Front-Ends e de qualquer outro computador interno que executa o Lync Server, conforme apropriado para sua organização.

As seções a seguir descrevem os requisitos específicos do Servidor de Chat Persistente e do banco de dados que armazena os dados do Chat Persistente.

## Requisitos do Servidor de Chat Persistente

Para obter detalhes sobre o hardware recomendado para a implantação do Lync Server e da versão mais recente do Servidor de Chat Persistente, consulte [Plataformas de hardware de servidor para Lync Server 2013](lync-server-2013-server-hardware-platforms.md) na documentação de suporte.

Para obter detalhes sobre o servidor e as ferramentas a que o sistema operacional oferece suporte para o Lync Server e o Servidor de Chat Persistente, consulte [Suporte a sistemas operacionais de servidor e de ferramentas no Lync Server 2013](lync-server-2013-server-and-tools-operating-system-support.md) na documentação de suporte.

Para obter detalhes sobre o software adicional necessário para a implantação do Servidor de Chat Persistente, consulte a tabela a seguir.

### Pré-requisitos de software do Servidor de Chat Persistente

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Software</th>
<th>Descrição</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Serviço de Enfileiramento de Mensagens</p></td>
<td><p>Usado pelo Serviço de Conformidade do Servidor de Chat Persistente e do Chat Persistente (se implantado).</p></td>
</tr>
</tbody>
</table>


## Requisitos de banco de dados do Servidor de Chat Persistente

O Servidor de Chat Persistente usa o banco de dados do Chat Persistente para armazenar o histórico do chat, a configuração e os dados de provisionamento de usuário. Opcionalmente, ele usa o banco de dados de conformidade do Chat Persistente para armazenar os dados de conformidade.

> [!IMPORTANT]  
> O banco de dados do Chat Persistente (mgc) e o banco de dados de conformidade (mgccomp) podem estar localizados na mesma instância do SQL Server ou em SQL Servers diferentes.

Para preparar uma plataforma de servidor de banco de dados, verifique se cada computador atende aos requisitos de hardware e instale o software necessário.

A plataforma de servidor para os servidores de banco de dados do Chat Persistente exige o mesmo hardware que o servidor de banco de dados Back-End do Lync Server. Para obter detalhes, consulte [Plataformas de hardware de servidor para Lync Server 2013](lync-server-2013-server-hardware-platforms.md) na documentação de suporte.

No servidor de banco de dados. verifique se um dos seguintes aplicativos de software está instalado:

  - Microsoft SQL Server 2012. Para obter detalhes sobre como instalar o Microsoft SQL Server 2012, consulte "Instalar o SQL Server 2012" em [http://go.microsoft.com/fwlink/p/?LinkID=248559](http://go.microsoft.com/fwlink/p/?linkid=248559).

  - Microsoft SQL Server 2008 R2. Para obter detalhes sobre como instalar o Microsoft SQL Server 2008 R2, consulte "Instalação do SQL Server (SQL Server 2008 R2)" em [http://go.microsoft.com/fwlink/?LinkId=275702](http://go.microsoft.com/fwlink/?linkid=275702).

## Requisitos de certificado do Servidor de Chat Persistente

Para obter detalhes sobre a aquisição de certificados, criação do banco de dados do SQL Server e criação dos repositórios de arquivos, consulte [Implantando o Lync Server 2013](lync-server-2013-deploying-lync-server.md) na documentação de Implantação.

