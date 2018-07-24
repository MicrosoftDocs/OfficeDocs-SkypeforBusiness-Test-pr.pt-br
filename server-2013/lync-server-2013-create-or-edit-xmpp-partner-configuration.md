---
title: 'Lync Server 2013: Criar ou editar configuração do parceiro XMPP'
TOCTitle: Criar ou editar configuração do parceiro XMPP
ms:assetid: 362dbe5e-8ee9-4aba-8c26-5907312b4a60
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ552447(v=OCS.15)
ms:contentKeyID: 49306359
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Criar ou editar configuração do parceiro XMPP no Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

O Microsoft Lync Server 2013 integra um proxy XMPP (Extensible Messaging and Presence Protocol) ao Servidor de Borda e um gateway XMPP ao Servidor Front-End ou ao Pool de Front-Ends. Para permitir conexões de outras implantações XMPP, é preciso configurar o XMPP no Painel de Controle do Lync Server. Defina as configuração com base no domínio XMPP. Para criar uma nova associação de parceiro, faça o seguinte:

## Para criar um novo parceiro federado ou editar uma configuração existente

1.  Usando uma conta de usuário que é membro do grupo RTCUniversalServerAdmins (ou tem direitos de usuário equivalentes), ou está atribuída à função CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerda, clique em **Federação e Acesso Externo** e, então, clique em **Parceiros XMPP Federados**.

4.  Para criar uma configuração, clique em **Novo**

5.  Para editar uma configuração existente, selecione-a e clique em **Editar**

6.  Para criar ou editar configurações de **Parceiros XMPP Federados**, defina as seguintes configurações:

7.  **Domínio primário** (Obrigatório). O domínio primário é o domínio base do parceiro XMPP. Por exemplo, você deve inserir **fabrikam.com** como nome de domínio do parceiro XMPP. Esta é uma entrada necessária.

8.  **Descrição**. A descrição destina-se a notas ou outras informações de identificação desta configuração. Esta entrada é opcional.

9.  **Domínios adicionais**. Os domínios adicionais são domínios que fazem parte do domínio do parceiro XMPP e que devem ser incluídos como parte da comunicação permitida do XMPP. Por exemplo, se o domínio primário for **fabrikam.com**, você precisará listar todos os domínios que estão em fabrikam.com e com os quais haverá comunicação por meio do XMPP. Por exemplo, é possível inserir **corp.fabrikam.com** e **it.fabrikam.com** para o domínio XMPP Corporativo e para o domínio XMPP de TI no domínio XMPP principal de fabrikam.com.

10. **Tipo de parceiro**. O **Tipo de parceiro** é uma configuração necessária que oferece três opções em um menu suspenso. Você deve escolher umas das seguintes opções para descrever e impor os contatos que podem ser adicionados. As opções são:
    
      - **Federado**. Um tipo de parceiro **Federado** é uma conexão confiável entre a implantação do parceiro Lync Server ou Office Communications Server 2007 R2.
    
      - **Público verificado**. Um parceiro **Público verificado** significa que há contatos que fazem parte de uma implantação, que foram verificados pelo provedor e que podem ser adicionados à lista de contatos do seu usuário. O usuário do Lync pode enviar convites ou o usuário do Lync pode aceitar convites do contato do parceiro.
    
      - **Público não verificado**. Uma relação **Público não verificado** envolve a ausência de um status estabelecido e verificável entre as duas implantações. Um usuário do Lync deve convidar o contato não verificado para que este possa adicionar o usuário do Lync à sua lista de contatos. Por exemplo, o Google GTalk não é um serviço XMPP público verificado, pois ele está relacionado ao Lync Server. Um usuário do GTalk não poderá adicionar o usuário do Lync como contato, a menos que haja um convite explícito enviado pelo usuário do Lync.

11. Observações sobre a negociação de fluxo e os métodos de segurança de TLS (protocolo TLS) e SASL (Software Authentication and Security Layer)
    
    O XSF ( **XMPP Standards Foundation**) e o IETF ( **Internet Engineering Task Force**) definem um conjunto de regras e padrões de uso e gerenciamento de certificados de cliente TLS, certificados de servidor TLS e o mecanismo SASL. O uso de TLS e SASL é o processo exigido para proteger o fluxo XMPP. Segundo o documento Padrões de XMPP **XEP-0178**, “especifica um fluxo de protocolo recomendado para uso do mecanismo EXTERNO SASL com certificados PKIX, especialmente quando um serviço XMPP indicar que o protocolo TLS é obrigatório para a negociação". PKIX, como declarado na documentação do XSF, refere-se à infraestrutura da chave pública, também conhecida como PKI.
    
    Consulte o documento do XSF XEP-0178 para obter mais detalhes sobre os requisitos de XMPP. Para obter detalhes, consulte “XEP-0178: Best Practices for Use of SASL EXTERNAL with Certificates”. <http://xmpp.org/extensions/xep-0178.html>
    
    Consulte o documento do IETF “Extensible Messaging and Presence Protocol (XMPP): Core“, seção 5.0, STARTTLS Negotiation <http://tools.ietf.org/html/rfc6120>.
    
      - **Negociação TLS**. Define as regras de negociação TLS. Um serviço XMPP pode exigir TLS, pode tornar o TLS opcional ou estabelecer que não há suporte para o TLS. A escolha da configuração Opcional deixa o requisito a cargo do serviço XMPP para uma decisão de obrigatória para negociação. Para exibir todas as configurações possíveis e detalhes sobre as negociações SASL, TLS e Retorno de Discagem, incluindo configurações de erros conhecidos e não válidos, consulte [Configurações de negociação para parceiros de XMPP federados no Lync Server 2013](lync-server-2013-negotiation-settings-for-xmpp-federated-partners.md).
        
           **Obrigatório**. O serviço XMPP exige negociação TLS.
        
           **Opcional**. O serviço XMPP indica que o TLS é obrigatório para negociação.
        
           **Sem Suporte**. O serviço XMPP não oferece suporte a TLS.
    
      - **Negociação SASL**. Define as regras de negociação SASL. Um serviço XMPP pode exigir SASL, pode tornar o SASL opcional ou estabelecer que não haja suporte para o SASL. A escolha da configuração Opcional deixa o requisito a cargo do serviço XMPP do parceiro para uma decisão de obrigatório para negociação.
        

        > [!WARNING]
        > SASL exige o protocolo TLS. Para usar SASL, o protocolo TLS deve ser obrigatório ou opcional. Qualquer configuração que defina SASL como obrigatório ou opcional deve ter suporte ao protocolo TLS. Quando clicar em <STRONG>Confirmar</STRONG> para salvar suas alterações, se ainda não tiver definido o protocolo TLS como obrigatório ou opcional, você será avisado de que SASL deve ter suporte ao protocolo TLS e as alterações não serão salvas. Para solucionar o erro, defina o protocolo TLS como <STRONG>Obrigatório</STRONG> ou <STRONG>Opcional</STRONG>. Se o uso de SASL for opcional e o suporte à negociação do protocolo TLS não for possível, será preciso definir a negociação SASL como <STRONG>Não suportado</STRONG>. Confirme no serviço XMPP como devem ser os fluxos de negociação apropriados SASL ou do protocolo TLS ou ocorrerá uma interrupção do serviço.

        
           **Obrigatório**. O serviço XMPP requer negociação SASL.
        
           **Opcional**. O serviço XMPP indica que o SASL é obrigatório para negociação.
        
           **Sem Suporte**. O serviço XMPP não oferece suporte a SASL.
    
      - **Negociação Retorno de Discagem**. A negociação Retorno de Discagem é definida pelo XSF no documento **XEP-220: Server Dialback**<http://xmpp.org/extensions/xep-0220.html>. O processo de retorno de discagem do servidor usa o DNS (Sistema de Nomes de Domínio) e um servidor autoritativo para verificar se a solicitação veio de um parceiro XMPP válido. Para isso, o servidor de origem cria uma mensagem de um tipo específico com uma chave de retorno de discagem gerada e pesquisa o servidor de recebimento no DNS. O servidor de origem envia a chave em um fluxo XML para a pesquisa DNS resultante, presumivelmente o servidor de recebimento. Ao receber a chave pelo fluxo XML, o servidor de recebimento não responde ao servidor de origem, mas envia a chave a um servidor autoritativo conhecido. O servidor autoritativo verifica se a chave é válida ou inválida. Se for inválida, o servidor de recebimento não responderá ao servidor de origem. Se for válida, o servidor de recebimento informará ao servidor de origem que a identidade e a chave são válidas e a conversa poderá começar.
        
        Existem dois estados válidos para **Negociação de discagem**:
        
           **True**. O servidor XMPP está configurado para usar a negociação Retorno de Discagem se uma solicitação for recebida de um servidor de origem.
        
           **False**. O servidor XMPP não está configurado para usar a negociação Retorno de Discagem; se uma solicitação for recebida de um servidor de origem, ela será ignorada.

