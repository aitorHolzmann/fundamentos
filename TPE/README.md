# Trabajo Práctico Especial: Global Food & Nutrition Database 2026
**Materia:** Fundamentos de la Ciencia de Datos (UNICEN) - Cursada 2026  
**Ayudante Asignado:** Duilio Deangeli  
**Integrantes:** [Completar nombres]

---

## 📋 Descripción del Proyecto
Este repositorio contiene el desarrollo completo del Trabajo Práctico Especial (TPE). Se realiza un análisis exploratorio, preprocesamiento y contrastación estadística de hipótesis univariadas, bivariadas y multivariadas sobre la base de datos *Global Food & Nutrition Database 2026 – Health Scores & Allergens*.

## 🚀 Instrucciones de Instalación y Ejecución Local

### 1. Clonar el Repositorio
```bash
git clone <URL_DEL_REPOSITORIO>
cd <CARPETA_DEL_PROYECTO>/TPE
```

### 2. Crear y Activar el Entorno Virtual
Se recomienda utilizar Python 3.11 o superior (entorno probado en Python 3.14):

```bash
# Crear entorno virtual
python3 -m venv venv

# Activar en Linux/macOS:
source venv/bin/activate

# Activar en Windows:
# .\venv\Scripts\activate
```

### 3. Instalar Dependencias
```bash
pip install --upgrade pip
pip install -r requirements.txt
```

### 4. Registrar el Kernel en Jupyter
```bash
python -m ipykernel install --user --name amb-tpe --display-name "Python (amb-tpe)"
```

### 5. Ejecutar la Notebook
1. Abrir el proyecto en **VS Code**, **JupyterLab** o **Jupyter Notebook**:
   ```bash
   jupyter lab
   ```
2. Abrir `tpe.ipynb`.
3. En la esquina superior derecha del editor, verificar y seleccionar el kernel **`Python (amb-tpe)`**.
4. Ejecutar las celdas secuencialmente (`Run All` o celda por celda).

---

## 📁 Estructura del Proyecto
```text
TPE/
├── global_food_nutrition.csv    # Dataset crudo (incluido según pauta de cátedra)
├── tpe.ipynb                   # Notebook única organizada en 5 secciones
├── requirements.txt            # Dependencias reproducibles de Python
├── README.md                   # Instrucciones de configuración y ejecución
└── Enunciado TPE ... .pdf      # Enunciado oficial de la cátedra
```
