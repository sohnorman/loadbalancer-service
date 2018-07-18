---

copyright:
  years: 2017
lastupdated: "2018-04-13"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}


# Introdução
Para começar a usar o IBM Cloud Load Balancer, você precisará de dois itens principais:

* Uma conta com a IBM: [IBMid](https://www.ibm.com/account/us-en/signup/register.html)
* Um servidor IBM, [Bare Metal](https://console.bluemix.net/docs/bare-metal/about.html#getting-started-with-bare-metal-servers) ou [Virtual Server Instance (VSI)](https://console.bluemix.net/docs/vsi/vsi_index.html#getting-started-with-virtual-servers)
 
Se você precisar de assistência na obtenção de uma conta **IBMid**, entre em contato com o [Representante de vendas IBM](https://www.ibm.com/cloud-computing/bluemix/contact-us) para obter orientação adicional.

Se você tiver uma conta existente do IBM Cloud Infrastructure (SoftLayer), será possível [vincular sua conta](https://console.bluemix.net/docs/account/softlayerlink.html#unifyingaccounts) a seu IBMid. 

## Solicitando um balanceador de carga

Para solicitar um serviço IBM Cloud Load Balancer, selecione **Rede > Load Balancers > IBM Cloud Load Balancer** no [Catálogo do IBM Cloud](https://console.bluemix.net/catalog/infrastructure/load-balancer-group). Efetue login ou crie uma nova conta, em seguida, execute o procedimento a seguir:

1. Selecione seu data center e revise o plano de serviço. Clique em **Avançar**.
2. Selecione a sub-rede na qual gostaria de implementar o balanceador de carga. A instância do serviço de balanceador de carga terá uma de suas interfaces de rede nesta sub-rede. Assegure-se de que seus servidores de aplicativos estejam nessa sub-rede ou sejam acessíveis nessa sub-rede. Se necessário, ative a ampliação da VLAN. Clique em **Avançar**.
3. Defina seus parâmetros de serviço básico, como o nome, a descrição, os protocolos e as portas do aplicativo front-end e backend, além do método de balanceamento de carga. É possível definir no máximo dois protocolos durante a criação de serviço inicial. É possível definir até dez protocolos após a criação do serviço. Deve-se também usar uma porta front-end exclusiva. Clique em **Avançar**.
4. Ajuste os parâmetros de verificação de funcionamento, se desejado, caso contrário, use as configurações padrão. Clique em **Avançar**.
5. Associe uma ou mais instâncias do servidor utilizadas com o balanceador de carga. Você só verá instâncias do servidor locais para seu data center. Clique em **Avançar**.
6. Revise a página de resumo e, em seguida, clique em **Criar**. 


A página de resumo exibe a instância do serviço de balanceador de carga recém-criada. Observe o campo **Status**. Um status de `Offline` sugere que o balanceador de carga não está em serviço. Nenhuma nova configuração poderá ser feita e nenhum serviço de balanceamento de carga poderá ser fornecido até que seu status mude para `Online`. Talvez seja necessário atualizar sua tela para ver o status atual.
 
Clicar no nome do serviço nessa página o levará para a página de visão geral do serviço. Será possível navegar para as guias **Protocolos**, **Verificações de funcionamento** e **Instâncias do servidor** para editar sua configuração existente.
