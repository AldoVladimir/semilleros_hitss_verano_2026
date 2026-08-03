# Instructivo de instalación

**Curso de Machine Learning — Semilleros HITSS Verano 2026**

Sigue estos pasos **antes de la primera sesión**. Al final tendrás todo instalado y
verificado. Si algo falla y no logras resolverlo, anota en qué paso te quedaste y
tráelo a la primera sesión.

Tiempo estimado: 20–30 minutos (más la descarga de librerías, que depende de tu internet).

---

## Paso 1 — VS Code

Es el editor donde trabajaremos todo el curso.

1. Descárgalo de <https://code.visualstudio.com/> e instálalo con las opciones por defecto.
2. Ábrelo una vez para confirmar que funciona.

## Paso 2 — Git

Git es el control de versiones con el que recibirás el material cada día.

**Windows** — descarga el instalador desde <https://git-scm.com/download/win>,
ejecútalo y acepta todas las opciones por defecto.

**Linux:**

```bash
sudo apt install git
```

**Verifica:** cierra la terminal, abre una nueva y ejecuta:

```
git --version
```

Debe responder algo como `git version 2.x.x`.

## Paso 3 — uv

[uv](https://docs.astral.sh/uv/) es el manejador de ambientes de Python que usamos.
**No necesitas instalar Python por separado** — uv lo descarga y administra solo.
Tampoco necesitas (ni debes usar) Anaconda.

A diferencia de git, uv no tiene un instalador de doble clic: la vía oficial de descarga
es un comando que baja y ejecuta el instalador desde <https://astral.sh/uv>.

**Windows** — abre PowerShell y ejecuta:

```powershell
powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"
```

**Linux:**

```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
```

**Verifica:** cierra la terminal, abre una **nueva** (importante: la terminal vieja
no conoce el comando recién instalado) y ejecuta:

```
uv --version
```

## Paso 4 — Clonar el repositorio del curso

En la terminal, ve a la carpeta donde guardas tus proyectos y ejecuta:

```bash
git clone https://github.com/AldoVladimir/semilleros_hitss_verano_2026.git
cd semilleros_hitss_verano_2026
```

## Paso 5 — Instalar el ambiente del curso

Dentro de la carpeta del repo:

```bash
uv sync
```

Esto crea el ambiente en `.venv/` con **exactamente las mismas versiones para todos**
(están congeladas en el archivo `uv.lock`). Solo se hace una vez.

- En tu **laptop (Windows)** descarga alrededor de 1 GB — unos minutos.
- En las **máquinas del laboratorio (Linux con GPU)** descarga varios GB
  (las librerías de CUDA son pesadas) — puede tardar bastante más. Es normal.

## Paso 6 — Extensiones de VS Code

1. Abre VS Code.
2. Abre el panel de extensiones (`Ctrl+Shift+X`).
3. Instala estas dos:
   - **Python** (editor: Microsoft, id `ms-python.python`)
   - **Jupyter** (editor: Microsoft, id `ms-toolsai.jupyter`)

## Paso 7 — Verificación final

1. En VS Code: *File → Open Folder* y abre la carpeta `semilleros_hitss_verano_2026`.
2. Abre el notebook `notebooks/modulo-01-aprendizaje-estadistico/00-verifica-tu-entorno.ipynb`.
3. Arriba a la derecha, haz clic en **Select Kernel** y elige el intérprete que dice
   `.venv` (es el ambiente que creó `uv sync`).
4. Ejecuta todo el notebook (**Run All**).

Si todas las celdas corren sin error, **terminaste**. En tu laptop es normal que la
celda de GPU diga `False` — la GPU solo está en las máquinas del laboratorio.

---

## Problemas comunes

| Síntoma | Causa y solución |
|---|---|
| `git` o `uv` "no se reconoce como comando" | La terminal se abrió antes de la instalación. Cierra **todas** las terminales y abre una nueva. |
| PowerShell bloquea el script de uv | Usa exactamente el comando del Paso 3 — el `-ExecutionPolicy ByPass` va incluido. |
| En *Select Kernel* no aparece `.venv` | Verifica que abriste la **carpeta del repo** (no un archivo suelto) y que `uv sync` terminó sin error. Reinicia VS Code. |
| `uv sync` falla a medias | Casi siempre es la red. Vuelve a ejecutar `uv sync` — retoma donde se quedó. |
| Una celda del notebook marca `ModuleNotFoundError` | El kernel seleccionado no es el de `.venv`. Repite el paso 7.3. |
