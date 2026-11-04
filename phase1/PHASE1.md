# Phase 1: Getting to Know Wazuh

## 1. What does Wazuh do, and how does an event travel from the agent to the dashboard?

Wazuh es una plataforma de seguridad *open-source* que combina capacidades XDR (*Extended Detection and Response*) y SIEM (*Security Information and Event Management*), proporcionando a los equipos de seguridad una serie de capacidades como visibilidad unificada, análisis de logs, correlación de eventos y respuesta automatizada ante amenazas.

Para conseguir esto, Wazuh está compuesto por el agente y otros tres componentes centrales:

- **Wazuh agent**:
  - Es el software de monitorización ligero que se despliega en los *endpoints*. Es decir, es el componente de Wazuh que debe ser instalado en cualquier dispositivo final (portátil, PC, servidor, VM, etc.) del que se desea obtener información. Este agente recopila registros críticos del sistema, de las aplicaciones y datos de inventario, y los envía al Wazuh server.
- **Wazuh indexer**:
  - Es el motor de búsqueda de texto y analíticas que almacena persistentemente e indexa las alertas generadas por el Wazuh server, proporcionando datos y analíticas casi en tiempo real. Este puede ser instalado tanto en un *single host* como en múltiples nodos, requiriendo en ambos casos acceso *root*.
- **Wazuh server**:
  - Deducible de los dos puntos anteriores, este almacena temporalmente la información recogida por los Wazuh agents con el objetivo de analizarla mediante decodificadores y reglas, lanzando alertas cuando se encuentran comportamientos sospechosos o amenazas, enviándolas finalmente al Wazuh indexer. Además, se puede utilizar para configurar de forma remota dichos Wazuh agents, y es instalable tanto en *single-node* como en *multi-node*, como el Wazuh indexer.
- **Wazuh dashboard**:
  - Es la interfaz web intuitiva y flexible diseñada para analizar, explorar y visualizar los datos obtenidos por el resto de componentes, convirtiéndose en el componente central de uso de toda la arquitectura para los analistas. Se puede instalar en un nodo dedicado o junto al Wazuh indexer.

Entendiendo el comportamiento de los componentes por separado, somos también capaces de entender el comportamiento general de Wazuh y así responder a la segunda parte de la pregunta, que es cómo viaja un evento desde el agente hasta el dashboard:

1. El agente recopila la telemetría en el *endpoint* y la transmite al servidor.
2. El servidor analiza y genera los eventos, y los envía al indexador.
3. El indexador almacena persistentemente e indexa estos eventos.
4. El dashboard realiza consultas sobre los datos indexados, mostrando esos eventos y las analíticas obtenidas de ellos.



![](assets/img/p1-event-flow.png)

No se especifica en las preguntas, pero creo que cabe mencionar adicionalmente que Wazuh ofrece Wazuh Cloud, que es la versión SaaS (*Software as a Service*) alternativa a la plataforma *open-source*. Proporciona las mismas capacidades, sin necesidad de instalar y mantener los tres componentes centrales (ya que el Wazuh agent debe seguir instalándose en los endpoints para la obtención de datos) y garantiza el cumplimiento normativo con SOC 2 y PCI DSS, entre otras ventajas.



## 2. What did you try in your lab, and what did you learn from it?

### 2.1 Primera instalación

Decidí no complicar mucho la prueba, buscando no simular un ataque ni algún tipo de malware ficticio. La opción que me pareció más sensata era probar la funcionalidad FIM (*File Integrity Monitoring*).

El setup sería el siguiente: dos máquinas virtuales dentro de mi Mac. De esta forma, usaría un Ubuntu Desktop para instalar el agente como si fuera el dispositivo de algún empleado, y un Ubuntu Server donde tendría instalado el core de Wazuh: el server, el indexer y el dashboard.

![](assets/img/p1-lab-layout.png)

#### Indexer, Server y Dashboard (Ubuntu Server)

Lo primero que hice fue instalar los componentes core en la máquina Ubuntu Server. Fue principalmente seguir los comandos de la instalación asistida de la documentación.

![](assets/img/p1-first-core-ip.png)

Preparando config file:

![](assets/img/p1-first-core-config.png)

Configuración inicial:

![](assets/img/p1-first-core-certificates.png)

Instalación del indexador:

![](assets/img/p1-first-indexer-install.png)

Inicialización del clúster:

![](assets/img/p1-first-indexer-cluster-start.png)

Probando la instalación del indexer:

![](assets/img/p1-first-indexer-password.png)

En este punto, decidí utilizar Warp en mi Mac personal para conectarme por SSH al Ubuntu Server, para poder copiar y pegar fácilmente la contraseña y los comandos. Por eso la apariencia de la terminal es diferente.

![](assets/img/p1-first-indexer-check.png)

![](assets/img/p1-first-indexer-nodes.png)

También seguí la recomendación de desactivar las actualizaciones:

![](assets/img/p1-first-core-disable-updates.png)

Instalación del servidor:

![](assets/img/p1-first-server-install.png)

Instalación del dashboard:

![](assets/img/p1-first-dashboard-install.png)

Accedemos al portal:

![](assets/img/p1-first-dashboard-login.png)

![](assets/img/p1-first-dashboard-api-error.png)

Yupi :))

Se puede apreciar un error en el dashboard. Este se explica la pregunta 3 "*What was hard, and how did you get past it?"* de esta primera fase.

#### Agent (Ubuntu Desktop)

El siguiente paso fue proceder con la instalación del agente en Ubuntu Desktop, instalando la GPG key, añadiendo el repositorio y actualizando la información de los paquetes:

![](assets/img/p1-first-agent-repository.png)

![](assets/img/p1-first-agent-package-error.png)

Como me equivoqué de IP, repetí el proceso, pero el cambio no surtió efecto, así que tuve que cambiarlo manualmente:

![](assets/img/p1-first-agent-manager-retry.png)

![](assets/img/p1-first-agent-edit-config.png)

![](assets/img/p1-first-agent-manager-config.png)

![](assets/img/p1-first-agent-restart.png)

Activamos y lanzamos el servicio del agente:

![](assets/img/p1-first-agent-service-start.png)

También seguimos la recomendación de desactivar las actualizaciones:

![](assets/img/p1-first-agent-disable-updates.png)

![](assets/img/p1-first-dashboard-overview.png)

### 2.2 Segunda instalación

Como especificaré más adelante en la pregunta 3, esta primera instalación fue arreglada con IA debido a varios problemas causados por un reinicio de la máquina virtual y una instalación corrupta. Como en esta fase se especificaba que el uso de IA no estaba permitido, decidí realizar una segunda instalación desde cero. De esta forma os proveo de las dos opciones, tanto la solución personal que encontré ante los problemas de la primera instalación (junto a los aprendizajes que me llevé de ello) así como una instalación completa desde cero, sin IA, como se especificaba en la prueba.

![](assets/img/p1-second-core-ssh.png)

En esta segunda instalación voy a ser bastante más conciso ya que los pasos son los mismos que en la primera

#### Indexer, Server y Dashboard (Ubuntu Server)

El primer paso fue conectarme por SSH al Ubuntu nuevo, que, como se puede apreciar, tiene una IP diferente, y seguir el proceso de instalación.

![](assets/img/p1-second-core-download.png)

Edición del config file:

![](assets/img/p1-second-core-config.png)

 Instalación y prueba del indexer:

![](assets/img/p1-second-indexer-install-check.png)

Instalación del server y desactivación de actualizaciones:

![](assets/img/p1-second-server-install.png)

Instalación del dashboard y desactivación de actualizaciones. Como se puede apreciar el primer intento falló pero el segundo fue exitoso:

![](assets/img/p1-second-dashboard-install-retry.png)

![](assets/img/p1-second-dashboard-login.png)

![](assets/img/p1-second-dashboard-no-agents.png)

#### Agent (Ubuntu Desktop)

Ahora solo faltaría la instalación del agente, desactivar las actualizaciones y recargar el dashboard:

![](assets/img/p1-second-agent-install.png)

![](assets/img/p1-second-dashboard-agent-active.png)

### 2.3.1 Simulación FIM (*File Integrity Monitoring*) sobre primera la instalación

Una vez completado el proceso de instalación y configuración inicial, el siguiente paso consistía en simular un cambio en la VM de Ubuntu Desktop donde está instalado el agente, para posteriormente analizar el comportamiento en Wazuh.

Para ello, investigué esta funcionalidad en la documentación y en el dashboard, donde se especifica la lista de directorios donde este análisis está activado por defecto.

![](assets/img/p1-first-fim-defaults-docs.png)

![](assets/img/p1-first-fim-monitored-directories.png)

Viendo el inventario de archivos monitorizados, escogí el siguiente:

![](assets/img/p1-first-fim-file-inventory.png)

![](assets/img/p1-first-fim-delete-file.png)

![](assets/img/p1-first-fim-navigation.png)

No me salía nada, e investigando un poco más me di cuenta de que los scans se realizan por defecto cada 12h (43200s):

![](assets/img/p1-first-fim-scan-interval-docs.png)

Revisando la documentación de *real-time*, realicé la configuración para detectar los cambios en tiempo real en una carpeta personalizada "FIM-Test" bajo el directorio de documentos:

![](assets/img/p1-first-fim-test-directory.png)

Añadiría dicha carpeta a la configuración y activaría el *real-time* en ella, creando un archivo dentro y esperando que crease un evento:

![](assets/img/p1-first-fim-realtime-config.png)

Reinicio el Wazuh agent:

![](assets/img/p1-first-fim-agent-restart.png)

Compruebo que está activo y creo el fichero:

![](assets/img/p1-first-fim-create-file.png)

![](assets/img/p1-first-fim-dashboard.png)

![](assets/img/p1-first-fim-file-added.png)

Yupi :))

Además del primer objetivo fijado, que era este, me manejé por otras vistas de la aplicación intentando visualizar el resto de funcionalidades ofrece Wazuh.

![](assets/img/p1-first-malware-dashboard.png)

![](assets/img/p1-first-rootcheck-event.png)

![](assets/img/p1-first-hipaa-dashboard.png)

### 2.3.2 Simulación FIM (*File Integrity Monitoring*) sobre la segunda instalación

Ya aprendido de la primera vez, fui directamente a crear el directorio y activar la detección real-time:

![](assets/img/p1-second-fim-test-directory.png)

![](assets/img/p1-second-fim-realtime-config.png)

Creo el archivo y veo el evento:

![](assets/img/p1-second-fim-create-file.png)

![](assets/img/p1-second-fim-dashboard.png)

![](assets/img/p1-second-fim-agent-event.png)

### ¿Qué aprendí?

Los principales aprendizajes obtenidos del laboratorio son, en esencia, los practicados en el mismo. Aprendí a:

- Instalar y configurar todos los componentes de Wazuh.
  - Entender mejor cómo se interconectan  desde la  práctica, no solo la teórica.
  - Realizar configuraciones básicas en algunos de ellos.
- Manejarme por la documentación de Wazuh, con la cual no estaba familiarizado.
- Manejarme  por la interfaz de Wazuh, con la que tampoco estaba familiarizado.

## 3. What was hard, and how did you get past it?

### Problema

Los principales errores que me encontré provinieron de un fallo muy trivial: no leí bien y no me di cuenta de que, durante el primer instento de instalación de Wazuh server, **Wazuh manager había fallado**. Al haber mensajes de éxito también, solo me fijé en el final y pensaba que se había instalado correctamente, pero no fue así. Después de instalar el dashboard me daba un error respecto a la API.

![](assets/img/p1-first-dashboard-api-error.png)

Tras instalar el agente y persistiendo el error, intenté solucionarlo, lo que produjo una larga sucesión de ellos, muchos de los mismos procedentes de la misma mala decisión:  el reinicio de la máquina virtual.

Después de haber reinstalado satisfactoriamente el servidor con el manager, al intentar reinstalar el dashboard, la máquina se quedaba sin espacio, por lo que decidí ampliar el almacenamiento de la VM.  esto provocó una serie de grandes inconsistencias en el estado de instalación de Wazuh, con elementos corruptos o configuraciones perdidas, que se detallan más adelante.

### Solución

Después del reinicio tras la ampliación, algunos servicios dejaron de funcionar correctamente. El indexer no arrancaba, ya que le faltaba el directorio de logs, y tuve que restaurarlo. También tuve que restaurar el repositorio de Wazuh, que ya no estaba configurado, y también las claves.

El dashboard había quedado en un estado inconsistente tras las instalaciones fallidas y las operaciones de limpieza. Algunas de esas operaciones dejaron archivos eliminados mientras `dpkg` seguía considerando que el paquete estaba instalado. El propio script de desinstalación fallaba al intentar detener un servicio que ya no existía, por lo que tuve que modificar la línea que lo intentaba detener, añadiendo `|| true` para permitir que continuara. Otro de los problemas era que se habían perdido los archivos de configuración, y aprendí a recuperarlos utilizando una función que desconocía de dpkg, `--force-confmiss`.

Además, tuve que corregir  problemas de conectividad y de autenticación entre el dashboard, el indexer y el manager, porque las instalaciones fallidas y las limpiezas del propio instalador de Wazuh dejaron desincronizadas las contraseñas que utilizaba el dashboard para comunicarse con los otros componentes. Esto se solucionó corrigiendo la IP de conexión con el indexer y las credenciales internas de `kibanaserver` y `wazuh-wui`, consiguiendo que todos los componentes funcionaran correctamente sin necesidad de reinstalar el sistema completo. En la instalación automática, la primera vez, no había tenido problemas con esto.

### Uso de IA para la solución de los problemas

Debo mencionar que, durante todo este proceso de *troubleshooting*, utilicé ChatGPT como apoyo para solucionar toda esta serie de problemas. Soy consciente de que las instrucciones de la prueba indicaban no utilizar IA en esta primera fase y por eso quiero dejar constancia de ello.

Entiendo que el objetivo de este ejercicio era realizar una instalación manual, entendiendo las bases y el funcionamiento de los elementos de Wazuh interconectados entre sí y cómo prepararlo en un entorno funcional. No obstante, también entiendo que solucionar los errores provenientes de una instalación dañada, en un caso tan concreto como un reinicio de una máquina virtual y una ampliación de memoria, no está considerado en esta prueba.

Con todo ello, tomé mi mejor juicio y entendí que saltarme esta norma, con el objetivo de entender los problemas sin necesidad de perder tantas horas, era la decisión correcta.  la solución más directa y sencilla hubiera sido reinstalarlo desde cero con una máquina virtual limpia, pero no hubiera llegado nunca a comprender el error subyacente. Todo esto me llevó más de hora y media, y sin la IA se podría haber ido fácilmente a 6-8 horas (o más).

De la misma manera tengo que destacar que en ningún momento utilicé un agente para realizar ese trabajo por mí. Me apoyé en la IA para ayudarme a entender los logs y a generar comandos de la terminal, pero el proceso lo fui haciendo yo manualmente. Usar un agente hubiera reducido bastante el aprendizaje del proceso.

No obstante, como entiendo que esta decisión es contraria a las condiciones de la prueba, agradecería que me señalaran si les parece un enfoque erróneo y comentar esto durante la fase 5.

### Problemas menores

Además de los problemas de gran magnitud mencionados anteriormente, me encontré con diversas pequeñas dificultades a lo largo del proceso, esperables al no ser conocedor de la tecnología.

Algunas de ellas fueron no saber cómo hacer el siguiente paso y tener que buscar la documentación, no saber qué archivo de configuración cambiar para conseguir el resultado esperado, no saber dónde está en la interfaz cierto elemento, no entender alguna terminología, etc.

No obstante esto no ha sido difícil, pero quería dejar constancia también de estos  pequeños "inconvenientes" naturales al  proceso.

## 4. If you had one more day with your lab, what would you explore next, and why?

De tener más tiempo para probar todo con mayor detalle, me gustaría empezar por la configuración remota de los agentes. Si bien he llegado hasta el `agent.conf` desde el dashboard, me gustaría probarlo, enviando configuraciones a los agentes en remoto y ver cómo surten efecto.

![](assets/img/p1-agent-group-config.png)

Otra de las funcionalidades que me gustaría probar es la ejecución de un malware ficticio que actuase como uno real (o incluso uno real en un entorno bien preparado para ello), levantando las alertas para detectar su ejecución o presencia en el sistema.

Además, trataría de simular un ataque de intrusión en un endpoint y ver  cuánto tiempo tardaría en ser detectado realmente, y cómo.

No solo probaría otras funcionalidades, sino que  me gustaría entender ciertos detalles, como por ejemplo, cómo funcionan los falsos positivos. Probando los diferentes dashboards, se detectaba un archivo trojanizado (esto puede apreciarse en una de las capturas de la pregunta número 2 de esta fase 1) pero era un archivo de una máquina virtual limpia, por lo que entiendo que se trata de un falso positivo. Me adentraría más en cómo correlacionar la información de los diferentes dashboards y descubrir si hay alguna forma de marcar los falsos positivos o de hacer *dismiss* de las alertas.

Por último, también me gustaría trastear con el propio laboratorio, escalando lo que ya tengo montado, o montando desde cero un setup completamente diferente: añadir más máquinas virtuales, hacer el servidor multinodo en lugar de con un solo host, almacenar en diferentes nodos el dashboard, el server y el indexer, etc.
