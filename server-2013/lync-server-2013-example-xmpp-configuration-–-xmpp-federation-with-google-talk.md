---
title: 'Lync Server 2013: Exemplo de configuração de XMPP no Lync Server 2013 – federação XMPP com Google Talk'
TOCTitle: Exemplo de configuração de XMPP – federação XMPP com Google Talk
ms:assetid: 360a2f7b-015b-4e93-ac67-0f609c21f1a2
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204807(v=OCS.15)
ms:contentKeyID: 49306366
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Exemplo de configuração de XMPP no Lync Server 2013 – federação XMPP com Google Talk

 

_**Tópico modificado em:** 2016-12-08_

Um exemplo de configuração para implantar o proxy XMPP é a federação com o Google Talk.

## Exemplo de configuração XMPP – Federação XMPP com o Google Talk

1.  No Servidor Front-End, abra o Assistente de Implantação do Lync Server. Clique em **Instalar** ou **Atualizar Sistema do Lync Server** e depois clique em **Instalar** ou **Remover Componentes do Lync Server**. Clique em **Executar Novamente**.

2.  Em **Instalar Componentes do Lync Server**, clique em **Avançar**. A tela de resumo exibirá as ações conforme foram executadas. Depois que a implantação estiver concluída, clique em **Exibir Log** para exibir os arquivos de log disponíveis. Clique em **Concluir** para concluir a implantação.

3.  No Servidor de Borda, abra o Assistente de Implantação do Lync Server. Clique em **Instalar** ou **Atualizar Sistema do Lync Server** e, depois, clique em **Instalar** ou **Remover Componentes do Lync Server**. Clique em **Executar Novamente**.

4.  Adicione o Google Talk como um parceiro XMPP permitido. O Google Talk suporta atualmente apenas conexões TCP não criptografadas para federação XMPP se servidor para servidor e suporta apenas o Server Dialback para verificação de identidade. (Consulte <http://xmpp.org/extensions/xep-0220.html>).
    
        New-CsXmppAllowedPartner gmail.com -TlsNegotiation NotSupported -SaslNegotiation NotSupported -EnableKeepAlive $false -SupportDialbackNegotiation $true

5.  Para habilitar a federação de borda, digite o seguinte:
    
        Set-CsAccessEdgeConfiguration -AllowFederatedUsers $true

6.  Em **Instalação de Componentes do Lync Server**, clique em **Avançar**. A tela de resumo exibirá as ações conforme foram executadas. Depois que a implantação estiver concluída, clique em **Exibir Log** para exibir os arquivos de log disponíveis. Clique em **Concluir** para concluir a implantação.

7.  No Servidor de Borda, no Assistente de Implantação do Lync Server, ao lado de **Etapa 3: Solicitar, Instalar ou Atribuir Certificados**, clique em **Executar Novamente**.
    

    > [!TIP]
    > Se estiver implantando o Servidor de Borda pela primeira vez, você verá Executar ao invés de Executar novamente.



8.  Na página **Tarefas de Certificado Disponíveis**, clique em **Criar uma nova solicitação de certificado**.

9.  Na página **Solicitação de Certificado**, clique em **Certificado de Borda Externa**.

10. Na página **Solicitação Atrasada ou Imediata**, marque a caixa de seleção **Preparar a solicitação agora, mas enviá-la depois**.

11. Na página **Arquivo de Solicitação de Certificado**, digite o nome de arquivo e o caminho completo do arquivo no qual a solicitação será salva (por exemplo, c:\\cert\_exernal\_edge.cer).

12. Na página **Especificar Modelo de Certificado Alternativo**, para usar um modelo diferente do modelo WebServer padrão, marque a caixa de seleção **Usar o modelo de certificado alternativo para a autoridade de certificação selecionada**.

13. Na página **Nome e Configurações de Segurança**, siga estes procedimentos:
    
    1.  Em **Nome amigável**, digite um nome de exibição para o certificado
    
    2.  Em **Comprimento de bit**, especifique o comprimento de bit (geralmente, o padrão é **2048** )
    
    3.  Verifique se a caixa de seleção **Marcar chave privada do certificado como exportável** está marcada

14. Na página **Informações da Organização**, digite o nome da organização e da unidade organizacional (por exemplo, uma divisão ou um departamento)

15. Na página **Informações Geográficas**, especifique as informações de local

16. Na página **Nome da Entidade/Nomes Alternativos da Entidade**, as informações a serem preenchidas automaticamente pelo assistente são exibidas. Se nomes da entidade adicionais forem necessários, especifique-os nas próximas duas etapas

17. Na página **Configuração do Domínio SIP em SANs (Nomes Alternativos da Entidade)**, marque a caixa de seleção do domínio para adicionar uma entrada sip. *\<domínio\_sip\>* à lista de nomes alternativos da entidade.

18. Na página **Configurar Nomes Alternativos da Entidade Adicionais**, especifique quaisquer nomes alternativos de entidade adicionais que sejam necessários.
    

    > [!TIP]
    > Se o proxy XMPP é instalado, por padrão o nome de domínio (como contoso.com) é preenchido nas entradas SAN. Se você precisa de mais entradas, adicione-as nesta etapa.



19. Na página **Resumo da Solicitação**, examine as informações do certificado a ser usado para gerar a solicitação.

20. Depois que a execução do comando estiver concluída, será possível **Exibir Log** ou clicar em **Avançar** para continuar.

21. Na página **Arquivo de solicitação de certificado**, é possível exibir o arquivo CSR gerado clicando em **Exibir** ou sair do Assistente de Certificado clicando em **Concluir**.

22. Copie o arquivo solicitado e envie-o para a autoridade de certificação pública.

23. Depois de receber, importar e atribuir o certificado público, é preciso interromper e reiniciar os serviços do servidor de borda. Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.. No Shell de Gerenciamento do Lync Server, digite:
    
```
Stop-CsWindowsService
```
```    
Start-CsWindowsService
```

24. Para configurar o DNS para federação XMPP, adicione o seguinte registro SRV ao DNS externo:\_xmpp-server.\_tcp. *\<nome do domínio\>* O registro SRV resolverá o FQDN de borda de acesso do servidor de borda com o valor da porta 5269

25. Configure uma nova política de acesso externo para permitir que todos os usuários abram o Shell de Gerenciamento do Lync Server em um Servidor Front-End e digitem:
    
```
New-CsExternalAccessPolicy -Identity FedPic -EnableFederationAccess $true -EnablePublicCloudAccess $true
```
```
Get-CsUser | Grant-CsExternalAccessPolicy -PolicyName FedPic
```