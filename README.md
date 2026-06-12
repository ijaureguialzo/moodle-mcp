# moodle-mcp

Configuración de MCP en moodle.

## Puesta en marcha

1. Arrancar el [servidor moodle](https://github.com/ijaureguialzo/moodle-docker) de prueba.

2. Completar el [instalador web](https://moodle.test).

3. Activar el [protocolo MCP](https://moodle.test/admin/settings.php?section=webserviceprotocols).

4. [Crear el servicio](https://moodle.test/admin/settings.php?section=externalservices) y darle permisos añadiendo
   funciones:

    - `core_course_*`
    - `mod_forum_*`
    - `core_group_*` (Recordarle que los usuarios tienen que estar inscritos en el curso para poder añadirlos a grupos)
    - `core_user_*` (Recordarle al agente que tiene darle un valor al password o dejarlo en automático con
      `createpassword: true`; si no, no se crean los usuarios)
    - `core_webservice_get_site_info`
    - `core_glossary_*` (El glosario ya tiene que existir, no hay función para crearlo)

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
- [Iconos de la UE para el etiquetado de contenidos generados por IA | Configurar el futuro digital de Europa](https://digital-strategy.ec.europa.eu/es/policies/eu-icons-labelling-ai-generated-content)

