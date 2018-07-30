---
title: Configurando a filtragem de transferência de arquivo e URL para mensagens instantâneas (IM) no Lync Server 2013
TOCTitle: Configurando a filtragem de transferência de arquivo e URL para mensagens instantâneas (IM) no Lync Server 2013
ms:assetid: 115a1a2c-599f-474c-a063-52f7144b5246
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg520952(v=OCS.15)
ms:contentKeyID: 49305925
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurando a filtragem de transferência de arquivo e URL para mensagens instantâneas (IM) no Lync Server 2013

 

_**Tópico modificado em:** 2012-11-01_

A ferramenta Filtro de IM Inteligente protege a implantação do Lync Server 2013 contra a difusão das formas mais comuns de vírus com o mínimo de degradação da experiência do usuário. Use o Filtro de IM Inteligente para configurar filtros para bloquear mensagens instantâneas não solicitadas ou potencialmente prejudiciais de pontos de extremidade desconhecidos fora do firewall da empresa. Configure os filtros especificando os critérios que devem ser usados para determinar o que vai ser bloqueado, como mensagens instantâneas que tenham hiperlinks com prefixos específicos e arquivos com determinadas extensões.

O filtro de IM Inteligente fornece o seguinte:

  - Filtro avançado de URL.

  - Filtro avançado de transferência de arquivo.

A configuração do filtro de IM inteligente inclui o seguinte:

  - Configuração do filtro de URL.

  - Configuração do filtro de transferência de arquivo.

## Como as opções de filtro são aplicadas a mensagens instantâneas

Antes de você implantar a ferramenta de filtro de mensagem de IM inteligente, é preciso entender como as opções de filtro são roteadas de um servidor Lync Server 2013 a outro. A forma como essas opções de filtragem são aplicadas é consistente, quer os servidores estejam em uma única organização ou ultrapasse os limites organizacionais. Essa consistência se aplica à forma com que os textos personalizados de observação e aviso são inseridos em mensagens e enviados pelos servidores.

> [!NOTE]  
> O filtro de mensagem instantânea aumenta a quantidade de recursos da CPU necessários para processar URLs em uma mensagem. Esse aumento de demanda da CPU também afeta o desempenho do Lync Server.

Usando a página **Filtro de URL** no grupo **IM e Presença** no Painel de Controle do Lync Server, você pode bloquear alguns ou todos os hiperlinks ou configurar um aviso. Esse aviso é inserido no início de uma mensagem instantânea que contém um hiperlink quando você escolhe a opção **Enviar mensagem de aviso** em **Prefixo de hiperlink**.

Quando uma mensagem instantânea passa de um servidor para outro, as seguintes diretrizes gerais se aplicam:

  - Se um servidor bloqueia uma mensagem instantânea (por você ter marcado a caixa de seleção **Bloquear URLs com extensão de arquivo** na página **Filtro de URL** ou por você ter escolhido a opção **Bloquear hiperlinks** em **Prefixo de hiperlink**), uma mensagem de erro é devolvida ao cliente. Os servidores subsequentes não recebem essa mensagem instantânea.

  - Se um servidor (Servidor1) adiciona um aviso a uma mensagem instantânea que contém um hiperlink ativo, um servidor subsequente (Servidor2) que recebe essa mensagem ainda pode tomar uma ação diferente com base nesse hiperlink ativo, bloqueando a mensagem instantânea ou adicionando um aviso. Se o Servidor2 estiver configurado apenas para adicionar um aviso a esse URL, o aviso anterior adicionado pelo Servidor1 é removido, e o aviso configurado no Servidor2 é adicionado ao início da mensagem instantânea.

> [!NOTE]  
> Se você estiver executando o Lync Server 2013 em um ambiente misto, o Live Communications Server 2005 com SP1 é a versão mínima requerida para uso do aplicativo Filtro de IM Inteligente. O Filtro de IM Inteligente não é suportado no Live Communications Server 2005 sem o SP1.

## Filtro de URL

Os URLs são filtrados de acordo com seu prefixo do hiperlink. Os exemplos a seguir são prefixos válidos:

  - www\*.

  - ftp.

  - http:

Se você não configurar o filtro de mensagem instantânea para realizar o filtro de URL, todos os URLs presentes em mensagens instantâneas passam pelo servidor sem serem modificados. Porém, se você configurá-lo para realizar o filtro de URL, os URLs presentes em mensagens instantâneas são filtrados de acordo com as opções que você selecionou nas caixas de diálogo **Editar Filtro de URL** ou **Novo Filtro de URL**.

  - **Habilitar filtro de URL**   Essa opção habilita o filtro de URL para a implantação global ou para o site que você selecionou.

  - **Bloquear URLs com extensão de arquivo**   O filtro de mensagem instantânea bloqueia qualquer URL ativo da intranet ou da Internet que contenha um arquivo com uma das extensões listadas em **Extensões de tipos de arquivos a serem bloqueadas** na caixa de diálogo **Editar Filtro de Arquivo**. Quando um URL é bloqueado, uma mensagem de erro é exibida para o remetente. Quando selecionada, essa opção busca precedência em todas as outras opções de filtro para quaisquer extensões de arquivos definidas em **Extensões de tipos de arquivos a serem bloqueadas**.
    
    > [!IMPORTANT]  
    > A filtragem de extensões de arquivo está limitada aos nomes padrão. A filtragem pode não funcionar com extensões de arquivo incorporadas em outros nomes.

Para configurar como hiperlinks são manuseados em conversas de mensagem instantânea, selecione uma das opções a seguir em **Prefixo de hiperlink**:

  - **Não filtrar**   Os URLs presentes nas mensagens são enviados através do servidor. Quando você escolhe essa opção, a caixa **Permitir mensagem** aparece. Na caixa **Permitir mensagem**, especifique o aviso que você quer inserir no começo de cada mensagem instantânea que contenha hiperlinks. Esse aviso não pode ter mais que 65535 caracteres.

  - **Bloquear hiperlinks**   A entrega de mensagens instantâneas contendo hiperlinks é bloqueada pelo Lync Server, e uma mensagem de erro é exibida para o remetente.

  - **Enviar mensagem de aviso**   O Lync Server permite hiperlinks ativos em mensagens instantâneas, mas inclui um aviso. Quando você escolhe essa opção, a caixa **Mensagem de aviso** aparece. Na caixa **Mensagem de aviso**, você deve digitar o aviso que você quer incluir nas mensagens instantâneas contendo hiperlinks válidos. Por exemplo, esse aviso pode informar sobre os potenciais perigos de clicar em um link desconhecido ou pode fazer referência às políticas e requisitos relevantes da organização. O aviso não pode ter mais que 65535 caracteres.

Se você selecionar **Bloquear hiperlinks** ou **Enviar mensagem de aviso**, as seguintes opções estarão disponíveis:

  - **Excluir hiperlinks de intranet local**   O filtro de mensagem instantânea bloqueia apenas URLs de Internet. Os URLs para locais dentro da sua intranet passam pelo servidor sem serem modificados. Porém, a passagem de URLs da intranet que servidores individuais executando o Lync Server depende de quais tipos de sites locais são considerados parte da sua zona da intranet. Para verificar as configurações de zona de intranet de um servidor, consulte o procedimento “Para configurar suas definições de intranet no Internet Explorer” em [Modificar o filtro de URL padrão](lync-server-2013-modify-the-default-url-filter.md).

  - **Filtrar estes prefixos de hiperlink**   Para escolher quais prefixos você quer bloquear, clique em **Selecionar**, depois em **Selecionar Prefixo de Hiperlink**, e adicione os prefixos à lista de **Prefixos de hiperlink**.
    
    Todos os prefixos, exceto **href** devem terminar com ponto ou dois pontos, ou com um asterisco seguido por um ponto. Prefixos válidos podem conter quaisquer caracteres no conjunto caracteres de URL válidos, exceto asterisco (\*). O conjunto de caracteres de URL válidos é: \#\*+/0123456789=@ABCDEFGHIJKLMNOPQRSTUVWXYZ^\_\` abcdefghijklmnopqrstuvwxyz|~

## Filtro de Transferência de Arquivo

O filtro de transferência de arquivo afeta as mensagens instantâneas e as conferências. Para as conferências, essas configurações afetam o recurso de folheto no cliente Office Live Meeting 2007 e os recursos de reprodução de multimídia.

> [!NOTE]  
> O Lync Server também oferece opções de configuração de transferência de arquivo. Essa opção do servidor é oferecida em adição aos controles de cliente disponíveis no Lync Server.

Você pode filtrar transferências de arquivos durante as conversas com mensagens instantâneas, quando você estiver usando um recurso de folheto no cliente do Office Live Meeting 2007 e para recursos de reprodução de multimídia para todos os tipos de arquivo. Você pode definir as seguintes opções para controlar arquivos de transferência:

  - **Habilitar o filtro de arquivo**   Essa opção habilita a filtragem de arquivo para a implantação global ou para o site que você selecionou.
    
    Quando você habilita o filtro de arquivo, você pode escolher uma das opções a seguir na **Transferência de arquivo**:
    
      - **Bloquear tipos de arquivos específicos**   Você especifica quais solicitações de transferências de arquivo são filtradas pelo servidor criando uma lista de extensões de arquivos a serem bloqueadas. As entradas da lista podem conter todos os caracteres padrão, com exceção do asterisco (\*). No cliente do Office Live Meeting 2007 o recurso de folheto está habilitado, mas nenhum arquivo com essa extensão pode ser carregado ou baixado. Se você marcar a caixa de seleção **Bloquear URLs com extensão de arquivo** nas configurações listadas na guia **Filtro de URL**, o filtro de URL usa essa mesma lista para bloquear hiperlinks ativos que contenham qualquer uma dessas extensões de arquivos. Para escolher quais tipos de arquivos você quer bloquear, clique em **Selecionar**, depois clique em **Selecionar Tipo de Arquivo**, e adicione as extensões de tipos de arquivos à lista **Extensões de tipos de arquivos selecionadas**.
    
      - **Bloquear tudo**   O servidor remove todas as mensagens instantâneas que contém solicitações de transferência de arquivo e retornar uma mensagem de erro ao remetente da solicitação. O recurso de folheto do cliente do Office Live Meeting 2007 será desabilitado.

> [!IMPORTANT]  
> A filtragem de extensões de arquivo está limitada aos nomes padrão. A filtragem pode não funcionar com extensões de arquivo incorporadas em outros nomes.

## Nesta seção

  - [Modificar o filtro de transferência de arquivo padrão](lync-server-2013-modify-the-default-file-transfer-filter.md)

  - [Criar um novo filtro de transferência de arquivos para um local específico](lync-server-2013-create-a-new-file-transfer-filter-for-a-specific-site.md)

  - [Modificar o filtro de URL padrão](lync-server-2013-modify-the-default-url-filter.md)

  - [Criar um novo filtro de URL para tratar hiperlinks em conversas de IM](lync-server-2013-create-a-new-url-filter-to-handle-hyperlinks-in-im-conversations.md)

## Consulte Também

#### Outros Recursos

[Gerenciando configurações de IM e de presença no Lync Server 2013](lync-server-2013-managing-im-and-presence-settings.md)

