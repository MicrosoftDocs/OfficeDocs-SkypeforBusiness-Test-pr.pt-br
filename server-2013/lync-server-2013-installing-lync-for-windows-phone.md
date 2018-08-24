---
title: Instalando o Lync para Windows Phone
TOCTitle: Instalando o Lync para Windows Phone
ms:assetid: bf502546-ff69-489f-a92e-a78b58803d53
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Hh690996(v=OCS.15)
ms:contentKeyID: 52057702
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Instalando o Lync para Windows Phone

 

_**Tópico modificado em:** 2016-12-08_

O Lync 2013 para Windows Phone é um aplicativo que pode ser instalado pelo usuário e está disponível no Windows Phone Marketplace.

## Instalando o Lync para Windows Mobile

É possível instruir seus usuários a instalarem o Lync 2013 para Windows Phone em seus dispositivos direcionando-os ao Windows Phone Marketplace em <http://go.microsoft.com/fwlink/?linkid=231901>.

## Se você usar um registro SRV de DNS para publicar Serviços Web do Exchange

Para permitir a integração do Exchange para clientes do Lync, algumas organizações publicam a URL de Serviços Web do Exchange usando um registro SRV de DNS. O documento "Entendendo e solucionando problemas de integração do Exchange", disponível no Centro de Download da Microsoft em [http://go.microsoft.com/fwlink/?LinkID=391095](http://go.microsoft.com/fwlink/?linkid=391095), descreve cenários nos quais isso talvez seja necessário. No entanto, a integração do Exchange para usuários do Windows Phone não funcionará nesse cenário, pois a plataforma Windows Phone não oferece suporte a pesquisas de SRV. Será necessário instruir os usuários do Windows Phone a especificarem a URL dos Serviços Web do Exchange, em vez de permitir que o telefone detecte o servidor automaticamente.

Instrua os usuários a definirem as configurações do Lync em seus Windows Phones da seguinte forma:

1.  No Windows Phone, nas configurações do Lync, selecione a tela do **Exchange**.

2.  Mova **Auto-Detect Server** para **Off**.

3.  Toque no campo vazio e insira o FQDN (nome de domínio totalmente qualificado) ou URL dos Serviços Web do Exchange.
    
    > [!NOTE]  
    > Você pode especificar o FQDN ou a URL completa do seu servidor de Serviços Web do Exchange. Se você especificar o FQDN, o protocolo (https://) e o caminho de Serviços Web do Exchange (/ews/exchange.asmx) são adicionados automaticamente. Se o seu caminho de Serviços Web do Exchange for diferente, você poderá especificar a URL completa.

4.  Feche a tela.

## Verificando a instalação do cliente móvel

Depois de configurar o cliente e entrar com êxito, use o teste a seguir para verificar se a instalação do Lync 2013 está funcionando corretamente no seu dispositivo móvel.

**Procure um contato no diretório corporativo**

1.  Na lista Contatos, toque em **Pesquisar** na parte inferior.

2.  Procure um contato que conste apenas na lista de endereços global.

3.  Verifique se o nome do contato aparece nos resultados da pesquisa.

**Teste mensagens instantâneas e presença**

1.  Na lista Contatos, toque em um contato.

2.  No cartão de visita, toque no ícone **IM**.

3.  Verifique se uma janela de mensagem instantânea (IM) aparece e se é possível digitar e enviar uma IM.

**Teste a conferência discada**

1.  No Outlook, agende uma reunião do Lync.

2.  No dispositivo móvel, abra o convite de reunião.

3.  Clique no link da reunião para ingressar.

4.  Atenda à chamada do serviço de conferência e verifique se você está conectado ao áudio da reunião.

**Teste as notificações por push**

1.  No dispositivo móvel do usuário A, entre no Lync com a conta do usuário A.

2.  Abra outro aplicativo no dispositivo móvel.

3.  Em um cliente diferente, entre no Lync com a conta do usuário B.

4.  Envie uma mensagem instantânea do usuário B para o usuário A.

5.  Verifique se a notificação de IM aparece no dispositivo móvel do usuário A.

