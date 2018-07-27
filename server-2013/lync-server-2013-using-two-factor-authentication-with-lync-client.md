---
title: Usar a autenticação de dois fatores com o cliente do Lync
TOCTitle: Usar a autenticação de dois fatores com o cliente do Lync
ms:assetid: d4136e61-c3ab-4b26-85c8-c1b2c24f5ee3
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn338071(v=OCS.15)
ms:contentKeyID: 56270476
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Usar a autenticação de dois fatores com o cliente do Lync

 

_**Tópico modificado em:** 2015-03-09_

Este tópico descreveu como aproveitar as vantagens da autenticação de dois fatores com o cliente do Lync 2013.

## Entrar no Lync 2013 pela primeira vez

Suas informações de entrada no Lync são normalmente configuradas de forma automática quando o Lync 2013 é instalado. Mas, na primeira vez em que você usar o Lync, talvez seja necessário iniciar manualmente o sistema.

**Para entrar no Lync pela primeira vez**

1.  Faça logon na rede da sua organização.

2.  Selecione **Iniciar** \> **Todos os Programas** \> **Microsoft Lync \> Lync 2013**.
    
    Você deverá ver a tela de entrada do Lync.
    
      - Se a caixa de endereço de entrada já estiver preenchida, confirme se o endereço mostrado está correto.
    
      - Se não estiver correto, ou se a caixa estiver vazia, insira seu endereço de entrada do Lync (normalmente ele será igual ao seu endereço de email).
    
      - Se uma caixa de senha vazia for exibida, adicione sua senha.

3.  Selecione **Entrar**.

## Sair do Lync

Quando você tiver terminado de usar o Lync, poderá fechar a tela, sair da sua sessão ou sair do programa, tudo do menu Arquivo. A tabela a seguir explica as diferenças nas opções.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Opção</th>
<th>O que ela faz</th>
<th>Como executar</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Fechar</p></td>
<td><p>Fecha a tela do Lync mas permite que a sessão do Lync identificada pela ID do usuário continue a ser executada. Isso acontece para que você possa continuar a obter notificações e a interagir com outras pessoas.</p>
<p>Você pode abrir a tela novamente em qualquer ocasião clicando no ícone do Lync na barra de tarefas ou na área de notificação na parte inferior da sua tela.</p></td>
<td><p>Na janela principal do Lync, siga um destes procedimentos:</p><ol><li><p>Selecione o botão <strong>Opções</strong>, então selecione <strong>Arquivo</strong> &gt; <strong>Fechar</strong>.</p></li>
> 
> 
> <li><p>Clique no botão <strong>Fechar</strong> (X) no canto superior direito da janela.</p></li></ol></td>
</tr>
<tr class="even">
<td><p>Sair</p></td>
<td><p>Encerra a sessão do Lync associada à sua ID de usuário, mas o Lync continua a ser executado em segundo plano. Quando você sair, a janela de entrada aparecerá.</p>
<div class="alert">

> [!TIP]
> Selecione <STRONG>Excluir minhas informações de entrada</STRONG> ao sair para remover o registro de sua ID de logon e da senha do computador. Fazer isso torna mais fácil para o pessoal de suporte solucionar problemas de entrada. Também ajuda a garantir que suas informações de entrada fiquem mais seguras ao dificultar que usuários não autorizados façam logon com suas credenciais.


</div></td>
<td><p>Na janela principal do Lync, selecione o botão <strong>Opções</strong>, então selecione <strong>Arquivo</strong> &gt; <strong>Sair</strong>.</p></td>
</tr>
<tr class="odd">
<td><p>Fechar</p></td>
<td><p>Encerra sua sessão do Lync e fecha o Lync em seu computador. Depois de fechar, se você quiser reiniciar o Lync, selecione <strong>Iniciar</strong> &gt; <strong>Todos os Programas</strong> &gt; <strong>Microsoft Lync</strong> &gt; <strong>Lync 2013</strong>.</p></td>
<td><p>Na janela principal do Lync, selecione o botão <strong>Opções</strong>, então selecione <strong>Arquivo</strong> &gt; <strong>Fechar</strong>.</p></td>
</tr>
</tbody>
</table>


## Entrar no Lync com um cartão inteligente

Algumas organizações usam um processo de entrada de várias etapas, chamado de autenticação de dois fatores, para aumentar a segurança de seus usuários do Lync 2013. Se você pretende usar essa opção, precisará de um "cartão inteligente" para entrar no Lync. Existem duas variedades de cartões inteligentes, físico e virtual:

  - **Físico**   Quase do tamanho de um cartão de crédito. Você o insere em um leitor de cartão inteligente ao fazer logon.

  - **Virtual**   Não é um objeto físico, mas um identificador eletrônico gravado em um chip especial do seu computador que, em essência, cria o cartão inteligente em seu computador. Disponível somente para uso com computadores com Windows 8 que contenham o chip TPM (Trusted Platform Module).

## Registrar seu cartão inteligente

Antes que seja possível entrar com um cartão inteligente, o cartão deverá ser "registrado" — ou seja, suas credenciais devem ser identificadas com o cartão. Esse será o caso seja o cartão físico ou virtual. Esse processo pode já ter sido realizado pelo administrador do Lync Server. Verifique com ele se não tiver certeza se isso foi feito.

> [!NOTE]  
> Uma vez que cada cartão inteligente está associado somente ao dispositivo em que está instalado, um cartão separado deverá ser registrado para cada computador com o Windows 8 usado.

**Para registrar manualmente seu cartão inteligente**

1.  Faça logon no computador em que o Lync será executado.

2.  Usando o Internet Explorer, navegue até a página de Registro da Autoridade de Certificação da sua organização.
    
    Peça ao administrador do Lync Server o endereço da Web desse recurso se ainda não o tiver. A URL será parecida com esta: https://MinhaCA.\[nomedasuaempresa\].com/certsrv.
    
    > [!NOTE]  
    > Se você estiver usando o Internet Explorer 10, talvez precise exibir o site em Modo de Compatibilidade.

3.  Quando solicitado a fazer logon na página de certificação, faça logon usando sua conta de domínio (em vez do administrador do seu computador).

4.  Na página de Boas-vindas do site, selecione **Solicitar um certificado**.

5.  Selecione **Solicitação Avançada**.

6.  Selecione **Criar e enviar uma solicitação para esta CA** e clique em **Avançar**.

7.  Agora você verá uma página chamada Estação de Registro de Cartão Inteligente. Aprove a solicitação para instalar o controle ActiveX e então preencha o formulário Solicitação de Certificado Avançado desta forma:
    
    1.  Selecione **Usuário de cartão inteligente** na lista suspensa **Modelo de Certificado**.
    
    2.  Selecione **Criar novo conjunto de chaves**.
    
    3.  Localize as informações do fabricante no rótulo do seu cartão inteligente e selecione esse fabricante na lista suspensa **CSP**.
    
    4.  Selecione **CSP** como o Formato de Solicitação, caso ainda não esteja selecionado.
    
    5.  Selecione **sha1** na lista suspensa Algoritmo de Hash, caso ainda não tenha sido selecionado.
    
    6.  Dê um nome ao seu certificado que seja fácil de reconhecer e clique em **Enviar**.

8.  Agora insira seu cartão inteligente em branco no leitor de cartão conectado à estação de registro e clique em **Registrar**.

9.  Quando solicitado, insira seu número de identificação pessoal (PIN) e clique em **OK**.
    
    > [!NOTE]  
    > Se o encarregado do suporte técnico não tiver dado um PIN para você registrar seu cartão inteligente, use o valor padrão de PIN de cartão inteligente, 12345678.

10. Selecione a opção para forçar o usuário (você) a alterar o PIN na primeira vez em que o cartão inteligente for usado.

11. Agora insira seu cartão inteligente em branco no leitor de cartão conectado à estação de registro e clique em **Registrar**.

12. Quando solicitado, insira seu número de identificação pessoal (PIN) e clique em **OK**.
    
    > [!NOTE]  
    > Se o encarregado do suporte técnico não tiver dado um PIN para você registrar seu cartão inteligente, use o valor padrão de PIN de cartão inteligente, 12345678.

13. Selecione a opção para forçar o usuário (você) a alterar o PIN na primeira vez em que o cartão inteligente for usado.

14. Clique em **OK** para confirmar se o certificado exibido tem suas informações neles.

15. Assim que for exibido o aviso de que o certificado foi emitido, clique em **Instalar este certificado** para concluir o processo de registro.

## Entrar no Lync com suas credenciais de cartão inteligente

Antes de usar seu cartão inteligente pela primeira vez, é recomendável que você clique em **Excluir minhas informações de entrada** na página de entrada do Lync. Fazer isso limpará qualquer credencial de entrada armazenada no computador e eliminará uma possível origem de erros.

**Para entrar no Lync com suas credenciais de cartão inteligente**

1.  Inicie o cliente do Lync.

2.  Na tela Entrar, digite seu nome de conta de usuário na caixa **Endereço de entrada** e clique em **Entrar**.

3.  Se você estiver usando um cartão inteligente virtual, ignore esta etapa.
    
    Se estiver usando um cartão inteligente físico, insira o cartão inteligente no leitor de cartão inteligente quando solicitado e então clique em **OK** quando o cartão for detectado.

4.  Digite o número PIN do seu cartão inteligente e clique em **OK**.
    
    > [!NOTE]  
    > Se você não tiver recebido um número PIN de cartão inteligente do pessoal de suporte, use o valor padrão, que é 12345678.
