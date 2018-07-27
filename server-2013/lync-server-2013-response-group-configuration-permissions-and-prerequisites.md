---
title: 'Lync Server 2013: Permissões e pré-requisitos de configuração de Grupo de Resposta'
TOCTitle: Permissões e pré-requisitos de configuração de Grupo de Resposta
ms:assetid: 4266f16a-b387-452c-a8ca-d771a3c58f0f
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204840(v=OCS.15)
ms:contentKeyID: 49306528
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Permissões e pré-requisitos de configuração de Grupo de Resposta no Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

Grupo de Resposta é um recurso de gerenciamento de chamada Enterprise Voice. Este tópico descreve o que você precisa ter antes de configurar o Grupo de Resposta e as credenciais e permissões que você precisa para efetuar tarefas de configuração.

Essa seção presume que você tenha lido a documentação de planejamento relacionada ao Grupo de Resposta. Para detalhes, consulte [Planejamento de recursos de gerenciamento de chamada no Lync Server 2013](lync-server-2013-planning-for-call-management-features.md) na documentação de Planejamento.

## Ferramentas de configuração e funções administrativas

Você pode utilizar as seguintes ferramentas administrativas para configurar o Grupo de Resposta:

  - Painel de Controle do Lync Server

  - Ferramenta de Configuração de Grupo de Resposta

  - Shell de Gerenciamento do Lync Server

Para configurar grupos de resposta, você deve ser membro de pelo menos uma das funções administrativas a seguir:


<table style="width:100%;">
<colgroup>
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>Grupo de segurança do Diretório Ativo(1)</strong></p></td>
<td><p>Criar fluxo de trabalho</p></td>
<td><p>Atribuir gerente</p></td>
<td><p>Criar/atribuir agentes, filas</p></td>
<td><p>Criar/gerenciar horas extras e de feriado</p></td>
<td><p>Ativar/Desativar fluxo de trabalho</p></td>
<td><p>Configurar fluxo de trabalho (IVR ou Grupo de busca)</p></td>
</tr>
<tr class="even">
<td><p><strong>CsResponseGroupAdministrator</strong></p></td>
<td><p>v</p></td>
<td><p>v</p></td>
<td><p>v</p></td>
<td><p>v</p></td>
<td><p>v</p></td>
<td><p>v</p></td>
</tr>
<tr class="odd">
<td><p><strong>CsResponseGroupManager</strong></p></td>
<td> </td>
<td><p>v(2)</p></td>
<td><p>v(3)</p></td>
<td><p>v(3)</p></td>
<td><p>v(3)</p></td>
<td><p>v(3)</p></td>
</tr>
<tr class="even">
<td><p><strong>CsVoiceAdministrator</strong></p></td>
<td><p>v</p></td>
<td><p>v</p></td>
<td><p>v</p></td>
<td><p>v</p></td>
<td><p>v</p></td>
<td><p>v</p></td>
</tr>
<tr class="odd">
<td><p><strong>CsServerAdministrator</strong></p></td>
<td><p>v</p></td>
<td><p>v</p></td>
<td><p>v</p></td>
<td><p>v</p></td>
<td><p>v</p></td>
<td><p>v</p></td>
</tr>
<tr class="even">
<td><p><strong>CsAdministrator</strong></p></td>
<td><p>v</p></td>
<td><p>v</p></td>
<td><p>v</p></td>
<td><p>v</p></td>
<td><p>v</p></td>
<td><p>v</p></td>
</tr>
<tr class="odd">
<td><p><strong>CsViewOnlyAdministrator</strong></p></td>
<td><p>v(4)</p></td>
<td><p>v(4)</p></td>
<td><p>v(4)</p></td>
<td><p>v(4)</p></td>
<td><p>v(4)</p></td>
<td><p>v(4)</p></td>
</tr>
</tbody>
</table>


> [!NOTE]  
> <strong>(1)</strong> Um objeto de usuário Serviços de Domínio Active Directory deve ser um membro do grupo de segurança especificado Active Directory na lista. Um administrador ou outro membro do grupo Active Directory delegado com permissões adequadas para adicionar usuários a um grupo de segurança (por exemplo, Administrador, Operadores de conta), é necessário adicionar um objeto de usuário ao grupo de segurança listado ou ao grupo para o usuário poder efetuaras funções listadas. <strong>(2)</strong> Apenas para fluxos de trabalho que o CsResponseGroupAdministrator possui atribuído ao CsResponseGroupManager. <strong>(3)</strong> Um Gerenciador Grupo de Resposta pode atribuir outro membro do CsResponseGroupManager para um fluxo de trabalho que o gerenciador atual já gerencia. <strong>(4)</strong> CsViewOnlyAdministrator pode executar apenas cmdlets com o verbo &quot;Get&quot; Shell de Gerenciamento do Lync Server.

## Grupo de Resposta Pré-requisitos de configuração

Grupo de Resposta requer os seguintes componentes:

  - Serviço de aplicativos

  - Aplicativo Grupo de Resposta

  - Pacotes de idioma

  - Repositório de arquivos (para manter arquivos de áudio)

  - Serviços da Web (inclui o Ferramenta de Configuração de Grupo de Resposta e o console de entrar e sair dos agentes)

Todos estes componentes são instalados por padrão ao implantar o Enterprise Voice.

Você pode precisar efetuar as seguintes tarefas antes de continuar Grupo de Resposta:

  - Ativar usuários para Lync Server 2013 e Enterprise Voice.

  - Modificar um arquivo de configuração para estar em conformidade com os Padrões de Processamento de Informação Federal (FIPS).

  - Modificar o agrupamento do banco de dados para suportar caracteres Yi, Meng, e Zang para nomes de fila e nomes de grupo de agentes.

## Ativando usuários

A primeira etapa na configuração do Grupo de Resposta é criar grupos de agentes. Antes de poder criar um, você deve ativar os usuários que serão agentes para Grupo de Resposta para Lync Server 2013 e Enterprise Voice. Ativar usuários para Lync Server 2013 normalmente é uma etapa na implantação do servidor Enterprise Edition ou Standard Edition. Para detalhes sobre ativar usuários para Lync Server 2013, consulte [Habilitar ou reabilitar uma conta de usuário para o Lync Server](lync-server-2013-disable-or-re-enable-user-account-for-lync-server.md). Ativar usuários para Enterprise Voice é normalmente uma etapa na implantação do Enterprise Voice. Para detalhes, consulte [Habilitar usuários para Enterprise Voice no Lync Server 2013](lync-server-2013-enable-users-for-enterprise-voice.md).

## Em conformidade com os requisitos FIPS

Essa seção se aplica apenas em caso de a organização precisar estar em conformidade com os Padrões de Processamento de Informações Federais (FIPS).

Para estar em conformidade com FIPS, você precisa modificar o nível de aplicativo do arquivo Web.config para utilizar um algoritmo de criptografia diferente após instalar os Serviços Web. Você precisa especificar que o ASP.NET utiliza o algoritmo do Padrão de Criptografia de Dados Triplo (3DES) para processar dados de estado de visualização. Para o Aplicativo Grupo de Resposta, este requisito se aplica ao Ferramenta de Configuração de Grupo de Resposta e o console de entrada e saída do agente. Para obter detalhes sobre este requisito, consulte o artigo 911722 da Base de Dados de Conhecimento da Microsoft, "Você pode receber uma mensagem de erro quando você acessa páginas da Web ASP.NET que tem ViewState habilitado após a atualização do ASP.NET 1.1 para ASP.NET 2.0" em [http://go.microsoft.com/fwlink/p/?linkId=196183](http://go.microsoft.com/fwlink/p/?linkid=196183).

Para modificar o arquivo Web.config, faça o seguinte:

1.  Em um editor de texto como o Bloco de Notas, abra o arquivo Web.config de nível de aplicativo.

2.  No arquivo Web.config, localize a seção `<system.web>`.

3.  Adicione a seguinte seção `<machineKey>` na seção `<system.web>`:
    
        <machineKey validationKey="AutoGenerate,IsolateApps" decryptionKey="AutoGenerate,IsolateApps" validation="3DES" decryption="3DES"/>

4.  Salve o arquivo Web.config.

5.  Reinicie o serviço IIS (Serviços de Informações da Internet) executando o seguinte comando no prompt de comando:
    
        iisreset

## Suporte a caracteres Yi, Meng e Zang

Essa seção se aplica apenas em caso de a sua organização precisar suportar caracteres Yi, Meng ou Zang.

> [!NOTE]  
> Para obter informações sobre quais são os caracteres Yi, Meng e Zang e por que eles podem ser importantes para a implantação, consulte as informações no conjunto de caracteres GB18030 <a href="http://go.microsoft.com/fwlink/p/?linkid=240223">http://go.microsoft.com/fwlink/p/?linkId=240223</a>.

Para suportar caracteres Yi, Meng ou Zang, você precisa modificar o agrupamento para o banco de dados Rgsconfig. Altere o agrupamento da coluna **Nome** nas seguintes tabelas em cada banco de dados Rgsconfig:

  - dbo.AgentGroups

  - dbo.BusinessHours

  - dbo.HolidaySets

  - dbo.Queues

  - dbo.Workflows

Para SQL Server 2008 R2 e SQL Server 2012, utilize o agrupamento Latin\_General\_100 (Diferencia acentos). Se você utiliza tal agrupamento, todos os nomes de objeto não diferenciam maiúsculas de minúsculas.

Você pode mudar o agrupamento utilizando o Microsoft SQL Server Management Studio. Para obter detalhes sobre como usar esta ferramenta, consulte "Usando o SQL Server Management Studio" em [http://go.microsoft.com/fwlink/p/?linkId=196184](http://go.microsoft.com/fwlink/p/?linkid=196184). Siga essas etapas para alterar o agrupamento:

1.  Certifique-se de que o SQL Server Management Studio está configurado para permitir alterações que precisam que as tabelas sejam recriadas. Para obter detalhes, consulte "Caixa de diálogo Salvar (Não Permitido)" em [http://go.microsoft.com/fwlink/p/?linkId=196186](http://go.microsoft.com/fwlink/p/?linkid=196186). Para obter detalhes sobre como definir o agrupamento de uma coluna, consulte "Como definir agrupamento de colunas (Visual Database Tools)" em [http://go.microsoft.com/fwlink/p/?linkId=196185](http://go.microsoft.com/fwlink/p/?linkid=196185).

2.  Utilizando o Microsoft SQL Server Management Studio, conecte-se ao banco de dados Rgsconfig.

3.  Encontre a tabela que deseja alterar no banco de dados Rgsconfig, clique com o botão direito na tabela e em **Design** .

4.  Altere o agrupamento da coluna **Nome** e salve a tabela.

