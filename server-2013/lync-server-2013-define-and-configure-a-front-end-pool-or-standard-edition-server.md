---
title: 'Lync Server 2013: Definir e configurar um pool Front-End ou um servidor Standard Edition'
TOCTitle: Definir e configurar um pool Front-End ou um servidor Standard Edition
ms:assetid: 713fc263-23dd-414a-b001-82932e4fe966
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398538(v=OCS.15)
ms:contentKeyID: 49307077
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Definir e configurar um pool Front-End ou um servidor Standard Edition no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

Este procedimento não exige associação a um grupo de administradores locais ou de domínio privilegiado. Você deve fazer logon em um computador como usuário padrão.

Se você estiver implantando um servidor Enterprise, é necessário que haja um número mínimo de Servidores Front-End em execução no pool em todos os momentos. A tabela a seguir resume esses requisitos.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Número total de Servidores de Front End no pool</th>
<th>Número de servidores que devem estar em execução para o pool ser funcional</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>1-2</p></td>
<td><p>1</p></td>
</tr>
<tr class="even">
<td><p>3-4</p></td>
<td><p>2</p></td>
</tr>
<tr class="odd">
<td><p>5-6</p></td>
<td><p>3</p></td>
</tr>
<tr class="even">
<td><p>7-8</p></td>
<td><p>4</p></td>
</tr>
<tr class="odd">
<td><p>9-10</p></td>
<td><p>5</p></td>
</tr>
<tr class="even">
<td><p>11-12</p></td>
<td><p>6</p></td>
</tr>
</tbody>
</table>


> [!NOTE]  
> Para Lync Server 2013, sempre que você adicionar ou remover um Servidor Front-End do pool, é necessário reiniciar os serviços. A remoção e adição de servidores devem ser feitas como operações separadas. Por exemplo, se você adicionar dois Servidores Front-End e remover dois Servidores Front-End, use o seguinte processo:<ol><li><p>Remova os dois servidores front-end.</p></li><li><p>Publique e reative a topologia.</p></li>
> <li><p>Reinicie os serviços</p></li>
> <li><p>Adicione os dois servidores front-end.</p></li>
> <li><p>Publique e reative a topologia.</p></li>
> <li><p>Reinicie os serviços.</p></li></ol>

Após definir a topologia, execute o procedimento a seguir para definir um Pool de Front-Ends para o site. Para obter detalhes sobre a definição da topologia, consulte [Definir e configurar uma topologia no Construtor de Topologia para Lync Server 2013](lync-server-2013-define-and-configure-a-topology-in-topology-builder.md).

## Para definir um Pool de Front-Ends

1.  No Assistente para Definir Novo Pool de Front-Ends, na página **Defina um novo Pool de Front-Ends**, clique em **Avançar**.

2.  Na página **Definir o FQDN doPool de Front-Ends**, insira um FQDN (nome de domínio totalmente qualificado) para o pool sendo criado, clique em **Enterprise Edition Pool de Front-Ends** e depois em **Avançar**.

3.  Na página **Definir os computadores neste pool**, insira um FQDN do computador para o primeiro Servidor Front-End no pool, depois clique em **Adicionar**. Repita esta etapa para qualquer computador adicional (até doze) que você quer adicionar ao pool, depois clique em **Avançar**.

4.  
    Na página **Selecionar recursos**, marque as caixas de seleção para os recursos que você deseja neste pool de front-ends. Por exemplo, se você estiver implantando somente mensagens instantâneas (IM) e recursos de presença, marque a caixa de seleção **Conferência** para permitir IM com várias partes, mas não marque as caixas de seleção **Conferência discada (PSTN)**, **Enterprise Voice** ou **Controle de Admissão de Chamadas**, porque representam recursos de conferência de voz, vídeo e colaboração.
    
    - **Conferência** Esta seleção habilita um rico conjunto de recursos, incluindo:
        
        - IM com mais de duas partes em uma sessão de mensagens instantâneas
        
        - Conferência, que inclui a colaboração de documento, o compartilhamento de aplicativo e o compartilhamento de área de trabalho.
        
        - Conferência A/V, que permite que os usuários realizem conferências de áudio/vídeo (A/V) em tempo real sem a necessidade de serviços externos, como o serviço do Live Meeting ou uma ponte de áudio de terceiros.
    
    - **Conferência (PSTN) discada**    Permite que os usuários participem da parte de áudio de uma conferência do Lync Server 2013 usando um telefone PSTN sem exigir um provedor de conferência de áudio.
    
    - **Enterprise Voice**    Enterprise Voice é a solução VoIP (voz sobre solução IP) no Lync Server 2013 que permite aos usuários fazer e receber chamadas telefônicas. Você implanta esse recurso quando planeja usar o Lync Server 2013 para chamadas de voz, correio de voz e outras funções que usam um dispositivo de hardware ou um cliente de software.
    
    - **Controle de admissão de chamada (CAC)**    O CAC determina, com base na largura de banda de rede disponível, se é permitido que as sessões de comunicações em tempo real (como chamadas de voz ou vídeo) sejam estabelecidas. Se você implantou apenas IM e presença, o CAC não é necessário porque nenhum destes dois recursos usam o CAC.
    
    - **Arquivamento**   O Arquivamento é um meio de arquivar conteúdo de IM, conferências (reuniões) ou ambos enviados pelo Lync Server 2013.
    
    - **Monitoramento**   O servidor de Monitoramento permite coletar dados que descrevem a qualidade da mídia na rede e nos pontos de extremidade, informações de uso relacionadas a chamadas VoIP, mensagens de IM, conversas A/V, compartilhamento de aplicativos e transferências de arquivos, além de informações de erros e solução de problemas de chamadas com falha.
    
    > [!NOTE]  
    > Se você deseja habilitar o CAC na implantação, é necessário habilitar o CAC em exatamente um pool por site central. O CAC é recomendado se você está implantando os recursos de voz ou conferência de A/V.    
    A tabela a seguir mostra os recursos disponíveis (superior) e as funções oferecidas aos usuários (esquerdo). As seleções na tabela são aquelas que você deve selecionar para habilitar estes recursos para sua organização.
    
    
    <table>
    <colgroup>
    <col style="width: 20%" />
    <col style="width: 20%" />
    <col style="width: 20%" />
    <col style="width: 20%" />
    <col style="width: 20%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th></th>
    <th>Conferência</th>
    <th>Conferência discada</th>
    <th>Enterprise Voice</th>
    <th>Serviço de Controle de Admissão de Chamadas</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p>Mensagens instantâneas e presença</p></td>
    <td><p>X</p></td>
    <td><p></p></td>
    <td><p></p></td>
    <td><p></p></td>
    </tr>
    <tr class="even">
    <td><p>Conferência</p></td>
    <td><p>X</p></td>
    <td><p>X</p></td>
    <td><p></p></td>
    <td><p></p></td>
    </tr>
    <tr class="odd">
    <td><p>Conferências A/V</p></td>
    <td><p>X</p></td>
    <td><p>X</p></td>
    <td><p></p></td>
    <td><p>X</p></td>
    </tr>
    <tr class="even">
    <td><p>Enterprise Voice</p></td>
    <td><p></p></td>
    <td><p></p></td>
    <td><p>X</p></td>
    <td><p>X</p></td>
    </tr>
    </tbody>
    </table>


5.  Na página **Selecionar funções de servidor colocadas**, você pode colocar o Servidor de Mediação no Servidor Front-End ou implantá-lo como servidor autônomo.
    
    Você pode colocar o Servidor de Mediação no Pool de Front-Ends.
    
      - Se você pretende colocar o Servidor de Mediação no Pool de Front-Ends do Enterprise Edition, verifique se a caixa de seleção está marcada. As funções de servidor serão implantadas nos servidores do pool.
    
      - Se você pretende implantar o Servidor de Mediação como servidores autônomos, desmarque a caixa de seleção apropriada. Você implantará Servidor de Mediação em uma etapa da implantação separada, depois de implantar completamente o Servidor Front-End.
    
    > [!NOTE]  
    > Recomendamos colocar o servidor de mediação, se possível. Para obter detalhes sobre o suporte a servidores de mediação colocados ou autônomos, consulte <a href="lync-server-2013-components-and-topologies-for-mediation-server.md">Componentes e topologias para o Servidor de Mediação no Lync Server 2013</a> na documentação de Planejamento.

6.  A página **Associar funções de servidor a este pool de Front-Ends** permite definir e associar funções de servidor com o Pool de Front-Ends. A seguinte função está disponível:
    
    **Habilitar um Pool de borda**   define e associa um único Servidor de Borda ou um pool de servidores de borda. Um Servidor de Borda facilita a comunicação e colaboração entre usuários dentro da organização e as pessoas fora da organização, inclusive usuários federados.
    
    Existem dois cenários possíveis que você pode usar para implantar e associar as funções do servidor:
    
    Para o cenário um, você está definindo uma nova topologia para uma nova instalação. É possível abordar a instalação em uma das duas seguintes formas:
    
      - Desmarque a caixa de seleção e prossiga com a definição da topologia. Após publicar, configurar e testar as funções de Servidor de Front-End e Back-End, execute o Construtor de Topologias novamente para adicionar os servidores de função à topologia. Esta estratégia habilitará o teste do Pool de Front-Ends e do servidor executando o SQL Server sem complicações adicionais de funções adicionais. Depois de concluir o teste inicial, execute o Construtor de Topologias novamente para selecionar as funções necessárias para implantação.
    
      - Selecione as funções que você precisa instalar e configure o hardware para acomodar as funções selecionadas.
    
    Para o cenário dois, você possui uma implantação existente e sua infraestrutura está pronta para novas funções ou você precisa associar as funções existentes com uma nova Servidor Front-End:
    
      - Neste caso, você irá selecionar as funções que pretende implantar ou associar com a nova Servidor Front-End. Em qualquer caso, você continuará com a definição das funções, configurar qualquer hardware necessário e continuar com a instalação.

7.  Na página **Definir o repositório SQL**, siga um destes procedimentos:
    
      - Para usar um repositório de SQL Server existente que já foi definido em sua topologia, selecione uma instância do **Repositório SQL**.
    
      - Para definir uma nova instância de SQL Server para armazenar informações de pool, clique em **Novo** e especifique o **FQDN do SQL Server** na caixa de diálogo **Definir Novo Repositório SQL**.
    
      - Para especificar o nome de uma instância de SQL Server, selecione **Instância nomeada** e especifique o nome da instância.
    
      - Para usar a instância padrão, clique em **Instância padrão**.
    
      - Para usar o espelhamento SQL, selecione **Habilitar espelhamento do SQL** e selecione uma instância existente ou crie uma nova instância.

8.  Na página **Definir o compartilhamento de arquivo**, execute um dos seguintes procedimentos:
    
      - Para usar um compartilhamento de arquivo que já foi definido na sua topologia, selecione **Usar um compartilhamento de arquivos definido anteriormente**.
    
      - Para definir um novo compartilhamento de arquivo, selecione **Definir um novo compartilhamento de arquivo** na caixa **FQDN do Servidor de Arquivos**, insira o FQDN do servidor de arquivos existente onde o compartilhamento de arquivo deve residir e insira um nome para o compartilhamento de arquivo na caixa **Compartilhamento de Arquivos**.
    
    > [!IMPORTANT]  
    > O compartilhamento de arquivos do Lync Server 2013 não pode ser localizado na Servidor Front-End. Observe que neste exemplo, o compartilhamento de arquivo foi localizado no servidor Back-End com base no SQL Server. Este pode não ser um local ideal para as necessidades da sua organização, um servidor de arquivos pode ser uma escolha melhor. Você pode definir o compartilhamento de arquivos sem que este tenha sido criado. Será necessário criar o compartilhamento de arquivos no local que você definir antes de publicar a topologia.

9.  Na página **Especificar a URL dos serviços Web**, execute um ou estes dois procedimentos:
    
    > [!IMPORTANT]  
    > A URL base é a identidade do Serviços Web para a URL, sem o https://. Por exemplo, se a URL completa para o Serviços Web do pool é https://pool01.contoso.net, a URL base será pool01.contoso.net.    

    > [!WARNING]
    > Caso tenha mais de um Pool de Front-Ends ou Servidor Front-End, o FQDN de serviços Web externos deverá ser exclusivo. Por exemplo, caso defina o FQDN de serviços Web externos de um Servidor Front-End como <STRONG>pool01.contoso.com</STRONG>, não será possível usar <STRONG>pool01.contoso.com</STRONG> para outro Pool de Front-Ends ou Servidor Front-End.

    
    1.  Se você configurar o balanceamento de carga DNS, marque a caixa de seleção **Substituir o FQDN do pool de serviços internos da Web**, insira a URL base interna (que deve ser diferente do FQDN de pool e poderia ser, por exemplo, interno-\<sua base URL\>) em **URL base interna**.
        

        > [!WARNING]
        > Se você decidir substituir os serviços Web internos por um FQDN autodefinido, cada FQDN deve ser exclusivo de qualquer Pool de Front-Ends, Diretor ou um Pool de diretores. <STRONG>Use apenas caracteres padrão</STRONG> (incluindo A-Z, a-z, 0-9 e hifens) ao definir URLs ou nomes de domínio totalmente qualificados. Não use caracteres Unicode ou sublinhados. Caracteres não padrão em uma URL ou FQDN, em geral, não têm suporte de DNS externos e CAs públicas (ou seja, quando a URL ou FQDN tiverem de ser atribuídos ao nome da entidade ou ao nome de entidade alternativo em um certificado).

    
    2.  Opcionalmente, insira a URL base externa em **URL base externa**. Insira a URL base externa para diferenciá-la da nomeação de domínio interna. Por exemplo, seu domínio interno é contoso.net, mas seu nome de domínio externo é contoso.com. Você deve definir a URL usando o nome do domínio contoso.com. Isso também é importante no caso de um proxy reverso. O nome de domínio da URL base externa seria igual ao nome de domínio do FQDN do proxy inverso. As mensagens instantâneas e presença exigem acesso HTTP para o Pool de Front-Ends.
    
    > [!NOTE]  
    > Para usar o balanceamento de carga DNS, você deve criar os registros DNS apropriados. Para obter detalhes, consulte <a href="lync-server-2013-configure-dns-for-load-balancing.md">Configurar DNS para balanceamento de carga no Lync Server 2013</a>.

10. Caso você selecione **Conferência** na página **Selecionar Recursos**, na página **Selecione um Servidor Office Web Apps**, selecione **Associar pool a um Servidor Office Web Apps** e clique em **Novo** (ou selecione um Servidor Office Web Apps existente na lista suspensa).

11. Na caixa de diálogo **Definir um Novo Servidor Office Web Apps**, digite o FQDN (nome de domínio totalmente qualificado) do computador do Servidor Office Web Apps na caixa **FQDN do Servidor Office Web Apps** ; quando você fizer isso, o URL de descoberta do Servidor Office Web Appsserá inserido automaticamente na caixa **URL de descoberta de Servidor Office Web Apps**.
    
    Se o Servidor Office Web Apps estiver instalado localmente na mesma zona de rede do Lync Server 2013, a opção **O Servidor Office Web Apps é implantado em uma rede externa (ou seja, de perímetro/Internet)** não deverá ser selecionada.
    
    Se o Servidor Office Web Apps for implantado fora do firewall interno, selecione a opção **O Servidor Office Web Apps é implantado em uma rede externa (ou seja, de perímetro/Internet)**.
    
    > [!NOTE]  
    > Para obter detalhes, consulte <a href="lync-server-2013-enabling-office-web-apps-server-and-lync-server-2013.md">Configurando a integração com servidor de Office Web Apps e Lync Server 2013</a>.

12. Na página **Definir o Repositório do SQL de Arquivamento**, selecione uma instância existente do SQL Server ou defina uma nova instância para armazenar os dados associados a arquivamento.

13. Na página **Definir o Repositório do SQL de Monitoramento**, selecione uma instância existente do SQL Server ou defina uma nova instância para armazenar os dados associados a monitoramento.

14. Clique em **Avançar**. Se você definiu outros servidores de função na página **Associar funções de servidor a este pool de Front-Ends**, páginas separadas de assistente de configuração de funções serão abertas para permitir a configuração das funções de servidor. Para obter detalhes, consulte:
    
    [Implantação de acesso do usuário externo no Lync Server 2013](lync-server-2013-deploying-external-user-access.md)

15. Se você não selecionou funções do servidor adicionais para configurar e implantar ou quando você finalizou a configuração dos servidores de função adicionais, clique em **Concluir**.

