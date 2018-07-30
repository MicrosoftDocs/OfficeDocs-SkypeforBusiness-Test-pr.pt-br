---
title: 'Lync Server 2013: Criar o design de topologia inicial'
TOCTitle: Criar o design de topologia inicial
ms:assetid: f3131153-de14-41be-b1e6-7d4bb0191af1
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg615047(v=OCS.15)
ms:contentKeyID: 52057767
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Criar o design de topologia inicial para Lync Server 2013

 

_**Tópico modificado em:** 2013-02-21_

Após concluir a instalação do Lync Server 2013, Ferramenta de Planejamento, você estará pronto para iniciar a Ferramenta de Planejamento e começar a projetar a infraestrutura do Lync Server 2013 proposta.

> [!NOTE]  
> A Ferramenta de Planejamento é uma ferramenta orientada por assistente, com guias detalhados para informá-lo no processo de tomada de decisões durante o design dos seus sites e da sua topologia. Este tópico não tem a intenção de servir como guia detalhado, mas simplesmente de ajudá-lo a começar a usar a Ferramenta de Planejamento em suas sessões de design.

## Para iniciar usando a Ferramenta de Planejamento e criar o design inicial

1.  Inicie o Lync Server 2013, Ferramenta de Planejamento: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Ferramenta de Planejamento**.

2.  Após a Ferramenta de Planejamento ser iniciada, a página **Bem-vindo à Ferramenta de Planejamento do Microsoft Lync Server 2013** será exibida. Escolha uma das seguintes opções para começar seu design:
    
      - **Opção 1: Iniciando**   Clicar em **Iniciando** oferece uma série específica de perguntas de entrevista com as seleções relevantes para definir o critério. Após ter finalizado a seção de entrevista **Iniciando** inicial, você continua com **Design de sites** para definir sua arquitetura de site. Para concluir esta opção, continue na etapa 3.
    
      - **Opção 2: Projetar sites**   Se você clicar em **Projetar sites** na página de Boas-vindas, as perguntas de entrevista apresentadas na seção **Introdução** serão ignoradas. Com esta opção, as informações que teriam sido recolhidas com as respostas às perguntas da entrevistas na seção **Introdução** são definidas como os valores padrão. Ao clicar em **Projetar sites** , o designer experiente pode ignorar a entrevista inicial e alterar os valores padrões conforme necessário na página inicial **Sites centrais** . Para concluir esta opção, pule as etapas de 3 a 5 e comece na etapa 6.
    
      - **Opção 3: Exibir sua topologia salva**   Se você já concluiu e salvou uma topologia usada anteriormente na Ferramenta de Planejamento, poderá ignorar a maioria dessas etapas e começar abrindo e exibindo a topologia. Você também pode fazer alterações e atualizações na topologia, salvá-la novamente e exportá-la para o Microsoft Excel ou Microsoft Visio. Para concluir esta opção, pule as etapas de 3 a 12 e comece na etapa 13.

3.  Clique em **Iniciando** para começar o design da sua topologia do Lync Server 2013.

4.  Responda cada seção selecionando os critérios apropriados para seu design e clique em **Avançar** para prosseguir à próxima página do assistente. Clique em **Voltar** para fazer alterações nas páginas anteriores.
    

    > [!TIP]
    > Cada página possui uma descrição do critério de seleção e recomendações com base nas práticas preferidas e no planejamento de capacidade. Se você precisa de mais detalhes, clique em <STRONG>Saber mais</STRONG> para ler a informação detalhada da documentação de Planejamento do Lync Server 2013 no site da Microsoft TechNet. Você deve ter uma conectividade com a Internet para acessar o site da Microsoft TechNet.



5.  Selecione as opções adequadas para seu design. Após o critério inicial ser definido, uma página confirmará que sua Visão Geral dos Recursos está concluída.

6.  Clique em **Design de sites** para definir seu site central.
    
    > [!NOTE]  
    > Cada topologia do Lync Server 2013 terá pelo menos um site central. Seu design pode ter um único site central, um site central com vários sites de lote, vários sites centrais ou vários sites centrais com sites de lote associados com cada site central.

7.  Em **Nome do site** , digite o nome que identificará este site central.

8.  Em **Usuários Hospedados no SIte** , digite o número esperado de usuários simultâneos locais que serão hospedados neste site central.

9.  Em **Usuários Hospedados na Nuvem** , digite o número esperado de usuários simultâneos online que serão hospedados neste site central.

10. Modifique as seleções para Colaboração Online, Usuários, Voz, Opções de Implantação Adicional ou Aplicativos do Servidor conforme necessário.
    
    > [!IMPORTANT]  
    > Neste ponto do design, você pode apenas selecionar ou desmarcar opções de sua implantação. No entanto, você pode configurar outras opções em uma fase posterior da Ferramenta de Planejamento. Existem também opções que não estão disponíveis e não podem ser desmarcadas. Além disso, talvez você precisa desmarcar uma opção para desmarcar outra. Por exemplo, se você desmarcar a opção <strong>Enterprise Voice</strong> em Voz, as opções <strong>Grupo de Resposta</strong> , <strong>Anúncio</strong> e <strong>Estacionamento de Chamada</strong> em Aplicativos do Servidor (todas elas recursos do Enterprise Voice) também serão desmarcadas.

11. Após definir um nome de site e número de usuários, clique em **Avançar** .

12. As páginas a seguir solicitam informações sobre domínios SIP, configurações de conferência, configurações e infraestrutura de voz, UM do Exchange, acesso de usuário externo, configurações do Chat Persistente, configurações de cliente, opções de colocação e sites de filial. Responda a essas perguntas conforme apropriado.

13. A pergunta final está relacionada à criação de outro site central. Se você selecionar **Sim** , a Ferramenta de Planejamento voltará à página Sites centrais. Se selecionar **Não** , clique em **Avançar** e, depois, em **Desenho** para obter uma exibição de alto nível da topologia global.

14. Para exibir uma topologia existente, clique em **Exibir** .

15. Clique no arquivo .xml que representa a topologia salva anteriormente e clique em **Abrir** .

16. A Ferramenta de Planejamento exibe a página Topologia global. Agora, você pode começar a editar, atualizar ou alterar a topologia usando as ferramentas disponíveis na Ferramenta de Planejamento.

## Consulte Também

#### Conceitos

[Editando o design no Lync Server 2013](lync-server-2013-editing-the-design.md)

