# Whatsapp 

## Functional Requirements 
- User should be able to chat with other users, (That should be via a phone number registered to whatsapp. )
- User should be able to receive the message. 
- User should be able to send acknowledgements. 
- Group chats (groups of 2)
- Send and receive media attachments. 
- What happens the person goes offline . (Users should be able to access messages offline. )
- Video and audio calling. 

Ask interviewers

## Non Functional Requirements
- Low latency calls and messages. (< 500 ms) <- We are going to ask if we have budget to do different things. 
- Guarentee delivery of messages. 
- Determine actual number of messages. 
- Just like whatsapp , I don't want to store the messages unneccessarily . 
  - For privacy , data is a toxic sludge and I don't want to deal with privacy issue. 
- Fault tolerant. 

## Core Entities

Peer1
Peer2
chat (Set up a chat. )
message 
message_status
Clients - This means devices that is associated with a peer. 

## API Interfaces


