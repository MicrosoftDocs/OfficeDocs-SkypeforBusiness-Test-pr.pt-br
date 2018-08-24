---
title: Criar configurações do Registrador
TOCTitle: Criar configurações do Registrador
ms:assetid: eddfbdd2-cfd0-4c03-986e-443d6728db7d
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg182601(v=OCS.15)
ms:contentKeyID: 49308517
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Criar configurações do Registrador

 

_**Tópico modificado em:** 2013-03-17_

É possível usar o Registrador para configurar métodos de autenticação do servidor proxy. O protocolo de autenticação que você especificar determina que tipo de desafios os servidores no pool vão gerar para os clientes. Os protocolos disponíveis são:

  - **Kerberos**   Este é o esquema de autenticação baseado em senha mais forte disponível aos clientes, mas ele está normalmente disponível somente para clientes empresariais, pois exige conexões clientes com um Centro de distribuição de chaves (controlador de domínio Kerberos). Essa configuração é apropriada se o servidor autenticar somente clientes empresariais.

  - **NTLM**   Esta é a autenticação baseada em senha disponível para clientes que usam um esquema de hash de desafio-resposta na senha. Essa é a única forma de autenticação disponível para clientes sem conectividade com um Centro de distribuição de chaves (controlador de domínio Kerberos), como usuários remotos. Se um servidor autenticar somente usuários remotos, escolha NTLM.

  - **Autenticação de certificado**   Esse é o novo método de autenticação quando o servidor precisa obter certificados de clientes do Lync Phone Edition, de telefones de área comum e do Lync 2013. Em clientes do Lync Phone Edition, após um usuário fazer login e autenticar com êxito fornecendo um PIN (número de identificação pessoal), o Lync Server 2013 fornece o URI de SIP para o telefone e fornece um certificado assinado do Lync Server ou um certificado de usuário que identifica Joe (Ex: SN=joe@contoso.com ) para o telefone. Esse certificado é usado para autenticação com o Registrador e Serviços Web.

> [!NOTE]  
> Recomendamos a habilitação do Kerberos e NTLM quando um servidor suporta autenticação para clientes remotos e empresariais. O Servidor de Borda e os servidores internos se comunicam para assegurar que somente a autenticação NTLM seja oferecida aos clientes remotos. Se somente Kerberos for habilitado nesses servidores, não poderão autenticar usuários remotos. Se os usuários empresariais também autenticarem com base no servidor, o Kerberos será usado.

Execute estas etapas para criar um novo Registrador.

## Para criar um Registrador

1.  Usando uma conta de usuário que é membro do grupo RTCUniversalServerAdmins (ou tem direitos de usuário equivalentes), ou está atribuída à função CsServerAdministrator ou CsAdministrator, faça logon em qualquer computador que está na rede na qual você implantou o Lync Server 2013.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerda, clique em **Segurança** e em **Registrador**.

4.  Na página **Registrador**, clique em **Novo**

5.  Em **Selecionar um Serviço** , clique no serviço ao qual o Registrador será aplicado e clique em **OK** .

6.  Em **Nova Configuração do Registrador** , selecione uma ou mais das seguintes opções, dependendo dos recursos dos clientes e do suporte em seu ambiente:
    
      - **Habilitar autenticação Kerberos** para que os servidores no pool emitam desafios usando a autenticação Kerberos.
    
      - **Habilitar autenticação NTLM** para que os servidores no pool emitam desafios usando NTLM.
    
      - **Habilitar autenticação de certificado** para que os servidores no pool emitam certificados aos clientes.

7.  Clique em **Confirmar**.

