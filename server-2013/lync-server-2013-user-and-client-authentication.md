---
title: Autenticação de Usuário e Cliente para o Lync Server 2013
TOCTitle: Autenticação de Usuário e Cliente para o Lync Server 2013
ms:assetid: 77f4b62a-f75c-424d-8f02-a6519090015d
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn481132(v=OCS.15)
ms:contentKeyID: 59679347
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Autenticação de Usuário e Cliente para o Lync Server 2013

 

_**Tópico modificado em:** 2013-11-11_

Um usuário confiável possui credenciais que foram autenticadas por um servidor confiável em Microsoft Lync Server 2013. Esse servidor é normalmente um Servidor Standard Edition, Enterprise EditionServidor Front-End ou Diretor. O Lync Server 2013 baseia-se no Serviços de Domínio Active Directory como um repositório único e de back-end das credenciais de usuário.

Autenticação é o fornecimento de credenciais de usuário a um servidor confiável. O Lync Server 2013 usa os seguintes protocolos de autenticação, dependendo do status e da localização do usuário.

  - **Protocolo de segurança da versão 5 do MIT Kerberos** para usuários internos com credenciais do Active Directory.O Kerberos requer a conectividade do cliente para o Serviços de Domínio Active Directory, e é por isso que não pode ser utilizado para autenticação de clientes fora do firewall corporativo.

  - **Protocolo NTLM** para usuários com credenciais do Active Directory que estiverem se conectando de um ponto de extremidade fora do firewall corporativo. O Serviço de Borda de Acesso redireciona solicitações de Logon a um Diretor, se houver, ou um Servidor Front-End para autenticação. O Serviço de Borda de Acesso não realiza nenhuma autenticação.
    
    > [!NOTE]  
    > O protocolo NTLM oferece uma proteção contra ataques mais fraca que o Kerberos, então, algumas empresas minimizam o uso do NTLM. Consequentemente, o acesso ao Lync Server 2013 poderá ser restrito a uso interno ou a clientes conectados por meio de uma conexão VPN ou DirectAccess.

  - **Protocolo Digest** para os chamados usuários anônimos. Usuários anônimos são usuários externos que não possuem credenciais reconhecidas do Active Directory, mas que foram convidados para uma conferência e possuem uma chave de conferência válida. A autenticação Digest não é usada para outras interações com clientes.

A autenticação do Lync Server 2013 consiste em duas fases:

1.  Uma associação de segurança é estabelecida entre o cliente e o servidor.

2.  O cliente e o servidor usa a associação de segurança existente para assinar mensagens enviadas e para verificar as mensagens recebidas. Mensagens não autenticadas de um cliente não são aceitas quando uma autenticação for habilitada no servidor.

Uma marca da confiança do usuário é anexada a cada mensagem de um usuário não para que ele se identifique. O servidor verifica cada mensagem, buscando por credenciais de usuário válidas. Se as credenciais de usuário forem válidas, a mensagem não será contestada nem pelo primeiro servidor nem pelos outros servidores de um servidor de nuvem confiável.

Usuários com credenciais válidas emitidas por um parceiro federado são confiáveis, porém são opcionalmente impedidos por restrições adicionais de utilizar toda a gama de privilégios concedidos aos usuários internos.

Os protocolos ICE e TURN também utilizam o mecanismo de desafio Digest, conforme descrito no IETF TURN RFC.

Os certificados do cliente proporcionam um caminho alternativo para que os usuários sejam autenticados pelo Lync Server 2013. Em vez de fornecer um nome de usuário e senha, os usuários possuem um certificado e uma chave privada correspondentes ao certificado necessário para resolver a criptografia. (Este certificado deverá ter um nome de entidade ou nome alternativo da entidade que identifique o usuário, deverá ser emitido pela CA raiz considerada confiável pelos servidores que executam o Lync Server 2013, estar dentro do período de validade do certificado e não ter sido revogado). Para serem autenticados, os usuários necessitam apenas inserir um número de identificação pessoal (PIN). Os certificados são particularmente utéis para telefones e outros dispositivos que executam o Phone Edition do Microsoft Lync 2013, no qual é difícil inserir um nome de usuário e/ou senha.

