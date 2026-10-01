Introduccion: En este trabajo practico voy a ahondar más en la diferencia entre el protocolo HTTP y el HTTPS, voy a identificar distintos protocolos visibles dentro de un dominio HTTP, también voy a explicar en que beneficia el uso de una VPN en la seguridad de un usuario
Por ultimo voy a establecer tres reglas de oro para navegar en una red Wi-Fi publica.

Sitio analizado: El sitio que analicé en este trabajo es: neverssl.com y lo analicé ya que es un sitio con protocolo HTTP y permitía un desglose amplio de todos los paquetes que se enviaban y recibían desde ese servidor.

Evidencia observada: Adjunto imagen de las herramientas del desarrollador del navegador utilizadas dentro de neverssl.com
<img width="580" height="715" alt="image" src="https://github.com/user-attachments/assets/6356c2eb-f826-48f1-b034-42caf0ef08f7" />



Parte 2 análisis
1.	Que protocolo utiliza el sitio?
El protocolo que utiliza el sitio es el HTTP, nos damos cuenta porque apretando el F12 nos da toda la información sin cifrar, si el protocolo fuera HTTPS, estaría toda esa información cifrada.

2.	¿Que información puede observarse durante la solicitud?
Encontré la URL: 
http://freshgoodyoungtreasure.neverssl.com/online/
También el status code: 200 OK
El host: freshgoodyoungtreasure.neverssl.com

3.	¿Que riesgos existen al navegar mediante HTTP desde una red Wi-Fi publica?
Los riegos son muchos, ya que en una red publica cualquier usuario que esté dentro puede tener acceso a todos los paquetes que envias y recibis, si navegas mediante HTTP que carece de una capa de seguridad, los riesgos son mucho mayores ya que se filtraría la información en crudo, sin ningún tipo de cifrado o protección, podrían leerla o hasta modificarla sin que el usuario se entere, podría por ejemplo robarte las credenciales de acceso a ese sitio web.
4.	Como cambiaria este escenario utilizando una VPN?
Este escenario cambiaria rotundamente para bien utilizando una VPN, ya que la VPN te protegería de diversas formas, la principal es que abriría un túnel privado y cifrado entre el usuario y la propia VPN, logrando asi que todos los paquetes que salgan del usuario terminen cifrados y totalmente protegidos por mas que sea navegando en HTTP, eso significa que si algún atacante que este merodeando en la red Wi-fi publica, puede robarte los paquetes pero estos paquetes estarían totalmente cifrados por la VPN.
Descripciones.
Cifrado: Transforma la información que es legible en información que no puede ser entendida sin tener una llave de acceso.
Túnel seguro: Es una conexión entre dos puntos (en este caso entre el dispositivo y la VPN), que está protegida y por la cual circula la información.
Protección del trafico: Trata de una disciplina que consta en evitar que los datos que viajan en una red puedan ser modificados, interceptados u observado sin consentimiento del usuario.
Privacidad: Es la capacidad de mantener protegida la información tuya y de las actividades que haces.


5.	Escribe tus tres reglas de oro para navegar en redes de Wi-Fi publica.
Mi primer regla de oro es utilizar una VPN, ya que cifra todos los paquetes que salen de tu dispositivo, es la mayor medida de protección que podes tener en una red publica.
Mi segunda regla de oro es olvidar la red cuando ya no la utilizas, para que no se te conecte automáticamente sin tu permiso, porque a veces suele pasar y terminas entrando a una red publica sin ninguna capa de protección previamente preparada.
Mi tercera regla de oro es no frecuentar sitios HTTP, considero que es atravesar un riesgo innecesario dentro de una red Wi-Fi publica, frecuentar sitios HTTPS es una medida de seguridad muy importante y mas en una red publica. 
