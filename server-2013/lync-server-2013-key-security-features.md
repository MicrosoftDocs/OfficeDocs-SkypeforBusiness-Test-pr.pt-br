---
title: Chave de Recursos de Segurança do Lync Server 2013
TOCTitle: Chave de Recursos de Segurança do Lync Server 2013
ms:assetid: bf2a3b8f-73c6-47e1-8c9e-ca1dc1a502bf
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn342829(v=OCS.15)
ms:contentKeyID: 56270468
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Chave de Recursos de Segurança do Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

O Lync Server 2013 possui uma série de recursos de segurança, incluindo a autenticação servidor para servidor, controle de acesso baseado em função e armazenamento de dados de configuração centralizado.

Este artigo fornece uma visão geral de alto nível da segurança do Lync Server 2013.

## Chave de Recursos de Segurança no Lync Server 2013

Segurança é um tópico bastante amplo. Ela atinge todos os recursos do Lync Server 2013, assim como bases de dados, serviços e hardware que organizam o ecossitema do Lync. Este artigo destaca alguns recursos do Lync Server 2013, em particular os designados para segurança.

## Ferramentas de Planejamento e Design

O Lync Server 2013 fornece duas ferramentas para facilitar o planejamento e o design e reduzir as chances de desconfiguração do Lync Server.

  - **A Ferramenta de Planejamento Topológico** automatiza grande parte do processo de design de topologia. Os resultados da Ferramentas de Planejamento podem ser exportados para o Construtor de Topologias, que é a ferramenta exigida para a instalação de cada servidor que executa o Lync Server 2013.

  - O **Construtor de Topologias** armazena todas as informações de configuração no repositório de Gerenciamento Central.

Para saber mais sobre essas ferramentas, consulte [Planejamento para Lync Server 2013](lync-server-2013-planning.md).

## Repositório de Gerenciamento Central

No Lync Server 2013, os dados e serviços de configuração dos servidores fazem parte do repositório de Gerenciamento Central. Este fornece um armazenamento robusto e esquematizado das informações necessárias para definir, configurar, manter, administrar, descrever e operar um ambiente do Lync Server. Ele também desempenha a validação de dados para assegurar a consistência da configuração. Todas as alterações na configuração dessas informações acontecem nesse repositório, eliminando problemas de "dessincronização".

Cópias somente leitura dos dados são replicadas para todos os servidores na topologia, incluindo Servidores de borda e Aparelhos de Filial Persistente. A replicação é gerenciada por um serviço que, por definição, é executado sob um contexto de serviço de rede, fazendo com que os direitos e permissões sejam reduzidos aos de um usuário comum do computador.

## Autenticação Servidor para Servidor

No Lync Server 2013, a autenticação pode ser configurada entre servidores usando o protocolo de Autorização Aberta (OAuth). Por exemplo, o Lync Server 2013 pode ser configurado para ser autenticado por um servidor que esteja executando o Exchange Server 2013. Usando o protocolo OAuth, o Lync Server e o Exchange Server podem confiar um no outro. Isso possibilita a integração perfeita dos produtos. Para detalhes, veja [Gerenciando autenticação de servidor para servidor (Oauth) e inscrições de parceiros no Lync Server 2013](lync-server-2013-managing-server-to-server-authentication-oauth-and-partner-applications.md)

## Gerenciamento baseado no Windows PowerShell e Interface de Gerenciamento baseada na Web

O Lync Server 2013 fornece uma interface de gerenciamento avançada, construída na interface de linha de comando do Windows PowerShell. Inclui cmdlets para gerenciamento de segurança e recursos de segurança do Windows Power Shell padrão, habilitados para que os usuários não executem scripts inadvertidamente. Isso significa que os padrões do software são definidos automaticamente para maximizar a segurança e reduzir possíveis ataques. Para obter detalhes acerca do suporte de gerenciamento do Windows PowerShell no Lync Server 2013, acesse [Shell de gerenciamento do Lync Server](lync-server-2013-lync-server-management-shell.md).

## Controle de Acesso Baseado em Função (RBAC)

O Microsoft Lync Server 2013 fornece controle de acesso baseado em função (RBAC) para permitir a delegação de tarefas administrativas ao passo que mantém um padrão de segurança alto. O RBAC pode ser usado seguindo o princípio do "menor privilégio", no qual aos usuários são dados direitos administrativos relativos aos seus trabalhos. O Lync Server 2013 também tem a habilidade de criar uma nova função e modificar uma já existente. Para saber mais, veja [Planejamento de controle de acesso baseado em função no Lync Server 2013](lync-server-2013-planning-for-role-based-access-control.md).

## Conversão de Endereço de Rede (NAT)

O Lync Server 2013 não dá suporte para uso do conversor de endereços de rede (NAT) na interface do Servidor de borda, mas dá suporte para a instalação da interface externa dos serviços de Borda de Acesso, Borda de Webconferência e Borda A/V oculto sob um roteador ou firewall que desempenhe a conversão de endereço de rede (NAT) para topologias do Servidor de Borda consolidada única ou escalonável. Múltiplos Servidores de Borda ocultos sob um balanceador de carga de hardware não podem usar o NAT. O balanceador de carga do DNS (Domain Name System) é obrigatório se múltiplos Servidores de Borda usarem o NAT em suas interfaces externas. Por seu turno, o uso do balanceador de carga do DNS permite que o número de endereços de IP públicos por Servidor de Borda sem um pool de Servidor de Borda seja reduzido. Para saber mais, veja [Planejamento para acesso de usuário externo no Lync Server 2013](lync-server-2013-planning-for-external-user-access.md).

> [!NOTE]  
> Se você federa com empresas em uma implantação da Microsoft Office Communications Server 2007 e precisa usar áudio/vídeo entre a sua empresa e a empresa federada, os requisitos de porta serão os da versão antiga do Servidor de Borda implantado. Por exemplo, os intervalos de porta exigidos para versões antigas devem ser abertos por ambas as empresas até que o parceiro federado atualize o seu Servidor de Borda do Lync Server 2013. Quando os requisitos de porta poderão ser revistos e reduzidos de acordo com a nova configuração.

## Simplificar Certificados para Servidores de Borda

O Assistente de Implantação preenche nomes de identidade (SNs) e nomes de identidade alternativos (SANs) automaticamente, reduzindo possíveis inclusões desnecessárias e entradas potencialmente não seguras.

## Ciclo de Vida do Desenvolvimento da Segurança de Computação Confiável (SDL)

O Lync Server 2013 foi elaborado e desenvolvido em conformidade com o Ciclo de Vida do Desenvolvimento da Segurança de Computação Confiável (SDL), descrito em <http://go.microsoft.com/fwlink/?linkid=68761>.

  - **Seguro por Padrão**   O primeiro passo para criar um sistema de comunicações unificado mais seguro é o desenvolvimento de modelos de ameaça e teste de cada recurso projetado. Além disso, a Microsoft executa testes de comportamento fora do esperado para encontrar vulnerabilidades na segurança resultantes de atitudes inesperadas do projeto. Os múltiplos aperfeiçoamentos relacionados à segurança foram criados dentro do código de processos e práticas. As ferramentas de construção em tempo detectam invasões de buffer e outras potenciais ameaças antes do código ser checado no produto final. Claro, é impossível detectar todas as ameaças de segurança desconhecidas. Nenhum sistema pode garantir segurança completa. No entanto, porque o desenvolvimento do produto adotou os princípios de design seguro desde o início, o Lync server 2013 incorpora tecnologias de segurança padrão da indústria como parte fundamental de sua arquitetura.

  - **Seguro por Padrão**   Por padrão, as comunicações de rede no Lync Server 2013 são criptografadas. Uma vez que todos os servidores usam certificados e autenticação Kerberos, TLS, Protocolo TLS, SRTP (Secure Real-Time Transport Protocol), e outras técnicas de criptografia padrão do setor, incluindo o Padrão de Criptografia de Dados Avançados (AES) de 128-bits, todos os dados do Lync Server estão virtualmente protegidos na rede. Além disso, o controle de acesso baseado em função possibilita a implantação dos servidores executores do Lync Server 2013 para que executem somente os serviços e as permissões relacionadas apropriadas para cada função do servidor.

  - **Seguro na Implantação**   Toda documentação do Lync Server 2013 inclui práticas recomendadas para ajudar a determinar e configurar níveis de segurança otimizadas para a sua implantação e avaliar os riscos de ativação de opções não padronizadas.

