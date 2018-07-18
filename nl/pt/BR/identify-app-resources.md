---



copyright:
  years: 2017
lastupdated: "2018-06-20"


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# Identificar seus recursos de aplicativo

Identifique os recursos de seu aplicativo, tais como conjuntos de origem e mecanismos de verificação de funcionamento.
 
1. Navegue para a seção **Conjuntos de origem** e clique em **Criar conjunto** para definir um novo conjunto de origem. 

   Os conjuntos de origem são recursos do servidor que entregam aplicativos para seus clientes. 
   
2. Designe um nome ao Conjunto de origem e selecione o mecanismo de verificação de funcionamento definido anteriormente. Inclua seu servidor de aplicativos como sua Origem. É possível incluir uma ou mais Origens clicando em **Incluir origem**. 

   **NOTA:** se seus servidores de aplicativos estiverem acomodados atrás de um balanceador de carga local, como um IBM Cloud Load Balancer, inclua o FQDN do balanceador de carga ou o IP virtual como sua Origem, em vez de incluir seus servidores individuais. 
   
3. Clique em **Prover recurso** para concluir a criação de seu Conjunto de origem.  

   <img src="images/Reliability6.png" alt="drawing" style="width: 300px;"/>
   
   O Conjunto de origem será inicialmente mostrado como **Sem funcionamento**. Seu estado será mudado para **Em funcionamento** após uma verificação de funcionamento bem-sucedida pelo sistema. Talvez seja necessário atualizar seu navegador para ver a mudança de estado. 
   
   <img src="images/Reliability9.png" alt="drawing" style="width: 300px;"/>
   
   **NOTA:** se você tiver múltiplas origens dentro de seu Conjunto de origem, use o limite de origem funcional para especificar o número mínimo de origens que devem estar em funcionamento antes de declarar o conjunto em funcionamento. 
   
4. Defina o mesmo número de conjuntos de origem que o de farms de aplicativos que você possuir. Essas farms podem estar dentro da mesma região geográfica ou em uma região geográfica diferente. No nosso exemplo, criaremos dois conjuntos de origem representando uma farm de aplicativos nas costas oeste e leste dos Estados Unidos. 

   <img src="images/Reliability10.png" alt="drawing" style="width: 300px;"/>
