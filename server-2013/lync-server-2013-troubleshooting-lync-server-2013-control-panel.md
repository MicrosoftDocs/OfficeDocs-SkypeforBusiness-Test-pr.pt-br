---
title: Resolver problemas do painel de controle do Lync Server 2013
TOCTitle: Resolver problemas do painel de controle do Lync Server 2013
ms:assetid: 54e7ab57-34ce-4a07-bcc9-643379eb4eb7
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg195689(v=OCS.15)
ms:contentKeyID: 49306742
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Resolver problemas do painel de controle do Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

Este tópico fornece informações e procedimentos que podem ajudá-lo a solucionar problemas de acesso ao Painel de Controle do Lync Server 2013.

## Requisitos de navegador da Internet

O Painel de Controle do Lync Server requer que a versão 4.0.50524.0 ou mais recente do Plug-in do navegador do Microsoft Silverlight esteja instalada. Se o Silverlight não estiver instalado ou se uma versão anterior estiver instalada, siga as instruções na mensagem para instalar a versão necessária.

> [!NOTE]  
> Os outros requisitos de software para o Painel de Controle do Lync Server pertencem ao sistema operacional no qual o Painel de Controle do Lync Server e todas as outras ferramentas administrativas do Lync Server 2013 podem ser instaladas. Para obter detalhes, consulte <a href="lync-server-2013-server-and-tools-operating-system-support.md">Suporte a sistemas operacionais de servidor e de ferramentas no Lync Server 2013</a> na documentação sobre Ajuste de Suporte.

Se o navegador da Internet bloquear a instalação do Silverlight devido a considerações de segurança, adicione a URL que abre o Painel de Controle do Lync Server à lista de sites confiáveis. Nas configurações de segurança do Internet Explorer, verifique se a opção **Executar controles ActiveX e plug-ins** está definida como **Habilitado**. Para obter detalhes, consulte [http://go.microsoft.com/fwlink/?linkid=214060\&clcid=0x416](http://go.microsoft.com/fwlink/?linkid=214060%26clcid=0x416). Além disso, verifique se o navegador está configurado para usar SSL 3.0.

Se o navegador da Internet estiver configurado para usar um servidor proxy, verifique se o navegador está configurado para ignorar o servidor proxy para os sites que são detectados automaticamente como sites internos. Ou adicione o endereço à lista de exceções do navegador nas definições de configuração de servidor proxy.

## Requisitos de registro DNS e de certificado para a URL de Acesso Administrativo

Se você tiver configurado uma URL simples para acessar o Painel de Controle do Lync Server, verifique se também configurou o registro de recurso (A) de host do DNS (Sistema de Nomes de Domínio) estático e o certificado necessários para usar a URL de acesso administrativo. Se você alterar a URL base a qualquer momento, verifique se a alteração foi refletida no registro DNS e no certificado apropriados e execute o *Enable-CsComputer* em cada Diretor e Servidor Front-End para registrar a alteração. Para obter detalhes, consulte os seguintes tópicos na documentação de Planejamento:

  - [Planejamento de URLs simples no Lync Server 2013](lync-server-2013-planning-for-simple-urls.md)

  - [Requisitos de DNS para URLs simples no Lync Server 2013](lync-server-2013-dns-requirements-for-simple-urls.md)

  - [Requisitos de certificado para servidores internos no Lync Server 2013](lync-server-2013-certificate-requirements-for-internal-servers.md)

Para obter os procedimentos passo a passo para configurar a URL de acesso administrativo, consulte [Editar ou configurar URLs simples no Lync Server 2013](lync-server-2013-edit-or-configure-simple-urls.md) na documentação de Implantação.

> [!NOTE]  
> Se você tiver mais de um adaptador de rede no servidor Web, configure manualmente o DNS para cada adaptador de rede adicional para que a resolução de DNS funcione corretamente.

## Requisitos de IIS (Serviços de Informações da Internet)

O Painel de Controle do Lync Server é um dos componentes do Lync Server 2013 que exige o IIS (Serviços de Informações da Internet). Em particular, verifique se o redirecionamento de HTTP e os recursos de autenticação do Windows estão habilitados e se o W3SVC (Serviço de Publicação na World Wide Web ) está em execução.

## Dependência do Serviço de Publicação na World Wide Web (Serviço do Windows)

Quando o Serviço de Publicação na World Wide Web é interrompido, você não pode acessar o Painel de Controle do Lync Server. Você pode reiniciar o serviço usando o MMC (Console de Gerenciamento Microsoft) dos Serviços do Windows.

**Para iniciar o Serviço de Publicação na World Wide Web**

1.  Faça logon no computador onde o Serviço de Publicação na World Wide Web foi instalado como parte do IIS (Serviços de Informações da Internet).

2.  Clique em **Iniciar**, em **Ferramentas administrativas** e em **Serviços**.

3.  Com o botão direito do mouse em **Serviço de Publicação na World Wide Web**e clique em **Iniciar**.

## Modo de pool de aplicativos

Configure o IIS para que o pool de aplicativos CsManagementAppPool use a conta do Serviço de Rede como sua identidade do modelo de processo.

## Permissões e direitos de usuário

Você deve entrar no Painel de Controle do Lync Server usando uma conta de domínio que é um membro do grupo CsAdministrator ou usando uma conta à qual você delegou as permissões e direitos de usuário. Você não pode entrar no Painel de Controle do Lync Server usando uma conta do computador local. Para obter detalhes sobre como delegar as tarefas administrativas por meio do RBAC (controle de acesso baseado em função), consulte [Planejamento de controle de acesso baseado em função no Lync Server 2013](lync-server-2013-planning-for-role-based-access-control.md) na documentação de Planejamento.

Se você usar uma URL simples para acessar o Painel de Controle do Lync Server, vrifique se os servidores Web foram adicionados aos grupos RTCUniversalServerAdmins e RTCUniversalUserAdmins.

## Consulte Também

#### Conceitos

[Ferramentas administrativas do Lync Server 2013](lync-server-2013-lync-server-administrative-tools.md)

