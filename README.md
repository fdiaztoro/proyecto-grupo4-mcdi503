# Proyecto grupo 4 · MCDI503 Exploración Inteligente de Datos

Proyecto ABP del curso MCDI503 (Magíster en Ciencias de Datos e Inteligencia Artificial, UNAB): análisis exploratorio de datos (EDA) reproducible en Jupyter Notebook, desde la definición del problema hasta el pipeline final de variables.

## Integrantes
- Felipe Díaz Toro ([@fdiaztoro](https://github.com/fdiaztoro))
- Pablo Ríos Passteni ([@pablo9876](https://github.com/pablo9876))
- Guillermo Subiabre Chacón ([@Gsubiabre](https://github.com/Gsubiabre))
- Ninoska Yévenes Hernández ([@nyevenes](https://github.com/nyevenes))

## Evaluaciones
Las formativas (0 %) orientan cada sumativa; todas las entregas vencen a las 23:59.

| Evaluación | Pondera | Vence |
| --- | --- | --- |
| Formativa 1 · Ficha del proyecto y plan inicial de EDA (PDF) | 0 % | Jue 26 nov |
| Sumativa 1 · EDA inicial reproducible (PDF + notebook) | 20 % | Dom 29 nov |
| Formativa 2 · Avance Fases 2 y 3 | 0 % | Jue 3 dic |
| Sumativa 2 · Calidad, limpieza y EDA univariado/bivariado | 40 % | Dom 6 dic |
| Formativa 3 · Avance Fase 4 | 0 % | Jue 10 dic |
| Sumativa 3 · Pipeline y presentación final | 30 % | Dom 13 dic |
| Sumativa 4 · Autoevaluación y coevaluación (individual) | 10 % | Mié 16 dic |

## Estructura
- `notebooks/`: notebooks de Jupyter (un archivo por sumativa).
- `data/raw/`: datasets de trabajo. No se suben a GitHub (ver `.gitignore`).
- `docs/`: apuntes, resúmenes semanales, rúbricas y borradores de informes.

## Dataset
Dataset del curso a definir por el grupo: `titanic` (recomendado), `mpg` o `penguins`. Se cargan desde Seaborn, por lo que no requieren descarga. Si se usa un archivo externo, copiarlo en `data/raw/` y registrar su tamaño y hash SHA-256 en `docs/`.

## Reglas de entrega
- Nombres sin tildes, ñ ni símbolos: `mcdi503_f1f_grupo4.pdf` (formativa), `mcdi503_f1_sumativo_grupo4.pdf` y `mcdi503_f1_sumativo_grupo4.ipynb` (sumativa).
- PDF de máximo 3 páginas, APA 7, Arial o Calibri 11. El notebook se entrega ejecutado.
- Un integrante sube los archivos al buzón de Canvas con la opción "Examinar mi equipo".

## Trabajo en equipo
- `main` contiene solo lo entregado; `develop` integra el trabajo en curso.
- Cada integrante trabaja en una rama propia, abre un PR a `develop` y otra persona lo aprueba antes de fusionarlo.
- Cada notebook debe ejecutarse completo desde cero, sin errores, antes de abrir el PR.

## Requisitos y ejecución

Python 3.13 o superior

```bash
# 1. Clonar repositorio e ingresar a la carpeta
git clone https://github.com/fdiaztoro/proyecto-grupo4-mcdi503.git
cd proyecto-grupo4-mcdi503

# 2. Crear y activar entorno virtual
python3 -m venv .venv
source .venv/bin/activate        # macOS y Linux
# .venv\Scripts\activate         # Windows

# 3. Instalar dependencias del proyecto
python -m pip install --upgrade pip
python -m pip install -r requirements.txt

# 4. Activar la higiene automática de notebooks en el repositorio local
# nbstripout borra las salidas (outputs) de las celdas antes de cada commit
nbstripout --install
# - extrakeys: quita metadata ruidosa que varía según el entorno de cada integrante.
# - --keep-id: evita diffs de metadata cuando alguien commitea el notebook.
git config filter.nbstripout.extrakeys "metadata.language_info.version metadata.colab cell.metadata.id cell.metadata.colab cell.metadata.outputId" \
  && git config filter.nbstripout.clean "$(git config filter.nbstripout.clean) --keep-id"

# 5. Registrar el kernel del proyecto en Jupyter
python -m ipykernel install --user --name grupo4_mcdi503 --display-name "Python (grupo4-mcdi503)"
```

Los notebooks de entrega conservan sus salidas (están excluidos del filtro en `.gitattributes`), porque Canvas exige el notebook ejecutado.
