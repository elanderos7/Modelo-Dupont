# 📊 Modelo DuPont en Streamlit

Esta aplicación construida en **Streamlit** permite analizar la rentabilidad de un negocio utilizando el modelo financiero **DuPont**. El modelo descompone el **ROE** y **ROA** en sus principales componentes: margen, rotación y apalancamiento.

## 🚀 Funcionalidades

- Carga de archivos CSV o Excel con tus datos financieros.
- Cálculo automático de los siguientes indicadores:
  - Margen Neto (%)
  - Rotación (veces)
  - Apalancamiento (veces)
  - ROE (%) — Return on Equity
  - ROA (%) — Return on Assets
  - Pay Back Capital (veces)
  - Pay Back Activos (veces)
- Visualización en formato de reporte:
  - Columnas: períodos (trimestres, años, etc.)
  - Filas: indicadores
- Exportación del reporte a Excel.

## 🧾 Fórmulas utilizadas

- **Margen Neto (%)** = Utilidad Neta / Ventas Netas  
- **Rotación (veces)** = Ventas Netas / Activos Totales  
- **Apalancamiento (veces)** = Activos Totales / Capital Contable  
- **ROE (%)** = Margen Neto × Rotación  
- **ROA (%)** = Rotación × Apalancamiento  
- **Pay Back Capital (veces)** = 1 / ROE  
- **Pay Back Activos (veces)** = 1 / ROA  

## 📂 Estructura esperada del archivo

El archivo que cargues (CSV o Excel) debe tener las siguientes columnas:

| Periodo | Utilidad Neta | Ventas Netas | Activos Totales | Capital Contable |
|---------|----------------|---------------|------------------|--------------------|
| 2023Q1  | 1000           | 8000          | 20000            | 5000               |
| 2023Q2  | 1200           | 8500          | 21000            | 5500               |

## ▶️ Cómo correr la app localmente

```bash
git clone https://github.com/tu_usuario/modelo-dupont-streamlit.git
cd modelo-dupont-streamlit
python -m venv venv
source venv/bin/activate  # En Windows: venv\Scripts\activate
pip install -r requirements.txt
streamlit run app.py
```

## ☁️ Despliegue en Streamlit Cloud

1. Sube este repositorio a GitHub.
2. Ve a [streamlit.io/cloud](https://streamlit.io/cloud) y crea una nueva app desde el repositorio.
3. Asegúrate de que:
   - `app.py` sea el archivo principal.
   - `requirements.txt` esté presente.

¡Y listo! Tu app estará disponible en línea.

## 📧 Contacto

¿Tienes dudas o sugerencias?  
Escríbeme o abre un issue en el repositorio.