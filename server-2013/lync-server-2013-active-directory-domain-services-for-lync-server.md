---
title: Active Directory Domain Services para Lync Server 2013
TOCTitle: Active Directory Domain Services para Lync Server 2013
ms:assetid: 5483afd5-d8af-4825-ae95-a82dbe941dbf
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn481129(v=OCS.15)
ms:contentKeyID: 59679344
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Active Directory Domain Services para Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

Serviços de Domínio Active Directory funciona como serviço de diretório para as redes Windows Server 2003, Windows Server 2008, Windows Server 2012 e Windows Server 2012 R2. O Serviços de Domínio Active Directory também serve como a base sobre a qual a infraestrutura de segurança do Microsoft Lync Server 2013 é construída. O objetivo desta seção é descrever como o Lync Server 2013 usa o Serviços de Domínio Active Directory para criar um ambiente seguro de IM, Webconferência, mídia e voz. Para obter mais detalhes sobre extensões do Lync Server para Serviços de Domínio Active Directory e sobre a preparação de seu ambiente do Serviços de Domínio Active Directory, consulte [Preparando Serviços de Domínio do Active Directory para o Lync Server 2013](lync-server-2013-preparing-active-directory-domain-services.md) na Documentação de implantação. Para obter mais detalhes sobre a função do Serviços de Domínio Active Directory nas redes Windows Server, consulte a documentação da versão do sistema operacional que estiver utilizando.

Lync Server 2013 utiliza o Serviços de Domínio Active Directory para armazenar:

  - As configurações globais exigidas por todos os servidores que executam o Lync Server 2013 em floresta.

  - Informações do sistema que identificam as funções de todos os servidores que executam o Lync Server 2013 em uma floresta.

  - Algumas configurações de usuário.

## Infraestrutura do Active Directory

Requisitos de infraestrutura para o Active Directory, incluindo o que segue:

  - Requisitos do sistema operacional para controladores de domínio

  - Requisitos de níveis funcionais de domínio e de floresta

  - Requisitos de domínio do catálogo global

Para obter mais detalhes, consulte [Requisitos de infraestrutura do Active Directory para Lync Server 2013](lync-server-2013-active-directory-infrastructure-requirements.md) na Documentação de implantação.

## Preparação do Serviços de Domínio Active Directory

> [!NOTE]  
> Recomendamos que implemente suas configurações globais de implantação ao Contêiner de configuração em vez do contêiner do Sistema. Isso não aumenta a segurança, mas pode resultar em melhorias de escalabilidade para algumas topologias Serviços de Domínio Active Directory. Se estiver migrando do Microsoft Office Communications Server 2007 e utilizou o contêiner do Sistema, mas planeja utilizar o Contêiner de configuração, você DEVE mover as configurações no Contêiner do sistema ANTES de realizar qualquer preparativo de atualização. Para migrar suas configurações de contêiner de Sistema para o contêiner de configuração, consulte a Ferramenta de migração de configurações globais do Office Communications Server 2007 em <a href="http://go.microsoft.com/fwlink/p/?linkid=145236">http://go.microsoft.com/fwlink/p/?LinkId=145236</a>.

Ao implantar Lync Server 2013, o primeiro passo é preparar o Serviços de Domínio Active Directory. A preparação do Serviços de Domínio Active Directory para Lync Server 2013 consiste nas seguintes etapas:

  - **Preparar Esquema** . Essa tarefa expande o esquema Serviços de Domínio Active Directory para incluir classes e atributos específicos para o Lync Server 2013. Para obter detalhes sobre a preparação do esquema, consulte [Executando preparação de esquema de Active Directory no Lync Server 2013](lync-server-2013-running-schema-preparation.md) na Documentação de implantação. Para obter mais informações, consulte [Migração do Office Communications Server 2007 R2 para Lync Server 2013](migration-from-office-communications-server-2007-r2-to-lync-server-2013.md).

  - **Preparar Floresta**. Essa tarefa cria configurações globais e objetos no domínio raiz da floresta, juntamente com o serviço universal e os grupos administrativos que regem o acesso a essas configurações e objetos. Para obter mais detalhes sobre a preparação da floresta, consulte [Executando preparação de floresta para Lync Server 2013](lync-server-2013-running-forest-preparation.md) na Documentação de implantação.

  - **Preparar Domínio**. Essa tarefa acrescenta as Entradas de controle de acesso (ACEs) necessárias aos grupos universais que concedem autorizações para hospedar e gerenciar usuários no domínio. Essa tarefa deve ser concluída em todos os domínios em que deseja implementar os servidores que executem o Lync Server 2013 e em quaisquer domínios em que seus usuários do Lync Server estão localizados. Para obter mais detalhes sobre a preparação do domínio, consulte [Executando preparação de domínio para Lync Server 2013](lync-server-2013-running-domain-preparation.md) na Documentação de implantação.

Para obter uma visão geral do processo completo de preparação do Active Directory e sobre os direitos e permissões necessários para realizar cada etapa, consulte [Requisitos de infraestrutura do Active Directory para Lync Server 2013](lync-server-2013-active-directory-infrastructure-requirements.md) na Documentação de implantação.

## Grupos Universais

Durante a preparação da floresta, o Lync Server 2013 cria vários grupos universais no Serviços de Domínio Active Directory, que têm permissão para acessar e gerenciar configurações e serviços globais. Esses grupos universais incluem:

  - **Grupos Administrativos**. Esses grupos definem as funções fundamentais do administrador em uma rede do Lync Server. Durante a preparação da floresta, esses grupos de administradores são adicionados aos grupos de infraestrutura do Lync Server.

  - **Grupos de Serviços**. Esses grupos são contas de serviços necessárias para acessar diversos serviços prestados pelo Lync Server.

  - **Grupos de infraestrutura**. Esses grupos fornecem permissão para acessar áreas específicas da infraestrutura do Lync Server. Eles funcionam como componentes dos grupos administrativos e você não deve modificá-los nem adicionar usuários diretamente a eles. Durante a preparação da floresta, grupos de serviços e de administração específicos são adicionados aos grupos de infraestrutura adequados.

Para obter detalhes sobre os grupos universais específicos criados ao preparar o AD para o Lync Server, bem como os grupos de serviços e administração adicionados aos grupos de infraestrutura, consulte [Alterações feitas pela preparação da floresta no Lync Server 2013](lync-server-2013-changes-made-by-forest-preparation.md) na Documentação de implantação.

> [!NOTE]  
> Lync Server 2013 oferece suporte aos grupos universais no Windows Server 2012 para servidores que executam o Lync Server 2013, bem como nos sistemas operacionais do Windows Server 2003 para controladores de domínio. Os membros dos grupos universais podem incluir outros grupos e contas de qualquer domínio na árvore ou floresta de domínio e podem receber permissões em qualquer domínio na árvore ou floresta de domínio. O suporte do grupo universal, combinado com a delegação de administrador, simplifica a implantação do Lync Server. Por exemplo, não é necessário adicionar um domínio a outro para permitir que um administrador os gerencie.

## Controle de Acesso Baseado em Função

Além de criar grupos de serviços e administração universais e de adicionar grupos de serviços e de administração aos grupos universais adequados, a preparação da floresta também cria grupos de Controle de acesso baseado em função (RBAC). Para obter mais detalhes sobre os grupos de RBAC específicos criados pela preparação da floresta, consulte [Alterações feitas pela preparação da floresta no Lync Server 2013](lync-server-2013-changes-made-by-forest-preparation.md) na Documentação de implantação. Para obter mais informações sobre os grupos de RBAC, consulte [Função de controle de acesso baseado em função (RBAC) do Lync Server 2013](lync-server-2013-role-based-access-control-rbac.md).

## Entradas de controle de acesso (ACEs) e Herança

A preparação da floresta cria ACEs privadas e públicas, adicionando ACEs nos grupos universais criados. Ela gera ACEs privadas específicas no contêiner de configurações globais usado pelo Lync Server. Esse contêiner é usado apenas pelo Lync Server e está localizado no contêiner de configuração ou do sistema no domínio raiz, dependendo de onde as configurações globais estão armazenadas.

A etapa de preparação do domínio adiciona entradas de controle de acesso (ACEs) necessárias aos grupos universais que concedem permissões para hospedar e gerenciar usuários no domínio. A preparação do domínio cria ACEs no domínio raiz e três contêiners integrados: Usuário, Computadores e Controladores de Domínio.

Para obter detalhes sobre as ACEs públicas criadas e adicionadas pela preparação da floresta e do domínio, consulte [Alterações feitas pela preparação da floresta no Lync Server 2013](lync-server-2013-changes-made-by-forest-preparation.md) e [Alterações feitas pela preparação de domínio no Lync Server 2013](lync-server-2013-changes-made-by-domain-preparation.md) na Documentação de implantação.

As organizações geralmente bloqueiam o Serviços de Domínio Active Directory (AD DS) para auxiliar a mitigar riscos de segurança. Entretanto, um ambiente Active Directory bloqueado pode limitar as permissões que o Lync Server 2013 exige. Isso inclui remover ACEs dos contêineres e OUs e desabilitar a herança de permissões nos objetos de Usuário, Contato, InetOrgPerson ou Computador. Em um ambiente Active Directory bloqueado, as permissões devem ser definidas manualmente nos contêineres e OUs que necessitam delas. Para obter mais detalhes, consulte [Preparando Serviços de Domínio Active Directory bloqueado no Lync Server 2013](lync-server-2013-preparing-a-locked-down-active-directory-domain-services.md) na Documentação de implantação.

## Informações do servidor

Durante a ativação, o Lync Server 2013 envia informações do servidor a três seguintes locais Serviços de Domínio Active Directory:

  - Um ponto de conexão de serviço (SCP) em cada objeto de computador do Active Directory corresponde a um computador físico no qual Lync Server 2013 é instalado.

  - Objetos de servidor criados no contêiner da classe **msRTCSIP-Pools**.

  - Servidores confiáveis especificados no Construtor de Topologias.

## Pontos de conexão de serviço

Cada objeto do Lync Server 2013 no Serviços de Domínio Active Directory possui um SCP, chamado de Serviços RTC, que possui vários atributos que identificam cada computador e especificam os serviços que realizam. Dentre os atributos SCP mais importantes estão *serviceDNSName*, *serviceDNSNameType*, *serviceClassname* e *serviceBindingInformation*. Os aplicativos de gestão de ativos de terceiros podem recuperar informações do servidor em uma implantação consultando esses e outros atributos SCP.

## o

Cada função de servidor do Lync Server 2013 possui um objeto do Active Directory correspondente, cujos atributos definem os serviços realizados por essa função. Além disso, quando um Servidor Standard Edition é ativado ou quando um pool do Enterprise Edition é criado, o Lync Server 2013 cria um novo objeto **msRTCSIP-Pool** no contêiner **msRTCSIP-Pools**. A classe **msRTCSIP-Pool** especifica o nome de domínio totalmente qualificado (FQDN) do pool, juntamente com a associação entre os componentes de front-end e back-end do pool. (Um Servidor Standard Edition é considerado um pool lógico, cujos front-ends e back-ends são colocados em um único computador.)

## Servidores confiáveis

No Lync Server 2013, os servidores confiáveis são especificados ao executar o Construtor de Topologias e publicar sua topologia. A topologia publicada, incluindo todas informações de servidor, é armazenada no Repositório de gerenciamento central. Apenas servidores definidos no Repositório de gerenciamento central são confiáveis. No Lync Server 2013, um servidor confiável é aquele que segue os seguintes critérios:

  - O FQDN do servidor é apresentado na topologia armazenada no Repositório de gerenciamento central.

  - O servidor apresenta um certificado válido de uma CA confiável. Para obter mais detalhes, consulte [Requisitos de infraestrutura de certificado para o Lync Server 2013](lync-server-2013-certificate-infrastructure-requirements.md).

Se algum desses critérios não for cumprido, o servidor não é confiável e a conexão será recusada. Este requisito duplo impede um possível, mesmo se improvável, ataque em que um servidor não autorizado tenta assumir um FQDN de um servidor válido.

Além disso, para permitir que implantações do Microsoft Office Communications Server 2007 R2 e do Microsoft Office Communications Server 2007 se comuniquem com servidores do Lync Server 2013, o Lync Server 2013 cria contêineres durante a preparação da floresta para guardar as listas de servidores confiáveis para versões futuras. A tabela seguinte descreve os contêineres criados para a compatibilidade com implantações anteriores.

### Listas de Servidores Confiáveis e Contêineres do Active Directory para Compatibilidade com Versões anteriores

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Lista de servidor confiável</th>
<th>Contêiner do Active Directory</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Servidor Standard Edition e Servidor Front-End do Pool Enterprise</p></td>
<td><p>Configurações globais/Serviço RTC</p></td>
</tr>
<tr class="even">
<td><p>Servidores de Conferência</p></td>
<td><p>Serviço RTC/MCUs Confiáveis</p></td>
</tr>
<tr class="odd">
<td><p>Servidores de componentes da Web</p></td>
<td><p>Serviço RTC/TrustedWebComponentsServers</p></td>
</tr>
<tr class="even">
<td><p>Servidor de Mediação e Servidores do Communicator Web Access, Servidor de Aplicativo, Registrador do QoE, Serviço de Conferência A/V (também servidores SIP de terceiros)</p></td>
<td><p>Serviço RTC/Serviços confiáveis</p></td>
</tr>
<tr class="odd">
<td><p>Servidores proxy</p></td>
<td><p>O Lync Server 2013 não suporta compatibilidade com versões anteriores para servidores proxy</p></td>
</tr>
</tbody>
</table>


Para suportar servidores de versões anteriores, você deve executar o analisador de melhores práticas. Para obter detalhes sobre a execução do analisador de melhores práticas, consulte [http://go.microsoft.com/fwlink/p/?LinkId=330633](http://go.microsoft.com/fwlink/p/?linkid=330633).

