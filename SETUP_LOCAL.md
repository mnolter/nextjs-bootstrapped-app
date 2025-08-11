# Dashboard Project - Configuración Local

Este es un dashboard moderno de seguros construido con Next.js 15, TypeScript, Tailwind CSS y shadcn/ui.

## 🚀 Características Implementadas

- ✅ **UI Embellecida**: Diseño moderno con gradientes, sombras y efectos hover
- ✅ **Dark/Light Mode**: Switch para cambiar entre modo claro y oscuro
- ✅ **Componentes Modernos**: Tarjetas con efectos visuales mejorados
- ✅ **Mapa Interactivo**: Mapa de US con datos de políticas por estado
- ✅ **Gráficos**: Charts con Recharts para visualización de datos
- ✅ **Responsive**: Diseño adaptable a diferentes tamaños de pantalla

## 📋 Requisitos Previos

- Node.js 18+ 
- npm, yarn, pnpm o bun

## 🛠️ Instalación

1. **Extraer el proyecto**:
   ```bash
   tar -xzf dashboard-project.tar.gz
   cd dashboard-project
   ```

2. **Instalar dependencias**:
   ```bash
   npm install
   # o
   yarn install
   # o
   pnpm install
   ```

3. **Ejecutar en modo desarrollo**:
   ```bash
   npm run dev
   # o
   yarn dev
   # o
   pnpm dev
   ```

4. **Abrir en el navegador**:
   ```
   http://localhost:3000
   ```

## 🏗️ Build para Producción

```bash
npm run build
npm start
```

## 📁 Estructura del Proyecto

```
├── src/
│   ├── app/
│   │   ├── globals.css          # Estilos globales
│   │   ├── layout.tsx           # Layout principal con ThemeProvider
│   │   └── page.tsx             # Dashboard principal
│   ├── components/
│   │   ├── ui/                  # Componentes shadcn/ui
│   │   ├── theme-provider.tsx   # Provider para dark/light mode
│   │   ├── theme-toggle.tsx     # Switch de tema
│   │   └── USMap.tsx           # Componente del mapa de US
│   ├── hooks/
│   │   └── use-mobile.ts       # Hook para detección móvil
│   └── lib/
│       └── utils.ts            # Utilidades (cn function)
├── public/                     # Archivos estáticos
├── components.json             # Configuración shadcn/ui
├── tailwind.config.ts          # Configuración Tailwind
├── tsconfig.json              # Configuración TypeScript
└── package.json               # Dependencias y scripts
```

## 🎨 Características de UI

### Modo Claro/Oscuro
- Switch en la esquina superior derecha
- Transiciones suaves entre temas
- Colores optimizados para ambos modos

### Tarjetas Mejoradas
- Sombras pronunciadas
- Efectos hover con elevación
- Gradientes en headers
- Bordes redondeados

### Botones Modernos
- Gradientes de colores
- Efectos de escala al hover
- Transiciones suaves

## 🔧 Tecnologías Utilizadas

- **Next.js 15**: Framework React con Turbopack
- **TypeScript**: Tipado estático
- **Tailwind CSS**: Estilos utilitarios
- **shadcn/ui**: Componentes accesibles
- **Recharts**: Gráficos y visualizaciones
- **next-themes**: Manejo de temas
- **react-simple-maps**: Mapas interactivos

## 📊 Datos del Dashboard

El dashboard incluye:
- Estadísticas rápidas (recordatorios, cumpleaños, logins fallidos, leads)
- Políticas por compañía de seguros
- Aplicantes por compañía
- Mapa de US con políticas por estado
- Estados de políticas (gráfico de pie)
- Leaderboard de agentes
- Gráfico de políticas mensuales
- Filtros y controles

## 🎯 Próximos Pasos

Para continuar el desarrollo:

1. **Conectar con API real**: Reemplazar datos mock con endpoints reales
2. **Agregar autenticación**: Implementar login/logout
3. **Más gráficos**: Expandir visualizaciones de datos
4. **Filtros avanzados**: Mejorar sistema de filtrado
5. **Exportación**: Implementar exportación a PDF/Excel

## 🐛 Solución de Problemas

### Error de dependencias
Si encuentras errores de peer dependencies:
```bash
npm install --legacy-peer-deps
```

### Puerto ocupado
Si el puerto 3000 está ocupado:
```bash
PORT=3001 npm run dev
```

### Problemas de TypeScript
Reinicia el servidor TypeScript en tu editor o ejecuta:
```bash
npx tsc --noEmit
```

## 📝 Notas

- El proyecto usa Turbopack para builds más rápidos en desarrollo
- Los iconos fueron reemplazados por símbolos Unicode para evitar dependencias externas
- El mapa usa datos mock que pueden ser reemplazados con datos reales
- Todos los componentes son responsive y accesibles

¡Disfruta trabajando con el dashboard! 🚀
