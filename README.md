# moodle-mcp

Configuración de MCP en moodle.

## Puesta en marcha

1. Arrancar el [servidor moodle](https://github.com/ijaureguialzo/moodle-docker) de prueba.

2. Completar el [instalador web](https://moodle.test).

3. Activar el [protocolo MCP](https://moodle.test/admin/settings.php?section=webserviceprotocols).

4. [Crear el servicio](https://moodle.test/admin/settings.php?section=externalservices) y darle permisos añadiendo
   funciones (ej. `core_course_*` y `mod_forum_*`).

5. [Crear un token](https://moodle.test/admin/webservice/tokens.php) para el usuario que queramos que use el agente.

6. Configurar el fichero MCP del agente reemplazando el token.

   <br>Hermes (`~/.hermes/config.yaml`):

   ```yaml
   moodle:
     url: https://moodle.test/webservice/mcp/server.php?wstoken=TOKEN
     ssl_verify: false
     enabled: true
   ```

## Referencias

- [Moodle Plugins directory: Model Context Protocol | Moodle.org](https://moodle.org/plugins/webservice_mcp)
- [ijaureguialzo/moodle-webservice_mcp: A Moodle web service plugin that implements the MCP for seamless integration with AI assistants](https://github.com/ijaureguialzo/moodle-webservice_mcp)
- [Web services - MoodleDocs](https://docs.moodle.org/502/en/Web_services)
