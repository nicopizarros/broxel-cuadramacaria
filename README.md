# Propuesta Broxel · Nicolás Pizarro

One-pager HTML para la propuesta de patrocinio como Global Equestrian Brand Ambassador.

## Estructura

```
broxel-proposal/
├── index.html                          ← archivo único editable
├── assets/
│   └── broxel-logo.svg                 ← logo oficial Broxel
└── images/
    ├── hero-01-action.jpg              ← saludo al público
    ├── hero-02-victory.jpg             ← vuelta de honor escarapela tricolor
    ├── hero-03.jpg                     ← galope GNP
    ├── hero-04.jpg                     ← tordo con listón
    ├── hero-05.jpg                     ← salto Santa Clara
    ├── hero-06.jpg                     ← reconocimiento pista
    └── hero-07.jpg                     ← celebración con casco en alto
```

## Paleta oficial Broxel

Extraída directamente del archivo SVG de marca:

- **Cyan primario:** `#00C1DE` (infinito y acentos)
- **Navy primario:** `#003A5D` (wordmark)

## Cómo editar

Todo el contenido vive en el objeto `proposalData` al inicio del bloque `<script>`. No tienes que tocar HTML ni CSS para cambiar texto, montos, tiers o pilares.

### Cambiar montos

```js
tiers: [
  {
    name: "Silver",
    price: "$250,000",        ← edita aquí
    priceUnit: "MXN · anual · + IVA",
    ...
  }
]
```

### Editar título del concurso

```js
concurso: {
  price: "$300,000",          ← cambia aquí
  priceUnit: "MXN · + IVA · por concurso",
  benefits: [ ... ]
}
```

### Carrusel: añadir o reordenar imágenes

1. Pon el archivo en `/images/`
2. Edita el array `slides`:

```js
slides: [
  { src: "images/hero-01-action.jpg", alt: "..." },
  { src: "images/nueva-foto.jpg",     alt: "..." }
]
```

Rota cada 5.5 segundos. Pausa con hover. Soporta swipe en mobile.

### Editar tiers de embajador

Cada tier acepta:

- `name`, `tagline`, `price`, `priceUnit`
- `featured: true` para destacar uno con badge "PAQUETE RECOMENDADO"
- `horsePackage.text`: el bloque resaltado en cyan que muestra cuántos caballos incluye
- `features`: lista de entregables con opción `strong: true` para resaltar

### Editar beneficios del Title Sponsor de Concurso

```js
concurso: {
  benefits: [
    {
      icon: "trophy",         // disponibles: trophy, medal, terrace
      title: "...",
      text: "..."
    }
  ]
}
```

## Exportar a PDF

`Cmd+P` → "Guardar como PDF". El CSS de impresión está optimizado para A4 horizontal.

## Deploy

### Vercel (recomendado)

```bash
cd broxel-proposal
vercel --prod
```

### Netlify drop

Arrastra la carpeta completa a https://app.netlify.com/drop

## Notas de diseño

- Logo oficial SVG embebido inline (escalable, nítido a cualquier resolución)
- Paleta extraída directamente del archivo de marca Broxel
- Tipografía: Cormorant Garamond (display) + Inter Tight (body)
- Responsive completo: 2 columnas en desktop, stack en mobile
- Carrusel con autoplay, controles, dots, swipe en mobile, pausa en hover
- Sin em dashes en todo el texto
- Imágenes optimizadas a 1920px, JPEG progresivo q82 (~3 MB total vs 92 MB originales)

## Próximas iteraciones

- Sección de calendario de concursos (fechas y sedes confirmadas)
- Métricas de audiencia y alcance en redes
- Versión en inglés con toggle de idioma
- Tiers escalables del Title Sponsor de Concurso (más allá del title único)
