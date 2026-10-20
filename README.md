# Technology Quiz — Unit 1 (2º ESO)

Juego-test interactivo para repasar la Unidad 1 de **Tecnología** de 2º de ESO
(asignatura en inglés): el taller, el impacto ambiental, el método de proyecto y
la seguridad. Es una página web de un solo archivo, sin dependencias ni
instalación: funciona abriendo `index.html` en cualquier navegador.

## 🎮 Cómo se juega

- **19 preguntas tipo test**, una a una, con opciones como botones.
- **Corrección al momento**: verde si aciertas, rojo si fallas, con una breve
  explicación de cada respuesta.
- **Ejercicio de relacionar** las señales de seguridad al final.
- Puntuación final **sobre 24** (19 del test + 5 de señales), con mensaje según
  la nota y **mejor resultado** guardado en el navegador.
- Se maneja con ratón, pantalla táctil o **teclado** (teclas `1`–`4` para elegir
  y `Enter` para avanzar).
- Las preguntas y las opciones salen en **orden aleatorio**, así se puede repetir
  sin memorizar posiciones.

## 🚀 Publicarlo en GitHub Pages

1. Sube este repositorio a GitHub (con `index.html` en la raíz).
2. En el repositorio, ve a **Settings → Pages**.
3. En **Source**, elige **Deploy from a branch**.
4. Selecciona la rama `main` y la carpeta `/ (root)`, y guarda.
5. En uno o dos minutos tendrás una URL pública tipo:
   `https://TU-USUARIO.github.io/NOMBRE-DEL-REPO/`

> Nota: el repositorio debe ser **público** para usar GitHub Pages gratis, así que
> el código del juego será visible. Para un juego de práctica no supone ningún
> problema.

## ✏️ Personalizar el test

Todo el contenido está dentro de `index.html`, en el bloque `<script>`:

- Para **añadir, quitar o editar preguntas**, modifica la lista `QUESTIONS`.
  Cada pregunta tiene: `t` (tema), `q` (enunciado), `o` (opciones), `a` (índice
  de la respuesta correcta, empezando en 0) y `e` (explicación).
- Para cambiar el **ejercicio de señales**, edita `TYPES` y `DESCS`.

El marcador, la nota y los totales se **recalculan automáticamente**, así que no
hay que tocar nada más al cambiar el número de preguntas.

## 📁 Estructura

```
.
├── index.html     # El juego completo (HTML + CSS + JS)
├── README.md      # Este archivo
├── LICENSE        # Licencia MIT
└── .gitignore
```

## 📄 Licencia

Publicado bajo licencia **MIT**. Consulta el archivo `LICENSE`.

Material de estudio basado en el temario de Tecnología de 2º de ESO.
