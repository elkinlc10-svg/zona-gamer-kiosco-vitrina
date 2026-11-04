# 🎮 Zona Gamer — kiosco de alquiler de juegos

Aplicación de escritorio que maneja un **local real de alquiler de PC por tiempo**. Los clientes eligen el juego
en un menú tipo consola, el encargado cobra y **solo los controles que pagaron funcionan**.

> 🔒 **El código de este proyecto es privado** porque se usa en un negocio real. Este repositorio es una vitrina:
> explica qué hace y cómo está construido. Con gusto muestro el código en una entrevista.

## ✨ Qué hace
- **Menú en modo kiosco** que se maneja con el control y no deja salir a Windows.
- **Cobro por jugador:** el niño presiona START, el encargado agrega 30 min o 1 hora y confirma. Cada jugador tiene
  su propio tiempo: uno puede unirse a mitad de partida y, cuando a uno se le acaba, solo se apaga su control.
- **Tiempo encima del juego:** una capa semitransparente muestra el tiempo de cada jugador mientras juegan.
- **Panel del encargado protegido con PIN cifrado**, con bloqueo tras 3 intentos fallidos y cierre automático por inactividad.
- **Caja:** registro de ventas, cierre de caja por turno, consulta por día y exportación a CSV para Excel.
- **Perfiles, ranking y minijuegos propios:** culebrita, pájaro, come-come y un kart en 3D hecho con Three.js.
- **A prueba de fallas:** se vuelve a abrir solo si se cae, respaldo diario de los datos (14 días) y guardado seguro
  de perfiles para que un corte de luz no los borre.

## 🧱 Cómo está construido
```
Electron (menú, panel, capa encima del juego)
        │  JSON por stdin/stdout
        ▼
Puente en Python ──► lee los controles físicos (ocultos a los juegos con HidHide)
                 └─► los copia a controles virtuales de Xbox 360 (ViGEm) SOLO para los jugadores activos
```
Así cualquier juego ve un control de Xbox normal, y **un control sin pagar simplemente no existe** para el juego.

## 🛠️ Tecnologías
`Electron` `Node.js` `JavaScript` `Three.js` `Python` `ViGEm` `HidHide` `Windows`

---
© Elkin Luna. Todos los derechos reservados.
