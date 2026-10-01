# Guía Práctica: Entornos Virtuales y Flujo de Trabajo en Notebooks

Esta guía describe el procedimiento técnico estándar para gestionar ambientes virtuales y ejecutar notebooks en VS Code para la materia **Fundamentos del Análisis de Datos**.

---

## 1. Creación y Registro del Entorno Virtual (Venv)

Para cada Trabajo Práctico (ej. `tp5`), se crea y configura un entorno virtual dedicado:

### Paso 1: Crear el entorno virtual en la carpeta del TP
```bash
cd /home/facha/Documents/FACU/fundamentos/fundamentos/tp5
python3 -m venv amb-tp5
```

### Paso 2: Activar e instalar dependencias oficiales
```bash
source amb-tp5/bin/activate
pip install --upgrade pip
pip install pandas numpy scipy matplotlib seaborn ipykernel
```

### Paso 3: Registrar el kernel en Jupyter para VS Code
```bash
python -m ipykernel install --user --name amb-tp5 --display-name "Python (amb-tp5)"
```

### Paso 4: Selección del Kernel en VS Code
1. Abre el archivo `.ipynb` correspondiente en VS Code.
2. En la esquina superior derecha del notebook, haz clic en **Select Kernel** (Seleccionar kernel).
3. Selecciona **Jupyter Kernel...** y elige **Python (amb-tp5)**.

---

## 2. Buenas Prácticas de Reproducibilidad en Notebooks

1. **Celda inicial de imports:**
   ```python
   import numpy as np
   import pandas as pd
   import matplotlib.pyplot as plt
   import seaborn as sns
   from scipy import stats

   # Configuración estética base
   sns.set_theme(style="whitegrid")
   plt.rcParams['figure.dpi'] = 110
   ```

2. **Rutas relativas y carga robusta de datos:**
   - Cargar siempre los datasets usando rutas relativas o descargándolos automáticamente si no existen localmente:
     ```python
     import os
     data_path = "ObesityDataSet_raw_and_data_sinthetic.csv"
     if not os.path.exists(data_path):
         # Lógica de descarga alternativa si fuera necesario
         pass
     df = pd.read_csv(data_path)
     ```

3. **Higiene de ejecución:**
   - Las celdas deben ejecutarse en orden secuencial estricto de arriba hacia abajo.
   - Antes de entregar o dar por terminado un TP, ejecutar siempre **Restart Kernel and Run All Cells** para verificar que no existan variables huérfanas en memoria.

