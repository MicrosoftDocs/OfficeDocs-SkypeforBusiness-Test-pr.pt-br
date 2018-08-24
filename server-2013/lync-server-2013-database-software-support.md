---
title: 'Lync Server 2013: Suporte a software de banco de dados'
TOCTitle: Suporte a software de banco de dados
ms:assetid: e05d0032-bbea-4e61-987d-d07b1c045fd5
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398990(v=OCS.15)
ms:contentKeyID: 49308365
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Suporte a software de banco de dados no Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

O Lync Server 2013 oferece suporte aos sistemas de gerenciamento do banco de dados a seguir:

  - **Banco de dados Back-end de um pool de Front-End, banco de dados de Arquivamento, banco de dados de Monitoramento, banco de dados de chat persistente e banco de dados de conformidade do chat persistente**
    
      - Software do banco de dados do Microsoft SQL Server 2008 R2 Enterprise (edição de 64 bits). Além disso, executar o service pack mais atual é recomendado.
    
      - Microsoft SQL Server 2008 R2 Standard (edição de 64 bits). Além disso, executar o service pack mais recente é recomendado.
    
      - Microsoft SQL Server 2012 Enterprise (edição de 64 bits). Além disso, executar o service pack mais recente é recomendado.
    
      - Microsoft SQL Server 2012 Standard (edição de 64 bits). Além disso, executar o service pack mais recente é recomendado.

  - **Banco de dados do servidor Standard Edition e banco de dados Servidor Front-End**
    
      - Microsoft SQL Server 2012 Express (edição de 64 bits). A execução adicional do service pack mais recente é recomendada
        
        Suportamos patch e atualização do Microsoft SQL Server em Servidores Front-End e em Servidores Standard Edition. No entanto, quando você faz qualquer tipo de atualização ou patch em Servidores Front-End, você deve considerar requisitos de quórum. Para mais informações, veja [Atualizar servidores Front End no Lync Server 2013](lync-server-2013-upgrade-or-update-front-end-servers.md) e [Topologias e componentes para Servidores Front-End, serviço de mensagens instantâneas e presença no Lync Server 2013](lync-server-2013-topologies-and-components-for-front-end-servers-instant-messaging-and-presence.md).
    
    > [!NOTE]  
    > O Microsoft SQL Server 2012 Express (64-bit edition) é instalado automaticamente pelo Lync Server 2013 em cada servidor Standard Edition e em cada servidor Servidor Front-End.

> [!IMPORTANT]  
> <ul>
> <li><p>O Lync Server 2013 não suporta a edição de 32 bits do SQL Server. Você deve usar a edição de 64 bits.</p></li>
> <li><p>O SQL Server Web Edition e o SQL Server Workgroup Edition não são suportados. Não é possível usá-los com o Lync Server 2013.</p></li>
> 
> <li><p>O Lync Server 2013 suporta espelhamento de banco de dados nativo.</p></li>
> 
> 
> <li><p>Para usar a função Monitoring Server, instale o Reporting Services do SQL Server.</p></li></ul>


Em um pool de front-end, o banco de dados de back-end pode ser um único computador SQL Server.

> [!IMPORTANT]  
> Se você posicionar bancos de dados do Lync Server com outros bancos de dados, recomendamos avaliar todos os fatores que podem afetar a disponibilidade e desempenho, assim como garantir que, se um nó falhar, o nó restante pode lidar com a carga. Para verificar as capacidades de failover, recomendamos o teste de todos os cenários de failover.

## Usando o espelhamento SQL e o cluster SQL

Lync Server 2013 suporta o uso do espelhamento SQL ou do cluster SQL para cada banco de dados do Lync Server. Você pode configurar facilmente o espelhamento SQL com a ferramenta Construtor de Topologias em Lync Server 2013. Para o cluster de failover SQK, você deve usar o SQL Server para a configuração.

O Lync Server 2013 oferece suporte às topologias de espelhamento do SQL e de clustering do SQL para todas as implantações, inclusive as inteiramente novas e as organizações que foram atualizadas a partir das versões anteriores do Lync Server.

O suporte do cluster SQL é para uma configuração ativa/passiva. Por motivos de desempenho, o nó passivo não deve ser compartilhado por nenhuma outra instância SQL.

O suporte a seguir é incluído:

  - Cluster de failover com dois nós para o seguinte:
    
      - Microsoft SQL Server 2012 Standard (edição de 64 bits). Além disso, executar o service pack mais recente é recomendado.
    
      - Microsoft SQL Server 2008 R2 Standard (edição de 64 bits). Além disso, executar o service pack mais recente é recomendado.

  - Cluster de failover com até 16 nós para o seguinte:
    
      - Microsoft SQL Server 2012 Enterprise (edição de 64 bits). Além disso, executar o service pack mais recente é recomendado.
    
      - Software do banco de dados do Microsoft SQL Server 2008 R2 Enterprise (edição de 64 bits). Além disso, executar o service pack mais atual é recomendado.

Para mais informações sobre o espelhamento SQL, consulte [Alta disponibilidade do Servidor Back-End no Lync Server 2013](lync-server-2013-back-end-server-high-availability.md). Para detalhes sobre como implantar o cluster SQL, consulte [Configurar Agrupamento do SQL Server para Lync Server 2013](lync-server-2013-configure-sql-server-clustering.md).

Para mais informações e melhores práticas para o cluster de failover no SQL Server 2012, consulte <http://technet.microsoft.com/pt-br/library/hh231721.aspx>. Para o cluster de failover no SQL Server 2008, consulte <http://technet.microsoft.com/pt-br/library/ms189134(v=sql.105).aspx>.

