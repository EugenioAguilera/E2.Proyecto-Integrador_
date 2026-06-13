# Diagrama de Clases UML

## Justificación del diseño

El sistema se dividió en módulos independientes para separar la interfaz gráfica, la lógica de negocio, la comunicación con IA y los modelos de datos.

- ChatController centraliza la lógica del chat.
- OllamaProvider encapsula la comunicación con Ollama.
- Message representa los mensajes intercambiados.
- Conversation almacena el historial de conversación.
- ConversationStats genera estadísticas sobre el historial.
- Las ventanas y diálogos se separan para mantener una arquitectura modular.

## Diagrama UML

![Diagrama UML](UML_diagrama.png)
