---
title: 'Lync Server 2013: Usando o portal administrativo da Web do Sistema de Salas do Lync'
TOCTitle: Usando o portal administrativo da Web do Sistema de Salas do Lync
ms:assetid: c387b2a3-3e42-4642-af72-88126ed2820f
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn743660(v=OCS.15)
ms:contentKeyID: 62269011
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Usando o portal administrativo da Web do Sistema de Salas do Lync no Lync Server 2013

 

_**Tópico modificado em:** 2014-11-10_

Depois que você implantar o LRS no servidor, poderá verificar o status de todas as salas do LRS entrando no portal administrativo da Web do LRS em um navegador.

## Entrar

1.  Navegue até a seguinte URL:
    
    https://\<fe-server\>/lrs

2.  Insira as credenciais da conta LRSSupport ou de uma conta que tenha sido adicionada ao grupo de segurança LRSSupportAdminGroup.

![Tela de entrada no portal admin do sistema Lync Room](images/Dn436326.050bcf70-2f3b-46b2-9b96-ebd12679b713(OCS.15).png "Tela de entrada no portal admin do sistema Lync Room")

## Página de resumo do portal administrativo da Web do LRS

A página de resumo fornece as seguintes informações sobre todas as salas do LRS implantadas no servidor:

  - **Marca**   O nome personalizado que o administrador atribui à sala. A marca pode ser definida no portal quando você clica no nome da sala.

  - **Integridade**   O status de integridade da sala, que é derivado do status Integridade Agregada da sala, que, por sua vez, é exibido na seção Integridade da página Configurações da Sala.

  - **Próxima Reunião**   A data e a hora em que a próxima reunião foi agendada.

  - **Versão, Fabricante, Modelo do LRS**   Estes valores são predefinidos no LRS. Dependendo do fabricante, estes campos podem ser deixados em branco.

  - **Última Atualização**   Exibe a última vez em que a página da Web foi atualizada.

![Visualização de Resumo do Portal de Administração do Sistema de Salas do Lync](images/Dn743660.f829ce90-dd95-4725-bd94-6870c5dcf046(OCS.15).png "Visualização de Resumo do Portal de Administração do Sistema de Salas do Lync")

## Informações da sala do LRS

A seção Informações da Sala do portal permite que você exiba e configure salas do LRS individuais. Ela contém quatro seções: Configurações, Detalhes, Registro em Log e Integridade.

## Configurações

Na seção Configurações, você pode definir a senha, a marca da sala e os níveis de volume padrão da sala. Se você definir essas configurações, as alterações serão replicadas somente depois que o console do LRS for reiniciado.

![Configurações de Salas do Portal de Administração do Sistema de Salas do Lync](images/Dn743660.ab162e19-41ac-4991-9b2a-92575aa53eda(OCS.15).png "Configurações de Salas do Portal de Administração do Sistema de Salas do Lync")

## Detalhes

A seção Detalhes fornece um resumo somente leitura das configurações da sala de LRS, incluindo: hora da última atualização; próxima reunião; últimas atualizações, manutenção e calibração; configurações padrão de alto-falante, microfone e toque; versão; URI do SPI; número de telas e detalhes sobre cada tela; status e atividade.

![Visualização de Detalhes do Portal de Administração do Sistema de Salas](images/Dn743660.2958bbba-db74-4670-a920-87fdfb2fc22d(OCS.15).png "Visualização de Detalhes do Portal de Administração do Sistema de Salas")

## Registro em log

A seção Registro em Log pode ser usada para coletar logs remotamente e salvá-los em um local especificado. Você também pode reiniciar o console do LRS (interface do usuário do LRS) ou reiniciar o sistema.

![Registro em Log de Salas do Portal de Administração do Sistema de Salas do Lync](images/Dn743660.749aee71-deaa-4ace-a146-fe2b349f0f42(OCS.15).png "Registro em Log de Salas do Portal de Administração do Sistema de Salas do Lync")

## Integridade

A seção Integridade oferece uma indicação visual da integridade da conexão, do dispositivo de áudio, do dispositivo de vídeo, do estado de resiliência e do dispositivo de tela do Lync Server.

![Integridade de Salas do Portal de Administração do Sistema de Salas do Lync](images/Dn743660.8cc644f8-8e3e-42d5-9079-045d8fe9daa7(OCS.15).png "Integridade de Salas do Portal de Administração do Sistema de Salas do Lync")

## Observações adicionais sobre o portal administrativo da Web

> [!NOTE]  
> <ul><li><p>Por motivos de segurança, o portal administrativo da Web desconecta você a cada 15 minutos.</p></li><li><p>As alterações da configuração são aplicadas somente após a reinicialização do sistema do LRS.</p></li><li><p>As notificações sobre o portal administrativo da Web do LRS são fixas; em outras palavras, elas não desaparecem.</p></li>
> <li><p>As notificações aparecem somente depois que você atualiza a página.</p></li>
> <li><p>O status das salas do LRS aparecem depois que você atualiza a página.</p></li>
> 
> <li><p>Se a senha da conta LRSApp expirar, você não poderá ver o status das salas. Configure a senha da conta LRSAppuser de modo que ela nunca expire, ou atualize a senha quando estiver perto da data de expiração.</p></li>
> 
> 
> <li><p>Há suporte para o portal administrativo da Web do LRS somente nas implantações locais.</p></li></ul>


## Solução de problemas

## Por que não consigo entrar no portal administrativo da Web?

  - Quando você abrir https://localhost/lrs, poderá ver a página de logon; mas quando você digitar suas credenciais, não conseguirá entrar. Nesse caso, você deve abrir https://FQDNofFEserver/lrs para entrar no portal administrativo da Web.

  - Se o computador em que você está acessando o portal administrativo da Web estiver em um grupo de trabalho, "http://" não funcionará. Use "https".

## Por que não consigo ver o LRS no portal administrativo da Web?

  - Verifique se você tem contas doLRS na sua implantação e se elas foram criadas de acordo com as recomendações de implantação do portal administrativo da Web do LRS. Verifique se as contas do LRS são provisionadas no Lync Server usando Enable-CsMeetingRoom, e não Enable-CsUser.

  - Se você tiver criado contas do LRS e não conseguir ver as contas no portal administrativo da Web, colete os logs de servidor usando a ferramenta Registro em Log do Lync Server com o componente **MeetingPortal** selecionado e envie-os ao contato de suporte do LRS.

## Por que não consigo ver o status do LRS no portal administrativo da Web?

  - Verifique se a conta de usuário LRSApp está habilitada para SIP.

  - Se você ainda estiver com problemas, colete o arquivo **Trace.log** no sistema LRS em D:\\Tracing\\LRSAdminLogs\\ e envie-o ao contato de suporte do LRS.

