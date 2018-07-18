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


# Novedades

Obtenga información sobre las características nuevas y actualizadas de IBM Cloud Load Balancer.

## Abril de 2018
### Escalado horizontal
IBM Cloud Load Balancer ahora se escala automáticamente cuando aumenta la carga (y se reduce a medida que se reduce la carga). Cuando se crea el equilibrador de carga, empieza con dos dispositivos, pero el número de dispositivos puede subir (hasta 16, en este momento) a medida que nuestro sistema de supervisión detecta un incremento de la carga. Las direcciones IP de cada uno de los dispositivos activos se añaden como registros A DNS al nombre de dominio completo (FQDN) del equilibrador de carga.

### Equilibrador de carga interno
Ya está disponible una versión "interna" muy solicitada de nuestro IBM Cloud Load Balancer. Este Load Balancer no está expuesto públicamente, pero se puede seguir utilizando para equilibrar la carga de las aplicaciones dentro de sus redes privadas de IBM Cloud (en un despliegue de varios niveles, por ejemplo, tal como se muestra en la imagen). Es seguro y coherente con las versiones anteriores de IBM Cloud Load Balancer de la parte pública. 

![Equilibrador de carga interno](./images/InternalLB.png)

### Supervisión de métricas
Ahora puede optimizar el servicio "IBM Cloud Monitoring" para supervisar las siguientes medidas de rendimiento asociadas con el equilibrador de carga y la aplicación:

* Rendimiento
* Velocidad de conexión
* Conexiones activas

![Supervisión de métricas](./images/Metrics.png)

La interfaz de usuario web del equilibrador de carga recopila y muestra hasta dos semanas de ejemplos. Los datos también se pueden visualizar en el portal del servicio IBM Cloud Monitoring. Si requiere datos de más de dos semanas, en función del volumen de otras métricas de nube que esté enviando a la instancia de Cloud Monitoring, es posible que deba actualizar su plan de supervisión.

Esta característica requiere que se enlacen las cuentas de IaaS y PaaS de IBM Cloud, mediante unos pocos [pasos sencillos](https://console.bluemix.net/docs/account/linking_accounts.html#unifyingaccounts). 

### Personalización de las suites de cifrado
Ahora puede personalizar las suites de cifrado que se utilizan cuando el equilibrador de carga está configurado para realizar la terminación SSL.

Cuando habilita la terminación SSL en IBM Cloud Load Balancer (seleccionando HTTPS como protocolo frontal), se habilita un conjunto predeterminado y cuidadosamente seleccionado de suites de cifrado que se ajustan a las prácticas recomendadas de seguridad. Seguimos de cerca las nuevas vulnerabilidades que se puedan descubrir y vamos actualizando la lista en consecuencia. Esto, junto con las actualizaciones de seguridad de componentes de software y hardware, ayuda a mantener las aplicaciones seguras en todo momento.
