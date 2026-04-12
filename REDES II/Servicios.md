# SERVICIOS
## PUERTOS
- HTTP  : 80
- HTTPS : 43
- TFTP  : 69
- FTP   : 20 Y 21 
## TFTP
- Servidor Anónimo, no requiere autenticacion, no tiene seguriddad.
- Se utiliza para almacenar configuraciones de tus dispositivos.
  ```
  COMANDOS:

  SW1# COPY RUNNING-CONFIG TFTP:
      [IP_SERVIDOR_TFTP]
      [NOMBRE_ARCHIVO]
  ```

## FTP 
- Para datos y sincronizacion, se requiere usuario y contraseña para ingresar.
- Se pueden crear usuarios con permisos W-R-D-R(rename)-L(list).
  ```
  COMANDOS:

  C:\> FTP [DIRECCION_SERVER_FTP]
  USERNAME : ALVAREX
  PASSWORD : *****
  ftp> put [archivo_pc_a_server]
  ftp> get [archivo_server_a_pc]
## EMAIL
- Debe haber un dominio ej: alvarex.com
- Usuarios y Contraseñas
