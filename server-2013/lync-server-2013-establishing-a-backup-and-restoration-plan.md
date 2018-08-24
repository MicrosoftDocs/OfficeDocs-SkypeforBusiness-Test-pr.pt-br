---
title: Estabelecendo um plano de restauração e backup
TOCTitle: Estabelecendo um plano de restauração e backup
ms:assetid: 9f562ef1-3804-41e2-b3e4-d45b2e8c63c9
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Hh202183(v=OCS.15)
ms:contentKeyID: 52057660
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Estabelecendo um plano de restauração e backup

 

_**Tópico modificado em:** 2013-02-17_

Criar um plano de backup e restauração envolve as seguintes etapas:

  - Desenvolver o plano.

  - Implementar o plano.

  - Manter o plano.

## Como desenvolver um plano de backup e restauração

Depois de desenvolver sua estratégia de backup e restauração para o Lync Server, use-a para documentar um plano detalhado de backup e restauração. Seu plano deve transmitir claramente as prioridades e requisitos para fazer backup de dados e configurações. Você pode usar as informações em [Estabelecendo uma estratégia de restauração e backup](lync-server-2013-establishing-a-backup-and-restoration-strategy.md) e as planilhas em [Planilhas de backup e restauração](lync-server-2013-backup-and-restoration-worksheets.md) para facilitar a documentação da sua estratégia. Seu plano também deve conter critérios para decidir quando e como restaurar serviços.

Enquanto desenvolve seu plano, você precisa considerar, e reponsabilizar-se por, o seguinte:

  - Como recuperará servidores no novo hardware.

  - Como recuperará serviços que exigem ações da parte de várias áreas de negócio ou departamentos.

  - Como poderá obter servidores sobressalentes de forma rápida.

  - O tempo necessário para a recuperação usando sua estratégia. Considere as exigências da sua organização com relação ao objetivo de tempo de recuperação (RTO).

Modifique os procedimentos de backup e restauração neste tópico, adicionando-os e excluindo-os conforme o apropriado para refletir os servidores e componentes na sua implantação. Você também pode adicionar detalhes como a agenda do backup aos procedimentos adequados, para garantir que a informação não seja negligenciada.

> [!NOTE]  
> É boa prática criar scripts para tantas etapas quanto forem possíveis para ajudar a garantir a qualidade e a reprodutibilidade dos procedimentos.

Em seu plano, especifique quem será responsável por analisá-lo, testá-lo e pela validação de quaisquer procedimentos ou ferramentas novos e quem deve aprovar quaisquer mudanças no plano e procedimentos relacionados.

Para garantir que seu plano de backup e restauração atinja completamente todas as metas e prioridades estabelecidas, obtenha a aprovação dos tomadores de decisão corporativas e técnicas em sua organização antes de implementá-lo.

## Como implementar o plano de backup e restauração

Implementar um plano de backup e restauração exige as seguintes etapas:

  - Testar e validar o plano.

  - Comunicar o plano.

  - Validar as operações de backup e restauração.

## Testar e validar o plano

Os procedimentos aqui descritos foram testados e validados em um ambiente de laboratório. Para garantir que estes ou quaisquer outros procedimentos funcionem no seu ambiente, você deve testar e validar cada procedimento que pretende implementar. Conclua os testes e a validação antes de enviar seu plano para a aprovação final.

## Comunicar o plano

Seu plano de backup e restauração deve descrever claramente quem implementará os procedimentos e incluir instruções passo a passo para executá-los. Você deve garantir que todos os responsáveis por qualquer aspecto do plano o compreendam, entendam como será implementado e quais são os seus papéis. Isso inclui todos os requisitos da implementação para:

  - Backup do pool e de servidores.

  - Restauração de serviços.

**Backup do pool e de servidores**

O plano de backup e restauração deve incluir todas as informações necessárias para concluir os procedimentos de backup continuamente. As principais informações a serem comunicadas aos membros da equipe responsável incluem:

  - Equipe ou pessoa (especificado como um indivíduo ou função) responsável por realizar o backup de cada servidor.

  - Agendas específicas para realizar o backup de cada servidor.

  - Locais de backup para cada tipo de dados (configurações, banco de dados e compartilhamentos de arquivos).

  - Procedimentos de backup a serem usados, incluindo as ferramentas necessárias para concluir cada um deles.

  - As informações necessárias para concluir os backups, conforme descrito em [Planilhas de backup e restauração](lync-server-2013-backup-and-restoration-worksheets.md).

  - Métodos de validação a serem usados para ajudar a garantir que o backup dos dados e configurações foi executado apropriadamente e está disponível para restauração, que pode incluir auditorias periódicas e restaurações de teste.

**Restauração de serviços**

O plano de backup e restauração deve incluir todas as informações necessárias para restaurar serviços para casos de um ou mais servidores sofrer uma perda que os tornem indisponíveis. As principais informações a serem comunicadas aos membros da equipe responsável são:

  - Equipe ou pessoa (especificado como indivíduo ou função) responsável por determinar quando a restauração de serviços será necessária e os procedimentos a serem usados para restaurá-los e, também, a equipe ou pessoa responsável por implementar procedimentos para cada cenário de restauração.

  - Critérios para determinar quais procedimentos de restauração são mais apropriados para uma situação específica.

  - Estimativas de tempo para a restauração de serviços e tempo de recuperação (RTO) em cada cenário de restauração.

  - Procedimentos de restauração a serem usados, incluindo as ferramentas necessárias para concluir cada um deles.

  - As informações necessárias para restaurar dados e configurações. Planilhas são fornecidas em [Planilhas de backup e restauração](lync-server-2013-backup-and-restoration-worksheets.md).

## Como validar as operações de backup e restauração

Depois de concluir os esforços iniciais de backup em seu ambiente de produção e a intervalos específicos (conforme descrito em seu plano de backup e restauração), você deve verificar se:

  - Os backups estão ocorrendo conforme o solicitado.

  - Os dados e as configurações incluídos no backup estão disponíveis.

  - Procedimentos de restauração podem ser executados dentro dos períodos de tempo de recuperação (RTO) especificados no plano de backup e restauração e os resultados estarão de acordo com todos os requisitos de negócio.

  - Planilhas de backup foram preenchidas e verificadas e estão armazenadas em um local seguro. Estas planilhas são fornecidas em [Planilhas de backup e restauração](lync-server-2013-backup-and-restoration-worksheets.md).

  - Procedimentos de restauração foram testados e verificados se funcionam conforme o esperado, de acordo com o especificado no plano.

## Como manter o plano de backup e restauração

Uma topologia do Lync Server é um ambiente dinâmico que muda com a sua organização. Reavalie seu plano de backup e restauração conforme sua organização muda e reveja-o periodicamente para garantir que continua atendendo as necessidades do seu negócio.

