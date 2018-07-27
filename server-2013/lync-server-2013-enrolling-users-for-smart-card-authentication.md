---
title: Registrando usuários para a autenticação de cartão inteligente
TOCTitle: Registrando usuários para a autenticação de cartão inteligente
ms:assetid: a6445a83-a94b-423f-ba2a-12b5f84c5d75
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn308570(v=OCS.15)
ms:contentKeyID: 56270458
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Registrando usuários para a autenticação de cartão inteligente

 

_**Tópico modificado em:** 2016-12-08_

Em geral, há dois métodos para registrar usuários para autenticação de cartão inteligente. O método mais fácil envolve ter usuários registrados diretamente para autenticação de cartão inteligente usando o registro via Web, enquanto o método mais complexo envolve o uso de um agente de registro. Este tópico se concentra no autorregistro para certificados de cartões inteligentes.

Para obter mais informações sobre o registro em nome de usuários como um agente de registro, consulte Registrar-se para certificados em nome de outros usuários[http://go.microsoft.com/fwlink/p/?LinkID=313367](http://go.microsoft.com/fwlink/p/?linkid=313367).

## Para registrar usuários para autenticação de cartão inteligente

1.  Faça o logon na estação de trabalho com o Windows 8 usando as credenciais de um usuário habilitado no Lync.

2.  Inicie o Internet Explorer.

3.  Acesse a página **Inscrição na Web de Autoridade de Certificação** (por exemplo, https://MinhaCA.contoso.com/certsrv).
    
    > [!NOTE]  
    > Caso esteja usando o Internet Explorer 10, pode ser necessário visualizar esta página em Modo de Compatibilidade.

4.  Na **Página Inicial**, selecione **Solicitar um certificado**.

5.  Em seguida, selecione **Solicitação Avançada**.

6.  Selecione **Criar e enviar uma solicitação para esta autoridade de certificação**.

7.  Selecione **Usuário do Cartão Inteligente** na seção **Modelo de Certificado** e preencha a solicitação de certificado avançado com os seguintes valores:
    
      - As **Opções de Chave** confirmam as seguintes configurações:
        
          - Selecione o botão de opção **Criar novo conjunto de chaves**
        
          - Em **CSP**, selecione **Microsoft Base Smart Card Crypto Provider**
        
          - Em **Uso da Chave**, selecione **Exchange** (é a única opção disponível).
        
          - Em **Tamanho da Chave**, digite **2048**
        
          - Confirme se a opção **Nome de contêiner de chave automático** está selecionada
        
          - Deixe as outras caixas desmarcadas.
    
      - Em **Opções Adicionais**, confirme os seguintes valores:
        
          - Em **Formato da Solicitação**, selecione **CMC**.
        
          - Em **Algoritmo de Hash**, selecione **sha1**.
        
          - Em **Nome Amigável**, digite **Certificado de Cartão Inteligente**.

8.  Caso você esteja usando um leitor de cartão inteligente físico, insira o cartão inteligente no dispositivo.

9.  Clique em **Enviar** para enviar a solicitação do certificado.

10. Quando solicitado, digite o PIN usado para criar o cartão inteligente virtual.
    
    > [!NOTE]  
    > O PIN padrão do cartão inteligente virtual é ‘12345678’.

11. Depois que o certificado tiver sido emitido, clique em **Instalar este certificado** para concluir o processo de registro.
    
    > [!NOTE]  
    > Caso sua solicitação de certificado falhe com o erro “Este navegador da Web não dá suporte à geração de solicitações de certificados”, há três maneiras possíveis para resolver o problema:    <ol>    
> <li><p>Habilitar o Modo de Exibição de Compatibilidade no Internet Explorer</p></li>    
> 
> <li><p>Habilitar a opção Ativar configurações de Intranet no Internet Explorer</p></li>    
> 
> 
> <li><p>Selecionar a configuração Restaurar o nível padrão de todas as zonas na guia Segurança no menu de opções do Internet Explorer.</p></li>    </ol>

