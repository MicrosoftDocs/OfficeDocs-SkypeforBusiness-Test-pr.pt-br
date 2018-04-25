---
title: Classes e descrições de esquema no Lync Server 2013
TOCTitle: Classes e descrições de esquema no Lync Server 2013
ms:assetid: 7d43b920-ac37-40cc-adfe-be289bda6e9e
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398625(v=OCS.15)
ms:contentKeyID: 49307242
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Classes e descrições de esquema no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

Esta seção descreve todas as classes de esquema usadas pelo Lync Server 2013.

## Classes e descrições de esquema


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Classe</th>
<th>Descrição</th>
<th>Comentários</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Destinatário do email</p></td>
<td><p>Unificação de Mensagens (UM) do Exchange destinatário de e-mail.</p></td>
<td><p>Essa classe auxiliar é compartilhada com UM do Exchange.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-ApplicationContacts</p></td>
<td><p>Esta classe é um contêiner para vários contatos de aplicativo e não contém atributos próprios.</p></td>
<td><p>Novo no Microsoft Office Communications Server 2007 R2.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-ApplicationServer</p></td>
<td><p>Esta classe contém a entrada para o ponto de controle de serviço a uma instância de UCAS (serviços de aplicativos de comunicação unificados).</p></td>
<td><p>Novo no Office Communications Server 2007 R2.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-ApplicationServerService</p></td>
<td><p>Essa classe fornece uma associação de um pool específico para o seu Serviço de aplicativos.</p></td>
<td><p>Novo no Communications Server 2007 R2.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-ApplicationServerSettings</p></td>
<td><p>Essa classe auxiliar para msRTCSIP-ApplicationServer contém atributos que representam as configurações de instâncias de Serviço de aplicativos.</p></td>
<td><p>Novo no Communications Server 2007 R2.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-Archive (obsoleto)</p></td>
<td><p>Esta classe auxiliar de msRTCSIP-GlobalContainer contém todas as configurações relacionadas ao arquivamento.</p></td>
<td><p>Obsoleto no Lync Server 2010.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-ArchivingServer (obsoleto)</p></td>
<td><p>Esta classe representa um único servidor de arquivamento de mensagens de instantâneas. Uma instância dessa classe é criada quando um computador é ativado como um servidor de arquivamento de mensagens de instantâneas, como um computador com o serviço de arquivamento de mensagens instantâneas instalado.</p></td>
<td><p>Obsoleto no Lync Server 2010.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-ConferenceDirectories</p></td>
<td><p>Esta classe é um contêiner para várias instâncias de diretórios de conferência e não contém atributos próprios.</p></td>
<td><p>Novo no Communications Server 2007 R2.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-ConferenceDirectory</p></td>
<td><p>Esta classe contém atributos que representam configurações de um diretório de conferência específico.</p></td>
<td><p>Novo no Communications Server 2007 R2.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-ConnectionPoint</p></td>
<td><p>Ponto de controle de serviço (SCP) genérico para especificar o computador como um servidor executando o Lync Server.</p></td>
<td><p>Novo no Lync 2010.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-DefaultCWABank</p></td>
<td><p>Esta classe auxiliar contém as configurações para um banco Microsoft Lync Web App.</p></td>
<td><p>Novo no Communications Server 2007 R2.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-Domain</p></td>
<td><p>Esta classe contém os atributos que definem os domínios configurados do registrador SIP.</p></td>
<td><p>-</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-EdgeProxy</p></td>
<td><p>Este recipiente classe representa um único Serviço de Borda de Acesso. Como um Serviço de Borda de Acesso é implantado no perímetro da rede e os clientes geralmente não permitem o Serviços de Domínio Active Directory acesso à rede de perímetro, as instâncias de Serviço de Borda de Acesso não fazem parte de rede do Active Directory da intranet. Portanto, os Proxies de acesso não são automaticamente registrados no AD DS. O administrador deve configurar manualmente a existência de cada instância de Serviço de Borda de Acesso no AD DS.</p></td>
<td><p>-</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-EnterpriseMCUSettings</p></td>
<td><p>Esta classe auxiliar de msRTCSIP-MCU contém atributos que representam configurações de servidores de conferência.</p></td>
<td><p>Novo no Microsoft Office Communications Server 2007.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-EnterpriseMediationServerSettings</p></td>
<td><p>Esta classe auxiliar de msRTCSIP-MediationServer contém atributos que representam configurações de Servidores de Mediação.</p></td>
<td><p>Novo no Office Communications Server 2007.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-EnterpriseServerSettings</p></td>
<td><p>Esta classe auxiliar de msRTCSIP-Server contém atributos que representam configurações de servidores SIP.</p></td>
<td><p>-</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-Federation</p></td>
<td><p>Esta classe auxiliar de msRTCSIP-GlobalContainer contém todas as configurações relacionadas à federação.</p></td>
<td><p>-</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-GlobalContainer</p></td>
<td><p>Esta classe contém todas as configurações que se aplicam em uma Lync Server implantação.</p></td>
<td><p>-</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-GlobalUserPolicy (obsoleto)</p></td>
<td><p>Esta classe representa uma única Office Communications Server política de reunião.</p></td>
<td><p>Obsoleto no Lync Server 2010.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-GlobalTopologySetting</p></td>
<td><p>O objeto de configuração da topologia global local.</p></td>
<td><p>Novo no Lync Server 2010.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-GlobalTopologySettings</p></td>
<td><p>Container para manter os objetos de configuração da topologia global.</p></td>
<td><p>Novo no Lync Server 2010.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-LocalNormalization</p></td>
<td><p>Esta classe é um contêiner que representa uma instância de uma regra de normalização de local.</p></td>
<td><p>-</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-LocationContactMapping</p></td>
<td><p>Essa classe é criada pelo Aplicativo Atendedor de Conferência e retém os atributos usados para categorizar os números de telefone de conferência por região.</p></td>
<td><p>Novo no Communications Server 2007 R2.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-LocationContactMappings</p></td>
<td><p>Esta classe é um contêiner para várias instâncias de mapeamentos de contato de localização e não contém atributos próprios.</p></td>
<td><p>Novo no Communications Server 2007 R2.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-LocationProfile</p></td>
<td><p>Esta classe é um contêiner que representa um perfil de localidade específico.</p></td>
<td><p>-</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-LocationProfiles (obsoleto)</p></td>
<td><p>Esta classe é um contêiner para vários perfis de localidade e não contém atributos próprios.</p></td>
<td><p>Obsoleto no Lync Server 2010.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-LocalNormalizations (obsoleto)</p></td>
<td><p>Esta classe é um contêiner para várias regras de normalização de local e não contém atributos próprios.</p></td>
<td><p>Obsoleto no Lync Server 2010.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-MCU</p></td>
<td><p>Esta classe representa um único servidor de conferência.</p></td>
<td><p>Novo no Communications Server 2007.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-MCUFactories</p></td>
<td><p>Esta classe contém várias classes msRTCSIP-MCUFactory e não tem atributos próprios.</p></td>
<td><p>Novo no Communications Server 2007.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-MCUFactory</p></td>
<td><p>Essa classe é um contêiner que representa uma fábrica de servidor de conferência para um único tipo de mídia. Uma instância dessa classe é criada quando o primeiro servidor de conferência para este tipo e fornecedor específicos é ativado.</p></td>
<td><p>Novo no Communications Server 2007.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-MCUFactoryService</p></td>
<td><p>Esta classe fornece uma associação de um pool específico com o respectivo Alocador de Servidores de Conferência.</p></td>
<td><p>Novo no Communications Server 2007.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-MediationServer</p></td>
<td><p>Esta classe contém a entrada do ponto de controle de serviço de um Servidor de Mediação.</p></td>
<td><p>Novo no Communications Server 2007.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-Meeting (obsoleto)</p></td>
<td><p>Esta classe auxiliar de msRTCSIP-GlobalContainer contém atributos que representam configurações de reunião que podem ser definidas.</p></td>
<td><p>Obsoleto no Lync Server 2010.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-Mobility</p></td>
<td><p>Contâiner que armazena as configurações de mobilidade global.</p></td>
<td><p>-</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-MonitoringServer</p></td>
<td><p>Esta classe contém atributos que representam as configurações para um único Servidor de Monitoramento.</p></td>
<td><p>Novo no Communications Server 2007 R2.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-PhoneRoute (obsoleto)</p></td>
<td><p>Esta classe é um contêiner que representa uma instância de uma rota de custo mínimo para um gateway ou um conjunto de gateways. Essa informação é usada por todos os pools Enterprise ou servidores executando o Standard Edition para rotear chamadas de saída à rede telefônica pública comutada (PSTN) da maneira mais econômica.</p></td>
<td><p>Obsoleto no Lync Server 2010.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-PhoneRoutes (obsoleto)</p></td>
<td><p>Esta classe é um contêiner para várias rotas econômicas e não contém atributos próprios.</p></td>
<td><p>Obsoleto no Lync Server 2010.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-Policies (obsoleto)</p></td>
<td><p>Esta classe contém várias Lync Server classes de política e não tem quaisquer atributos próprios.</p></td>
<td><p>Obsoleto no Lync Server 2010.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-Pool</p></td>
<td><p>Esta classe representa um único Lync Server pool.</p></td>
<td><p>-</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-Pools</p></td>
<td><p>Esta classe contém vários Lync Server pools e não tem quaisquer atributos próprios.</p></td>
<td><p>-</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-PoolService</p></td>
<td><p>Esta classe representa o ponto de controle de serviço de um pool. Os usuários hospedados em um pool têm o seu ponto de atributo msRTCSIP-PrimaryHomeServer a uma instância desta classe.</p></td>
<td><p>-</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-Presence</p></td>
<td><p>Contâiner que armazena as configurações de presença global.</p></td>
<td><p>-</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-Registrar</p></td>
<td><p>Esta classe auxiliar de msRTCSIP-GlobalContainer contém atributos que representam configurações de usuário mantidas pelos servidores do registrador SIP.</p></td>
<td><p>-</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-RouteUsage (obsoleto)</p></td>
<td><p>Esta classe é um contêiner que representa uma instância de uso de uma rota telefônica. Uma classe de rota de uso telefônica consiste em um campo de atributo e um campo de descrição. O campo de atributo define um tipo de uso. O campo da descrição permite que os administradores descrever o uso para este atributo na rota telefônica.</p></td>
<td><p>Obsoleto no Lync Server 2010.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-RouteUsages (obsoleto)</p></td>
<td><p>Esta classe contém várias instâncias da classe msRTCSIP-RouteUsage e não tem atributos próprios.</p></td>
<td><p>Obsoleto no Lync Server 2010.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-Search</p></td>
<td><p>Esta classe auxiliar de msRTCSIP-GlobalContainer contém atributos que limitam e controlam o escopo dos resultados da pesquisa.</p></td>
<td><p>-</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-Server</p></td>
<td><p>Esta classe representa um único servidor executando Lync Server.</p></td>
<td><p>-</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-Service</p></td>
<td><p>Esta classe contém o contêiner de configurações globais e os objetos msRTCSIP-Domain.</p></td>
<td><p>-</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-TrustedMCU</p></td>
<td><p>Esta classe contém atributos que representam configurações de um único servidor de conferência confiável.</p></td>
<td><p>Novo no Communications Server 2007.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-TrustedMCUs</p></td>
<td><p>Esta classe contém várias instâncias da classe msRTCSIP-TrustedMCU e não tem atributos próprios.</p></td>
<td><p>Novo no Communications Server 2007.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-TrustedProxies</p></td>
<td><p>Esta classe contém várias classes msRTCSIP-TrustedProxy e não tem atributos próprios.</p></td>
<td><p>Novo no Communications Server 2007.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-TrustedProxy</p></td>
<td><p>Essa classe é um contêiner que representa um servidor executando o servidor Proxy. Uma instância desta classe é criada ao ativar um novo servidor de Proxy em um computador associado ao AD DS.</p></td>
<td><p>Novo no Communications Server 2007.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-TrustedServer</p></td>
<td><p>Esta classe contém atributos que representam configurações de um único servidor confiável.</p></td>
<td><p>-</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-TrustedService</p></td>
<td><p>Esta classe é um contêiner que representa um serviço confiável que é roteável usando um URI de operador usuário de encaminhamento global (GRUU). Uma instância dessa classe é criada quando um novo servidor que é confiável por Lync Server está ativado. O servidor confiáve deve ser associado a um domínio Active Directory.</p></td>
<td><p>Novo no Communications Server 2007.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-TrustedServices</p></td>
<td><p>Esta classe é um contêiner para vários servidores GRUU e não contém atributos próprios.</p></td>
<td><p>Novo no Communications Server 2007.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-TrustedWebComponentsServer</p></td>
<td><p>Esta classe contém atributos que representam as configurações de um componente da web confiável.</p></td>
<td><p>Novo no Communications Server 2007.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-TrustedWebComponentsServers</p></td>
<td><p>Esta classe contém várias instâncias da classe msRTCSIP-TrustedWebComponentServer e não tem atributos próprios.</p></td>
<td><p>Novo no Communications Server 2007.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-UnifiedCommunications (obsoleto)</p></td>
<td><p>Esta classe auxiliar de msRTCSIP-GlobalContainer contém atributos relacionados à comunicação unificada.</p></td>
<td><p>Obsoleto no Lync Server 2010.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-WebComponents</p></td>
<td><p>Esta classe contém o ponto de controle do serviço IIS (Internet Information Server). Ele identifica um servidor como um servidor de componentes web.</p></td>
<td><p>Novo no Communications Server 2007.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-WebComponentsService</p></td>
<td><p>Esta classe fornece uma associação de um pool específico com os componentes web que ele usará.</p></td>
<td><p>Novo no Communications Server 2007.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-WebComponentSettings</p></td>
<td><p>Esta classe auxiliar de msRTCSIP-WebComponents contém atributos que representam configurações de componentes web.</p></td>
<td><p>Novo no Communications Server 2007.</p></td>
</tr>
</tbody>
</table>

