---
title: 'Lync Server 2013: Definindo seus requisitos para o Servidor de Chat Persistente'
TOCTitle: Definindo os requisitos de sua organização para o Servidor de Chat Persistente
ms:assetid: 568674fb-c08a-4170-ac38-e2f8428c69e0
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398372(v=OCS.15)
ms:contentKeyID: 49306754
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Definindo os requisitos de sua organização para o Servidor de Chat Persistente no Lync Server 2013

 

_**Tópico modificado em:** 2014-01-15_

Antes de implantar o Servidor de Chat Persistente na sua organização, é essencial considerar as seguintes principais perguntas para otimizar sua implantação:

  - Quem (perfil do usuário) deve ser habilitado para o Servidor de Chat Persistente? O Servidor de Chat Persistente é habilitado por uma política que pode ser definida em nível global, de site, de pool ou do usuário.

  - Quantos usuários (escala) devem ser habilitados para o Servidor de Chat Persistente? O Servidor de Chat Persistente suporta 150.000 usuários provisionados (habilitados pela política) e um máximo de 80.000 usuários simultâneos utilizando o Servidor de Chat Persistente. Um único Servidor de Chat Persistente pode suportar 20.000 usuários conectados e um único Pool de Servidor de Chat Persistente pode ter até 4 servidores ativos para um total de 80.000 usuários conectados simultaneamente.

  - Você está migrando de uma versão anterior do Servidor de Chat de Grupo ou está implantando o Servidor de Chat Persistente pela primeira vez?

  - Há requisitos de conformidade? O Servidor de Chat Persistente suporta conformidade. O serviço de conformidade é executado no Servidor de Chat PersistenteServidor Front-End, em oposição ao requisito para um computador separado nas implantações anteriores do Servidor de Chat de Grupo. A conformidade é opcional e, se escolhida, requer um banco de dados de conformidade que deve ser configurado para armazenar dados e eventos de conformidade. Também pode ser configurado um adaptador para obter dados do banco de dados de conformidade e convertê-los em outro formato (como arquivos XML ou arquivos hospedados no Exchange).

  - Como você deseja controlar escopos, limites éticos e acesso? É possível definir as **Categorias** para segregar esses limites e escolher quem estará habilitado para estar nas salas que forem criadas para cada uma dessas categorias.

  - Como você deseja controlar quem pode criar salas? É possível configurar em **Criadores**, de forma adequada para a suas categorias, quem pode criar salas. Os criadores podem atribuir outros membros como **Gerentes de Sala de Chat** para gerenciamento contínuo das salas (adicionando ou removendo membros adicionais), de acordo com o escopo para **AllowedMembers/DeniedMembers** configurados por categoria.

  - Como você deseja criar salas? O Servidor de Chat Persistente fornece um recurso com base na Web para criação e gerenciamento de salas. Ele pode ser iniciado no cliente do Lync 2013. Você pode definir uma solução personalizada (utilizando o Software Development Kit (SDK) do Servidor de Chat Persistente) que implementa requisitos e fluxos de trabalho do seu negócio e configura o Servidor de Chat Persistente para usuários diretos da sua solução personalizada.

  - Que tipo de suplementos você deseja provisionar? A opção **Suplementos** aprimora a experiência na sala aproveitando o painel de extensibilidade no cliente do Lync 2013 para fornecer contexto que seja relevante à sala. É possível escolher quais suplementos gerais podem ser mais úteis (por exemplo, o site da sua empresam documentos de colaboração interna e etc.). Os gerentes das salas de chat podem escolher um dos suplementos registrados e associá-lo às salas, se desejado.

  - Que tipo de alta disponibilidade e requisitos de recuperação de desastre você tem? Servidor de Chat Persistente suporta espelhamento de SQL Server e clustering de SQL Server para alta disponibilidade e suporta até 8 servidores (4 ativos e 4 em espera) em um pool descompactado com envio de logs de SQL Server para recuperação de desastre.

  - Há requisitos da regulamentação? Se a sua empresa estiver em um país/região onde os dados precisem ser mantidos, poderá ser necessário implantar vários Pools de Servidor de Chat Persistente, cada local a uma geografia específica. Uma sala, categoria, ou suplemento não inclui pools—pertence a um Pool de Servidor de Chat Persistente. É possível gerenciar o conjunto de categorias, suplementos e salas para cada Pool de Servidor de Chat Persistente. Os usuários podem ser configurados para terem acesso às salas em um ou mais pools usando o escopo da categoria AllowedMembers ou da adesão da sala, dependendo de como você cria suas categorias.
    
    > [!IMPORTANT]  
    > Ter vários Pools de Servidor de Chat Persistente não oferece a você mais escala (ainda assim, é possível ter apenas 80 mil usuários conectados simultaneamente em todos os seus Pools de Servidor de Chat Persistente). A principal razão para suportar vários Pools de Servidor de Chat Persistente é o suporte de preocupações regulatórias.
