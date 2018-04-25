---
title: Práticas recomendadas para backup e restauração
TOCTitle: Práticas recomendadas para backup e restauração
ms:assetid: abbce0e4-973a-4624-a0c1-e0f22e1d348b
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Hh202184(v=OCS.15)
ms:contentKeyID: 52057683
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Práticas recomendadas para backup e restauração

 

_**Tópico modificado em:** 2013-02-21_

Esta seção inclui dois tipos de melhores práticas:

  - Melhores práticas para backup e restauração.

  - Melhores práticas para minimizar o impacto de um desastre.

## Melhores práticas para backup e restauração

Para facilitar seu processo de backup e restauração, aplique as seguintes melhores práticas ao fazer backup ou restaurar seus dados:

  - Execute backups regulares em intervalos adequados. O tipo de backup e agendamento rotativo mais simples e mais comumente usado é o backup noturno completo de todo o banco de dados do SQL Server. Assim, se for necessário executar uma restauração, o processo exigirá somente um backup e dados e não se poderá perder mais do que os dados referentes a um dia.

  - Se você usa cmdlets ou o Painel de Controle do Lync Server para fazer alterações na configuração, use o cmdlet **Export-CsConfiguration** para fazer um backup instantâneo do arquivo de configuração da topologia (Xds.mdf) depois de fazer as alterações, para não perdê-las se for necessário restaurar seus bancos de dados. Observe que é feito um backup dessa configuração em formato XML e esse backup é comprimido em formato ZIP.

  - Certifique-se de que a pasta compartilhada que planeja usar para fazer backup do Lync Server tem espaço em disco suficiente para armazenar todos os dados de backup.

  - Agende backups quando o uso do Lync Server for rotineiramente baixo, para melhorar o desempenho do servidor e a experiência do usuário.

  - Certifique-se que o local em que você realiza backup dos dados é seguro (recomendamos um local remoto).

  - Mantenha os arquivos de backup onde permanecerão disponíveis caso seja necessário restaurar os dados.

  - Planeje e agende testes periódicos dos processos de restauração suportados pela sua organização.

  - Valide os processos de backup e restauração antecipadamente para garantir que eles funcionem conforme o esperado.

## Melhores práticas para minimizar o impacto de um desastre

A melhor estratégia para lidar com interrupções de serviço desastrosas (causadas por eventos incontroláveis, como quedas de energia ou falhas de hardware repentinas) é assumir que elas acontecerão e planejar de acordo.

Se os serviços Lync, com um mínimo de distúrbio e interrupção, são corporativamente essenciais para sua organização, você deve considerar a implementação de pools de servidores Front End emparelhados entre si, como descrito em [Planejamento para alta disponibilidade e recuperação de desastre no Lync Server 2013](lync-server-2013-planning-for-high-availability-and-disaster-recovery.md). Assim, se um desses pools passar por um desastre, um administrador pode alternar o acesso dos usuários, de modo que os usuários desse pool sejam atendidos pelo outro, com um mínimo de tempo de inatividade.

Os planos de gerenciamento de desastres desenvolvidos como parte da sua estratégia de backup e restauração devem incluir:

  - Manter sua mídia de software e suas atualizações de software e de firmware facilmente disponíveis.

  - Manter registros de hardware e software.

  - Fazer backup de seus dados regularmente e monitorar a integridade dos backups.

  - Treinar sua equipe em recuperação de desastres, procedimentos de documentação e implementar exercícios de simulação de recuperação de desastres.

  - Manter hardware sobressalente disponível ou, se houver um contrato de nível de serviço (SLA), estabelecer contrato com fornecedores de hardware para reposições imediatas.

  - Separar a localização dos seus arquivos de log de transações (arquivos .ldf) e arquivos de banco de dados (arquivos .mdf).

