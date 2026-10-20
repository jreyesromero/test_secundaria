# test_secundaria — Study Quizzes

Pequeña web de **tests de estudio** para repasar asignaturas de secundaria. Es una
página estática y, sobre todo, **basada en datos**: el contenido (asignaturas,
temas y preguntas) vive en archivos JSON dentro de `data/`, así que se pueden
añadir temas nuevos **sin tocar el código**.

## 🎮 Cómo funciona

- La página de inicio muestra las **asignaturas** y sus **temas**.
- Al elegir un tema, se juega su **test**: preguntas una a una, corrección al
  momento, barra de progreso, puntuación y mejor resultado guardado.
- Si el tema tiene ejercicio de **relacionar** (por ejemplo, señales de
  seguridad), aparece al final.

## 🧩 Estructura

```
/
├── index.html              # El motor (inicio + test). No se edita para añadir contenido.
├── images/                 # Imágenes opcionales usadas por algunas preguntas
├── data/
│   ├── subjects.json       # Índice de asignaturas y temas
│   └── tecnologia/
│       └── unit-01.json    # Un archivo por tema
├── README.md
├── LICENSE
├── .gitignore
└── CLAUDE.md               # Reglas del proyecto para Claude Code
```

## ➕ Añadir un tema nuevo

1. Crea `data/<asignatura>/<tema>.json` siguiendo el esquema de `CLAUDE.md`.
2. Añade una entrada en `data/subjects.json`.
3. No hace falta tocar `index.html`.

Lo normal es pedírselo a **Claude Code**: *"añade este tema"* + el JSON. Las reglas
están en `CLAUDE.md`.

## 🚀 Publicar en GitHub Pages

En **Settings → Pages → Source: Deploy from a branch → `main` / `(root)`**.
En uno o dos minutos tendrás la URL pública.

> ⚠️ Importante: la web carga los datos con `fetch()`, así que **debe abrirse por
> HTTP** (GitHub Pages o un servidor local). Si abres `index.html` haciendo doble
> clic, el navegador bloquea la carga de los datos. Para probar en local:
> `python3 -m http.server` dentro de la carpeta y abre `http://localhost:8000`.

## 📄 Licencia

MIT — consulta `LICENSE`.
