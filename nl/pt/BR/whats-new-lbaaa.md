---

copyright:
  years: 2017
lastupdated: "2018-05-01"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}


# Novidades

Descubra os recursos novos e atualizados no IBM Cloud Load Balancer.

## Abril de 2018
### Escala horizontal
O IBM Cloud Load Balancer agora tem a capacidade aumentada automaticamente quando o carregamento aumenta (e diminui à medida que o carregamento diminui). Quando o balanceador de carga é criado, ele começa com dois dispositivos, mas o número de dispositivos pode aumentar (para 16, a partir dessa gravação), pois nosso sistema de monitoramento detecta um aumento no carregamento. Os endereços IP de cada um dos dispositivos ativos são incluídos como DNS A-Records para o Nome completo do domínio (FQDN) do balanceador de carga.

### Balanceador de carga interno
Uma versão "interna" altamente pedida de nosso IBM Cloud Load Balancer está disponível agora. Esse Balanceador de carga não está exposto publicamente, mas ainda pode ser usado para balancear a carga dos aplicativos dentro de suas redes privadas do IBM Cloud (em uma implementação com multicamadas, por exemplo, como mostrado na figura). Ele é seguro e consistente com as versões anteriores do IBM Cloud Load Balancer no lado público. 

![Balanceador de carga interno](./images/InternalLB.png)

### Monitorando métricas
Agora é possível alavancar o serviço "IBM Cloud Monitoring" para monitorar as métricas de desempenho a seguir associadas ao balanceador de carga e ao aplicativo:

* Rendimento
* Taxa de conexão
* Conexões ativas

![Monitorando métricas](./images/Metrics.png)

Até duas semanas de amostras são coletadas e exibidas pela IU da web do balanceador de carga. Os dados também podem ser visualizados no portal de serviço IBM Cloud Monitoring. Se você precisar de dados por mais de duas semanas, dependendo do volume de outras métricas de nuvem que estiver enviando para a sua instância do Cloud Monitoring, talvez seja necessário fazer upgrade de seu plano de monitoramento.

Esse recurso requer que suas contas do IBM Cloud IaaS e PaaS sejam vinculadas, com algumas [etapas simples](https://console.bluemix.net/docs/account/linking_accounts.html#unifyingaccounts). 

### Customização do conjunto de cifras
Agora é possível customizar os conjuntos de cifras que são usados quando o balanceador de carga está configurado para executar a finalização de SSL.

Quando você ativa a finalização de SSL no IBM Cloud Load Balancer (selecionando HTTPS como o protocolo de front-end), ativamos um conjunto padrão cuidadosamente selecionado de conjuntos de cifras que estão em conformidade com as melhores práticas de segurança. Observamos atentamente quaisquer novas vulnerabilidades que possam ser descobertas e atualizamos a lista adequadamente. Isso, junto com atualizações de segurança contínuas de componentes de software e hardware, ajuda a manter seus aplicativos seguros em todos os momentos.
