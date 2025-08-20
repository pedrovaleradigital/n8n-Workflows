# WORKFLOWS N8N

Este repositorio contiene workflows de n8n para automatización e integración de IA.

## Orquestador de IA para n8n (`202508 Orquestador de IA.json`)

Workflow que funciona como un orquestador de IA, seleccionando dinámicamente el modelo más adecuado basado en el tipo de entrada.

### Características

- **Clasificación automática**: Clasifica las solicitudes en categorías (general, razonamiento, programación, búsqueda)
- **Selección dinámica de modelos**: Enruta cada tipo de solicitud al modelo de IA más apropiado
- **Optimización de costos**: Utiliza modelos especializados para maximizar eficiencia y calidad
- **Memoria de conversación**: Mantiene el contexto de las conversaciones

### Modelos incluidos

- **Claude Sonnet 4**: Para programación
- **Gemini Thinking Pro**: Para razonamiento complejo
- **GPT 4.1 mini**: Para consultas generales
- **Perplexity**: Para búsquedas y información actualizada

### Uso

1. Importa el archivo `202508 Orquestador de IA.json` en tu instancia de n8n
2. Configura tus credenciales de API para cada proveedor de IA
3. Activa el workflow
4. Envía mensajes de chat que serán automáticamente enrutados al modelo apropiado

### Configuración

El workflow está completamente en español y listo para usar. Solo necesitas configurar las credenciales de API en n8n para:

- Anthropic (Claude)
- Google (Gemini)
- OpenAI (GPT)
- OpenRouter (Perplexity)