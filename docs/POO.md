## Modificadores de acceso
private:
    Sender sender_;
    QString content_;
public:
    QString content() const;

## Sobrecarga

En Message tenemos:

Message();
Message(Sender sender, const QString &content);

Eso es sobrecarga de constructores.

## Herencia y Polimorfismo
La utilizamos en OllamaProvider

## Clases abstractas

En la clase de ollama y en la de Conversation utilizamos el =0
