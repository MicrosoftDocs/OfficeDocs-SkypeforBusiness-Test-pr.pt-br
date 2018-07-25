---
title: Configurar gateway XMPP no Lync Server 2013
TOCTitle: Configurar gateway XMPP no Lync Server 2013
ms:assetid: 00777a34-cc36-4992-9459-08c14543ef6b
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ687953(v=OCS.15)
ms:contentKeyID: 49886078
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurar gateway XMPP no Lync Server 2013

 

_**Tópico modificado em:** 2012-10-19_

Quando você configura políticas de suporte de parceiros federados XMPP (extensible messaging and presence protocol), as políticas se aplicam a usuários de domínios federados XMPP, mas não a usuários de provedores de serviço de IM (mensagem instantânea) de SIP (protocolo de iniciação de sessão) (por exemplo, Windows Live) ou domínios federados SIP. Configure um Parceiro Federado XMPP para cada domínio federado XMPP ao qual você que deseja permitir que seus usuários adicionem contatos e se comuniquem. Após a aplicação das políticas, é necessário executar outras tarefas como configurar os certificados de Gateway XMPP, implantar o Gateway XMPP do Lync Server 2013 e finalmente atualizar os registros DNS do Gateway XMPP.

## Configurar certificados do Gateway XMPP no Servidor de Borda do Lync Server 2013

1.  No Servidor de Borda, no Assistente de Implantação, próximo a **Etapa 3: Solicitar, instalar ou atribuir certificados**, clique em **Executar novamente**.
    

    > [!TIP]
    > Se estiver implantando o Servidor de Borda pela primeira vez, você verá Executar ao invés de Executar novamente.



2.  Na página **Tarefas de Certificado Disponíveis**, clique em **Criar uma nova solicitação de certificado**.

3.  Na página **Solicitação de Certificado**, clique em **Certificado de Borda Externa**.

4.  Na página **Solicitação Atrasada ou Imediata**, marque a caixa de seleção **Preparar a solicitação agora, mas enviá-la depois**.

5.  Na página **Arquivo de Solicitação de Certificado**, digite o nome de arquivo e o caminho completo do arquivo no qual a solicitação será salva (por exemplo, c:\\cert\_exernal\_edge.cer).

6.  Na página **Especificar Modelo de Certificado Alternativo**, para usar um modelo diferente do modelo WebServer padrão, marque a caixa de seleção **Usar o modelo de certificado alternativo para a autoridade de certificação selecionada**.

7.  Na página **Nome e Configurações de Segurança**, siga estes procedimentos:
    
    1.  Em **Nome amigável**, digite um nome para exibição do certificado.
    
    2.  Em **Comprimento de bit**, especifique o comprimento de bit (normalmente o padrão de 2048).
    
    3.  Verifique se a caixa de seleção **Marcar chave privada de certificado como exportável** está marcada.

8.  Na página **Informações da Organização**, digite o nome da organização e a unidade organizacional (por exemplo, uma divisão ou departamento).

9.  Na página **Informações Geográficas**, especifique as informações de localização.

10. Na página **Nome da Entidade/Nomes Alternativos da Entidade**, as informações a serem preenchidas automaticamente pelo assistente são exibidas. Se nomes alternativos de entidade adicionais forem necessários, especifique-os nas próximas duas etapas.

11. Na página **Configuração do Domínio SIP em SANs (Nomes Alternativos da Entidade)**, marque a caixa de seleção do domínio para adicionar uma entrada sip.\<domínio\_sip\> à lista de nomes alternativos da entidade.

12. Na página **Configurar Nomes Alternativos da Entidade Adicionais**, especifique quaisquer nomes alternativos de entidade adicionais que sejam necessários.
    

    > [!TIP]
    > Se o proxy XMPP é instalado, por padrão o nome de domínio (como contoso.com) é preenchido nas entradas SAN. Se você precisa de mais entradas, adicione-as nesta etapa.



13. Na página **Resumo da Solicitação**, examine as informações do certificado a ser usado para gerar a solicitação.

14. Depois que a execução do comando estiver concluída, será possível **Exibir Log** ou clicar em **Avançar** para continuar.

15. Na página **Arquivo de Solicitação de Certificado**, veja o arquivo de solicitação de assinatura de certificado (CSR) gerado clicando em Exibir ou saia do Assistente de Certificado clicando em **Concluir**.

16. Copie o arquivo solicitado e envie-o para a autoridade de certificação pública.

17. Após receber, importar e atribuir o certificado público, você deve parar e reiniciar os serviços do Servidor de Borda. Você faz isso digitando no console do Gerenciamento do Lync Server:
    
```
        Stop-CsWindowsService
```
```    
        Start-CsWindowsService
```

## Configurar um novo Gateway XMPP do Lync Server 2013

1.  Abrir o Painel de Controle do Lync Server.

2.  Na barra de navegação esquerda, clique em **Acesso Externo e Federação** e em **Parceiros XMPP Federados**.

3.  Para criar uma nova configuração, clique em **Novo**.

4.  Defina as configurações globais:

5.  **Domínio primário**     (Obrigatório). O domínio primário é o domínio base do parceiro XMPP. Por exemplo, você deveria inserir **fabrikam.com** para o nome de domínio do parceiro XMPP. Esta é uma entrada necessária.

6.  **Descrição**    A descrição é para notas ou outra informação de identificação desta determinada configuração. Esta entrada é opcional.

7.  **Domínios adicionais**    Os domínios adicionais são domínios que fazem parte do seu domínio do parceiro XMPP que devem ser incluídos como parte da comunicação XMPP permitida. Por exemplo, se o domínio primário é **fabrikam.com**, você deve listar todos os outros domínios sob fabrikam.com que irão se comunicar através do XMPP.

8.  **Tipo de parceiro**    O **Tipo de parceiro** é uma configuração obrigatória. Você deve escolher um dos seguintes para descrever e forçar quais contatos podem ser adicionados. É possível selecionar entre:
    
      - **Federado**    Um tipo de parceiro **Federado** representa um alto nível de confiança entre a implantação do Lync Server e o parceiro XMPP.  Este tipo de parceiro é recomendado para federação com servidores XMPP dentro da mesma empresa ou se há uma relação comercial estabelecida. Os contatos XMPP nos parceiros Federados podem:
        
        1.  Adicionar contatos do Lync e exibir sua presença sem autorização expressa do usuário Lync.
        
        2.  Enviar mensagens instantâneas para contatos do Lync se o usuário do Lync os adicionou ou não em sua lista de contatos.
        
        3.  Veja as notas de status do usuário do Lync.
    
      - **Público verificado**    Um parceiro **Público verificado** é um provedor XMPP público confiável para verificar a identidade de seus usuários. Os contatos XMPP nas redes Públicas verificadas podem adicionar contatos do Lync e exibir sua presença e enviar mensagens instantâneas para eles sem expressar a autorização dos usuários do Lync. Os contatos do XMPP em redes verificadas públicas nunca veem as notas de status dos usuários do Lync. Esta configuração não é recomendada.
    
      - **Público não verificado**    Um parceiro **Público não verificado** é um provedor XMPP público não confiável para verificar a identidade de seus usuários. Os usuários do XMPP nas redes Públicas não verificadas não podem se comunicar com os usuários do Lync a não ser que o usuário Lync tenha autorizado expressamente adicionando-os à lista de contatos.  Os usuários do XMPP em redes públicas não verificadas nunca veem as notas de status dos usuários do Lync.  Esta configuração é recomendada para qualquer federação com provedores XMPP públicos como o Google Talk.

9.  **Tipo de conexão:** Define as várias regras e configurações de discagem.
    
      - **Negociação TLS**    define as regras de negociação TLS. Um serviço XMPP pode requerer TLS, pode tornar TLS opcional ou você define que o TLS não é suportado. Escolher Opcional deixa o requisito por conta do serviço XMPP para uma decisão de negociação de obrigatoriedade. Para ver todas as configurações possíveis e detalhes para SASL, TLS e negociação de Retorno de chamada - incluindo configurações não válidas e de erro conhecido - consulte [Configurações de negociação para parceiros de XMPP federados no Lync Server 2013](lync-server-2013-negotiation-settings-for-xmpp-federated-partners.md)
        
           **Obrigatório**    O serviço XMPP exige a negociação TLS.
        
           **Opcional**    O serviço XMPP indica que o TLS é obrigatório para negociar.
        
           **Não suportado**    O serviço XMPP não suporta TLS.
    
      - **Negociação SASL**    Define as regras de negociação SASL. Um serviço XMPP pode exigir SASL, pode tornar SASL opcional ou definir que o SASL não é suportado. Escolher Opcional deixa os requisitos para o serviço XMPP parceiro para uma decisão de obrigatório para negociar.
        
           **Obrigatório**    O serviço XMPP exige negociação SASL.
        
           **Opcional**    O serviço XMPP indica que o SASL é obrigatório para negociar.
        
           **Não suportado**    O serviço XMPP não suporta SASL.
    
      - **Negociação de discagem do servidor de suporte** O processo de negociação de discagem do servidor de suporte usa o DNS e um servidor autoritativo para verifique se a solicitação veio de um parceiro XMPP válido. Para fazer isso, o servidor originador cria uma mensagem de um tipo específico com uma chave de discagem gerada e procura o servidor de recebimento no DNS. O servidor originador envia a chave em um fluxo XML para a pesquisa DNS resultante, provavelmente o servidor recebedor. Na receita do fluxo chave sobre XML, o servidor recebedor não responde ao servidor originador, mas envia a chave para um servidor autoritativo conhecido. O servidor autoritativo verifica se a chave é válida ou inválida. Se não for válida, o servidor recebedor não responde ao servidor originador. Se a chave é válida, o servidor recebedor informa ao servidor originador que a identidade e a chave é válida e a conversação pode começar.
        
        Existem dois estados válidos para **Negociação de discagem**:
        
           **Verdadeiro**    O servidor XMPP é configurado para usar a negociação de Discagem se uma solicitação deve ser recebida de um servidor originador.
        
           **Falso**    O servidor XMPP não está configurado para usar negociação de Discagem e se uma solicitação deve ser recebida do servidor originador, será ignorada.

10. Clique em **Confirmar** para salvar suas mudanças para a política local ou do usuário.

## Atualizar registros DNS para Gateway XMPP do Lync Server 2013

1.  Para configurar DNS para federação XMPP, você adiciona o seguinte registro SRV para seu DNS externo:\_xmpp-server.\_tcp.\<nome de domínio\> O registro SRV resolverá o FQDN de Borda de Acesso do servidor de Borda, com um valor de porta de 5269.

