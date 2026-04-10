# 🕵️‍♂️ WhatsApp Tracking Tool (OSINT)

Herramienta basada en Python y Selenium para automatizar el seguimiento de contactos en WhatsApp Web. Permite registrar las sesiones exactas de conectividad ("en línea") de un contacto, almacenando todo de manera silenciosa en una base de datos local SQLite y exportando reportes.

---

## ✨ Características Principales (Actualizadas)

- **Soporte Multi-Navegador:** Utiliza tanto **Google Chrome** (`--browser chrome`) como **Mozilla Firefox** (`--browser firefox`).
- **Seguimiento Headless:** Ejecuta el rastreador de forma 100% invisible en el fondo.
- **Mecanismo Anti-Idle (Keep-Alive):** Inyección periódica invisible de Javascript (`mousemove`) para mantener la sesión de WhatsApp despierta y evadir que el sistema caiga en inactividad tras no recibir input humano.
- **Modo Debugging:** Bandera `--debug` para registrar meticulosamente los dispatchers sintéticos y acciones profundas en el terminal.
- **Exportaciones y Análisis:** Guarda en Base de Datos (SQLite), expórtalo a `.xlsx` o genera un **Dashboard HTML interactivo** para visualizar gráficos de presencia.

---

## 🚀 Instalación y Uso (Local)

Dado que este es un fork de desarrollo, la mejor manera de correrlo es clonando y usando un entorno virtual:

```bash
# 1. Crear y activar el entorno virtual
python3 -m venv .venv
source .venv/bin/activate

# 2. Instalar el paquete en modo de desarrollo
pip install -e ".[dev]"
```

### Ejecutar Localmente

**Primera ejecución (Con navegador visible para escanear QR):**
```bash
whatsapp-beacon -u "Nombre Del Contacto" --browser firefox
```

**Ejecuciones posteriores silenciosas (Headless):**
```bash
whatsapp-beacon -u "Nombre Del Contacto" --browser firefox --headless
```

---

## 📊 Panel de Analíticas (Dashboard)

El rastreador puede generar un sitio web estático (un reporte HTML) super visual basado en los datos que ha recabado:

```bash
whatsapp-beacon --analytics
```

El reporte se guardará en `analytics/index.html`. Puedes abrirlo con cualquier navegador para visualizar barras de tiempo, horas de mayor frecuencia de conexión y las sesiones más largas.

---

## ⚙️ Banderas Adicionales

| Argumento | Descripción |
|----------|-------------|
| `-u`, `--username` | Nombre exacto del contacto tal y como lo tienes agendado. |
| `-b`, `--browser` | Navegador a utilizar (`chrome` o `firefox`). Defecto: `chrome`. |
| `-l`, `--language` | Idioma de WhatsApp Web (`en`, `es`, `fr`, etc.). Defecto: `en`. |
| `--headless` | Modo invisible (Oculta la ventana del navegador). |
| `--debug` | Habilita logs profundos e imprime el ping Anti-Idle. |
| `-e`, `--excel` | Exporta la base de datos a Excel (`History_wp.xlsx`). |
| `--analytics` | Genera y guarda automáticamente el dashboard de estadísticas y sale. |

> **Aviso**: Herramienta creada con fines de investigación educativa.

---
