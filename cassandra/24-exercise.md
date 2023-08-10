# Messaging System

**Description:**
We want to create the tables required for a persistent messaging system similar to WhatsApp.

**Features**:

* We need to store all messages
* The user has the ability to create groups
* Access patterns:
  * Send a message (store a single message) in a conversation or group
  * Retrieve all messages from a conversation
  * Retrieve all messages from a group
  * Retrieve my groups and conversations
  * Remove a single message
---

**Create keyspace**
```
CREATE KEYSPACE IF NOT EXISTS whatsapp 
    WITH replication = {'class': 'SimpleStrategy', 'replication_factor' : 1};

DESCRIBE KEYSPACE whatsapp;

USE whatsapp;
```

**Create users table**
```
CREATE TABLE IF NOT EXISTS users(
    id uuid PRIMARY KEY,
    first_name text,
    last_name text
);

INSERT INTO users (id, first_name, last_name) VALUES(uuid(), 'Lucian', 'Neghina');
INSERT INTO users (id, first_name, last_name) VALUES(uuid(), 'Gigi', 'Masinuta');
INSERT INTO users (id, first_name, last_name) VALUES(uuid(), 'Ion', 'Popescu');

SELECT * FROM users;
```

**Create groups table**
```
CREATE TABLE IF NOT EXISTS groups(
    group_id uuid,
    created_at timeuuid,
    admin uuid,
    participants set<uuid>,
    PRIMARY KEY (admin, created_at)
);

// conversation 
INSERT INTO groups (group_id, created_at, admin, participants) 
    VALUES (uuid(), now(), 64a1cfb6-d5e8-4911-992b-4b4fd2407adb, { 451ec601-606b-473d-ba27-a374504749df });

// group
INSERT INTO groups (group_id, created_at, admin, participants) 
    VALUES (uuid(), now(), c7e3959b-c67b-4227-9c7a-6bcca93c9020, { 64a1cfb6-d5e8-4911-992b-4b4fd2407adb, 451ec601-606b-473d-ba27-a374504749df });

SELECT * FROM groups;
```

**Create messages table**
```
CREATE TABLE IF NOT EXISTS messages (
    message_id uuid,
    message_content text,
    sent_at timeuuid,
    group_id uuid,
    sender uuid,
    message_reply uuid,
    PRIMARY KEY (group_id, message_id, sent_at)
);

// send message in conversation
INSERT INTO messages (message_id, message_content, sent_at, group_id, sender)
    VALUES (uuid(), 'Salut Academy!', now(), 4ab1b764-6220-4792-b68d-21c9797f2baf, 64a1cfb6-d5e8-4911-992b-4b4fd2407adb);

// replay to the first message
INSERT INTO messages (message_id, message_content, sent_at, group_id, sender, message_reply)
    VALUES (uuid(), 'Buna!', now(), 4ab1b764-6220-4792-b68d-21c9797f2baf, 451ec601-606b-473d-ba27-a374504749df, 382186c7-65c1-4c48-b48e-04e83f0b3ddf);

SELECT * FROM messages;",        
```
**Q1:** Retrieve all messages from a conversation
```
SELECT  * FROM messages WHERE group_id=4ab1b764-6220-4792-b68d-21c9797f2baf;
```
**Q2:** Retrieve all messages from a group
```
SELECT  * FROM messages WHERE group_id=4ab1b764-6220-4792-b68d-21c9797f2baf;
```
**Q3:** Retrieve my groups and conversations
```
SELECT * FROM groups WHERE admin = 64a1cfb6-d5e8-4911-992b-4b4fd2407adb;
```