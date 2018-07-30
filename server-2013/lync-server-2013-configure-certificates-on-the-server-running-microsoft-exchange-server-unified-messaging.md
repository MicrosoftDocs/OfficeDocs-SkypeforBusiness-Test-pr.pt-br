---
title: Configurar certificados no servidor executando o Unified Messaging do Microsoft Exchange Server
TOCTitle: Configurar certificados no servidor executando o Unified Messaging do Microsoft Exchange Server
ms:assetid: 74c883b4-cef6-41a9-b2eb-7212be32fea4
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398564(v=OCS.15)
ms:contentKeyID: 49307126
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurar certificados no servidor executando o Unified Messaging do Microsoft Exchange Server

 

_**Tópico modificado em:** 2016-12-08_

Se você implantou o Unificação de Mensagens (UM) do Exchange, conforme descrito em [Planejamento para integração de Unificação de Mensagens do Exchange no Lync Server 2013](lync-server-2013-planning-for-exchange-unified-messaging-integration.md) na documentação de Planejamento e deseja fornecer recursos do UM do Exchange aos usuários do Enterprise Voice na sua organização, você pode executar os procedimentos abaixo para configurar o certificado no servidor que executa o UM do Exchange.

> [!IMPORTANT]  
> Para os certificados internos, os servidores que executam o Lync Server 2013 e os servidores que executam o Microsoft Exchange devem ter certificados de autoridade raiz que sejam mutuamente confiáveis. A CA (autoridade de certificação) pode ser a mesma ou diferente, desde que os servidores tenham o certificado raiz da autoridade de certificação registrado em seu repositório de certificado de autoridade raiz confiável.

O Exchange Server deve ser configurado com um certificado de servidor para se conectar a Lync Server 2013:

1.  Baixe o certificado da autoridade de certificação do Exchange Server.

2.  Instale o certificado da autoridade de certificação do Exchange Server.

3.  Verifique se a autoridade de certificação está na lista de autoridades de certificação raiz confiáveis do Exchange Server.

4.  Crie uma solicitação de certificado do Exchange Server e instale o certificado.

5.  Atribua o certificado do Exchange Server.

## Para baixar o certificação da autoridade de certificação

1.  No servidor que executa o UM do Exchange, clique em **Iniciar**, em **Executar**, digite **http://\<name of your Issuing CA Server\>/certsrv** e clique em **OK**.

2.  Em **Selecionar uma tarefa**, clique em **Download de um certificado de autoridade de certificação, cadeia de certificados ou lista de certificados revogados**.

3.  Em **Download de um Certificado de Autoridade de Certificação, Cadeia de Certificados ou Lista de Certificados Revogados**, selecione **Método de Codificação em Base 64** e clique em **Fazer download de certificado de autoridade de certificação**.
    
    > [!NOTE]  
    > Você também pode especificar a codificação DER (regras de codificação distintas) nesta etapa. Se você selecionar a codificação DER, o tipo de arquivo na próxima etapa deste procedimento e na etapa 10 de <strong>Para instalar o Certificado de autoridade de certificação</strong> é. p7b, em vez de .cer.

4.  Na caixa de diálogo **Download de Arquivo**, clique em **Salvar** e salve o arquivo no disco rígido no servidor. (O arquivo terá um .cer ou uma extensão de arquivo .p7b, dependendo da codificação que você selecionou na etapa anterior).

## Para instalar o certificado da autoridade de certificação

1.  No servidor que executa o UM do Exchange, abra o MMC (Console de Gerenciamento Microsoft) clicando em **Iniciar**, clique em **Executar**, digite **mmc** na caixa **Abrir** e clique em **OK**.

2.  No menu **Arquivo**, clique em **Adicionar/Remover Snap-in** e em **Adicionar**.

3.  Na caixa **Adicionar Snap-in Autônomo**, clique em **Certificados** e em **Adicionar**.

4.  Na caixa de diálogo **Snap-in de certificados**, clique em **Conta de computador** e em **Avançar**.

5.  Na caixa de diálogo **Selecionar computador**, verifique se a caixa de seleção **Computador local: (o computador que este console está executando)** está marcada e clique em **Concluir**.

6.  Clique em **Fechar** e em **OK**.

7.  Na árvore de console, expanda **Certificados (Computador Local)**, expanda **Autoridades de Certificação Raiz Confiáveis** e clique em **Certificados**.

8.  Clique com o botão direito do mouse em **Certificados**, clique em **Todas as Tarefas** e em **Importar**.

9.  Clique em **Avançar**.

10. Clique em **Procurar** para localizar o arquivo e clique em **Avançar**. (O arquivo terá uma extensão de arquivo .cer ou .p7b, dependendo da codificação que você selecionou na etapa 3 de **Para baixar o certificado de autoridade de certificação**.

11. Clique em **Colocar todos os certificados no repositório a seguir**.

12. Clique em **Procurar** e selecione **Autoridades de Certificação Raiz Confiáveis**.

13. Clique em **Avançar** para verificar as configurações e, em seguida, clique em **Concluir**.

## Para verificar se a autoridade de certificação está na lista de autoridades de certificação raiz confiáveis

1.  No servidor que executa o UM do Exchange, no MMC, expanda **Certificados (Computador Local)**, expanda **Autoridades de Certificação Raiz Confiáveis** e clique em **Certificados**.

2.  No painel de detalhes, verifique se a autoridade de certificação está na lista de autoridades de certificação confiáveis.

## Para configurar o Exchange Server 2013 UM com Lync Server

1.  Para obter detalhes, consulte o tópico sobre integração do Exchange 2013 UM com Lync Server na documentação do Exchange Server, em [http://go.microsoft.com/fwlink/?linkid=265372\&clcid=0x416](http://go.microsoft.com/fwlink/?linkid=265372%26clcid=0x416).

## Para criar uma solicitação de certificado e instalar o certificado no Exchange Server 2007 (SP1)

1.  No servidor que executa o UM do Exchange, clique em **Iniciar**, clique em **Executar**, digite **http://\<***nome do seu servidor de autoridade de certificação emissor***\>/certsrv** e clique em **OK**.

2.  Em **Selecionar uma tarefa**, clique em **Solicitar um Certificado**.

3.  Em **Solicitar um Certificado**, clique em **Solicitação avançada de certificado**.

4.  Em **Solicitação Avançada de Certificado**, clique em **Criar e enviar uma solicitação para a autoridade de certificação**.

5.  Em **Solicitação Avançada de Certificado**, selecione **Servidor Web** ou outro modelo de certificado de servidor configurado para autenticação de servidor.

6.  Em **Informações de identificação para modelo offline**, na caixa **Nome**, digite o FQDN (nome de domínio totalmente qualificado) do Exchange Server.
    
    > [!NOTE]  
    > Você deve inserir o FQDN do Exchange Server para que a comunicação funcione.

7.  Em **Opções de Chave**, clique na caixa de seleção **Armazenar certificado no armazenamento de certificados do computador local**.

8.  Clique no botão **Enviar** na parte inferior da página da Web.

9.  Na caixa de diálogo que solicita a confirmação, clique em **Sim**.

10. Na página Certificado Emitido, em **Certificado Emitido**, clique em **Instalar este certificado**.

11. Na caixa de diálogo que solicita a confirmação, clique em **Sim**.

12. Verifique se a mensagem "O novo certificado foi instalado com êxito" é exibida.

## Para criar um certificado no Exchange Server 2010

1.  Faça logon no servidor que executa o UM do Exchange com os direitos de usuário adequados. Para obter detalhes, consulte "Permissões de acesso do cliente" em [http://go.microsoft.com/fwlink/?linkid=195499\&clcid=0x416](http://go.microsoft.com/fwlink/?linkid=195499%26clcid=0x416).

2.  Consulte os seguintes procedimentos para criar o certificado:
    
    1.  "Criar um novo certificado do Exchange" em [http://go.microsoft.com/fwlink/?linkid=195494\&clcid=0x416](http://go.microsoft.com/fwlink/?linkid=195494%26clcid=0x416)
    
    2.  "Importar um certificado do Exchange" em [http://go.microsoft.com/fwlink/?linkid=195496\&clcid=0x416](http://go.microsoft.com/fwlink/?linkid=195496%26clcid=0x416)
    
    > [!NOTE]  
    > Para o certificado <strong>Nome da Entidade</strong>, digite o FQDN do Exchange Server para que as comunicações funcionem.

## Para atribuir o certificado no Exchange Server 2007 (SP1)

1.  No servidor que executa o UM do Exchange, abra o MMC.

2.  Na árvore de console, expanda **Pessoal** e clique em **Certificados**.

3.  No painel de detalhes, verifique se o certificado pessoal é exibido.

4.  Clique duas vezes no certificado para ler seus detalhes e verificar se ele é válido.
    
    > [!NOTE]  
    > Possivelmente levará alguns minutos para que o certificado apareça como válido.

5.  Reinicie o serviço de Unificação de Mensagens do Microsoft Exchange.
    
    > [!NOTE]  
    > O servidor que está executando a Unificação de Mensagens do Exchange Server 2007 SP1 recupera automaticamente o certificado correto.

6.  Abra o Visualizador de Eventos e procure a ID de Evento 1112, que especifica qual certificado foi recuperado pelo servidor que está executando a Unificação de Mensagens do Exchange Server 2007 SP1.

## Para atribuir o certificado no Exchange Server 2010

1.  Faça logon no servidor que executa o UM do Exchange com os direitos de usuário adequados. Para obter detalhes, consulte "Permissões de acesso do cliente" em [http://go.microsoft.com/fwlink/?linkid=195499\&clcid=0x416](http://go.microsoft.com/fwlink/?linkid=195499%26clcid=0x416).

2.  Para obter o procedimento de atribuição do certificado, consulte "Atribuir serviços a um certificado" em [http://go.microsoft.com/fwlink/?linkid=195497\&clcid=0x416](http://go.microsoft.com/fwlink/?linkid=195497%26clcid=0x416).

