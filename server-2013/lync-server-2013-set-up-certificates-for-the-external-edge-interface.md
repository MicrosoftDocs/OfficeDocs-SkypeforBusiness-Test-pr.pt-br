---
title: 'Lync Server 2013: Configurar certificados para a interface de borda externa'
TOCTitle: Configurar certificados para a interface de borda externa
ms:assetid: 5d78182c-88d8-4483-95ad-74b17f2d5fac
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398409(v=OCS.15)
ms:contentKeyID: 49306848
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurar certificados para a interface de borda externa para Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

> [!IMPORTANT]  
> Ao executar o Assistente de Certificado, certifique-se de que você está conectado usando uma conta que seja membro de um grupo ao qual tenham sido atribuídas as permissões apropriadas para o tipo de modelo de certificado que será utilizado. Por padrão, uma solicitação de certificado do Lync Server utilizará o modelo de certificado do Servidor Web. Se uma conta membro do grupo RTCUniversalServerAdmins for utilizada para solicitar um certificado usando este modelo, verifique se foram atribuídas as permissões Inscrever a este grupo, necessárias para usar o modelo.

Cada Servidor de Borda requer um certificado público na interface entre a rede de perímetro e a Internet, e o nome alternativo da entidade do certificado deve conter nomes externos do serviço de Borda de Acesso e FQDNs (nomes de domínio totalmente qualificado) do serviço de Borda de Webconferência.

Para detalhes sobre este e outros requisitos de certificado, consulte [Requisitos de certificado para acesso do usuário externo no Lync Server 2013](lync-server-2013-certificate-requirements-for-external-user-access.md).

Para uma lista de autoridades de certificação públicas (AAs) que fornecem certificados que atendem aos requisitos específicos para certificados de comunicações unificadas e fizeram uma parceria com a Microsoft para garantir que elas trabalham com o Assistente de Certificados do Lync Server 2013, consulte o artigo 929395 da Base de Dados de Conhecimento Microsoft, "Parceiros de Certificado de Comunicação Unificada para Exchange e Communications Server" em [http://go.microsoft.com/fwlink/p/?linkId=202834](http://go.microsoft.com/fwlink/p/?linkid=202834).

## Configurando certificados nas interfaces externas

Para configurar um certificado na interface de borda externa em um site, use os procedimentos desta seção para fazer o seguinte:

  - Crie a solicitação de certificado para a interface externa do Servidor de Borda.

  - Envie a solicitação à autoridade de certificação pública.

  - Importe o certificado da interface externa de cada Servidor de Borda.

  - Atribua o certificado à interface externa de cada Servidor de Borda.

  - Se sua implantação incluir vários Servidores de Borda, exporte o certificado junto com sua chave privada e o copie para os Servidores de Borda. Em seguida, para cada Servidor de Borda, importe-o e atribua-o conforme descrito anteriormente. Repita este procedimento para cada Servidor de Borda.

Você pode solicitar os certificados públicos diretamente de uma autoridade de certificação pública (como a partir do site de uma autoridade de certificação pública). Os procedimentos nesta seção usam o Assistente de Certificados na maioria das tarefas do certificado. Se você optar por solicitar um certificado diretamente a partir de uma autoridade de certificação pública, precisará modificar cada procedimento conforme apropriado para solicitar, transportar e importar o certificado e também para importar a cadeia de certificados.

Quando você solicita um certificado junto a uma autoridade de certificação externa, as credenciais fornecidas devem ter direitos para solicitar um certificado nessa autoridade de certificação. Cada autoridade de certificação tem uma política de segurança que define quais credenciais (ou seja, nomes de usuário e grupo específicos) têm permissão para solicitar, emitir, gerenciar ou ler certificados.

Se você decidir usar o MMC (Console de Gerenciamento Microsoft) de Certificados para importar a cadeia de certificados e o certificado, deverá importá-los para o repositório de certificados do computador. Se você importá-los para o repositório de certificados do usuário ou serviço, o certificado não estará disponível para atribuição no Assistente de Certificados do Lync Server 2013.

## Para criar a solicitação de certificado para a interface externa do Servidor de Borda

1.  No Servidor de Borda, no Assistente de Implantação, próximo a **Etapa 3: Solicitar, instalar ou atribuir certificados**, clique em **Executar novamente**.
    
    > [!NOTE]  
    > Se sua organização desejar oferecer suporte à conectividade pública de mensagens instantâneas com o AOL, você não pode usar o Assistente de Implantação do Lync Server para solicitar o certificado. Em vez disso, execute as etapas no procedimento &quot;Para criar uma solicitação de certificado para a interface externa do Servidor de Borda para oferecer suporte à conectividade pública de IM com o AOL&quot; posteriormente neste tópico.<br />    Se você tiver vários Servidores de Borda em um único local de um pool, poderá executar o Assistente de Certificados do Lync Server 2013 em qualquer um dos Servidores de Borda.

2.  Na página **Tarefas de Certificado Disponíveis**, clique em **Criar uma nova solicitação de certificado**.

3.  Na página **Solicitação de Certificado**, clique em **Certificado de Borda Externa**.

4.  Na página **Solicitação Atrasada ou Imediata**, marque a caixa de seleção **Preparar a solicitação agora, mas enviá-la depois**.

5.  Na página **Arquivo de Solicitação de Certificado**, digite o nome de arquivo e o caminho completo do arquivo no qual a solicitação será salva (por exemplo, c:\\cert\_exernal\_edge.cer).

6.  Na página **Especificar Modelo de Certificado Alternativo**, para usar um modelo diferente do modelo WebServer padrão, marque a caixa de seleção **Usar o modelo de certificado alternativo para a autoridade de certificação selecionada**.

7.  Na página **Nome e Configurações de Segurança**, siga estes procedimentos:
    
      - Em **Nome amigável**, digite um nome para exibição do certificado.
    
      - Em **Comprimento de bit**, especifique o comprimento de bit (normalmente o padrão de **2048** ).
    
      - Verifique se a caixa de seleção **Marcar chave privada de certificado como exportável** está marcada.

8.  Na página **Informações da Organização**, digite o nome da organização e a unidade organizacional (por exemplo, uma divisão ou departamento).

9.  Na página **Informações Geográficas**, especifique as informações de localização.

10. Na página **Nome da Entidade/Nomes Alternativos da Entidade**, as informações a serem preenchidas automaticamente pelo assistente são exibidas. Se nomes alternativos de entidade adicionais forem necessários, especifique-os nas próximas duas etapas.

11. Na página **Configuração do Domínio SIP em SANs (Nomes Alternativos da Entidade)**, marque a caixa de seleção do domínio para adicionar uma entrada sip. *\<domínio\_sip\>* à lista de nomes alternativos da entidade.

12. Na página **Configurar Nomes Alternativos da Entidade Adicionais**, especifique quaisquer nomes alternativos de entidade adicionais que sejam necessários.

13. Na página **Resumo da Solicitação**, examine as informações do certificado a ser usado para gerar a solicitação.

14. Após o término da execução de comandos, faça o seguinte:
    
      - Para exibir o log da solicitação do certificado, clique em **Exibir Log**.
    
      - Para concluir a solicitação do certificado, clique em **Avançar**.

15. Na página **Arquivo de Solicitação de Certificado**, siga o seguinte procedimento:
    
      - Para exibir o arquivo de solicitação de assinatura de certificado (CSR), clique em **Exibir**.
    
      - Para fechar o assistente, clique em **Concluir**.

16. Copie o arquivo de saída para um local de onde você possa enviá-lo à autoridade de certificação pública.

## Para criar uma solicitação de certificado para a interface externa do Servidor de Borda para oferecer suporte à conectividade pública de IM com o AOL

1.  Quando o modelo necessário estiver disponível para a autoridade de certificação, use o seguinte cmdlet Windows PowerShell no Servidor de Borda para solicitar o certificado:
    
        Request-CsCertificate -New -Type AccessEdgeExternal  -Output C:\ <certfilename.txt or certfilename.csr>  -ClientEku $true -Template <template name>
    
    O nome do certificado padrão do modelo fornecido no Lync Server 2013 é Servidor Web. Somente especifique o *\<nome do modelo\>* quando precisar usar um modelo diferente do padrão.
    
    > [!NOTE]  
    > Se sua organização desejar oferecer suporte à conectividade a redes públicas de IM com o AOL, você deverá usar o Windows PowerShell em vez do Assistente de Certificados para solicitar o certificado a ser atribuído à borda externa do Serviço de Borda de Acesso. Isso ocorre porque o modelo de Servidor Web do Lync Server 2013 usado pelo Assistente de Certificados para solicitar um certificado não oferece suporte à configuração de EKU de cliente. Antes de usar o Windows PowerShell para criar o certificado, o administrador da CA deverá criar e implantar um novo modelo que oferece suporte a EKU de cliente.

## Para enviar uma solicitação a uma autoridade de certificação pública

1.  Abra o arquivo de saída.

2.  Copie e cole o conteúdo da CSR (Solicitação de Assinatura de Certificado).

3.  Se solicitado, especifique o seguinte:
    
      - **Microsoft** como plataforma de servidor.
    
      - **IIS** como versão.
    
      - **Servidor Web** como o tipo de uso.
    
      - **PKCS7** como o formato de resposta.

4.  Quando a autoridade de certificação pública tiver confirmado suas informações, você receberá uma mensagem de email contendo o texto necessário para o seu certificado.

5.  Copie o texto da mensagem de email e salve o conteúdo em um arquivo de texto (.txt) no computador local.

## Para importar o certificado da interface externa do Servidor de Borda

1.  Faça logon como membro do grupo de Administradores no mesmo Servidor de Borda no qual você criou a solicitação de certificado.

2.  No Assistente de Implantação, na página **Implantar Servidor de Borda**, ao lado de **Etapa 3: solicitar, instalar ou atribuir certificados**, clique em **Executar novamente**.

3.  Na página **Tarefas de Certificado Disponíveis**, clique em **Importar um certificado de um arquivo. p7b, .pfx ou .cer**.

4.  Na página **Importar Certificado**, clique em **Procurar** para localizar e selecionar o certificado que você solicitou para a interface externa do Servidor de Borda (ou pode digitar o caminho completo e o nome do arquivo). Se o certificado tiver uma chave privada, selecione **Arquivo de certificado contém a chave privada do certificado** e digite a senha da chave privada. Clique em **Avançar**.

5.  Na página **Importar Resumo de Certificado**, revise o resumo e clique em **Avançar**.

6.  Em **Executando Comandos**, revise os resultados da importação, clique em **Exibir Log** para obter mais informações conforme necessário e clique em **Concluir** para concluir a importação do certificado.

7.  Se você estiver configurando um pool de Servidores de Borda, exporte o certificado com sua chave privada, conforme descrito no procedimento "Para exportar o certificado com a chave particular para Servidores de Borda em um pool" neste tópico. Copie o arquivo de certificado exportado para os outros Servidores de Borda e importe-o para o repositório do computador em cada Servidor de Borda.

## Para exportar o certificado com a chave privada para os Servidores de Borda em um pool

1.  Faça logon como membro do grupo Administradores no mesmo Servidor de Borda em que o certificado foi importado.

2.  Clique em **Iniciar**, **Executar** e digite **MMC** .

3.  No console MMC (Console de Gerenciamento Microsoft), clique em **Arquivo** e em **Adicionar/Remover Snap-in**.

4.  Em **Adicionar ou Remover Snap-ins**, clique em **Certificados** e em **Adicionar**.

5.  Na caixa de diálogo **Certificados**, selecione **Conta do computador**, clique em **Avançar**, selecione **Computador local: (o computador em que este console está sendo executado)** em **Selecionar Computador**, clique em **Concluir** e em **OK** para concluir a configuração do console MMC.

6.  Clique duas vezes em **Certificados (Computador Local)** para expandir os repositórios de certificados, clique duas vezes em **Pessoais** e em **Certificados**.
    
    > [!IMPORTANT]  
    > Se não houver certificados no repositório Certificados Pessoais para o computador local, não existe chave privada associada ao certificado importado. Analise a solicitação e as etapas de importação. Se o problemas persistir, entre em contato com o administrador ou fornecedor da sua autoridade de certificação.

7.  No **Repositório de Certificados Pessoais do computador local**, clique com o botão direito do mouse no certificado que você está exportando, clique em **Todas as Tarefas** e em **Exportar**.

8.  No Assistente para Exportação de Certificados, clique em **Avançar**, selecione **Sim, exportar a chave privada** e clique em **Avançar**.
    
    > [!NOTE]  
    > Se a opção <strong>Sim, exportar a chave privada</strong> não estiver disponível, a chave privada associada a este certificado não foi marcada para exportação. Será necessário solicitar o certificado novamente, garantindo que esteja marcado para permitir a exportação da chave privada antes de dar continuidade à exportação. Entre em contato com o administrador ou fornecedor da sua autoridade de certificação.

9.  Na caixa de diálogo Exportar Formatos de Arquivo, selecione **Troca de Informações Pessoais - PKCS\#12 (.PFX)** e selecione:
    
      - Incluir todos os certificados no caminho de certificação, se possível
    
      - Exportar todas as propriedades avançadas
        

        > [!WARNING]
        > Ao exportar o certificado de um servidor de Borda, não selecione <STRONG>Excluir a chave privada se a exportação tiver êxito</STRONG>. Selecionar esta opção exigirá a importação do certificado e da chave privada para este Servidor de Borda.



10. Clique em **Avançar**.

11. Digite uma senha para a chave privada, digite a senha novamente para confirmar e clique em **Avançar**.

12. Digite um caminho e nome de arquivo para o certificado exportado, usando uma extensão de arquivo .pfx. O caminho deve estar acessível a todos os outros servidores de Borda no pool ou disponível para transporte via mídia removível - por exemplo, um pen drive. Clique em **Avançar**.

13. Revise o resumo em **Concluindo o Assistente para Exportação de Certificados** e clique em **Concluir**.

14. Na caixa de diálogo de exportação bem-sucedida, clique em **OK**.

15. Importe o arquivo de certificado exportado para outros servidores de Borda seguindo as etapas descritas no procedimento "Para importar o certificado para a interface externa do Servidor de Borda" neste tópico.

## Para atribuir o certificado à interface externa do Servidor de Borda

1.  Em cada Servidor de Borda, no Assistente de Implantação, em **Etapa 3: Solicitar, Instalar ou Ceder Certificados**, clique em **Executar novamente**.

2.  Na página **Tarefas de Certificado Disponíveis**, clique em **Atribuir um certificado existente**.

3.  Na página **Atribuição de Certificado**, clique em **Certificado de Borda Externa** e marque a caixa de seleção **Usos Avançados de Certificado**.

4.  Na página **Usos Avançados de Certificado**, marque todas as caixas de seleção para atribuir o certificado a todos os usos.

5.  Na página **Repositório de Certificados**, selecione o certificado público que você solicitou e importou para a interface externa do Servidor de Borda.
    
    > [!NOTE]  
    > Se o certificado solicitado e importado não estiver na lista, um dos métodos de solução de problemas é verificar se o nome da entidade e os nomes alternativos da entidade do certificado atendem a todos os requisitos do certificado. Se você importou manualmente o certificado e a cadeia de certificados em vez de usar os procedimentos anteriores, verifique se o certificado está no repositório de certificados correto (o repositório de certificados do computador, não o repositório de certificados do usuário ou serviço).

6.  Na página **Resumo da Atribuição de Certificado**, analise suas configurações e clique em **Avançar** para atribuir os certificados.

7.  Na página de conclusão do assistente, clique em **Concluir**.

8.  Depois de usar este procedimento para atribuir o certificado de borda, abra o snap-in de Certificados em cada servidor, expanda **Certificados (Computador Local)**, expanda **Pessoais**, clique em **Certificados** e verifique se o certificado está listado no painel de detalhes.

9.  Se sua implantação incluir vários Servidores de Borda, repita este procedimento para cada um deles.

