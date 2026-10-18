Informe de Auditoría de Red Wi-Fi Insegura
1. Introducción
El objetivo de esta práctica es analizar los riesgos de utilizar el protocolo HTTP en una red Wi-Fi pública, identificar qué información puede observarse durante una solicitud web y explicar cómo una VPN puede proteger el tráfico de red.
Para realizar el análisis se utilizó el sitio NeverSSL y las herramientas de desarrollador del navegador. También se propone complementar la observación con Wireshark para examinar los paquetes que circulan durante una conexión HTTP.
2. Sitio analizado
- Sitio: http://neverssl.com
- Host observado: majesticshininglushplan.neverssl.com
- Protocolo de aplicación: HTTP
- Método de solicitud: GET, si se confirma en la solicitud capturada.
- Estado observado: 200 OK, según la observación realizada en el navegador.
NeverSSL es un sitio pensado para permitir conexiones HTTP sin cifrado, lo que facilita estudiar la información que puede quedar expuesta durante una comunicación web.
3. Evidencia observada
3.1. Herramientas de desarrollador del navegador

<img width="1029" height="676" alt="image" src="https://github.com/user-attachments/assets/482f54b1-e416-4198-b798-5e21b9409969" />
 
Para inspeccionar la solicitud se utilizaron las herramientas de desarrollador:
1. Se abrió el sitio indicado.
2. Se presionó F12 para abrir las herramientas.
3. Se seleccionó la pestaña Network (Red).
4. Se recargó la página.
5. Se seleccionó la solicitud correspondiente al sitio.
Durante la observación se identificaron los siguientes datos:
Elemento	Resultado
URL	http://majesticshininglushplan.neverssl.com/online/
Host	freshgoodyoungtreasure.neverssl.com
Código de estado	200 OK
Método HTTP	Completar con el valor mostrado en Network
Protocolo	HTTP, sin cifrado TLS en esa solicitud los encabezados (headers) que deben revisarse en la solicitud incluyen, por ejemplo, Host, User-Agent, Accept y Accept-Language, siempre que aparezcan en la captura realizada.
Evidencia pendiente de adjuntar: captura de la pestaña Network donde se vean la URL, el método, el estado y los encabezados de la solicitud.
3.2. Análisis complementario con Wireshark

Wireshark permite capturar y examinar paquetes que circulan por una interfaz de red. Para esta práctica, el análisis debe limitarse al tráfico propio generado al visitar el sitio.
Procedimiento sugerido:
1. Abrir Wireshark y seleccionar la interfaz de red que se está utilizando.
2. Iniciar la captura.
3. Visitar http://neverssl.com y recargar la página.
4. Detener la captura.
5. Aplicar el filtro http para localizar paquetes HTTP, si la captura permite identificarlos.
6. Seleccionar una solicitud y revisar sus detalles.
En una solicitud HTTP sin cifrado, es posible que Wireshark muestre datos como el método, la ruta solicitada, el host y los encabezados. Si se selecciona Follow → TCP Stream en una conversación compatible, también puede ser posible leer el contenido HTTP transmitido.
Importante: esta sección debe completarse con los datos que efectivamente aparezcan en la captura. No se debe afirmar que se observaron paquetes, encabezados o contenido si no se verificaron.
4. Análisis de riesgos
4.1. ¿Qué protocolo utiliza el sitio?
La solicitud analizada utiliza HTTP. A diferencia de HTTPS, HTTP no incorpora cifrado TLS para proteger el contenido de la comunicación.
Por ese motivo, los datos de la solicitud HTTP pueden transmitirse en texto legible para alguien que consiga observar el tráfico. La disponibilidad de esa información depende de la solicitud y de los paquetes que se puedan capturar.
4.2. ¿Qué información puede observarse durante la solicitud?
Entre los elementos que pueden ser visibles en una solicitud HTTP se encuentran:
- URL o ruta solicitada: permite conocer qué recurso se intenta obtener.
- Host: identifica el nombre del servidor al que se dirige la solicitud.
- Método HTTP: por ejemplo, GET, que se utiliza habitualmente para solicitar un recurso.
- Headers: aportan información adicional sobre la solicitud.
- User-Agent: puede identificar el navegador y ciertos detalles del entorno del cliente, según el valor enviado.
Estos datos permiten analizar cómo se establece una comunicación web. En una conexión HTTP sin cifrado, un observador con acceso al tráfico puede llegar a leer la solicitud y la respuesta.
4.3. ¿Qué riesgos existen al navegar mediante HTTP desde una red Wi-Fi pública?
Una red Wi-Fi pública o no confiable puede permitir que otros participantes o un atacante con una posición adecuada en la red intenten observar el tráfico.
Cuando la comunicación utiliza HTTP sin cifrado, los principales riesgos son:
- Exposición de información: la URL, los encabezados y el contenido transmitido pueden quedar visibles.
- Intercepción: un tercero que consiga capturar el tráfico podría analizar la información intercambiada.
- Modificación de contenido: un atacante con capacidad para intervenir la comunicación podría alterar datos HTTP antes de que lleguen al destinatario.
- Pérdida de privacidad: la navegación puede revelar qué recursos se solicitan y otros metadatos de la comunicación.
El robo de credenciales es un riesgo posible si se transmiten por HTTP, pero no debe asumirse que ocurrió en esta práctica. El ejercicio utiliza un sitio de prueba y no requiere introducir contraseñas ni información personal.
4.4. ¿Cómo cambiaría el escenario utilizando una VPN?
Una VPN (Virtual Private Network o red privada virtual) establece un túnel cifrado entre el dispositivo y el servidor VPN.
Sus funciones principales son:
- Cifrado: protege el tráfico dentro del túnel para que otros participantes de la red local no puedan leerlo fácilmente.
- Túnel seguro: encapsula el tráfico del dispositivo y lo transporta de forma protegida hasta el servidor VPN.
- Protección del tráfico: dificulta que alguien que observa la red Wi-Fi pueda interpretar o modificar directamente los datos que circulan dentro del túnel.
- Privacidad: reduce la exposición del tráfico frente a otros participantes de la red local. Sin embargo, el proveedor de VPN puede observar determinados metadatos y la VPN no garantiza anonimato absoluto.
Limitación importante: una VPN no convierte HTTP en HTTPS. El tramo entre el servidor VPN y el sitio web puede seguir utilizando HTTP sin cifrado. Por lo tanto, el operador de la VPN o un atacante situado en ese tramo podría llegar a observar o modificar ese tráfico. Para proteger la comunicación con el sitio web, HTTPS sigue siendo fundamental.
5. Mis tres Reglas de Oro para navegar en redes Wi-Fi públicas
1. Utilizar una VPN confiable cuando corresponda. Ayuda a proteger el tráfico entre mi dispositivo y el servidor VPN, especialmente cuando utilizo una red pública que no controlo.
2. Evitar las conexiones automáticas a redes públicas. Desactivar la conexión automática y olvidar las redes que ya no utilizo reduce el riesgo de conectarme sin darme cuenta a una red no confiable.
3. Priorizar HTTPS y no ignorar las advertencias del navegador. HTTPS protege la comunicación entre el navegador y el sitio web mediante TLS. Si una página presenta errores de certificado o advertencias de seguridad, no debo ignorarlos ni introducir datos sensibles.
6. Conclusión
El análisis de NeverSSL permite estudiar las diferencias entre HTTP y HTTPS y comprender por qué una comunicación HTTP sin cifrado puede exponer información a quien consiga observar el tráfico.
Las herramientas de desarrollador permiten examinar los detalles de una solicitud web, mientras que Wireshark puede complementar el análisis mostrando los paquetes capturados y, cuando corresponde, el contenido HTTP legible.
Una VPN ofrece una capa adicional de protección en redes públicas al cifrar el tráfico entre el dispositivo y el servidor VPN, pero no reemplaza el cifrado HTTPS de extremo a extremo entre el navegador y el sitio web.
La combinación de HTTPS, hábitos de conexión seguros y una VPN confiable cuando sea necesaria ayuda a reducir los riesgos al utilizar redes Wi-Fi públicas.
