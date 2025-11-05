# Guía de Estudio: Proyecto "Control de Gastos Vue"

## 1. Estructura del Proyecto

```
admin-gastos/
│
├── index.html
├── package.json
├── vite.config.js
├── mejorasPropias.md
├── README.md
├── public/
├── src/
│   ├── App.vue
│   ├── main.js
│   ├── assets/
│   │   └── img/
│   ├── components/
│   │   ├── Alerta.vue
│   │   ├── ControlPresupuesto.vue
│   │   ├── Filtro.vue
│   │   ├── Modal.vue
│   │   └── Presupuesto.vue
│   └── helpers/
│       └── index.js
```

## 2. Arquitectura General

- **SPA (Single Page Application)** construida con Vue 3 y Vite.
- El núcleo de la aplicación es `App.vue`, que orquesta la lógica principal y el flujo de componentes.
- Los componentes están en `src/components/` y cada uno tiene una responsabilidad clara.
- Los helpers en `src/helpers/` contienen funciones reutilizables o utilidades.
- Los assets (imágenes, íconos) están en `src/assets/`.

## 3. App.vue: El Componente Raíz

- Importa y utiliza los componentes principales: `Presupuesto`, `ControlPresupuesto`, `Modal`.
- Define el estado global relevante usando `ref` y `reactive` de Vue:
  - `presupuesto`, `disponible`: controlan el presupuesto total y el disponible.
  - `modal`: controla la visibilidad y animación del modal para agregar gastos.
  - `gasto`: objeto reactivo para el formulario de nuevo gasto.
- Métodos principales:
  - `definirPresupuesto`: actualiza el presupuesto y el disponible.
  - `mostrarModal` y `ocultarModal`: controlan la apertura/cierre del modal con animación.
- Renderiza condicionalmente los componentes según el estado:
  - Si el presupuesto es 0, muestra el formulario para definirlo (`Presupuesto`).
  - Si ya hay presupuesto, muestra el control de presupuesto y el botón para agregar gastos.
  - El modal se muestra solo cuando se requiere agregar un gasto.

## 4. Componentes

### Presupuesto.vue
- Formulario para ingresar el presupuesto inicial.
- Usa un input numérico y valida que el valor sea mayor a 0.
- Emite el evento `definir-presupuesto` al componente padre (`App.vue`).
- Muestra alertas usando el componente `Alerta` si hay errores de validación.

### ControlPresupuesto.vue
- Muestra el presupuesto total y el disponible.
- Permite visualizar el estado financiero actual.

### Modal.vue
- Modal animado para agregar un nuevo gasto.
- Recibe props para el estado del modal y los campos del gasto.
- Usa `v-model` personalizado para enlazar los campos del formulario con el estado en `App.vue`.
- Emite eventos para actualizar los valores y cerrar el modal.

### Alerta.vue
- Componente simple para mostrar mensajes de error o información.
- Utiliza slots para mostrar contenido personalizado.

### Filtro.vue
- (No detallado en los fragmentos, pero típicamente se usa para filtrar gastos por categoría o fecha.)

## 5. Helpers

- El archivo `src/helpers/index.js` está pensado para contener funciones utilitarias, como formateo de fechas, validación, o cálculos auxiliares.
- Permite separar la lógica reutilizable del código de los componentes.

## 6. Lógica y Flujo de Datos

- El flujo principal inicia en `App.vue`, donde se define el presupuesto.
- Una vez definido, se habilita la funcionalidad para agregar gastos.
- El modal para agregar gastos utiliza `v-model` personalizado para enlazar los campos del formulario con el estado reactivo del gasto.
- Los eventos personalizados (`emit`) permiten la comunicación entre componentes hijo y padre.
- La validación y el manejo de errores se realiza en los componentes correspondientes, mostrando alertas cuando es necesario.

## 7. Buenas Prácticas y Modularidad

- Cada componente tiene una única responsabilidad.
- Se utiliza el sistema de slots y props de Vue para máxima flexibilidad y reutilización.
- La lógica de estado global se mantiene en el componente raíz, mientras que los componentes hijos son lo más "puros" posible.
- Los helpers permiten mantener el código limpio y DRY (Don't Repeat Yourself).

## 8. Recomendaciones para el Estudio

- Analiza cómo se comunican los componentes mediante props y eventos.
- Observa el uso de `ref` y `reactive` para el manejo de estado.
- Revisa cómo se implementan las validaciones y el manejo de errores.
- Estudia la estructura de carpetas y cómo se importan los módulos.
- Experimenta agregando nuevos helpers o componentes para extender la funcionalidad.

---

Este documento te servirá como referencia para entender la arquitectura, los módulos y la lógica de este proyecto Vue. Profundiza en cada archivo para ver ejemplos concretos de las prácticas aquí descritas.