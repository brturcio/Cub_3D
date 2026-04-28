# Cub_3D (cub3D) — Raycasting engine in C (MiniLibX)

[English](#english) | [Español](#español)

---

## English

### Overview
**Cub_3D** is a small 3D raycasting project written in **C**, inspired by early FPS engines (Wolfenstein-like).
It renders a pseudo-3D environment from a 2D map using **raycasting**, with textures and configurable floor/ceiling colors.

This project uses **MiniLibX (Linux)** and links against **X11**.

### Features
- Raycasting-based rendering
- Wall textures (North/South/West/East)
- Configurable floor and ceiling colors
- Map parsing from `.cub` files
- Player spawn direction (`N`, `S`, `E`, `W`)

**Bonus build (`cub3D_bonus`)** (based on headers and sources naming):
- Doors / interaction system
- Sprites + sprite animation handling
- Minimap rendering
- Mouse look / mouse movement support
- Timing / smoother movement utilities

### Requirements (Linux)
You will need:
- `cc` (clang or gcc)
- `make`
- X11 development libraries (commonly: `libx11-dev`, `libxext-dev`, `zlib1g-dev`, `libbsd-dev` depending on distro)

> The project includes `libraries/minilibx-linux` and links with `-lmlx -lXext -lX11 -lm -lz` (see `Makefile`).

### Build
Mandatory:
```bash
make
```

Bonus:
```bash
make bonus
```

Clean:
```bash
make clean
```

Full clean:
```bash
make fclean
```

Rebuild:
```bash
make re
```

### Run
Mandatory:
```bash
./cub3D maps/mandatory/valid_maps/01_basic_valid.cub
```

Bonus:
```bash
./cub3D_bonus maps/bonus/valid_maps/<some_map>.cub
```

### Map format (`.cub`)
A `.cub` file contains:
1) Texture paths:
- `NO <path>` north wall texture
- `SO <path>` south wall texture
- `WE <path>` west wall texture
- `EA <path>` east wall texture

2) Colors:
- `F R,G,B` floor color
- `C R,G,B` ceiling color

3) The map grid:
- `1` wall
- `0` empty space
- `N/S/E/W` player spawn and initial direction

Example (from `maps/mandatory/valid_maps/01_basic_valid.cub`):
```txt
NO ./textures/north.xpm
SO ./textures/south.xpm
WE ./textures/west.xpm
EA ./textures/east.xpm

F 138,46,0
C 0,0,50

111111
100001
10N001
100001
111111
```

### Controls
Typical cub3D controls are:
- `W/A/S/D` or arrow keys: move
- `Left/Right arrows`: rotate
- `ESC`: quit

> Controls can vary depending on your implementation. If you want, I can inspect `sources/*/input*.c` and document the exact keys.

### Project structure
- `sources/mandatory/` mandatory implementation
- `sources/bonus/` bonus implementation
- `includes/` headers (`cub3D.h`, `cub3D_bonus.h`)
- `maps/` sample maps (valid/invalid)
- `textures/` XPM textures
- `libraries/` third-party libraries (`libft`, `minilibx-linux`)

---

## Español

### Descripción
**Cub_3D** es un proyecto de raycasting en **C**, inspirado en los primeros motores FPS (estilo Wolfenstein).
Renderiza un entorno “pseudo-3D” a partir de un mapa 2D usando **raycasting**, con texturas y colores configurables para suelo/techo.

Este proyecto usa **MiniLibX (Linux)** y enlaza contra **X11**.

### Características
- Render con raycasting
- Texturas de paredes (Norte/Sur/Oeste/Este)
- Colores configurables para suelo y techo
- Parseo de mapas `.cub`
- Dirección inicial del jugador (`N`, `S`, `E`, `W`)

**Bonus (`cub3D_bonus`)** (por lo que se ve en headers/sources):
- Puertas / interacción
- Sprites + animación
- Minimap
- Control con ratón
- Utilidades de tiempo para movimiento más fluido

### Requisitos (Linux)
Necesitas:
- `cc` (clang o gcc)
- `make`
- Librerías de desarrollo de X11 (por ejemplo: `libx11-dev`, `libxext-dev`, `zlib1g-dev`, `libbsd-dev` según tu distro)

> El proyecto incluye `libraries/minilibx-linux` y enlaza con `-lmlx -lXext -lX11 -lm -lz` (ver `Makefile`).

### Compilar
Mandatory:
```bash
make
```

Bonus:
```bash
make bonus
```

Limpiar objetos:
```bash
make clean
```

Limpiar todo:
```bash
make fclean
```

Recompilar:
```bash
make re
```

### Ejecutar
Mandatory:
```bash
./cub3D maps/mandatory/valid_maps/01_basic_valid.cub
```

Bonus:
```bash
./cub3D_bonus maps/bonus/valid_maps/<un_mapa>.cub
```

### Formato del mapa (`.cub`)
Un archivo `.cub` incluye:
1) Rutas de texturas:
- `NO <ruta>` textura pared norte
- `SO <ruta>` textura pared sur
- `WE <ruta>` textura pared oeste
- `EA <ruta>` textura pared este

2) Colores:
- `F R,G,B` color del suelo
- `C R,G,B` color del techo

3) El mapa:
- `1` pared
- `0` espacio libre
- `N/S/E/W` posición inicial del jugador y su orientación

Ejemplo:
```txt
NO ./textures/north.xpm
SO ./textures/south.xpm
WE ./textures/west.xpm
EA ./textures/east.xpm

F 138,46,0
C 0,0,50

111111
100001
10N001
100001
111111
```

### Controles
Los controles típicos en cub3D suelen ser:
- `W/A/S/D` o flechas: mover
- `Flecha izquierda/derecha`: rotar
- `ESC`: salir

> Puede variar según tu implementación. Si quieres, reviso `sources/*/input*.c` y lo dejo exacto.

### Estructura del proyecto
- `sources/mandatory/` implementación mandatory
- `sources/bonus/` implementación bonus
- `includes/` headers (`cub3D.h`, `cub3D_bonus.h`)
- `maps/` mapas de ejemplo (válidos/inválidos)
- `textures/` texturas XPM
- `libraries/` librerías (`libft`, `minilibx-linux`)
