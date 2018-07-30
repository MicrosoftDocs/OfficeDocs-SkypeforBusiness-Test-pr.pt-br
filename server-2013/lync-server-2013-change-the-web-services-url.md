---
title: Alterar a URL do Web Services no Lync Server 2013
TOCTitle: Alterar a URL do Web Services no Lync Server 2013
ms:assetid: 4cee37c0-3b99-4207-997f-bf4229d760c0
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg520992(v=OCS.15)
ms:contentKeyID: 49306653
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Alterar a URL do Web Services no Lync Server 2013

 

_**Tópico modificado em:** 2015-11-16_

Ao configurar os pools de Front-Ends e os servidores Standard Edition, você tem a opção de configurar um FQDN (nome de domínio totalmente qualificado) de Web farm externo e as portas associadas. Se não tiver configurado essa URL ao executar o Assistente de Implantação do Lync Server, você precisará definir manualmente as configurações. Um administrador normalmente não precisa alterar essas configurações, pois essas são as portas recomendadas e padrão.

> [!NOTE]  
> A captura de tela a seguir foi obtida durante a configuração de um servidor Standard Edition, portanto, a opção Substituir FQDN está desabilitada. Essa opção é habilitada durante a configuração de um servidor Enterprise Edition em um pool de Front-Ends.

![Editar configurações do pool de serviços da Web](images/Gg520992.fbdf5cc9-479a-463f-bb1d-53575ecdfc9d(OCS.15).jpg "Editar configurações do pool de serviços da Web")

## Para configurar serviços Web

1.  Faça logon no computador no qual o Construtor de Topologias está instalado como um membro do grupo Admins. do Domínio ou do grupo RTCUniversalServerAdmins.

2.  Inicie o Construtor de Topologias: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Construtor de Topologias do Lync Server**.

3.  No Construtor de Topologias, na árvore de console em **Servidor Front-End Standard Edition**, **Pools de Front-Ends Enterprise Edition** e **Pools de Diretores**, selecione o nome do pool. Clique com o botão direito do mouse no nome, clique em **Editar Propriedades** e em **Serviços Web**.

4.  Adicione ou edite o **FQDN de Serviços Web Externos** e clique em **OK**.
    

    > [!WARNING]
    > Se você possui mais de um Pool de Front-Ends ou Servidor Front-End, o FQDN dos serviços Web externo devem ser únicos. Por exemplo, se você define o FQDN dos serviços web externos de um Servidor Front-End como <STRONG>pool01.contoso.com</STRONG>, você não pode usar <STRONG>pool01.contoso.com</STRONG> para outro Pool de Front-Ends ou Servidor Front-End. Se você estiver implantando também Diretores, o FQDN dos serviços web externos definido para qualquer Diretor ou Pool de diretores deve ser único se comparado a outro Diretor ou Pool de diretores, assim como qualquer Pool de Front-Ends ou Servidor Front-End.



5.  Verifique se as portas de escuta e publicadas estão configuradas corretamente para seu ambiente.

6.  Repita estas etapas para todos os servidores Standard Edition, Pools de Front-Ends e pools de Diretores em seu ambiente.

7.  Na árvore de console, clique em **Lync Server 2013** e, no painel **Ações** clique em **Publicar Topologia**.

Existem alguns requisitos que você deve estar ciente ao configurar as portas de Escuta e Publicação:

  - As portas de escuta mostradas são as portas configuradas para o IIS (Internet Information Server) em cada Servidor Front-End.

  - As portas de escuta internas e externas devem ser diferentes para o IIS. Para as portas de escuta externas, geralmente são iguais porque uma representa o balanceador de carga de hardware para tráfego da Web interno e a outra representa o servidor proxy inverso para tráfego da Web externo.

  - Você pode substituir os serviços web internos em um Pool de Front-Ends, um Diretor ou um Pool de diretores e definir seu próprio FQDN.
    

    > [!WARNING]
    > Se você decidir substituir os serviços web internos com um FQDN definido automaticamente, cada FQDN deve ser único se comparado a outro Pool de Front-Ends, Diretor ou um Pool de diretores.



  - As portas publicadas devem ser configuradas no balanceador de carga de hardware ou de proxy reverso como portas de escuta.

  - Para um pool de Front-End (não mostrado no exemplo), o FQDN do pool SIP interno deve ser diferente do FQDN de serviços Web internos, pois o tráfego da Web passa pelo balanceador de carga de hardware e o tráfego de pool SIP interno passa pelo balanceador de carga de DNS. Este requisito deve ser atendido.

  - Uma implantação do Lync Server Standard Edition não precisa ou permite que um FQDN de serviços Web internos seja substituído, pois não pode ser feito balanceamento de carga desse servidor.

  - Se você tiver um balanceador de carga de hardware no seu ambiente que você usa para SIP interno e tráfego da Web, o Construtor de Topologias não pode fazer distinção.
    
    Os FQDNs de serviço Web devem ser diferenciados facilmente um do outro; isso ajuda a assegurar que o redirecionamento de URL indique o servidor apropriado aos clientes. Por exemplo, se houver dois FQDNs, talvez você queira considerar nomear um como meeting.contoso.com e o outro como conferencing.contoso.com. Você poderia enfrentar problemas de redirecionamento se tivesse FQDNs com nomes semelhantes, como meet1.contoso.com e meet2.contoso.com.

Os serviços Web externos funcionam em conjunto com um proxy reverso na rede de perímetro. Ele fornece aos clientes acesso externo ao usando esses serviços Web. Os FQDNs configurados aqui são enviados aos clientes quando eles fazem logon e são usados para estabelecer uma conexão HTTPS com o proxy reverso ao conectar remotamente. O servidor proxy reverso encaminha o FQDN do serviço Web externo para um balanceador de carga de hardware interno ou diretamente para o pool. O proxy reverso deve ser capaz de resolver o FQDN de serviços Web externos para o endereço IP do servidor Web interno. O FQDN de serviços Web externos deve ser resolvido na Internet pública.

Se o seu servidor interno for um Servidor Standard Edition, o FQDN interno será o FQDN do Servidor Standard Edition. Se seu servidor interno for um pool de Front-End, o FQDN será um VIP (IP virtual) do balanceador de carga de hardware que faz o balanceamento de carga dos servidores de Web farm IP virtual (VIP) que o equilíbrio de carga de servidores de web farm internos. É necessário um balanceador de carga de hardware em um pool de Front-End com mais de um servidor Enterprise Edition. Um balanceador de carga não é necessário para um servidor Standard Edition ou um único Servidor Front-End Enterprise Edition.

