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

# Identificar los recursos de la aplicación

Identifique los recursos de la aplicación, como las agrupaciones de origen y los mecanismos de comprobación de estado.
 
1. Vaya a la sección **Agrupaciones de origen** y pulse **Crear agrupación** para definir una nueva agrupación de origen. 

   Las agrupaciones de origen son recursos de servidor que proporcionan aplicaciones a sus clientes. 
   
2. Asigne un nombre a la agrupación de origen y seleccione el mecanismo de comprobación de estado definido anteriormente. Añada el servidor de aplicaciones como Origen. Puede añadir uno o varios orígenes pulsando **Añadir origen**. 

   **NOTA:** Si los servidores de aplicaciones están ubicados detrás de un equilibrador de carga local como, por ejemplo, un IBM Cloud Load Balancer, añada el FQDN o la IP virtual del equilibrador de carga como su Origen en lugar de añadir los servidores individuales. 
   
3. Pulse **Suministrar recurso** para completar la creación de la agrupación de origen.  

   <img src="images/Reliability6.png" alt="drawing" style="width: 300px;"/>
   
   Inicialmente, la agrupación de origen se mostrará como **En mal estado**. Su estado cambiará a **En buen estado** tras de una comprobación de estado satisfactoria por parte del sistema. Es posible que deba renovar el navegador para ver el cambio de estado. 
   
   <img src="images/Reliability9.png" alt="drawing" style="width: 300px;"/>
   
   **NOTA:** Si tiene varios orígenes dentro de la agrupación de origen, utilice el umbral de origen correcto para especificar el número mínimo de orígenes que estar en buen estado antes de declarar la agrupación en buen estado. 
   
4. Defina tantas agrupaciones de origen como granjas de aplicaciones tenga. Estas granjas pueden estar dentro de las mismas regiones geográficas o estar en distintas regiones. En nuestro ejemplo, crearemos dos agrupaciones de origen que representan una granja de aplicaciones en las costas este y oeste de Estados Unidos. 

   <img src="images/Reliability10.png" alt="drawing" style="width: 300px;"/>
