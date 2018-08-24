---
title: Configurando o repositório para arquivamento
TOCTitle: Configurando o repositório para arquivamento
ms:assetid: f751245c-743e-454f-8325-968ae5e3de71
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205392(v=OCS.15)
ms:contentKeyID: 49308639
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurando o repositório para arquivamento

 

_**Tópico modificado em:** 2016-12-08_

O arquivamento do Lync Server 2013 inclui o seguinte:

  - **Armazenamento de dados**   O armazenamento de dados é necessário para armazenar o conteúdo de IM.

  - **Armazenamento de arquivos**   O armazenamento de arquivos é necessário para armazenar o conteúdo de dados e arquivos das conferências (reuniões).

## Configurando o armazenamento de dados

Os requisitos de configuração do armazenamento de dados no Lync Server 2013 dependem de como você deseja armazenar os dados:

  - Integre o arquivamento do Lync Server 2013 à sua implantação do Exchange para armazenar dados usando o armazenamento do Exchange.

  - Defina servidores de banco de dados do SQL Server para armazenar os dados.

## Configurando o repositório do Exchange para arquivamento de dados

A configuração do repositório do Exchange para arquivamento de dados requer que a implantação do Exchange execute o Exchange 2013. Além disso, as caixas de correio dos usuários devem estar hospedadas no servidor Exchange 2013 e as caixas de correio devem ser colocadas em espera no local. Para obter mais informações sobre como configurar o Exchange 2013, consulte a documentação do produto do Exchange.

## Configurando o repositório dos Servidores de banco de dados do SQL Server para arquivamento de dados

O arquivamento no Lync Server 2013 requer o software de banco de dados do SQL Server para armazenar os dados arquivados, a não ser que você integre sua implantação ao Exchange.

Para bancos de dados de arquivamento do SQL Server, você deve instalar o SQL Server no computador que hospedará o banco de dados de arquivamento. É possível usar a mesma instância do SQL utilizada para o banco de dados de back-end de um pool de Front Ends. Para obter um melhor desempenho, você deve implantar o banco de dados de arquivamento em um computador separado do armazenamento de Gerenciamento Central. Para obter mais informações sobre como colocar componentes do Lync Server 2013, consulte [Colocação em conjunto de servidor suportado no Lync Server 2013](lync-server-2013-supported-server-collocation.md) na documentação de Suporte.

Cada servidor de banco de dados deve ser executado em uma versão suportada do SQL Server. Para obter detalhes sobre as versões suportadas, consulte [Requisitos técnicos de Arquivamento no Lync Server 2013](lync-server-2013-technical-requirements-for-archiving.md) na documentação de Planejamento.

Você deve configurar as plataformas do SQL Server antes de implantar e habilitar o arquivamento. Se a conta utilizada para publicar a topologia tiver os direitos e permissões apropriados, é possível criar o banco de dados de arquivamento (LcsLog) ao publicar a topologia. Também é possível criar o banco de dados posteriormente, incluindo-o como parte do procedimento de instalação. Para obter mais informações sobre o SQL Server, consulte o SQL Server TechCenter em [http://go.microsoft.com/fwlink/?linkid=129045\&clcid=0x416](http://go.microsoft.com/fwlink/?linkid=129045%26clcid=0x416).

> [!NOTE]  
> Certifique-se de que o Tipo de inicialização do Serviço SQL Server Agent é Automático e que o Serviço SQL Server Agent está executando a Instância SQL que mantém o Banco de dados de arquivamento, para que o Trabalho de Manutenção Padrão do SQL Server de Arquivamento seja executado de forma agendada sob controle do Serviço SQL Server Agent.

## Configurando o armazenamento de arquivos

O arquivamento usa o compartilhamento de arquivos do Lync Server 2013 especificado ao configurar o pool de Front Ends ou o servidor Edição Padrão. Não é possível alterar o compartilhamento de arquivos usado para o Arquivamento. Para obter mais informações sobre os sistemas de armazenamento de arquivos suportados, consulte [Suporte a armazenamento de arquivo no Lync Server 2013](lync-server-2013-file-storage-support.md) na documentação de Suporte.

