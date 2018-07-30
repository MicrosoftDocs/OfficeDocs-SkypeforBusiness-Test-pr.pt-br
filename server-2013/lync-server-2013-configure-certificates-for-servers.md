---
title: 'Lync Server 2013: Configurar certificados para servidores'
TOCTitle: Configurar certificados para servidores
ms:assetid: e12e59b5-a146-4859-86ec-cabfc198c7b5
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398995(v=OCS.15)
ms:contentKeyID: 49308377
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurar certificados para servidores no Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

Para concluir com êxito este procedimento, você deve estar conectado como um usuário que seja membro do grupo RTCUniversalServerAdmins ou com as permissões delegadas corretas. Para obter detalhes sobre delegação de permissões, consulte [Delegar permissões de configuração no Lync Server 2013](lync-server-2013-delegate-setup-permissions.md). Dependendo da sua organização e dos requisitos para a solicitação de certificados, talvez sejam necessárias associações a outros grupos. Consulte o grupo que gerencia a autoridade de certificação da sua PKI (infraestrutura de chave pública).

> [!NOTE]  
> O Lync Server 2013 inclui suporte para o pacote do SHA-2 (o SHA-2 usa extensões de disco de 224, 256, 384 ou 512 bits) de hash de disco e algoritmos de assinatura para conexões de clientes executando o Windows 7, Windows Server 2008 R2, Windows Server 2008, Windows Vista ou Windows XP, além do Lync Phone Edition. Para suportar o acesso externo usando o pacote do SHA-2, o certificado externo é emitido por um CA público que também pode emitir um certificado com a mesma extensão disco.


> [!WARNING]
> A seleção do hash de disco e do algoritmo de assinatura dependerá do cliente e dos servidores que utilizarão o certificado, e de outros computadores e dispositivos que os clientes e servidores comunicarão a quem também deve saber como usar os algoritmos usados no certificado. Para obter mais informações sobre quais extensões de disco são suportadas no sistema operacional e em alguns aplicativos do cliente, consulte <A href="http://go.microsoft.com/fwlink/?linkid=287002">http://go.microsoft.com/fwlink/?LinkId=287002</A>.



Cada Servidor Standard Edition ou Servidor Front-End exige até quatro certificados: o certificado oAuthTokenIssuer, um certificado padrão, um certificado interno da Web e um certificado externo da Web. No entanto, é possível solicitar e atribuir um único certificado padrão com as entradas de nome de assunto alternativo, assim como o certificado oAuthTokenIssuer. Para obter detalhes sobre os requisitos de certificado, consulte [Requisitos de certificado para servidores internos no Lync Server 2013](lync-server-2013-certificate-requirements-for-internal-servers.md). Para obter detalhes sobre como solicitar, atribuir e instalar o certificado oAuthTokenIssuer, consulte [Gerenciando autenticação de servidor para servidor (Oauth) e inscrições de parceiros no Lync Server 2013](lync-server-2013-managing-server-to-server-authentication-oauth-and-partner-applications.md)

Use o seguinte procedimento para solicitar, atribuir e instalar o Servidor Standard Edition ou certificados do Servidor Front-End. Repita o procedimento para cada Servidor Front-End.

> [!IMPORTANT]  
> O procedimento a seguir descreve como configurar certificados a partir de um PKI empresarial interno implantado por sua organização e com processamento de solicitação offline. Para obter informações sobre como obter certificados de uma CA pública, consulte <a href="lync-server-2013-certificate-requirements-for-internal-servers.md">Requisitos de certificado para servidores internos no Lync Server 2013</a> na documentação Planejamento. Além disso, esse procedimento descreve como solicitar, atribuir e instalar certificados durante a configuração do Servidor Front-End. Se você tiver solicitado certificados com antecedência, conforme descrito na seção <a href="lync-server-2013-request-certificates-in-advance-optional.md">Solicitar certificados com antecedência (opcional) para Lync Server 2013</a> desta documentação Implantação ou não usar um PKI empresarial interno implantado em sua organização a fim de obter certificados, será necessário modificar esse procedimento conforme o apropriado.

## Para configurar certificados para um Servidor Front-End

1.  No Assistente de Implantação do Lync Server, clique em **Executar** ao lado de **Etapa 3: solicitar, instalar ou atribuir certificados** .

2.  Na página **Assistente de Certificados** , clique em **Solicitar** .

3.  Na página **Solicitação de Certificado** , clique em **Avançar** .

4.  Na página **Solicitações Atrasadas ou Imediatas** , é possível aceitar a opção padrão **Enviar a solicitação imediatamente para uma autoridade de certificação online** clicando em **Avançar** . A CA interna com inscrição online automática precisa estar disponível se você selecionar essa opção. Se você escolher a opção para atrasar a solicitação, receberá uma solicitação de um nome e local para salvar o arquivo de solicitação do certificado. A solicitação de certificado precisa ser apresentada a processada por uma CA dentro de sua organização ou por uma CA pública. Em seguida, será necessário importar a resposta do certificado e atribuí-la à função de certificado apropriada.

5.  Na página **Escolher uma Autoridade de certificação (CA)** , selecione a opção **Selecionar uma CA na lista detectada em seu ambiente** e uma CA conhecida (por meio do registro no Serviços de Domínio Active Directory) na lista. Em alternativa, selecione a opção **Especificar outra autoridade de certificação** , digite o nome de outra CA na caixa e clique em **Avançar** .

6.  Na página **Conta da Autoridade de Certificação** , você recebe uma solicitação por credenciais para solicitar e processar a solicitação de certificado na CA. Você deve ter determinado se um nome de usuário e senha são necessários para solicitar um certificado com antecedência. Seu administrador de CA terá as informações necessárias e talvez precise ajudá-lo com essa etapa. Se você precisar de credenciais alternativas, marque a caixa de seleção, forneça um nome de usuário e senha nas caixas de texto e clique em **Avançar** .

7.  Na página **Especificar Modelo de Certificado Alternativo** , para usar o modelo de Servidor da web padrão, clique em **Avançar** .
    
    > [!NOTE]  
    > Se sua organização tiver criado um modelo para ser usado como uma alternativa para o modelo de CA padrão do Servidor da web, marque a caixa de seleção, e digite o nome do modelo alternativo. Você precisará do nome do modelo, conforme definido pelo administrador de CA.

8.  Na página **Nome e Configurações de Segurança** , especifique um **Nome Amigável** que deve permiti-lo identificar o certificado e a finalidade. Se você deixá-lo em branco, um nome será gerado automaticamente. Defina o **Tamanho do bit** da chave ou aceite o padrão de 2048 bits. Selecione **Marcar a chave privada do certificado como exportável** se você determinar que o certificado e a chave privada precisam ser movidos ou copiados para outros sistemas e clique em **Avançar** .
    
    > [!NOTE]  
    > O Lync Server 2013 tem requisitos mínimos para uma chave privada exportável. Um local como esse é nos Servidores de Borda em um pool, onde o Serviço de Autenticação de Media Relay usa cópias do certificado, em vez de certificados individuais para cada instância no pool.

9.  Na página **Informações da Organização** , forneça, opcionalmente, as informações da organização e clique em **Avançar** .

10. Na página **Informações Geográficas** , forneça, opcionalmente, informações geográficas e clique em **Avançar** .

11. Na página **Nome da Entidade/Nomes Alternativos da Entidade** , revise os nomes alternativos da entidade que serão adicionados e clique em **Avançar** .

12. Na página **Configuração do Domínio SIP** , selecione o **Domínio SIP** e clique em **Avançar** .

13. Na página **Configurar Nomes Alternativos da Entidade Adicionais** , adicione quaisquer nomes alternativos da entidade adicionais necessários, incluindo qualquer um que possa ser exigido para domínios SIP adicionais no futuro, e clique em **Avançar** .

14. Na página **Resumo da Solicitação de Certificado** , revise as informações no resumo. Se as informações estiverem corretas, clique em **Avançar** . Se você precisar corrigir ou modificar uma configuração, clique em **Voltar** para a página apropriada a fim de fazer a correção ou modificação.

15. Na página **Executando Comandos** , clique em **Avançar** .

16. Na página **Status da Solicitação de Certificado Online** , revise as informações retornadas. Observe que o certificado foi emitido e instalado no repositório de certificados local. Se ele for reportado como emitido e instalado, mas não estiver válido, certifique-se de que o certificado raiz CA tenha sido instalado no repositório de CA raiz confiável do servidor. Consulte sua documentação de CA sobre como recuperar um certificado CA raiz confiável. Se você precisar ver o certificado recuperado, clique em **Exibir Detalhes do Certificado** . Por padrão, a caixa de seleção **Atribuir o certificado às utilizações de certificado do Lync Server** está marcada. se você quiser atribuir manualmente o certificado, desmarque a caixa e clique em **Concluir** .

17. Se você tiver desmarcado a caixa de seleção para **Atribuir o certificado às utilizações de certificado do Lync Server** na página anterior, será encaminhado à página **Atribuição de Certificado** . Clique em **Avançar** .

18. Na página **Repositório de Certificados** , selecione o certificado que você solicitou. Se você quiser ver o certificado, clique em **Exibir Detalhes do Certificado** e clique em **Avançar** para continuar.
    
    > [!NOTE]  
    > Se a página <strong>Status da Solicitação de Certificado Online</strong> informar um problema com o certificado, como um certificado inválido, a exibição do certificado real pode ajudar a resolver o problema. Dois problemas específicos que podem causar a invalidez de um certificado são a ausência mencionada anteriormente do certificado CA raiz confiável e a ausência de uma chave privada associada ao certificado. Consulte sua documentação de CA para resolver esses dois problemas.

19. Na página **Resumo de Atribuição de Certificado** , examine as informações apresentadas a fim de garantir que esse certificado deve ser atribuído e clique em **Avançar** .

20. Na página **Executando Comandos** , revise a saída do comando. Clique em **Exibir Log** se quiser revisar o processo de atribuição ou se houver um erro ou aviso. Após a conclusão da revisão, clique em **Concluir** .

21. Na página **Assistente de Certificados** , verifique se o **Status** do certificado está como “Atribuído” e clique em **Fechar** .

## Consulte Também

#### Outros Recursos

[Requisitos de infraestrutura de certificado para o Lync Server 2013](lync-server-2013-certificate-infrastructure-requirements.md)

