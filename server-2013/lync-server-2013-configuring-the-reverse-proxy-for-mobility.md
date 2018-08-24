---
title: 'Lync Server 2013: Configurando o proxy reverso para mobilidade'
TOCTitle: Configurando o proxy reverso para mobilidade
ms:assetid: 3f4a9e33-77e4-4c18-a73f-24d4bec8ea9c
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Hh690011(v=OCS.15)
ms:contentKeyID: 49306498
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurando o proxy reverso para mobilidade no Lync Server 2013

 

_**Tópico modificado em:** 2014-03-20_

Se você quiser usar a descoberta automática para clientes do dispositivo móvel, precisará modificar ou criar uma nova regra de publicação na Web para o proxy reverso quer você atualize ou não as listas de nome alternativo de assunto nos certificados de proxy reverso.

Se decidir usar HTTPS para solicitações iniciais do Serviço Descoberta Automática do Lync Server 2013 e atualizar listas de nomes alternativos de assunto nos certificados de proxy reverso, você precisará atribuir o certificado público atualizado ao Ouvinte do SSL em seu proxy reverso. Para obter detalhes sobre as entradas de nome alternativo do assunto necessários, consulte [Requisitos técnicos para mobilidade no Lync Server 2013](lync-server-2013-technical-requirements-for-mobility.md). Em seguida, você precisa modificar o ouvinte existente para serviços da Web externos ou criar uma nova regra de publicação para o URL do Serviço Descoberta Automática externo. Se você ainda não tiver uma regra de publicação na Web para o URL externo de Serviços Web para Lync Server 2013 para Pool de Front-Ends, você também precisará publicar uma regra para tal.

> [!NOTE]  
> A regra de publicação de proxy reversa e o ouvinte podem fornecer serviços tanto para Web externa quanto para o Serviço de Descoberta Automática, desde que o certificado atribuído ao ouvinte possua o nome de assunto necessário e os nomes alternativos de assunto para ambos. Para mais detalhes sobre a configuração padrão do ouvinte da Web e regra de publicação, consulte <a href="lync-server-2013-setting-up-reverse-proxy-servers.md">Configurando servidores de proxy reverso para o Lync Server 2013</a>.

Se você decidir usar HTTP para solicitações iniciais de Serviço Descoberta Automática para que não precise atualizar nomes alternativos de assunto para o proxy reverso, você precisará criar ou modificar uma regra de publicação na Web para a porta 80.

Os procedimentos nesta seção descrevem como criar ou modificar as regras de publicação na Web no Microsoft Forefront Threat Management Gateway 2010 para descoberta automática.

> [!NOTE]  
> Esses procedimentos assumem que você possui a Standard Edition do Forefront Threat Management Gateway (TMG) 2010 instalado. Se você estiver utilizando outro proxy reverso, os procedimentos são similares, mas precisarão ser mapeados para a documentação do produto de terceiro.

## Para criar uma regra de publicação na Web para a URL externa de Descoberta Automática

1.  Clique em **Iniciar**, aponte para **Programas**, **Microsoft Forefront TMG** e, então, clique em **Forefront TMG Management**.

2.  No painel esquerdo, expanda **Nome do Servidor**, clique com o botão direito do mouse em **Diretiva de Firewall**, aponte para **Novo** e clique em **Regra de Publicação de Site**.

3.  Na página **Bem-vindo à nova regra de publicação na Web**, digite um nome para exibição para a nova regra de publicação (por exemplo, LyncDiscoveryURL).

4.  Na página **Selecionar Ação da Regra**, selecione **Permitir**.

5.  Na página **Tipo de Publicação**, selecione **Publicar um único site da Web ou balanceador de carga**.

6.  Na página **Segurança da Conexão do Servidor**, selecione **Usar SSL para conectar ao servidor da Web publicado ou ao farm de servidores**.

7.  Na página **Detalhes sobre Publicação Interna**, em **Nome do Site Interno**, digite o nome de domínio totalmente qualificado (FQDN) de seu Pool de diretores (por exemplo, lyncdir01.contoso.local). Caso esteja criando uma regra para o URL de Serviços de Web Externo no Pool de Front-Ends, digite o endereço VIP do Balanceador de carga de hardware (HLB) à frente de Pool de Front-Ends.

8.  Na página **Detalhes de Publicação Interna**, em **Caminho (opcional)**, digite **/\*** como o caminho da pasta a ser publicada e selecione **Encaminhar o cabeçalho de host original**.

9.  Na página **Detalhes do Nome Público**, faça o seguinte:
    
      - Em **Aceitar Solicitações para**, selecione **Este nome de domínio**.
    
      - Em **Nome Público**, digite **lyncdiscover.** *\<sipdomain\>* (o URL externo de Serviço Descoberta Automática). Se você estiver criando uma regra para o URL de Serviços Web externos no Pool de Front-Ends, digite o FQDN referente aos Serviços Web externos no Pool de Front-Ends (por exemplo, lyncwebextpool01.contoso.com).
    
      - Em **Caminho**, digite **/\*** .

10. Na página **Selecionar Ouvinte da Web**, no **Ouvinte da Web**, selecione o Ouvinte SSL existente com o certificado público atualizado.

11. Na página **Delegação de autenticação**, selecione **Nenhuma delegação, mas o cliente pode autenticar diretamente**.

12. Na página **Conjunto de Usuários**, selecione **Todos os Usuários**.

13. Na página **Concluir o novo assistente da regra de publicação da Web**, verifique se as configurações da regra de publicação da Web estão corretas e clique em **Finalizar**.

14. Na lista Forefront TMG de regras de publicação, clique duas vezes na nova regra que você acabou de adicionar para abrir **Propriedades**.

15. Na guia **Para**, faça o seguinte:
    
      - Selecione **Encaminhar o cabeçalho de host original em vez do presente**.
    
      - Selecione **As solicitações parecem vir de computador do Forefront TMG**.

16. Na guia **Ponte**, configure o seguinte:
    
      - Selecione **Servidor Web**.
    
      - Selecione **Redirecionar solicitações para a porta HTTP** e digite **8080** para o número da porta.
    
      - Selecione **Redirecionar solicitações para a porta SSL** e digite **4443** para o número da porta.

17. Clique em **OK**.

18. Clique em **Aplicar** no painel de detalhes para salvar as alterações e atualizar a configuração.

19. Clique em **Regra de Teste** para verificar se a nova regra está definida corretamente.

## Para modificar uma regra de publicação Web existente para adicionar o SAN de Descoberta Automática externa e URL

1.  Clique em **Iniciar**, aponte para **Programas**, **Microsoft Forefront TMG** e, então, clique em **Forefront TMG Management**.
    
    > [!IMPORTANT]  
    > Você irá repetir a modificação para cada regra de publicação e ouvinte que possuir. Normalmente, isso será a única regra e ouvinte para Pools de Front-Ends e um para os conjuntos Diretores ou Diretor opcionais, se você tiver implantado-os.

2.  No painel à esquerda, expanda **ServerName**, clique com o botão direito em **Política de firewall** e clique na regra aplicável. Na aba **Tarefas**, clique na **regra Editar selecionado**.

3.  Na aba **Nome público**, em **Esta regra se aplica a**, selecione **Solicitações para os seguintes sites da Web**.

4.  Clique em **Adicionar**, digite o nome do site de Descoberta Automática novo (por exemplo, “lyncdiscover.contoso.com”) e clique em **OK**.

5.  Na aba **Ouvinte**, clique em **Selecionar certificado** e atribua o novo certificado com as entradas SAN da Descoberta Automática adicionadas. Feche o Ouvinte e as propriedades de Publicação na Web.

6.  Clique em **Aplicar** no painel de detalhes para salvar as alterações e atualizar a configuração.

7.  Clique em **Regra de Teste** para verificar se a nova regra está definida corretamente.

## Para criar uma regra de publicação na Web para a porta 80

1.  Clique em **Iniciar**, aponte para **Programas**, **Microsoft Forefront TMG** e, então, clique em **Forefront TMG Management**.

2.  No painel esquerdo, expanda **Nome do Servidor**, clique com o botão direito do mouse em **Diretiva de Firewall**, aponte para **Novo** e clique em **Regra de Publicação de Site**.

3.  Na página **Bem-vindo à nova regra de publicação na Web**, digite um nome para exibição para a nova regra de publicação (por exemplo, Descoberta Automática do Lync (HTTP)).

4.  Na página **Selecionar Ação da Regra**, selecione **Permitir**.

5.  Na página **Tipo de Publicação**, selecione **Publicar um único site da Web ou balanceador de carga**.

6.  Na página **Segurança da Conexão do Servidor**, selecione **Usar conexões não seguras para conectar ao servidor Web ou ao farm de servidores publicado**.

7.  Na página de **Detalhes da Publicação Interna**, em **Nome do Site Interno**, digite o endereço VIP do Balanceador de carga de hardware (HLB) à frente de Pool de Front-Ends.

8.  Na página **Detalhes de Publicação Interna**, em **Caminho (opcional)**, digite **/\*** como o caminho da pasta a ser publicada e selecione **Encaminhar o cabeçalho de host original, em vez daquele especificado no campo de nome interno de site**.

9.  Na página **Detalhes do Nome Público**, faça o seguinte:
    
      - Em **Aceitar Solicitações para**, selecione **Este nome de domínio**.
    
      - Em **Nome Público**, digite **lyncdiscover.** *\<sipdomain\>* (o URL do Serviço de Descoberta Automática externo).
    
      - Em **Caminho**, digite **/\*** .

10. Em **Selecionar Ouvinte da Web**, em **Ouvinte da Web**, selecione um Ouvinte da Web ou use o Assistente de Nova Definição de Ouvinte da Web para criar um novo.

11. Na página **Delegação de Autenticação**, selecione **Nenhuma delegação, e o cliente não pode autenticar diretamente**.

12. Na página **Conjunto de Usuários**, selecione **Todos os Usuários**.

13. Na página **Concluir o novo assistente da regra de publicação da Web**, verifique se as configurações da regra de publicação da Web estão corretas e clique em **Finalizar**.

14. Na lista Forefront TMG de regras de publicação, clique duas vezes na nova regra que você acabou de adicionar para abrir **Propriedades**.

15. Na guia **Ponte**, configure o seguinte:
    
      - Selecione **Servidor Web**.
    
      - Selecione **Redirecionar solicitações para a porta HTTP** e digite **8080** para o número da porta.
    
      - Verifique se **Redirecionar solicitações para a porta SSL** não está selecionada.

16. Clique em **OK**.

17. Clique em **Aplicar** no painel de detalhes para salvar as alterações e atualizar a configuração.

18. Clique em **Regra de Teste** para verificar se a nova regra está definida corretamente.

19. Verifique se a URL do Serviço Descoberta Automática externo não está definida em nenhuma outra regra de publicação na Web.

## Consulte Também

#### Conceitos

[Configurando servidores de proxy reverso para o Lync Server 2013](lync-server-2013-setting-up-reverse-proxy-servers.md)  
[Requisitos técnicos para mobilidade no Lync Server 2013](lync-server-2013-technical-requirements-for-mobility.md)

