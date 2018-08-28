---
title: Usando o Analisador de Conectividade do Lync
TOCTitle: Usando o Analisador de Conectividade do Lync
ms:assetid: 954953fb-0c7a-4fd5-8acd-68ecb59b20af
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ907302(v=OCS.15)
ms:contentKeyID: 52057654
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Usando o Analisador de Conectividade do Lync

 

_**Tópico modificado em:** 2016-12-08_

O Analisador de Conectividade do Lync da Microsoft ajuda os administradores do Lync a determinar se a implantação e a configuração local do ambiente do Office 365 atendem aos requisitos para fornecer suporte às conexões do aplicativo Aplicativo Lync Windows Store dos aplicativos Lync em dispositivos móveis.

O Analisador de Conectividade do Lync tenta se conectar ao Lync Server local ou Skype for Business Online usando os mesmos serviços e protocolos utilizados pelos aplicativos móveis Aplicativo Lync Windows Store e Lync. Você pode executar os testes de conexão sobre a rede interna ou sobre uma rede externa que se conecta ao Lync Server ou o Analisador de Conectividade do Skype for Business Online. Lync fornece um relatório com informações detalhadas sobre cada etapa de conexão para ajudá-lo a validar sua configuração e resolver problemas de conexão.

O Analisador de Conectividade do Lync testa os seguintes componentes do Lync Server:

  - Serviço de Descoberta Automática

  - Serviço do Agente de Autenticação (Reach)

  - Serviço de Mobilidade (MCX)

  - Serviço de Mobilidade (UCWA)

  - Serviço do WebTicket

O Analisador de Conectividade do Lync testa a configuração dos seguintes componentes:

  - Publicação de registros DNS das URLs da Descoberta Automática

  - Certificados

  - Servidores proxy

Você pode fazer download do Analisador de Conectividade do Lync a partir do Centro de Download da Microsoft em <http://go.microsoft.com/fwlink/?linkid=277056>.

## Para analisar sua conectividade

1.  Insira as credenciais para uma conta do Lync válida (em uma conta local do Lync ou uma conta do Office 365Lync) que será usada pela ferramenta para testar a conexão:
    
      - Em **Tipo de conta do Lync**, selecione **Office 365** ou **Local**.
    
      - Em **URI do SIP**, insira o endereço de entrada do SIP para a conexão do Lync no formato **user&#64;domain.com**.
    
      - Em **Senha**, insira a senha associada a esta conta.
    
      - Em **Nome de usuário (opcional)**, insira um nome de usuário, se aplicável. O nome do usuário também é conhecido como UPN (nome principal do usuário). Se o nome do usuário e a URl do SIP forem os mesmos, não será necessário inserir um nome de usuário. Se eles não forem os mesmo, insira o nome de usuário no formato **user&#64;domain.com** ou **domínio\\usuário**, conforme apropriado.
    
      - Em **Acesso à rede**, escolha **Dentro da Minha Organização** se estiver executando o Analisador de Conectividade do Lync a partir de um computador conectado à sua rede interna. Caso contrário, escolha **Externa &#40;Internet&#41;**. O Analisador de Conectividade do Lync sempre executa testes internos e externos, mas especificar se você está dentro ou fora da sua própria rede ajuda a ferramenta a interpretar se determinadas falhas são esperadas.
    
      - Em **Cliente**, selecione se quer executar os testes de conectividade para o **Aplicativo Lync Windows Store**, **Aplicativo móvel do Lync 2010Aplicativos móveis 2013**.
    
      - Em **Descoberta do servidor**, selecione o tipo de teste a ser executado:
        
          - Se você quiser que a ferramenta descubra o Lync Server automaticamente, selecione **Automático**.
        
          - Se você quiser que a ferramenta ignore o teste de descoberta automática ou se você souber o nome do servidor ao qual deseja se conectar, selecione **Uso manual de endereço** e especifique o nome de domínio totalmente qualificado (FQDN) do servidor do Lync—por exemplo, **lync.company.com**.

2.  (Opcional) Em **Arquivo de Log**, selecione a caixa de seleção se quiser criar um arquivo de log no caminho especificado. Se o log estiver habilitado, clique em **Limpar** para limpar o arquivo de log, clique em **Abrir** para abrir e visualizar o arquivo de log, clique em **E-mail** para abrir uma mensagem de e-mail e enviar os resultados à sua equipe de suporte (você pode anexar manualmente o arquivo de log a partir do caminho especificado).

3.  Clique em **Iniciar**.

A figura a seguir exibe uma amostra dos resultados do Analisador de Conectividade do Lync.

**Analisador de Conectividade do Lync**

![Captura de tela do Analisador de Conectividade do Lync](images/JJ907302.a7cc0abe-fac2-4691-a7d8-9ffef59cdee5(OCS.15).png "Captura de tela do Analisador de Conectividade do Lync")

## Componentes testados pelo Analisador de Conectividade do Lync

O Analisador de Conectividade do Lync tenta descobrir o servidor Lync e estabelecer uma conexão usando as mesmas etapas usadas pelo Aplicativo Lync Windows Store e aplicativos móveis do Lync. Ele executa os testes conforme descrito nesta seção.

Se a **Descoberta Automática** estiver selecionada, o Analisador de Conectividade do Lync fará o seguinte:

  - Consultas do DNS (Serviço de Nomes de Domínio) para URLs da descoberta automática.

  - Tente descobrir usando o canal interno seguro. Por exemplo, **HTTPS://lyncdiscoverinternal.company.com/**.

  - Tente descobrir usando o canal interno inseguro. Por exemplo, **HTTP://lyncdiscoverinternal.company.com/**.

  - Tente descobrir usando o canal externo seguro. Por exemplo, **HTTPS://lyncdiscover.company.com**.

  - Tente descobrir usando o canal externo inseguro. Por exemplo, **HTTP://lyncdiscover.company.com**.

Se **Usar o seguinte endereço de descoberta do servidor** estiver selecionado, o Analisador de Conectividade do Lync faz o seguinte:

  - Consultas DNS para o FQDN do servidor.

  - Tente descobrir usando o canal seguro. Por exemplo, **HTTPS://serverFQDN/**.

  - Tente descobrir usando o canal interno inseguro. Por exemplo, **HTTP://serverFQDN/**.

Se o aplicativo **Lync Windows Store** estiver selecionado em **Testar requisitos para**, o Analisador de Conectividade do Lync faz o seguinte:

  - Verifique se o serviço do WebTicket está disponível e teste a autenticação das credenciais da conta do Lync.

  - Verifique se o serviço de Agente de Autenticação (Reach) está disponível.

Se o **Aplicativo móvel do Lync 2010** estiver selecionado em **Cliente**, o Analisador da conectividade do Lync faz o seguinte:

  - Verifique se o serviço do WebTicket está disponível e teste a autenticação das credenciais da conta do Lync.

  - Verifique se o servido de Mobilidade (MCX) está disponível.

Se o **Aplicativo móvel do Lync 2013** estiver selecionado em **Cliente**, o Analisador de Conectividade do Lync fará o seguinte:

  - Verifica se o serviço WebTicket está disponível e testa a autenticação das credenciais de conta do Lync.

  - Verifica se o serviço Serviço de Mobilidade (UCWA) está disponível.

Enquanto estiver executando esses testes, o Analisador de Conectividade do Lync valida os certificados instalados no Lync Server, balanceadores de carga de hardware, servidores proxy e o computador no qual você estiver executando os testes.

## Outros Recursos

A Microsoft também fornece o Analisador de Conectividade Remoto da Microsoft, uma ferramenta de teste de conectividade com base na Web, que está disponível em <https://testconnectivity.microsoft.com/>. Lync O Analisador de Conectividade e o Analisador de Conectividade Remoto diferem das seguintes maneiras:

  - O Analisador de Conectividade Remoto pode testar a conectividade do Microsoft Exchange e do Outlook, além do Lync da Microsoft.

  - O Analisador de Conectividade Remoto completa a entrada do SIP, enquanto o Analisador de Conectividade do Lync somente valida as credenciais da conta, sem entrar.

  - O Analisador de Conectividade Remoto testa as conexões somente fora da rede da sua organização, pois ele é executado a partir de um servidor Web público.

  - O Analisador de Conectividade Remoto não testa a disponibilidade dos serviços de Agente de Autenticação (Reach), de Mobilidade (MCX) e do WebTicket.

  - O Analisador de Conectividade do Lync testa o serviço de Descoberta Automática.

  - O Analisador de Conectividade Remoto pode se conectar a qualquer versão do Lync Server, enquanto o Analisador de Conectividade do Lync pode se conectar com sucesso somente ao Lync Server 2010 com atualizações cumulativas do Lync Server 2010: fevereiro de 2012 (no mínimo) ou a versão mais recente do Lync Server.

A documentação a seguir descreve os requisitos e procedomentos para a implantação e configuração do Lync Server para oferecer suporte ao Aplicativo Lync Windows Store e aos clientes móveis do Lync:

  - [Implantando clientes e dispositivos no Lync Server 2013](lync-server-2013-deploying-clients-and-devices.md)

  - [Planejamento para mobilidade no Lync Server 2013](lync-server-2013-planning-for-mobility.md)

  - [Implantando mobilidade no Lync Server 2013](lync-server-2013-deploying-mobility.md)

