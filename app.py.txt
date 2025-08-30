import streamlit as st
import pandas as pd

st.set_page_config(page_title="Modelo DuPont", layout="wide")

st.title("📊 Modelo DuPont - Análisis de Rentabilidad")

archivo = st.file_uploader("📥 Carga tu archivo (.csv o .xlsx)", type=["csv", "xlsx"])

if archivo:
    if archivo.name.endswith(".csv"):
        df = pd.read_csv(archivo)
    else:
        df = pd.read_excel(archivo)

    columnas = ["Periodo", "Utilidad Neta", "Ventas Netas", "Activos Totales", "Capital Contable"]
    if not all(col in df.columns for col in columnas):
        st.error(f"⚠️ El archivo debe contener: {', '.join(columnas)}")
    else:
        df = df.sort_values("Periodo").reset_index(drop=True)

        df["Margen Neto (%)"] = df["Utilidad Neta"] / df["Ventas Netas"] * 100
        df["Rotación (veces)"] = df["Ventas Netas"] / df["Activos Totales"]
        df["Apalancamiento (veces)"] = df["Activos Totales"] / df["Capital Contable"]
        df["ROE (%)"] = df["Margen Neto (%)"] * df["Rotación (veces)"]
        df["ROA (%)"] = df["Rotación (veces)"] * df["Apalancamiento (veces)"]
        df["Pay Back Capital (veces)"] = 1 / df["ROE (%)"]
        df["Pay Back Activos (veces)"] = 1 / df["ROA (%)"]

        df = df.round(1)

        indicadores = [
            "Margen Neto (%)",
            "Rotación (veces)",
            "Apalancamiento (veces)",
            "ROE (%)",
            "ROA (%)",
            "Pay Back Capital (veces)",
            "Pay Back Activos (veces)"
        ]

        resumen = df[["Periodo"] + indicadores].set_index("Periodo").T

        st.subheader("📄 Reporte Formato Transpuesto")
        st.dataframe(resumen, use_container_width=True)

        st.download_button(
            label="📤 Descargar Excel",
            data=resumen.to_excel(index=True, engine="openpyxl"),
            file_name="Reporte_DuPont.xlsx",
            mime="application/vnd.openxmlformats-officedocument.spreadsheetml.sheet"
        )
