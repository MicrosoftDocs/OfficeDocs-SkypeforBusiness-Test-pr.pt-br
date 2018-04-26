---
title: Configurando plataformas do sistema para arquivamento
TOCTitle: Configurando plataformas do sistema para arquivamento
ms:assetid: 2df40fdf-0e32-46d4-9fb2-1ce1d7bfa328
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204768(v=OCS.15)
ms:contentKeyID: 49306250
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurando plataformas do sistema para arquivamento

 

_**Tópico modificado em:** 2012-10-09_

Antes de iniciar a implantação do Arquivamento, você deve instalar o sistema operacional necessário e qualquer outro software pré-requisito no hardware que atende os requisitos do sistema:

  - A plataforma **Lync Server 2013**   Implantações do Lync Server 2013 não possuem Servidores de Arquivamento, Agentes de Coleta de Dados Unificados executando em Servidores de Front-End e servidores do Standard Edition para capturar dados para arquivamento. Portanto, nenhuma plataforma do sistema separada é necessária para hospedar o Arquivamento.

  - **Plataforma de armazenamento de dados**   No Lync Server 2013, é possível armazenar dados usando um dos seguintes:
    
      - Integração do **Microsoft Exchange**   Se você deseja armazenar os dados de arquivamento do Lync Server 2013 usando sua implantação do Exchange 2013, ao invés ou além de configurar um banco de dados separado para armazenamento dos dados de Arquivamento, sua implantação do Exchange deve estar executando o Exchange 2013. Para obter detalhes sobre a configuração de plataformas do sistema para Exchange 2013, consulte a documentação do produto Exchange.
    
      - **SQL Server**   Se você deseja usar um banco de dados do SQL Server separado para armazenamento dos dados de arquivamento, ao invés ou além de usar a integração do Microsoft Exchange, você deve configurar a plataforma do sistema para o banco de dados antes da implantação do Arquivamento. Os requisitos da plataforma do sistema específicos depende se você deve usar o Microsoft SQL Server 2008 R2 ou o Microsoft SQL Server 2012 para o banco de dados de Arquivamento. Para obter detalhes sobre a configuração de plataformas do sistema para os bancos de dados, consulte o Microsoft SQL Server 2008 R2 e a documentação do produto Microsoft SQL Server 2012.

  - **Plataforma do servidor de arquivos**   O Lync Server 2013 armazena arquivos de arquivamento do Lync Server no mesmo local que você especifica para o armazenamento de arquivos ao configurar seus Servidores de Front-End ou servidores do Standard Edition. Não é possível especificar um local separado para armazenamento de arquivo. Portanto, nenhuma plataforma do sistema separado é necessária para o armazenamento de arquivos. Se você usar a integração do Microsoft Exchange, Exchange 2013 os arquivos para as comunicações do Lync arquivadas são armazenados nos servidores do Exchange 2013 para usuários hospedados nestes servidores do Exchange.

