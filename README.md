# Corrector IA — Corrige tu ortografía con IA en cualquier app de Windows

Una pequeña aplicación que corre en segundo plano y, **mientras escribes en cualquier programa de Windows** (WhatsApp, Word, navegador, Telegram, Discord, correo…), **corrige automáticamente** lo que tecleas usando inteligencia artificial.

A diferencia de los autocorrectores tradicionales, **entiende el contexto**:
- Distingue `tu casa` de `tú vienes` y pone (o no) la tilde según corresponda.
- Añade los signos `¿` y `¡` al inicio de preguntas y exclamaciones.
- Aplica las normas ortográficas del español (tildes, mayúsculas, b/v, h, g/j…).

## Demostración

```
Lo que escribes:                      Lo que aparece:
  matematicas[espacio]            →     matemáticas[espacio]
  como estas?                     →     ¿Cómo estás?
  que sorpresa!                   →     ¡Qué sorpresa!
  hoy es martes.                  →     Hoy es martes.
  tu opinion es para mi.          →     Tu opinión es para mí.
  solo tu lo sabes.               →     Solo tú lo sabes.
```

---

## Instalación rápida (3 pasos)

### 1. Descarga el programa

Descárgate los archivos de este repositorio (botón verde **`Code` → `Download ZIP`**) y descomprímelos donde quieras.

### 2. Configura tu API key

El programa usa **Groq** (gratis) o **OpenAI** para corregir el texto con IA. Necesitas tu propia API key.

**Opción A — Groq (gratis, recomendado):**

1. Entra en [console.groq.com](https://console.groq.com/) y crea una cuenta gratis.
2. Ve a **API Keys** → **Create API Key** → copia la clave (empieza por `gsk_`).
3. En la carpeta del programa, **renombra** `config.ejemplo.json` a `config.json`.
4. Abre `config.json` con el Bloc de notas y pega tu clave en el campo `api_key` de la sección `groq`.

```json
"groq": {
    "api_key": "gsk_TU_CLAVE_AQUI",
    ...
}
```

**Opción B — OpenAI (de pago):**
Igual pero pega la clave de OpenAI en su sección y cambia `"motor": "groq"` por `"motor": "openai"`.

### 3. Ejecuta

Doble clic en **`CorrectorIA.exe`**.

Aparecerá un icono **"AI"** azul en la bandeja del sistema (junto al reloj). A partir de ese momento, **escribe normalmente en cualquier aplicación**: las correcciones llegan solas.

---

## Atajos

| Atajo            | Acción                |
| ---------------- | --------------------- |
| `Ctrl + Alt + P` | Pausar / reanudar     |
| `Ctrl + Alt + Q` | Cerrar el programa    |

También tienes menú con **clic derecho en el icono** de la bandeja.

---

## Ajustes finos (`config.json`)

```json
"comportamiento": {
  "modo_trigger": "palabra",       // "palabra" / "frase" / "ambos"
  "longitud_palabra_minima": 3,
  "longitud_minima": 8,
  "longitud_maxima": 500,
  "pausa_tras_correccion_ms": 120
},
"reemplazo": {
  "pausa_despues_borrar_ms": 45,
  "pausa_despues_copiar_ms": 130,
  "pausa_despues_pegar_ms": null
}
```

- **`modo_trigger`**: cuándo se dispara la corrección.
  - `"palabra"`: cada vez que pulsas espacio (rápido, palabra por palabra).
  - `"frase"`: solo al cerrar la frase con `. `, `? `, `! ` o Enter.
  - `"ambos"`: las dos cosas.
- Si en alguna app el texto **se desplaza o salta** al corregir, sube los valores de la sección `reemplazo` (por ejemplo `pausa_despues_borrar_ms: 70`).

---

## Privacidad

- Solo el texto inmediato (la última frase o palabra) se envía al servicio de IA configurado (Groq u OpenAI), bajo **tu propia cuenta**.
- Tu API key se guarda únicamente en tu PC, en el archivo `config.json`.
- El programa no envía estadísticas, telemetría ni nada al autor.
- Las contraseñas y campos protegidos de Windows quedan fuera del corrector.

---

## Aviso de Windows SmartScreen

La primera vez que ejecutes `CorrectorIA.exe`, Windows puede mostrar el aviso "Windows protegió tu PC". Es porque el ejecutable no tiene firma digital comercial (los certificados son caros). El archivo es seguro: si quieres ejecutarlo, pulsa **Más información → Ejecutar de todas formas**.

---

## Licencia y propiedad intelectual

Este programa es **propiedad intelectual de Leticia Sepúlveda Mancilla**. Todos los derechos reservados.

✅ **Puedes:** descargar, instalar y usar el programa **gratuitamente para uso personal** en tu propio ordenador.

❌ **NO puedes:** redistribuir el ejecutable en otros sitios, modificar el programa, descompilarlo, hacer ingeniería inversa, ni utilizarlo con fines comerciales sin permiso por escrito de la autora.

Lee el archivo [`LICENSE`](LICENSE) para los términos completos.

---

## Sobre el proyecto

Aplicación personal desarrollada con asistencia de IA por **Leticia Sepúlveda Mancilla** © 2026.
