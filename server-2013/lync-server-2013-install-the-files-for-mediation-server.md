---
title: 'Lync Server 2013: Instalar os arquivos para o Servidor de Mediação'
TOCTitle: Instalar os arquivos para o Servidor de Mediação
ms:assetid: f0f7dd15-58e1-40fd-aa7e-6db50ceafacd
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg412998(v=OCS.15)
ms:contentKeyID: 49308546
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Instalar os arquivos para o Servidor de Mediação no Lync Server 2013

 

_**Tópico modificado em:** 2012-08-06_

Para concluir com êxito este procedimento, você deve estar conectado no servidor no mínimo como um administrador local e um usuário de domínio com associação no grupo RTCUniversalReadOnlyAdmins.

Use as etapas neste tópico para executar o Assistente de Implantação do Lync Server 2013 para instalar os arquivos no Servidor de Mediação em um computador onde você adicionou um Pool do servidor de mediação quando usou o Construtor de Topologia para definir e publicar o pool. Ao instalar os arquivos no Servidor de Mediação, você também instala e atribui o certificado solicitado por cada computador em um Pool do servidor de mediação.

Neste site, se você já implantou os Servidor de Mediação nos Pools de Front-Ends ou nos Servidor Standard Edition, é possível pular este tópico e continuar em [Configurando troncos no Lync Server 2013](lync-server-2013-configuring-trunks.md).

> [!NOTE]  
> Este tópico assume que você já definiu e publicou um Pool do servidor de mediação autônomo, conforme descrito no <a href="lync-server-2013-define-a-mediation-server-in-topology-builder.md">Definir um Servidor de Mediação no Construtor de Topologia no Lync Server 2013</a> e <a href="lync-server-2013-publish-the-topology.md">Publicar a topologia no Lync Server 2013</a> na documentação de Implantação, e que você verificou se os computadores no Pool do servidor de mediação cumprem os pré-requisitos descritos em <a href="lync-server-2013-software-prerequisites-for-enterprise-voice.md">Pré-requisitos de software para Enterprise Voice no Lync Server 2013</a> e <a href="lync-server-2013-security-and-configuration-prerequisites-for-enterprise-voice.md">Pré-requisitos de configuração e segurança para Entreprise Voice no Lync Server 2013</a>.

## Para instalar os arquivos em um pool do Servidor de Mediação autônomo

1.  Na mídia de instalação, clique com o botão direito em *\<installation media\>* **\\Setup\\amd64\\Setup.exe** e clique em **Executar como administrador**.

2.  Na página **Local de instalação**, clique em **OK**.

3.  Na página **Acordo de licença do usuário final**, clique em **Eu aceito** e em **OK**. (Obrigatório para continuar.)

4.  Na página **Assistente de Implantação do Lync Server 2010**, clique em **Instalar ou atualizar o sistema do Lync Server**.

5.  Próximo a **Etapa 1: Instalar repositório de configuração local**, clique em **Executar** e siga as instruções na tela.

6.  Na página **Configurar réplica local do repositório de gerenciamento central**, aceite o padrão **Recuperar diretamente no repositório de gerenciamento central** e clique em **Avançar**.

7.  Na página **Executar comandos**, quando o status da tarefa é exibido como **Concluído**, clique em **Finalizar**.

8.  Próximo a **Etapa 2: Configurar ou remover os componentes do Lync Server**, clique em **Executar** e em **Avançar**.

9.  Na página **Executar comandos**, quando o status da tarefa é exibido como **Concluído**, clique em **Finalizar**.

10. Próximo a **Etapa 3: Solicitar, instalar ou atribuir certificados**, clique em **Executar**. Siga as instruções na tela, aceitando as configurações padrões. O Servidor de mediação exige um certificado, você executará a **Etapa 3** duas vezes: uma vez para emitir um certificado necessário e novamente para atribui-lo.

11. Quando o certificado for emitido e atribuído corretamente, ao lado da **Etapa 4: Iniciar serviços**, clique em **Executar** e siga as instruções na tela.

12. Quando a **Etapa 4** for concluída com êxito, reinicie o servidor e faça o login no servidor como membro do grupo DomainAdmins.

13. No computador onde você está executando o Painel de Controle do Lync Server, verifique na página **Topologia** do Painel de Controle do Lync Server se o status de serviço do Servidor de Mediação é exibido com uma marca de verificação verde. Se um X vermelho é exibido, selecione o Servidor de Mediação. No menu **Ações**, clique em **Iniciar todos os serviços**.

Se você adicionou mais de um computador ao pool do Servidor de Mediação, realize as etapas neste procedimento em todos os computadores no Pool do servidor de mediação. Se você não precisa instalar os arquivos no Servidor de Mediação em qualquer outro computador, siga os procedimentos em [Configurando troncos no Lync Server 2013](lync-server-2013-configuring-trunks.md) para definir as configurações da conexão em tronco entre este Pool do servidor de mediação (ou todos os Servidores de Mediação neste site) e seu ponto.

## Consulte Também

#### Conceitos

[Requisitos de certificado para servidores internos no Lync Server 2013](lync-server-2013-certificate-requirements-for-internal-servers.md)

