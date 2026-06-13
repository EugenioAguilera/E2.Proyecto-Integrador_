## Conversation.h
#pragma once

#include <QVector>
#include "Message.h"

class Conversation {
public:
    Conversation();

    void addMessage(const Message& message);

    QVector<Message> messages() const;

    QVector<Message> messagesBySender(Message::Sender sender) const;

    Message lastMessage() const;

    int size() const;

    bool isEmpty() const;

    void clear();

private:
    QVector<Message> messages_;
};

## Conversation.cpp

#include "Conversation.h"

Conversation::Conversation()
{
}

void Conversation::addMessage(const Message& message)
{
    messages_.append(message);
}

QVector<Message> Conversation::messages() const
{
    return messages_;
}

QVector<Message> Conversation::messagesBySender(Message::Sender sender) const
{
    QVector<Message> filteredMessages;

    for (const Message& message : messages_)
    {
        if (message.sender() == sender)
        {
            filteredMessages.append(message);
        }
    }

    return filteredMessages;
}

Message Conversation::lastMessage() const
{
    if (messages_.isEmpty())
    {
        return Message();
    }

    return messages_.last();
}

int Conversation::size() const
{
    return messages_.size();
}

bool Conversation::isEmpty() const
{
    return messages_.isEmpty();
}

void Conversation::clear()
{
    messages_.clear();
}

## ConversationStats.h

#pragma once

#include "Conversation.h"

class ConversationStats {
public:
    static int totalMessages(const Conversation& conversation);

    static int totalUserMessages(const Conversation& conversation);

    static int totalAssistantMessages(const Conversation& conversation);

    static int totalSystemMessages(const Conversation& conversation);

    static int totalErrorMessages(const Conversation& conversation);
};


## ConversationStats.cpp

#include "ConversationStats.h"

int ConversationStats::totalMessages(const Conversation& conversation)
{
    return conversation.size();
}

int ConversationStats::totalUserMessages(const Conversation& conversation)
{
    return conversation.messagesBySender(Message::Sender::User).size();
}

int ConversationStats::totalAssistantMessages(const Conversation& conversation)
{
    return conversation.messagesBySender(Message::Sender::Assistant).size();
}

int ConversationStats::totalSystemMessages(const Conversation& conversation)
{
    return conversation.messagesBySender(Message::Sender::System).size();
}

int ConversationStats::totalErrorMessages(const Conversation& conversation)
{
    return conversation.messagesBySender(Message::Sender::Error).size();
}

