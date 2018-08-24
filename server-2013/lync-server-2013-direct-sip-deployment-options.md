---
title: 'Lync Server 2013: Opções de implantação de SIP Direto'
TOCTitle: Opções de implantação de SIP Direto
ms:assetid: 84691944-03f2-4a89-9f2b-1ab3d7f388cc
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398672(v=OCS.15)
ms:contentKeyID: 49307318
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Opções de implantação de SIP Direto no Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

Este tópico apresenta exemplos de topologias para a implantação de conexões SIP diretas.

## Lync Server autônomo

Se a sua organização usa uma das implantações descritas nesta seção, você pode usar Lync Server 2013 como solução de telefonia exclusivamente para uma empresa ou uma parte dela. Esta seção descreve as seguintes implantações detalhadamente:

  - **Implantação incremental:** esta opção pressupõe que você tenha uma infraestrutura de PBX existente e pretende apresentar o Enterprise Voice incrementalmente para grupos ou equipes menores na sua organização.

  - **Implantação somente de VoIP do Lync Server:** esta opção pressupõe que você considera implantar o Enterprise Voice em um site sem infraestrutura de telefonia tradicional.

## Implantação Incremental

Na implantação incremental, o Lync Server 2013 é a única solução de telefonia para equipes individuais ou departamentos, enquanto o restante dos usuários em uma organização continuam a usar PBX. Essa estratégia de implantação incremental é uma maneira de introduzir a telefonia IP em sua empresa através de programas piloto controlados. Os grupos de trabalho cujas necessidades de comunicação estão melhor atendidas pela Microsoft Unified Communications são transferidos para o Enterprise Voice, enquanto outros usuários permanecem no PBX existente. Os grupos de trabalho adicionais podem migrar para o Enterprise Voice conforme necessário.

A opção incremental é recomendada se você tem grupos de usuários claramente definidos que têm requisitos de comunicação em comum e que se prestam para gerenciamento centralizado. Essa opção também é eficiente se você tiver equipes ou departamentos espalhados em grandes áreas geográficas, pois a economia em tarifas interurbanas pode ser significativa. Na verdade, esta opção é útil para criar equipes virtuais cujos membros podem estar espalhados por todo o mundo. É possível criar, corrigir ou dispersar tais equipes em resposta rápida às necessidades inconstantes dos negócios.

A figura a seguir mostra a topologia genérica para a implantação do Enterprise Voiceatrás de um PBX. Esta é a topologia recomendada para a implantação incremental.

**Opção de implantação incremental**

![Diagrama de opção da migração por departamento](images/Gg398672.e951ecf4-7cd2-425a-9106-76977492d682(OCS.15).jpg "Diagrama de opção da migração por departamento")

> [!NOTE]  
> Se estiver conectando a implantação do Lync Server a um parceiro certificado de SIP direto, não será necessário usar o gateway da PSTN (rede telefônica pública comutada) entre o Servidor de Mediação e o PBX. Para obter uma lista de parceiros certificados de SIP direto, consulte o site do programa de interoperabilidade aberta Microsoft Unified Communications em <a href="http://go.microsoft.com/fwlink/p/?linkid=203309">http://go.microsoft.com/fwlink/p/?linkId=203309</a>.

> [!NOTE]  
> O caminho de mídia mostrado nesta figura possui um bypass de mídia habilitado (a configuração recomendada). Se você optar por desabilitar o bypass de mídia, o caminho de mídia é direcionado pelo Servidor de Mediação.

Nessa topologia, os departamentos ou grupos de trabalho selecionados são habilitados para o Enterprise Voice. Um gateway PSTN vincula o grupo de trabalho habilitado para VoIP ao PBX. Os usuários que estão habilitados para o Enterprise Voice, incluindo funcionários remotos, comunicam-se através da rede IP. As chamadas de usuários do Enterprise Voice ao PSTN e a colegas de trabalho que não estão habilitados para o Enterprise Voice são encaminhadas para o gateway PSTN adequado. As chamadas de colegas que ainda estão no sistema PBX ou de chamadores no PSTN, são encaminhadas para o gateway PSTN, que as encaminha ao Lync Server para roteamento.

Há duas configurações recomendadas para a conexão de Enterprise Voice a uma infra-estrutura de PBX existente para interoperabilidade: o Enterprise Voice atrás de PBX e o Enterprise Voice na frente do PBX.

## Enterprise Voice atrás do PBX

Quando o Enterprise Voice é implantado atrás de PBX, todas as chamadas de PSTN chegam ao PBX, o que roteia as chamadas aos usuários do Enterprise Voice a um gateway PSTN e chama usuários do PBX ao PBX.

## Enterprise Voice na frente do PBX

Quando o Enterprise Voice é implantado na frente do PBX, todas as chamadas chegam ao gateway PSTN, o que roteia as chamadas para os usuários do Enterprise Voice ao Lync Server e chamadas para usuários do PBX ao PBX. As chamadas de PSTN do Enterprise Voice e dos usuários de PBX são roteadas pela rede IP para o gateway PSTN mais econômico. A tabela a seguir mostra as vantagens e desvantagens dessa configuração.

### Vantagens e desvantagens de implantar o Enterprise Voice na frente do PBX

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Vantagens</th>
<th>Desvantagens</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>O PBX ainda serve aos usuários não habilitados para o Enterprise Voice.</p></td>
<td><p>Os gateways existentes podem não suportar os recursos ou capacidade que você deseja.</p></td>
</tr>
<tr class="even">
<td><p>O PBX lida com todos os dispositivos anteriores.</p></td>
<td><p>Requer um tronco de gateway para o PBX e de gateway para o Servidor de Mediação. Você pode precisar de mais troncos do provedor de serviço.</p></td>
</tr>
<tr class="odd">
<td><p>Os usuários do Enterprise Voice mantém os mesmos números de telefone.</p></td>
<td><p> </p></td>
</tr>
</tbody>
</table>


## Implantação de somente VoIP do Lync Server

O Enterprise Voice oferece novos negócios e até mesmo novos sites de escritório para empresas existentes, com a oportunidade de implementar uma solução de VoIP completa sem a necessidade de se preocupar com a integração de PBX ou incorrer em custos substanciais de implantação e manutenção de infraestrutura de PBX IP. Esta solução oferece suporte a funcionários locais e remotos.

Nesta implantação, todas as chamadas são roteadas pela rede IP. As chamadas ao PSTN são roteadas para o gateway PSTN adequado. O Lync 2013 ou o Lync Phone Edition serve como um softphone. O controle de chamada remota não está disponível e é desnecessário, porque não há telefones PBX para os usuários do controle. Os serviços de atendedor automático e correio de voz estão disponíveis através da implantação opcional do Unificação de Mensagens (UM) do Exchange.

> [!NOTE]  
> Além da infra-estrutura de rede necessária para oferecer suporte ao Lync Server 2013, uma implantação de somente VoIP pode usar um gateway pequeno, qualificado para dar suporte a dispositivos analógicos e máquinas de fax.

A figura a seguir mostra uma topologia típica de uma implantação de somente VoIP.

**Opção de implantação de somente VoIP**

![Opção de implantação Greenfidle](images/Gg398672.820dc5fe-0e20-431b-ae4e-fefdf2221d3b(OCS.15).jpg "Opção de implantação Greenfidle")

> [!NOTE]  
> O caminho de mídia mostrado nesta figura possui um bypass de mídia habilitado (a configuração recomendada). Se você optar por desabilitar o bypass de mídia, o caminho de mídia é direcionado pelo Servidor de Mediação.
