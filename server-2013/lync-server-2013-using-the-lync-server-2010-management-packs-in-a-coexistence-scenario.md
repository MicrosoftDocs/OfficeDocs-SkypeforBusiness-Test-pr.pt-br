---
title: "Usando os pacotes de gerenc. do Lync Server 2010 em um cenário de coexistência"
TOCTitle: "Usando os pacotes de gerenc. do Lync Server 2010 em um cenário de coexistência"
ms:assetid: 8b792503-bd88-47fe-9d97-b071e8d429a5
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205078(v=OCS.15)
ms:contentKeyID: 49307406
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Usando os pacotes de gerenciamento do Lync Server 2010 em um cenário de coexistência

 

_**Tópico modificado em:** 2012-10-22_

Muitos clientes adotam um programa de distribuição dentro de suas empresas na qual os usuários são migrados progressivamente do Microsoft Lync Server 2010 para Lync Server 2013. Os administradores nessas empresas precisam monitorar ambas as versões do Lync Server para ajudar a garantir que todos os seus usuários finais estejam obtendo a melhor experiência de comunicação possível. Para este cenário, o Pacote de Gerenciamento do Lync Server 2013 suporta um caminho de migração lado a lado com o Pacote de Gerenciamento do Lync Server 2010.

No Lync Server 2010, os computadores do Lync Server eram descobertos através do documento de topologia armazenado no armazenamento o Gerenciamento Central. Nessa configuração, um único computador reportaria a existência de todos os outros computadores do Lync Server.

Os pacotes de gerenciamento do Lync Server 2013 são agora mecanismos de descoberta no nível da máquina, em vez da descoberta central que era usada no Lync Server 2010. Isso significa que cada agente do System Center, descobre essencialmente a si mesmo e relata sua existência ao System Center Operations Manager. Usar a descoberta no nível da máquina simplifica a administração da sua infraestrutura do System Center e também permite que diferentes versões dos pacotes de gerenciamento do Lync Server (por exemplo, pacotes de gerenciamento do Lync Server 2010 e pacotes de gerenciamento do Lync Server 2013) coexistam mais facilmente.

Para suportar essa migração, você precisará primeiramente atualizar o monitoramento do Lync Server 2010 existente para evitar lacunas na cobertura. Para isso, escolha um computador do Lync Server 2010 existente para servir o script de Descoberta Central do Lync Server 2010 antes de atualizar seu armazenamento do Gerenciamento Central para o Lync Server 2013. Este é um processo em quatro etapas:

1.  Atualize os Pacotes de Gerenciamento do Lync Server 2010 para a atualização cumulativa 7.

2.  Instrua um computador do Lync Server 2010 para executar o script de Descoberta Central

3.  Substitua o Candidato a Descoberta Central no Pacote de Gerenciamento do Microsoft Lync Server 2010.

4.  Verifique se o novo Candidato a Descoberta Central foi descoberto.

## Instrua um computador com Lync Server 2010 para executar o script de Descoberta Central

Para nomear um computador de armazenamento que não seja do servidor de Gerenciamento Central (por exemplo, um front end do Lync Server) para lidar com a descoberta central, é necessário criar a seguinte chave de registro no servidor de armazenamento que não é do Gerenciamento Central.

HKLM\\Software\\Microsoft\\Real-Time Communications\\Health\\CentralDiscoveryCandidate

Você pode instalar criar essa chave de registro concluindo o seguinte procedimento:

1.  Clique em **Iniciar** e depois em **Executar**.

2.  Na caixa de diálogo **Executar**, digite **regedit** e depois pressione ENTER.

3.  No Editor do Registro, expanda **HKEY\_LOCAL\_MACHINE**, expanda **SOFTWARE**, expanda **Microsoft**, e depois expanda **Comunicação em tempo real**.

4.  Com o botão direito em **Integridade**, clique em **Novo**, e depois em **Chave**. Se a chave **Integridade** não existir, clique com o botão direito em **Comunicações em tempo real**, aponte para **Novo**, e depois clique em **Chave**. Quando a nova chave for criada, digite Integridade, e depois pressione ENTER.
    
    Depois que a nova chave for criada, digite **CentralDiscoveryCandidate** e pressione ENTER para renomear a chave.

Pode levar algumas horas para que o computador obtenha essa alteração. Para atualizar essas configurações imediatamente, pare e em seguida reinicie o serviço Agente de Integridade. Para reiniciar o serviço Agente de Integridade, siga o procedimento a seguir no computador do Lync Server 2010:

1.  Clique em **Iniciar**, **Todos os Programas**, **Acessórios**, clique o botão direito no **Prompt de comando**, e depois clique em **Executar como administrador**.

2.  Na janela do console, digite o seguinte comando e pressione ENTER.
    
        Net stop HealthService

3.  Você verá uma mensagem que diz "O serviço de Gerenciamento do Gerenciamento do System Center está sendo interrompido", seguida por uma segunda mensagem que diz que o serviço foi interrompido. Após a interrupção do serviço, você pode reiniciá-lo digitando o seguinte comando e pressionando ENTER:
    
        Net start HealthService

## Substituição do Candidato a Descoberta Central no Pacote de Gerenciamento do Lync Server 2010

Após instruir o computador do Lync Server 2010 para relatar em computadores do Lync Server 2010, será necessário informar o Pacote de Gerenciamento do Lync Server 2010 também sobre essa mudança. Para fazer isso, será necessário criar uma substituição no Pacote de Gerenciamento. Isso pode ser feito realizando o procedimento a seguir:

1.  No console do Operations Manager, clique em **Criação**.

2.  Na guia Criação, expanda **Objetos do Pacote de Gerenciamento**, clique em **Descobertas de Objeto**, e depois em **Escopo**.

3.  Na caixa de diálogo **Delimitar Objetos do Pacote de Gerenciamento**, selecione o item com o **Candidato à descoberta LS** do alvo e depois clique em **OK**. Observe que o Candidato à descoberta LS será exibido apenas se você tiver instalado o Pacote de Gerenciamento do Lync Server 2010.

4.  No console do Operations Manager, clique com o botão direito em **Candidato à descoberta LS**, aponte para **Substituições**, aponte para **Substituir a Descoberta de Objeto**, e clique em **Para todos os objetos da classe: Candidato à descoberta LS**.

5.  Na caixa de diálogo **Substituir propriedades**, marque a caixa de seleção **Substituir** ao lado do parâmetro **WatcherNode Fqdn da Descoberta Central**. Digite o nome de domínio totalmente qualificado do computador do Lync Server 2010 nas caixas **Valor de substituição** e **Valor efetivo**. Marque a caixa de seleção **Imposto** e clique em **OK**.

Após criar a substituição, será necessário reiniciar o serviço de integridade no Servidor de Gerenciamento Raiz. Para reiniciar o serviço Agente de Integridade, siga o procedimento a seguir no Servidor de Gerenciamento Raiz:

1.  Clique em **Iniciar**, **Todos os Programas**, **Acessórios**, clique o botão direito no **Prompt de comando**, e depois clique em **Executar como administrador**.

2.  Na janela do console, digite o seguinte comando e pressione ENTER:
    
        Net stop HealthService

3.  Você verá uma mensagem que diz "O serviço de Gerenciamento do Gerenciamento do System Center está sendo interrompido", seguida por uma segunda mensagem que diz que o serviço foi interrompido. Após a interrupção do serviço, você poderá reiniciá-lo digitando o seguinte comando e pressionando ENTER:
    
        Net start HealthService

## Verificação se o novo Candidato a Descoberta Central foi descoberto.

A etapa final, antes de atualizar o armazenamento do Gerenciamento Central, é ter certeza de que o novo candidato à descoberta central foi descoberto pelo Pacote de Gerenciamento do Lync Server 2010. Para isso, abra o console do Operations Manager e clique em Monitoramento. Na guia Monitoramento, expanda **Integridade do Microsoft Lync Server 2010**, expanda **Descoberta de topologia** e depois clique em **Exibição do estado de descoberta**. Verifique se uma linha na exibição tem o **Caminho** que lista o nome de domínio totalmente qualificado do candidato à descoberta central. Você também deve verificar se o estado do computador é relatado como **Íntegro**.

