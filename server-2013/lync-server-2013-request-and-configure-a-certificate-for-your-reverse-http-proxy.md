---
title: 'Lync Server 2013: Solicitar e configurar um certificado para seu proxy HTTP reverso'
TOCTitle: Solicitar e configurar um certificado para seu proxy HTTP reverso
ms:assetid: 4b70991e-5f10-40a3-b069-0b227c3a3a0a
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg429704(v=OCS.15)
ms:contentKeyID: 49306635
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Solicitar e configurar um certificado para seu proxy HTTP reverso no Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

Você precisa instalar o certificado de autoridade de certificação (CA) raiz no servidor que está executando o Microsoft Forefront Threat Management Gateway 2010 ou ARR do IIS para a infraestrutura da CA que emitiu os certificados de servidor para os servidores internos que estão executando o Microsoft Lync Server 2013.

Você também deve instalar um certificado de servidor web público no seu servidor proxy reverso. Os nomes alternativos de entidade desse certificado devem conter os FQDNs (nomes de domínio totalmente qualificados) externos publicados de cada pool que é o início para usuários habilitados para acesso remoto, e os FQDNs externos de todos os Diretores ou pools de Diretores que serão usados dentro dessa infraestrutura de Borda. O nome alternativo da entidade também deve conter a URL simples de reunião, a URL simples de discagem e, se você estiver implantando aplicativos móveis e planejar usar descoberta automática, a URL do Serviço Descoberta Automática externo, como mostrado na tabela a seguir.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th></th>
<th>Valor</th>
<th>Exemplo</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Nome da entidade</p></td>
<td><p>FQDN do pool</p></td>
<td><p>webext.contoso.com</p></td>
</tr>
<tr class="even">
<td><p>Nome alternativo de entidade</p></td>
<td><p>FQDN do pool</p></td>
<td><p>webext.contoso.com</p>
<div class="alert">
> [!IMPORTANT]  
> O nome da entidade também deve estar presente no nome alternativo da entidade.
</div></td>
</tr>
<tr class="odd">
<td><p>Nome alternativo de entidade</p></td>
<td><p>Serviços Web do Diretor opcionais (se Diretor for implantado)</p></td>
<td><p>webdirext.contoso.com</p></td>
</tr>
<tr class="even">
<td><p>Nome alternativo de entidade</p></td>
<td><p>URL simples de reunião</p>
<div class="alert">
> [!NOTE]  
> Todas as URLs simples de reunião devem estar no nome alternativo da região. Cada domínio SIP deve ter pelo menos uma URL simples de reunião ativa.
</div></td>
<td><p>meet.contoso.com</p></td>
</tr>
<tr class="odd">
<td><p>Nome alternativo de entidade</p></td>
<td><p>URL simples de discagem</p></td>
<td><p>dialin.contoso.com</p></td>
</tr>
<tr class="even">
<td><p>Nome alternativo de entidade</p></td>
<td><p>Servidor do Office Web Apps</p></td>
<td><p>officewebapps01.contoso.com</p></td>
</tr>
<tr class="odd">
<td><p>Nome alternativo de entidade</p></td>
<td><p>URL de Serviço Descoberta Automática Externo</p></td>
<td><p>lyncdiscover.contoso.com</p>
<div class="alert">
> [!NOTE]  
> Se você também estiver usando o Microsoft Exchange Server também precisará configurar regras de proxy reverso para a descoberta automática do Exchange e URLs de serviços Web.
</div></td>
</tr>
</tbody>
</table>


> [!NOTE]  
> Se sua implantação interna consiste em mais de um servidor Standard Edition ou pool de Front-End, você deve configurar regras de publicação na Web para cada FQDN de web farm externo e será necessário um ouvinte da web e certificado para cada um, ou você deve obter um certificado cujo nome alternativo da entidade contém os nomes usados por todos os pools, atribuí-lo a um ouvinte da web e compartilhá-lo entre várias regras de publicação na web.

## Criar uma solicitação de certificado

Você cria uma solicitação de certificado no proxy reverso. Uma solicitação é criada em outro computador, mas é preciso exportar o certificado assinado com a chave privada e importá-lo para o proxy reverso assim que você o tiver recebido da autoridade de certificação pública.

> [!NOTE]  
> Uma solicitação de certificado ou uma solicitação de assinatura de certificado (CSR) é uma solicitação para uma autoridade de certificação pública (CA) confiável para validar e assinar a chave pública do computador solicitante. Quando um certificado é gerado, uma chave pública e uma chave privada são criadas. Somente a chave pública é compartilhada e assinada. Como o nome implica, a chave pública é disponibilizada para todas as solicitações públicas. A chave pública destina-se a ser usada por clientes, servidores e outros solicitantes que precisam trocar informações com segurança e validar uma identidade de um computador. A chave privada é mantida segura e é usada somente pelo computador que criou o par de chaves para descriptografar mensagens criptografadas com sua chave pública. A chave privada pode ser usada para outros fins. Para fins de proxy reverso, a codificação de dados é o uso principal. De forma secundária, a autenticação do certificado no nível da chave de certificado é outro uso e é limitada somente à validação de que um solicitante tenha a chave pública do computador ou que o computador em que você tenha uma chave pública seja realmente o computador que diz ser.


> [!TIP]
> Se você planejar seus certificados do Servidor de Borda e seus certificados de proxy reverso ao mesmo tempo, deverá observar que há muita semelhança entre os dois requisitos de certificado. Quando você configurar e solicitar seu certificado do Servidor de Borda, combine o Servidor de Borda e os nomes alternativos de entidade de proxy reverso. Você poderá usar o mesmo certificado para seu proxy reverso se exportar o certificado e a chave privada e copiar o arquivo exportado para o proxy reverso e então importar o par certificado/chave e o atribuir como necessário aos próximos procedimentos. Consulte os requisitos de certificado para o Servidor de Borda&nbsp; <A href="lync-server-2013-plan-for-edge-server-certificates.md">Planejar certificados do Servidor de Borda no Lync Server 2013</A> e o proxy reverso <A href="lync-server-2013-certificate-summary-reverse-proxy.md">Resumo de certificado - Proxy reverso no Lync Server 2013</A>. Crie o certificado com uma chave privada exportável. A criação do certificado e da solicitação de certificado com uma chave privada exportável é necessária para o Servidores de Borda em pool, portanto essa é uma prática normal e o Assistente de Certificado na Assistente de Implantação do Lync Server para a Servidor de Borda permitirá que você defina o sinalizador <STRONG>Tornar a chave privada exportável</STRONG>. Assim que você receber a solicitação de certificado de volta da autoridade de certificação pública, você exportará o certificado e a chave privada. Consulte a seção "Para exportar o certificado com a chave privada para Servidores Edge em um pool" no tópico <A href="lync-server-2013-set-up-certificates-for-the-external-edge-interface.md">Configurar certificados para a interface de borda externa para Lync Server 2013</A> para obter detalhes sobre como criar e exportar seu certificado com uma chave privada. A extensão do certificado deverá ser do tipo <STRONG>.pfx</STRONG>.



Para gerar uma solicitação de assinatura de certificado no computador para onde o certificado e a chave privada serão atribuídos, faça o seguinte:

**Criando uma solicitação de assinatura de certificado**

1.  Abra o Console de Gerenciamento Microsoft (MMC) e adicione o snap-in Certificados e selecione **Computadores** e então expanda **Pessoal**. Para obter detalhes sobre como criar um console de certificados no Console de Gerenciamento Microsoft (MMC), consulte [http://go.microsoft.com/fwlink/?LinkId=282616](http://go.microsoft.com/fwlink/?linkid=282616).

2.  Clique com o botão direito do mouse em **Certificados**, clique em **Todas as Tarefas**, clique em **Operações Avançadas**, clique em **Criar Solicitação Personalizada**.

3.  Na página **Registro de Certificado**, clique em **Avançar**.

4.  Na página **Selecionar Política de Registro de Certificado**, em **Solicitação Personalizada**, selecione **Prosseguir sem a política de registro**. Clique em **Avançar**.

5.  Na página **Solicitação Personalizada**, para **Modelo** selecione **(Sem modelo) Chave herdada**. A menos que direcionado por seu provedor de certificado, deixe **Suprimir extensões padrão** desmarcado e a seleção **Solicitar formato** em **PKCS \#10**. Clique em **Avançar**.

6.  Na página **Informações do Certificado**, clique em **Detalhes**, então clique em **Propriedades**.

7.  Na página **Propriedades do Certificado** na guia **Geral** no campo **Nome Amigável**, digite um nome para este certificado. Opcionalmente, digite uma descrição no campo **Descrição**. O Nome Amigável e a descrição são normalmente usados pelo Administrador para identificar a finalidade do certificado, como **Ouvinte de Proxy Reverso para o Lync Server**.

8.  Selecione a guia **Entidade**. Em **Nome da entidade** para o **Tipo**, selecione **Nome comum** para o tipo de nome de Entidade. Para o **Valor**, digite o nome da entidade que você usará para o proxy reverso e então clique em **Adicionar**. No exemplo fornecido na tabela neste tópico, o nome da entidade é webext.contoso.com e seria digitado no campo Valor para o nome da Entidade.

9.  Na guia **Entidade**, em **Nome alternativo**, selecione **DNS** na lista suspensa de **Tipo**. Para cada nome alternativo de entidade definido exigido no certificado, digite o nome de domínio totalmente qualificado e então clique em **Adicionar**. Por exemplo, na tabela há três nomes alternativos de entidade, meet.contoso.com, dialin.contoso.com e lyncdiscover.contoso.com. No campo **Valor**, digite meet.contoso.com, então clique em **Adicionar**. Repita esse procedimento para cada nome alternativo de entidade que seja necessário definir.

10. Na página **Propriedades do Certificado**, clique na guia **Extensões**. Nessa página, você definirá as finalidades da chave criptográfica no **Uso de chave** e o uso estendido de chave em **Uso Estendido de Chave (políticas de aplicação)**.

11. Clique na seta **Uso de chave** para mostrar as **Opções disponíveis**. Em Opções disponíveis, clique em **Assinatura digital**, então clique em **Adicionar**. Clique em **Codificação de chave**, então clique em **Adicionar**. Se a caixa de seleção de **Tornar estes usos de chave críticos** estiver desmarcada, marque-a.

12. Clique na seta **Uso Estendido de Chave (políticas de aplicação)** para mostrar as **Opções disponíveis**. Em Opções disponíveis, clique em **Autenticação do Servidor**, então clique em **Adicionar**. Clique em **Autenticação do Cliente**, então clique em **Adicionar**. Se a caixa de seleção de **Tornar os Usos Estendidos de Chave críticos** estiver marcada, desmarque-a. Ao contrário da caixa de seleção Uso de chave (que deverá ser marcada), certifique-se de que a caixa de seleção Uso Estendido de Chave não esteja marcada.

13. Na página **Propriedades do Certificado**, clique na guia **Chave Privada**. Clique na seta **Opções de chave**. Para **Tamanho de chave**, selecione **2048** na lista suspensa. Se você estiver gerando esse par de chaves e o CSR em um computador diferente do proxy reverso para o qual este certificado se destina, selecione **Tornar a chave privada exportável**.
    
    > [!security]  
    > A seleção de <strong>Tornar uma chave privada exportável</strong> é geralmente aconselhável quando você tem mais de um proxy reverso em um farm, porque você copiará o certificado e a chave privada para cada máquina no farm. Se você permitir uma chave privada exportável, deverá tomar cuidado adicional com o certificado e o computador em que ele será gerado. A chave privada, se comprometida, inutilizará o certificado, além de potencialmente expor o computador ou computadores a acesso externo e a outras vulnerabilidades de segurança.

14. Na guia **Chave Privada**, clique na seta **Tipo de chave**. Selecione a opção **Exchange**.

15. Clique em **OK** para salvar as **Propriedades do Certificado** que você definiu.

16. Na página **Registro de Certificado**, clique em **Avançar**.

17. Na página **Onde você deseja salvar a solicitação offline?**, será solicitado um **Nome de Arquivo** e um **Formato de Arquivo** para salvar a solicitação de assinatura do certificado.

18. No campo de entrada **Nome do Arquivo**, digite um caminho e um nome de arquivo para a solicitação ou clique em **Procurar** para selecionar um local para o arquivo e digite o nome de arquivo para a solicitação.

19. Para o **Formato de arquivo**, clique em **Base 64** ou em **Binário**. Selecione **Base 64** a menos que seja instruído o contrário pelo fornecedor de seus certificados.

20. Localize o arquivo de solicitação salvo na etapa anterior. Envie para sua autoridade de certificação pública.
    
    > [!IMPORTANT]  
    > A Microsoft identificou CAs públicas que atendem aos requisitos para fins de Comunicações Unificadas. Uma lista é mantida no seguinte artigo da base de dados de conhecimento. <a href="http://go.microsoft.com/fwlink/?linkid=282625">http://go.microsoft.com/fwlink/?LinkId=282625</a>
