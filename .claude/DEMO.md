# Demo: Cómo usar el Skill y Agent de n8n

## Ejemplos de Uso

### Ejemplo 1: Consulta Simple al Skill
```
@n8n-expert ¿Cuál es la estructura básica de datos en n8n?
```

**Respuesta esperada**: Explicación de la estructura de array con objetos json/binary + ejemplos

---

### Ejemplo 2: Configuración de Nodo Específico
```
@n8n-expert muéstrame cómo configurar un nodo HTTP Request para hacer un POST
```

**Respuesta esperada**: JSON completo del nodo httpRequest con método POST + explicaciones

---

### Ejemplo 3: Diseño de Workflow Completo
```
@prompt-n8n-assistant necesito crear un workflow que:
1. Reciba mensajes de Telegram
2. Use un AI Agent para procesarlos
3. Envíe respuestas de vuelta a Telegram
```

**Respuesta esperada**: Diseño completo del workflow con todos los nodos necesarios + JSON + explicaciones

---

### Ejemplo 4: Troubleshooting
```
@prompt-n8n-assistant mi AI Agent está devolviendo las respuestas como string en vez de JSON, ¿cómo lo parseo?
```

**Respuesta esperada**: Explicación del problema + código JavaScript para un Code node que parsea el output

---

### Ejemplo 5: Best Practices
```
@n8n-expert ¿cuáles son las mejores prácticas para manejar errores en n8n?
```

**Respuesta esperada**: Lista de técnicas (continueOnFail, Error Trigger, Stop And Error) + ejemplos

---

### Ejemplo 6: Integración Específica
```
@prompt-n8n-assistant ¿cómo integro Google Calendar para leer eventos?
```

**Respuesta esperada**: Configuración del nodo Google Calendar + parámetros + setup de credenciales

---

### Ejemplo 7: AI Agent con Memoria
```
@prompt-n8n-assistant muéstrame cómo configurar un AI Agent con memoria conversacional
```

**Respuesta esperada**: Configuración de AI Agent + Memory Buffer + explicación de cómo conectarlos

---

### Ejemplo 8: Expresiones Dinámicas
```
@n8n-expert ¿cómo accedo a datos de nodos anteriores usando expresiones?
```

**Respuesta esperada**: Sintaxis de expresiones {{ $json.field }}, {{ $node["Name"].json }} + ejemplos

---

### Ejemplo 9: Data Processing
```
@prompt-n8n-assistant necesito dividir un array en items individuales
```

**Respuesta esperada**: Configuración del nodo Item Lists con operation splitIntoItems + ejemplo

---

### Ejemplo 10: Workflow Scheduling
```
@n8n-expert ¿cómo programo un workflow para que se ejecute automáticamente?
```

**Respuesta esperada**: Configuración de Cron Trigger con ejemplos de horarios + alternativas

---

## Prueba Práctica

Ahora puedes hacer tus propias preguntas. Intenta con:

1. **Preguntas conceptuales**: "¿Qué es un webhook trigger?"
2. **Solicitudes de código**: "Dame el JSON para un nodo Set"
3. **Diseño de workflows**: "Crea un workflow para [tu caso de uso]"
4. **Troubleshooting**: "Tengo este error... ¿cómo lo soluciono?"
5. **Comparaciones**: "¿Cuál es la diferencia entre IF y Switch node?"

---

## Ventajas vs Archivos .txt

| Archivos .txt | Skill + Agent |
|---------------|---------------|
| Estáticos | Interactivos |
| Buscar manualmente | Búsqueda inteligente |
| Leer todo | Respuestas específicas |
| Copiar/pegar código | Código contextualizado |
| Sin explicaciones adicionales | Explicaciones detalladas |
| No actualizable fácilmente | Fácil de actualizar |

---

## Siguiente Paso

Ahora que tienes el skill y el agent configurados, puedes:

1. ✅ **Borrar los archivos .txt antiguos**
2. ✅ **Empezar a usar @n8n-expert y @prompt-n8n-assistant**
3. ✅ **Hacer preguntas específicas a tus necesidades**
4. ✅ **Actualizar el skill con tus propios aprendizajes**

---

**¡Disfruta tu nuevo asistente inteligente de n8n!** 🚀
