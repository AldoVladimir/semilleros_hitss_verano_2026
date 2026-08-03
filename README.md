# Curso de Machine Learning — Semilleros HITSS Verano 2026

Curso universitario de Machine Learning: 1 mes, 2 horas diarias.

| Módulo | Tema | Herramienta principal |
|---|---|---|
| 1 | Aprendizaje estadístico | scikit-learn |
| 2 | Redes neuronales | PyTorch |
| 3 | Visión computacional y detección de objetos | Ultralytics YOLO |

Todo el material son notebooks de Jupyter que se ejecutan en **VS Code**
(no usamos Colab ni Anaconda). Los módulos 1 y 2 corren en tu laptop;
el entrenamiento del módulo 3 se hace en las máquinas del laboratorio (GPU).

## Instalación

Sigue el **[instructivo de instalación](INSTALACION.md)** paso a paso (VS Code, git,
uv, clonar el repo y crear el ambiente). Al final, el notebook
`notebooks/modulo-01-aprendizaje-estadistico/00-verifica-tu-entorno.ipynb`
verifica que todo quedó funcionando.

## Cómo trabajar durante el curso

- **Al inicio de cada sesión:** `git pull` para recibir el material del día.
- **No edites los notebooks originales.** Copia el notebook de la sesión a la
  carpeta `mi-trabajo/` (créala en la raíz del repo; git la ignora) y trabaja
  sobre tu copia. Así `git pull` nunca te genera conflictos.
- La carpeta `datos/` también es local: ahí se descargan los datasets, no se suben al repo.
