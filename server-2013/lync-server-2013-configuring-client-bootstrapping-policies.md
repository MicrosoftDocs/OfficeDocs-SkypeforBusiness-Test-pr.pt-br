---
title: Configurando políticas de bootstrap de cliente no Lync Server 2013
TOCTitle: Configurando políticas de bootstrap de cliente no Lync Server 2013
ms:assetid: 45042eca-b845-4207-b12f-b8b7f5d44bdf
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg425941(v=OCS.15)
ms:contentKeyID: 49306576
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurando políticas de bootstrap de cliente no Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

O Console de Gerenciamento de Política de Grupo (GPMC) e o Editor de Objeto de Política de Grupo são ferramentas que você utiliza para gerenciar Políticas de Grupo. Incluído no Modelo Administrativo de Política de Grupo do Office, estão os Modelos Administrativos Lync 2013.admx (ADMX) e .adml (ADML), que contém configurações de políticas com base em registro para configurar os objetos da Política de Grupo no domínio. Os arquivos ADML são complementos específicos de idioma para arquivos ADMX. Cada arquivo ADMX e ADML contém as configurações de política para um único aplicativo Office.

Para Lync 2013, existem várias políticas de bootstrap do cliente que você deve considerar configurar antes de entrar no servidor pela primeira vez. Por exemplo, os servidores padrão e modo de segurança que o cliente deve utilizar até sair é completo. Você pode usar uma Política de Grupo para estabelecer tais configurações em registros de computador dos usuários antes que eles entrem e comecem a receber configurações de provisionamento em banda para o servidor. A tabela a seguir lista as configurações de Política de Grupo disponíveis para Lync 2013.

### Configurações de Política de Grupo para Lync 2013

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Configuração de Política de Grupo</th>
<th>Descrição</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Especificar servidor<br />(ConfigurationMode)</p></td>
<td><p>Especifica como o Lync 2013 identifica o transporte e servidor a utilizar durante a assinatura. Com essa configuração, você especifica o seguinte:</p><ul><li><p>ServerAddressExternal: Especifica o nome de servidor ou endereço IP utilizado pelos clientes e contatos federados ao se conectar de fora do firewall externo.</p></li><li><p>ServerAddressInternal: Especifica o nome de servidor ou endereço IP utilizado quando os clientes se conectam de dentro do firewall da organização.</p></li><li><p>Transport: Especifica o protocolo TCP ou protocolo TLS.</p></li></ul></td>
</tr>
<tr class="even">
<td><p>Versões de servidor adicionais suportadas<br />(ConfiguredServerCheckValues)</p></td>
<td><p>Especifica uma lista de nomes de versão de servidor separadas por ponto e vírgula que o Lync Server 2013 irá efetuar login, além das versões de servidor que são suportadas por padrão.</p></td>
</tr>
<tr class="odd">
<td><p>Desativa o upload automático de logs de falha de assinatura (DisableAutomaticSendTracing)</p></td>
<td><p>Efetua upload automaticamente dos logs de falha de assinatura para análise do Lync Server. Nenhum log é enviado automaticamente se a assinatura ocorrer com sucesso. Se esta política não estiver configurada, o seguinte ocorre:</p>
<dl>
<dt><span></span></dt>
<dd><p>Para usuários Lync Online: Logs de falha de assinatura são enviados automaticamente..</p>
</dd>
<dt><span></span></dt>
<dd><p>Para usuários locais Lync: Uma caixa de diálogo de confirmação é exibida ao usuário antes do envio.</p>
</dd>
</dl>
<p>Quando a configuração estiver desativada, os logs de assinatura são enviados automaticamente para o Lync Server para Lync locais e usuários Lync Online. Quando essa configuração estiver ativada, os logs de assinatura nunca são enviados automaticamente.</p></td>
</tr>
<tr class="even">
<td><p>Desativar o fallback de HTTP para conexão SIP<br />(DisableHttpConnect)</p></td>
<td><p>Previne que o Lync Server tente se conectar com o servidor utilizando HTTP, caso TLS ou TCP estejam indisponíveis. Por padrão, o Lync tenta primeiro se conectar ao servidor utilizando o TLS ou TCP e, se nenhum destes métodos de transporte estejam funcionando, o Lync tenta se conectar utilizando HTTP. Utilize essa política para desativar a tentativa de conexão por HTTP de fallback.</p></td>
</tr>
<tr class="odd">
<td><p>Requer credenciais de login<br />(DisableNTCredentials)</p></td>
<td><p>Requer que o usuário forneça credenciais de login para Lync em vez de utilizar automaticamente credenciais do Windows durante a assinatura a um servidor SIP.</p></td>
</tr>
<tr class="even">
<td><p>Desativar a verificação de versão de servidor<br />(DisableServerCheck)</p></td>
<td><p>Se esta política estiver definida para 1, evita que Lync verifique o nome do servidor e versão antes de assinar. Por padrão, o Lync efetua tais verificações antes de assinar.</p></td>
</tr>
<tr class="odd">
<td><p>Ativar o uso de BITS para baixar arquivos do Serviço de Catálogo de Endereços<br />(EnableBitsForGalDownload)</p></td>
<td><p>Ativa o Lync para utilizar o Serviço de transferência inteligente de plano de fundo (BITS) para baixar os arquivos do Serviço de Catálogo de Endereços.</p></td>
</tr>
<tr class="even">
<td><p>Configurar o modo de segurança do SIP<br />(EnableSIPHighSecurityMode)</p></td>
<td><p>Ativa o Lync a enviar e receber mensagens instantâneas de forma mais segura. Esta política não possui efeito no Windows .NET ou serviços do Servidor do Microsoft Exchange.</p>
<p>Se você não definir esta configuração de política, o Lync poderá usar qualquer transporte. Mas, caso não utilize o TLS e o servidor autenticar usuários, o Lync deve utilizar a autenticação do NTLM ou Kerberos.</p></td>
</tr>
<tr class="odd">
<td><p>Atraso inicial de download do Catálogo de Endereços global<br />(GalDownloadInitialDelay)</p></td>
<td><p>Especifica o período de tempo antes de um download da lista de endereço global (GAL) ocorrer. O valor padrão é 60 minutos, o que significa que o download do arquivo GAL é atrasado para um período aleatório entre 0 e 60 minutos.</p></td>
</tr>
<tr class="even">
<td><p>Evita que usuários executem o Microsoft Lync<br />(PreventRun)</p></td>
<td><p>Evita que os usuários executem o Lync. Você pode definir esta configuração de política tanto sob a Configuração do Computador quanto da Configuração de usuário, mas a configuração de política em Configuração de Computador tem precedência.</p></td>
</tr>
<tr class="odd">
<td><p>Permitir armazenamento de senhas de usuário<br />(SavePassword)</p></td>
<td><p>Ativa o Lync a armazenar senhas.</p></td>
</tr>
<tr class="even">
<td><p>Configurar o modo de compressão do SIP<br />(SipCompression)</p></td>
<td><p>Especifica quando ativar a compressão do SIP. Por padrão, a compressão do SIP está ativada com base na velocidade do adaptador. Observe que configurar tal política pode causar um aumento no tempo de assinatura.</p></td>
</tr>
<tr class="odd">
<td><p>Lista de domínio confiável<br />(TrustModelData)</p></td>
<td><p>Lista os domínios confiáveis que não correspondem ao prefixo do domínio SIP cliente.</p></td>
</tr>
</tbody>
</table>


As políticas configuradas no servidor têm precedência sobre as configurações de Política de Grupo e as opções de cliente configuradas pelo usuário. A tabela a seguir resume a ordem na qual as configurações têm precedência quando ocorre um conflito.

### Precedência das Políticas de Grupo

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Precedência</th>
<th>Local ou método da configuração</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>1</p></td>
<td><p>Provisionamento em banda do Lync Server 2013</p>
<p></p></td>
</tr>
<tr class="even">
<td><p>2</p></td>
<td><p>HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Office\15.0\Lync</p>
<p></p></td>
</tr>
<tr class="odd">
<td><p>3</p></td>
<td><p>HKEY_CURRENT_USER\SOFTWARE\Policies\Microsoft\Office\15.0\Lync</p>
<p></p></td>
</tr>
<tr class="even">
<td><p>4</p></td>
<td><p>A caixa de diálogo Lync - Opções no Lync 2013</p></td>
</tr>
</tbody>
</table>


## Para definir as configurações de Política de Grupo usando os arquivos de modelo administrativo do Lync 2013

1.  Crie uma pasta de nível de raiz para inserir todos os arquivos ADMX de idioma neutro. Por exemplo, crie uma pasta raiz para o armazenamento central no controlador de domínio neste local:
    
    `%systemroot%\sysvol\domain\policies\PolicyDefinitions`
    
    > [!NOTE]  
    > Este procedimento presume que você deseja gerenciar diversos computadores no seu domínio. Neste caso, armazene os modelos em um repositório central na pasta Sysvol no controlador de domínio primário. Isso fornece uma localização de armazenamento central replicado para Modelos Administrativos.

2.  Crie uma subpasta para cada idioma que for utilizar. Essas subpastas vão conter os arquivos de recurso ADML específicos do idioma. Por exemplo, crie uma subpasta para United States English (EN-US) neste local:
    
    `%systemroot%\sysvol\domain\policies\PolicyDefinitions\EN-US`

Para detalhes sobre arquivos ADMX, consulte o Guia Passo a Passo de Arquivos ADMX para Gerenciamento de Políticas de Grupo em [http://go.microsoft.com/fwlink/?linkid=75124\&clcid=0x416](http://go.microsoft.com/fwlink/?linkid=75124%26clcid=0x416).

