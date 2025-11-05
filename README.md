# SIMÓN DICE - PMDM 🦑🫧🪼

- **Antes de empezar a codificar el programa hemos realizado un diagrama de flujo y de estado para comprender de manera profunda la lógica...**

---

> **DIAGRAMA DE ESTADO 🎀**

```mermaid
---
config:
  theme: redux
  look: neo
---
stateDiagram-v2
  [*] --> Idle : Aplicación abierta / Pantalla de inicio
  Idle --> Jugando : Usuario pulsa START
  Jugando --> MostrandoSecuencia : Generar y añadir color a la secuencia
  MostrandoSecuencia --> EsperandoEntrada : Secuencia iluminada completamente
  EsperandoEntrada --> VerificandoEntrada : Usuario pulsa un botón
  VerificandoEntrada --> EsperandoEntrada : Pulsación correcta (secuencia NO completada)
  VerificandoEntrada --> RondaSuperada : Pulsación correcta (secuencia completada)
  VerificandoEntrada --> GameOver : Pulsación incorrecta
  RondaSuperada --> Jugando : Aumentar ronda y nueva secuencia
  GameOver --> Idle : Mostrar mensaje de pérdida y reiniciar a ronda inicial

```

---

> **DIAGRAMA DE FLUJO 🎳**

```mermaid
flowchart TD
  A["Inicio - Pantalla principal<br/>(Simon Dice)"] --> B["Botón START pulsado"]
  B --> C["Inicializar juego:<br/>ronda = 1, puntuación = 0, secuencia = []"]
  C --> D["Generar/añadir color aleatorio a la secuencia"]
  D --> E["Mostrar secuencia al usuario<br/>(iluminar botones secuencialmente)"]
  E --> F["Habilitar entrada del usuario"]
  F --> G["Usuario pulsa un botón"]
  G --> H{"¿Pulsa el botón<br/>correcto según secuencia?"}
  H -->|"Sí"| I["Avanzar índice de comprobación"]
  I --> J{"¿Ha completado<br/>el usuario la secuencia?"}
  J -->|"No"| F
  J -->|"Sí"| K["Aumentar puntuación<br/>mostrar 'Rondas' y 'Puntuación'"]
  K --> L["Incrementar ronda"]
  L --> D
  H -->|"No"| M["Game Over"]
  M --> N["Mostrar pantalla Final:<br/>'Fin de juego'<br/>Rondas completadas y puntuación"]
  N --> O["Opcional: botón REINICIAR -> volver a C"]

```

