# 🚀 Quick Start: n8n Expert System

## ✅ Sistema Instalado

Tu workspace ahora tiene un sistema experto de n8n compuesto por:

### 📚 Skill: `n8n-expert`
Base de conocimiento completa sobre n8n

### 🤖 Agent: `prompt-n8n-assistant`
Asistente inteligente que usa el skill para ayudarte

---

## 💡 Cómo Usar

### Opción 1: Consulta Directa al Conocimiento
```
@n8n-expert [tu pregunta]
```

**Ejemplo:**
```
@n8n-expert show me how to configure a webhook trigger
```

### Opción 2: Asistente Interactivo (Recomendado)
```
@prompt-n8n-assistant [tu pregunta o solicitud]
```

**Ejemplos:**
```
@prompt-n8n-assistant necesito crear un workflow para Telegram bot

@prompt-n8n-assistant cómo configuro un AI Agent con memoria?

@prompt-n8n-assistant muéstrame JSON para Google Calendar integration
```

---

## 🎯 Casos de Uso Comunes

| Necesitas | Usa |
|-----------|-----|
| JSON de un nodo específico | `@n8n-expert` |
| Diseño completo de workflow | `@prompt-n8n-assistant` |
| Troubleshooting | `@prompt-n8n-assistant` |
| Conceptos y teoría | `@n8n-expert` |
| Implementación paso a paso | `@prompt-n8n-assistant` |
| Best practices | Cualquiera de los dos |

---

## 📦 Estructura del Sistema

```
.claude/
├── skills/
│   └── n8n-expert.md          # Base de conocimiento
├── agents/
│   └── prompt-n8n-assistant.md # Agente interactivo
├── README.md                    # Documentación completa
├── DEMO.md                      # 10 ejemplos de uso
└── QUICK_START.md              # Esta guía rápida
```

---

## 🔥 Ejemplos Rápidos

### 1. Configurar un nodo específico
```
@n8n-expert HTTP Request POST configuration
```

### 2. Crear workflow completo
```
@prompt-n8n-assistant create a workflow that:
- Receives webhook data
- Processes with AI Agent
- Saves to Airtable
```

### 3. Solucionar problemas
```
@prompt-n8n-assistant my AI Agent returns string instead of JSON, how to parse?
```

### 4. Integración con servicios
```
@prompt-n8n-assistant Google Calendar integration examples
```

### 5. Best practices
```
@n8n-expert error handling best practices
```

---

## ✂️ Limpieza

Ahora puedes **borrar** estos archivos obsoletos:
- ❌ `0. n8n cheat sheet guide.txt`
- ❌ `0. n8n tips and tricks.txt`

Todo su contenido está en el skill, pero de forma interactiva.

---

## 📝 Personalización

Para agregar tu propio conocimiento:
1. Abre [.claude/skills/n8n-expert.md](.claude/skills/n8n-expert.md)
2. Agrega tus snippets, tips o casos de uso
3. El agente usará automáticamente el contenido actualizado

---

## 🎓 Próximos Pasos

1. ✅ Prueba el sistema con una pregunta real
2. ✅ Explora los ejemplos en [DEMO.md](DEMO.md)
3. ✅ Lee la documentación completa en [README.md](README.md)
4. ✅ Personaliza el skill con tus propios aprendizajes

---

**¡Listo para empezar! Haz tu primera pregunta al agente.** 🚀
