# Bienvenido al equipo!

Bienvenido al equipo de Votacion Electrónica de Mejor Mascota! El objetivo de este proyecto es proveer un sistema donde nuestros clientes puedan elegir cuál animal brinda más cariño y mejor compañía.

La aplicacion esta corriendo actualmente en produccion y se puede acceder a ver los resultados en http://result.bitlogic.party/ y votar en http://vote.bitlogic.party/.

Como es nuestra tradición, creemos que la mejor manera de sumarte al equipo es que resuelvas un defecto y hagas tu primer despliegue a producción antes de terminar el dia. Pronto te llegará una notificación a tu correo con los detalles de tu asignación.

A continuación, encontrarás el proceso de desarrollo para que te vayas familiarizando:


## Setup de Entorno de desarrollo

1. Pre-requisitos
* Docker 
* GIT
* Tu editor de codigo favorito


1. El sistema usa nginx para rutear los _requests_ al servicio que corresponda según el nombre de _host_. Configura los siguientes equipos en tu máquina:
   ```bash
   $ echo "127.0.0.1 vote.dev result.dev" >> /etc/hosts
   ```

1. Levanta el sistema localmente.
   ```bash
    $ docker run -v /var/run/docker.sock:/var/run/docker.sock bitlogicos/demo
   ```
   Ahora puedes ver la aplicación corriendo en tu máquina entrando a http://vote.dev y http://result.dev.

1. Baja el código de la aplicación.
   ```bash
   $ git clone git@github.com:bitlogic/demo-vote.git
   ```
   
## Primer Fix y Despliegue a Produccion

1. Completa tu asignación.
   ```bash
   $ vim <archivo>
   ```

1. Haz un build local y actualiza el sistema que corre localmente.
   ```bash
   $ drone exec
   $ docker build -t bitlogicos/demo-vote:latest .
   $ docker run -v /var/run/docker.sock:/var/run/docker.sock bitlogicos/demo
   ```
1. Verifica que la implementación funciona correctamente entrando a http://vote.dev y http://result.dev

1. Sube tus cambios al repositorio.
   ```bash
   $ git add -u
   $ git commit -m 'This fixes #<issue>'
   $ git push
   ```

1. Verifica el estado del build en el servidor de  http://drone.bitlogic.party/bitlogic/demo-vote.

1. Si tu cambio fue exitoso, al finalizar el build, podrás verlo funcionando en producción. En caso de fallo, deberás volver al paso 3.
