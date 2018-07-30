---
title: 'Lync Server 2013: Configurar regras de publicação na Web para um único pool interno'
TOCTitle: Configurar regras de publicação na Web para um único pool interno
ms:assetid: 86ff4b2a-1ba9-46a2-a175-8b19e00a49dd
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg429712(v=OCS.15)
ms:contentKeyID: 49307353
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurar regras de publicação na Web para um único pool interno no Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

O Microsoft Forefront Threat Management Gateway 2010 e o IIS ARR (Roteamento de Solicitações do Aplicativo do Servidor de Informações da Internet) utilizam regras de publicação na Web para publicar recursos internos, como URLs de reuniões, para usuários da Internet.

Além das URLs dos Serviços da Web para diretórios virtuais, você também deve criar regras de publicação para URLs simples, URL do LyncDiscover e do Servidor Office Web Apps. A cada URL simples, você deve criar uma regra individual no proxy reverso que pontue para essa URL simples.

Se você implantar a versão móvel e usar a descoberta automática, é necessário criar uma regra de publicação para a URL do Serviço de Descoberta Automática externo. A Descoberta automática também requer as regras de publicação para a URL de Serviços Web externa do Lync Server para o Pool de diretores e o Pool de Front-Ends. Para obter detalhes sobre como criar as regras de publicação da web para descoberta automática, consulte [Configurando o proxy reverso para mobilidade no Lync Server 2013](lync-server-2013-configuring-the-reverse-proxy-for-mobility.md).

Use os procedimentos a seguir para criar regras de publicação da Web.

> [!NOTE]  
> Estes procedimentos presumem que você tenha instalado a Standard Edition do Forefront Threat Management Gateway (TMG) 2010 ou tenha instalado e configurado o Servidor de Informações da Internet com a extensão Application Request Routing (IIS ARR). Você deve usar ou o TMG ou o IIS ARR.

## Para criar uma regra de publicação de servidor Web no computador que está executando o TMG 2010

1.  Clique em **Iniciar**, selecione **Programas**, selecione **Microsoft Forefront TMG** e clique em **Gerenciamento de forefront TMG**.

2.  No painel esquerdo, expanda **ServerName**, clique com o botão direito do mouse em **Política de firewall**, selecione **Novo** e clique em **Regra de publicação de site**.

3.  Na página **Bem-vindo à Nova Regra de Publicação da Web**, digite um nome de exibição para a regra de publicação (por exemplo, LyncServerWebDownloadsRule).

4.  Na página **Selecionar Ação da Regra**, selecione **Permitir**.

5.  Na página **Tipo de Publicação**, selecione **Publicar um único site da Web ou balanceador de carga**.

6.  Na página **Segurança da Conexão do Servidor**, selecione **Usar SSL para conectar ao servidor da Web publicado ou ao farm de servidores**.

7.  Na página **Detalhes de Publicação Interna**, digite o FQDN (nome de domínio totalmente qualificado) da Web farm interna que hospeda o conteúdo das reuniões e o conteúdo do Catálogo de Endereços na caixa **Nome do site interno**.
    
    > [!NOTE]  
    > Se o seu servidor interno é um servidor Standard Edition, este FQDN é o FQDN do servidor Standard Edition. Se seu servidor interno é um pool de Front-Ends, este FQDN é um IP virtual (VIP) de balanceador de carga de hardware que equilibra a carga dos servidores de farm da web internos. O servidor TMG deve ser capaz de resolver o FQDN ao endereço IP do servidor web interno. Se o servidor TMG não é capaz de resolver o FQDN ao endereço IP correto, você pode selecionar <strong>Usar um nome de computador ou endereço IP para a conexão com o servidor publicado</strong> e, na caixa <strong>Nome do computador ou</strong> <strong>endereço IP</strong>, digite o endereço IP do servidor web interno. Se você fizer isso, você deve verificar se a porta 53 é aberta no servidor TMG e se ela pode acessar um servidor DNS que reside na rede de perímetro. Também pode usar as entradas no arquivo de hosts local para fornecer uma resolução de nome.

8.  Na página **Detalhes de Publicação Interna**, na caixa **Caminho (opcional)**, digite **/\*** como caminho da pasta a ser publicada.
    
    > [!NOTE]  
    > No assistente de publicação de site, só é possível especificar um caminho. Caminhos adicionais podem ser adicionados modificando as propriedades da regra.

9.  Na página **Detalhes do Nome Público**, confirme se **Este nome de domínio** está selecionado para **Aceitar Solicitações de**, digite o FQDN dos serviços Web externos na caixa **Nome Público**.

10. Na página **Selecionar Ouvinte da Web**, clique em **Novo** para abrir o Assistente para Definição de Novo Ouvinte da Web.

11. Na página **Bem-vindo ao Assistente de Novo Ouvinte da Web**, digite um nome para o ouvinte da Web na caixa **Nome do ouvinte da Web** (por exemplo, LyncServerWebServers) e clique em Avançar.

12. Na página **Segurança da Conexão do Cliente**, selecione **Exigir conexões SSL seguras com clientes**.

13. Na página **Endereços IP do Ouvinte da Web**, selecione **Externo** e clique em **Selecionar Endereços IP**.

14. Na página **Seleção do IP do Ouvinte Externo**, selecione **Endereços IP especificados no computador do Forefront TMG da rede selecionada**, selecione o endereço IP apropriado e clique em **Adicionar**.

15. Na página **Certificados SSL de Ouvinte**, selecione **Atribuir um certificado para cada endereço IP**, selecione o endereço IP que está associado ao FQDN da Web externo e clique em **Selecionar Certificado**.

16. Na página **Selecionar Certificado**, selecione o certificado que corresponde ao nome público especificado na etapa 9 e clique em **Selecionar**.

17. Na página **Configuração da Autenticação**, selecione **Sem Autenticação**.

18. Na página **Configurações de Logon Único**, clique em **Avançar**.

19. Na página **Concluindo o Assistente de Novo Ouvinte da Web**, verifique se as configurações de **Ouvinte da Web** estão corretas e clique em **Concluir**.

20. Na página **Delegação de autenticação**, selecione **Nenhuma delegação, mas o cliente pode autenticar diretamente**.

21. Na página **Conjunto de Usuários**, clique em **Avançar**.

22. Na página **Concluir o novo assistente da regra de publicação da Web**, verifique se as configurações da regra de publicação da Web estão corretas e clique em **Finalizar**.

23. Clique em **Aplicar** no painel de detalhes para salvar as alterações e atualizar a configuração.

## Para criar uma regra de publicação do servidor da Web no computador que executa o IIS ARR

1.  Vincule o certificado que usará para o proxy reverso reverso no protocolo HTTPS. Clique em **Iniciar**, selecione **Programas**, selecione **Ferramentas administrativas** e clique em **Gerenciador de Serviços de Informações da Internet (IIS)**.
    
    > [!NOTE]  
    > Ajuda adicional, capturas de tela e orientação para a implementação e configuração de IIS ARR podem ser encontradas no artigo do NextHop <a href="http://go.microsoft.com/fwlink/?linkid=293391">Usando IIS ARR como um proxy reverso para Lync Server 2013</a>.

2.  Se você ainda não tiver feito isso, importe o certificado que usará no proxy reverso. No **Gerenciador do Serviços de Informações da Internet (IIS)**, clique no nome do servidor do proxy reverso no lado esquerdo do console. No meio do console, em **IIS** localizar **Certificados do servidor**. Clique com o botão direito do mouse em **Certificados do servidor** e selecione **Abrir recurso**.

3.  No lado direito do console, clique em **Importar…**. Digite o nome do arquivo e o caminho do certificado com a extensão ou clique em **…** para navegar pelo certificado. Selecione o certificado e clique em **Abrir**. Forneça a senha usada para proteger a chave privada (se você tiver atribuído uma senha ao exportar o certificado e a chave privada). Clique em **OK**. Se a importação do certificado for bem-sucedida, ele aparecerá como uma entrada no meio do console e como uma entrada nos **Certificados do servidor**.

4.  Atribua o certificado para uso por HTTPS. No lado esquerdo do console, selecione **Site padrão** do servidor IIS. No lado direito, clique em **Ligações…**. Na caixa de diálogo **Ligações do site** , clique em **Adicionar…**. Na caixa de dialogo **Adicionar ligação de site** em **Tipo:**, selecione **https**. Ao selecionar https, será permitido selecionar o certificado para uso para https. Em **Certificado SSL:**, selecione o certificado importado para o proxy reverso. Clique em **OK**. Em seguida, clique em **Fechar**. Agora, o certificado ficará vinculado ao proxy reverso para SSL (camada de soquete seguro) e TLS (segurança da camada de transporte).
    
    > [!IMPORTANT]  
    > Se receber uma notificação ao fechar as caixas de diálogo Ligações dos certificados intermediários que estão faltando, você precisará localizar e importar o certificado de autoridade raiz de uma autoridade de certificação pública ou qualquer certificado intermediário de uma autoridade de certificação. Consulte as instruções na autoridade de certificação pública na qual você tenha solicitado os certificados e sigas as instruções para solicitar e importar uma cadeia de certificados. Se você tiver exportado o certificado do Servidor de Borda, você poderá exportar o certificado de autoridade de certificação raiz e todos os certificados de autoridade de certificação intermediária associados ao Servidor de Borda. Importe o certificado de autoridade de certificação raiz para o armazenamento do computador das Autoridades de certificação confiáveis (não confundir com o armazenamento do Usuário) e os certificados intermediários para o armazenamento das Autoridades de certificação intermediária.

5.  No lado esquerdo do console, abaixo do nome do servidor IIS, clique com o botão direito do mouse em **Farms de servidores** e clique em **Criar Farm de Servidores...**.
    
    > [!NOTE]  
    > Se você não visualizar o nó <strong>Farms de servidores</strong>, terá que instalar o Application Request Routing. Para mais detalhes, consulte <a href="lync-server-2013-setting-up-reverse-proxy-servers.md">Configurando servidores de proxy reverso para o Lync Server 2013</a>.    
    Na caixa de diálogo **Criar farm de servidores** em **Nome do farm de servidores**, digite um nome (pode ser um nome amigável para propósitos de identificação) na primeira URL. Clique em **Próximo**.

6.  Na caixa de diálogo **Adicionar servidor** em **Endereço do servidor**, digite nome de domínio totalmente qualificado (FQDN) dos serviços da Web externos no Servidor Front-End. Os nomes que serão usados aqui para fim de exemplo são os mesmos usados na seção Planejamento do proxy reverso, [Resumo de certificado - Proxy reverso no Lync Server 2013](lync-server-2013-certificate-summary-reverse-proxy.md). Em relação ao planejamento de proxy reverso, deve-se digitar o FQDN `webext.contoso.com`. Confirme se a caixa de seleção próxima a **Online** está selecionada. Clique em **Adicionar** para adicionar o servidor ao pool de servidores da web desta configuração.
    

    > [!WARNING]
    > Lync Server usa balanceadores de carga de hardware para pool do Diretor e o Servidores Front-End para tráfego HTTP e HTTPS. Você deverá fornecer apenas um FQDN ao adicionar um servidor para o Farm de servidores ARR. O FQDN será o Servidor Front-End ou Diretor nas configurações do servidor sem pool ou o FQDN do balanceador de carga de hardware configurado para os pools do servidor. O único método suportado para balancear a carga do tráfego HTTP e HTTPS é o uso dos balanceadores de carga de hardware.



7.  Na caixa de diálogo **Adicionar servidor**, clique em **Configurações avançadas…**. Esta opção abrirá uma caixa de diálogo para definir o roteamento de solicitações de aplicativo do FQDN configurado. Isso serve para redefinir qual porta será usada quando a solicitações forem processadas pelo IIS ARR.
    
    Por padrão, a porta HTTP de destino deve ser definida como 8080. Clique próximo a **httpPort 80** atual e defina o valor para **8080**. Clique próximo a **httpsPort 443** atual e defina o valor para **4443**. Deixe o parâmetro **peso** como 100. Se necessário, você poderá redefinir os pesos de uma regra fornecida, uma vez que você tem as estatísticas da linha de base. Clique em **Concluir** para concluir esta parte da configuração da regra.

8.  Você poderá ver a caixa de diálogo Regras de regravação que informa que o Gerenciador de IIS pode criar uma regra de regravação de URL para encaminhar automaticamente todas as solicitações de entrada para o farm de servidores. Clique em **Sim**. Você ajustará as regras manualmente, no entanto, selecionar Yes definirá a configuração inicial.

9.  Clique no nome do farm de servidores que você acabou de criar. No **Farm de servidores**, em Exibição de recursos do gerenciador do IIS, clique duas vezes em **Cache**. Desmarque **Habilitar cache de disco**. Clique em **Aplicar** no lado direito.

10. Clique no nome do farm de servidores. Em **Farm de servidores**, em Exibição de recursos do gerenciador do IIS, clique duas vezes em **Proxy**. Na página de configurações do Proxy, altere o valor de **Tempo limite (segundos)** para um valor adequado para sua implantação. Clique em **Aplicar** para salvar a alteração.
    
    > [!IMPORTANT]  
    > O valor de Tempo limite de proxy é um número que pode variar de implantação para implantação. Você deve monitorar sua implantação e modificar o valor para a melhor experiência dos clientes. É possível definir um valor tão baixo quanto 200. Se você está oferecendo suporte a clientes móveis do Lync em seu ambiente, defina o valor como 960 para permitir tempo limite de notificações por push do Office 365, que tem um valor de tempo limite de 900. É muito provável que você precise aumentar o valor de tempo limite para evitar que o cliente se desconecte quando o valor for muito baixo ou diminuir o número se as conexões por meio de proxy não se desconectarem e apagarem após o cliente ter se desconectado. O monitoramento e a criação de linha de base para o que é normal para seu ambiente são o único meio preciso de determinar onde está a definição certa para este valor..

11. Clique no nome do farm de servidores. Em **Farm de servidores** na Visualização de Recursos do Gerenciador de IIS, clique duas vezes em **Regras de roteamento**. Na caixa de diálogo Regras de roteamento abaixo de Roteamento, desmarque a caixa de seleção próxima a Habilitar descarregamento de SSL. Se o recurso para desmarcar a caixa de seleção não estiver disponível, selecione a caixa de seleção para **Use Reescrita de URL para inspecionar as solicitações de entrada**. Clique em **Aplicar** para salvar suas alterações.
    

    > [!WARNING]
    > Descarregamento de SSL por proxy reverso não tem suporte.



12. Repita os passos de 5 a 11 de cada URL que deverá passar pelo proxy reverso, uma lista comum seria:
    
      - Serviços da Web de Servidor Front-End externos: webext.contoso.com (já configurado na etapa inicial)
    
      - Serviços da Web de Diretor externos para Diretor: webdirext.contoso.com (Opcional se implementado um Diretor)
    
      - Reunião de URL simples: meet.contoso.com
    
      - Discagem de URL simples: dialin.contoso.com
    
      - URL da Descoberta Automática do Lync: lyncdiscover.contoso.com
    
      - URL do servidor do Office Web Apps: officewebapps01.contoso.com
        
        > [!IMPORTANT]  
        > A URL de Servidor Office Web Apps usará um endereço httpsPort diferente. No passo 7, você define a <strong>httpsPort</strong> como <strong>443</strong> e a <strong>httpPort</strong> como porta <strong>80</strong>. Todas as outras definições de configuração são as mesmas.

13. No lado esquerdo do console, clique no nome do servidor IIS. No meio do console, localize **Reescrita de URL** abaixo de **IIS**. Clique duas vezes em Reescrita de URL para abrir a configuração de regras de Reescrita de URL. Você deve ver as regras de cada Farm de servidores que criou nos passos anteriores. Caso isso não ocorra, confirme que você clicou no nome do **Servidor IIS** logo abaixo do nó **Página inicial** no console do Gerenciador do Servidor de Informações da Internet.

14. Na caixa de diálogo **Reescrita de URL**, usando webext.contoso.com como um exemplo, o nome completo da regra como exibido é **ARR\_webext.contoso.com\_loadbalance\_SSL**.
    
      - Clique duas vezes para abrir a caixa de diálogo **Editar regra de entrada**.
    
      - Clique em **Adicionar** na caixa de diálogo **Condições**.
    
      - Em **Adicionar condição** na **Entrada de condição:** digite **{HTTP\_HOST}** . (Conforme você digita, é exibida uma caixa de diálogo que permitirá selecionar a condição). Em **Verificar sequência de caracteres:** selecione **Corresponde ao padrão** Na **Entrada de padrão** digite **\*** . Selecione **Ignorar maiúsculas e minúsculas**. Clique em **OK**.
    
      - Role para baixo na caixa de diálogo **Editar regra de entrada** para localizar a caixa de diálogo **Ação**. O **Tipo de ação** deverá estar definido como **Rota para farm de servidores**, **Esquema:** definido como **https://**, **Farm de servidores:** definido para a URL na qual as regras são aplicadas. Neste exemplo, deverá estar definido como **webext.contoso.com**. **Caminho:** definido como **/{R:0}**
    
      - Clique em **Aplicar** para salvar suas alterações. Clique em **Voltar às regras** para retornar às regras de Reescrita de URL.

15. Repita o procedimento definido no Passo 14 para cada uma das regras de de reescrita de SSL que você definiu, uma por URL de farm de servidores.
    

    > [!WARNING]
    > Por padrão, as regras de HTTP também são criadas e são indicadas pela nomenclatura semelhante às regras de SSL. Para nosso exemplo atual, a regra de HTTP seria nomeada como <STRONG>ARR_webext.contoso.com_loadbalance</STRONG>. Não são necessárias modificações para essas regras e elas podem ser facilmente ignoradas.



## Para modificar as propriedades da regra de publicação no TMG 2010

1.  Clique em **Iniciar**, aponte para **Programas**, selecione **Microsoft Forefront TMG** e clique em **Gerenciamento do Forefront TMG**.

2.  No painel esquerdo, expanda **Nome do Servidor** e clique em **Política de Firewall**.

3.  No painel de detalhes, clique com o botão direito do mouse na regra de publicação de servidor Web que você criou no procedimento anterior (por exemplo, LyncServerExternalRule) e clique em **Propriedades**.

4.  Na página **Propriedades**, clique na guia **De** e faça o seguinte:
    
      - Na lista **Esta regra aplica-se ao tráfego destas origens**, clique em **Qualquer Lugar** e clique em **Remover**.
    
      - Clique em **Adicionar**.
    
      - Em **Adicionar Entidades de Rede**, expanda **Redes**, clique em **Externa**, clique em **Adicionar** e, em seguida, clique em **Fechar**.

5.  Na guia **Para**, verifique se a caixa de seleção **Encaminhar o cabeçalho do host original em vez do real** está marcada.

6.  Na guia **Ponte**, marque a caixa de seleção **Redirecionar a solicitação para a porta SSL** e especifique a porta **4443**.

7.  Na guia **Nome Público**, adicione as URLs simples (por exemplo, meet.contoso.com e dialin.contoso.com).

8.  Clique em **Aplicar** para salvar as alterações e clique em **OK**.

9.  Clique em **Aplicar** no painel de detalhes para salvar as alterações e atualizar a configuração.

## Para modificar as propriedades da regra de publicação na Web no IIS ARR

1.  Clique em **Iniciar**, selecione **Programas**, **Ferramentas administrativas** e depois clique em **Gerenciador de Serviços de Informações da Internet (IIS)**.

2.  No lado esquerdo do console, clique no nome do servidor IIS.

3.  No meio do console, localize **Reescrita de URL** abaixo de **IIS**. Clique duas vezes em Reescrita de URL para abrir a configuração das regras de Reescrita de URL.

4.  Clique duas vezes na regra que precisa modificar. Faça suas modificações, conforme necessário, em **URL correspondente**, **Condições**, **Variáveis do servidor** ou **Ação**.

5.  Clique em **Aplicar** para confirmar suas alterações. Clique em **Voltar às Regras** para modificar outras regras, ou feche o console do **Gerenciado do IIS** se tiver concluído suas alterações.

