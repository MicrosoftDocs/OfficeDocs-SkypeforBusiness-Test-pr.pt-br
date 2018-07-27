---
title: 'Lync Server 2013: Perguntas Frequentes: Configurando Lync Server para conectividade com Skype'
TOCTitle: 'Perguntas Frequentes: Configurando Lync Server para conectividade com Skype'
ms:assetid: 4d1b2bfc-780b-4b8c-afd5-11c2e59203b5
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn440172(v=OCS.15)
ms:contentKeyID: 59602792
ms.date: 12/29/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Perguntas Frequentes: Configurando Lync Server 2013 para conectividade com Skype

 

_**Tópico modificado em:** 2016-12-27_

**P: Que recursos têm suporte entre o Microsoft Lync e o Skype?**

**R:** Com o Skype, agora parte da família da Microsoft, novas possibilidades se abrem para a extensão de cenários de comunicações unificadas para centenas de milhões de pessoas que usam o Skype. Essa combinação permitirá que os clientes do Lync se conectem e colaborem com fornecedores, clientes e parceiros, apoiados na riqueza do Lync e no alcance do Skype.

  - Mensagem instantânea e Chamadas de áudio e de vídeo - Mensagens instantâneas e chamadas de áudio e de vídeo federadas entre usuários do Lync e do Skype

  - Compartilhamento de presença - informações de presença do Exchange entre contatos federados

  - Administração simples - configurações e controles para configurar comunicações federadas de acordo com suas políticas e padrões da organização

**P: Como posso me qualificar para a conexão da minha implantação do Lync com o Skype?**

**R:** Você estará licenciado para a conectividade do Skype se tiver:

  - Lync Server (2010 ou 2013) mais Licenças de Acesso para Cliente ("CALs"; 2010 ou 2013) Padrão do Lync Server para os usuários e/ou dispositivos em sua organização que se conectará ao Skype. 

  - Lync Online (como licenças autônomas ou como parte de um pacote do Office 365).  Entretanto, este serviço (pic.lync.com) destina-se somente para o provisionamento de implantações do Lync Server e do Lync Server híbrido e do Lync Online.  O provisionamento do PIC do Lync Online é feito no Painel de Controle do Lync Online (LOCP).

**P: O que os usuários finais do Lync deverão fazer para se conectar a contatos do Skype?**

**R:** Depois que um domínio tiver sido ativado e recursos tiverem sido habilitados pelo administrador de uma organização do Lync, os usuários do Lync podem adicionar contatos do Skype às suas listas de contatos no cliente do Lync.

**P: O que os usuários finais do Skype fazem para se conectar a contatos do Lync?**

**R:** Todos os usuários do Skype que esperam se conectar a um usuário do Lync deverão ter uma Conta da Microsoft associada a suas IDs do Skype e entrar usando a Conta da Microsoft.  Isso pode ser habilitado no cliente do Skype.

**P: A federação do Windows Live ainda disponível?**

**R:** A partir de outubro de 2012, a Microsoft começou a ajudar os usuários do Windows Live Messenger (WLM) a mudarem para o Skype, a caminho de eventualmente desativar o WLM. O Lync continuará a dar suporte à federação com o WLM até quando o WLM estiver no mercado, mas nenhuma ativação de domínio adicional do Windows Live será permitida. A movimentação de usuários do WLM é habilitada pelo Skype 6.0 para Mac e Windows (lançado em 25 de outubro de 2012) que permite a entrada com uma Conta da Microsoft (isto é, as mesmas credenciais do WLM). Depois de simplesmente entrar no Skype, as listas de amigos do WLM são automaticamente preenchidas no Skype e os usuários podem aproveitar as vantagens dos recursos de comunicação expandidos do Skype, como chamar telefones fixos e móveis, compartilhamento de tela, chamada de vídeo em grupo e suporte para uma ampla variedade de dispositivos. Além disso, os contatos do Lync federados dos usuários do WLM seguem a transição para o Skype com o restante da lista de amigos, e o IM entre o Skype e o Lync para esses contatos estarão disponíveis imediatamente. Os clientes do Lync não precisam fazer nada para habilitar essa continuidade de serviço.

**P: A federação com o Yahoo\! ou a AOL ainda está disponível?**

**R:** A federação do Yahoo\! e da AOL estão em um caminho em direção ao final da vida útil para clientes do Lync e do Office Communications Server. A capacidade da Microsoft de fornecer cada um desses serviços tem sido contingente no suporte do Yahoo\! e da AOL, e os contratos subjacentes deles estão terminando. Para o Yahoo\! e a AOL, o serviço continuará até junho de 2014.

  - Yahoo\!: o serviço continuará até junho de 2014 e os clientes continuarão precisando da Licença de Assinatura de Usuário de Conectividade de IM Pública do Microsoft Lync ("PIC USL"). Desde 1º de setembro de 2012, a PIC USL, está indisponível para compra ou renovação. Os clientes com licenças compradas antes desta data poderão continuar a federar o Yahoo\! até a data de término do serviço ou encerramento da licença. Os clientes que possuem Licença PIC em contratos que se ultrapassam 30 de junho de 2014 receberão um crédito à proporção do valor dos pagamentos do período de tempo após 30 de junho de 2014

  - AOL: A partir de 30 de junho de 2014, o serviço de Conectividade de IM Pública do Microsoft Lync ("PIC") não estará mais disponível. A fim de evitar a perturbação de clientes quando o serviço terminar, interrompemos o fornecimento de domínios adicionais aos clientes. Até 30 de junho de 2014, os clientes não precisarão fazer nada para continuar a suportar comunicações federadas com a AIM. Depois desta data (ou para clientes que gostariam de obter domínios adicionais durante esse período), um serviço alternativo estará disponível diretamente a partir da AOL. Para obter informações sobre o novo serviço da AOL, consulte <http://aimenterprise.aol.com/pic.php> (opens new page on AOL.com). 

**P: Posso experimentar a conectividade do Skype antes de comprar o Lync?**

**R:** A conectividade do Skype não é oferecida como avaliação. No lugar de uma avaliação, os clientes do Lync com licenças qualificadas são incentivados a simplesmente assinarem o serviço a ser testado.

**P: Quais informações são necessárias para o provisionamento?**

**R:** Para enviar uma solicitação de provisionamento sob uma licença qualificada, você precisa do seguinte:

  - Número do contrato da Microsoft
    
      - Suporte do Microsoft Volume Licensing: número do Microsoft Volume Licensing Agreement
    
      - Microsoft Partner Network: ID do parceiro da sede
    
      - Service Provider Licensing Agreement: número de registro inicial
    
      - High Volume Services: numero de registro do produto

  - Nomes de domínio totalmente qualificados (FQDNs) para o serviço de Borda de Acesso.
    
      - É necessário um FQDN para pelo menos um serviço de Borda de Acesso.
    
      - Se sua organização tem mais de um servidor com o serviço de Borda de Acesso, especifique os FQDNs de cada serviço de Borda de Acesso adicional. Importante: se você especificou previamente um FQDN para o serviço de Borda de Acesso e quer alterá-lo, a configuração da alteração pode levar vários dias para ser concluída e pode resultar em interrupção do serviço. Para evitar interrupção de serviço, recomendamos que você mantenha o FQDN especificado anteriormente para o serviço de Borda de Acesso.

  - Domínios SIP. É o sufixo de domínio do URL SIP que os usuários usam atualmente para mensagens instantâneas. Se a sua organização tiver mais de um domínio SIP, especifique o sufixo de cada domínio para mensagens instantâneas. Por exemplo, para usuario1@contoso.com, especifique contoso.com como o domínio SIP; para usuário1@example.fabrikam.com, especifique example.fabrikam.com como o domínio SIP.
    
    > [!NOTE]  
    > Especifique somente o sufixo de domínio para o domínio SIP. Não especifique qualquer FQDN, incluindo o FQDN do serviço de Borda de Acesso, para o domínio SIP.

  - Informações de contato. Especifique um endereço de email para o administrador de cada domínio SIP especificado por você.

**P: Como eu habilito a Conectividade Lync-Skype Connectivity em um cenário de domínio dividido?**

**R:**Se você tiver um cenário de domínio dividido local do Lync Online 2013 e do Lync Server (com usuários online e locais usando o mesmo domínio SIP), habilite a Conectividade Lync-Skype executando uma destas duas etapas na ordem a seguir

1.  Configure a Conectividade Lync-Skype local como explicado no Guia de provisionamento do PIC.

2.  Aguarde até ver a confirmação de que seu domínio tenha sido provisionado pela Microsoft.

3.  Depois de ver a confirmação, use o Centro de administração do Lync para ativar as "comunicações externas". Para obter mais informações, consulte [http://office.microsoft.com/pt-br/support/configure-external-communications-HA102817865.aspx?CTT=5\&origin=HA102817356](http://office.microsoft.com/pt-br/support/configure-external-communications-ha102817865.aspx?ctt=5%26origin=ha102817356)

Esta ordem é importante. Você deve configurar a conectividade local antes de habilitar as comunicações no Lync Online. Se a ordem for invertida, as informações inseridas para <https://pic.lync.com> local não passarão. Se você já tiver configurado o Lync Online para comunicações com seu domínio, será necessário desativá-lo, aguarde 24 horas e comece novamente, primeiro inserindo suas informações locais em <https://pic.lync.com> e então ativando comunicações externas para o Lync Online.

**P: Posso provisionar vários FQDNs do serviço de Borda de Acesso para conectividade do Skype?**

**R:** Você pode provisionar até dez FQDNs do serviço de Borda de Acesso com cada solicitação de provisionamento.

**P: Posso obter a lista de endereços de email da Conta da Microsoft encontrados para a organização que está solicitando o provisionamento?**

**R:** Não. Esses endereços são considerados informação pessoalmente identificável e não são compartilhados.

**P: Como adiciono um contato do Windows Live Messenger com uma ID com um domínio diferente dos domínios com suporte do Windows Live?**

**R:** Se você estiver adicionando um usuário do Windows Live Messenger com uma conta ou ID de um domínio diferente do Windows Live, insira o endereço no seguinte formato: \<nome de usuário\>(\<nome de domínio\>)@msn.com, onde \<nome de domínio\> é o nome de domínio no endereço de email do usuário. Por exemplo, se você quisesse adicionar joao@contoso.com, usaria o seguinte formato: joao(contoso.com)@msn.com. Para obter uma lista de domínios administrados pelo Windows Live, consulte a seção Domínios com suporte em "Problemas conhecidos que ocorrem com mensagens instantâneas públicas e do Lync Server ou servidor de comunicações" em http://support.microsoft.com/?kbid=897567.

**P: Quanto tempo demora o processo de provisionamento?**

**R:** O provisionamento pode levar até 30 dias.

**P: Como saberei quando o provisionamento foi concluído?**

**R:** A Microsoft enviará uma notificação por email quando o provisionamento estiver concluído.

**P: Como posso atualizar a configuração ou os detalhes de contato que enviei?**

**R:** Você pode atualizar suas informações no mesmo site usado para solicitar o provisionamento, depois que o provisionamento estiver concluído. Insira o número do seu contrato e então clique em Atualizar serviço.

