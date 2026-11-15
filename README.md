### AI Agents Action
CODIGO PARA AGENTES DE IA 

Este repositorio contiene el código de ejemplo del libro AI Agents in Action, Second Edition (Manning). El código demuestra cómo crear y ejecutar agentes de IA utilizando el SDK de OpenAI Agents y el Protocolo de Contexto de Modelo (MCP).
Instrucciones de configuración
## 1. Clonar el repositorio
Para comenzar, clona este repositorio en tu equipo local:
```bash
git clone https://github.com/cxbxmxcx/AI-Agent-Workflows.git
cd AI-Agent-Workflows
```

### 2. Instalar los requisitos previos
- Python 3.11 o posterior. Las versiones fijadas de las dependencias se han probado con Python 3.11, 3.13 y 3.14.
- Node.js 20 o posterior. Los servidores MCP que los ejemplos inician con npx se ejecutan en Node.js (consulta el apéndice B).
- Graphviz. El capítulo 4 genera gráficos de agentes mediante draw_graph(...).view(), lo cual requiere que los programas de Graphviz estén disponibles en tu variable PATH, no solamente el paquete de Python. Puedes instalarlos desde graphviz.org.
- Docker o el servidor Phoenix (capítulo 7). Los ejemplos de trazabilidad envían sus registros de ejecución (traces) a Phoenix. Puedes iniciar el contenedor indicado al principio de cada archivo de trazabilidad del capítulo 7 o prescindir de Docker e iniciar el mismo servidor mediante phoenix serve. En Python 3.12 y versiones posteriores, requirements.txt instala el comando phoenix; en Python 3.11, utiliza Docker.
3. Crear tu entorno
Este proyecto requiere Python 3.11 o posterior. Crea y activa un entorno virtual de Python:
En Windows:
```bash
python -m venv venv
venv\Scripts\activate
```
En macOS/Linux:
```bash
python3 -m venv venv
source venv/bin/activate
```
Si prefieres utilizar un entorno externo de Python, asegúrate de configurar la ruta de Python en VS Code:
1. Abre la Paleta de comandos (Ctrl+Shift+P o Cmd+Shift+P en macOS).
2. Busca "Python: Select Interpreter".
3. Selecciona el intérprete de Python correspondiente a tu entorno.
4. Instalar las dependencias
Opción A: Utilizar la depuración de VS Code
Si tienes VS Code, simplemente puedes iniciar la depuración (presiona F5) para ejecutar los ejemplos.

La tarea Install requirements se ejecuta antes de cada inicio e instala cualquier dependencia que falte de las especificadas en requirements.txt. Por eso, la primera ejecución puede tardar unos minutos, mientras que las siguientes se iniciarán inmediatamente.
Opción B: Instalación manual
Como alternativa, puedes instalar manualmente las dependencias utilizando pip:
```bash
pip install -r requirements.txt
```
El archivo requirements.txt fija las versiones exactas con las que se han probado los ejemplos. Mantén estas versiones sin cambios: en particular, mcp debe permanecer por debajo de la versión 2.0, porque la versión 2 eliminó la clase FastMCP, sobre la cual están construidos los servidores de los capítulos 3 y 4.
5. Configurar el entorno
Copia el archivo .env.example en un archivo llamado .env dentro del directorio raíz y completa tus claves:

```
'OPENAI_API_KEY'=your_openai_api_key
'BRAVE_API_KEY'=your_brave_api_key
'OPENAI_DEFAULT_MODEL'=gpt-5.1
```
- OPENAI_API_KEY es necesaria para todos los ejemplos. Puedes obtener una clave API desde la página de claves API de OpenAI.
- BRAVE_API_KEY  es necesaria para los agentes de investigación de los capítulos 9 y 10, que realizan búsquedas en la web mediante el servidor Brave Search MCP. Puedes obtener una clave desde la página de Brave Search API.
- OPENAI_DEFAULT_MODEL establece el modelo que utilizarán todos los agentes que no especifiquen uno. Sin esta variable, el SDK de Agents utiliza su propio modelo predeterminado, que cambia de una versión a otra.
VS Code carga automáticamente el archivo .env cuando inicias un ejemplo con F5.

La mayoría de los ejemplos no cargan este archivo por sí mismos. Por lo tanto, cuando los ejecutes desde una terminal, debes configurar las variables en tu shell o permitir que python-dotenv cargue el archivo:
python -m dotenv run -- python chapter_04/01_single_agent_multiple_mcp.py

6. Ejecutar el código
Ejecuta los ejemplos desde el directorio raíz del repositorio, porque varios de ellos abren archivos utilizando rutas relativas a ese directorio.

Por ejemplo:
```
python chapter_02/01_first_agent.py
```
Esto ejecutará el agente y mostrará el resultado en la terminal.
Servidores MCP durante la primera ejecución
Muchos ejemplos inician servidores MCP utilizando npx (Node.js) o uvx (Python).

La primera vez que un ejemplo inicia un servidor, npx o uvx lo descarga. Este proceso puede tardar desde unos segundos hasta un minuto o más. Los ejemplos esperan el tiempo suficiente para que se complete la descarga.

Para descargar previamente todos los servidores, ejecuta:
```
python tools/check_repo.py --servers
```
Estructura del repositorio
- chapter_02 a chapter_11: contienen el código correspondiente a cada capítulo del libro. El directorio chapter_08/microservices/ contiene la implementación mediante Docker Compose del ejemplo 8.5.
- bonus_projects/: contiene ejemplos adicionales que van más allá del contenido del libro.
- extras/: contiene material que no forma parte del libro:
  - demo_project/: una secuencia de demostración construida a partir de los ejemplos de los capítulos 2 al 6.
  - chapter_12/: un esquema de cliente Agent2Agent (A2A).
- tools/check_repo.py: verifica el repositorio para detectar problemas conocidos y descarga previamente los servidores MCP.
Archivos renombrados
Tres archivos fueron renombrados después de la primera impresión para corregir errores tipográficos en sus nombres:
Primera impresión	Nombre actual
chapter_04/06_agent_to_agent_monitroing_handoffs.py	chapter_04/06_agent_to_agent_monitoring_handoffs.py
chapter_04/10_agent__guardrails_retry.py	chapter_04/10_agent_guardrails_retry.py
chapter_05/04_time_travel_agent_soluriont.py	chapter_05/04_time_travel_agent_solution.py


Ejercicios
Los ejercicios que aparecen al final de cada capítulo son abiertos y no existe un conjunto oficial de soluciones.

El archivo chapter_05/04_time_travel_agent_solution.py contiene una solución desarrollada para uno de los ejercicios del capítulo 5.
Notas
- Asegúrate de utilizar el intérprete de Python correcto, que corresponda a tu entorno.
- El archivo .env no debe compartirse ni incluirse en el control de versiones para mantener segura tu clave API.
- El archivo ERRATA.md contiene las correcciones realizadas desde la primera impresión. Además, el comando python tools/check_repo.py verifica una copia del repositorio para comprobar cada una de estas correcciones.
Nota técnica: Se han traducido los textos explicativos, encabezados y comentarios descriptivos al español. Se han conservado sin modificaciones los comandos de Python, Bash, las rutas, los nombres de archivos, las variables de entorno, las funciones, las clases, las dependencias y las instrucciones ejecutables para que puedas copiar y ejecutar el código sin introducir errores.
