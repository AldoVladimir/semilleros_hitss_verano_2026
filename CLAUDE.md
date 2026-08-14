# Curso de Machine Learning — Semilleros HITSS Verano 2026

Material de un curso universitario de ML: sesiones de 2 h.
Temario en cinco módulos: aprendizaje estadístico (scikit-learn) →
redes neuronales (PyTorch) → visión computacional con detección de objetos (Ultralytics YOLO) →
IA agéntica (AWS Strands Agents, modelos vía Bedrock) →
producción en AWS (contenerización con ECS, SageMaker, Bedrock AgentCore).

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
- Esta regla de estilo de comunicación aplica también a las respuestas de Claude en
  el chat, no solo al material escrito: concreto y sin relleno, sin jerga
  corporativa ("alinear expectativas", "poner sobre la mesa", "a nivel de",
  "insights accionables", "leverage", "sinergia"), sin condescendencia — explicar
  sin asumir que el lector no puede seguir el razonamiento, sin sobreexplicar lo
  obvio. Español neutro: sin regionalismos ni modismos propios de un solo país
  hispanohablante. Sin anglicismos crudos cuando existe un término establecido en
  español: no "commitear", sí "versionar" o "confirmar".
- No anthropomorfizar las matemáticas ni los algoritmos: nada de verbos que les den
  intención o agencia ("la regularización domestica la varianza", "el modelo
  persigue el ruido", "Lasso apaga coeficientes", "aplasta los pesos"). Decir qué
  es la cantidad y cómo se calcula, no qué "parece hacer". Preferir el término
  técnico establecido en la literatura (ej. *shrinkage* / contracción) sobre una
  imagen inventada.
- No inventar: si un dato, una decisión de alcance o una convención no está clara,
  preguntar antes de asumir. No generar notebooks completos sin un outline aprobado
  primero.
- Sin antítesis retórica, en ninguna variante: ni "no es X: es Y", ni la forma
  disfrazada "A responde a Z, no a W" o "no una relación estadística sino
  geométrica". Es el recurso que más delata redacción generada por IA. Afirmar el
  hecho directamente. Si la aclaración ya se dio antes en el mismo notebook, no
  repetirla reformulada — omitirla, o dejar que el término técnico ya la implique
  (ej. "artefacto geométrico" descarta una relación estadística sin decirlo).
  Registro de libro de texto (referencia: *The Elements of Statistical Learning* de
  Hastie/Tibshirani/Friedman; principios de Halmos, *How to Write Mathematics*, y de
  Knuth/Larrabee/Roberts, *Mathematical Writing*): una afirmación autocontenida por
  oración, sin gancho narrativo ("resulta que...", "lo interesante es que..."), sin
  guion largo como muletilla de inciso.
- Tampoco anuncios de transición que retrasan el dato antes de darlo ("tiene una
  consecuencia:", "esto provoca que", "el resultado es que", "esto tiene un efecto:"):
  es la misma cadencia de suspenso que la antítesis, aplicada a causa-efecto en vez de
  a contraste. El dato va en la misma cláusula que lo introduce, sin anunciarlo antes.
- Guion largo (—) reservado para una ruptura real de la oración, no como conector por
  defecto entre una afirmación y su explicación: para eso están el punto, los dos
  puntos, la coma o el paréntesis. Más de un guion largo en una misma oración es señal
  de que se está usando como muletilla; hay que reescribir. Excepciones, ambas
  tipográficas y no prosa: como separador de título/subtítulo en encabezados de
  sección o de figura ("Reto — ensambles a escala real"), y como separador entre el
  término en negrita que abre un ítem de lista y su explicación ("**Bagging** —
  entrena muchos árboles...").

## Entorno

- `uv sync` y nada más. Prohibido Colab, Anaconda o `pip install` suelto.
- Notebooks Jupyter ejecutados en VS Code con el kernel del `.venv` del proyecto.
- La versión de Python se fija en `pyproject.toml` (`requires-python`); no hay `.python-version`.
- Cómputo mixto: laptops de estudiantes con **Windows/CPU**, laboratorio con **Linux/GPU**.
  Todo el material de los módulos 1–2 debe correr en CPU en tiempos razonables;
  solo el fine-tuning de YOLO (módulo 3) asume GPU.
- El módulo 5 requiere una cuenta AWS Academy Learner Lab (gestionada por el
  instructor) y Docker instalado localmente; ningún otro módulo depende de servicios
  en la nube.
- Los despliegues de contenedores del módulo 5 usan siempre CPU (ECS Fargate); no se
  cubre el launch type EC2/GPU.

## Convenciones del material

- Un notebook por sesión: `NN-tema.ipynb` (ej. `01-regresion-lineal.ipynb`),
  dentro de `notebooks/modulo-XX-nombre/`. Ejercicios en `ejercicios/` de cada módulo.
- Estructura pedagógica de cada notebook: motivación → teoría en markdown con LaTeX →
  código ejecutable → ejercicio. En el módulo 5 (infraestructura, no matemática), la
  "teoría en LaTeX" se reemplaza por contexto técnico en markdown: arquitectura del
  servicio, diagramas de flujo, contratos de API.
- Datasets **nunca** al repo: usar los loaders de las librerías
  (`sklearn.datasets`, `torchvision.datasets`, descarga automática de Ultralytics)
  con caché en `datos/` (gitignored).
- **Plotly** es la librería de graficación estándar del curso: interactiva y
  consistente en los cuatro módulos. Excepción única y explícita: utilidades de
  diagnóstico de scikit-learn sin equivalente en Plotly (`plot_tree`,
  `ConfusionMatrixDisplay`) pueden usar matplotlib — se marca como excepción en el
  notebook donde aparezca.
- Los `.ipynb` se versionan sin outputs ni metadata de ejecución (filtro nbstripout
  vía `.gitattributes`).
- Los estudiantes solo hacen `clone` + `pull`: no editan los notebooks originales,
  trabajan sobre copias en `mi-trabajo/` (gitignored).

## Estilo de código

- ruff como formateador y linter (grupo dev).
- Código idiomático y explícito — es material que los estudiantes van a leer e imitar.
  En PyTorch, training loops explícitos: nada de abstracciones que escondan la mecánica.
