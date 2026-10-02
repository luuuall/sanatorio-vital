# Sanatorio Papa Francisco

Landing page del Sanatorio Papa Francisco, un sanatorio médico. Construida con **Astro**.

## Comandos

| Comando                 | Acción                                        |
| :---------------------- | :-------------------------------------------- |
| `npm install`           | Instala las dependencias                      |
| `npm run dev`           | Inicia el servidor de desarrollo en `localhost:4321` |
| `npm run build`         | Genera el sitio estático en `dist/`           |
| `npm run preview`       | Previsualiza el build localmente              |

## Estructura

```
src/
├── data/site.ts          # Contenido central (servicios, especialidades, testimonios, etc.)
├── layouts/Layout.astro  # Layout base con estilos globales y tema
├── components/           # Header, Footer, Hero, ServiceCard, Icon
└── pages/
    ├── index.astro       # Home: hero, stats, servicios, por qué elegirnos, especialidades, testimonios, CTA
    ├── servicios.astro   # Servicios y especialidades
    ├── contacto.astro    # Contacto y formulario de turnos
    └── gracias.astro     # Confirmación de formulario
```

## Contenido

Todo el contenido editable (servicios, especialidades, testimonios, datos de contacto)
está centralizado en `src/data/site.ts`.
