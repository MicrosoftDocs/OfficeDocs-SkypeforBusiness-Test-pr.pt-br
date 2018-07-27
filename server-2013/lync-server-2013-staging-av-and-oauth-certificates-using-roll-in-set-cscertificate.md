---
title: Adaptando Certificados AV e OAuth Usando no Lync Server 2013 -Roll in Set-CsCertificate
TOCTitle: Adaptando Certificados AV e OAuth Usando no Lync Server 2013 -Roll in Set-CsCertificate
ms:assetid: 22dec3cc-4b6b-4df2-b269-5b35df4731a7
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ660292(v=OCS.15)
ms:contentKeyID: 49886134
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Adaptando Certificados AV e OAuth Usando no Lync Server 2013 -Roll in Set-CsCertificate

 

_**Tópico modificado em:** 2012-11-13_

Comunicações de áudio/vídeo (A/V) é um principal componente do Microsoft Lync Server 2013. Recursos como compartilhamento de aplicativos e conferência de áudio e vídeo dependem dos certificados atribuídos ao Serviço de Borda A/V, especificamente o serviço de Autenticação A/V.

> [!IMPORTANT]  
> <ol>
> 
> <li><p>Este novo recurso é projetado para funcionar com o Serviço de Borda A/V e o certificado <em>OAuthTokenIssuer</em>. Outros tipos de certificados podem ser provisionados junto com o Serviço de Borda A/V e o tipo de certificado OAuth, mas não serão beneficiados com o comportamento de coexistência que o certificado do Serviço de Borda A/V será.</p></li>
> 
> 
> <li><p>Os cmdlets do Shell de Gerenciamento do Lync Server PowerShell usados para gerenciar certificados do Microsoft Lync Server 2013 referem-se ao certificado do Serviço de Borda A/V como o tipo de certificado <em>AudioVideoAuthentication</em> e o certificado OAuthServer como o tipo <em>OAuthTokenIssuer</em>. Para o resto deste tópico e para identificar exclusivamente os certificados, eles serão referidos pelo mesmo tipo de identificador, <em>AudioVideoAuthentication</em> e <em>OAuthTokenIssuer</em>.</p></li></ol>


O serviço de Autenticação A/V é responsável por emitir tokens que são usados por clientes e outros consumidores A/V. Os tokens são gerados de atributos no certificado e, quando o certificado expira, a perda de conexão e o requisito para participar novamente com um novo token gerado pelo novo certificado resultará. Um novo recurso no Lync Server 2013 reduzirá este problema – a capacidade de inserir um novo certificado antes do antigo expirar e permitir que ambos continuem a funcionar por um período de tempo. Este recurso usa a funcionalidade atualizada no cmdlet Set-CsCertificate Shell de Gerenciamento do Lync Server. O novo parâmetro –Roll, com o parâmetro existente –EffectiveDate, substituirá o novo certificado AudioVideoAuthentication no repositório de certificados. O certificado AudioVideoAuthentication mais antigo permanecerá para tokens emitidos serem validados. Começando a colocar o novo certificado AudioVideoAuthentication, a seguinte série de eventos ocorrerá:


> [!TIP]
> Usando os cmdlets do Shell de Gerenciamento do Lync Server para gerenciar certificados, é possível solicitar certificados diferentes para cada objetivo no Servidor de Borda. Usar o Assistente de Certificados no Assistente de Implantação do Lync Server ajuda na criação de certificados, mas é geralmente um tipo <STRONG>padrão</STRONG> que agrupam todos os certificados usados para o Servidor de Borda em um único certificado. A prática recomendada que você usará o recurso de agrupamento de certificado é desagrupar o certificado AudioVideoAuthentication de outros objetivos. É possível provisionar e dividir um certificado do tipo Padrão, mas apenas a parte do AudioVideoAuthentication do certificado combinado será beneficiada da separação. Um usuário envolvido em (por exemplo) uma conversa de mensagem instantânea quando o certificado vencer precisará fazer o logoff e login para usar o novo certificado associado com o Serviço de Borda de Acesso. Irá ocorrer um comportamento semelhante para um usuário envolvido em uma conferência da Web usando o Serviço de Borda de Webconferência. O certificado OAuthTokenIssuer é um tipo específico compartilhado em todos os servidores. Você cria e gerencia o certificado em um local e o certificado é armazenado no Repositório de Gerenciamento Central para todos os outros servidores.



Detalhes adicionais são necessários para compreender totalmente suas opções e requisitos ao usar o cmdlet Set-CsCertificate e usá-lo para dividir certificados antes do vencimento do certificado atual. O parâmetro –Roll é importante, mas tem essencialmente um único objetivo. Se você defini-lo como um parâmetro, está dizendo ao Set-CsCertificate que você irá fornecer informações sobre o certificado que será afetado definido pelo –Type (por exemplo, AudioVideoAuthentication e OAuthTokenIssuer), quando o certificado se tornar efetivamente definido por -EffectiveDate

**-Roll:** O parâmetro –Roll é necessário e possui dependências que devem ser fornecidas com ele. Os parâmetros necessários para definir completamente quais certificados serão afetados e como eles serão aplicados:

**-EffectiveDate:** O parâmetro –EffectiveDate define quando o novo certificado se tornará co-ativo com o certificado atual. O –EffectiveDate pode estar próximo do tempo de vencimento do certificado atual ou pode ser um período de tempo mais longo. Um mínimo recomendado –EffectiveDate para o certificado AudioVideoAuthentication será de 8 horas, que é o tempo do token padrão para os tokens de serviço de Borda AV emitidos usando o certificado AudioVideoAuthentication.

Ao separar certificados OAuthTokenIssuer, há requisitos diferentes para o tempo limite antes do certificado se tornar efetivo. O tempo mínimo que o certificado OAuthTokenIssuer deve ter para este tempo limite é de 24 horas antes do tempo de vencimento do certificado atual. O tempo limite estendido para coexistência é por causa de outras funções do servidor que dependem do certificado OAuthTokenIssuer (por exemplo, Exchange Server) que possui um tempo de retenção maior para autenticação criada por certificado e materiais da chave de criptografia.

**-Thumbprint:** O thumbprint é um atributo no certificado que é exclusivo para ele. O parâmetro –Thumbprint é usado para identificar o certificado que será afetado pelas ações do cmdlet Set-CsCertificate.

**-Type:** O parâmetro –Type pode aceitar um único tipo de uso de certificado ou uma lista separada por vírgulas de tipos de uso de certificado. Os tipos de certificado são aqueles que identificam para o cmdlet e para o servidor qual o objetivo do certificado. Por exemplo, digite AudioVideoAuthentication para o uso pelo Serviço de Borda A/V e o serviço de Autenticação AV. Se você decidir dividir e provisionar certificados de um tipo diferente ao mesmo tempo, você deve considerar o tempo limite efetivo mínimo necessário para certificados. Por exemplo, você precisa separar certificados do tipo AudioVideoAuthentication e OAuthTokenIssuer. Seu –EffectiveDate mínimo deve ser maior do que dois certificados, neste caso o OAuthTokenIssuer, que possui um tempo limite mínimo de 24 horas. Se você não deseja separar o certificado AudioVideoAuthentication com um tempo limite de 24 horas, separe-o separadamente com um EffectiveDate superior aos seus requisitos.

## Para atualizar ou renovar um certificado Serviço de Borda A/V com os parâmetros –Roll e -EffectiveDate

1.  Faça logon no computador local como membro do grupo Administradores.

2.  Solicitar uma renovação ou novo certificado AudioVideoAuthentication com a chave privada exportável para o certificado existente no Serviço de Borda A/V.

3.  Importar o novo certificado AudioVideoAuthentication para o Servidor de Borda e todos os outros Servidor de Borda em seu pool (se você implantou um pool).

4.  Configurar o certificado importado com o cmdlet Set-CsCertificate e usar o parâmetro –Roll com o parâmetro –EffectiveDate. A data efetiva deve ser definida como o tempo de expiração do certificado atual (14:00:00 ou 2:00:00 PM) menos o tempo de vida do token (por padrão, oito horas). Isto nos fornece um tempo que o certificado deve ser definido para ativo e é o –EffectiveDate \<string\>: “22/7/2012 6:00:00 AM”.
    
    > [!IMPORTANT]  
    > Para um Pool de borda, você deve ter todos os certificados AudioVideoAuthentication implantados e provisionados pela data e hora definida pelo parâmetro –EffectiveDate do primeiro certificado implantado para evitar possíveis interrupções das comunicações A/V devido ao vencimento do certificado mais antigo antes que todos os tokens dos clientes e consumidores sejam renovados usando o novo certificado.    
    O comando Set-CsCertificate com o parâmetro –Roll e –EffectiveTime:
    
        Set-CsCertificate -Type AudioVideoAuthentication -Thumbprint <thumb print of new certificate> -Roll -EffectiveDate <date and time for certificate to become active>
    
    Um exemplo de comando Set-CsCertificate:
    
        Set-CsCertificate -Type AudioVideoAuthentication -Thumbprint "B142918E463981A76503828BB1278391B716280987B" -Roll -EffectiveDate "7/22/2012 6:00:00 AM"
    
    > [!IMPORTANT]  
    > A EffectiveDate deve ser formatada para corresponder às configurações de idioma e região do seu servidor. O exemplo usa as configurações de Idioma e Região Inglês dos EUA

Para compreender ainda mais o processo que o Set-CsCertificate, -Roll e –EffectiveDate usam para dividir um novo certificado para emissão de novos tokens AudioVideoAuthentication enquanto ainda usa um certificado existente para validar o AudioVideoAuthentication que está em uso por consumidores, um prazo visual é um meio eficaz de compreender o processo.

No exemplo a seguir, o administrador determina que o certificado do Serviço de Borda A/V irá expirar as 14:00:00 PM em 22/07/2012. Ele solicita e recebe um novo certificado e o importa para cada Servidor de Borda no seu pool. As 2 AM de 22/07/2012, ele começa a executar o Get-CsCertificate com –Roll, -Thumbprint igual a sequência thumbprint do novo certificado e –EffectiveTime definido para 22/07/2012 6:00:00 AM. Ele executa este comando em cada Servidor de Borda.

![Usando os parâmetros Roll e EffectiveDate.](images/JJ660292.21d51a76-0d03-4ed7-a37e-a7c14940265f(OCS.15).jpg "Usando os parâmetros Roll e EffectiveDate.")

Quando a hora efetiva é atingida (22/7/2012 6:00:00 AM), todos os novos tokens são emitidos pelo novo certificado. Ao validar tokens, eles serão primeiro validados no novo certificado. Se a validação falhar, o certificado antigo é testado. O processo de testar o novo e retornar para o certificado antigo continuará até o tempo de expiração do certificado antigo. Quando o certificado antigo expirar (22/7/2012 14:00:00 PM), os tokens serão validados apenas pelo novo certificado. O certificado antigo pode ser removido com segurança usando o cmdlet Remove-CsCertificate com o parâmetro –Previous.

    Remove-CsCertificate -Type AudioVideoAuthentication -Previous

## Para atualizar ou renovar um certificado OAuthTokenIssuer com parâmetros –Roll e -EffectiveDate

1.  Faça logon no computador local como membro do grupo Administradores.

2.  Solicitar u ma renovação ou um novo certificado OAuthTokenIssuer com uma chave privada exportável para o certificado existente no Serviço de Borda A/V.

3.  Importar o novo certificado OAuthTokenIssuer para um Servidor Front-End em seu pool (se você tem um pool implantado). O certificado OAuthTokenIssuer é replicado globalmente e apenas precisa ser atualizado ou renovado em qualquer servidor da sua implantação. O Servidor Front-End é usado como um exemplo.

4.  Configurar o certificado importado com o cmdlet Set-CsCertificate e usar o parâmetro –Roll com o parâmetro –EffectiveDate. A data efetiva deve ser definida como o tempo de expiração do certificado atual (14:00:00 ou 2:00:00 PM) menos um mínimo de 24 horas.
    
    O comando Set-CsCertificate com o parâmetro –Roll e –EffectiveTime:
    
        Set-CsCertificate -Type OAuthTokenIssuer -Thumbprint <thumb print of new certificate> -Roll -EffectiveDate <date and time for certificate to become active>
    
    Um comando Set-CsCertificate de exemplo:
    
        Set-CsCertificate -Type OAuthTokenIssuer -Thumbprint "B142918E463981A76503828BB1278391B716280987B" -Roll -EffectiveDate "7/21/2012 1:00:00 PM"
    
    > [!IMPORTANT]  
    > O EffectiveDate deve ser formatado para corresponder às configurações de idioma e região do seu servidor. O exemplo usa as configurações de Idioma e Região Inglês dos EUA

Quando a hora efetiva é atingida (21/7/2012 1:00:00 AM), todos os novos tokens são emitidos pelo novo certificado. Ao validar tokens, os tokens serão validados primeiro no novo certificado. Se a validação falhar, o certificado antigo é testado. O processo de teste do novo certificado e retorno ao certificado antigo continuará até o tempo de expiração do certificado antigo. Quando o certificado antigo vencer (22/7/2012 14:00:00 PM), os tokens serão validados apenas pelo novo certificado. O certificado antigo pode ser removido com segurança usando o cmdlet Remove-CsCertificate com o parâmetro –Previous.

    Remove-CsCertificate -Type OAuthTokenIssuer -Previous

## Consulte Também

#### Conceitos

[Planejar certificados do Servidor de Borda no Lync Server 2013](lync-server-2013-plan-for-edge-server-certificates.md)  
[Gerenciando autenticação de servidor para servidor (Oauth) e inscrições de parceiros no Lync Server 2013](lync-server-2013-managing-server-to-server-authentication-oauth-and-partner-applications.md)  

#### Outros Recursos

[Configurar certificados de Borda para Lync Server 2013](lync-server-2013-set-up-edge-certificates.md)  
[Set-CsCertificate](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsCertificate)  
[Remove-CsCertificate](https://docs.microsoft.com/en-us/powershell/module/skype/Remove-CsCertificate)

