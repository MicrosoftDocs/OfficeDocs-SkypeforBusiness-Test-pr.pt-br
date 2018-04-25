---
title: Ameaças de Segurança Comuns no Modern Day Computing
TOCTitle: Ameaças de Segurança Comuns no Modern Day Computing
ms:assetid: 56d22197-e8e2-46b8-b3a3-507bd663700e
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn433220(v=OCS.15)
ms:contentKeyID: 56558972
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Ameaças de Segurança Comuns no Modern Day Computing

 

_**Tópico modificado em:** 2015-03-09_

Porque o Lync Server 2013 é um sistema de comunicação de classe empresarial, você deve saber dos ataques à segurança comuns que podem afetar a infraestrutura e a comunicação.

## Chave de Ataque Comprometida

Uma chave é um código secreto ou um número que é usado para criptografar, descriptografar ou validar uma informação secreta. Há duas chaves sensitivas em uso na chave de infraestrutura pública (PKI) que deve ser considerada: .

  - A chave privada que cada titular do certificado tem

  - A chave da sessão que é usada depois da identificação com sucesso e a chave da sessão alterada pelos parceiros de comunicação

Um ataque à chave comprometida acontece quando o atacante determina a chave de privacidade ou a chave da sessão. Quando o atacante é bem sucedido nesta determinação da chave, ele pode usá-la para descriptografar dados criptografados sem que o remetente.

O Lync Server 2013 usa os recursos PKI no sistema operacional Windows Server para proteger os dados da chave para criptografar para as conexões do Transport Layer Security (TLS). As chaves usadas para criptografar mídia são trocados através de conexões TLS.

## Rede de Ataque De Negação de Serviço

O ataque *de negação de serviço* ocorre quando o atacante impede o uso da rede normal e função pelos usuários válidos. Isso é feito quando o atacante inunda o serviço com pedidos legítimos que domina o uso do serviço pelos usuários legítimos. Usando um ataque de negação de serviço, o atacante pode fazer o seguinte:

  - Enviar dados inválidos aos aplicativos e serviços que estão funcionando na rede atacada para interromper o funcionamento normal delel.

  - Enviar uma grande quantidade de tráfego, sobrecarregando o sistema até que ele pare de responder ou responda devagar aos pedidos legítimos.

  - Esconder a evidência dos ataques.

  - Impedir os usuários de acessar os recursos de acesso a rede.

## Espionagem (Bisbilhotar, Intrometer)

*A Espionagem* pode ocorrer quando um atacante ganha acesso ao caminho dos dados na rede e tem a habilidade para monitorar e ler o tráfego. Isso também é chamado de *bisbilhotar* ou *falsificar*. Se o tráfego está no texto plano, o atacante pode lê-lo quando o atacante ganha acesso ao caminho. Um exemplo é um ataque realizado no controle de um router no caminho dos dados.

A recomendação padrão e a configuração para o tráfego com o Microsoft Lync Server 2013 é para usar mutualmente o TLS (MTLS) entre os servidores confiáveis e o TLS do cliente para servir. Essa medida protetora poderia dificultar e muito um ataque ou impossibilitar o alcance com o período de tempo no qual tal conversa ocorre. TLS autentica todas as partes e criptografa todo tráfego. Isso não impede a espionagem, mas o atacante não pode ler o tráfego, a não ser que quebre a criptografia.

O protocolo de Relay de Uso Traversal NAT (TURN) não exige o tráfego para ser criptografado e as informações que são enviadas são protegidas pela integridade da mensagem. Mesmo estando abertas apara a espionagem, as informações que são enviadas (o endereço do IP e a porta) podem ser extraídas diretamente dando uma simples olhada nos endereços de saída e de destino dos pacotes. O serviço A/V Edge certifica que os dados são válidos verificando a Integridade da Mensagem da mensagem, usando a chave derivada de poucos itens, incluindo uma senha do TURN, que nunca é enviada em um texto claro. Se o ProtocoIo (SRTP) é usado, o tráfego de mídia também é criptografado.

## Falsificação de ID (endereço de IP de Falsificação)

*A falsificação* ocorre quando o atacante determina e usa um endereço de IP de uma rede, computador ou componente de rede sem autorização para tal ação. Um ataque bem sucedido permite que o atacante opere como se o atacante fosse a entidade normalmente identificada pelo endereço de IP. No contexto da Microsoft Lync Server 2013, essa situação acontece somente se o administrador fizer as duas ações seguintes:

  - Conexões configuradas que suportam apenas o Protocolo de Controle de Transmissão (TCP) (o que não é recomendado, porque as comunicações do TCP são descriptografadas).

  - Marque os endereços de IP daquelas conexões como hosts confiáveis.

É menos um problema para as conexões de Transport Layer Security (TLS), como TLS autentica todaas as partes e criptografa todo o tráfego. Usando o TLS evita que um atacante falsifique o endereço de IP em uma conexão específica (por exemplo, conexões TLS mútuas). Mas um atacante ainda poderia falsificar o endereço do servidor DNS que o Lync Server 2013 utiliza. No entanto, uma vez que a autenticação no Lync é feita com certificados, um atacante não teria um certificado válido necessário para falsificar uma das partes na comunicação.

## Ataque a intermediário

Um ataque a intermediário (man-in-the-middle) ocorre quando um atacante redireciona a comunicação entre dois usuários através do computador do atacante, sem o conhecimento dos dos dois usuários que estão se comunicando.O atacante pode monitorar e ler o tráfego antes de enviar para um recipiente independente. Cada usuário na comunicação, sem saber, envia e recebe o tráfego do atacante, enquanto pensam que estão se comunicando apenas com o outro usuário. Isso pode acontecer se um atacante pode modificar o Serviços de Domínio Active Directory para adicionar seu servidor como um servidor confiável ou modificar o Sistema de Nomes de Domínio (DNS) para que os clientes conectem através do atacante no caminho do servidor. Um ataque a intermediário também pode ocorrer com o tráfego de mídia entre dois clientes. No entanto, no ponto a ponto de áudio e vídeo e o compartilhamento de aplicativos do Microsoft Lync Server 2013,os fluxos são criptografados com SRTP, usando chaves criptográficas que são negociadas entres as partes que estão usando o Protocolo SIP sobre os servidores TLS, como um Bate Papo em Grupo usa o HTTPS para fortalecer a segurança do tráfego na rede.

## Ataque por Repetição RTP

Um *ataque por repetição* ocorre quando uma tramissão válida de mídia entre duas partes é interceptada e retransmitida pde forma mal-intencionada. O SRTP usado em conexão com um protocolo de sinalização de segurança protege as transmissões dos ataques por repetição, habilitando o receptor de manter um índice de pacotes RTP já recebidos e comparar cada novo pacote com aqueles já listados no índice.

## Spim

*Spim* é uma mensagem instantânea comercial não solicitada ou pedidos de inscrição de presença. Embora não seja por si só um compromisso da rede, é, no mínimo, irritante, pode reduzir a dispobilidade de pesquisa e produção, e pode levar a um comprometimento da rede. Um exemplo disso é os usuários spimming uns aos outros, enviando pedidos. Os usuários podem bloquear uns aos outros para evitar isso, mas com federação, se um ataque spim coordenado, isso pode ser difícil de superar, a não ser que você desabilite a federação do parceiro.

## Vírus e Worms

Um *vírus* é uma unidade de código cujo propósito é reproduzir unidades de códigos adicionais ou similares. Para funcionar, um vírus precisa de um host, como um arquivo, email ou programa. Um *worm* é uma unidade de código cujo propósito é reproduzir unidades de códigos adicionais, similares, mas não precisa de um host. Os vírus e os worms, aparecem principalmente durante transferências de arquivos entre clientes ou quando as URLs são enviadas por outros usuários. Se um vírus está no seu computador, ele pode, por exemplo, usar sua identidade e enviar mensagens instantâneas em seu nome.

## Informações de Identificação Pessoal

O Microsoft Lync Server 2013 tem o potencial para divulgar informações para uma rede pública que pode ser capaz de ser vinculada a um indivíduo. Os tipos de informações podem ser separadas em duas categorias:

  - **Aumento dos dados de presença ** O aumento dos dados de presença é uma informação que um usuário pode escolher para compartilhar ou não, um link para um parceiro federado ou com contatos em uma organização. Esses dados não são compartilhado com usuários em uma rede IM pública.As políticas dos clientes e outras configurações de clientes pode dar um certo controle com o administrador do sistema. O modo privado de aumento de presença do Lync Server 2013 pode ser configurado para um usuário individual para evitar que os usuários Lync na lista de contatos de usuários vejam as informações de presença do usuário. O modo de privacidade do aumento de presença não evita que os usuários do Microsoft Office Communicator 2007 e do Microsoft Office Communicator 2007 R2 vejam as informações de presença do usuário. Para mais detalhes visite [Novidades para clientes no Lync Server 2013](lync-server-2013-what-s-new-for-clients.md) na documentação do Guia de Introdução e [Configurando o modo de privacidade de presença avançada](lync-server-2013-configuring-enhanced-presence-privacy-mode.md) na documentação de Implementação.

  - **Dados obrigatórios** Os dados obrigatórios são pedidos para uma operação adequada do servidor ou o cliente e não está sob o controle do cliente ou da administração do sistema. Essas informações que são necessárias no servidor ou a nível de rede para os propósitos de roteamento, manutenção de estado e sinalização.

As seguintes listas tabelas de dados são exibidas para a rede pública.

### Dados de Presença Aumentados

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Dados divulgados</th>
<th>Configurações Possíveis</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Dados Pessoais</p></td>
<td><p>Nome, Título, empresa, Email, Fuso Horário</p></td>
</tr>
<tr class="even">
<td><p>Números de Telefone</p></td>
<td><p>Comercial, Celular, Residencial</p></td>
</tr>
<tr class="odd">
<td><p>Informações de Calendário</p></td>
<td><p>Disponível/Ocupado, Aviso de Ausência, Detalhes da Reunião (para aqueles que têm acesso ao seu calendário)</p></td>
</tr>
<tr class="even">
<td><p>Status de Presença</p></td>
<td><p>Ausente, Disponível, Ocupado, Não Perturbe, Offline</p></td>
</tr>
</tbody>
</table>


### Dados Obrigatórios

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Dados Divulgados</th>
<th>Exemplo de Informações</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Endereço de IP</p></td>
<td><p>Endereço atual do computador ou endereço do NATed</p></td>
</tr>
<tr class="even">
<td><p>URI do SIP</p></td>
<td><p>jeremylos@litwareinc.com</p></td>
</tr>
</tbody>
</table>

