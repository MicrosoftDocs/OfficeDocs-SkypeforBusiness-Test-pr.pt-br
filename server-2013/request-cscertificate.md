---
title: Request-CsCertificate
TOCTitle: Request-CsCertificate
ms:assetid: 24e8ba6f-6023-4c03-a594-5b40784fd16a
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg425723(v=OCS.15)
ms:contentKeyID: 49306147
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Request-CsCertificate

 

_**Tópico modificado em:** 2015-03-09_

Oferece uma maneira de solicitar certificados para uso com servidores que executam o Lync Server e com funções de servidor. Oferece também uma maneira de conferir o status das solicitações de certificados existentes e, caso necessário, de cancelar solicitações que possam existir. Este cmdlet foi introduzido no Lync Server 2010.

## Sintaxe

    Request-CsCertificate -New <SwitchParameter> -Type <CertType[]> [-AllSipDomain <SwitchParameter>] [-CA <String>] [-CaAccount <String>] [-CaPassword <String>] [-City <String>] [-ClientEKU <$true | $false>] [-ComputerFqdn <Fqdn>] [-Country <String>] [-DomainName <String>] [-FriendlyName <String>] [-GlobalCatalog <Fqdn>] [-GlobalSettingsDomainController <Fqdn>] [-KeyAlg <RSA | ECDH_P256 | ECDH_P384 | ECDH_P521>] [-KeySize <Int32>] [-Organization <String>] [-OU <String>] [-Output <String>] [-PrivateKeyExportable <$true | $false>] [-State <String>] [-Template <String>] <COMMON PARAMETERS>

    Request-CsCertificate -List <SwitchParameter> [-RequestId <Int32>] <COMMON PARAMETERS>

    Request-CsCertificate -Retrieve <SwitchParameter> [-RequestId <Int32>] <COMMON PARAMETERS>

    Request-CsCertificate -Clear <SwitchParameter> [-RequestId <Int32>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-Report <String>] [-WhatIf [<SwitchParameter>]]

## Exemplos

## EXEMPLO 1

O comando mostrado no Exemplo 1 cria uma nova solicitação de certificado: ele entra em contato com a CA atl-ca-001.litwareinc.com\\myca e solicita um novo certificado WebServicesExternal.

    Request-CsCertificate -New -Type WebServicesExternal -CA "atl-ca-001.litwareinc.com\myca"

## EXEMPLO 2

O Exemplo 2 lista todas as solicitações de certificado pendentes realizadas com o cmdlet **Request-CsCertificate**.

    Request-CsCertificate -List

## EXEMPLO 3

O Exemplo 3 usa o parâmetro Output para criar uma solicitação de certificado offline.

    Request-CsCertificate -New -Type WebServicesExternal -Output C:\Certificates\WebServicesExternal.cer

## EXEMPLO 4

O Exemplo 4 anterior é um exemplo mais detalhado (e mais realista) de como usar o cmdlet Request-CsCertificate. Este exemplo solicita um certificado para uso com a edição Standard do Lync Server.

    Request-CsCertificate -New -Type Default,WebServicesInternal,WebServicesExternal -ComputerFqdn "atl-cs-001.litwareinc.com" -CA "atl-ca-001.litwareinc.com\myca" -FriendlyName "Standard Edition Certficate" -Template jcila -PrivateKeyExportable $True -DomainName "atl-cs-001.litwareinc.com,atl-ext.litwareinc.com"

## EXEMPLO 5

No Exemplo 5, um certificado de pool é solicitado para uso com a edição Enterprise do Lync Server.

    Request-CsCertificate -New -Type Default,WebServicesInternal,WebServicesExternal -ComputerFqdn "atl-cs-001.litwareinc.com" -CA "atl-ca-001.litwareinc.com\myca" -FriendlyName "Enterprise Edition Pool Certificate" -Template jcila -PrivateKeyExportable $True -DomainName "pool1.litwareinc.com,pool1int.litwareinc.com,pool1ext.litwareinc.com"

## EXEMPLO 6

O Exemplo 6 mostra como solicitar um certificado para o Servidor de Borda interno.

    Request-CsCertificate -New -Type Internal -ComputerFqdn "atl-edge-001" -CA "atl-ca-001.litwareinc.com\myca" -FriendlyName "Internal Edge Certificate" -Template jcila -PrivateKeyExportable $True -DomainName "atl-edge-001.litwareinc.com, ap.litwareinc.com"

## EXEMPLO 7

O Exemplo 7 é uma variação do comando exibido no Exemplo 6. Neste caso, porém, a solicitação é para o Servidor de Borda externo.

    Request-CsCertificate -New -Type AccessEdgeExternal,DataEdgeExternal,AudioVideoAuthentication -ComputerFqdn "atl-edge-001" -CA "atl-ca-001.litwareinc.com\myca" -FriendlyName "External Edge Certificate" -Template jcila -PrivateKeyExportable $True -DomainName "atl-edge-001.litwareinc.com,ap.litwareinc.com,dp.litwareinc.com,atl-edge-001"

## Descrição detalhada

O Lync Server usa certificados para que servidores e funções de servidores verifiquem suas identidades; por exemplo, um Servidor de Borda usa certificados para verificar se o computador com o qual está se comunicando realmente é um Servidor Front-End e vice-versa. Para implementar completamente o Lync Server, é preciso ter os certificados apropriados atribuídos às funções de servidor apropriadas.

Uma maneira de solicitar certificados para uso com o Lync Server é chamar o cmdlet **Request-CsCertificate**. Embora seja possível usar outras ferramentas comuns do Windows para solicitar certificados para uso com o Lync Server, uma grande vantagem de se usar o cmdlet **Request-CsCertificate** é o fato de que o cmdlet irá analisar sua topologia antes de entrar em contato com a CA (autoridade de certificação). Com base nessa análise, o cmdlet **Request-CsCertificate** solicitará automaticamente um certificado com os campos nome da entidade e nome alternativo de entidade apropriados.

O cmdlet **Request-CsCertificate** foi desenvolvido para solicitar certificados especificamente para uso com o Lync Server. Ele não foi desenvolvido para ser uma ferramenta de gerenciamento de certificados para fins gerais.

Além de solicitar novos certificados, este cmdlet também pode ser usado para analisar solicitações pendentes de certificados, desde que essas solicitações tenham sido feitas com o cmdlet **Request-CsCertificate**. O cmdlet **Request-CsCertificate** também pode ser usado para excluir solicitações pendentes de certificados, desde que essas solicitações tenham sido feitas com o cmdlet.

Ao tentar obter solicitações de certificado, você talvez receba uma mensagem de erro se tiver alguma solicitação revogada; no momento, o cmdlet **Request-CsCertificate** só tem suporte a estes tipos de solicitações: Issued (emitida), Denied (negada) e Pending (pendente). Se tiver problemas por causa de um certificado revogado, use um comando semelhante a este para limpar a solicitação revogada (onde 224 é o RequestID da solicitação de certificado revogada):

Request-CsCertificate –Clear –RequestID 224

Depois disso, deve ser possível obter solicitações de certificado.

Quem pode executar este cmdlet: É preciso ser um administrador local e ter direitos à autoridade de certificação especificada para executar o cmdlet **Request-CsCertificate** localmente. Para retornar uma lista de todas as funções do RBAC (controle de acesso baseado na função) atribuídas a este cmdlet (incluindo eventuais funções personalizadas do RBAC que você mesmo tenha criado), execute o comando a seguir no prompt do Windows PowerShell:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Request-CsCertificate"}

## Parâmetros


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Parâmetro</th>
<th>Obrigatório</th>
<th>Tipo</th>
<th>Descrição</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>Clear</em></p></td>
<td><p>Obrigatório</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Quando presente, exclui solicitações de certificado pendentes realizadas com o cmdlet <strong>Request-CsCertificate</strong>.</p></td>
</tr>
<tr class="even">
<td><p><em>List</em></p></td>
<td><p>Obrigatório</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Quando presente, lista solicitações de certificado pendentes realizadas com o cmdlet <strong>Request-CsCertificate</strong>.</p></td>
</tr>
<tr class="odd">
<td><p><em>New</em></p></td>
<td><p>Obrigatório</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Quando presente, indica que você deseja solicitar um novo certificado.</p></td>
</tr>
<tr class="even">
<td><p><em>Retrieve</em></p></td>
<td><p>Obrigatório</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Quando presente, recupera solicitações de certificado pendentes realizadas com o cmdlet <strong>Request-CsCertificate</strong>, e tenta concluir a operação e importar o certificado solicitado.</p></td>
</tr>
<tr class="odd">
<td><p><em>Type</em></p></td>
<td><p>Obrigatório</p></td>
<td><p>Microsoft.Rtc.Management.Deployment.CertType[]</p></td>
<td><p>Tipo de certificado que está sendo solicitado. Os tipos de certificado incluem, mas não se restringem a:</p>
<p>AccessEdgeExternal</p>
<p>AudioVideoAuthentication</p>
<p>DataEdgeExternal</p>
<p>Default</p>
<p>External</p>
<p>Internal</p>
<p>iPhoneAPNService</p>
<p>iPadAPNService</p>
<p>MPNService</p>
<p>PICWebService (apenas Microsoft Lync Online 2010)</p>
<p>ProvisionService (apenas Microsoft Lync Online 2010)</p>
<p>WebServicesExternal</p>
<p>WebServicesInternal</p>
<p>WsFedTokenTransfer</p>
<p>Por exemplo, esta sintaxe solicita um novo certificado Default (padrão): -Type Default.</p>
<p>É possível especificar mais de um tipo em um mesmo comando, separando os tipos de certificados por vírgulas:</p>
<p>-Type Internal,External,Default</p></td>
</tr>
<tr class="even">
<td><p><em>AllSipDomain</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Quando presente, todos os seus domínios SIP são adicionados automaticamente ao campo Nome Alternativo do Assunto certificados. Se não estiver presente, apenas o domínio SIP é adicionado por padrão. No entanto, domínios adicionais podem ser especificados usando o parâmetro DomainName.</p></td>
</tr>
<tr class="odd">
<td><p><em>CA</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>FQDN (nome de domínio totalmente qualificado) que aponta para a CA. Por exemplo: -CA &quot;atl-ca-001.litwareinc.com\myca&quot;. Para obter uma lista de CAs conhecidas, digite o seguinte no prompt do Windows PowerShell e pressione ENTER:</p>
<p>certutil</p>
<p>A propriedade Config retornada pelo Certutil indica a localização de uma CA.</p></td>
</tr>
<tr class="even">
<td><p><em>CaAccount</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Nome da conta do usuário que está solicitando o novo certificado, usando o formato nome_de_dominio\nome_de_usuario. Por exemplo: -CaAccount &quot;litwareinc\kenmyer&quot;. Caso não seja especificado, o cmdlet <strong>Request-CsCertificate</strong> usará as credenciais do usuário conectado ao solicitar o novo certificado.</p></td>
</tr>
<tr class="odd">
<td><p><em>CaPassword</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Senha do usuário que está solicitando o novo certificado (conforme especificado com o parâmetro CaAccount).</p></td>
</tr>
<tr class="even">
<td><p><em>City</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Cidade na qual o certificado será implementado.</p></td>
</tr>
<tr class="odd">
<td><p><em>ClientEKU</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Boolean</p></td>
<td><p>Defina este parâmetro como True se o certificado for usado para autenticação de clientes. Esse tipo de autenticação é necessário se você quiser que seus usuários sejam capazes de trocar mensagens instantâneas com pessoas que tenham contas com a AOL. A parte EKU do nome do parâmetro é uma abreviação para uso estendido de chave; esse campo lista as utilizações válidas do certificado.</p></td>
</tr>
<tr class="even">
<td><p><em>ComputerFqdn</em></p></td>
<td><p>Opcional</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>FQDN do computador para o qual o certificado está sendo solicitado. Quando presente, este parâmetro força o cmdlet <strong>Request-CsCertificate</strong> a se conectar ao Repositório de Gerenciamento Central para localizar o computador especificado. Sempre use o nome do computador ao solicitar um certificado, mesmo ao solicitar um certificado do pool. O cmdlet <strong>Request-CsCertificate</strong> adicionará automaticamente o nome do pool ao nome da entidade de qualquer certificado obtido com o uso deste cmdlet.</p></td>
</tr>
<tr class="odd">
<td><p><em>Confirm</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Solicita confirmação antes da execução do comando.</p></td>
</tr>
<tr class="even">
<td><p><em>Country</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>País/região no qual o certificado será implementado.</p></td>
</tr>
<tr class="odd">
<td><p><em>DomainName</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Lista separada por vírgulas dos nomes de domínio totalmente qualificado que devem ser adicionados ao campo Nome Alternativo da Entidade do certificado. Por exemplo:</p>
<p>-DomainName &quot;atl-cs-001.litwareinc.com, atl-cs-002.litwareinc.com,atl-cs-003.litwareinc.com&quot;</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Suprime a exibição de mensagens de erro não fatais que possam ocorrer na execução do comando.</p></td>
</tr>
<tr class="odd">
<td><p><em>FriendlyName</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Nome atribuído pelo usuário que facilita a identificação do certificado.</p></td>
</tr>
<tr class="even">
<td><p><em>GlobalCatalog</em></p></td>
<td><p>Opcional</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>FQDN de um servidor de catálogo global em seu domínio. O parâmetro não será necessário se o cmdlet <strong>Request-CsCertificate</strong> estiver sendo executado em um computador com uma conta em seu domínio.</p></td>
</tr>
<tr class="odd">
<td><p><em>GlobalSettingsDomainController</em></p></td>
<td><p>Opcional</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>FQDN de um controlador de domínio no qual as configurações globais serão armazenadas. Se as configurações globais forem armazenadas no contêiner System do Serviços de Domínio Active Directory, este parâmetro deverá apontar para o controlador de domínio raiz. Se as configurações globais forem armazenadas no contêiner Configuration, qualquer controlador de domínio pode ser usado e o parâmetro pode ser omitido.</p></td>
</tr>
<tr class="even">
<td><p><em>KeyAlg</em></p></td>
<td><p>Opcional</p></td>
<td><p>Microsoft.Rtc.Management.Deployment.X509Certificates.KeyAlgorithmIdentifier</p></td>
<td><p>Indica o tipo de algoritmo criptográfico a ser usado na geração das chaves públicas e privadas do novo certificado. Algoritmos de chave válidos incluem:</p>
<p>RSA</p>
<p>ECDH_P256</p>
<p>ECDH_P384</p>
<p>ECDH_P521</p></td>
</tr>
<tr class="odd">
<td><p><em>KeySize</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Int32</p></td>
<td><p>Indica o tamanho (em bits) da chave privada usada pelo certificado. Chaves com tamanhos maiores são mais seguras, mas exigem mais sobrecarga de processamento para sua descriptografia.</p>
<p>Os tamanhos de chave válidos são 1024, 2048 e 4096. Por exemplo: -KeySize 2048.</p></td>
</tr>
<tr class="even">
<td><p><em>Organization</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Nome da organização que está solicitando o novo certificado. Por exemplo: -Organization &quot;Litwareinc&quot;.</p></td>
</tr>
<tr class="odd">
<td><p><em>OU</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Unidade organizacional do Active Directory para o computador ao qual o novo certificado será atribuído.</p></td>
</tr>
<tr class="even">
<td><p><em>Output</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Caminho para o arquivo do certificado. Caso queira criar uma solicitação de certificado offline, use o parâmetro Output e especifique um caminho de arquivo para a solicitação de certificado; por exemplo: -Output C:\Certificates\NewCertificate.pfx. Isso criará um arquivo de solicitação de certificado que pode ser enviado por email a uma autoridade de certificação para processamento.</p></td>
</tr>
<tr class="odd">
<td><p><em>PrivateKeyExportable</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Boolean</p></td>
<td><p>Defina este parâmetro como True se quiser tornar exportável a chave privada do certificado. Quando uma chave privada é exportável, o certificado pode ser copiado e usado em vários computadores.</p></td>
</tr>
<tr class="even">
<td><p><em>Report</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Permite especificar um caminho de arquivo para o arquivo de log criado quando o cmdlet é executado. Por exemplo: -Report &quot;C:\Logs\Certificates.html&quot;</p></td>
</tr>
<tr class="odd">
<td><p><em>RequestId</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Int32</p></td>
<td><p>Número de identificação associado a uma solicitação de certificado. O parâmetro RequestID oferece uma maneira de listar, recuperar ou limpar um certificado individual.</p></td>
</tr>
<tr class="even">
<td><p><em>State</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Estado dos EUA no qual o certificado será implementado. Por exemplo: -State WA.</p></td>
</tr>
<tr class="odd">
<td><p><em>Template</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Indica o modelo de certificado a ser usado na geração de um novo certificado, como por exemplo: -Template &quot;WebServer&quot;. O modelo solicitado deve estar instalado na autoridade de certificação. Observe que o valor digitado deve ser o nome do modelo, e não o nome para exibição do modelo.</p></td>
</tr>
<tr class="even">
<td><p><em>WhatIf</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Descreve o que aconteceria se o comando fosse executado sem ser executado de fato.</p></td>
</tr>
</tbody>
</table>


## Tipos de entrada

Nenhuma. O cmdlet **Request-CsCertificate** não aceita entrada em pipeline.

## Tipos de retorno

Nenhuma. Em vez disso, o cmdlet **Request-CsCertificate** ajuda a gerenciar instâncias do objeto Microsoft.Rtc.Management.Deployment.CertificateReference.

## Consulte Também

#### Outros Recursos

[Get-CsCertificate](get-cscertificate.md)  
[Import-CsCertificate](import-cscertificate.md)  
[Remove-CsCertificate](remove-cscertificate.md)  
[Set-CsCertificate](set-cscertificate.md)

