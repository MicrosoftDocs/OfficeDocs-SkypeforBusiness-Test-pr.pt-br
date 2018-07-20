---
title: Documentação das Ferramentas do Resource Kit do Lync Server 2013
TOCTitle: Documentação das Ferramentas do Resource Kit do Lync Server 2013
ms:assetid: b1c341f1-86fa-479d-ba4d-28df5a4c1622
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ945604(v=OCS.15)
ms:contentKeyID: 52057789
ms.date: 08/03/2014
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Documentação das Ferramentas do Resource Kit do Lync Server 2013

 

_**Tópico modificado em:** 2014-01-09_

Este tópico descreve as ferramentas que fazem parte do Resource Kit do Lync Server 2013, incluindo o objetivo de cada uma e como usá-las. O Lync Server 2013, Ferramentas do Resource Kit ajuda a facilitar as tarefas de rotina para os administradores de TI responsáveis por implementar e gerenciar o Lync Server 2013. Por exemplo, a ferramenta **Web Conf Data** pode ser usada para controlar facilmente os dados carregados pelos usuários durante uma reunião online. A ferramenta **SEFAUtil** pode ser usada para configurar o encaminhamento e respostas das chamadas de representantes para os usuários. Nós encorajamos os administradores de TI a usarem essas ferramentas para gerenciar com mais eficácia o Lync Server 2013.

## Instalação das ferramentas do Resource Kit

Para instalar o Lync Server 2013, Ferramentas do Resource Kit, baixe o **OCSReskit.msi**. Você pode baixar o instalador das Ferramentas do Resource Kit no Centro de Download em [http://go.microsoft.com/fwlink/p/?LinkID=330429](http://go.microsoft.com/fwlink/p/?linkid=330429).

Execute o **OCSResKit.msi** para realizar uma instalação simples. O .msi instala todas as ferramentas no seguinte caminho:**%Program Files%\\Microsoft Lync Server 2013\\ResKit**. As ferramentas executáveis autocontidas ficam nesta pasta. As ferramentas que possuem arquivos ficam nas suas próprias subpastas.

## Ambientes com suporte

Para um melhor desempenho, o Lync Server 2013, Ferramentas do Resource Kit deve ser instalado no mesmo ambiente e com as mesmas especificações necessárias para o Lync Server 2013.

## Visão geral das ferramentas do Resource Kit

A lista abaixo descreve as ferramentas fornecidas no Resource Kit do Lync Server 2013. Uma descrição de cada ferramenta, incluindo os requisitos e exemplos usados, é abordada na seção abaixo:

  - ABSConfig

  - Monitor de serviço da política de largura de banda

  - Analisador de Utilização da Largura de Banda

  - Estacionador de chamadas

  - CleanupStorageServiceData

  - DBAnalyze

  - ImportStorageServiceData

  - LCSSync

  - LookupUserConsole

  - MsTurnPing

  - Visualizador de configuração da rede

  - Response Group Agent Live

  - SEFAUtil

  - SYSPrep.ps1

  - Migração de Comunicados de Número não Atribuído

  - Web Conf Data

## ABSConfig

A ferramenta Configuração do serviço de catálogo de endereços (ABSConfig) é uma ferramenta administrativa que ajuda os administradores a personalizarem a configuração do Serviço de catálogo de endereços no Lync Server 2013. Ela também permite que os administradores do Lync Server 2013 restaurem a configuração padrão do Serviço de catálogo de endereços.

## Descrição

O ABSConfig é um aplicativo de interface de usuário gráfico que permite aos administradores configurar os atributos do Serviços de Domínio Active Directory relacionados ao Serviço do catálogo de endereços.

Os principais cenários da ferramenta são os seguintes:

  - Permite aos administradores mapear os atributos dos Serviços de Domínio Active Directory para os atributos do Lync Server 2013.

  - Permite aos administradores especificar os atributos dos Serviços de Domínio Active Directory a serem incluídos ou excluídos dos arquivos de Serviço de catálogo de endereços.

  - Permite aos administradores restaurar as configurações padrão do Serviço de catálogos de endereço.

A ferramenta ABSConfig pode ser iniciada usando o arquivo absConfig.exe. A ferramenta abre a guia **Configurar atributos** . Esta tabela possui opções para mapear os atributos dos Serviços de Domínio Active Directory para os campos de atributo do Lync Server 2013 e especificar quais usuários devem ser incluídos ou excluídos dos arquivos do Serviço de catálogo de endereço baseado em filtros de atributos específicos. Também possui opções para personalizar quais números telefônicos serão incluídos no arquivo do Catálogo de endereços. A opção **Restaurar padrões** permite aos administradores restaurar para os valores padrão as configurações do Serviço de catálogo de endereços.

## Alterações no Lync Server 2010

Na ferramenta Configuração ABS do Lync Server 2013, os atributos (linhas) podem ser removidos desmarcando a caixa de seleção "habilitar" do atributo. O mesmo acontece ao excluir a linha no Lync Server 2010.

> [!NOTE]
> A caixa de seleção de habilitação fica na coluna à direita; é necessário rolar para a direita para visualizar a coluna


## Resultado

A ABSConfig armazena a configuração do Serviço de catálogo de endereços no banco de dados.

    Path: %ProgramFiles%\Microsoft Lync Server 2013\Reskit

## Objetivo

A ABSConfig proporciona uma forma rápida e fácil de personalizar o Serviço de catálogo de endereços do Lync Server 2013.

## Requisitos

## Computador

A ABSConfig só poderá ser executada em um computador associado a um domínio que tenha o Lync Server 2013 instalado. No caso do Lync Server 2013, Enterprise Edition, esta ferramenta poderá ser executada em qualquer servidor Front End que tenha o Serviço de catálogo de endereços habilitado durante a instalação.

## Rede

O computador deve estar apto a se conectar com o Pool de Front Ends e com o banco de dados back-end.

## Software

Os seguintes componentes de software deverão ser instalados antes de executar a ferramenta ABSConfig:

  - Microsoft Lync Server 2013

## Usuários

Administradores que possuem as permissões necessárias para atualizar a implantação Lync Server 2013.

## Exemplos

A ABSConfig pode ser iniciada digitando **ABSConfig.exe** em um prompt de comando. Abaixo é mostrada a interface de usuário da ferramenta ABSConfig.

![A ferramenta ABSConfig.exe.](images/JJ945604.6fb63a70-7b63-4b8b-b7d1-82fe9aa2028f(OCS.15).jpg "A ferramenta ABSConfig.exe.")

## Resumo

A ferramenta ABSConfig proporciona aos administradores uma forma rápida e fácil de personalizar o Serviço de catálogo de endereços do Lync Server 2013.

## Monitor de serviço da política de largura de banda

A ferramenta Monitor de serviço da política de largura de banda permite que os administradores visualizem uma lista do seguinte:

1.  Todos os serviços da Política de largura de banda (Autenticação e núcleo) do Lync Server 2013 configurados na topologia

2.  As conexões de cada um dos serviços a outros serviços de Política de largura de banda e servidores de Borda

3.  Todos os links configurados contidos no documento de configuração da Rede e largura de banda em tempo real usada e conforme informada por cada um dos serviços da Política de largura de banda

## Descrição

A ferramenta Monitor de serviço da política de largura de banda é implementada como um aplicativo baseado na GUI. Os administradores iniciam a ferramenta executando o PDPMonUI.exe.

Ao iniciar a ferramenta, ela tenta descobrir a lista dos serviços da Política de largura de banda na topologia. Após a conclusão da atualização inicial, o painel à esquerda da janela é preenchido com uma lista de serviços agrupados pelos clusters aos quais pertencem.

Quando os administradores selecionam um determinado Serviço de Política de Largura de Banda, o painel à direita exibe as informações sobre aquele determinado serviço. O painel também possui duas guias principais que exibem informações.

## Guia Informações do computador

A guia **Informações do computador** mostra os detalhes do Serviço de Política de Largura de Banda selecionado e a lista e o estado de todas as conexões realizadas pelo Serviço de Política de Largura de Banda selecionado para outros serviços.

## Guia Informações da topologia

A guia **Informações da topologia** mostra uma lista de todos os links configurados nas configurações de Rede. É exibida a capacidade de largura de banda de vídeo e áudio de cada link. Além disso, a largura de banda utilizada atualmente também é exibida, tanto em Kbps como em porcentagem da capacidade. A ferramenta usa uma codificação por cores para realçar os links cuja utilização está próxima do limite de capacidade, permitindo aos administradores isolarem rapidamente estes links.

> [!NOTE]
> Se houver uma falha no Monitor de serviço da política de largura de banda ao se conectar com qualquer um dos serviços de Política de largura de banda configurados, as informações nas guias <strong>Informações do computador</strong> e <strong>Informações da topologia</strong> não serão exibidas. No entanto, é possível que haja uma conexão inicial ao serviço e depois falhe. Nesses casos, os administradores verão as informações desatualizadas. Há um carimbo de data/hora <strong>Última atualização</strong> em cada uma das guias que permitem aos administradores visualizar quais foram os últimos dados atualizados de um determinado Serviço de Política de Largura de Banda.


## Resultado

Não há nenhum resultado da linha de comando; o resultado do programa está contido dentro da interface gráfica do usuário principal (GUI).

## Objetivo

O objetivo da ferramenta Monitor de serviço da política de largura de banda é permitir aos administradores a visualização do estado de cada um dos serviços de Política de largura de banda definidos na topologia. Além disso, os administradores podem visualizar a largura de banda em tempo real usada em todos os links definidos no documento de configuração da Rede.

## Requisitos

A ferramenta Monitor de serviço da política de largura de banda deve ser executado em um computador que faça parte da topologia do Lync Server.

## Resumo

A ferramenta Monitor de serviço da política de largura de banda pode ser um recurso valioso para os administradores, pois com ela é possível inspecionar na topologia o estado de todos os serviços de Política de largura de banda — e o mais importante — obter a utilização da largura de banda em tempo real nos links definidos nas configurações de Rede.

## Analisador de utilização de largura de banda

O Analisador de Utilização da Largura de Banda é uma ferramenta que cria relatórios sobre diversas visualizações de consumo de largura de banda pelos pontos de extremidade do UC nos links WAN da rede corporativa.

## Descrição

O Analisador de Utilização da Largura de Banda é implementado como um aplicativo baseado na GUI. Esta ferramenta gera relatórios específicos para utilização de áudio na rede e ajuda no planejamento da capacidade. Também interage com a capacidade de largura de banda atribuída a diversos links.

## Resultado

O Analisador de Utilização da Largura de Banda fornece plotagens gráficas da utilização e da capacidade de largura da banda para o áudio de todos os links WAN configurados no sistema.

## Objetivo

Em qualquer implantação de vídeo e voz, é fundamental monitorar e entender a tendência da utilização da largura de banda do tráfego da mídia na rede corporativa. A ferramenta Analisador de Utilização da Largura de Banda permite ao administrador realizar justamente isso. Essa ferramenta realiza o seguinte:

  - Gera relatórios específicos da utilização de áudio na rede

  - Ajuda com um planejamento de capacidade mais eficaz e interage na capacidade da largura de banda atribuída a diversos links

O Analisador de Utilização da Largura de Banda gera plotagens gráficas dos relatórios de utilização e capacidade da largura de banda; tais como:

  - Todos os links WAN na rede corporativa

  - Filtradas de acordo com os links WAN escolhidos selecionados

  - Filtradas de acordo com os links WAN que excederam o limite de capacidade de links

  - Filtradas de acordo com os links WAN que utilizaram a largura de banda provisionada

  - Filtradas de acordo com os links WAN que alcançaram níveis críticos (uma utilização de largura de banda superior a 90% da capacidade da largura de banda do link WAN)

  - Filtradas de acordo com o tipo de link WAN — links rede-site, links inter-regionais e links dentro de um site

  - Filtradas de acordo com a região da rede

## Aplicativos

O Analisador de Utilização da Largura de Banda possui os dois aplicativos (ferramentas) abaixo:

  - **WanLinkLogCollector.exe**   Esta ferramenta permite ao usuário inserir as informações necessárias.

  - **BandwidthUtilizationAnalyzer.xlsm**  Uma planilha de relatório de software é iniciada automaticamente pelo WanLinkLogCollector.exe. Este aplicativo permite ao usuário aplicar filtros no relatório, como será mostrado posteriormente neste artigo.

## Fases de uso do Analisador de Utilização da Largura de Banda

Há duas fases ao usar o Analisador de Utilização da Largura de Banda:

  - Coletar logs, o que é realizado ao usar o WanLinkLogCollector.exe

  - Personalizar relatórios, o que é realizado ao usar o BandwidthUtilizationAnalyzer.xlsm

> [!IMPORTANT]
> Recomendamos que o BandwidthUtilizationAnalyzer.xlsm não seja iniciado manualmente pelos usuários finais.


## Iniciando o Analisador de Utilização da Largura de Banda

Start WanLinkLogCollector.exe no prompt de comando ou usando o Windows Explorer.

**Usando o WanLinkLogCollector.exe**

Há três etapas para usar o WanLinkLogCollector.exe:

1.  **Log da linha do tempo**   Forneça a linha do tempo na qual o relatório precisa ser gerado

2.  **Especificar os diretórios do arquivo**   Forneça as informações de localização do arquivo

3.  **Coletar os logs e iniciar o visualizador de relatórios**  Execute o comando para gerar o relatório

## Etapa 1 - Log da linha do tempo

O registro em log da linha do tempo permite ao usuário da ferramenta especificar o seguinte, observe a figura abaixo:

1.  **Data de início** Trata-se da data de início da linha do tempo na qual o relatório foi gerado; por exemplo, 1 de agosto de 2010. 

2.  **Data de término** Trata-se da data de término da linha do tempo na qual o relatório foi gerado; por exemplo, 30 de setembro de 2010.  
    
    ![Datas de início e término na Utilização da Largura de Banda A](images/JJ945604.2c597cfc-3372-4d41-816b-26202f607ad8(OCS.15).jpg "Datas de início e término na Utilização da Largura de Banda A")  

## Etapa 2 - Especificar os diretórios do arquivo

Os seguintes diretórios de arquivo devem ser especificados pelo usuário, conforme mostrado:

  - **Localização dos arquivos de log no servidor** Localização da pasta onde os logs do servidor da Política de largura de banda são armazenados. Geralmente na opção \<servidordearquivos\>\\\< do FE\>\\AppServerFiles\\PDP.

  - **Localização do armazenamento do arquivo temporário** Localização do arquivo temporário onde os arquivos intermediários serão armazenados enquanto o relatório estiver sendo gerado.

![Arquivos de diretórios na Análise da Utilização da Largura de Banda](images/JJ945604.d66daeac-1669-45e3-932d-3f6782840c2a(OCS.15).jpg "Arquivos de diretórios na Análise da Utilização da Largura de Banda")

> [!NOTE]
> Certifique-se de fornecer ao usuário da ferramenta acesso de arquivo suficiente aos logs do servidor e à pasta de armazenamento de arquivo temporário.


## Etapa 3 - Coletar os logs e iniciar o visualizador de relatórios

Para coletar os logs e iniciar o visualizador de relatórios, clique em **Executar** , como mostrado abaixo. Esta etapa coleta os dados necessários.

![Coletando dados da Análise de Utilização de Largura de Banda](images/JJ945604.0019cb2c-7c01-4dc9-ac90-ac47c47d1bfd(OCS.15).jpg "Coletando dados da Análise de Utilização de Largura de Banda")

Se a validação da entrada for bem-sucedida, a mensagem abaixo mostrada será exibida.

![Notificação de coleta de logs no Bandwidth Utili](images/JJ945604.eda91da8-3285-4eab-8ccb-c6d89c8cc221(OCS.15).jpg "Notificação de coleta de logs no Bandwidth Utili")

Clique em **OK**. BandwidthUtilizationAnalyzer.xlsm será iniciado automaticamente. Siga as instrução na caixa de mensagens. Para mais detalhes, consulte **Usando o BandwidthUtilizationAnalyzer.xlsm** na próxima seção.


**Usando o BandwidthUtilizationAnalyzer.xlsm**

1.  Se o BandwidthUtilizationAnalyzer.xlsm tiver sido iniciado automaticamente, clique em **Atualizar** , conforme mostrado abaixo:
    
    ![BandwidthUtilizationAnalyzer.xlsm](images/JJ945604.c4e675b9-1671-400e-a712-6db82d731b39(OCS.15).jpg "BandwidthUtilizationAnalyzer.xlsm")

2.  Com a pasta de arquivo aberta, selecione consolidated.csv na localização especificada na caixa de mensagens, conforme mostrado abaixo. A localização também é mostrada como **C:\\Temp**.
    
    ![Como abrir uma pasta no BandwidthUtilizationAnalyzer.](images/JJ945604.601cc572-cee9-45fb-9ed1-c4b96a2fa21e(OCS.15).jpg "Como abrir uma pasta no BandwidthUtilizationAnalyzer.")

3.  Clique em **Importar**.

4.  A plotagem gráfica é gerada automaticamente. Ela será disponibilizada assim que o ponteiro operando em segundo plano desaparecer.
    
    ![Aplicando filtros no modo de exibição Relatórios.](images/JJ945604.1416468e-e3ab-478e-b569-e42ba9c27a17(OCS.15).jpg "Aplicando filtros no modo de exibição Relatórios.")

## Aplicando filtros no Visualizador de relatórios

Os filtros possíveis de serem aplicados no visualizador de relatórios conforme mostrado abaixo, são descritos da seguinte forma:

![Aplicando filtros no modo de exibição Relatórios.](images/JJ945604.1416468e-e3ab-478e-b569-e42ba9c27a17(OCS.15).jpg "Aplicando filtros no modo de exibição Relatórios.")

1.  **Nome** Filtrado de acordo os links WAN (localizado na lateral direita do gráfico). O prefixo denota os seguintes tipos de links; consulte a caixa (azul) vertical:
    
      - **S Site** O link WAN de um site da rede a uma região da rede
    
      - **IS Inter-Site** O link WAN entre dois sites da rede
    
      - **R Inter-Region** O link WAN entre duas regiões da rede

2.  **Limite excedido** Filtrado de acordo com os links WAN cuja utilização da largura de banda seja superior ao limite da capacidade da largura de banda

3.  **Níveis críticos** Filtrados de acordo com os links WAN cuja utilização da largura de banda tenha alcançado 90% ou mais da capacidade da largura de banda

4.  **Subutilizado** Filtrado de acordo com os links WAN cuja utilização da largura de banda seja inferior a 25% da capacidade da largura de banda

5.  **Tipo de link** Filtrado de acordo com os seguintes tipos de links WAN:
    
      - **Tipo de site da rede**
    
      - **Tipo de entre sites**
    
      - **Tipo de link entre região**

6.  **Região** Filtrado de acordo com a região da rede

As imagens abaixo mostram os filtros descritos anteriormente.

Filtrado de acordo com o **Nome**. Selecione a lista de links que precisam ser exibidos no gráfico.

![Filtrando por nome em BandwidthUtilizationAnalyzer.](images/JJ945604.002b7c8e-f0da-48ce-9e1a-5c34d2cab063(OCS.15).jpg "Filtrando por nome em BandwidthUtilizationAnalyzer.")

Filtrado de acordo com o **Limite excedido**. Selecione **Verdadeiro** para impor o filtro.

![Filtrando por Limite Excedido.](images/JJ945604.5946c95e-76ce-46ca-8f3e-a79be1e5c527(OCS.15).jpg "Filtrando por Limite Excedido.")

Filtrado de acordo com os **Níveis críticos**. Selecione **Verdadeiro** para impor o filtro.

![Filtrando por Níveis Críticos.](images/JJ945604.60771a52-d8ba-4cb9-a02d-d6c888cb5505(OCS.15).jpg "Filtrando por Níveis Críticos.")

Filtrado de acordo com o **Subutilizado**. Selecione **Verdadeiro** para impor o filtro.

![Filtrando por Sub-utilizados.](images/JJ945604.95a2bf01-5aba-4927-af47-1ad3c459d791(OCS.15).jpg "Filtrando por Sub-utilizados.")

Filtrado de acordo com o **Tipo de link**. Selecione o tipo ou tipos que precisam ser exibidos.

![Filtrando por tipo de Link.](images/JJ945604.08757949-06bd-4cf3-809f-d81fd23a6639(OCS.15).jpg "Filtrando por tipo de Link.")

Filtrado de acordo com a **Região**. Selecione uma lista de regiões cujos links precisam ser exibidos.

![Filtrando por Região.](images/JJ945604.5de4cec4-6c09-48bb-98c7-b56f7bdb3d5a(OCS.15).jpg "Filtrando por Região.")

## Requisitos

  - .NET Framework 3.5

  - Microsoft Excel 2010 ou Excel 2007

## Resumo

O Analisador de Utilização da Largura de Banda é usado para traçar a utilização da largura de banda do áudio do tráfego de UC na rede. Esta ferramenta pode ser usada para informar a utilização da largura de banda do vídeo na rede.

## Estacionador de chamadas

O Estacionador de chamadas é um aplicativo de linha de comando que proporciona fácil acesso ao banco de dados da órbita do Estacionamento de chamadas.

## Descrição

O Estacionador de chamadas é uma ferramenta que rastreia as chamadas estacionadas atualmente. E também coleta estatística sobre as órbitas e Servidor de estacionamento de chamadas (CPS) usados. Esta ferramenta de linha de comando proporciona acesso de leitura e gravação no SQL Server banco de dados da órbita do CPS a partir de um computador conectado remotamente ou local.

Todas as opções são mutuamente exclusivas. A sintaxe da linha de comando é a seguinte:

  - **Parâmetro –o** — lista todos os intervalos de órbita configurados para este pool.

  - **Parâmetro –n** — lista todas as órbitas usadas atualmente neste pool. As informações são exibidas da seguinte forma:
    
      - Identificador de recurso uniforme (URI) do SIP do estacionado e estacionador.
    
      - Nome do host do CPS onde a chamada está estacionada.
    
      - Carimbo de data/hora de onde a chamada foi estacionada

  - **Parâmetro –f** —l lista o número de órbitas atualmente livres no pool.

  - **Parâmetro–r \<n\>** — lista as \<n\> últimas chamadas estacionadas. As informações são exibidas da seguinte forma:
    
      - URI do SIP do estacionado
    
      - URI do SIP do estacionador.
    
      - Nome do host do CPS no qual as chamadas foram estacionadas.
    
      - Carimbo de data/hora de quando as chamadas foram recuperadas ou ignoradas.

  - **parâmetro -t\<n\>** - realiza testes reservando uma órbita no banco de dados para mostrar a aleatoriedade dos números de órbita atribuídos.

## Resultado

Dependendo dos parâmetros de entrada especificados em um prompt de comando, o Estacionador de chamadas exibirá o seguinte resultado:

  - Todos os intervalos de órbita configurados para este pool

  - Chamadas estacionadas atualmente

  - Número de órbitas livres (disponíveis)

  - Chamadas estacionadas recentemente

  - Órbitas reservadas para testes uniformes e valores de órbita aleatórios

## Objetivo

O objetivo da ferramenta CPS é fornecer o acesso da linha de comando ao banco de dados do CPS. O administrador pode visualizar o CPS usado e determinar o números de órbitas atribuídas a um pool.

## Requisitos

Não haverá nenhuma exigência se esta ferramenta for executada no mesmo computador que estiver executando o CPS. Se esta ferramenta estiver sendo executada em um computador remoto, o banco de dados do SQL Server usado pelo Lync Server 2013 deverá ser configurado para permitir o acesso remoto. O Estacionador de chamadas deve ser configurado com uma cadeia de conexão de banco de dados doSQL Server para se conectar ao SQL Server do pool. Esta Cadeia de conexão do banco de dados do SQL Server é definida no arquivo de configuração **parkometer.exe.config**. Deverá será colocado no mesmo diretório onde o parkometer.exe está localizado. O seguinte arquivo XML trata-se de um exemplo do parkometer.exe.config. Os parâmetros que devem ser configurados são o nome de usuário (por exemplo: meudomínio\\Administrador), a senha (por exemplo, minhasenha) e o nome do host (por exemplo, meuservidor).

```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <configuration>
      <appSettings>
       <add key="SQL" value="server=myserver\RTC;
    database=cpsdyn;
    User Id=mydomain\Administrator;
    Password=mypassword.;
    Integrated Security=false;"/>
      </appSettings>
    </configuration>
```

## Exemplos

Intervalos de órbita implantados: o parâmetro –o lista todos os intervalos de órbita configurado para este pool, conforme mostrado:

![Intervalos de órbitas no Estacionador de Chamadas.](images/JJ945604.9ede64cb-29d9-4782-a34b-b76c42fbdcad(OCS.15).jpg "Intervalos de órbitas no Estacionador de Chamadas.")

Chamadas estacionadas atualmente: o parâmetro –n lista todas as órbitas usadas atualmente neste pool, conforme mostrado:

![Chamadas estacionadas no momento no Estacionador de Chamadas.](images/JJ945604.07a7eec4-7999-4c92-93f0-95525b244b4c(OCS.15).jpg "Chamadas estacionadas no momento no Estacionador de Chamadas.")

Número de órbitas livres: o parâmetro –f lista o números de órbitas livres atualmente neste pool, conforme mostrado:

![Órbitas livres no Estacionador de Chamadas.](images/JJ945604.ecc1d621-0ca0-4ecf-a579-08b41c6f08ed(OCS.15).jpg "Órbitas livres no Estacionador de Chamadas.")

Chamadas estacionadas recentemente: o \<n\> parâmetro –r lista \<n\> as últimas chamadas estacionadas, conforme mostrado:

![Chamadas estacionadas recentemente no Estacionador de Chamadas.](images/JJ945604.1c5eb27d-faa1-491b-b4aa-b484255c3353(OCS.15).jpg "Chamadas estacionadas recentemente no Estacionador de Chamadas.")

Reserva da órbita de teste: o parâmetro –t \<n\> testa a reserva de uma órbita no banco de dados, conforme mostrado:

![Reservas de órbitas de teste no Estacionador de Chamadas.](images/JJ945604.84c9b69e-7af0-4224-8711-a43a28f08691(OCS.15).jpg "Reservas de órbitas de teste no Estacionador de Chamadas.")

## Resumo

O Estacionador de Chamadas é uma ferramenta de linha de comando que fornece informações detalhadas sobre o Servidor de Estacionamento de Chamadas.

## CleanupStorageServiceData

A ferramenta do resource kit do CleanupStorageServiceData permite a exclusão de dados órfão do banco de dados usados pelo Serviço de armazenamento do Lync Server (LYSS). Uma função do serviço de armazenamento é armazenar em buffer a comunicação entre o Lync Server e diversos pontos de extremidade de armazenamento de dados de back-end, tais como SQL Server e Exchange.

## Descrição

Para dar suporte a uma alta disponibilidade, o LYSS aceita e salva temporariamente cópias de dados em diversos servidores front end no pool e também remove os dados após serem entregues à localização de armazenamento de longo prazo final. Situações inusitadas poderão ocorrer mesmo em uma operação normal, tais como, um servidor falhar ou apresentar um problema de processamento, e alguns dados poderão não ser limpos adequadamente. Estes dados são inofensivos, mas consomem recursos de processamento limitados. Grande parte de uma manutenção de dados normal necessária é automatizada, mas esta ferramenta permite a identificação e remoção segura de dados órfão quando a remoção automática não for possível. O uso desta ferramenta será indicado se o alerta do SCOM do System Center Operations Manager (SCOM) for disparado e solicitar ao administrador a remoção de dados desnecessários dos bancos de dados de LYSS locais no pool. Haverá um evento correspondente no caso de fazer logon no front end no qual o alerta foi disparado. Os detalhes do evento conterão informações sobre a quantidade de dados órfãos contidos no front end e será disparado se os dados excederem a determinados limites pré-determinados

## Requisitos

Instale o Lync Server 2013, Ferramentas do Resource Kit. A ferramenta será executada em computadores que estejam associados a um domínio que tenham os Lync Server e Shell de Gerenciamento do Lync Server 2013 instalados. A ferramenta usa um cmdlet de um shell de gerenciamento para identificar todos os servidores Front End no pool. Em segundo lugar, a ferramenta deverá ser executada a partir de um computador no pool que tenha o banco de dados **RtcLocal** instalado. Esse banco de dados será usado pela ferramenta CleanupStorageServiceData para obter os detalhes necessários para se comunicar com o Serviço de roteamento do Lync Server . Por fim, a conta ou credencial invocando a ferramenta deverá possuir permissão de leitura/gravação para o arquivo compartilhado e no qual deseja gravar o log de resultados. Essa ferramenta também depende do pool estar em um estado estável. Ou seja, o servidor Front End deverá estar instalado e funcionando, a instância LYNCLOCAL do SQL Server e o banco de dados do LYSS deverão estar conectados e cada grupo de roteamento deverá ter um conjunto completo de 1 servidor Front End primário e 2 servidores Front End secundários.

## Exemplos

C:\\Arquivos de Programas\\Microsoft Lync Server 2013\\ResKit\\StorageService\> ImportStorageServiceData.exe

    Description:
    This tool will remove orphaned data from the Storage Service database
    for a pool. You are required to run this tool on a machine inside the
    pool which has the Lync Server Management Shell installed and has RtcLocal database installed.
    Usage: Default behavior is to clean up orphaned data from the all the 
           Storage Service databases in the current pool.
    Additional Options:
    -Verbose    : Turn verbose output on.
    -LogPath    : The UNC path to which to write the log.
    ------------------------------------------------------------------------------
    Please wait while we initialize...
    Found 4 front end servers
    Replica Instances for LYSS Service
    Address: server2.vdomain.com - Primaries: 7 Secondaries: 14
    Address: server.vdomain.com - Primaries: 7 Secondaries: 14
    Address: server1.vdomain.com - Primaries: 7 Secondaries: 14
    Address: server3.vdomain.com - Primaries: 7 Secondaries: 14
    Primary Total Count = 28, Secondary Total Count = 56
    Finding and removing orphaned data for 28 routing groups
    Removing 1 stale groups from FE server.vdomain.com
    No stale routing groups detected on FE server2.vdomain.com
    No stale routing groups detected on FE server1.vdomain.com
    No stale routing groups detected on FE server3.vdomain.com
    Searching for stale queue items
    Removed 20 stale queue items for routing group 17D5435AE40259F7BBDF1866776386E4
    No stale queue items found for routing group 1975349662315F90B119DACB4F2AE3AD
    No stale queue items found for routing group 1A23E3D58BDB5A458A0B73F34AB7ACBE
    No stale queue items found for routing group 1AC91E3A1029535A80123121989CEADC
    No stale queue items found for routing group 3313935458E35B9B9759E08A15D251E6
    No stale queue items found for routing group 39BB0035B06B5427873FC6099720462A
    No stale queue items found for routing group 40721948E7B55CE893A53E911F76D185
    No stale queue items found for routing group 4501E04EAE4856059346949FF817C220
    No stale queue items found for routing group 4D833C98801F546F8E45E417EE028E2E
    No stale queue items found for routing group 5AD77443AD955A22A876749BE66D5317
    No stale queue items found for routing group 69844A271E6C5633A1F2B46A42287DD6
    No stale queue items found for routing group 69DA3BE407A95C7284EB4B1337718C93
    No stale queue items found for routing group 8437358AB34A5CC8967D5EF39494AB8D
    No stale queue items found for routing group 8ED455B1789655359816E1C5BF4C430F
    No stale queue items found for routing group 904F6C9B8AC951AE8B3C86684D3832E4
    No stale queue items found for routing group 90AAB3AE9A1950E0ADE7809A27021D63
    No stale queue items found for routing group 944F5724C65C5F93900DC1C8C898B102
    No stale queue items found for routing group 9E8A2630250C51769E39F63F0FB552BA
    No stale queue items found for routing group A11E27AE439A582288D4657EDA86B565
    No stale queue items found for routing group A9B10C76E764556FAEA3E47301EDF518
    No stale queue items found for routing group AEA2699E74ED59848ACEA7896699430D
    No stale queue items found for routing group B269961603E75065AFDA4F4F006DA5E4
    No stale queue items found for routing group BB873D9A3DA959DAB2FD743E5AA619F7
    No stale queue items found for routing group BCC6A48FBA2454B79B9EDB276657A404
    No stale queue items found for routing group C8EF4805722B5F6C876EBC0440B420FD
    No stale queue items found for routing group CA38EBDAC4845489ACE208C2240E4056
    No stale queue items found for routing group F5921887DB025C5F908CE42DB7F1AEE8
    No stale queue items found for routing group F9E606A825395422B3BF7A01ECBB7B1F
    Writing log: M:\Dev\Server\ResKit\StorageService\CleanupStorageServiceData.Log_20121009_151040
    Tool has finished execution.  Errors encountered: 0
    C:\Program Files\Microsoft Lync Server 2013\ResKit\StorageService>

## DBAnalyze

## Descrição

O DBAnalyze é uma ferramenta de linha de comando que ajuda os administradores a coletarem relatórios de análise sobre os bancos de dados do Lync Server 2013. O DBAnalyze possui os seguintes modos: diagnóstico, dados do usuário, conferência, MCUs e fragmentação de disco:

  - **Modo de diagnóstico**   Cria um relatório com informações sobre tabelas (número de registros, fragmentação, tamanho dos dados e tamanho do índice), dados e tamanhos do arquivo de log, a hora do último backup e distribuição de contatos entre os servidores que estiverem executando o Microsoft Office Communications Server, o número médio de permissões, contatos, contêineres, assinaturas, publicações, pontos de extremidade por usuário, usuários hospedados inadequadamente, usuários que não podem ser roteados, o número médio de conferências organizadas por usuários, conferências agendadas, conferências habilitadas e a versão do banco de dados.
    
    > [!NOTE]
    > A execução do modo de diagnóstico poderá afetar o desempenho do servidor.


  - **Modo de dados do usuário**  Informa os dados de contato, contêineres, assinatura, publicação, permissão e grupos de contato de um usuário específico e dos usuários que tenham o este usuário nas listas de permissões e contatos. Este modo também informa os dados resumidos das conferências organizadas por este usuários ou para as quais foi convidado.

  - **Modo de conferência**   Informa os dados detalhados de uma conferência específica, incluindo os detalhes da hora agendada da conferência, a lista de convidados, a lista de tipos de mídia permitidos para a conferência, as MCUs (Unidades de Controle de Multipontos) habilitadas, a lista de participantes ativos e o estado de sinalização de cada participante.

  - **Decodificar ID de reunião**  Decodifica a ID de reunião de uma rede telefônica pública comutada (PSTN) especificada pelo switch **/pstnid** mas não se conecta ao ponto de extremidade para informações detalhadas.

  - **Resolução de conferência**   Decodifica uma ID de PSTN especificada pelo switch<strong>/pstnid</strong> e exibe as informações sobre a conferência indicada pela ID.

  - **Modo das MCUs**  Informa a ID, tipo de mídia, URL,status da pulsação, carga de conferência e carga de participante de cada MCU no pool.

  - **Modo de disco de fragmentação**  Exibe o status de fragmentação de todos os discos.

Esta ferramenta pode ser usada para diagnosticar diversos problemas ou para ajudar os administradores no planejamento da capacidade. Por exemplo, se a maioria dos usuários hospedados no servidor A escolherem como seus contatos usuários hospedados no servidor B, o administrador poderá mover os usuários do servidor A para o servidor B para reduzir o tráfego no servidor.

## Resultado

Esta ferramenta gera relatórios pré-definidos sobre o banco de dados do Lync Server 2013 database. **Caminho:** %ProgramFiles%\\Microsoft Lync Server 2013\\Reskit

## Objetivo

Para instalar o Dbanalyze.exe, copie-o para uma pasta local e execute a ferramenta. Para usar a ferramenta, execute o seguinte comando na linha de comando.`dbanalyze.exe [/v] [/report:value] [/sqlserver:value] [/user:user@domain.com] [/conf:value][/pstnid:Value] [/maxcontacts:value]` As descrições das opções de linha de comando são mostradas abaixo.

![Opções de linha de comando para Dbanalyze.exe.](images/JJ945604.22bf3432-af6d-495b-8f48-d94c5d259523(OCS.15).jpg "Opções de linha de comando para Dbanalyze.exe.")

## Requisitos

**Computador** O DBAnalyze poderá ser executado apenas em um computador que esteja associado a um domínio que tenha o Lync Server 2013 instalado.

**Rede** O computador deve estar apto a se conectar ao banco de dados back-end.

**Software** Os componentes de software do Lync Server 2013 deverão ser instalados antes de executar o DBAnalyze.

**Usuários**A tabela abaixo mostra os administradores que possuem as permissões necessárias para acessar os bancos de dados do Lync Server 2013 .

![Tabela de permissões para Dbanalyze.exe.](images/JJ945604.b8931e9e-834e-4dec-8a84-2fc47d1613e9(OCS.15).jpg "Tabela de permissões para Dbanalyze.exe.")

> [!NOTE]
> Uma conta de administrador local é necessária para o modo <strong>/report:disk</strong>.


## Exemplos

Seguem abaixo os exemplos de comandos Dbanalyze.exe válidos:

    dbanalyze.exe /report:diag
    dbanalyze.exe /report:user /user:usera@domainb.com
    dbanalyze.exe /report:conf /user:bob@example.com /conf:1W9J71SKSX2X
    dbanalyze.exe /report:resolve /pstnid:12345
    dbanalyze.exe /report:mcus
    dbanalyze.exe /report:disk

## Resumo

O DBAnalyzer proporciona aos administradores uma forma rápida e fácil de analisar os bancos de dados do Lync Server 2013 .

## ImportStorageServiceData

A ferramenta do resource kit do ImportStorageServiceData permite a reimportação dos dados da Fila e do Ponto de extremidade que foram liberados do Serviço de Armazenamento (LYSS) para ele novamente.

## Descrição

A liberação dos dados do Serviço de armazenamento pode ter sido automática (periodicamente) com base no status do Item da fila ou no tamanho do banco de dados. Pode ter ocorrido devido a invocação manual do cmdlet failover pool ou cmdlet StorageServiceFullFlush (invocado pelo cmdlet failover pool). Observe que idealmente os dados não deverão ser reimportados se o tamanho de algum banco de dados do Serviço de armazenamento (LYSS) nos front ends estiver acima do nível normal, pois fazer isso fará com que mais dados tenham que ser exportados novamente. Além disso, todos os problemas que possam ter contribuído para os erros que fizeram com que a Fila do serviço de armazenamento aumentasse, deverão ser resolvidos primeiramente (por exemplo Exchange erros de ponto de extremidade, problemas na rede ou outros problemas).

**Cenário 1:** durante o pool failover, os arquivos poderão ser liberados do serviço de armazenamento de cada front end. Após a conclusão do failover, a ferramenta deverá ser executada para reimportar os dados.

**Cenário 2:** os dados que estiverem sendo liberados automaticamente diariamente ou que excederam os limites de tamanho determinados do banco de dados do Serviço de armazenamento (por exemplo: 60%, 80%, 90% da capacidade). Esses dados liberados automaticamente devem ser reimportados de forma rotineira pelo administrador. Na situação acima, se o pacote SCOM de monitoramento não for implantado, haverá eventos do Serviço de armazenamento do Lync Server relacionados aos dados que serão liberados do Serviço de armazenamento. As IDs de evento de 32075 (operação de liberação completa), 32076 (conclusão da liberação completa), 32082 (inicio da liberação do nível de manutenção), 32083 (conclusão da liberação do nível de manutenção), 32089 (liberação ocorrida devido ao preenchimento do banco de dados). Observe que as Ids de evento correspondem à versão do RTM. Se o administrador conseguir ver estes eventos, significa que há arquivos que foram liberados. Estes dados deverão ser importados novamente rotineiramente usando esta ferramenta, por exemplo, semanalmente.

Quanto à liberação do Atendimento online, se o pacote de monitoramente de saúde SCOM para Lync Server for implementado, haverá novos alertas que podem ser emitidos para pedir ao administrador para reimportar os dados liberados de volta ao Serviço de armazenamento. Haverá um evento correspondente no log de eventos no servidor Front End que acionou o alerta. O evento dará uma descrição do caminho pai sob o qual se encontram os arquivos de dados liberados, bem como a quantidade de arquivos que houver que atenda aos critérios do alerta. Os critério de alerta é de que há X ou mais arquivos no caminho do pai específico possuem pelo menos Y dias (onde X e Y são predefinidos dentro do StorageService, mas podem ser substituídos, alterando o arquivo APPCONFIG). Dois exemplos de eventos que podem disparar a alerta de saúde são mostrados abaixo, com a diferença sendo caminho do pai correspondente. Uma possibilidade está no compartilhamento de arquivo do serviço da Web, enquanto a outra possibilidade está no diretório de Dados de aplicativo local de cada front-end. (por exemplo c:\\ProgramData\\Microsoft\\Lync Server\\StorageService). O administrador irá, em seguida, executar esta ferramenta do reskit.

Esta ferramenta aumentará a carga de CPU e de E/S no front end que estiver sendo executado, e também em outros front ends se os dados não pertencerem ao front end no qual a ferramenta está sendo executada. Recomendamos executar essa ferramenta se os front ends não estiverem sob uma carga de E/S e CPU pesada, por exemplo, fora das horários de pico. Em segundo lugar, esta ferramenta leva de 2 a 3 minutos para importar um arquivo de dados. Lembre-se disso ao estimar por quanto tempo a ferramenta será executada. O arquivo de log detalhado gerado pela ferramenta será exibido de forma padrão no Armazenamento de arquivos. Exclua-o se houver algum erro informado, pois o arquivo de log pode ter milhares de MB ou mais.

![Amostra de eventos de registro de eventos do Servidor de Armazenamento.](images/JJ945604.3a903ef7-ea8a-4606-8229-a3e32f13af3a(OCS.15).jpg "Amostra de eventos de registro de eventos do Servidor de Armazenamento.")

## Requisitos

Instale o Lync Server 2013, Ferramentas do Resource Kit. A ferramenta será executada no computador que esteja associado a um domínio e no qual os Lync Server e Shell de Gerenciamento do Lync Server estejam instalados. A ferramenta usa um cmdlet do shell de gerenciamento para identificar todos os servidores Front End no pool. Em segundo lugar, a ferramenta deverá ser executada em um computador no pool que tenha o banco de dados **RtcLocal** instalado. Este banco de dados é usado pela ferramenta para recuperar a localização do compartilhamento do arquivo WEBSERVICE no pool. Além disso, antes de usar a ferramenta, cada servidor Front End deverá primeiramente habilitar o Windows PowerShell remotamente usando o **Enable-PSRemoting** em cada servidor Front End, assim como no computador onde a ferramenta está sendo executada. Caso contrário, os comandos remotos do Windows PowerShell desta ferramenta falharão. A comunicação remota do Windows PowerShell poderá ser desativada de todos os servidores Front End no pool após a conclusão. Por fim, a conta ou credencial que invocam a ferramenta devem ter permissão para ler/gravar no arquivo de serviço da web compartilhado com o pool que está executando a ferramenta. Do contrário, a ferramenta falhará com as Permissões de E/S.

> [!NOTE]
> No Windows Server 2012, Windows PowerShell, a comunicação remota é habilitada por padrão, mas não no Sistema operacional Windows Server 2008.


## Exemplos

    >  C:\StorageService>ImportStorageServiceData.exe
    Description:
    This tool will re-import Storage Service (LYSS) flushed queue data back in.  For a pool: you are required to run this tool on a machine inside the pool which has the Lync Server Management Shell installed.  Additionally, all front end machines need to have Windows Powershell Remoting enabled before executing this tool by executing Enable-PSRemoting.  Also, please ensure that all Storage Service instance DB Size are at the 'Normal' level (verify this by viewing Eventlog events). Otherwise re-importing may cause data to be flushed out again if any Storage Service instance DB size level goes above 'Normal'.
    Usage: Default behavior is to Import data from web service file share as well as any files on all Front End machines in pool.
    Additional Options:
    -Verbose                    : Turn verbose output on.
    
    -StorageServiceHostName     : Host Name of Storage Service WCF endpoint.  ( Default=localhost netnamedpipe binding. )
                                        
    -FileSharePath              : Import only all data from just under the UNC path specified.
    
    ActivityID: cc3b62ff-bb66-4e61-a6e2-96cb3626315c. <-- Use this to correlate with StorageService trace logs if troubleshooting.
    Type Server name (TCP binding) or press <enter> for localhost (NamePipe binding):
    Using NetNamedPipeBinding...
    OnTopologyChanged Event received
    Web Service File Share: \\dc.vdomain.com\OcsFileStore\co1-WebServices-1\StorageService
    
    Front Ends:
    server.vdomain.com
    server2.vdomain.com
    server1.vdomain.com
    server3.vdomain.com
    Looking under directory: \\dc.vdomain.com\OcsFileStore\co1-WebServices-1\StorageService for exported data.
    # Files found: 8
    Starting Import for file:\\dc.vdomain.com\OcsFileStore\co1-WebServices-1\StorageService\DataExport\2
    0120910\SERVER.vdomain.com\944f5724c65c5f93900dc1c8c898b102__0.xml
    Items deserialized: 20
    
    All items in file were enqueued successfully, will try to delete file: \\dc.vdomain.com\OcsFileStore\co1-WebServices-1\StorageService\DataExport\20120910\SERVER.vdomain.com\944f5724c65c5f93900dc1c8c898b102__0.xml
    
    All items in file failed to enqueue so file will not be deleted.  File path: \\dc.vdomain.com\OcsFileStore\co1-WebServices-1\StorageService\DataExport\20120910\SERVER.vdomain.com\944f5724c65c5f93900dc1c8c898b102__0.xml
    
    Summary for file \\dc.vdomain.com\OcsFileStore\co1-WebServices-1\StorageService\DataExport\20120910\SERVER.vdomain.com\944f5724c65c5f93900dc1c8c898b102__0.xml: succeeded: 20, failed: 0
    
    Starting Import for file:\\dc.vdomain.com\OcsFileStore\co1-WebServices-1\StorageService\DataExport\20120910\SERVER1.vdomain.com\17d5435ae40259f7bbdf1866776386e4__0.xml
    Items deserialized: 20
    
    [cc3b62ff-bb66-4e61-a6e2-96cb3626315c] Send EnqueueMessages to redirected, targetServer=server1.vdomain.com, queueItems=20
    
    All items in file were enqueued successfully, will try to delete file: \\dc.vdomain.com\OcsFileStore\co1-WebServices-1\StorageService\DataExport\20120910\SERVER1.vdomain.com\17d5435ae40259f7bbdf1866776386e4__0.xml
    
    All items in file failed to enqueue so file will not be deleted.  File path: \\dc.vdomain.com\OcsFileStore\co1-WebServices-1\StorageService\DataExport\20120910\SERVER1.vdomain.com\17d5435ae40259f7bbdf1866776386e4__0.xml
    
    Summary for file \\dc.vdomain.com\OcsFileStore\co1-WebServices-1\StorageService\DataExport\20120910\
    SERVER1.vdomain.com\17d5435ae40259f7bbdf1866776386e4__0.xml: succeeded: 20, failed: 0
    
    Starting Import for file:\\dc.vdomain.com\OcsFileStore\co1-WebServices-1\StorageService\DataExport\20120910\SERVER1.vdomain.com\904f6c9b8ac951ae8b3c86684d3832e4__0.xml
    
    Items deserialized: 20
    [cc3b62ff-bb66-4e61-a6e2-96cb3626315c] Send EnqueueMessages to redirected, targetServer=server1.vdomain.com, queueItems=20
    
    All items in file were enqueued successfully, will try to delete file: \\dc.vdomain.com\OcsFileStore
    \co1-WebServices-1\StorageService\DataExport\20120910\SERVER1.vdomain.com\904f6c9b8ac951ae8b3c86684d
    3832e4__0.xml
    
    All items in file failed to enqueue so file will not be deleted.  File path: \\dc.vdomain.com\OcsFil
    eStore\co1-WebServices-1\StorageService\DataExport\20120910\SERVER1.vdomain.com\904f6c9b8ac951ae8b3c
    86684d3832e4__0.xml
    
    
    Summary for file \\dc.vdomain.com\OcsFileStore\co1-WebServices-1\StorageService\DataExport\20120910\
    SERVER1.vdomain.com\904f6c9b8ac951ae8b3c86684d3832e4__0.xml: succeeded: 20, failed: 0
    
    Starting Import for file:\\dc.vdomain.com\OcsFileStore\co1-WebServices-1\StorageService\DataExport\2
    0120910\SERVER2.vdomain.com\69844a271e6c5633a1f2b46a42287dd6__0.xml
    
    Items deserialized: 20
    
    [cc3b62ff-bb66-4e61-a6e2-96cb3626315c] Send EnqueueMessages to redirected, targetServer=server2.vdom
    ain.com, queueItems=20
    
    All items in file were enqueued successfully, will try to delete file: \\dc.vdomain.com\OcsFileStore
    \co1-WebServices-1\StorageService\DataExport\20120910\SERVER2.vdomain.com\69844a271e6c5633a1f2b46a42
    287dd6__0.xml
    
    All items in file failed to enqueue so file will not be deleted.  File path: \\dc.vdomain.com\OcsFil
    eStore\co1-WebServices-1\StorageService\DataExport\20120910\SERVER2.vdomain.com\69844a271e6c5633a1f2
    b46a42287dd6__0.xml
    
    Summary for file \\dc.vdomain.com\OcsFileStore\co1-WebServices-1\StorageService\DataExport\20120910\
    SERVER2.vdomain.com\69844a271e6c5633a1f2b46a42287dd6__0.xml: succeeded: 20, failed: 0
    
    Starting Import for file:\\dc.vdomain.com\OcsFileStore\co1-WebServices-1\StorageService\DataExport\2
    0120910\SERVER3.vdomain.com\3313935458e35b9b9759e08a15d251e6__0.xml
    
    Items deserialized: 20
    
    [cc3b62ff-bb66-4e61-a6e2-96cb3626315c] Send EnqueueMessages to redirected, targetServer=server3.vdom
    ain.com, queueItems=1
    
    All items in file were enqueued successfully, will try to delete file: \\dc.vdomain.com\OcsFileStore
    \co1-WebServices-1\StorageService\DataExport\20120910\SERVER3.vdomain.com\3313935458e35b9b9759e08a15
    d251e6__0.xml
    
    All items in file failed to enqueue so file will not be deleted.  File path: \\dc.vdomain.com\OcsFil
    eStore\co1-WebServices-1\StorageService\DataExport\20120910\SERVER3.vdomain.com\3313935458e35b9b9759
    e08a15d251e6__0.xml
    
    Summary for file \\dc.vdomain.com\OcsFileStore\co1-WebServices-1\StorageService\DataExport\20120910\
    SERVER3.vdomain.com\3313935458e35b9b9759e08a15d251e6__0.xml: succeeded: 20, failed: 0
    
    Starting Import for file:\\dc.vdomain.com\OcsFileStore\co1-WebServices-1\StorageService\DataExport\2
    0120910\SERVER3.vdomain.com\4501e04eae4856059346949ff817c220__0.xml
    Items deserialized: 20
    [cc3b62ff-bb66-4e61-a6e2-96cb3626315c] Send EnqueueMessages to redirected, targetServer=server3.vdom
    ain.com, queueItems=1
    All items in file were enqueued successfully, will try to delete file: \\dc.vdomain.com\OcsFileStore
    \co1-WebServices-1\StorageService\DataExport\20120910\SERVER3.vdomain.com\4501e04eae4856059346949ff8
    17c220__0.xml
    All items in file failed to enqueue so file will not be deleted.  File path: \\dc.vdomain.com\OcsFil
    eStore\co1-WebServices-1\StorageService\DataExport\20120910\SERVER3.vdomain.com\4501e04eae4856059346
    949ff817c220__0.xml
    
    Summary for file \\dc.vdomain.com\OcsFileStore\co1-WebServices-1\StorageService\DataExport\20120910\
    SERVER3.vdomain.com\4501e04eae4856059346949ff817c220__0.xml: succeeded: 20, failed: 0
    Starting Import for file:\\dc.vdomain.com\OcsFileStore\co1-WebServices-1\StorageService\DataExport\2
    0120910\SERVER3.vdomain.com\5ad77443ad955a22a876749be66d5317__0.xml
    
    Items deserialized: 20
    [cc3b62ff-bb66-4e61-a6e2-96cb3626315c] Send EnqueueMessages to redirected, targetServer=server3.vdom
    ain.com, queueItems=20
    All items in file were enqueued successfully, will try to delete file: \\dc.vdomain.com\OcsFileStore
    \co1-WebServices-1\StorageService\DataExport\20120910\SERVER3.vdomain.com\5ad77443ad955a22a876749be6
    6d5317__0.xml
    All items in file failed to enqueue so file will not be deleted.  File path: \\dc.vdomain.com\OcsFil
    eStore\co1-WebServices-1\StorageService\DataExport\20120910\SERVER3.vdomain.com\5ad77443ad955a22a876
    749be66d5317__0.xml
    Summary for file \\dc.vdomain.com\OcsFileStore\co1-WebServices-1\StorageService\DataExport\20120910\
    SERVER3.vdomain.com\5ad77443ad955a22a876749be66d5317__0.xml: succeeded: 20, failed: 0
    Starting Import for file:\\dc.vdomain.com\OcsFileStore\co1-WebServices-1\StorageService\DataExport\2
    0120910\SERVER3.vdomain.com\a11e27ae439a582288d4657eda86b565__0.xml
    Items deserialized: 20
    [cc3b62ff-bb66-4e61-a6e2-96cb3626315c] Send EnqueueMessages to redirected, targetServer=server3.vdom
    ain.com, queueItems=20
    All items in file were enqueued successfully, will try to delete file: \\dc.vdomain.com\OcsFileStore
    \co1-WebServices-1\StorageService\DataExport\20120910\SERVER3.vdomain.com\a11e27ae439a582288d4657eda
    86b565__0.xml
    All items in file failed to enqueue so file will not be deleted.  File path: \\dc.vdomain.com\OcsFil
    eStore\co1-WebServices-1\StorageService\DataExport\20120910\SERVER3.vdomain.com\a11e27ae439a582288d4
    657eda86b565__0.xml
    Summary for file \\dc.vdomain.com\OcsFileStore\co1-WebServices-1\StorageService\DataExport\20120910\
    SERVER3.vdomain.com\a11e27ae439a582288d4657eda86b565__0.xml: succeeded: 20, failed: 0
    All files have been imported into Storage Service for path: \\dc.vdomain.com\OcsFileStore\co1-WebSer
    vices-1\StorageService
    Importing files for: server.vdomain.com
    No files founds.
    Importing files for: server2.vdomain.com
    No files founds.
    Importing files for: server1.vdomain.com
    No files founds.
    Importing files for: server3.vdomain.com
    No files founds.
    Writing log: \\dc.vdomain.com\OcsFileStore\co1-WebServices-1\StorageService\ImportStorageServiceData
    Log20120910_1609SS
    Tool has finished execution.
    >  C:\StorageService>

## LCSSync

A ferramenta LCSSync ajuda a implantar o software de comunicação do Lync Server 2013 em um ambiente com diversas florestas. Essa ferramenta é usada para sincronizar usuários e grupos de diversas florestas de usuários, assim como o objeto de contato dos Serviços de Domínio Active Directory para uma floresta central onde tenha o Lync Server 2013 instalado.

## Descrição

O LCSSync usa os objetos de contato sincronizados dos Serviços de Domínio Active Directory na floresta central para habilitar usuários para o Lync Server. Para fornecer logon único, a conta de usuário principal deverá ser mapeada para o objeto de contato dos Serviços de Domínio Active Directory na floresta central para o Lync Server 2013. Esta ferramenta ajuda a realizar o mapeamento. Ela também fornece modelos para a criação de Agentes de gerenciamento no Microsoft Identity Integration Server.

## Resumo

A ferramenta LCSSync ajuda a implantar o Lync Serve em um ambiente com diversas florestas.

## LookupUserConsole

A ferramenta LookupUserConsole exibe as informações de roteamento internas do Lync Server de usuários específicos. Estas informações poderão ser úteis para suporte pessoal da Microsoft na implantação de diagnóstico e problemas de roteamento.

## Descrição

Executar o LookupUserConsole.exe abrirá um prompt de comando que aceitará endereços SIP e tentará exibir as informações de roteamento internas do Lync Server relacionadas. Digite **exit** para encerrar a ferramenta LookupUserConsole.

## Requisitos

Instale o Lync Server 2013, Ferramentas do Resource Kit. A ferramenta será executada nos computadores que estejam associados a um domínio que tenha o Lync Server instalado.

## Exemplos

C:\\Arquivos de Programas\\Microsoft Lync Server 2013\\ResKit\>LookupUserConsole.exe

    > sip:john.doe@vdomain.com
    
      Execution time (ms):                            171.094
      Exeuction result:                               Success
      SIP URI:                                        sip:john.doe@vdomain.com
      User info:
        SID:                                          S-1-5-21-2831376166-29632525...    Display name:                                     John Doe
        Grouping ID:                                  00000000-0000-0000-0000-...
        Line URI:                                     <null>
        Policy assignment:                            TenantId={00000000--0000-000....
        SIP enabled:                                  True
        UC enabled:                                   False
        Tenant ID:                                    00000000-0000-0000-0000-...  Cluster info:
        Active cluster:                               pool0.vdomain.com
        Backup registrar cluster:                     <null>
        Deployment location:                          <null>
        Home Front-End FQDN:                          SERVER.vdomain.com
        Primary Registrar cluster:                    pool0.vdomain.com
        Remote Director external SIP FQDN:            <null>
        Remote Director internal SIP FQDN:            <null>
        Remote Director Web FQDN:                     <null>
        Routing group ID:                             4501e04e-ae48-5605-9346...
        Service tag ID:                               1266953005
        User Front-End resolved:                      True
        User in local forest:                         True
        User in remote forest:                        False
        User in split domain:                         False
        User-Services cluster:                        pool0.vdomain.com
    
    > sip:nouser@vdomain.com
    
      Execution time (ms):                            948.7574
      Exeuction result:                               UserDoesNotExist
    
    > exit

## MsTurnPing

A ferramenta MSTurnPing permite ao administrador do software de comunicações do Microsoft Lync Server 2013 verificar o status dos servidores que estejam executando os serviços de Autenticação de áudio/vídeo e Borda de áudio/vídeo, assim como os servidores que estejam executando os Serviços de política de largura de banda na topologia.

## Descrição

A ferramenta MSTurnPing permite ao administrador do software de comunicações do Lync Server 2013 verificar o status dos servidores que estejam executando os serviços de Autenticação de áudio/vídeo e Borda de áudio/vídeo, assim como os servidores que estejam executando os Serviços de política de largura de banda na topologia.

A ferramenta permite ao administrador realizar os seguintes testes:

1.  Teste do Servidor de borda de áudio/vídeo: Esta ferramenta realiza testes em todos os Servidores de borda de áudio/vídeo na topologia ao executar as seguintes ações:
    
      - Verifica se o serviço de Autenticação de áudio/vídeo do Lync Server foi iniciado e se pode emitir as devidas credenciais.
    
      - Verifica se o serviço Edge de áudio/vídeo do Lync Server foi iniciado e se é possível alocar com êxito os recursos nas bordas externas.

2.  Teste do Serviço de Política de Largura de Banda: essa ferramenta realiza testes nos servidores que estejam executando os Serviços de política de largura de banda na topologia ao executar as seguintes ações:
    
      - Verifica se o Serviço de Política de Largura de Banda (Autenticação) do Lync Server foi iniciado e se pode emitir as devidas credenciais.
    
      - Verifica se o Serviço de Política de Largura de Banda (Núcleo) do Lync Server foi iniciado e se pode realizar com êxito a verificação da largura de banda.

Esta ferramenta deve ser executada em um computador que faça parte da topologia e tenha o armazenamento local instalado.

## Resultado

Esta ferramenta gera os resultados de cada uma das operações.

  - Se o teste **AudioVideoEdgeServer** for realizado, a ferramenta gerará o seguinte:
    
      - Os resultados do teste dos computadores que forneceram o serviço de Autenticação de áudio/vídeo do Lync Server na topologia
    
      - Os resultados do teste dos computadores que forneceram o serviço de Borda de áudio/vídeo do Lync Server na topologia

  - Se o teste **BandwidthPolicyServer** for realizado, a ferramenta gerará o seguinte:
    
      - Os resultados do teste dos computadores que forneceram o Serviço de Política de Largura de Banda do Lync Server na topologia
    
      - Os resultados do teste dos computadores que forneceram o Serviço de Política de Largura de Banda do Lync Server (Núcleo) na topologia

## Requisitos

  - Esta ferramenta deve ser executada em um computador que faça parte da topologia e tenha o armazenamento local instalado.

  - A ferramenta deve ser executada por um administrador que tenha acesso ao armazenamento local.

## Exemplos

Abaixo há um exemplo de entrada de ferramenta.

    MsTurnPing -ServerRole AudioVideoEdgeServer
    
    MsTurnPing -ServerRole BandwidthPolicyServer

## Resumo

Esta ferramenta poderá ser um recurso valioso para os administradores do Lync Server 2013 que queiram verificar o status dos servidores que estejam executando os serviços de política de largura de banda e áudio/vídeo.

## Visualizador da configuração de rede

O Visualizador da configuração de rede pode ser usado pelos administradores do software de comunicações do Microsoft Lync Server 2013 para visualizar a topologia da rede do controle de admissão de chamadas (CAC) de uma rede corporativa que seja provisionada para permitir sessões de comunicação em tempo real, tais como chamadas por voz ou vídeo com base na capacidade da largura de banda especificada. Os administradores do Lync Server 2013 definem as políticas do CAC, que são impostas pelos serviços da Política de largura de banda instalados com o Lync Server 2013.

## Descrição

O Visualizador da configuração de rede (NetworkConfigurationViewer.exe) permite aos administradores executar as seguintes tarefas:

  - Carrega e exibe a topologia de rede do CAC de uma implantação do Lync Server 2013 em um formato gráfico.

  - Carrega e visualiza a topologia de rede do CAC de um arquivo de log do Servidor de política de largura de banda em um formato gráfico.

  - Salva e armazena no disco a topologia de rede do CAC no formato XML.

  - Salva e armazena o diagrama da topologia de rede do CAC no formato JPG ou BMP.

  - Exibe os dados de configuração da topologia de rede do CAC.

  - Exibe a topologia de rede do CAC no estilo de modo de exibição de árvore.

  - Define conectores personalizados para os links da topologia de rede do CAC (por exemplo, site para região, região para site e site para links de site).

  - Exibe as informações do site de topologia de rede do CAC, informações da região e links de rede e políticas de largura de banda provisionadas.

## Objetivo

Exibe os links de topologia de rede do CAC da empresa em uma interface gráfica.

## Exemplos

**Carrega e exibe a topologia de rede do CAC de uma implantação do Lync Server 2013 em um formato gráfico:** Os administradores do Lync Server 2013 podem carregar e visualizar a configuração da topologia de rede do CAC em qualquer computador do Lync Server 2013 usando a opção **Download da configuração de rede**, conforme mostrado na figura abaixo. A ferramenta falhará ao fazer o download ou ao exibir essa configuração se for implantada em um computador que não tenha conectividade com o armazenamento de configuração do Lync.

![Baixando configurações de rede.](images/JJ945604.8d126d3f-2545-4f13-a244-974f09614982(OCS.15).jpg "Baixando configurações de rede.")

**Carrega e exibe a topologia de rede do CAC de um arquivo de log no servidor de Política de largura de banda em um formato gráfico: Os servidores de Política de largura de banda do** Lync Server 2013 salvam a topologia de rede do CAC como uma parte do mecanismo de registro de log no local de compartilhamento de arquivo do Lync Server 2013. Os administradores do Lync Server podem exibir um arquivo em um formato gráfico usando a opção **Abrir Configuração da Rede** conforme mostrado abaixo:

![Abrindo um arquivo de registro do Servidor de Políticas de Largura de Banda.](images/JJ945604.3e503e92-aacb-4921-a8d2-23f860fe2df6(OCS.15).jpg "Abrindo um arquivo de registro do Servidor de Políticas de Largura de Banda.")

Salvar e armazenar no disco a topologia de rede do CAC no formato XML: os administradores do Lync Server 2013 podem salvar o arquivo de configuração da topologia de rede do CAC no formato XML usando a opção **Salvar uma cópia da configuração de rede**, conforme mostrado abaixo. O arquivo de configuração salvo pode ser usado offline para fins de visualização gráfica.

![Salvando a configuração de rede como arquivo XML.](images/JJ945604.6eeef3b0-78b5-4ee6-8d94-1a4ddf3d8676(OCS.15).jpg "Salvando a configuração de rede como arquivo XML.")

Salvar e armazenar o diagrama da topologia de rede do CAC no formato JPG ou BMP: os administradores do Lync Server 2013 podem salvar a configuração da topologia de rede do CAC em um formato gráfico (formatos de arquivo JPG e BMP) usando a opção **Salvar diagrama de configuração de rede como imagem**, conforme mostrado abaixo:

![Salvando a configuração de rede como imagem.](images/JJ945604.145a6fb9-58b1-46b1-bbd5-a661ceba07b4(OCS.15).jpg "Salvando a configuração de rede como imagem.")

**Exibir os dados de configuração da topologia de rede do CAC: os administradores do**Lync Server 2013 podem exibir os dados de configuração de rede relacionados, tais como, regiões da rede, sites da rede, perfis de largura de banda e endereços de IP da sub-rede do site em um formato de texto usando a opção de dados Visualizar configuração da rede, conforme mostrado abaixo:

![Exibindo dados de configuração de rede.](images/JJ945604.b72a4c21-a042-4d91-bf96-fcb396af0679(OCS.15).jpg "Exibindo dados de configuração de rede.")

**Exibir a topologia de rede do CAC no estilo de modo de exibição de árvore: Os administradores do** Lync Server 2013 podem visualizar os dados de configuração da rede relacionada no estilo de modo de exibição de árvore usando o painel de controle na lateral esquerda da janela de ferramentas, conforme mostrado abaixo:

![Exibindo dados de configuração de rede na visualização de árvore.](images/JJ945604.4d924ac9-fd96-430f-b211-ee35b7ef9a23(OCS.15).jpg "Exibindo dados de configuração de rede na visualização de árvore.")

**Definir conectores personalizados para os links de topologia de rede do CAC (tais como site para região, região para região e site para links de site): Os administradores do** Lync Server 2013 podem definir conectores gráficos personalizados para os links WAN da configuração da rede do CAC usando a opção Configurações, conforme mostrado abaixo. Isto ajudar a diferenciar os tipos de links de rede provisionados na configuração da rede.

![b20bea67-c8e1-453e-b1dd-e2aa17b62566](images/JJ945604.b20bea67-c8e1-453e-b1dd-e2aa17b62566(OCS.15).jpg "b20bea67-c8e1-453e-b1dd-e2aa17b62566")

**Exibir informações do site da topologia de rede do CAC, informações da região e políticas de largura de banda provisionadas: Os administradores do** Lync Server 2013 podem exibir as informações da região da rede do CAC relacionado, informações do site e informações de provisionamento da largura de banda do CAC usando as opções mostradas abaixo. (Por exemplo, clique em **Informações** no objeto do site da rede ou região da rede).

![Definindo conectores personalizados para sua rede.](images/JJ945604.26262c75-4342-41c3-bc98-1793aa6a7713(OCS.15).jpg "Definindo conectores personalizados para sua rede.")

## Resumo

Esta ferramenta pode ser um recurso valioso para os administradores do Lync Server 2013 que gostariam de visualizar a topologia de rede do CAC para sua implantação em um formato gráfico.

## Agente de Grupo de Respostas Dinâmico

O aplicativo Grupo de Respostas proporciona aos agentes a capacidade de acessar as informações úteis em tempo real usando o serviço da Web embutido. Infelizmente, nenhuma visualização gráfica destes dados está disponível fora do aplicativo. A ferramenta do Resource Kit do Agente de Grupo de Respostas Dinâmico soluciona este problema ao fornecer uma forma simples e gráfica de acessar estas informações, aprimorada com as informações do software de comunicações do Microsoft Lync 2013 em tempo real, tais como a presença de outros agentes.

## Descrição

O Agente de Grupo de Respostas Dinâmico é um aplicativo do Windows que fornece a funcionalidade de entrar e sair, assim como algumas informações em tempo reais (tais como membros do grupo e número de chamadas atuais) para os agentes do Grupo de Respostas. Trata-se de uma versão aprimorada da página Grupo de agentes (acessível a partir do Lync 2013.

## Objetivo

O aplicativo Grupo de Respostas enfileira as chamadas recebidas e, em seguida, as encaminha para o grupo de agentes . Para tomar decisões conscientes sobre quais chamadas devem ser atendidas, os agentes podem acessar informações em tempo real sobre os grupos de agentes, assim como quais são outros agentes disponíveis e quantas chamadas estão esperando em cada fila. Estas informações, inicialmente somente acessadas pelo serviço do Grupo de Respostas, são disponibilizadas de uma forma intuitiva pelo Agente de Grupo de Respostas Dinâmico.

## Recursos

A ferramenta Agente de Grupo de Respostas Dinâmico está embutida no serviço do Grupo de Respostas e no SDK do Microsoft Lync 2013. E fornece aos agentes do Grupo de Respostas as informações e habilidades disponíveis no serviço de Grupo de Respostas (tais como membros do grupo, presença de outros agentes e número de chamadas em espera).

A figura abaixo ilustra a interface principal do Agente de Grupo de Respostas Dinâmico.

![A ferramenta Agente de Grupo de Respostas Dinâmico.](images/JJ945604.63cb0374-a6ef-4a59-b60e-bec86a880d09(OCS.15).jpg "A ferramenta Agente de Grupo de Respostas Dinâmico.")

Os seguintes três recursos principais estão disponíveis para agentes do Agente de Grupo de Respostas Dinâmico:

  - **Entrar/sair:** Ao contrário da página Grupos de agentes (acessada pelo Lync 2013), urgente de Grupo de Respostas Dinâmico permite apenas que agentes entrem ou saiam de todos os grupos de agentes de uma só vez. Este aplicativo fornece três formas rápidas para os agentes entrarem ou saírem:
    
      - Clique nos botões Entrar/sair (verde e vermelho) do aplicativo.
    
      - Clique com o botão direito do mouse no ícone de bandeja do sistema e selecione entrar ou sair.
    
      - Usando os atalhos do teclado configurável.

  - **Membros do grupo** Se um grupo de agentes for selecionado, o Agente de Grupo de Respostas Dinâmico exibirá a lista dos agentes no grupo no painel à direita. Se o Lync 2013 estiver sendo executado no mesmo computador deste aplicativo, as informações de presença e cartão de visita serão exibidas no Agente de Grupo de Respostas Dinâmico. Os agentes poderão enviar uma MI ou chamar outros agentes diretamente dali.

  - **Estatísticas em tempo real:** O Agente de Grupo de Respostas Dinâmico fornece estatísticas em tempo real para todos os grupos de agentes. A frequência de atualização fica em torno de um minuto. Se uma chamada for respondida por um Grupo de Respostas, um indicador visual será adicionado próximo ao nome do grupo com o número atual de chamadas em fila. Pausar o ponteiro sobre um grupo também exibe o tempo de espera mais longo.

## Requisitos

O Agente de Grupo de Respostas Dinâmico requer o .NET Framework 4.0. Além disso, para aproveitar os recursos de cartão de visita e presença, o Lync 2013 deverá ser instalado localmente (e estar em execução).

## Configuração

O Agente de Grupo de Respostas Dinâmico pode ser personalizado de acordo com as preferências individuais usando a caixa de diálogo Opções no aplicativo. Além disso, o administrador pode definir o endereço de host padrão editando diretamente a propriedade defaultHostAddress do arquivo RGAgentLive.exe.config.

A figura abaixo ilustra a caixa de diálogo Opções que os agentes podem usar para configurar as teclas de atalho e endereços de host. Essa caixa de diálogo é acessada clicando no botão Opções no lado direito superior da interface principal.

![A caixa de diálogo de opções do Agente de Grupo de Respostas Dinâmico.](images/JJ945604.3cc15e29-8699-45ab-90c3-e1565fa6ebf6(OCS.15).jpg "A caixa de diálogo de opções do Agente de Grupo de Respostas Dinâmico.")

As três configurações diferentes abaixo podem ser personalizadas na configuração do Agente de Grupo de Respostas Dinâmico:

  - Endereço de host: esse é um pool da web FQDN que pertence ao pool da página inicial do agente. O endereço de serviço exato do Grupos de respostas é automaticamente derivado no plano de fundo desta informação (anexado no caminho à direita depois do host).

  - Atalhos: Os atalhos exatos para entrar/sair podem ser personalizados. A única limitação é que ambos os atalhos devem conter a tecla "Logotipo do Windows" (além de pelo menos outra tecla).

  - Iniciando com o Windows: O aplicativo pode ser configurado para ser iniciado automaticamente com o Windows.

## Exemplos

A figura abaixo ilustra como chamar ou enviar uma MI para outro agente clicando com o botão direito do mouse no contato no painel à direita.

![Realizar uma chamada ou enviar chat.](images/JJ945604.009cebe0-5a93-4745-89c3-8a16c7c13009(OCS.15).jpg "Realizar uma chamada ou enviar chat.")

A figura abaixo ilustra como o Agente de Grupo de Respostas Dinâmico exibe o número de chamadas atuais em fila e o tempo de espera mais longo entre todas as chamadas recebidas.

![Visualizando informações da fila.](images/JJ945604.131d7f79-b7ed-41f5-a9da-ffc556e31037(OCS.15).jpg "Visualizando informações da fila.")

## Resumo

Rápida entrada e saída, membros do grupo e estatísticas em tempo real são recursos interessantes do agente do Grupo de resposta que agora estão disponíveis fora do aplicativo do serviço de Grupo de Respostas. Com a ferramenta do Resource Kit do Agente de Grupo de Respostas Dinâmico, os administradores do Lync podem fornecer aos seus agentes um aplicativo do Windows que permite a execução de tarefas de uma forma gráfica e rápida.

## SEFAUtil

O SEFAUtil (ativação de recurso de extensão secundária) é uma ferramenta de linha de comando que permite aos agentes de suporte técnico e administradores do software de comunicações do Microsoft Lync Server 2013 configurarem a delegação da campainha, encaminhamento de chamadas, toques simultâneos, configurações da chamada de equipe e recebimento de chamada de grupo em nome de um usuário do Lync Server 2013. Essa ferramenta também permite aos administradores consultarem as configurações de roteamento de chamadas publicadas para um determinado usuário.A ferramenta SEFAUtil permite ao administrador habilitar/desabilitar/modificar o encaminhamento de chamadas em nome do usuário. Essa ferramenta também permite aos administradores adicionarem ou removerem membros do grupo de chamada de equipe ou delegações em nome do usuário. Esta ferramenta está embutida no Microsoft Unified Communications Managed API (UCMA) 3.0 e requer que os administradores criem um aplicativo confiável no armazenamento de Gerenciamento Central para o SEFAUtil

O SEFAUtil (ativação de recurso de extensão secundária) permite aos administradores e agentes de suporte técnico do Lync Server 2013 configurarem a delegação da campainha, encaminhamento de chamadas, toques simultâneos, configurações da chamada de equipe e recebimento de chamada de grupo em nome de um usuário do Lync Server 2013. Esta ferramenta também permite aos administradores consultar as configurações do roteamento de chamadas publicadas para um determinado usuário.

## Descrição

A versão atual do SEFAUtil é apenas uma ferramenta de linha de comando; não há nenhum suporte para interface de usuário gráfica. Essa ferramenta está baseada no Microsoft Unified Communications Managed API (UCMA) 3.0. Os recursos desta ferramenta permitem aos administradores e agentes de suporte técnico executarem as seguintes ações:

  - Exibir as configurações do roteamento de chamada de um usuário (inclui encaminhamento de chamadas, delegação, toque simultâneo, chamada de equipe e recebimento de chamada de grupo)

  - Habilitar/desabilitar/modificar a configuração do encaminhamento de chamadas (inclui temporizador de resposta e destino)

  - Habilitar/desabilitar/modificar configurações do encaminhamento de chamadas imediato

  - Habilitar/desabilitar/modificar configurações de delegação

  - Habilitar/desabilitar/modificar configurações do grupo de chamadas de equipe
    
    > [!NOTE]
    > Novidade na ferramenta Lync Server 2013 SEFAUtil


  - Habilitar/desabilitar/modificações configurações de toques simultâneos (inclui destino)
    
    > [!NOTE]
    > Novidade na ferramenta Lync Server 2013 SEFAUtil


  - Habilitar/desabilitar/modificar configurações do recebimento de chamada de grupo
    

    > [!WARNING]
    > Novidade na ferramenta Lync Server 2013 SEFAUtil



Esta ferramenta possui as seguintes limitações:

  - É suportada apenas por usuários hospedados em um pool do Lync Server

  - A edição em massa de configurações de roteamento de chamada para diversos usuários não é suportada

## Resultado

A versão atual desta ferramenta fornece resultados apenas na janela Prompt de comando. Para mais detalhes, consulte posteriormente a seção Exemplos neste documento.

## Objetivo

Abaixo há alguns exemplos de cenários chave onde esta ferramenta pode ser usada:

  - Bob é um executivo e mudou para telefonia do Lync Server. Ele tem representação em seu sistema de PBX existente. Como parte da mudança para o Lync, o administrador é capaz de configurar o roteamento de Bob para refletir sua configuração de representação pré-existente.

  - Alice está viajando e percebe que está aguardando uma chamada importante de um de seus clientes. No entanto, ela está em um hotel e não tem acesso a um computador. Ela liga para assistência técnica e solicita que eles encaminhem todas as chamadas feitas para seu número de trabalho para o seu para seu número de celular. O pessoal de assistência técnica é capaz de fazer a configuração em seu nome.

  - As chamadas de Joe para seu número de trabalho vão para a caixa postal de seu celular sempre que ele está no trabalho; no entanto, as coisas parecem estar funcionando corretamente na maioria dos outros locais. O técnico da assistência técnica é capaz de visualizar a configuração de roteamento e descobre que Joe tem o toque simultâneo configurado em seu celular. O técnico pergunta a Joe sobre a cobertura móvel em seu escritório e é capaz de determinar que a regra de toque simultâneo é o que faz com que as chamadas sejam encaminhadas para a caixa postal do celular de Joe quando sua cobertura de rede está fraca.

  - Mike é um funcionário novo da Contoso e está se juntando a uma nova equipe na qual todos os membros são configurados para a chamada de equipe. Depois de serem habilitados para o Microsoft Lync, o administrador é capaz de definir para que suas definições de grupo de chamada de equipe incluam os novos membros de sua equipe. Além disso, o administrador adiciona Mike como um membro do grupo de chamada de equipe para cada um dos membros de sua equipe.

  - Uma prática de atendimento ao cliente no departamento de recursos humanos da Contoso é fornecer um atendimento pessoal para todos os chamadores desde a primeira chamada. Uma vez que todos os membros do departamento sentam muito próximos uns dos outros, ter todos os telefones tocando ao mesmo tempo com a chamada de equipe é muito perturbador para a equipe. Para fornecer o melhor atendimento serviço sem atrapalhar os membros da equipe, o administrador do Lync tira proveito do recurso de Recebimento de Chamadas em Grupo. O administrador adiciona todos os membros do departamento a um grupo de recebimento e informa o número do grupo de recebimento ao departamento. Quando Samantha está fora de sua mesa, Joe percebe que seu telefone e responde a chamada de sua mesa.

## Requisitos

A ferramenta SEFAUtil pode ser executada apenas em um computador que faça parte de um Pool de aplicativo confiável. O UCMA 3.0 deve ser instalado nesse computador. Para executar a ferramenta, um novo Aplicativo confiável com a ID do aplicativo SEFAUtil deve ser criado nesse pool.

**Criando um novo Aplicativo Confiável para a ferramenta SEFAUtil**

1.  A ferramenta SEFAUTil pode ser executada apenas em um computador que faça parte de um pool de aplicativo confiável. Se necessário, adicionar um pool como um novo pool de aplicativo confiável pode ser feito por meio do Shell de gerenciamento do Lync Server com o seguinte cmdlet:
    
        New-CsTrustedApplicationPool -id <Pool FQDN> -Registrar <Pool Registrar FQDN> -site Site:<Pool Site>
    
    > [!NOTE]
    > O UCMA 3.0 deve ser instalado em qualquer computador seja usado para executar a ferramenta SEFAUtil.


2.  Um aplicativo confiável precisa ser definido na topologia da ferramenta SEFAUtil. Para definir SEFAUtil como um novo aplicativo confiável, use o Shell de Gerenciamento do Lync Server e execute o seguinte cmdlet:
    
        New-CsTrustedApplication -ApplicationId sefautil -TrustedApplicationPoolFqdn <Pool FQDN>  -Port 7489
    
    > [!NOTE]
    > Uma porta diferente pode ser usada se necessário.


3.  As alterações de topologia precisam ser habilitadas. A habilitação das alterações de topologia pode ser feita via Shell de gerenciamento do Lync Server ao executar o seguinte cmdlet:
    
        Enable-CsToplogy

4.  Se necessário, instale as ferramentas do Resource Kit do Lync Server 2013 no servidor que será usado para executar a ferramenta SEFAUtil (o servidor deve fazer parte de um pool de aplicativo confiável).

5.  Verifique se o SEFAUtil está sendo executado corretamente. Para fazer isso, execute a ferramenta a partir de um prompt de comando do Windows com privilégios de administrador de modo a exibir as configurações de encaminhamento de chamada de um usuário na implementação. Por padrão, a ferramenta será localizada em: “…\\Arquivos de Programas\\Microsoft Lync Server 2013\\Reskit”. Para exibir as configurações de chamada de um usuário, use o comando a seguir:
    
        SEFAUtil.exe <user SIP address> /server:<Lync Server/Pool FQDN>
    
    As configurações de encaminhamento de chamada do usuário devem ser exibidas.

## Recebimento de Chamadas em Grupo

O Recebimento de Chamadas em Grupo requer que a configuração adicional no Lync Server referente ao recurso esteja totalmente habilitada. Antes de atribuir grupos de recebimento aos usuários, consulte a documentação do produto Recebimento de Chamadas em Grupo para as etapas de planejamento e implementação deste recurso.

## Exemplos

## Exibir configurações atuais de administração de chamadas

O comando a seguir exibe a administração de chamadas do usuário. `SEFAUtil.exe /server:lyncserver.contoso.com katarina@contoso.com`

> [!NOTE]
> Este exemplo usa a opção <strong>/server</strong> para especificar o Lync Server a se conectar.


**Resultado**

    User Aor: sip:katarina@contoso.com
    Display Name: Katarina Larsson
    UM Enabled: True
    Simulring enabled: False
    User Ring time: 00:00:20
    Call Forward No Answer to: voicemail

## Definir Destino de Encaminhamento de Chamadas/destino sem Resposta

Este exemplo define o encaminhamento de chamadas/destino sem resposta e o atraso de toque. Aqui a opção /servidor não é fornecida; SEAUtil tenta descobrir automaticamente o Lync Server

    SEFAUtil.exe /server:lyncserver.contoso.com sip:katarina@contoso.com /enablefwdnoanswer /callanswerwaittime:30 /setfwddestination:+1425555 0126@contoso.com;user=phone

**Resultado**

    User Aor: sip:katarina@contoso.com
    Display Name: Katarina Larsson
    UM Enabled: True
    Simulring enabled: False
    User Ring time: 00:00:30
    Call Forward No Answer to: sip:+14255550126@contoso.com;user=phone

## Habilitar Imediatamente o Encaminhamento de Chamadas

Este exemplo habilita imediatamente o encaminhamento de chamadas para outro usuário

    SEFAUtil.exe sip:katarina@contoso.com /enablefwdimmediate /setfwddestination:anders@contoso.com

**Resultado**

    User Aor: sip:katarina@contoso.com
    Display Name: Katarina Larsson
    UM Enabled: True
    Simulring enabled: False
    Forward immediate to: sip:anders@contoso.com

## Desabilitar Imediatamente o Encaminhamento de Chamadas

Este exemplo desabilita imediatamente o encaminhamento de chamadas

    SEFAUtil.exe /server:lyncserver.contoso.com katarina@contoso.com  /disablefwdimmediate

**Resultado**

    User Aor: sip:katarina@contoso.com
    Display Name: Katarina Larsson
    UM Enabled: True
    Simulring enabled: False
    User Ring time: 00:00:30
    Call Forward No Answer to: voicemail

## Adicionar um usuário como um delegado e configurar toque simultâneo dos delegados

Este exemplo adiciona um usuário como um delegado e configura o toque simultâneo dos delegados:

    SEFAUtil.exe /server:lyncserver.contoso.com sip:katarina@contoso.com /adddelegate:joe@contoso.com /simulringdelegates

**Resultado**

    User Aor: sip:katarina@contoso.com
    Display Name: Katarina Larsson
    UM Enabled: True
    Simultaneously Ringing Delegates: sip:joe@contoso.com

## Alterar Regra de Toque Simultâneo dos Representantes

Este exemplo altera a regra de toque simultâneo que foi definida no exemplo anterior à regra de toque exibida.

    SEFAUtil.exe /server:lyncserver.contoso.com sip:katarina@contoso.com /delayringdelegates:10

**Resultado**

    User Aor: sip:katarina@contoso.com
    Display Name: Katarina Larsson
    UM Enabled: True
    Simulring enabled: False
    Delay Ringing Delegates (delay:10 seconds): sip:joe@contoso.com

## Remover o representante

Este exemplo remove o representante

> [!NOTE]
> Quando o ultimo representante delegado é removido, o toque do representante é desabilitado automaticamente.


    SEFAUtil.exe /server:lyncserver.contoso.com sip:katarina@contoso.com /removedelegate:joe@contoso.com

**Resultado**

    User Aor: sip:katarina@contoso.com
    Display Name: Katarina Larsson
    UM Enabled: True
    Simulring enabled: False
    User Ring time: 00:00:30
    Call Forward No Answer to: voicemail

## Adicionar um Representante e Configurar a Regra de Encaminhamento de Chamadas para Representantes

Este exemplo adiciona um representante e configura a regra de encaminhamento de chamadas para representantes.

    SEFAUtil.exe /server:lyncserver.contoso.com sip:katarina@contoso.com /adddelegate:anders@contoso.com /fwdtodelegates

**Resultado**

    User Aor: sip:katarina@contoso.com
    Display Name: Katarina Larsson
    UM Enabled: True
    Forwarding calls to Delegates: sip:anders@contoso.com

## Habilitar Toque Simultâneo e Definir um Número de Destino

Este exemplo habilita o toque simultâneo e define o número de destino do toque simultâneo.

    SEFAUtil.exe /server:lyncserver.contoso.com sip:katarina@contoso.com /setsimulringdestination:+14255550126 /enablesimulring

> [!NOTE]
> Para alterar o número de destino do toque simultâneo de um usuário cujo toque simultâneo já está habilitado, mantenha o comando com a opção /enablesimulring, do contrário o número de destino não será alterado.


**Resultado**

    User Aor: sip:katarina@contoso.com
    Display Name: Katarina Larsson
    UM Enabled: True
    Simulring enabled: True
    Simul_Ringing to: sip:+14255550126@contoso.com;user=phone

## Desabilitar Toque Simultâneo

Este exemplo desabilita o toque simultâneo.

    SEFAUtil.exe /server:lyncserver.contoso.com sip:katarina@contoso.com /disablesimulring

**Resultado**

    User Aor: sip:katarina@contoso.com
    Display Name: Katarina Larsson
    UM Enabled: True
    Simulring enabled: False
    User Ring time: 00:00:30
    Call Forward No Answer to: voicemail

## Adicionar um membro de equipe para chamada de equipe e configurar o toque simultâneo para o grupo de membros de chamada de equipe

Este exemplo adiciona um membro de equipe ao grupo de chamada de equipe de um usuário e habilita o toque simultâneo para o grupo de chamada.

    SEFAUtil.exe /server:lyncserver.contoso.com sip:katarina@contoso.com /addteammember:anders@contoso.com /simulringteam

> [!NOTE]
> Adicionar um membro ao grupo de chamada de um usuário alternará automaticamente as configurações de toque simultâneo dos usuários para equipe.


**Resultado**

    User Aor: sip:katarina@contoso.com
    Display Name: Katarina Larsson
    UM Enabled: True
    Team ringing enabled. Team: sip:anders@contoso.com

## Remover um Membro do Grupo de Chamadas de Equipe

Este exemplo remove um membro de equipe do grupo de chamada de equipe de um usuário.

    SEFAUtil.exe /server:lyncserver.contoso.com sip:katarina@contoso.com /removeteammember:anders@contoso.com

> [!NOTE]
> Se o membro a ser removido for o único membro do grupo de chamada de equipe, o toque simultâneo para o grupo de chamada de equipe será automaticamente desabilitado.


**Resultado**

    User Aor: sip:katarina@contoso.com
    Display Name: Katarina Larsson
    UM Enabled: True
    User Ring time: 00:00:30
    Call Forward No Answer to: voicemail

## Definir Toque Atrasado para o Grupo de Chamada de Equipe

Este exemplo altera o toque atrasado para a configuração de hora do grupo de chamada de equipe.

    SEFAUtil.exe /server:lyncserver.contoso.com sip:katarina@contoso.com /delayringteam:5

**Resultado**

    User Aor: sip:katarina@contoso.com
    Display Name: Katarina Larsson
    UM Enabled: True
    Delay Ringing Team (delay:5 seconds). Team: sip:anders@contoso.com

## Habilitar Chamada de Equipe

Isso habilita a chamada de equipe de um determinado usuário.

    SEFAUtil.exe /server:lyncserver.contoso.com sip:katarina@contoso.com /simulringteam

> [!NOTE]
> Se o grupo da chamada de equipe do usuário não tiver membros, a chamada de equipe não será ativada.


**Resultado**

## Desabilitar Chamada de Equipe

Este exemplo desabilita a chamada de equipe de um determinado usuário.

    SEFAUtil.exe /server:lyncserver.contoso.com sip:katarina@contoso.com /disableteamcall

**Resultado**

    User Aor: sip:katarina@contoso.com
    Display Name: Katarina Larsson
    UM Enabled: True
    User Ring time: 00:00:30
    Call Forward No Answer to: voicemail

## Habilitar Recebimento de Chamadas em Grupo e Atribuir um Grupo de Recebimento a um Usuário

Este exemplo atribui um grupo de recebimento a um usuário e habilita o Recebimento de Chamadas em Grupo.

    SEFAUtil.exe /server:lyncserver.contoso.com sip:katarina@contoso.com /enablegrouppickup:199

**Resultado**

    User Aor: sip:katarina@contoso.com
    Display Name: Katarina Larsson
    UM Enabled: True
    Group Pickup Orbit: sip:199;phone-context=user-default@ contoso.com;user=phone

## Desabilitar Recebimento de Chamadas em Grupo

Este exemplo desabilita o Recebimento de Chamadas em Grupo de um determinado usuário.

    SEFAUtil.exe /server:lyncserver.contoso.com sip:katarina@contoso.com /disablegrouppickup

> [!NOTE]
> Ao desabilitar o Recebimento de Chamadas em Grupo de um determinado usuário, o número do grupo que foi designado ao usuário não é retido. Se desejar reabilitar posteriormente o Recebimento de Chamadas em Grupo para esse usuário, será necessário atribuir o numero de grupo novamente com a chave /enablegrouppickup.


    User Aor: sip:katarina@contoso.com
    Display Name: Katarina Larsson
    UM Enabled: True

## SYSPrep.ps1

## Descrição

SYSPrep.ps1 é um script de Windows PowerShell que instalará o seguintes pré-requisitos do Lync Server 2013 em sua máquina do Sistema operacional Windows Server 2008.

  - Microsoft .Net Framework 4.5

  - Microsoft SQL Server Express

  - Windows Powershell versão 3.0

  - Visual C++ 2010 Redistribuível

  - Atualização do Servidor de Informações da Internet

  - Windows Identity Foundation

  - Arquivos principais do Lync Server 2013

Enquanto o nome do script é semelhante à Ferramenta de preparação do sistema para os sistemas operacionais Microsoft Windows, eles são diferentes. Este script só irá instalar os pré-requisitos necessários para Lync Server 2013. Uma vez que os requisitos são instalados, o a ferramenta SYSPREP do Windows pode então ser usadas para criar uma imagem do servidor.

## Requisitos

Antes de executar o script SYSPrep.ps1, você deve copiar os arquivos de pré-requisito em uma pasta local na máquina Sistema operacional Windows Server 2008 (por exemplo **D:\\Setup)**. Essa pasta também deve incluir uma cópia dos arquivos do Lync Server 2013, especificamente o **Setup.exe.** Os arquivos de pré-requisito podem ser baixados dos locais a seguir:


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Pré-requisito</th>
<th>Local</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Microsoft .Net Framework 4.5</p></td>
<td><p>http://go.microsoft.com/?linkid=9816306</p></td>
</tr>
<tr class="even">
<td><p>Microsoft SQL Server Express 2008 R2</p></td>
<td><p>http://www.microsoft.com/en-us/download/details.aspx?id=23650</p></td>
</tr>
<tr class="odd">
<td><p>Windows Powershell versão 3.0</p></td>
<td><p>http://www.microsoft.com/en-us/download/details.aspx?id=34595</p></td>
</tr>
<tr class="even">
<td><p>Visual C++ 2010 Redistribuível</p></td>
<td><p>http://www.microsoft.com/en-us/download/details.aspx?id=5555</p></td>
</tr>
<tr class="odd">
<td><p>Atualizações do Servidor de Informações da Internet</p></td>
<td><p>http://www.microsoft.com/en-us/download/details.aspx?id=34869</p></td>
</tr>
<tr class="even">
<td><p>Windows Identity Foundation</p></td>
<td><p>http://www.microsoft.com/en-us/download/details.aspx?id=17331</p></td>
</tr>
<tr class="odd">
<td><p>Setup.exe do Lync Server 2013</p></td>
<td><p>Cópia de mídia do Lync Server 2013</p></td>
</tr>
</tbody>
</table>


## Parâmetro

O parâmetro **–SetupFolder** toma como um argumento o local do diretório dos arquivos de pré-requisitos

## Exemplos:

Para executar o script SYSPrep.ps1 e instalar os pré-requisitos do Lync Server 2013, execute o seguinte comando em um prompt de comando elevado:

    ./SysPrep.PS1 -SetupFolder D:\Setup

## Migração de Comunicados de Número não Atribuído

A ferramenta de Migração de Comunicados de Número não Atribuído permite que um administrador do Lync mova a configuração de números não atribuídos que é atendida pelo aplicativos de comunicados de um Lync Server de origem a um Lync Server de destino.

## Descrição

A ferramenta de Migração de Comunicados de Número não Atribuído é um script do Windows PowerShell que move a configuração de números não atribuídos atendida pelo aplicativo de comunicados de anúncio de um servidor ou pool de origem a um servidor ou pool de diferente.

Quando executado, o script da Migração de Comunicados de Número não Atribuído realizará as seguintes operações.

1.  Mova todos os arquivos de áudio usados pelos comunicados de número não atribuído do aplicativo de anúncios hospedado no servidor ou pool de origem para o armazenamento de arquivos do servidor ou pool de destino.
    
    > [!NOTE]
    > os arquivos de áudio são removidos do pool de origem após serem copiados para o pool de destino.


2.  Mova todos os comunicados de número não atribuído configurados do aplicativo de comunicados hospedado no servidor ou pool de origem para o servidor ou pool de destino.

3.  Atribua novamente todos os intervalos de números não atribuídos que são atendidos pelo aplicativo de comunicados hospedado no servidor ou pool de origem ao servidor ou pool de destino.

Depois de executar o script com êxito, todos os intervalos de números não atribuídos que eram atendidos pelo aplicativo de comunicados hospedado no servidor ou pool de origem agora serão atendidos com a mesma configuração pelo servidor ou pool de destino.

## Resultado

O script **Move-CsAnnouncementConfiguration** indica onde a operação de migração é bem ou mal sucedida na janela do Shell do gerenciamento do Lync.

Se a execução da operação for interrompida por qualquer erro, os intervalos de números não atribuídos que foram transferidos com êxito para o destino permanecerão no destino de uma forma operacional, e o restante dos intervalos de números não atribuídos a serem migrados permanecerá na origem bem como em uma forma operacional. Para migrar totalmente o restante da configuração, execute novamente o script depois de abordar o erro.

## Objetivo

O script de Migração de Comunicados de Número não Atribuído pode ser usado nos três cenários a seguir:

  - **Configuração das definições de configuração para uma nova versão do Lync Server:** a Contoso está em processo de migração para o Lync Server 2013 e, como parte do processo de migração, o administrador do Lync Server gostaria de transferir a configuração de números não atribuídos atendida pelo aplicativo de comunicados da implementação do Lync Server 2010 para a nova implementação do Lync Server 2013. Para transferir a definições de configuração, o administrador do Lync Server usa a ferramenta de Migração de Comunicados de Número não Atribuído.

  - **Revertendo a implementação do Lync Server 2013 para o Lync Server 2010:** devido fatores inesperados, a Contoso tem que reverter a migração para a nova implementação do Lync Server 2013. Para minimizar as interrupções no serviço, o administrador do Lync Server usa a ferramenta de Migração de Comunicados de Número não Atribuído para reverter a configuração da implementação do Lync Server 2013 para a implementação do Lync Server 2010.

  - **Movendo dados entre implementações do Lync:** a Contoso está em processo de substituição de todos os servidores de um pool por servidores mais recentes. Sua estratégia é implantar um novo pool do Lync Server 2013, mova todos os dados do pool antigo para o novo e, em seguida, descarte o pool antigo. Depois de o pool novo ser implementado, a ferramenta de Migração de Comunicados de Número não Atribuído é usada para mover a configuração do pool antigo para o novo.

## Requisitos

Os principais requisitos necessários para executar a ferramenta com êxito são apresentados a seguir:

1.  O script deve ser executado de um computador que tenha o Shell de Gerenciamento do Lync Server 2013 instalado.

2.  O aplicativo de comunicados precisa ser implementado com êxito nos pools e Lync Servers de origem e destino.

## Script Move-CsAnnouncementConfiguration

O script Move-CsAnnouncementConfiguration exige os dois parâmetros que são descritos na tabela abaixo.

![Parâmetros Move-CsAnnouncementConfiguration.](images/JJ945604.7ab66ad3-d0db-4d77-8b93-ebccf0cb0663(OCS.15).jpg "Parâmetros Move-CsAnnouncementConfiguration.")

## Exemplos

## Transferindo a configuração de comunicados de número não atribuído de um pool do Lync Server 2010 Pool para um pool do Lync Server 2013

Este exemplo transfere os comunicados de número não atribuído do pool de origem (Lync Server 2010) para o pool de destino (Lync Server 2013).

    Move-CsAnnouncementConfiguration.ps1 -Source LS2010Pool.contoso.com -Destination LS2013Pool.contoso.com

## Transferindo a configuração de comunicados de número não atribuído de um pool do Lync Server 2013 Pool para um pool do Lync Server 2010

Este exemplo move os anúncios números não atribuídos a partir da piscina da fonte (Lync Server 2013) para o pool de destino (Lync Server 2010).

    Move-CsAnnouncementConfiguration.ps1 -Source LS2013Pool.contoso.com -Destination LS2010Pool.contoso.com

## Web Conf Data

A ferramenta Web Conf Data permite que um administrador do software de comunicações Lync Server 2013 tenha mais controle sobre os dados associados a conferências Web do organizador. Os cenários incluem a capacidade de excluir dados específicos da reunião de um usuário com base em um critério de carimbo de data/hora.

## Descrição

Esta ferramenta permite ao administrador executar as seguintes operações:

1.  Encontre todos os dados de conferência Web associados a um único usuário.

2.  Exclua todos os dados de conferência Web associados a um único usuário.

3.  Exclua todos os dados de conferência Web associados a um único usuário que seja mais velho que uma determinada data.

4.  Transfira todos os dados de conferência Web associados a um único usuário quando o usuário é movido de um pool para outro.

> [!NOTE]
> O Ferramentas do Resource Kit para Lync Server 2010 oferecia suporte para os dados de conferência Web associados a um único usuário quando esse usuário era transferido de um pool para outro. Essa funcionalidade agora está depreciada nesta ferramenta em favor do parâmetro <strong>MoveConferenceData</strong>. Para obter detalhes sobre este parâmetro, veja o cmdlet <a href="https://technet.microsoft.com/pt-br/library/gg398528(v=ocs.15)">Move-CSUser</a>.


A ferramenta elimina atender apenas os dados para as reuniões que estão inativas. As reuniões ativas (ou reuniões em sessões) não podem ser excluídas.

Essa ferramenta deve ser executada de um computador que esteja no mesmo pool do usuário alvo. O usuário cujos dados de conteúdo de reuniões estão sendo gerenciados por essa ferramenta deve ser hospedado no mesmo pool de usuário.

## Resultado

Esta ferramenta gera os resultados de cada uma das operações:

  - Se uma consulta for executada, a ferramenta gera a lista de todas as pastas de dados reuniões inativos que têm esse usuário como um organizador.

  - Se uma exclusão for realizada, a ferramenta gera a lista de todas as pastas de dados de reuniões cujos dados serão excluídos.

## Requisitos

A ferramenta deve ser executada no mesmo pool onde o organizador está hospedado.

A ferramenta deve ser executada com privilégios de administrador com acesso ao repositório de arquivos de conteúdo.

## Exemplos

A tabela a seguir descreve os parâmetros, alguns dos quais são usados nos exemplos.

![Parâmetros da ferramenta Web Conf Data.](images/JJ945604.a733c1c6-5dfc-4874-a74f-bfdee81c1401(OCS.15).jpg "Parâmetros da ferramenta Web Conf Data.")

    WebConfDataTool.exe /User:user0@contoso.com /Action:query ""/ExpirationDate:08/09/2010 12:00:00""

O exemplo anterior mostra como um comando de consulta funcionaria. O resultado desse comando seria uma lista de todas as pastas de conteúdo de reuniões que seriam afetados por esta ferramenta.

    WebConfDataTool.exe /User:user0@contoso.com /Action:delete

O anterior é um exemplo de um comando de exclusão. O comando delete removerá todas as pastas de reuniões inativas deste usuário.

## Resumo

Esta ferramenta pode ser um recurso valioso para os administradores que precisam de um controle mais preciso sobre os dados da reunião da conferência.

