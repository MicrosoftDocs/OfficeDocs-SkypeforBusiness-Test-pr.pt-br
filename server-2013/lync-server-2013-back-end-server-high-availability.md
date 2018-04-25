---
title: 'Lync Server 2013: Alta disponibilidade do Servidor Back-End'
TOCTitle: Alta disponibilidade do Servidor Back-End
ms:assetid: c559aacb-4e1d-4e78-9582-41f966ad418d
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205248(v=OCS.15)
ms:contentKeyID: 49308047
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Alta disponibilidade do Servidor Back-End no Lync Server 2013

 

_**Tópico modificado em:** 2013-08-12_

Para garantir a alta disponibilidade dos Servidores Back-End, é possível usar o espelhamento SQL sincronizado ou o agrupamento SQL, como solução opcional, mas recomenda-se que se mantenha a continuidade de negócio da sua organização. O espelhamento SQL dessincronizado não é suportado pela alta disponibilidade do Servidor de Back-End no Lync Server 2013. No restante do documento, o espelhamento do SQL é sincronizado, a menos que o contrário seja explicitamente afirmado.

É possível configurar o espelhamento SQL facilmente com o Construtor de Topologias. Para failover de agrupamento de SQL, use o servidor SQL para configurações.

Ao usar tanto o espelhamento quanto o agrupamento de SQL em um pool pareado com outro, de Front-End, para a recuperação de desastre, é preciso usar a mesma solução de alta disponibilidade do Back-End em ambos os pools. Não é recomendado parear um pool usando um espelhamento SQL com um pool usando agrupamento SQL.

Quando se implementa o espelhamento SQL, todas as bases de dados Lync Server no pool são espelhadas, incluindo o Repositório de Gerenciamento Central, se este estiver localizado neste pool, assim como as bases de dados dos aplicativos do Grupo de Resposta e do Estacionamento de Chamadas, caso estes estejam sendo executados em um pool.

Com o espelhamento SQL, você não precisa usar o armazenamento compartilhado para servidores. Cada servidor mantém sua cópia dos bancos de dados no armazenamento local.

Você pode escolher implantar espelhamento SQL com ou sem uma testemunha. Recomendamos usar uma testemunha porque habilita o failover do Servidor de Back-End como automático. De outra forma, um administrador deve invocar manualmente o failover. Observe que mesmo se uma testemunha é implantada, um administrador pode invocar manualmente o failover do Servidor de Back-End, se necessário.

Se você usar uma testemunha, é possível utilizar uma única testemunha para vários pares de Servidores de Back-End. Não há correspondência exata entre testemunhas e pares de Servidores de Back-End. As implantações usam uma única testemunha para vários pares de Servidores de Back-End não são tão resilientes quanto topologias com uma testemunha separada para cada par de Servidor de Back-End.

Para saber mais sobre suporte de agrupamento SQL, veja [Suporte a software de banco de dados no Lync Server 2013](lync-server-2013-database-software-support.md). Para saber mais sobre implantação de agrupamento de SQL, veja [Configurar Agrupamento do SQL Server para Lync Server 2013](lync-server-2013-configure-sql-server-clustering.md).

## Tempo de Recuperação para failover do Servidor de Back-End Automático

Para failover automático do Back-End com espelhamento SQL, a meta de engenharia para o tempo de recuperação do objeto (RTO) é de 5 minutos. Como o espelhamento SQL é sincronizado, não antecipamos a perda de dados durante as falhas do servidor de Back-End, exceto em raras ocasiões em que tanto o Servidor Front-End quanto o Back-End sejam carregados simultaneamente enquanto os dados são movidos entre os servidores. A meta de engenharia para o objetivo do ponto de recuperação (RPO) é de 5 minutos.

## Experiência do Usuário Durante Falha do Servidor Back-End com Espelhamento SQL

Experiência do usuário durante uma falha depende da natureza falha e da sua topologia.

Se você usa o espelhamento SQL e tem uma testemunha configurada, e o servidor principal falhar, o failover do Servidor Back-End é executado rápida e automaticamente. Os usuários ativos não devem notar a interrupção em suas sessões contínuas.

Se não há uma testemunha configurada, pode levar algum tempo para o administrador invocar manualmente o failover. Durante este tempo, os usuários ativos podem ser afetados. Eles continuam suas sessões normalmente por cerca de 30 minutos. Se o diretor ainda não for restaurado ou um administrador não tiver um failover para o backup, os usuários são trocados para o modo Resiliência, significando que não poderão realizar tarefas que exigem uma mudança persistente no Lync Server (como adicionar um contato).

Se o diretor e o Servidor de Back-End espelho falharem ou se um destes servidores e a testemunha falharem, o Servidor de Back-End se tornará indisponível (mesmo se o diretor ainda estiver funcionando). Neste caso, os usuários ativos são mudados para o modo Resiliência após algum tempo.

