---
title: 'Lync Server 2013: Soluções de resiliência do site de filial'
TOCTitle: Soluções de resiliência do site de filial
ms:assetid: 1700f99b-709c-4e47-88eb-c0a5490e26e2
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398234(v=OCS.15)
ms:contentKeyID: 49306002
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Soluções de resiliência do site de filial no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

Existem vantagens explícitas em fornecer resiliência de locais de filial à sua organização. Especificamente, se você perder a conexão com o local central, os usuários da filial continuarão tendo o serviço Enterprise Voice e a caixa postal (se você definir configurações de redirecionamento da caixa postal. Para obter detalhes, consulte [Requisitos de resiliência do site da filial para Lync Server 2013](lync-server-2013-branch-site-resiliency-requirements.md)). Entretanto, para locais com menos de 25 usuários, a solução de resiliência pode não gerar retorno do investimento.

Se decidir fornecer a resiliência do site de filial, você tem três opções. Use a tabela a seguir para ajudá-lo a determinar qual opção é a melhor para sua organização.



<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Se você…</th>
<th>Recomendamos que você use um(a)…</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Hospede entre 25 e 1.000 usuários no seu site de filial se o retorno sobre o investimento não suportar uma implantação completa ou em um local em que o suporte administrativo não estiver disponível</p></td>
<td><p>Aparelho de Filial Persistente</p>
<p>O Aparelho de Filial Persistente é um servidor blade com base no setor com um Registrador Lync Server e um Servidor de Mediação em execução no Windows Server 2008 R2. O Aparelho de Filial Persistente também contém um gateway PSTN (rede telefônica pública comutada). Dispositivos qualificados de terceiros (desenvolvidos pelos parceiros da Microsoft no programa de qualificação/certificação SBA [aparelho de filial persistente]) fornece uma conexão PSTN contínua caso uma WAN falhe, mas essa abordagem não fornece a presença e a conferência resilientes porque esses recursos dependem do servidores Front-End no site central.</p>
<p>Para detalhes sobre os Aparelho de Filial Persistente, consulte &quot;Detalhes do Aparelho de Filial Persistente&quot; mais adiante neste tópico.</p>
<p><strong>Observação:</strong> se você também decidir usar um tronco SIP com seu Aparelho de Filial Persistente, entre em contato com seu fornecedor de Aparelho de Filial Persistente para aprender sobre qual é o melhor provedor de serviço para a sua organização.</p></td>
</tr>
<tr class="even">
<td><p>Hospede entre 1.000 e 2.000 usuários no seu site de filial, com falta de uma conexão de WAN resiliente e tendo treinado administradores do Lync Server disponíveis</p></td>
<td><p>Servidor de Filial Persistente ou dois Aparelho de Filial Persistente.</p>
<p>O Servidor de Filial Persistente é um Windows Server que atende a requisitos de hardware específicos e que possui um software Registrador do Lync Server e um Servidor de Mediação instalado nele. Ele deve ser conectado a um gateway PSTN ou a um tronco SIP a um provedor de serviço telefônico.</p>
<p>Para obter detalhes sobre o Servidor de Filial Persistente, consulte &quot;Detalhes do Servidor de Filial Persistente&quot; mais adiante neste tópico.</p></td>
</tr>
<tr class="odd">
<td><p>Se você requer recursos de presença e de conferência além dos recursos de voz para até 5.000 usuários e treinou administradores do Lync Server disponíveis</p></td>
<td><p>Implante como um site central com um servidor Standard Edition e não como um site de filial.</p>
<p>Uma implantação do Lync Server de escala total fornece uma conexão PSTN contínua e presença e conferência resiliente no caso de uma falha de WAN.</p>
<p>Para obter detalhes sobre a preparação para essa solução, consulte <a href="lync-server-2013-planning-for-your-organization.md">Planejamento de organização para Lync Server 2013</a>, <a href="lync-server-2013-determining-your-system-requirements.md">Determinando seus requisitos de sistema para Lync Server 2013</a>, <a href="lync-server-2013-determining-your-infrastructure-requirements.md">Determinando seus requisitos de infraestrutura para Lync Server 2013</a>, e outras seções relevantes da documentação de Planejamento.</p></td>
</tr>
</tbody>
</table>


## Topologia de resiliência

A figura a seguir mostra as topologias recomendadas para a resiliência do site de filial.

**Opções de resiliência do site de filial**

![Opções de resiliência da ramificação de voz](images/Gg398234.47eecd19-08ae-4d82-acbe-61f0de760306(OCS.15).jpg "Opções de resiliência da ramificação de voz")

## Detalhes do aparelho de filial persistente

O aparelho de filial persistente do Lync Server inclui os componentes a seguir:

  - Um Registrador para a autenticação do usuário, registro e roteamento de chamada

  - Um Servidor de Mediação para a manipulação de sinalização entre o Registrador e o gateway PSTN

  - Um gateway PSTN para o roteamento de chamadas ao PSTN como um transporte fallback no caso de uma interrupção da WAN

  - SQL Server Express para armazenamento de dados do usuário local

O Aparelho de Filial Persistente também inclui troncos PSTN, portas análogas e uma adaptador de Ethernet.

Se a conexão WAN do site de filial a um site central se tornar indisponível, os usuários internos de filia continuam registrados com o Registrador do Aparelho de Filial Persistente e obtêm o serviço ininterrupto de voz ao usarem a conexão do Aparelho de Filial Persistente com a PSTN. Os usuários do site de filial que se conectam de casa ou de outro locais remotos serão capazes de se registrar com um servidor Registrador em um site central quando um link de WAN ao site de filial estiver indisponível. Esses usuários terão a funcionalidade de comunicações completamente unificadas com única exceção de que as chamadas de entrada ao site de filial irão para a caixa postal. Quando a conexão WAN voltar a ficar disponível, a funcionalidade total deve ser restabelecida aos usuários do site de filial. Nem o failover ao Aparelho de Filial Persistente nem a restauração do serviço requer a presença de um administrador de TI.

O Lync Server suporta até dois Aparelho de Filial Persistente em um site de filial.

## Visão geral de implantação de aparelho de filial persistente

O Aparelho de Filial Persistente é fabricado por fabricantes de equipamento original em associação à Microsoft e implantado em nome desta por varejistas de valor agregado. Essa implantação só deve ocorrer depois de o Lync Server ter sido implantado no site central, uma conexão WAN ao site de filiar está em vigor, e os usuários do site de filial estão habilitados para o Enterprise Voice.

Para obter detalhes sobre essas fases, consulte [Implantando Aplicativo ou Servidor de Filial Persistente com Lync Server 2013](lync-server-2013-deploying-a-survivable-branch-appliance-or-server.md) na documentação de Implantação.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Fase</th>
<th>Etapas</th>
<th>Direitos do usuário</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Instalar serviços de domínio do Active Directory para o Aparelho de Filial Persistente</p></td>
<td><p><strong>No site central:</strong></p>
<ol>
<li><p>Crie uma conta de usuário de domínio (ou uma identidade corporativa) para o técnico que for instalar e ativar o Aparelho de Filial Persistente no site de filial.</p></li>
<li><p>Crie uma conta de computador (com o FQDN [nome de domínio totalmente qualificado] aplicável) para o Aparelho de Filial Persistente nos Serviços de Domínio Active Directory.</p></li>
<li><p>No Construtor de Topologias, crie e publique o Aparelho de Filial Persistente.</p></li>
</ol></td>
<td><p>A conta do usuário técnico deve ser um membro RTCUniversalSBATechnicians. O Aparelho de Filial Persistente deve pertencer ao grupo RTCSBAUniversalServices, o que acontece automaticamente quando você usa o Construtor de topologias.</p></td>
</tr>
<tr class="even">
<td><p>Instalar e ativar o Aparelho de Filial Persistente.</p></td>
<td><p><strong>No site de filial:</strong></p>
<ol>
<li><p>Conecte o Aparelho de Filial Persistente a uma porta Ethernet e PSTN.</p></li>
<li><p>Inicie o Aparelho de Filial Persistente.</p></li>
<li><p>Participe do Aparelho de Filial Persistente para o domínio, usando a conta de usuário do domínio criada para o Aparelho de Filial Persistente no site central. Defina o FQDN e o endereço IP para corresponderem ao FQDN criado na conta do computador.</p></li>
<li><p>Configure o Aparelho de Filial Persistente usando a interface de usuário OEM.</p></li>
<li><p>Teste a conectividade do PSTN.</p></li>
</ol></td>
<td><p>O usuário técnico deve ser um membro do RTCUniversalSBATechnicians.</p></td>
</tr>
</tbody>
</table>


## Detalhes do servidor de filial persistente

No Construtor de Topologias, crie o site de filial, adicione o Servidor de Filial Persistente ao site, e execute o Assistente de Implantação do Lync Server no computador no qual você quer instalar a função.

## Consulte Também

#### Outros Recursos

[Implantando o Lync Server 2013](lync-server-2013-deploying-lync-server.md)

