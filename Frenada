import streamlit as st

# Función para calcular la capacidad de frenado
def capacidad_frenado(peso, traccion, km_neumaticos, condicion_asfalto):
    # Coeficiente de fricción estático medio para neumáticos de verano
    coef_resistencia = 0.8 if condicion_asfalto == 'seco' else 0.6
    
    # Asumir desgaste lineal de los neumáticos
    vida_util_delanteros = 20000 if traccion == 'delantera' else 35000
    vida_util_traseros = 80000 if traccion == 'delantera' else 35000
    
    desgaste_delanteros = km_neumaticos / vida_util_delanteros
    desgaste_traseros = km_neumaticos / vida_util_traseros
    
    # Limitar el desgaste al 100%
    desgaste_delanteros = min(desgaste_delanteros, 1)
    desgaste_traseros = min(desgaste_traseros, 1)
    
    # Ajustar coeficiente por desgaste
    coef_resistencia *= (1 - (desgaste_delanteros + desgaste_traseros) / 2)
    
    # Calcular capacidad de frenado
    capacidad_frenado = peso * coef_resistencia  # Esta es una simplificación
    return capacidad_frenado

# Interfaz de usuario en Streamlit
st.title('Calculadora de capacidad de frenado')

# Entrada de datos
peso = st.number_input('Peso del coche (kg)', min_value=0)
traccion = st.selectbox('Tipo de tracción', ['delantera', 'trasera'])
km_neumaticos = st.number_input('Kilómetros de uso de los neumáticos', min_value=0)
condicion_asfalto = st.selectbox('Condición del asfalto', ['seco', 'humedo'])

# Botón de cálculo
if st.button('Calcular capacidad de frenado'):
    resultado = capacidad_frenado(peso, traccion, km_neumaticos, condicion_asfalto)
    st.write(f'La capacidad de frenado estimada es: {resultado}')
