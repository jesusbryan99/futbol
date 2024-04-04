# Creacion de requerimentos para bases de datos sql

## Entidades

### jugadores

- id_jugador **(PK)**
- nombre
- apellido_paterno
- apellido_materno
- edad
- fecha_nacimiento
- genero
- estatura
- foto
- curp
- posicion
- dorsal
- pierna_dominante
- id_contacto **(FK)**
- id_equipo **(FK)**

### contacto

- id_contacto **(PK)**
- numero
- numero_secundario
- redsocial
- correo

### equipos

- id_equipo **(PK)**
- nombre
- id_usuario
- foto
- posicion_tabla
- id_contacto **(FK)**
- id_liga **(FK)**

### ligas

- id_liga **(PK)**
- nombre
- descripcion
- numero_equipos

### juegos

- id_juego
- local (id_equipo)
- visitante (id_equipo)
- fecha
- hora_encuentro
- nombre_campo_juego
- estatus
- id_estadistica_juego **(FK)**
- id_liga **(FK)**

### estadisticas_juego

- id_estadistica_juego **(Pk)**
- disparos_ap (tiros a puerta)
- disparos_f (tiros fuera)
- gol_local
- gol_visita
- faltas_local
- faltas_visita
- cambios_local
- cambios_visita

### faltasXjugador

- id_faltaxjugador **(PK)**
- amonestacion
- expulsion
- descripcion
- id_jugador **(FK)**
- id_estadistica_juego **(FK)**

### estadisticas_jugadores

- id_e_jugador **(PK)**
- mano_a_mano_ganado
- mano_a_mano_perdido
- intercepcion
- id_jugador **(FK)**
- id_pases **(FK)**
- id_tiro **(FK)**
- id_juego **(FK)**

### pases

- id_pase **(PK)**
- acertado **(boolean)**
- asistencia **(boolean)**
- balon_parado **(boolean)**
- golpeo (lugar con el que se golpea el balon)
- id_jugador **(FK)**

### tiros

- id_tiro **(PK)**
- gol **(boolean)**
- acertado **(boolean)**
- balon_parado **(boolean)**
- golpeo (lugar con el que se golpea el balon)
- id_jugador **(FK)**

### usuarios

- id_usuario
- nombre
- apellido_paterno
- apellido_materno
- correo
- password
- telefono
- fecha_nacimiento
- edad
- genero
- curp
- rol

## Relaciones

- Un jugador tiene contactos _1 a M_
- Un jugador tiene un equipo _M a 1_
- Un equipo tiene contactos _1 a M_
- Una liga tiene varios equipos _1 a M_;

  (En ligas amateur varios equipos pueden estar en varias ligas, pero no son los mismos jugadores, cada liga se cuenta por separado ya que no se concidera oficial, ni restringido que un jugador que juega en una liga en "x" equipo no pueda jugar en "y" equipo de esta misma liga).

- Varios juegos tienen varias estadisticas _M a M_
- Las ligas tienes varios juegos _M a M_
- Un juego tiene varias faltas _1 a M_
- Un jugador puede hacer varias faltas _1 a M_
- Un jugador tiene estadisticas _1 a M_
- un jugador hace pases _1 a M_
- un jugador hace tiros _1 a M_
- un juego tiene varias estadisticas
- un delegado tiene un equipo
