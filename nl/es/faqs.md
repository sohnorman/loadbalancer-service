---

copyright:
  years: 2017
lastupdated: "2018-03-14"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}

# Preguntas más frecuentes

Esta sección contiene respuestas a algunas preguntas frecuentes sobre el servicio de equilibrador de carga de IBM Cloud.

## ¿Cuántas opciones de equilibrio de carga hay disponibles en {{site.data.keyword.BluSoftlayer_notm}}?

Para obtener una comparación detallada de las ofertas de equilibradores de carga de IBM, consulte [Explorar los equilibradores de carga](https://dev-console.bluemix.net/docs/infrastructure/loadbalancer-service/explore-load-balancers.html#explore-load-balancers).

## ¿Puedo utilizar un nombre DNS distinto para mi equilibrador de carga?

Aunque el nombre DNS auto-asignado para el equilibrador de carga no es personalizable, puede añadir un registro CNAME (nombre canónico) que apunte a su nombre DNS preferido para el nombre DNS del equilibrador de carga auto-asignado. Por ejemplo, su número de cuenta es 123456, su equilibrador de carga se despliega en el centro de datos "dal09" y su nombre es "myapp", el nombre DNS del equilibrador de carga auto-asignado es "myapp-123456-dal09.lb.bluemix.net". Su nombre DNS preferido es "www.myapp.com". Puede añadir un registro CNAME (a través del proveedor de DNS que utilice para gestionar myapp.com) que apunte "www.myapp.com" al nombre DNS del equilibrador de carga "myapp-12345-dal09.lb.bluemix.net".

## ¿Cuál es el número máximo de puertos virtuales que puedo definir con mi servicio de equilibrador de carga?

Al crear un nuevo servicio de equilibrador de carga, puede definir hasta dos puertos virtuales. Puede definir puertos virtuales adicionales después de haber creado el servicio. El número máximo de puertos virtuales permitido es de 10. 

## ¿Cuál es el número máximo de instancias de cálculo que puedo asociar con mi equilibrador de carga?

50.

## ¿Cuáles son los valores predeterminados y los permitidos para los distintos parámetros de comprobación de estado?

Los valores predeterminados y los permitidos se enumeran a continuación:

* **Intervalo de comprobación de estado:** el valor predeterminado es de 5 segundos, el rango oscila entre 2 y 60 segundos
* **Tiempo de espera de respuesta de la comprobación de estado:** el valor predeterminado es de 2 segundos, el rango oscila entre 1 y 59 segundos
* **Número máximo de reintentos:** El valor predeterminado es de 2 reintentos y el rango oscila de 1 a 10 reintentos

**NOTA:** el valor de tiempo de espera de la respuesta de comprobación de estado siempre debe ser inferior al valor del intervalo de la comprobación de estado. 

## ¿Puedo utilizar instancias de cálculo que residan en centros de datos remotos con este servicio? 

Le recomendamos que el servicio de equilibrador de carga y las instancias de cálculo residan localmente en el mismo centro de datos. La interfaz gráfica de usuario (GUI) del servicio de equilibrador de carga no muestra las instancias de cálculo de otros centros de datos remotos. Con todo, la GUI puede incluir instancias de cálculo de otros centros de datos de la misma ciudad (por ejemplo, centros de datos cuyos nombres compartan las tres primeras letras, como DALxx). De todas formas, se puede utilizar la interfaz de la API para añadir instancias de cálculo desde cualquier centro de datos remoto. 

## ¿Qué versión de TLS se soporta con la descarga SSL?

El servicio Cloud Load Balancer soporta TLS 1.2 con terminación de SSL. 

En la siguiente lista, se enumeran los cifrados soportados (listados en orden de precedencia):  

* ECDHE-RSA-AES256-GCM-SHA384
* ECDHE-RSA-AES256-SHA384
* AES256-GCM-SHA384
* AES256-SHA256
* ECDHE-RSA-AES128-GCM-SHA256
* ECDHE-RSA-AES128-SHA256
* AES128-GCM-SHA256
* AES128-SHA256

## ¿Cuál es el número máximo de instancias de servicio del equilibrador de carga que puedo crear en mi cuenta? 

Actualmente, puede crear un máximo de 20 instancias de servicio. Si necesita más instancias, póngase en contacto con el soporte de IBM. 

## ¿Puede utilizarse el servicio de equilibrador de carga de IBM Cloud con VMware? 

Las máquinas virtuales VMware que tienen asignadas direcciones privadas portátiles de SoftLayer se pueden especificar como servidores back-end en el equilibrador de carga. Esta característica actualmente solo está disponible utilizando la API, y no por la interfaz de usuario web (GUI). Las IP privadas portátiles añadidas mediante la API aparecen como "Desconocidas" en la GUI, ya que no han sido asignadas por SoftLayer. Tenga en cuenta que esta clase de configuración se puede utilizar con otros hipervisores, como Xen y KVM.

Las direcciones no SoftLayer asignadas por máquinas virtuales VMware (como con las redes VMware NSX) no se pueden añadir directamente como servidores back-end al equilibrador de carga. Sin embargo, en función de su configuración, es posible configurar un intermediario, como una pasarela NSX, que tenga una dirección privada de SoftLayer como el servidor back-end para el equilibrador de carga (con los servidores reales siendo máquinas virtuales conectadas a red(es) gestionadas por VMware NSX).

## Si elijo utilizar una VLAN pública bajo mi cuenta para desplegar mi equilibrador de carga y tengo un cortafuegos desplegado en mi VLAN pública, ¿qué configuraciones requiere mi cortafuegos para que funcione con el servicio de equilibrador de carga?

El puerto TCP 56501 se utiliza para la gestión. Asegúrese de que el tráfico a este puerto, así como los puertos de su aplicación, no estén bloqueados por su cortafuegos, de lo contrario el suministro del equilibrador de carga fallará.

## ¿Qué debo hacer si obtengo un error "Esta cuenta de SoftLayer no está enlazada a ninguna cuenta de Bluemix"?

Compruebe que la cuenta de SoftLayer está enlazada con la cuenta de Bluemix. Consulte [Enlace de Softlayer](https://console.bluemix.net/docs/account/softlayerlink.html#switching-to-ibmid) para obtener más instrucciones.
