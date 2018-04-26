---
title: Planejamento para a autenticação de dois fatores
TOCTitle: Planejamento para a autenticação de dois fatores
ms:assetid: 16f08710-8961-4659-acbf-ebb95a198fb4
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn308562(v=OCS.15)
ms:contentKeyID: 56270375
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Planejamento para a autenticação de dois fatores

 

_**Tópico modificado em:** 2016-12-08_

Veja a seguir uma lista de pontos de implantação que devem ser levados em consideração durante a configuração de um ambiente Microsoft Lync Server 2013 que suporte autenticação de dois fatores.

## Suporte de Cliente

As Atualizações Cumulativas do Lync 2013 para o Lync Server 2013: o cliente de desktop de julho de 2013 é o único cliente do Lync compatível com a autenticação de dois fatores.

## Requisitos de topologia

Recomendamos que nossos clientes implantem a autenticação de dois fatores usando o Lync Server 2013 dedicado com as Atualizações Cumulativas para o Lync Server 2013: Pools de Edge, Diretores e Usuários de julho de 2013. Para habilitar a autenticação passiva para usuários do Lync, é necessário desabilitar outros métodos de autenticação para outras funções e serviços, tais como:


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Tipo de configuração</th>
<th>Tipo de serviço</th>
<th>Função do servidor</th>
<th>Tipo de autenticação a ser desabilitada</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Serviço Web</p></td>
<td><p>WebServer</p></td>
<td><p>Diretor</p></td>
<td><p>Kerberos, NTLM e Certificado</p></td>
</tr>
<tr class="even">
<td><p>Serviço Web</p></td>
<td><p>WebServer</p></td>
<td><p>Front End</p></td>
<td><p>Kerberos, NTLM e Certificado</p></td>
</tr>
<tr class="odd">
<td><p>Proxy</p></td>
<td><p>EdgeServer</p></td>
<td><p>Edge</p></td>
<td><p>Kerberos e NTLM</p></td>
</tr>
<tr class="even">
<td><p>Proxy</p></td>
<td><p>Registrador</p></td>
<td><p>Front End</p></td>
<td><p>Kerberos e NTLM</p></td>
</tr>
</tbody>
</table>


A não ser que esses tipos de autenticação estejam desabilitados no nível de serviço, todas as outras versões do cliente do Lync não conseguirão se conectar enquanto a autenticação de dois fatores estiver habilitada em sua implantação.

## Descoberta de Serviços do Lync

Os registros de DNS usados pelos clientes internos e/ou externos para descobrir serviços do Lync devem ser configurados para resolver um servidor do Lync que não esteja habilitado para a autenticação de dois fatores. Com esta configuração, os usuários dos Pools do Lync que não estão habilitados para a autenticação de dois fatores não precisarão informar um PIN para fins de autenticação, ao passo que os usuários de Pools do Lync que estão habilitados para a autenticação de dois fatores serão obrigados a informar seus PINs para fins de autenticação.

## Autenticação do Exchange

Os clientes que implantaram a autenticação de dois fatores para o Microsoft Exchange podem descobrir que alguns recursos no cliente do Lync estão indisponíveis. No momento, isso ocorre devido ao projeto, já que o cliente do Lync não é compatível com a autenticação de dois fatores para recursos que dependem da integração do Exchange.

## Contatos do Lync

Os usuários do Lync configurados para usar o recurso de Armazenamento Unificado de Contatos descobrirão que seus contatos não estão mais disponíveis após a conexão com a autenticação de dois fatores.

Recomendamos usar o cmdlet **Invoke-CsUcsRollback** para remover contatos de usuários antigos do Armazenamento Unificado de Contatos e armazená-los no Lync Server 2013 antes de habilitar a autenticação de dois fatores.

## Pesquisa de Habilidades

Os clientes que configuraram o recurso de Pesquisa de Habilidades no ambiente Lync descobrirão que este recurso não funciona quando o Lync está habilitado para a autenticação de dois fatores. Isso ocorre devido ao projeto, já que o Microsoft SharePoint não é compatível com a autenticação de dois fatores.

## Credenciais do Lync

Há várias considerações de implantação que envolvem as credenciais salvas do Lync que podem afetar usuários configurados para usar a autenticação de dois fatores.

## Exclusão de Credenciais Salvas

Os usuários devem usar a opção **Excluir informações de entrada** no cliente do Lync e excluir a pasta do perfil SIP de %localappdata%\\Microsoft\\Office\\15.0\\Lync antes de tentar se conectar pela primeira vez usando a autenticação de dois fatores.

## DisableNTCredentials

Com o método de autenticação Kerberos ou NTLM, as credenciais do Windows do usuário são usadas automaticamente para fins de autenticação. Em uma implantação típica do Lync Server 2013, onde o Kerberos e/ou NTLM estão habilitados para autenticação, os usuários não devem ter de informar suas credenciais a cada vez que se conectam.

Se as credenciais dos usuários forem inadvertidamente solicitadas antes de ser necessário informar o PIN, a chave de registro **DisableNTCredentials** pode estar configurada por engano nos computadores clientes, possivelmente através de uma Política de Grupo.

Para evitar outras solicitações de credenciais, crie a seguinte entrada de registro na estação de trabalho local ou use o modelo administrativo do Lync para ser aplicado a todos os usuários para um determinado pool usando a Política de Grupo:

HKEY\_LOCAL\_MACHINE\\Software\\Policies\\Microsoft\\Office\\15.0\\Lync

REG\_DWORD: DisableNTCredentials

Value: 0x0

## SavePassword

Ao se conectar ao Lync pela primeira vez, o usuário tem a opção de salvar sua senha. Em caso positivo, o certificado de cliente do usuário fica armazenado no armazenamento de certificado pessoal e as credenciais do Windows do usuário ficam armazenadas no Gerenciador de Credenciais do computador local.

A configuração de registro **SavePassword** deve estar desabilitada quando o Lync estiver configurado para dar suporte à autenticação de dois fatores. Para evitar que os usuários salvem suas senhas, altere a seguinte entrada de registro na estação de trabalho local ou use o modelo administrativo do Lync para ser aplicado a todos os usuários para um determinado pool usando a Política de Grupo:

HKEY\_CURRENT\_USER\\Software\\Microsoft\\Office\\15.0\\Lync

REG\_DWORD: SavePassword

Value: 0x0

## AD FS 2.0 Token Replay

O AD FS 2.0 oferece um recurso chamado detecção de repetição de token, pelo qual é possível detectar várias solicitações de token que usam o mesmo token a fim de descartá-las. Quanto este recurso está habilitado, a detecção de repetição de token protege a integridade das solicitações de autenticação tanto no perfil passivo do WS-Federation quanto no perfil de SAML WebSSO, certificando-se de que o mesmo token nunca é usado mais de uma vez.

Esse recurso deve ser habilitado em situações em que há grandes preocupações com a segurança, como quando se usa quiosques. Para obter mais informações sobre a detecção de repetição de token, consulte Práticas recomendadas para o planejamento e a implantação seguros do AD FS 2.0 em [http://go.microsoft.com/fwlink/p/?LinkId=309215](http://go.microsoft.com/fwlink/p/?linkid=309215).

## Acesso de usuários externos

Estes tópicos não contemplam a configuração de um proxy ADFS ou um proxy reverso para suportar a autenticação de dois fatores do Lync a partir de redes externas.

