# Congreso WEB

## Necesidades

- Sistema interno de reuniones.

- Sistema de usuarios interno.

- Reunion de 300 personas.

- Moderador de la reunion.

- Sistema de seguridad via SMS.

- Sistema de votación.

  
  

## Tecnologias que vamos a utilizar para cada necesidad

  

- ## Sistema de usuarios
1) **Laravel AUTH**. (Lo elegimos por todas las funcionalidades OUT-THE-BOX) que trae
integradas.

- ## Reunion de 300 personas

1) Vamos a utilizar **ZOOM** haciendo uso principalmente de la SDK gratuita que ofrece para integrar una sala dentro del sitio.
2) Todos los usuarios que vayan a ingresar exceptuando al HOST van a ingresar como INVITADOS ( referencia a invitado de zoom ).

- ## Moderador de la reunion

1) Mediante el SCHEDULE de ZOOM podemos definir un moderador / co-host(s) de la reunion.

2) Todos los usuarios HOST deben estar logeados con cuentas de ZOOM.

- ## Sistemas de seguridad.

1) Para agregar una capa de seguridad, las contraseñas generadas para los participantes de la reunion se van a generar 2 horas antes de la hora programada de comienzo de la reunion. ( Revisar )

2) **SMS** En una primera instancia vamos a utilizar <a  target='_blank'  href='https://developer.nexmo.com/'>**NEXMO**</a>, una moderna API que se lleva muy bien con Laravel y nos permite generar una capaz de seguridad extra ( via PIN ).

	>**SOBRE NEXMO**
	>- Cada mesanje tiene un precio de 0.03€($2,87) ( No testeado )
	>
	>- Provee de ANALITYCS.
	>
	>- Provee de sistema de PIN de 4 o 6 digitos.
	>
	>-  <a  target='_blank'  href='https://help.nexmo.com/hc/en-us/articles/204018063-Argentina-SMS-> Features-and-Restrictions'> Restricciones para enviar SMS en Argentina .</a>

  
  
  

- ## Sistema de votacion

1) Para el sistema de votacion es **OBLIGATORIO** que el usuario verifique su identidad via SMS

2) El sistema de votacion lo vamos a hacer a modo de APIRest. Para no tener que cerrar la reunion a la hora de votar y poder fetchear los resultados en vivo.

**Sobre el proceso de votacion**

- La reunion va a contar con un boton de "Votar" al darle click va a ser una REQUEST para chequear que este habilitado.

- El host / admin debe habilitar la encuesta para todos los usuarios.

- Cuando esa encuesta se dispare se enviara el mail con el PIN ( este paso revisar si es conveniente hacerlo previamente a la reunion o la hora de votar)

- Una vez NEXMO notifique que el SMS fue enviado a todos los participantes vamos a habilitar la votación.

- El boton de Votar ahora una vez clickeado va a abrir un modal para votar.

- Los usuarios cargan el voto.

- El host va a poder ver los resultados on-demand.
