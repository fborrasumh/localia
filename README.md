# LocalIA

Modelo local o API: qué tarea de investigación necesita cada uno. Aplicación web de un solo fichero.

**Usar la app:** https://fborrasumh.github.io/localia/

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.23114706.svg)](https://doi.org/10.5281/zenodo.23114706)

## Qué hace

- Ejecuta Qwen3-4B en el navegador (WebLLM con WebGPU) o en el equipo con Ollama, y lo prueba en cuatro tareas de investigación: anonimizar fragmentos de entrevista, extraer datos de resúmenes a JSON, cribar títulos y resúmenes y codificar texto cualitativo.
- Valida cada salida por código: el JSON y sus valores, que el tamaño muestral aparezca en el texto, que el diseño tenga su palabra clave, que las citas sean literales y que no queden datos personales conocidos tras anonimizar.
- Si la validación falla y la persona lo permite, repite la tarea con su API sobre texto enmascarado. La anonimización nunca se escala: lo que falla pasa a revisión humana.
- Redacta una síntesis narrativa con la API a partir de un JSON de datos extraídos y comprueba que no inventa cifras ni identificadores.
- Muestra una tabla comparativa con válidas en local, aciertos, errores silenciosos, escaladas, tiempo y una ruta sugerida por tarea. Exporta a Word, CSV y JSON reproducible.
- Incluye 20 resúmenes y 6 fragmentos de entrevista ficticios con respuesta correcta conocida, y un ejemplo con salidas precalculadas que funciona sin modelo ni clave.

## Cómo se usa la IA

El modelo local no necesita clave. Para el escalado y la síntesis, la persona usa su propia clave de OpenAI, Google Gemini o Anthropic Claude. La clave se guarda solo en el navegador. No hace falta servidor.

## Privacidad

Los textos y las respuestas del modelo local se quedan en el navegador. Solo se descargan el motor (jsDelivr) y los pesos del modelo (Hugging Face, unos 2,5 GB, luego en caché). Los resultados se guardan en IndexedDB. Hacia el proveedor de API solo sale texto con correos, DNI y teléfonos enmascarados por expresiones regulares, tras un aviso con muestra y confirmación; los nombres propios no se detectan por código.

## Límites

- Los datos de demostración son ficticios y los porcentajes no se pueden extrapolar a datos reales: hay que repetir la prueba con una muestra propia.
- Los errores silenciosos (respuestas incorrectas que el código da por válidas) solo se pueden contar con los datos ficticios.
- La ruta sugerida por tarea es una guía, no una garantía.
- Requiere un navegador con WebGPU (Chrome o Edge recientes) o Ollama con `OLLAMA_ORIGINS` configurado.
- La carga del modelo real depende de servicios externos y no se ha probado en el entorno de desarrollo, que no tiene WebGPU.

## Autoría

Fernando Borrás Rocher (Universidad Miguel Hernández de Elche).


ORCID: Fernando Borrás Rocher [0000-0002-5519-4573](https://orcid.org/0000-0002-5519-4573)

## Cómo citar

Borrás Rocher, F. (2026). *LocalIA* (v1.0.0) [Software]. DOI: [10.5281/zenodo.23114706](https://doi.org/10.5281/zenodo.23114706)

## Licencia

MIT. Véase [LICENSE](LICENSE).
