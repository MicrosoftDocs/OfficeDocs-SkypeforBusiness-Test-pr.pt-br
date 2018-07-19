---
title: Usando o Painel de Monitoramento no Lync Server 2013
TOCTitle: Usando o Painel de Monitoramento no Lync Server 2013
ms:assetid: e00e5783-116f-481f-ad17-3af847d6769a
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ721905(v=OCS.15)
ms:contentKeyID: 49886438
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Usando o Painel de Monitoramento no Lync Server 2013

 

_**Tópico modificado em:** 2014-02-05_

O Painel de Monitoramento oferece aos administradores uma visão geral rápida da integridade do sistema e uso do sistema do Microsoft Lync Server 2013. O Painel é projetado para exibir uma visualização conjunta das principais métricas do sistema e para fazer isso exibindo também:

  - Os totais para o dia atual. Observe que os valores mostrados para o dia atual representa dados que foram gravados da meia noite até a hora atual (com base no tempo local do servidor de relatório). Isto significa que você geralmente estará exibindo dados para um dia parcial, não para um período de 24 horas. Por exemplo, se a hora local do servidor é 8:00 horas, você verá oito horas de dados porque há oito horas entre meia noite e o horário atual de 8:00 horas.

  - Totais para a semana e totais de tendência das últimas seis semanas.

  - Totais para o mês e os totais de tendência pelos últimos seis meses (apenas para uso do sistema).

Observe que você pode usar o cmdlet [Get-CsReportingConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsReportingConfiguration) para retornar a URL usada para acessar Relatórios de Monitoramento do Lync Server 2013:

    Get-CsReportingConfiguration

Por padrão, o Painel de Monitoramento mostra dados para as seguintes métricas da semana atual (e os totais de tendência para as seis semanas anteriores):

## Métricas de uso do sistema

**Registro**

  - Usuário de logon exclusivo

**Ponto a ponto**

  - Total de sessões

  - Sessões de IM

  - Sessões de áudio

  - Sessões de vídeo

  - Compartilhamento de aplicativos

  - Total de minutos da sessão de áudio

  - Média de minutos da sessão de áudio

**Conferência**

  - Conferências totais

  - Conferência de IM

  - Conferências A/V

  - Conferências de compartilhamento de aplicativo

  - Conferências da Web

  - Total de organizadores

  - Total de minutos de conferências de A/V

  - Média de minutos da conferência A/V

  - Total de Conferências PSTN

  - Total de participantes PSTN

  - Total de minutos de participantes PSTN

Além das métricas de Uso do Sistema, as seguintes métricas exibem o total para o dia atual e os seis dias anteriores (se você selecionar **Exibição semanal**) ou para a semana atual e as últimas seis semanas se você selecionar **Exibição mensal**.

## Diagnósticos de chamada por usuário

**Usuários com falhas de chamada**

  - Total de usuários com falhas de chamada

  - Organizadores de conferência com falhas de chamada

**Usuários com chamadas de baixa qualidade**

  - Total de usuários com chamadas de baixa qualidade

## Diagnósticos de chamada

Ponto a ponto

  - Total de falhas

  - Taxa geral de falha

  - Taxa de falha de IM

  - Taxa de falha de áudio

  - Taxa de falha de compartilhamento de aplicativos

Conferência

  - Total de falhas

  - Taxa de falha geral

  - Taxa de falha de IM

  - Taxa de falha de A/V

  - Taxa de falha de compartilhamento de aplicativos

Principais cinco servidores por sessões de falha

## Diagnósticos de Qualidade de Mídia

Ponto a ponto

  - Total de chamadas de baixa qualidade

  - Porcentagem de chamadas de baixa qualidade

  - Chamadas PSTN com baixa qualidade

Conferência

  - Total de chamadas de baixa qualidade

  - Porcentagem de chamada de baixa qualidade

  - Chamadas PSTN com baixa qualidade

Principais servidores ruins com porcentagem de chamada de baixa qualidade

## Trabalhando com o Painel de Monitoramento

Conforme observado, os totais padrões são mostrados para a semana atual e os valores de tendência são mostrados para as últimas seis semanas. Se você prefere ver os totais para o mês atual (assim como os valores de tendência para os últimos seis meses), clique no link **Exibição mensal** no canto superior direito do painel. Se você decidir exibir os totais mensais, o texto do link irá mudar para **Exibição semanal**. É possível voltar para a exibição semanal clicando neste link.


> [!TIP]
> O Painel de Monitoramento restringe a exibição dos totais para a semana atual (ou mês) e os valores de tendência das últimas seis semanas (ou meses). Não é possível alterar estas datas e horas. Por exemplo, não é possível usar o Painel para exibir os totais do relatório par ao período de tempo começando nove meses atrás.



Os valores mostrados nas colunas **Esta semana**, **Este mês** ou **Hoje** vinculam você à informações mais detalhadas sobre o item. Lembre-se de que o nome da coluna e os valores exibidos nesta coluna frequentemente são diferentes dependendo da métrica escolhida e dependendo se você selecionou exibição semanal ou mensal. Por exemplo, se você clicar nos totais exibidos para a métrica **Logins de usuário exclusivo**, você verá o **Relatório de registro do usuário** para o período de tempo especificado. É possível retornar para o Painel de Monitoramento a qualquer momento clicando em **Painel**.


> [!TIP]
> Também é possível acessar a página inicial dos Relatórios do Servidor de Monitoramento clicando no link <STRONG>Relatórios</STRONG> no canto superior da página do Painel.



A coluna **Tendência** exibe um gráfico de linha simples que mostram os totais das últimas seis semanas (ou, dependendo da métrica e do intervalo de tempo, os últimos seis dias ou últimos seis meses). Estes gráficos de linha simples mostram um ponto de dados não rotulado para cada período de tempo (por exemplo, um ponto de dados não marcado para cada uma das seis semanas anteriores). No entanto, é possível recuperar os valores reais destes gráficos segurando o ponteiro do mouse sobre o gráfico. Neste caso, um ponteiro mostra os valores máximos e mínimo no gráfico.

## Exportando dados do Painel de Monitoramento

O Painel de Monitoramento oferece várias formas de exportar a exibição do painel atual. Na barra de ferramentas do Painel, você verá um ícone semelhante a um disco floppy com uma seta verde anexada. Se você clicar neste ícone, uma lista suspensa aparecerá oferecendo os seguintes formatos de exportação de dados:

  - Arquivo XML com dados de relatório

  - CSV (delimitado por vírgula)

  - PDF

  - MHTML (arquivo da web)

  - Excel

  - Arquivo TIFF

  - Word

Para exportar a exibição de painel atual (e seus valores), clique na opção de exportação desejada. O Lync Server 2013 gera um relatório no formato especificado e oferece a opção de abrir este relatório ou salvá-lo. Observe que, por padrão, o Lync Server intitula o relatório de **Painel de Monitoramento** e salva-o em sua pasta de Downloads. Para dar um nome diferente ou armazená-lo em uma pasta diferente, clique na seta próxima ao botão **Salvar** e clique em **Salvar como**. Se você concorda com o nome **Painel de Monitoramento** e em salvar na pasta Downloads, basta clicar no botão **Salvar**.

É possível que, ao tentar exportar os dados do painel, uma caixa de diálogo **Alerta de segurança** seja exibida junto com a mensagem "Suas configurações atuais não permitem que este arquivo seja baixado". Se isso ocorrer, faça o seguinte:

  - No Internet Explorer, selecione **Opções de Internet**.

  - Na caixa de diálogo **Opções de Internet**, na guia **Segurança**, clique em **Sites confiáveis** e em **Sites**.

  - Na caixa de diálogo **Sites confiáveis**, clique em **Adicionar** para adicionar o Lync Server 2013 executando os Relatórios do Lync Server 2013 para o conjunto de sites confiáveis.

  - Clique em **Fechar** e em **OK**.

Você precisará atualizar o painel de Monitoramento antes das alterações terem efeito. Para fazer isso, pressione F5 ou clique no ícone **Atualizar** na barra de ferramentas do Painel. (O ícone **Atualizar** é um círculo com um par de setas verdes.)

Também é possível criar uma planilha do Excel que inclui feeds de dados ao vivo, incluindo links para os dados do Painel de Monitoramento. Para criar um arquivo de feed de dados ao vivo, clique no ícone laranja **Exportar para feed de dados** na barra de ferramentas.

Se você prefere imprimir o Painel atual, clique no ícone impressora na barra de ferramentas.

