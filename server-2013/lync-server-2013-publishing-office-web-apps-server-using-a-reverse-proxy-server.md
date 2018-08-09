---
title: "Lync Server 2013: Publ. o serv. do Office Web Apps usando um serv. de proxy reverso"
TOCTitle: Publicando o servidor do Office Web Apps usando um servidor de proxy reverso
ms:assetid: 0babe39f-c4b9-46f0-995a-33dc99c2be03
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204665(v=OCS.15)
ms:contentKeyID: 49305850
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Publicando o servidor do Office Web Apps no Lync Server 2013 usando um servidor de proxy reverso

 

_**Tópico modificado em:** 2013-02-25_

Se você quiser que os usuários externos (ou seja, usuários que estão fazendo logon de fora do firewall de sua organização) tenha acesso às apresentações do Office Web Apps Server PowerPoint, será necessário usar o Office Web Apps Server e um servidor de proxy reverso, como o Microsoft Forefront Threat Management Gateway. Isso também significa que será necessário criar e configurar uma regra de publicação de site; essa regra garantirá que os usuários possam se conectar ao servidor. Se não for necessário fornecer acesso aos usuários externos, não será necessário configurar uma regra de publicação de site.

Para configurar uma regra de publicação de site no Forefront Threat Management Gateway complete o seguinte procedimento:

1.  Clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Forefront TMG** e em **Gerenciamento do Forefront TMG**.

2.  No Forefront TMG, clique com o botão direito do mouse em **Política de Firewall**, aponte para **Novo** e clique em **Regra de Publicação de Site**.

3.  No Assistente de Nova Regra de Publicação na Web, na página **Bem-vindo ao Assistente de Nova Regra de Publicação na Web**, digite um nome para sua nova regra na caixa **Nome da regra de publicação na Web** (por exemplo, **Regra do Office Web Apps Server** ) e clique em **Avançar**.

4.  Na página **Especificar Ação de Regra**, selecione **Permitir** e clique em **Avançar**.

5.  Na página **Tipo de Publicação**, selecione **Publicar um único site ou balanceador de carga** e clique em **Avançar**.

6.  Na página **Segurança da Conexão do Servidor**, selecione **Usar SSL para se conectar ao servidor Web ou farm de servidores publicado** e clique em **Avançar**.

7.  Na página **Detalhes de Publicação Interna**, digite o FQDN de seu servidor Office Web Apps (por exemplo, **officewebapps01.contoso.com** ) na caixa **Nome de site interno** e clique em **Avançar**. O nome digitado na caixa **Nome do site interno** precisa aparecer no campo Assunto ou no campo Nome Alternativo da Entidade do certificado atribuído ao Office Web Apps Server.

8.  Na página **Detalhes de Publicação Interna**, digite **/\*** na caixa **Caminho (opcional)** e clique em **Avançar**. A sintaxe /\* garantirá que todas as pastas e subpastas do site sejam publicadas.

9.  Na página **Detalhes do Nome Público**, selecione **Este nome de domínio (digite abaixo)** na lista suspensa **Aceitar solicitações para** e digite o nome de domínio totalmente qualificado de seu Office Web Apps Server na caixa Nome público. Esse nome deve ser o nome usado para acessar seu site. Por exemplo, se seu site for acessado usando o URL http://officewebapps01.contoso.com, digite **officewebapps01.contoso.com** na caixa **Nome público**.

10. Clique em **Avançar**.

11. Na página **Selecionar Ouvinte da Web**, clique em **Novo**.

12. No Assistente de Definição de Novo Ouvinte da Web, digite um nome para o novo ouvinte da Web (por exemplo, **SSL** ) na caixa **Nome do ouvinte da Web** e clique em **Avançar**.

13. Na página **Segurança de Conexão do Cliente**, selecione **Exigir conexões SSL seguras com clientes** e clique em **Avançar**.

14. Na página **Endereço IP do Ouvinte da Web**, selecione **Externo**, selecione **Interno** e clique em **Avançar**.

15. Na página **Certificados SSL do Ouvinte**, selecione **Usar um único certificado para este Ouvinte da Web** e clique em **Selecionar Certificado**.

16. Na caixa de diálogo **Selecionar Certificado**, selecione o certificado a ser usado para esse Ouvinte da Web e clique em **Selecionar**.

17. Na página **Certificados SSL do Ouvinte**, clique em **Avançar**.

18. Na página **Configurações de Autenticação**, selecione **Sem Autenticação** na lista suspensa **Selecionar como os clientes fornecerão credenciais para o Forefront TMG** e clique em **Avançar**.

19. Na página **Configurações de Logon Único**, clique em **Avançar**.

20. Na página **Concluindo o Assistente de Novo Ouvinte da Web**, revise o resumo das opções de configuração feitas. Quando estiver pronto, clique em **Concluir**.

21. Na página **Selecionar Ouvinte da Web**, clique em **Avançar**.

22. Na página **Delegação de Autenticação**, selecione **Nenhuma delegação, mas o cliente pode autenticar diretamente** na lista suspensa **Selecionar o método usado pelo Forefront TMG para autenticar para o servidor Web publicado** e clique em **Avançar**.

23. Na página **Conjuntos de Usuários**, confirme se os conjuntos de usuário apropriados estão listados. Por padrão, esse é o conjunto de usuários **Todos os Usuários**. Clique em **Adicionar** para adicionar outros conjuntos de usuário que você possa ter definido. Após a conclusão, clique em **Avançar**.

24. Na página **Concluindo o Assistente de Nova Regra de Publicação**, clique em **Concluir**.

Observe que clicar em **Concluir** não significa que você concluiu o processo; ou seja, isso não aplica e habilita automaticamente a nova regra. Em vez disso, será necessário clicar no botão **Aplicar** que aparecerá na interface de usuário do Forefront TMG. Ao clicar em **Aplicar** a caixa de diálogo **Descrição da Alteração de Configuração** aparecerá. Clique em **Aplicar** nessa caixa de diálogo para habilitar a nova regra de publicação.

Após a aplicação da nova regra, será necessário fazer algumas pequenas modificações na regra a fim de assegurar que os usuários possam usar as novas capacidades de apresentação do PowerPoint. Para fazer isso, complete o seguinte procedimento:

1.  No Forefront TMG, clique com o botão direito do mouse no nome da nova regra de publicação e clique em **Propriedades**.

2.  Na caixa de diálogo **Propriedades**, na guia **Para**, selecione a opção **Encaminhar o cabeçalho de host original em vez do presente**.

3.  Na guia **Tráfego**, clique em **Filtragem** e clique em **Configurar HTTP**.

4.  Na caixa de diálogo **Configurando a política HTTP para regra**, desmarque a caixa de seleção **Verificar normalização** e clique em **OK**.

5.  Na caixa de diálogo **Propriedades**, clique em **OK**.

6.  No Forefront TMG, clique em **Aplicar** para habilitar as alterações. quando a caixa de diálogo **Descrição da Alteração de Configuração** aparecer, clique em **Aplicar**.

Após completar a instalação, você pode testar o Servidor Office Web Apps usando os procedimentos no tópico [Validando a Configuração do servidor do Office Web Apps no Lync Server 2013](lync-server-2013-validating-the-configuration-of-office-web-apps-server.md).

