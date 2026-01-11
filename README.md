# AnimeScraping WebApp

Aplicación web para webOS TV que se conecta al backend de AnimeScraping.

## Características

- Visualización de animes en grid responsive
- Navegación por teclado optimizada para TV
- Detalles de anime con lista de episodios
- Sistema de favoritos (almacenamiento por sesión)
- Categorías: Inicio, Populares, Nuevos, Favoritos
- Integración completa con backend API

## Configuración

### 1. Configurar la IP del backend

Edita `config.js` y cambia la IP a la de tu computadora:
```javascript
const CONFIG = {
  BACKEND_HOST: '192.168.1.147',  // ← Cambia esta IP
  BACKEND_PORT: 3000,
};
```

### 2. Iniciar el backend

```bash
cd ../backend
npm run dev
```

El backend debe estar corriendo en `http://0.0.0.0:3000`

### 3. CORS configurado

El backend ya está configurado para aceptar peticiones desde webOS TV (sin origin)

## Endpoints utilizados

- `GET /api/anime` - Lista de animes
- `GET /api/anime/:id` - Detalles de un anime
- `POST /api/anime/favorite/add` - Agregar favorito
- `POST /api/anime/favorite/remove` - Eliminar favorito
- `GET /api/anime/favorite/list/:sessionId` - Lista de favoritos
- `GET /api/anime/favorite/check/:sessionId/:animeId` - Verificar favorito

## Controles de navegación

### Vista principal (Grid de animes)
- **Flechas ← →**: Navegar entre animes horizontalmente
- **Flechas ↑ ↓**: Navegar entre animes verticalmente
- **Flecha ↓** (en última fila): Ir al menú inferior
- **Enter**: Ver detalles del anime

### Vista de detalles
- **Flechas ↑ ↓**: Navegar entre episodios
- **Enter**: Seleccionar episodio
- **Escape/Backspace**: Volver a la lista principal

### Menú inferior
- **Flechas ← →**: Navegar entre opciones del menú
- **Flecha ↑**: Volver al grid de animes
- **Enter**: Activar opción del menú

## Estructura de archivos

```
WebApp/
├── appinfo.json      # Configuración de la app webOS
├── index.html        # App principal (HTML + CSS + JS)
├── icon.png          # Icono pequeño
├── largeIcon.png     # Icono grande
└── README.md         # Este archivo
```

## Despliegue en webOS TV

1. Empaqueta la aplicación usando CLI de webOS
2. Instala en el TV usando `ares-install`
3. Ejecuta la app desde el launcher del TV

Para más información sobre desarrollo en webOS TV: https://webostv.developer.lge.com/
