---
title: 'Lync Server 2013: Configurar certificados para a interface de borda interna'
TOCTitle: Configurar certificados para a interface de borda interna
ms:assetid: a1963cc9-87c5-4935-86c0-6bedc6afd0ac
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg412750(v=OCS.15)
ms:contentKeyID: 49307653
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurar certificados para a interface de borda interna no Lync Server 2013

 

_**Tópico modificado em:** 2013-11-07_

> [!IMPORTANT]  
> Ao executar o Assistente de Certificado, certifique-se de que você está conectado usando uma conta que seja membro de um grupo ao qual tenham sido atribuídas as permissões apropriadas para o tipo de modelo de certificado que será utilizado. Por padrão, uma solicitação de certificado do Lync Server 2013 utilizará o modelo de certificado do Servidor Web. Se uma conta membro do grupo RTCUniversalServerAdmins for utilizada para solicitar um certificado usando este modelo, verifique se foram atribuídas as permissões Inscrever a este grupo, necessárias para usar o modelo.

Um único certificado é necessário na interface interna de cada Servidor de Borda. Os certificados para a interface interna podem ser emitidos por uma autoridade de certificação empresarial interna ou por uma autoridade de certificação pública. Se a sua organização tiver uma autoridade de certificação interna implantada, poderá diminuir as despesas de uso de certificados públicos utilizando a autoridade de certificação interna para emitir o certificado para a interface interna. Você pode usar uma autoridade de certificação interna do Windows Server 2008 ou uma autoridade de certificação do Windows Server 2008 R2 para criar esses certificados.

Para detalhes sobre este e outros requisitos de certificado, consulte [Requisitos de certificado para acesso do usuário externo no Lync Server 2013](lync-server-2013-certificate-requirements-for-external-user-access.md).

Para configurar certificados na interface da borda interna em um site, use os procedimentos nesta seção para:

1.  Fazer download da cadeia de certificação da AC para a interface interna para cada Servidor de Borda.

2.  Importar a cadeia de certificação do para a interface interna, em cada Servidor de Borda.

3.  Criar a solicitação de certificado da interface externa em um Servidor de Borda, considerado o primeiro Servidor de Borda.

4.  Importar o certificado da interface interna no primeiro Servidor de Borda.

5.  Importar o certificado nos outros Servidores de Borda neste local (ou implantados por trás deste balanceador de carga).

6.  Atribuir o certificado à interface interna de cada Servidor de Borda.

Se você tem mais de um local com Servidores de Borda (ou seja, uma topologia de borda de múltiplos locais) ou conjuntos separados de Servidores de Borda implantados por trás de diferentes balanceadores de carga, é necessário seguir estas etapas para cada local que possua Servidores de Borda e para cada conjunto de Servidores de Borda implantados por trás de um balanceador de carga diferente.

> [!NOTE]  
> As etapas dos procedimentos nesta seção são baseadas na utilização de uma AC do Windows Server 2008, AC do Windows Server 2012, AC do Windows Server 2008 R2 ou AC do Windows Server 2012 R2 para criar um certificado para cada Servidor de Borda. Para uma orientação passo a passo para qualquer outra AC, consulte a documentação para aquela AC. Por padrão, todos os usuários autenticados possuem os direitos de usuário apropriados para solicitar certificados.<br />Os procedimentos nesta seção são baseados na criação de solicitações de certificado no Servidor de Borda como parte do processo de implantação do Servidor de Borda. É possível criar solicitações de certificado usando o Servidor Front End. Faça isso para concluir a solicitação do certificado mais cedo no processo de planejamento e implantação, antes de começar a implantação dos Servidores de Borda. Para isso, você deve garantir que o certificado a ser solicitado é definido como uma chave privada que pode ser exportada.<br />Os procedimentos nesta seção descrevem a utilização de um arquivo .cer e um arquivo .p7b para o certificado. Se você usa um tipo diferente de arquivo, modifique estes procedimentos de acordo.

## Para fazer download da cadeia de certificação da AC para a interface interna usando o website certsrv

1.  Faça logon em um servidor do Lync Server 2013 na rede interna (ou seja, não no Servidor de Borda) como membro do grupo **Administradores**.

2.  Execute o comando a seguir no prompt de comando, clicando em **Iniciar**, **Executar** e digitando:
    
        https://<name of your Issuing CA Server>/certsrv
    
    Por exemplo:
    
        https://ca01.contoso.net/certsrv
    
    > [!NOTE]  
    > Se estiver usando uma AC do Windows Server 2008 ou Windows Server 2008 R2 Enterprise, você deve usar https, não http.

3.  Na página web certsrv da AC emissora, em **Selecione uma tarefa**, clique em **Download de um Certificado de Autoridade de Certificação, Cadeia de Certificados ou Lista de Certificados Revogados**.

4.  Em **Download de um Certificado de Autoridade de Certificação, Cadeia de Certificados ou Lista de Certificados Revogados**, clique em **Fazer download de cadeia de certificados de autoridade de certificação**.

5.  Na caixa de diálogo **Download de Arquivo**, clique em **Salvar**.

6.  Salve o arquivo .p7b na unidade de disco rígido e copie-o para uma pasta em cada Servidor de Borda.
    
    > [!NOTE]  
    > O arquivo .p7b contém todos os certificados existentes no caminho de certificação. Para exibir o caminho de certificação, abra o certificado do servidor e clique no caminho de certificação.

## Para importar a cadeia de certificação da AC para a interface interna usando MMC

1.  Você pode exportar o certificado raiz da AC de qualquer máquina associada ao domínio, usando o Console de Gerenciamento Microsoft (MMC). Clique em **Iniciar**, **Executar** e depois digite **MMC**.

2.  No console do MMC, clique em **Arquivo** e em **Adicionar/Remover**.

3.  Na lista de diálogos **Adicionar/Remover Snap-ins**, selecione **Certificados**, e depois clique em **Adicionar**. Ao ser solicitado, selecione **Conta do computador**. No diálogo **Selecionar computador**, selecione **Computador local**. Clique em **Finalizar**. Clique em **OK**.

4.  Expanda **Certificados (Computador local)**. Expanda **Autoridades de Certificação Raiz Confiáveis.**, selecione **Certificados**.

5.  Clique no certificado raiz emitido por sua AC. Clique com o botão direito no certificado, selecione **Todas as tarefas**, selecione **Exportar**. O **Assistente de Exportação de Certificado** será aberto.

6.  No **Assistente de Exportação de Certificado**, clique em **Avançar**.

7.  Na caixa de diálogo **Formato do arquivo de exportação**, selecione um formato para exportar. Recomendamos o **Cryptographic Message Syntax Standard - PKCS \#7 Certificates (.P7B)**. Se você selecionar **Cryptographic Message Syntax Standard - PKCS \#7 Certificates (.P7B)**, marque a caixa de seleção **Incluir todos os certificados no caminho de certificação, se possível** para exportar a cadeia de certificado, incluindo o certificado AC raiz e qualquer certificado AC intermediário. Clique em **Avançar**.

8.  Na caixa de diálogo **Arquivo para exportar**, na entrada do nome do arquivo, digite um caminho e nome de arquivo (a extensão padrão é .p7b) para o certificado exportado. Opcionalmente, clique em **Procurar**, localize um diretório para colocar o certificado exportado e forneça um nome para o certificado exportado. Clique em **Salvar**. Clique em **Avançar**.

9.  Revise o resumo de ações e clique em **Concluir** para concluir a exportação do certificado. Clique em **OK** para confirmar que a exportação foi bem sucedida.

## Para importar a cadeia de certificação da AC para a interface interna

1.  Em cada Servidor de Borda, abra o Console de Gerenciamento Microsoft clicando em **Iniciar**, clicando em **Executar**, digitando **mmc** na caixa **Abrir** e clicando em **OK**.

2.  No menu **Arquivo**, clique em **Adicionar/Remover Snap-in** e, em seguida, clique em **Adicionar**.

3.  Na caixa **Adicionar Snap-in Autônomo**, clique em **Certificados** e, em seguida, clique em **Adicionar**.

4.  Na caixa de diálogo **Snap-in de certificados**, clique em **Conta de computador** e, em seguida, clique em **Avançar**.

5.  Na caixa de diálogo **Selecionar computador**, certifique-se de que a opção **Computador local: (o computador em que este console está sendo executado)** esteja marcada e clique em **Concluir**.

6.  Clique em **Fechar** e em **OK**.

7.  Na árvore do console, expanda **Certificados (computador local)**, clique com o botão direito em **Autoridades de Certificação Confiáveis**, aponte para **Todas as tarefas** e clique em **Importar**.

8.  No assistente, em **Arquivo a ser importado**, especifique o nome do arquivo do certificado (ou seja, o nome que você especificou quando fez o download da cadeia de certificado da AC para a interface interna no procedimento anterior).

9.  Repita esse procedimento em cada Servidor de Borda.

## Para criar a solicitação de certificado da interface interna

1.  Em um dos Servidores de Borda, inicie o Assistente de Implantação e na **Etapa 3: Solicitar, Instalar ou Ceder Certificados**, clique em **Executar**.
    
    > [!NOTE]  
    > Se houver vários Servidores de Borda em uma localização em um pool, você pode executar o Assistente de Certificado em qualquer um deles.<br />    Depois de executar a Etapa 3 pela primeira vez, o botão é alterado para <strong>Executar novamente</strong> e uma marca de seleção verde que indica a conclusão bem sucedida da tarefa não é exibida até que todos os certificados tenham sido solicitados, instalados e cedidos.

2.  Na página **Tarefas de Certificado Disponíveis**, clique em **Criar uma nova solicitação de certificado**.

3.  Na página **Solicitação de Certificado**, clique em **Avançar**.

4.  Na página **Solicitações Atrasadas ou Imediatas**, clique em **Preparar a solicitação agora, mas enviá-la depois**.

5.  Na página **Arquivo de Solicitação de Certificado**, digite o caminho completo e o nome do arquivo em que a solicitação será salva (por exemplo, **c:\\cert\_internal\_edge.cer** ).

6.  Na página **Especificar Modelo de Certificado Alternativo**, para usar um modelo diferentes do modelo padrão do WebServer, marque a opção **Usar modelo de certificado alternativo para a Autoridade de Certificação selecionada**.

7.  Na página **Nome e Configurações de Segurança**, siga estes procedimentos:
    
      - Em **Nome amigável**, digite um nome de exibição para o certificado (por exemplo, Borda Interna).
    
      - Em **Comprimento de bit**, especifique o comprimento de bit (normalmente o padrão de **2048** ).
        
        > [!NOTE]  
        > Comprimentos de bit mais altos oferecem mais segurança, mas causam um impacto negativo sobre a velocidade.    
      - Se for necessário que o certificado seja exportável, marque a opção **Marcar chave privada do certificado como exportável**.

8.  Na página **Informações da Organização**, digite o nome da organização e da unidade organizacional (UO) (por exemplo, uma divisão ou departamento).

9.  Na página **Informações Geográficas**, especifique as informações de localização.

10. Na página **Nome da Entidade/Nomes Alternativos da Entidade**, as informações a serem preenchidas automaticamente pelo assistente são exibidas.

11. Na página **Configurar Nomes Alternativos da Entidade Adicionais**, especifique quaisquer nomes alternativos de entidade adicionais que sejam necessários.

12. Na página **Resumo da Solicitação**, analise as informações do certificado a serem usadas para gerar a solicitação.

13. Depois de concluir os comandos, siga o seguinte procedimento:
    
      - Para exibir o log da solicitação do certificado, clique em **Exibir Log**.
    
      - Para concluir a solicitação do certificado, clique em **Avançar**.

14. Na página **Arquivo de Solicitação de Certificado**, siga o seguinte procedimento:
    
      - Para exibir o arquivo de solicitação de assinatura de certificado (CSR), clique em **Exibir**.
    
      - Para fechar o assistente, clique em **Concluir**.

15. Envie este arquivo para a sua AC (por e-mail ou por outro método aceito pela sua organização para sua AC corporativa) e, quando receber o arquivo de resposta, copie o novo certificado para este computador, para que esteja disponível para importação.

## Para importar o certificado da interface interna

1.  Faça logon no Servidor de Borda em que você criou a solicitação de certificado como membro do grupo Administradores local.

2.  No Assistente de Implantação, em **Etapa 3: Solicitar, Instalar ou Ceder Certificados**, clique em **Executar novamente**.
    
    Depois de executar a Etapa 3 pela primeira vez, o botão é alterado para **Executar novamente**, mas uma marca de seleção verde que indica a conclusão bem sucedida da tarefa não é exibida até que todos os certificados tenham sido solicitados, instalados e cedidos.

3.  Na página **Tarefas de Certificado Disponíveis**, clique em **Importar um certificado de um arquivo .P7b, .pfx ou .cer**.

4.  Na página **Importar Certificado**, digite o caminho completo e nome do arquivo do certificado que você solicitou e recebeu para a interface interna deste Servidor De Borda (ou clique em **Procurar** para localizar e selecionar o arquivo).

5.  Se você estiver importando certificados para outros membros do pool, um certificado que contenha uma chave privada, marque a opção **O arquivo do certificado contém a chave privada do certificado** e especifique a senha.

## Para exportar o certificado com a chave privada para os Servidores de Borda em um pool

1.  Faça logon como membro do grupo Administradores no mesmo Servidor de Borda em que o certificado foi importado.

2.  Clique em **Iniciar**, **Executar** e digite **MMC** .

3.  No console do MMC, clique em **Arquivo** e em **Adicionar/Remover Snap-in**.

4.  Na página Adicionar ou Remover Snap-ins, clique em **Certificados** e em **Adicionar**.

5.  Na caixa de diálogo Snap-in de certificados, selecione **Conta de computador**. Clique em **Avançar**. Em Selecionar Computador, selecione **Computador local: (o computador no qual este console está sendo executado)**. Clique em **Concluir**. Clique em **OK** para concluir a configuração do console MMC.

6.  Dê um duplo clique em **Certificados (Computador Local)** para expandir o repositório de certificados. Dê um duplo clique em **Pessoal** e em **Certificados**.
    
    > [!IMPORTANT]  
    > Se não houver certificados no repositório Certificados Pessoais para o computador local, não existe chave privada associada ao certificado importado. Analise a solicitação e as etapas de importação. Se o problemas persistir, entre em contato com o administrador ou fornecedor da sua autoridade de certificação.

7.  No repositório Certificados Pessoais para o computador local, clique com o botão direito no certificado que está exportando. Clique em **Todas as Tarefas** e em **Exportar**.

8.  No Assistente de Exportação de Certificado, clique em **Avançar**. Selecione **Sim, exportar a chave privada**. Clique em **Avançar**.
    
    > [!NOTE]  
    > Se a opção <strong>Sim, exportar a chave privada</strong> não estiver disponível, a chave privada associada a este certificado não foi marcada para exportação. Será necessário solicitar o certificado novamente, garantindo que esteja marcado para permitir a exportação da chave privada antes de dar continuidade à exportação. Entre em contato com o administrador ou fornecedor da sua autoridade de certificação.

9.  Na caixa de diálogo Exportar Formatos de Arquivo, selecione **Troca de Informações Pessoais - PKCS\#12 (.PFX)** e selecione:
    
      - Incluir todos os certificados no caminho de certificação, se possível
    
      - Exportar todas as propriedades avançadas
        

        > [!WARNING]
        > Ao exportar o certificado de um servidor de Borda, não selecione <STRONG>Excluir a chave privada se a exportação tiver êxito</STRONG>. Selecionar esta opção exigirá a importação do certificado e da chave privada para este Servidor de Borda.

    
    Clique em **Avançar** para continuar.

10. Se desejar atribuir uma senha para proteger a chave privada, digite uma senha para a chave privada. Insira novamente a senha para confirmar. Clique em **Avançar**.

11. Digite um caminho e nome de arquivo para o certificado exportado, usando uma extensão de arquivo .pfx. O caminho deve estar acessível a todos os outros servidores de Borda no pool ou disponível para transporte via mídia removível - por exemplo, um pen drive. Clique em **Avançar**.

12. Analise o resumo na caixa de diálogo Concluindo o Assistente para Exportação de Certificados. Clique em **Concluir**.

13. Clique em **OK** na caixa de diálogo da exportação com sucesso.

14. Importe o certificado exportado para os outros servidores de Borda seguindo as etapas descritas nos procedimentos em [Configurar certificados para a interface de borda externa para Lync Server 2013](lync-server-2013-set-up-certificates-for-the-external-edge-interface.md).

## Para atribuir o certificado interno aos Servidores de Borda

1.  Em cada Servidor de Borda, no Assistente de Implantação, em **Etapa 3: Solicitar, Instalar ou Ceder Certificados**, clique em **Executar novamente**.

2.  Na página **Tarefas de Certificado Disponíveis**, clique em **Atribuir um certificado existente**.

3.  Na página **Atribuição de Certificado**, selecione **Interno à Borda** na lista.

4.  Na página **Repositório de Certificados**, selecione o certificado importado para a borda interna (no procedimento anterior).

5.  Na página **Resumo da Atribuição de Certificado**, analise suas configurações e clique em **Avançar** para atribuir os certificados.

6.  Na página de conclusão do assistente, clique em **Concluir**.

7.  Depois de usar este procedimento para atribuir o certificado de borda interna, abra o Snap-in de Certificados em cada servidor, expanda **Certificados (computador local)**, expanda **Pessoal**, clique em **Certificados** e verifique no painel de detalhes se o certificado da borda interna está listado.

8.  Se sua implantação incluir vários Servidores de Borda, repita este procedimento para cada um deles.

