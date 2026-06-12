# moodle-mcp

Configuración de MCP en moodle.

## Puesta en marcha

1. Arrancar el [servidor moodle](https://github.com/ijaureguialzo/moodle-docker) de prueba.

2. Completar el [instalador web](https://moodle.test).

3. Activar el [protocolo MCP](https://moodle.test/admin/settings.php?section=webserviceprotocols).

4. [Crear el servicio](https://moodle.test/admin/settings.php?section=externalservices) y darle permisos añadiendo
   funciones (ej. `core_course*` y `mod_forum*`).

5. [Crear un token](https://moodle.test/admin/webservice/tokens.php) para el usuario que queramos que use el agente.

6. Configurar el fichero MCP del agente reemplazando el token.

   <br>Hermes (`~/.hermes/config.yaml`):

   ```yaml
   moodle:
     url: https://moodle.test/webservice/mcp/server.php?wstoken=TOKEN
     ssl_verify: false
     enabled: true
   ```
