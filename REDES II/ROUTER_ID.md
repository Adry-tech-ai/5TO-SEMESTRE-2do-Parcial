# ROUTER ID
- Identificador unico de un router
- Este se disigna de la siguiente manera:
  1. Se designa de forma manual con el comando: `router id [id]`
  2. Elije la interfaz fisica mas alta conectada al router, nota: este no se modifica hasta que se reinicie el router o el proceso.
 
# DR Y BDR
- Este es útil para la sincronizacion con la base de datos.
- Se designa de la siguiente manera:
  1. Observa la prioridad que tiene el router, si es que tiene una.
  2. La interfaz Loopback más alta configurada en el router.
  3. La interfaz física más alta conectada al router.  
<img width="1200" height="1600" alt="image" src="https://github.com/user-attachments/assets/9068f29e-435b-4e46-94e3-1016937084f0" /># Router ID
# CUAL ES EL ROUTER DR Y BDR DE LA IMAGEN
-EL route DR es el router A y el BDR es el D (escogiento la ip mas alta dando), la lookback tiene mas prioridad que la IPv4 configurada en los giheternet
