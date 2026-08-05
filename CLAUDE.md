# Curso de Machine Learning — Semilleros HITSS Verano 2026

Material de un curso universitario de ML: ~20 sesiones de 2 h.
Temario en cuatro módulos: aprendizaje estadístico (scikit-learn) →
redes neuronales (PyTorch) → visión computacional con detección de objetos (Ultralytics YOLO) →
IA agéntica (AWS Strands Agents, modelos vía Bedrock).

## Idioma y tono

- Prosa, markdown y docstrings en **español**. Código e identificadores en **inglés**.
- Tono formal, técnico y preciso. Sin adjetivos innecesarios ni frases vagas —
  preferir "cálculo por operaciones matriciales" sobre "cómputo preciso".
  El material presenta hechos, no opiniones.
- Sin coloquialismos ni muletillas conversacionales: nada de complicidad con el
  lector ("y está bien", "tráelo a...", "guarda este resultado"), nada de relleno
  ("ahora sí", "ojo:"), nada de metáforas o eslóganes ("un lado oscuro", "es un
  lujo", "aprenderlo una vez es aprenderlos todos"). Registro de texto académico:
  tercera persona o primera persona del plural exhortativa ("consideremos",
  "definamos"), nunca dirigirse al lector como a un compañero.
- No inventar: si un dato, una decisión de alcance o una convención no está clara,
  preguntar antes de asumir. No generar notebooks completos sin un outline aprobado
  primero.
- NO uses antitética

## Entorno

- `uv sync` y nada más. Prohibido Colab, Anaconda o `pip install` suelto.
- Notebooks Jupyter ejecutados en VS Code con el kernel del `.venv` del proyecto.
- La versión de Python se fija en `pyproject.toml` (`requires-python`); no hay `.python-version`.
- Cómputo mixto: laptops de estudiantes con **Windows/CPU**, laboratorio con **Linux/GPU**.
  Todo el material de los módulos 1–2 debe correr en CPU en tiempos razonables;
  solo el fine-tuning de YOLO (módulo 3) asume GPU.

## Convenciones del material

- Un notebook por sesión: `NN-tema.ipynb` (ej. `01-regresion-lineal.ipynb`),
  dentro de `notebooks/modulo-XX-nombre/`. Ejercicios en `ejercicios/` de cada módulo.
- Estructura pedagógica de cada notebook: motivación → teoría en markdown con LaTeX →
  código ejecutable → ejercicio.
- Datasets **nunca** al repo: usar los loaders de las librerías
  (`sklearn.datasets`, `torchvision.datasets`, descarga automática de Ultralytics)
  con caché en `datos/` (gitignored).
- **Plotly** es la librería de graficación estándar del curso: interactiva y
  consistente en los cuatro módulos. Excepción única y explícita: utilidades de
  diagnóstico de scikit-learn sin equivalente en Plotly (`plot_tree`,
  `ConfusionMatrixDisplay`) pueden usar matplotlib — se marca como excepción en el
  notebook donde aparezca.
- Los `.ipynb` se commitean sin outputs ni metadata de ejecución (filtro nbstripout
  vía `.gitattributes`).
- Los estudiantes solo hacen `clone` + `pull`: no editan los notebooks originales,
  trabajan sobre copias en `mi-trabajo/` (gitignored).

## Estilo de código

- ruff como formateador y linter (grupo dev).
- Código idiomático y explícito — es material que los estudiantes van a leer e imitar.
  En PyTorch, training loops explícitos: nada de abstracciones que escondan la mecánica.
