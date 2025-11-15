# Minecraft Packet ID Reference - Complete Protocol Packet List

**Complete reference guide for Minecraft Java Edition packet IDs across all versions.**

This comprehensive database contains packet IDs for Minecraft protocol packets including clientbound and serverbound packets. Find packet IDs, version ranges, packet fields, and detailed descriptions for all Minecraft versions from 1.8 to latest.

## 📋 Quick Navigation

- [What are Minecraft Packets?](#what-are-minecraft-packets)
- [How to Use This Reference](#how-to-use-this-reference)
- [Packet Lists](#packet-lists)

## What are Minecraft Packets?

Minecraft packets are the fundamental units of communication between the Minecraft client and server. Each packet has a unique ID that varies between Minecraft versions. This reference provides:

- **Packet IDs** in hexadecimal and decimal formats
- **Version ranges** showing when each packet ID is valid
- **Packet fields** with types and descriptions
- **Clientbound packets** - sent from server to client
- **Serverbound packets** - sent from client to server

## How to Use This Reference

1. Use **Ctrl+F** (or Cmd+F on Mac) to search for a specific packet name
2. Check the version range to find the correct packet ID for your Minecraft version
3. Use the packet ID in hexadecimal (0x...) or decimal format
4. Review packet fields to understand the packet structure

**Total packets documented:** 241

---

## Packet Lists

### Table of Contents

- [Clientbound Packets](#clientbound) - 170 packets
- [Serverbound Packets](#serverbound) - 71 packets

---

## Clientbound Packets

**Clientbound packets** are sent from server to client. Total: **170 packets**.

### ADD_ENTITY

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.8 | 0xE | 14 |
| 1.9 - 1.19.3 | 0x0 | 0 |
| 1.19.4 - 1.21.9 | 0x1 | 1 |

**Description:**

Sent by the server to create an entity on the client, normally upon the entity spawning within or entering the player's view range. The local player entity is automatically created by the client, and must not be created explicitly using this packet. Doing so on the vanilla client will have strange consequences.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `VAR_INT` | Entity ID: A unique integer ID mostly used in the protocol to identify the entity. If an entity with the same ID already exists on the client, it is automatically deleted and replaced by the new entity. On the vanilla server entity IDs are globally unique across all dimensions and never reused while the server is running, but not preserved across server restarts. |
| `UUID` | Entity UUID: A unique identifier that is mostly used in persistence and places where the uniqueness matters more. It is possible to create multiple entities with the same UUID on the vanilla client, but a warning will be logged, and functionality dependent on UUIDs may ignore the entity or otherwise misbehave. |
| `VAR_INT` | Type: ID in the minecraft:entity_type registry (see "type" field in Entity metadata#Entities). |
| `DOUBLE` | X |
| `DOUBLE` | Y |
| `DOUBLE` | Z |
| `BYTE` | Pitch |
| `BYTE` | Yaw |
| `BYTE` | Head Yaw: Only used by living entities, where the head of the entity may differ from the general body rotation. |
| `VAR_INT` | Data: Meaning dependent on the value of the Type field, see Object Data for details. |
| `SHORT` | Velocity X: Same units as Set Entity Velocity. |

---

### ADD_EXPERIENCE_ORB

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.8 | 0x11 | 17 |
| 1.9 - 1.19.3 | 0x1 | 1 |
| 1.19.4 - 1.21.2 | 0x2 | 2 |

---

### ADD_GLOBAL_ENTITY

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.8 | 0x2C | 44 |
| 1.9 - 1.15 | 0x2 | 2 |

---

### ADD_MOB

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.8 | 0xF | 15 |
| 1.9 - 1.15 | 0x3 | 3 |
| 1.16 - 1.18 | 0x2 | 2 |

---

### ADD_PAINTING

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.8 | 0x10 | 16 |
| 1.9 - 1.15 | 0x4 | 4 |
| 1.16 - 1.18 | 0x3 | 3 |

---

### ADD_PLAYER

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.8 | 0xC | 12 |
| 1.9 - 1.15 | 0x5 | 5 |
| 1.16 - 1.18 | 0x4 | 4 |
| 1.19 - 1.19.3 | 0x2 | 2 |
| 1.19.4 | 0x3 | 3 |

---

### ADD_VIBRATION_SIGNAL

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.17 - 1.18 | 0x5 | 5 |

---

### ANIMATE

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.8 | 0xB | 11 |
| 1.9 - 1.15 | 0x6 | 6 |
| 1.16 - 1.16.2 | 0x5 | 5 |
| 1.17 - 1.18 | 0x6 | 6 |
| 1.19 - 1.19.3 | 0x3 | 3 |
| 1.19.4 - 1.20.1 | 0x4 | 4 |
| 1.20.2 - 1.21.4 | 0x3 | 3 |
| 1.21.5 - 1.21.9 | 0x2 | 2 |

**Description:**

Sent whenever an entity should change animation.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `VAR_INT` | Entity ID: Player ID. |
| `BYTE` | Animation: Animation ID (see below). |

---

### AWARD_STATS

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.8 | 0x37 | 55 |
| 1.9 - 1.15 | 0x7 | 7 |
| 1.16 - 1.16.2 | 0x6 | 6 |
| 1.17 - 1.18 | 0x7 | 7 |
| 1.19 - 1.19.3 | 0x4 | 4 |
| 1.19.4 - 1.20.1 | 0x5 | 5 |
| 1.20.2 - 1.21.4 | 0x4 | 4 |
| 1.21.5 - 1.21.9 | 0x3 | 3 |

**Description:**

Sent as a response to Client Status (id 1). Will only send the changed values if previously requested.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `CATEGORY_ID` | Statistics: Prefixed Array |
| `VAR_INT` | Statistic ID: See below. |
| `VAR_INT` | Value: The amount to set it to. |

---

### BLOCK_BREAK_ACK

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.14.4 | 0x5C | 92 |
| 1.15 | 0x8 | 8 |
| 1.16 - 1.16.2 | 0x7 | 7 |
| 1.17 - 1.18 | 0x8 | 8 |

---

### BLOCK_CHANGED_ACK

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.19 - 1.19.3 | 0x5 | 5 |
| 1.19.4 - 1.20.1 | 0x6 | 6 |
| 1.20.2 - 1.21.4 | 0x5 | 5 |
| 1.21.5 - 1.21.9 | 0x4 | 4 |

**Description:**

Acknowledges a user-initiated block change. After receiving this packet, the client will display the block state sent by the server instead of the one predicted by the client.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `VAR_INT` | Sequence ID: Represents the sequence to acknowledge; this is used for properly syncing block changes to the client after interactions. |

---

### BLOCK_DESTRUCTION

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.8 | 0x25 | 37 |
| 1.9 - 1.14.4 | 0x8 | 8 |
| 1.15 | 0x9 | 9 |
| 1.16 - 1.16.2 | 0x8 | 8 |
| 1.17 - 1.18 | 0x9 | 9 |
| 1.19 - 1.19.3 | 0x6 | 6 |
| 1.19.4 - 1.20.1 | 0x7 | 7 |
| 1.20.2 - 1.21.4 | 0x6 | 6 |
| 1.21.5 - 1.21.9 | 0x5 | 5 |

**Description:**

0–9 are the displayable destroy stages and each other number means that there is no animation on this coordinate. Block break animations can still be applied on air; the animation will remain visible, although there is no block being broken.  However, if this is applied to a transparent block, odd graphical effects may happen, including water losing its transparency.  (An effect similar to this can be seen in normal gameplay when breaking ice blocks) If you need to display several break animations at the same time, you have to give each of them a unique Entity ID. The entity ID does not need to correspond to an actual entity on the client. It is valid to use a randomly generated number. When removing the break animation, you must use the ID of the entity that set it.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `VAR_INT` | Entity ID: The ID of the entity breaking the block. |
| `POSITION` | Location: Block Position. |
| `BYTE` | Destroy Stage: 0–9 to set it, any other value to remove it. |

---

### BLOCK_ENTITY_DATA

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.8 | 0x35 | 53 |
| 1.9 - 1.14.4 | 0x9 | 9 |
| 1.15 | 0xA | 10 |
| 1.16 - 1.16.2 | 0x9 | 9 |
| 1.17 - 1.18 | 0xA | 10 |
| 1.19 - 1.19.3 | 0x7 | 7 |
| 1.19.4 - 1.20.1 | 0x8 | 8 |
| 1.20.2 - 1.21.4 | 0x7 | 7 |
| 1.21.5 - 1.21.9 | 0x6 | 6 |

**Description:**

Sets the block entity associated with the block at the given location.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `POSITION` | Location |
| `VAR_INT` | Type: ID in the minecraft:block_entity_type registry |
| `NBT` | NBT Data: Data to set. |
| `POSITION` | Location |
| `VAR_INT` | Type: ID in the minecraft:block_entity_type registry |
| `NBT` | NBT Data: Data to set. |

---

### BLOCK_EVENT

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.8 | 0x24 | 36 |
| 1.9 - 1.14.4 | 0xA | 10 |
| 1.15 | 0xB | 11 |
| 1.16 - 1.16.2 | 0xA | 10 |
| 1.17 - 1.18 | 0xB | 11 |
| 1.19 - 1.19.3 | 0x8 | 8 |
| 1.19.4 - 1.20.1 | 0x9 | 9 |
| 1.20.2 - 1.21.4 | 0x8 | 8 |
| 1.21.5 - 1.21.9 | 0x7 | 7 |

**Description:**

This packet is used for a number of actions and animations performed by blocks, usually non-persistent.  The client ignores the provided block type and instead uses the block state in their world. See Block Actions for a list of values.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `POSITION` | Location: Block coordinates. |
| `BYTE` | Action ID (Byte 1): Varies depending on block — see Block Actions. |
| `BYTE` | Action Parameter (Byte 2): Varies depending on block — see Block Actions. |
| `VAR_INT` | Block Type: ID in the minecraft:block registry. This value is unused by the vanilla client, as it will infer the type of block based on the given position. |

---

### BLOCK_UPDATE

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.8 | 0x23 | 35 |
| 1.9 - 1.14.4 | 0xB | 11 |
| 1.15 | 0xC | 12 |
| 1.16 - 1.16.2 | 0xB | 11 |
| 1.17 - 1.18 | 0xC | 12 |
| 1.19 - 1.19.3 | 0x9 | 9 |
| 1.19.4 - 1.20.1 | 0xA | 10 |
| 1.20.2 - 1.21.4 | 0x9 | 9 |
| 1.21.5 - 1.21.9 | 0x8 | 8 |

**Description:**

Fired whenever a block is changed within the render distance.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `POSITION` | Location: Block Coordinates. |
| `VAR_INT` | Block ID: The new block state ID for the block as given in the block state registry. |
| `POSITION` | Location: Block Coordinates. |
| `VAR_INT` | Block ID: The new block state ID for the block as given in the block state registry. |

---

### BOSS_EVENT

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.9 - 1.14.4 | 0xC | 12 |
| 1.15 | 0xD | 13 |
| 1.16 - 1.16.2 | 0xC | 12 |
| 1.17 - 1.18 | 0xD | 13 |
| 1.19 - 1.19.3 | 0xA | 10 |
| 1.19.4 - 1.20.1 | 0xB | 11 |
| 1.20.2 - 1.21.4 | 0xA | 10 |
| 1.21.5 - 1.21.9 | 0x9 | 9 |

**Packet Fields:**

| Type | Description |
| --- | --- |
| `UUID` | UUID: Unique ID for this bar. |
| `VAR_INT` | Action: Determines the layout of the remaining packet. |
| `TEXT_COMPONENT` | Title |
| `FLOAT` | Health: From 0 to 1. Values greater than 1 do not crash a vanilla client, and start rendering part of a second health bar at around 1.5. |
| `VAR_INT` | Color: Color ID (see below). |
| `VAR_INT` | Division: Type of division (see below). |
| `BYTE` | Flags: Bit mask. 0x01: should darken sky, 0x02: is dragon bar (used to play end music), 0x04: create fog (previously was also controlled by 0x02). |
| `NO_FIELDS` | no fields: Removes this boss bar. |
| `FLOAT` | Health: as above |
| `TEXT_COMPONENT` | Title |
| `VAR_INT` | Color: Color ID (see below). |
| `VAR_INT` | Dividers: as above |
| `BYTE` | Flags: as above |

---

### BUNDLE_DELIMITER

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.19.4 - 1.21.9 | 0x0 | 0 |

**Description:**

The delimiter for a bundle of packets. When received, the client should store every subsequent packet it receives and wait until another delimiter is received. Once that happens, the client is guaranteed to process every packet in the bundle on the same tick, and the client should stop storing packets. As of 1.20.6, the vanilla server only uses this to ensure Spawn Entity and associated packets used to configure the entity happen on the same tick. Each entity gets a separate bundle. The vanilla client doesn't allow more than 4096 packets in the same bundle.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `CLIENT` | Play: no fields |
| `CLIENT` | Play: no fields |

---

### CHANGE_DIFFICULTY

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.8 | 0x41 | 65 |
| 1.9 - 1.14.4 | 0xD | 13 |
| 1.15 | 0xE | 14 |
| 1.16 - 1.16.2 | 0xD | 13 |
| 1.17 - 1.18 | 0xE | 14 |
| 1.19 - 1.19.3 | 0xB | 11 |
| 1.19.4 - 1.20.1 | 0xC | 12 |
| 1.20.2 - 1.21.4 | 0xB | 11 |
| 1.21.5 - 1.21.9 | 0xA | 10 |

**Description:**

Changes the difficulty setting in the client's option menu

**Packet Fields:**

| Type | Description |
| --- | --- |
| `BYTE` | Difficulty: 0: peaceful, 1: easy, 2: normal, 3: hard. |
| `BOOLEAN` | Difficulty locked? |
| `BYTE` | Difficulty: 0: peaceful, 1: easy, 2: normal, 3: hard. |
| `BOOLEAN` | Difficulty locked? |

---

### CHAT

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.8 | 0x2 | 2 |
| 1.9 - 1.12.1 | 0xF | 15 |
| 1.13 - 1.14.4 | 0xE | 14 |
| 1.15 | 0xF | 15 |
| 1.16 - 1.16.2 | 0xE | 14 |
| 1.17 - 1.18 | 0xF | 15 |

---

### CHAT_PREVIEW

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.19 - 1.19.1 | 0xC | 12 |

---

### CHUNKS_BIOMES

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.19.4 - 1.20.1 | 0xD | 13 |
| 1.20.2 - 1.21.4 | 0xE | 14 |
| 1.21.5 - 1.21.9 | 0xD | 13 |

**Packet Fields:**

| Type | Description |
| --- | --- |
| `CHUNK_Z` | Chunk biome data: Prefixed Array |
| `INT` | Chunk X: Chunk coordinate (block coordinate divided by 16, rounded down) |
| `BYTE` | Data: Chunk data structure, with sections containing only the Biomes field |

---

### CHUNK_BATCH_FINISHED

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.20.2 - 1.21.4 | 0xC | 12 |
| 1.21.5 - 1.21.9 | 0xB | 11 |

**Description:**

Marks the end of a chunk batch. The vanilla client marks the time it receives this packet and calculates the elapsed duration since the beginning of the chunk batch. The server uses this duration and the batch size received in this packet to estimate the number of milliseconds elapsed per chunk received. This value is then used to calculate the desired number of chunks per tick through the formula 25 / millisPerChunk, which is reported to the server through Chunk Batch Received. This likely uses 25 instead of the normal tick duration of 50 so chunk processing will only use half of the client's and network's bandwidth. The vanilla client uses the samples from the latest 15 batches to estimate the milliseconds per chunk number.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `VAR_INT` | Batch size: Number of chunks. |
| `VAR_INT` | Batch size: Number of chunks. |

---

### CHUNK_BATCH_START

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.20.2 - 1.21.4 | 0xD | 13 |
| 1.21.5 - 1.21.9 | 0xC | 12 |

**Description:**

Marks the start of a chunk batch. The vanilla client marks and stores the time it receives this packet.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `CLIENT` | Play: no fields |
| `CLIENT` | Play: no fields |

---

### CHUNK_BLOCKS_UPDATE

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.8 | 0x22 | 34 |
| 1.9 - 1.12.1 | 0x10 | 16 |
| 1.13 - 1.14.4 | 0xF | 15 |
| 1.15 | 0x10 | 16 |
| 1.16 | 0xF | 15 |

---

### CLEAR_DIALOG

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.21.6 - 1.21.8 | 0x84 | 132 |
| 1.21.9 | 0x89 | 137 |

**Description:**

If we're currently in a dialog screen, then this removes the current screen and switches back to the previous one.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `CLIENT` | Configuration: no fields |
| `CLIENT` | Play: no fields |

---

### CLEAR_TITLES

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.17 - 1.18 | 0x10 | 16 |
| 1.19 - 1.19.2 | 0xD | 13 |
| 1.19.3 | 0xC | 12 |
| 1.19.4 - 1.20.1 | 0xE | 14 |
| 1.20.2 - 1.21.4 | 0xF | 15 |
| 1.21.5 - 1.21.9 | 0xE | 14 |

**Description:**

Clear the client's current title information, with the option to also reset it.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `BOOLEAN` | Reset |
| `BOOLEAN` | Reset |

---

### COMMANDS

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.13 - 1.14.4 | 0x11 | 17 |
| 1.15 | 0x12 | 18 |
| 1.16 - 1.16.1 | 0x11 | 17 |
| 1.16.2 | 0x10 | 16 |
| 1.17 - 1.18 | 0x12 | 18 |
| 1.19 - 1.19.2 | 0xF | 15 |
| 1.19.3 | 0xE | 14 |
| 1.19.4 - 1.20.1 | 0x10 | 16 |
| 1.20.2 - 1.21.4 | 0x11 | 17 |
| 1.21.5 - 1.21.9 | 0x10 | 16 |

**Description:**

Lists all of the commands on the server, and how they are parsed. This is a directed graph, with one root node.  Each redirect or child node must refer only to nodes that have already been declared.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `ARRAY` | Nodes: An array of nodes. |
| `VAR_INT` | Root index: Index of the root node in the previous array. |
| `ARRAY` | Nodes: An array of nodes. |
| `VAR_INT` | Root index: Index of the root node in the previous array. |

---

### COMMAND_SUGGESTIONS

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.8 | 0x3A | 58 |
| 1.9 - 1.12.1 | 0xE | 14 |
| 1.13 - 1.14.4 | 0x10 | 16 |
| 1.15 | 0x11 | 17 |
| 1.16 - 1.16.1 | 0x10 | 16 |
| 1.16.2 | 0xF | 15 |
| 1.17 - 1.18 | 0x11 | 17 |
| 1.19 - 1.19.2 | 0xE | 14 |
| 1.19.3 | 0xD | 13 |
| 1.19.4 - 1.20.1 | 0xF | 15 |
| 1.20.2 - 1.21.4 | 0x10 | 16 |
| 1.21.5 - 1.21.9 | 0xF | 15 |

**Description:**

The server responds with a list of auto-completions of the last word sent to it. In the case of regular chat, this is a player username. Command names and parameters are also supported. The client sorts these alphabetically before listing them.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `VAR_INT` | ID: Transaction ID. |
| `VAR_INT` | Start: Start of the text to replace. |
| `VAR_INT` | Length: Length of the text to replace. |
| `STRING` | Prefixed Array: One eligible value to insert, note that each command is sent separately instead of in a single string, hence the need for Count. |
| `PREFIXED_OPTIONAL_TEXT_COMPONENT` | Tooltip: Tooltip to display. |

---

### CONTAINER_ACK

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.8 | 0x32 | 50 |
| 1.9 - 1.12.1 | 0x11 | 17 |
| 1.13 - 1.14.4 | 0x12 | 18 |
| 1.15 | 0x13 | 19 |
| 1.16 - 1.16.1 | 0x12 | 18 |
| 1.16.2 | 0x11 | 17 |

---

### CONTAINER_CLOSE

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.8 | 0x2E | 46 |
| 1.9 - 1.12.1 | 0x12 | 18 |
| 1.13 - 1.14.4 | 0x13 | 19 |
| 1.15 | 0x14 | 20 |
| 1.16 - 1.16.1 | 0x13 | 19 |
| 1.16.2 | 0x12 | 18 |
| 1.17 - 1.18 | 0x13 | 19 |
| 1.19 - 1.19.2 | 0x10 | 16 |
| 1.19.3 | 0xF | 15 |
| 1.19.4 - 1.20.1 | 0x11 | 17 |
| 1.20.2 - 1.21.4 | 0x12 | 18 |
| 1.21.5 - 1.21.9 | 0x11 | 17 |

**Description:**

This packet is sent from the server to the client when a window is forcibly closed, such as when a chest is destroyed while it's open. The vanilla client disregards the provided window ID and closes any active window.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `VAR_INT` | Window ID: This is the ID of the window that was closed. 0 for inventory. |

---

### CONTAINER_SET_CONTENT

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.8 | 0x30 | 48 |
| 1.9 - 1.12.1 | 0x14 | 20 |
| 1.13 | 0x15 | 21 |
| 1.14 - 1.14.4 | 0x14 | 20 |
| 1.15 | 0x15 | 21 |
| 1.16 - 1.16.1 | 0x14 | 20 |
| 1.16.2 | 0x13 | 19 |
| 1.17 - 1.18 | 0x14 | 20 |
| 1.19 - 1.19.2 | 0x11 | 17 |
| 1.19.3 | 0x10 | 16 |
| 1.19.4 - 1.20.1 | 0x12 | 18 |
| 1.20.2 - 1.21.4 | 0x13 | 19 |
| 1.21.5 - 1.21.9 | 0x12 | 18 |

**Description:**

Replaces the contents of a container window. Sent by the server upon initialization of a container window or the player's inventory, and in response to state ID mismatches (see #Click Container).

**Packet Fields:**

| Type | Description |
| --- | --- |
| `VAR_INT` | Window ID: The ID of window which items are being sent for. 0 for player inventory. The client ignores any packets targeting a Window ID other than the current one. However, an exception is made for the player inventory, which may be targeted at any time. (The vanilla server does not appear to utilize this special case.) |
| `VAR_INT` | State ID: A server-managed sequence number used to avoid desynchronization; see #Click Container. |
| `SLOT` | Carried Item: Item being dragged with the mouse. |

---

### CONTAINER_SET_DATA

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.8 | 0x31 | 49 |
| 1.9 - 1.12.1 | 0x15 | 21 |
| 1.13 | 0x16 | 22 |
| 1.14 - 1.14.4 | 0x15 | 21 |
| 1.15 | 0x16 | 22 |
| 1.16 - 1.16.1 | 0x15 | 21 |
| 1.16.2 | 0x14 | 20 |
| 1.17 - 1.18 | 0x15 | 21 |
| 1.19 - 1.19.2 | 0x12 | 18 |
| 1.19.3 | 0x11 | 17 |
| 1.19.4 - 1.20.1 | 0x13 | 19 |
| 1.20.2 - 1.21.4 | 0x14 | 20 |
| 1.21.5 - 1.21.9 | 0x13 | 19 |

**Description:**

This packet is used to inform the client that part of a GUI window should be updated.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `VAR_INT` | Window ID |
| `SHORT` | Property: The property to be updated, see below. |
| `SHORT` | Value: The new value for the property, see below. |

---

### CONTAINER_SET_SLOT

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.8 | 0x2F | 47 |
| 1.9 - 1.12.1 | 0x16 | 22 |
| 1.13 | 0x17 | 23 |
| 1.14 - 1.14.4 | 0x16 | 22 |
| 1.15 | 0x17 | 23 |
| 1.16 - 1.16.1 | 0x16 | 22 |
| 1.16.2 | 0x15 | 21 |
| 1.17 - 1.18 | 0x16 | 22 |
| 1.19 - 1.19.2 | 0x13 | 19 |
| 1.19.3 | 0x12 | 18 |
| 1.19.4 - 1.20.1 | 0x14 | 20 |
| 1.20.2 - 1.21.4 | 0x15 | 21 |
| 1.21.5 - 1.21.9 | 0x14 | 20 |

**Description:**

Sent by the server when an item in a slot (in a window) is added/removed.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `VAR_INT` | Window ID: The window that is being updated. 0 for player inventory. The client ignores any packets targeting a Window ID other than the current one; see below for exceptions. |
| `VAR_INT` | State ID: A server-managed sequence number used to avoid desynchronization; see #Click Container. |
| `SHORT` | Slot: The slot that should be updated. |
| `SLOT` | Slot Data |

---

### COOKIE_REQUEST

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.20.5 - 1.21.4 | 0x16 | 22 |
| 1.21.5 - 1.21.9 | 0x15 | 21 |

**Description:**

Requests a cookie that was previously stored.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `STRING` | Key: The identifier of the cookie. |
| `STRING` | Key: The identifier of the cookie. |
| `STRING` | Key: The identifier of the cookie. |

---

### COOLDOWN

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.9 - 1.12.1 | 0x17 | 23 |
| 1.13 | 0x18 | 24 |
| 1.14 - 1.14.4 | 0x17 | 23 |
| 1.15 | 0x18 | 24 |
| 1.16 - 1.16.1 | 0x17 | 23 |
| 1.16.2 | 0x16 | 22 |
| 1.17 - 1.18 | 0x17 | 23 |
| 1.19 - 1.19.2 | 0x14 | 20 |
| 1.19.3 | 0x13 | 19 |
| 1.19.4 - 1.20.1 | 0x15 | 21 |
| 1.20.2 - 1.20.4 | 0x16 | 22 |
| 1.20.5 - 1.21.4 | 0x17 | 23 |
| 1.21.5 - 1.21.9 | 0x16 | 22 |

**Description:**

Applies a cooldown period to all items with the given type.  Used by the vanilla server with enderpearls.  This packet should be sent when the cooldown starts and also when the cooldown ends (to compensate for lag), although the client will end the cooldown automatically. Can be applied to any item, note that interactions still get sent to the server with the item, but the client does not play the animation nor attempt to predict results (i.e, block placing).

**Packet Fields:**

| Type | Description |
| --- | --- |
| `STRING` | Cooldown Group: Identifier of the item (minecraft:stone) or the cooldown group ("use_cooldown" item component) |
| `VAR_INT` | Cooldown Ticks: Number of ticks to apply a cooldown for, or 0 to clear the cooldown. |

---

### CUSTOM_CHAT_COMPLETIONS

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.19.1 - 1.19.2 | 0x15 | 21 |
| 1.19.3 | 0x14 | 20 |
| 1.19.4 - 1.20.1 | 0x16 | 22 |
| 1.20.2 - 1.20.4 | 0x17 | 23 |
| 1.20.5 - 1.21.4 | 0x18 | 24 |
| 1.21.5 - 1.21.9 | 0x17 | 23 |

**Description:**

Unused by the vanilla server. Likely provided for custom servers to send chat message completions to clients.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `VAR_INT` | Action: 0: Add, 1: Remove, 2: Set |
| `STRING` | Entries |

---

### CUSTOM_PAYLOAD

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.8 | 0x3F | 63 |
| 1.9 - 1.12.1 | 0x18 | 24 |
| 1.13 | 0x19 | 25 |
| 1.14 - 1.14.4 | 0x18 | 24 |
| 1.15 | 0x19 | 25 |
| 1.16 - 1.16.1 | 0x18 | 24 |
| 1.16.2 | 0x17 | 23 |
| 1.17 - 1.18 | 0x18 | 24 |
| 1.19 - 1.19.0 | 0x15 | 21 |
| 1.19.1 - 1.19.2 | 0x16 | 22 |
| 1.19.3 | 0x15 | 21 |
| 1.19.4 - 1.20.1 | 0x17 | 23 |
| 1.20.2 - 1.20.4 | 0x18 | 24 |
| 1.20.5 - 1.21.4 | 0x19 | 25 |
| 1.21.5 - 1.21.9 | 0x18 | 24 |

**Description:**

Mods and plugins can use this to send their data. Minecraft itself uses several plugin channels. These internal channels are in the minecraft namespace. More information on how it works on Dinnerbone's blog. More documentation about internal and popular registered channels are here.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `STRING` | Channel: Name of the plugin channel used to send the data. |
| `BYTE` | Data: Any data. The length of this array must be inferred from the packet length. |
| `STRING` | Channel: Name of the plugin channel used to send the data. |
| `BYTE` | Data: Any data. The length of this array must be inferred from the packet length. |

---

### CUSTOM_REPORT_DETAILS

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.21 - 1.21.1 | 0x7A | 122 |
| 1.21.2 - 1.21.8 | 0x81 | 129 |
| 1.21.9 | 0x86 | 134 |

**Description:**

Contains a list of key-value text entries that are included in any crash or disconnection report generated during connection to the server.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `TITLE` | Details: Prefixed Array (32) |
| `STRING` | Description |
| `TITLE` | Details: Prefixed Array (32) |
| `STRING` | Description |
| `TITLE` | Details: Prefixed Array (32) |
| `STRING` | Description |

---

### CUSTOM_SOUND

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.8 | 0x29 | 41 |
| 1.9 - 1.12.1 | 0x19 | 25 |
| 1.13 | 0x1A | 26 |
| 1.14 - 1.14.4 | 0x19 | 25 |
| 1.15 | 0x1A | 26 |
| 1.16 - 1.16.1 | 0x19 | 25 |
| 1.16.2 | 0x18 | 24 |
| 1.17 - 1.18 | 0x19 | 25 |
| 1.19 - 1.19.0 | 0x16 | 22 |
| 1.19.1 | 0x17 | 23 |

---

### DAMAGE_EVENT

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.19.4 - 1.20.1 | 0x18 | 24 |
| 1.20.2 - 1.20.4 | 0x19 | 25 |
| 1.20.5 - 1.21.4 | 0x1A | 26 |
| 1.21.5 - 1.21.9 | 0x19 | 25 |

**Packet Fields:**

| Type | Description |
| --- | --- |
| `PLAY` | protocol:0x19resource:damage_event: Client |
| `VAR_INT` | Entity ID: The ID of the entity taking damage |
| `VAR_INT` | Source Type ID: The type of damage in the minecraft:damage_type registry, defined by the Registry Data packet. |
| `VAR_INT` | Source Cause ID: The ID + 1 of the entity responsible for the damage, if present. If not present, the value is 0 |
| `VAR_INT` | Source Direct ID: The ID + 1 of the entity that directly dealt the damage, if present. If not present, the value is 0. If this field is present:
and damage was dealt indirectly, such as by the use of a projectile, this field will contain the ID of such projectile;
and damage was dealt directly, such as by manually attacking, this field will contain the same value as Source Cause ID. |
| `DOUBLE` | Prefixed Optional: The vanilla server sends the Source Position when the damage was dealt by the /damage command and a position was specified |
| `PLAY` | protocol:0x19resource:damage_event: Client |
| `VAR_INT` | Entity ID: The ID of the entity taking damage |
| `VAR_INT` | Source Type ID: The type of damage in the minecraft:damage_type registry, defined by the Registry Data packet. |
| `VAR_INT` | Source Cause ID: The ID + 1 of the entity responsible for the damage, if present. If not present, the value is 0 |
| `VAR_INT` | Source Direct ID: The ID + 1 of the entity that directly dealt the damage, if present. If not present, the value is 0. If this field is present:
and damage was dealt indirectly, such as by the use of a projectile, this field will contain the ID of such projectile;
and damage was dealt directly, such as by manually attacking, this field will contain the same value as Source Cause ID. |
| `DOUBLE` | Prefixed Optional: The vanilla server sends the Source Position when the damage was dealt by the /damage command and a position was specified |

---

### DEBUG_BLOCK_VALUE

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.21.9 | 0x1A | 26 |

---

### DEBUG_CHUNK_VALUE

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.21.9 | 0x1B | 27 |

---

### DEBUG_ENTITY_VALUE

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.21.9 | 0x1C | 28 |

---

### DEBUG_EVENT

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.21.9 | 0x1D | 29 |

---

### DEBUG_SAMPLE

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.20.5 - 1.21.4 | 0x1B | 27 |
| 1.21.5 - 1.21.8 | 0x1A | 26 |
| 1.21.9 | 0x1E | 30 |

**Description:**

Sample data that is sent periodically after the client has subscribed with Debug Sample Subscription. The vanilla server only sends debug samples to players who are server operators.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `LONG` | Sample: Array of type-dependent samples. |
| `VAR_INT` | Sample Type: See below. |
| `LONG` | Sample: Array of type-dependent samples. |
| `VAR_INT` | Sample Type: See below. |

---

### DELETE_CHAT

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.19.1 - 1.19.2 | 0x18 | 24 |
| 1.19.3 | 0x16 | 22 |
| 1.19.4 - 1.20.1 | 0x19 | 25 |
| 1.20.2 - 1.20.4 | 0x1A | 26 |
| 1.20.5 - 1.21.4 | 0x1C | 28 |
| 1.21.5 - 1.21.8 | 0x1B | 27 |
| 1.21.9 | 0x1F | 31 |

**Description:**

Removes a message from the client's chat. This only works for messages with signatures; system messages cannot be deleted with this packet.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `VAR_INT` | Message ID: The message ID + 1, used for validating message signature. The next field is present only when value of this field is equal to 0. |
| `BYTE` | Signature: The previous message's signature. Always 256 bytes and not length-prefixed. |

---

### DISCONNECT

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.8 | 0x40 | 64 |
| 1.9 - 1.12.1 | 0x1A | 26 |
| 1.13 | 0x1B | 27 |
| 1.14 - 1.14.4 | 0x1A | 26 |
| 1.15 | 0x1B | 27 |
| 1.16 - 1.16.1 | 0x1A | 26 |
| 1.16.2 | 0x19 | 25 |
| 1.17 - 1.18 | 0x1A | 26 |
| 1.19 - 1.19.0 | 0x17 | 23 |
| 1.19.1 - 1.19.2 | 0x19 | 25 |
| 1.19.3 | 0x17 | 23 |
| 1.19.4 - 1.20.1 | 0x1A | 26 |
| 1.20.2 - 1.20.4 | 0x1B | 27 |
| 1.20.5 - 1.21.4 | 0x1D | 29 |
| 1.21.5 - 1.21.8 | 0x1C | 28 |
| 1.21.9 | 0x20 | 32 |

**Description:**

Sent by the server before it disconnects a client. The client assumes that the server has already closed the connection by the time the packet arrives.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `TEXT_COMPONENT` | Reason: The reason why the player was disconnected. |
| `TEXT_COMPONENT` | Reason: Displayed to the client when the connection terminates. |

---

### DISGUISED_CHAT

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.19.3 | 0x18 | 24 |
| 1.19.4 - 1.20.1 | 0x1B | 27 |
| 1.20.2 - 1.20.4 | 0x1C | 28 |
| 1.20.5 - 1.21.4 | 0x1E | 30 |
| 1.21.5 - 1.21.8 | 0x1D | 29 |
| 1.21.9 | 0x21 | 33 |

**Description:**

Sends the client a chat message, but without any message signing information. The vanilla server uses this packet when the console is communicating with players through commands, such as /say, /tell, /me, among others. This is used as the sender parameter when formatting the message on the client. This is used as the target parameter when formatting the message on the client.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `TEXT_COMPONENT` | Message: This is used as the content parameter when formatting the message on the client. |
| `COMPONENT` | Chat Type: Either the type of chat in the minecraft:chat_type registry, defined by the Registry Data packet, or an inline definition. |
| `TEXT_COMPONENT` | Sender Name: The name of the one sending the message, usually the sender's display name.
This is used as the sender parameter when formatting the message on the client. |
| `PREFIXED_OPTIONAL_TEXT_COMPONENT` | Target Name: The name of the one receiving the message, usually the receiver's display name.
This is used as the target parameter when formatting the message on the client. |

---

### ENTITY_EVENT

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.8 | 0x1A | 26 |
| 1.9 - 1.12.1 | 0x1B | 27 |
| 1.13 | 0x1C | 28 |
| 1.14 - 1.14.4 | 0x1B | 27 |
| 1.15 | 0x1C | 28 |
| 1.16 - 1.16.1 | 0x1B | 27 |
| 1.16.2 | 0x1A | 26 |
| 1.17 - 1.18 | 0x1B | 27 |
| 1.19 - 1.19.0 | 0x18 | 24 |
| 1.19.1 - 1.19.2 | 0x1A | 26 |
| 1.19.3 | 0x19 | 25 |
| 1.19.4 - 1.20.1 | 0x1C | 28 |
| 1.20.2 - 1.20.4 | 0x1D | 29 |
| 1.20.5 - 1.21.4 | 0x1F | 31 |
| 1.21.5 - 1.21.8 | 0x1E | 30 |
| 1.21.9 | 0x22 | 34 |

**Description:**

Entity statuses generally trigger an animation for an entity.  The available statuses vary by the entity's type (and are available to subclasses of that type as well).

**Packet Fields:**

| Type | Description |
| --- | --- |
| `INT` | Entity ID |
| `BYTE` | Entity Status: See Entity statuses for a list of which statuses are valid for each type of entity. |
| `INT` | Entity ID |
| `BYTE` | Entity Status: See Entity statuses for a list of which statuses are valid for each type of entity. |

---

### ENTITY_POSITION_SYNC

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.21.2 - 1.21.4 | 0x20 | 32 |
| 1.21.5 - 1.21.8 | 0x1F | 31 |
| 1.21.9 | 0x23 | 35 |

**Description:**

This packet is sent by the server when an entity moves more than 8 blocks.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `VAR_INT` | Entity ID |
| `DOUBLE` | X |
| `DOUBLE` | Y |
| `DOUBLE` | Z |
| `DOUBLE` | Velocity X |
| `DOUBLE` | Velocity Y |
| `DOUBLE` | Velocity Z |
| `FLOAT` | Yaw: Rotation on the X axis, in degrees. |
| `FLOAT` | Pitch: Rotation on the Y axis, in degrees. |
| `BOOLEAN` | On Ground |

---

### EXPLODE

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.8 | 0x27 | 39 |
| 1.9 - 1.12.1 | 0x1C | 28 |
| 1.13 | 0x1E | 30 |
| 1.14 - 1.14.4 | 0x1C | 28 |
| 1.15 | 0x1D | 29 |
| 1.16 - 1.16.1 | 0x1C | 28 |
| 1.16.2 | 0x1B | 27 |
| 1.17 - 1.18 | 0x1C | 28 |
| 1.19 - 1.19.0 | 0x19 | 25 |
| 1.19.1 - 1.19.2 | 0x1B | 27 |
| 1.19.3 | 0x1A | 26 |
| 1.19.4 - 1.20.1 | 0x1D | 29 |
| 1.20.2 - 1.20.4 | 0x1E | 30 |
| 1.20.5 - 1.21.1 | 0x20 | 32 |
| 1.21.2 - 1.21.4 | 0x21 | 33 |
| 1.21.5 - 1.21.8 | 0x20 | 32 |
| 1.21.9 | 0x24 | 36 |

**Description:**

Sent when an explosion occurs (creepers, TNT, and ghast fireballs).

**Packet Fields:**

| Type | Description |
| --- | --- |
| `DOUBLE` | X |
| `DOUBLE` | Y |
| `DOUBLE` | Z |
| `DOUBLE` | Prefixed Optional: Velocity difference of the player being pushed by the explosion. |
| `VAR_INT` | Explosion Particle ID: ID in the minecraft:particle_type registry. |
| `VARIES` | Explosion Particle Data: Particle data as specified in Particles. |
| `ID_OR_SOUND_EVENT` | Explosion Sound: ID in the minecraft:sound_event registry, or an inline definition. |

---

### FORGET_LEVEL_CHUNK

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.9 - 1.12.1 | 0x1D | 29 |
| 1.13 | 0x1F | 31 |
| 1.14 - 1.14.4 | 0x1D | 29 |
| 1.15 | 0x1E | 30 |
| 1.16 - 1.16.1 | 0x1D | 29 |
| 1.16.2 | 0x1C | 28 |
| 1.17 - 1.18 | 0x1D | 29 |
| 1.19 - 1.19.0 | 0x1A | 26 |
| 1.19.1 - 1.19.2 | 0x1C | 28 |
| 1.19.3 | 0x1B | 27 |
| 1.19.4 - 1.20.1 | 0x1E | 30 |
| 1.20.2 - 1.20.4 | 0x1F | 31 |
| 1.20.5 - 1.21.1 | 0x21 | 33 |
| 1.21.2 - 1.21.4 | 0x22 | 34 |
| 1.21.5 - 1.21.8 | 0x21 | 33 |
| 1.21.9 | 0x25 | 37 |

**Description:**

Tells the client to unload a chunk column.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `INT` | Chunk Z: Block coordinate divided by 16, rounded down. |
| `INT` | Chunk X: Block coordinate divided by 16, rounded down. |

---

### GAME_EVENT

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.8 | 0x2B | 43 |
| 1.9 - 1.12.1 | 0x1E | 30 |
| 1.13 | 0x20 | 32 |
| 1.14 - 1.14.4 | 0x1E | 30 |
| 1.15 | 0x1F | 31 |
| 1.16 - 1.16.1 | 0x1E | 30 |
| 1.16.2 | 0x1D | 29 |
| 1.17 - 1.18 | 0x1E | 30 |
| 1.19 - 1.19.0 | 0x1B | 27 |
| 1.19.1 - 1.19.2 | 0x1D | 29 |
| 1.19.3 | 0x1C | 28 |
| 1.19.4 - 1.20.1 | 0x1F | 31 |
| 1.20.2 - 1.20.4 | 0x20 | 32 |
| 1.20.5 - 1.21.1 | 0x22 | 34 |
| 1.21.2 - 1.21.4 | 0x23 | 35 |
| 1.21.5 - 1.21.8 | 0x22 | 34 |
| 1.21.9 | 0x26 | 38 |

**Description:**

Used for a wide variety of game events, such as weather, respawn availability (from bed and respawn anchor), game mode, some game rules, and demo messages.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `BYTE` | Event: See below. |
| `FLOAT` | Value: Depends on Event. |
| `BYTE` | Event: See below. |
| `FLOAT` | Value: Depends on Event. |

---

### GAME_EVENT_TEST_HIGHLIGHT_POS

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.21.9 | 0x27 | 39 |

---

### HORSE_SCREEN_OPEN

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.14 - 1.14.4 | 0x1F | 31 |
| 1.15 | 0x20 | 32 |
| 1.16 - 1.16.1 | 0x1F | 31 |
| 1.16.2 | 0x1E | 30 |
| 1.17 - 1.18 | 0x1F | 31 |
| 1.19 - 1.19.0 | 0x1C | 28 |
| 1.19.1 - 1.19.2 | 0x1E | 30 |
| 1.19.3 | 0x1D | 29 |
| 1.19.4 - 1.20.1 | 0x20 | 32 |
| 1.20.2 - 1.20.4 | 0x21 | 33 |
| 1.20.5 - 1.21.1 | 0x23 | 35 |
| 1.21.2 - 1.21.4 | 0x24 | 36 |
| 1.21.5 - 1.21.8 | 0x23 | 35 |
| 1.21.9 | 0x28 | 40 |

**Description:**

This packet is used exclusively for opening the horse GUI. Open Screen is used for all other GUIs.  The client will not open the inventory if the Entity ID does not point to a horse-like animal.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `VAR_INT` | Window ID: Same as the field of Open Screen. |
| `VAR_INT` | Inventory columns count: How many columns of horse inventory slots exist in the GUI, 3 slots per column. |
| `INT` | Entity ID: The "owner" entity of the GUI. The client should close the GUI if the owner entity dies or is cleared. |

---

### HURT_ANIMATION

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.19.4 - 1.20.1 | 0x21 | 33 |
| 1.20.2 - 1.20.4 | 0x22 | 34 |
| 1.20.5 - 1.21.1 | 0x24 | 36 |
| 1.21.2 - 1.21.4 | 0x25 | 37 |
| 1.21.5 - 1.21.8 | 0x24 | 36 |
| 1.21.9 | 0x29 | 41 |

**Description:**

Plays a bobbing animation for the entity receiving damage.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `VAR_INT` | Entity ID: The ID of the entity taking damage |
| `FLOAT` | Yaw: The direction the damage is coming from in relation to the entity |
| `VAR_INT` | Entity ID: The ID of the entity taking damage |
| `FLOAT` | Yaw: The direction the damage is coming from in relation to the entity |

---

### INITIALIZE_BORDER

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.17 - 1.18 | 0x20 | 32 |
| 1.19 - 1.19.0 | 0x1D | 29 |
| 1.19.1 - 1.19.2 | 0x1F | 31 |
| 1.19.3 | 0x1E | 30 |
| 1.19.4 - 1.20.1 | 0x22 | 34 |
| 1.20.2 - 1.20.4 | 0x23 | 35 |
| 1.20.5 - 1.21.1 | 0x25 | 37 |
| 1.21.2 - 1.21.4 | 0x26 | 38 |
| 1.21.5 - 1.21.8 | 0x25 | 37 |
| 1.21.9 | 0x2A | 42 |

**Packet Fields:**

| Type | Description |
| --- | --- |
| `DOUBLE` | X |
| `DOUBLE` | Z |
| `DOUBLE` | Old Diameter: Current length of a single side of the world border, in meters. |
| `DOUBLE` | New Diameter: Target length of a single side of the world border, in meters. |
| `VAR_LONG` | Speed: Number of real-time milliseconds until New Diameter is reached. It appears that vanilla server does not sync world border speed to game ticks, so it gets out of sync with server lag. If the world border is not moving, this is set to 0. |
| `VAR_INT` | Portal Teleport Boundary: Resulting coordinates from a portal teleport are limited to ±value. Usually 29999984. |
| `VAR_INT` | Warning Blocks: In meters. |
| `VAR_INT` | Warning Time: In seconds as set by /worldborder warning time. |

---

### KEEP_ALIVE

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.8 | 0x0 | 0 |
| 1.9 - 1.12.1 | 0x1F | 31 |
| 1.13 | 0x21 | 33 |
| 1.14 - 1.14.4 | 0x20 | 32 |
| 1.15 | 0x21 | 33 |
| 1.16 - 1.16.1 | 0x20 | 32 |
| 1.16.2 | 0x1F | 31 |
| 1.17 - 1.18 | 0x21 | 33 |
| 1.19 - 1.19.0 | 0x1E | 30 |
| 1.19.1 - 1.19.2 | 0x20 | 32 |
| 1.19.3 | 0x1F | 31 |
| 1.19.4 - 1.20.1 | 0x23 | 35 |
| 1.20.2 - 1.20.4 | 0x24 | 36 |
| 1.20.5 - 1.21.1 | 0x26 | 38 |
| 1.21.2 - 1.21.4 | 0x27 | 39 |
| 1.21.5 - 1.21.8 | 0x26 | 38 |
| 1.21.9 | 0x2B | 43 |

**Description:**

The server will frequently send out a keep-alive, each containing a random ID. The client must respond with the same payload (see Serverbound Keep Alive). If the client does not respond to a Keep Alive packet within 15 seconds after it was sent, the server kicks the client. Vice versa, if the server does not send any keep-alives for 20 seconds, the client will disconnect and yield a "Timed out" exception. The vanilla server uses a system-dependent time in milliseconds to generate the keep alive ID value.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `LONG` | Keep Alive ID |
| `LONG` | Keep Alive ID |

---

### LEVEL_CHUNK

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.8 | 0x21 | 33 |
| 1.9 - 1.12.1 | 0x20 | 32 |
| 1.13 | 0x22 | 34 |
| 1.14 - 1.14.4 | 0x21 | 33 |
| 1.15 | 0x22 | 34 |
| 1.16 - 1.16.1 | 0x21 | 33 |
| 1.16.2 | 0x20 | 32 |
| 1.17 - 1.17.1 | 0x22 | 34 |

---

### LEVEL_CHUNK_WITH_LIGHT

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.18 | 0x22 | 34 |
| 1.19 - 1.19.0 | 0x1F | 31 |
| 1.19.1 - 1.19.2 | 0x21 | 33 |
| 1.19.3 | 0x20 | 32 |
| 1.19.4 - 1.20.1 | 0x24 | 36 |
| 1.20.2 - 1.20.4 | 0x25 | 37 |
| 1.20.5 - 1.21.1 | 0x27 | 39 |
| 1.21.2 - 1.21.4 | 0x28 | 40 |
| 1.21.5 - 1.21.8 | 0x27 | 39 |
| 1.21.9 | 0x2C | 44 |

**Description:**

Sent when a chunk comes into the client's view distance, specifying its terrain, lighting and block entities. The chunk must be within the view area previously specified with Set Center Chunk; see that packet for details. It is not strictly necessary to send all block entities in this packet; it is still legal to send them with Block Entity Data later.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `INT` | Chunk X: Chunk coordinate (block coordinate divided by 16, rounded down) |
| `INT` | Chunk Z: Chunk coordinate (block coordinate divided by 16, rounded down) |
| `CHUNK_DATA` | Data |
| `LIGHT_DATA` | Light |

---

### LEVEL_EVENT

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.8 | 0x28 | 40 |
| 1.9 - 1.12.1 | 0x21 | 33 |
| 1.13 | 0x23 | 35 |
| 1.14 - 1.14.4 | 0x22 | 34 |
| 1.15 | 0x23 | 35 |
| 1.16 - 1.16.1 | 0x22 | 34 |
| 1.16.2 | 0x21 | 33 |
| 1.17 - 1.18 | 0x23 | 35 |
| 1.19 - 1.19.0 | 0x20 | 32 |
| 1.19.1 - 1.19.2 | 0x22 | 34 |
| 1.19.3 | 0x21 | 33 |
| 1.19.4 - 1.20.1 | 0x25 | 37 |
| 1.20.2 - 1.20.4 | 0x26 | 38 |
| 1.20.5 - 1.21.1 | 0x28 | 40 |
| 1.21.2 - 1.21.4 | 0x29 | 41 |
| 1.21.5 - 1.21.8 | 0x28 | 40 |
| 1.21.9 | 0x2D | 45 |

**Description:**

Sent when a client is to play a sound or particle effect. By default, the Minecraft client adjusts the volume of sound effects based on distance. The final boolean field is used to disable this, and instead, the effect is played from 2 blocks away in the correct direction. Currently, this is only used for effect 1023 (wither spawn), effect 1028 (enderdragon death), and effect 1038 (end portal opening); it is ignored on other effects.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `INT` | Event: The event, see below. |
| `POSITION` | Location: The location of the event. |
| `INT` | Data: Extra data for certain events, see below. |
| `BOOLEAN` | Disable Relative Volume: See above. |

---

### LEVEL_PARTICLES

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.8 | 0x2A | 42 |
| 1.9 - 1.12.1 | 0x22 | 34 |
| 1.13 | 0x24 | 36 |
| 1.14 - 1.14.4 | 0x23 | 35 |
| 1.15 | 0x24 | 36 |
| 1.16 - 1.16.1 | 0x23 | 35 |
| 1.16.2 | 0x22 | 34 |
| 1.17 - 1.18 | 0x24 | 36 |
| 1.19 - 1.19.0 | 0x21 | 33 |
| 1.19.1 - 1.19.2 | 0x23 | 35 |
| 1.19.3 | 0x22 | 34 |
| 1.19.4 - 1.20.1 | 0x26 | 38 |
| 1.20.2 - 1.20.4 | 0x27 | 39 |
| 1.20.5 - 1.21.1 | 0x29 | 41 |
| 1.21.2 - 1.21.4 | 0x2A | 42 |
| 1.21.5 - 1.21.8 | 0x29 | 41 |
| 1.21.9 | 0x2E | 46 |

**Description:**

Displays the named particle

**Packet Fields:**

| Type | Description |
| --- | --- |
| `BOOLEAN` | Long Distance: If true, particle distance increases from 256 to 65536. |
| `BOOLEAN` | Always Visible: Whether this particle should always be visible. |
| `DOUBLE` | X: X position of the particle. |
| `DOUBLE` | Y: Y position of the particle. |
| `DOUBLE` | Z: Z position of the particle. |
| `FLOAT` | Offset X: This is added to the X position after being multiplied by random.nextGaussian(). |
| `FLOAT` | Offset Y: This is added to the Y position after being multiplied by random.nextGaussian(). |
| `FLOAT` | Offset Z: This is added to the Z position after being multiplied by random.nextGaussian(). |
| `FLOAT` | Max Speed |
| `INT` | Particle Count: The number of particles to create. |
| `VAR_INT` | Particle ID: ID in the minecraft:particle_type registry. |
| `VARIES` | Data: Particle data as specified in Particles. |

---

### LIGHT_UPDATE

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.14 - 1.14.4 | 0x24 | 36 |
| 1.15 | 0x25 | 37 |
| 1.16 - 1.16.1 | 0x24 | 36 |
| 1.16.2 | 0x23 | 35 |
| 1.17 - 1.18 | 0x25 | 37 |
| 1.19 - 1.19.0 | 0x22 | 34 |
| 1.19.1 - 1.19.2 | 0x24 | 36 |
| 1.19.3 | 0x23 | 35 |
| 1.19.4 - 1.20.1 | 0x27 | 39 |
| 1.20.2 - 1.20.4 | 0x28 | 40 |
| 1.20.5 - 1.21.1 | 0x2A | 42 |
| 1.21.2 - 1.21.4 | 0x2B | 43 |
| 1.21.5 - 1.21.8 | 0x2A | 42 |
| 1.21.9 | 0x2F | 47 |

**Description:**

Updates light levels for a chunk.  See Light for information on how lighting works in Minecraft.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `VAR_INT` | Chunk X: Chunk coordinate (block coordinate divided by 16, rounded down) |
| `VAR_INT` | Chunk Z: Chunk coordinate (block coordinate divided by 16, rounded down) |
| `LIGHT_DATA` | Data |

---

### LOGIN

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.8 | 0x1 | 1 |
| 1.9 - 1.12.1 | 0x23 | 35 |
| 1.13 - 1.14.4 | 0x25 | 37 |
| 1.15 | 0x26 | 38 |
| 1.16 - 1.16.1 | 0x25 | 37 |
| 1.16.2 | 0x24 | 36 |
| 1.17 - 1.18 | 0x26 | 38 |
| 1.19 - 1.19.0 | 0x23 | 35 |
| 1.19.1 - 1.19.2 | 0x25 | 37 |
| 1.19.3 | 0x24 | 36 |
| 1.19.4 - 1.20.1 | 0x28 | 40 |
| 1.20.2 - 1.20.4 | 0x29 | 41 |
| 1.20.5 - 1.21.1 | 0x2B | 43 |
| 1.21.2 - 1.21.4 | 0x2C | 44 |
| 1.21.5 - 1.21.8 | 0x2B | 43 |
| 1.21.9 | 0x30 | 48 |

**Description:**

See protocol encryption for information on logging in.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `INT` | Entity ID: The player's Entity ID (EID). |
| `BOOLEAN` | Is hardcore |
| `STRING` | Dimension Names: Identifiers for all dimensions on the server. |
| `VAR_INT` | Max Players: Was once used by the client to draw the player list, but now it is ignored. |
| `VAR_INT` | View Distance: Render distance (2-32). |
| `VAR_INT` | Simulation Distance: The distance that the client will process specific things, such as entities. |
| `BOOLEAN` | Reduced Debug Info: If true, a vanilla client shows reduced information on the debug screen.  For servers in development, this should almost always be false. |
| `BOOLEAN` | Enable respawn screen: Set to false when the doImmediateRespawn gamerule is true. |
| `BOOLEAN` | Do limited crafting: Whether players can only craft recipes they have already unlocked. Currently unused by the client. |
| `VAR_INT` | Dimension Type: The ID of the type of dimension in the minecraft:dimension_type registry, defined by the Registry Data packet. |
| `STRING` | Dimension Name: Name of the dimension being spawned into. |
| `LONG` | Hashed seed: First 8 bytes of the SHA-256 hash of the world's seed. Used client-side for biome noise |
| `BYTE` | Game mode: 0: Survival, 1: Creative, 2: Adventure, 3: Spectator. |
| `BYTE` | Previous Game mode: -1: Undefined (null), 0: Survival, 1: Creative, 2: Adventure, 3: Spectator. The previous game mode. Vanilla client uses this for the debug (F3 + N & F3 + F4) game mode switch. (More information needed) |
| `BOOLEAN` | Is Debug: True if the world is a debug mode world; debug mode worlds cannot be modified and have predefined blocks. |
| `BOOLEAN` | Is Flat: True if the world is a superflat world; flat worlds have different void fog and a horizon at y=0 instead of y=63. |
| `BOOLEAN` | Has death location: If true, then the next two fields are present. |
| `STRING` | Death dimension name: Name of the dimension the player died in. |
| `POSITION` | Death location: The location that the player died at. |
| `VAR_INT` | Portal cooldown: The number of ticks until the player can use the last used portal again. Looks like it's an attempt to fix MC-180. |
| `VAR_INT` | Sea level |
| `BOOLEAN` | Enforces Secure Chat |

---

### MAP_BULK_CHUNK

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.8 | 0x26 | 38 |

---

### MAP_ITEM_DATA

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.8 | 0x34 | 52 |
| 1.9 - 1.12.1 | 0x24 | 36 |
| 1.13 - 1.14.4 | 0x26 | 38 |
| 1.15 | 0x27 | 39 |
| 1.16 - 1.16.1 | 0x26 | 38 |
| 1.16.2 | 0x25 | 37 |
| 1.17 - 1.18 | 0x27 | 39 |
| 1.19 - 1.19.0 | 0x24 | 36 |
| 1.19.1 - 1.19.2 | 0x26 | 38 |
| 1.19.3 | 0x25 | 37 |
| 1.19.4 - 1.20.1 | 0x29 | 41 |
| 1.20.2 - 1.20.4 | 0x2A | 42 |
| 1.20.5 - 1.21.1 | 0x2C | 44 |
| 1.21.2 - 1.21.4 | 0x2D | 45 |
| 1.21.5 - 1.21.8 | 0x2C | 44 |
| 1.21.9 | 0x31 | 49 |

**Description:**

Updates a rectangular area on a map item.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `VAR_INT` | Map ID: Map ID of the map being modified |
| `BYTE` | Scale: From 0 for a fully zoomed-in map (1 block per pixel) to 4 for a fully zoomed-out map (16 blocks per pixel) |
| `BOOLEAN` | Locked: True if the map has been locked in a cartography table |
| `VAR_INT` | Prefixed Optional Prefixed Array: See below |
| `BYTE` | X: Map coordinates: -128 for furthest left, +127 for furthest right |
| `BYTE` | Z: Map coordinates: -128 for highest, +127 for lowest |
| `BYTE` | Direction: 0-15 |
| `PREFIXED_OPTIONAL_TEXT_COMPONENT` | Display Name |
| `BYTE` | Columns: Number of columns updated |
| `BYTE` | Rows: Only if Columns is more than 0; number of rows updated |
| `BYTE` | X: Only if Columns is more than 0; x offset of the westernmost column |
| `BYTE` | Z: Only if Columns is more than 0; z offset of the northernmost row |
| `BYTE` | Data: Only if Columns is more than 0; see Map item format |

---

### MERCHANT_OFFERS

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.14 - 1.14.4 | 0x27 | 39 |
| 1.15 | 0x28 | 40 |
| 1.16 - 1.16.1 | 0x27 | 39 |
| 1.16.2 | 0x26 | 38 |
| 1.17 - 1.18 | 0x28 | 40 |
| 1.19 - 1.19.0 | 0x25 | 37 |
| 1.19.1 - 1.19.2 | 0x27 | 39 |
| 1.19.3 | 0x26 | 38 |
| 1.19.4 - 1.20.1 | 0x2A | 42 |
| 1.20.2 - 1.20.4 | 0x2B | 43 |
| 1.20.5 - 1.21.1 | 0x2D | 45 |
| 1.21.2 - 1.21.4 | 0x2E | 46 |
| 1.21.5 - 1.21.8 | 0x2D | 45 |
| 1.21.9 | 0x32 | 50 |

**Description:**

The list of trades a villager NPC is offering. 1: Novice, 2: Apprentice, 3: Journeyman, 4: Expert, 5: Master.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `VAR_INT` | Window ID: The ID of the window that is open; this is an int rather than a byte. |
| `TRADE_ITEM` | Prefixed Array: See below. The first item the player has to supply for this villager trade. The count of the item stack is the default "price" of this trade. |
| `SLOT` | Output item: The item the player will receive from this villager trade. |
| `PREFIXED_OPTIONAL_TRADE_ITEM` | Input item 2: The second item the player has to supply for this villager trade. |
| `BOOLEAN` | Trade disabled: True if the trade is disabled; false if the trade is enabled. |
| `INT` | Number of trade uses: Number of times the trade has been used so far. If equal to the maximum number of trades, the client will display a red X. |
| `INT` | Maximum number of trade uses: Number of times this trade can be used before it's exhausted. |
| `INT` | XP: Amount of XP the villager will earn each time the trade is used. |
| `INT` | Special Price: Can be zero or negative. The number is added to the price when an item is discounted due to player reputation or other effects. |
| `FLOAT` | Price Multiplier: Can be low (0.05) or high (0.2). Determines how much demand, player reputation, and temporary effects will adjust the price. |
| `INT` | Demand: If positive, causes the price to increase. Negative values seem to be treated the same as zero. |
| `VAR_INT` | Villager level: Appears on the trade GUI; meaning comes from the translation key merchant.level. + level.
1: Novice, 2: Apprentice, 3: Journeyman, 4: Expert, 5: Master. |
| `VAR_INT` | Experience: Total experience for this villager (always 0 for the wandering trader). |
| `BOOLEAN` | Is regular villager: True if this is a regular villager; false for the wandering trader.  When false, hides the villager level and some other GUI elements. |
| `BOOLEAN` | Can restock: True for regular villagers and false for the wandering trader. If true, the "Villagers restock up to two times per day." message is displayed when hovering over disabled trades. |
| `VAR_INT` | Window ID: The ID of the window that is open; this is an int rather than a byte. |
| `TRADE_ITEM` | Prefixed Array: See below. The first item the player has to supply for this villager trade. The count of the item stack is the default "price" of this trade. |
| `SLOT` | Output item: The item the player will receive from this villager trade. |
| `PREFIXED_OPTIONAL_TRADE_ITEM` | Input item 2: The second item the player has to supply for this villager trade. |
| `BOOLEAN` | Trade disabled: True if the trade is disabled; false if the trade is enabled. |
| `INT` | Number of trade uses: Number of times the trade has been used so far. If equal to the maximum number of trades, the client will display a red X. |
| `INT` | Maximum number of trade uses: Number of times this trade can be used before it's exhausted. |
| `INT` | XP: Amount of XP the villager will earn each time the trade is used. |
| `INT` | Special Price: Can be zero or negative. The number is added to the price when an item is discounted due to player reputation or other effects. |
| `FLOAT` | Price Multiplier: Can be low (0.05) or high (0.2). Determines how much demand, player reputation, and temporary effects will adjust the price. |
| `INT` | Demand: If positive, causes the price to increase. Negative values seem to be treated the same as zero. |
| `VAR_INT` | Villager level: Appears on the trade GUI; meaning comes from the translation key merchant.level. + level.
1: Novice, 2: Apprentice, 3: Journeyman, 4: Expert, 5: Master. |
| `VAR_INT` | Experience: Total experience for this villager (always 0 for the wandering trader). |
| `BOOLEAN` | Is regular villager: True if this is a regular villager; false for the wandering trader.  When false, hides the villager level and some other GUI elements. |
| `BOOLEAN` | Can restock: True for regular villagers and false for the wandering trader. If true, the "Villagers restock up to two times per day." message is displayed when hovering over disabled trades. |
| `VAR_INT` | Item ID: The item ID. Item IDs are distinct from block IDs; see Data Generators for more information. |
| `VAR_INT` | Item Count: The item count. |
| `COMPONENT_TYPE` | Components: Prefixed Array |
| `VARIES` | Component data: The component-dependent data. See Structured components for more detail. |

---

### MOVE_ENTITY

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.8 | 0x14 | 20 |
| 1.9 - 1.11 | 0x28 | 40 |
| 1.12 - 1.12.1 | 0x25 | 37 |
| 1.13 | 0x27 | 39 |
| 1.14 - 1.14.4 | 0x2B | 43 |
| 1.15 | 0x2C | 44 |
| 1.16 - 1.16.1 | 0x2B | 43 |
| 1.16.2 | 0x2A | 42 |

---

### MOVE_ENTITY_POS

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.8 | 0x15 | 21 |
| 1.9 - 1.11 | 0x25 | 37 |
| 1.12 - 1.12.1 | 0x26 | 38 |
| 1.13 - 1.14.4 | 0x28 | 40 |
| 1.15 | 0x29 | 41 |
| 1.16 - 1.16.1 | 0x28 | 40 |
| 1.16.2 | 0x27 | 39 |
| 1.17 - 1.18 | 0x29 | 41 |
| 1.19 - 1.19.0 | 0x26 | 38 |
| 1.19.1 - 1.19.2 | 0x28 | 40 |
| 1.19.3 | 0x27 | 39 |
| 1.19.4 - 1.20.1 | 0x2B | 43 |
| 1.20.2 - 1.20.4 | 0x2C | 44 |
| 1.20.5 - 1.21.1 | 0x2E | 46 |
| 1.21.2 - 1.21.4 | 0x2F | 47 |
| 1.21.5 - 1.21.8 | 0x2E | 46 |
| 1.21.9 | 0x33 | 51 |

**Description:**

This packet is sent by the server when an entity moves a small distance. The change in position is represented as a fixed-point number with 12 fraction bits and 4 integer bits. As such, the maximum movement distance along each axis is 8 blocks in the negative direction, or 7.999755859375 blocks in the positive direction. If the movement exceeds these limits, Teleport Entity should be sent instead.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `VAR_INT` | Entity ID |
| `SHORT` | Delta X: Change in X position as currentX * 4096 - prevX * 4096. |
| `SHORT` | Delta Y: Change in Y position as currentY * 4096 - prevY * 4096. |
| `SHORT` | Delta Z: Change in Z position as currentZ * 4096 - prevZ * 4096. |
| `BOOLEAN` | On Ground |

---

### MOVE_ENTITY_POS_ROT

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.8 | 0x17 | 23 |
| 1.9 - 1.11 | 0x26 | 38 |
| 1.12 - 1.12.1 | 0x27 | 39 |
| 1.13 - 1.14.4 | 0x29 | 41 |
| 1.15 | 0x2A | 42 |
| 1.16 - 1.16.1 | 0x29 | 41 |
| 1.16.2 | 0x28 | 40 |
| 1.17 - 1.18 | 0x2A | 42 |
| 1.19 - 1.19.0 | 0x27 | 39 |
| 1.19.1 - 1.19.2 | 0x29 | 41 |
| 1.19.3 | 0x28 | 40 |
| 1.19.4 - 1.20.1 | 0x2C | 44 |
| 1.20.2 - 1.20.4 | 0x2D | 45 |
| 1.20.5 - 1.21.1 | 0x2F | 47 |
| 1.21.2 - 1.21.4 | 0x30 | 48 |
| 1.21.5 - 1.21.8 | 0x2F | 47 |
| 1.21.9 | 0x34 | 52 |

**Description:**

This packet is sent by the server when an entity rotates and moves. See #Update Entity Position for how the position is encoded.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `VAR_INT` | Entity ID |
| `SHORT` | Delta X: Change in X position as currentX * 4096 - prevX * 4096. |
| `SHORT` | Delta Y: Change in Y position as currentY * 4096 - prevY * 4096. |
| `SHORT` | Delta Z: Change in Z position as currentZ * 4096 - prevZ * 4096. |
| `BYTE` | Yaw: New angle, not a delta. |
| `BYTE` | Pitch: New angle, not a delta. |
| `BOOLEAN` | On Ground |

---

### MOVE_ENTITY_ROT

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.8 | 0x16 | 22 |
| 1.9 - 1.11 | 0x27 | 39 |
| 1.12 - 1.12.1 | 0x28 | 40 |
| 1.13 - 1.14.4 | 0x2A | 42 |
| 1.15 | 0x2B | 43 |
| 1.16 - 1.16.1 | 0x2A | 42 |
| 1.16.2 | 0x29 | 41 |
| 1.17 - 1.18 | 0x2B | 43 |
| 1.19 - 1.19.0 | 0x28 | 40 |
| 1.19.1 - 1.19.2 | 0x2A | 42 |
| 1.19.3 | 0x29 | 41 |
| 1.19.4 - 1.20.1 | 0x2D | 45 |
| 1.20.2 - 1.20.4 | 0x2E | 46 |
| 1.20.5 - 1.21.1 | 0x30 | 48 |
| 1.21.2 - 1.21.4 | 0x32 | 50 |
| 1.21.5 - 1.21.8 | 0x31 | 49 |
| 1.21.9 | 0x36 | 54 |

**Description:**

This packet is sent by the server when an entity rotates.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `VAR_INT` | Entity ID |
| `BYTE` | Yaw: New angle, not a delta. |
| `BYTE` | Pitch: New angle, not a delta. |
| `BOOLEAN` | On Ground |

---

### MOVE_MINECART_ALONG_TRACK

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.21.2 - 1.21.4 | 0x31 | 49 |
| 1.21.5 - 1.21.8 | 0x30 | 48 |
| 1.21.9 | 0x35 | 53 |

**Packet Fields:**

| Type | Description |
| --- | --- |
| `VAR_INT` | Entity ID |
| `DOUBLE` | Prefixed Array |
| `DOUBLE` | Y |
| `DOUBLE` | Z |
| `DOUBLE` | Velocity X |
| `DOUBLE` | Velocity Y |
| `DOUBLE` | Velocity Z |
| `BYTE` | Yaw |
| `BYTE` | Pitch |
| `VAR_INT` | Entity ID |
| `DOUBLE` | Prefixed Array |
| `DOUBLE` | Y |
| `DOUBLE` | Z |
| `DOUBLE` | Velocity X |
| `DOUBLE` | Velocity Y |
| `DOUBLE` | Velocity Z |
| `BYTE` | Yaw |
| `BYTE` | Pitch |

---

### MOVE_VEHICLE

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.9 - 1.12.1 | 0x29 | 41 |
| 1.13 | 0x2B | 43 |
| 1.14 - 1.14.4 | 0x2C | 44 |
| 1.15 | 0x2D | 45 |
| 1.16 - 1.16.1 | 0x2C | 44 |
| 1.16.2 | 0x2B | 43 |
| 1.17 - 1.18 | 0x2C | 44 |
| 1.19 - 1.19.0 | 0x29 | 41 |
| 1.19.1 - 1.19.2 | 0x2B | 43 |
| 1.19.3 | 0x2A | 42 |
| 1.19.4 - 1.20.1 | 0x2E | 46 |
| 1.20.2 - 1.20.4 | 0x2F | 47 |
| 1.20.5 - 1.21.1 | 0x31 | 49 |
| 1.21.2 - 1.21.4 | 0x33 | 51 |
| 1.21.5 - 1.21.8 | 0x32 | 50 |
| 1.21.9 | 0x37 | 55 |

**Description:**

If the player is riding a client-side-controlled vehicle, teleports the vehicle to the specified position. Sent by the vanilla server in response to serverbound Move Vehicle packets that fail the movement speed check. Note that all fields use absolute positioning and do not allow for relative positioning.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `DOUBLE` | X: Absolute position (X coordinate). |
| `DOUBLE` | Y: Absolute position (Y coordinate). |
| `DOUBLE` | Z: Absolute position (Z coordinate). |
| `FLOAT` | Yaw: Absolute rotation on the vertical axis, in degrees. |
| `FLOAT` | Pitch: Absolute rotation on the horizontal axis, in degrees. |

---

### OPEN_BOOK

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.14 - 1.14.4 | 0x2D | 45 |
| 1.15 | 0x2E | 46 |
| 1.16 - 1.16.1 | 0x2D | 45 |
| 1.16.2 | 0x2C | 44 |
| 1.17 - 1.18 | 0x2D | 45 |
| 1.19 - 1.19.0 | 0x2A | 42 |
| 1.19.1 - 1.19.2 | 0x2C | 44 |
| 1.19.3 | 0x2B | 43 |
| 1.19.4 - 1.20.1 | 0x2F | 47 |
| 1.20.2 - 1.20.4 | 0x30 | 48 |
| 1.20.5 - 1.21.1 | 0x32 | 50 |
| 1.21.2 - 1.21.4 | 0x34 | 52 |
| 1.21.5 - 1.21.8 | 0x33 | 51 |
| 1.21.9 | 0x38 | 56 |

**Description:**

Sent when a player right-clicks with a signed book. This tells the client to open the book GUI.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `VAR_INT` | Hand: 0: Main hand, 1: Off hand . |
| `VAR_INT` | Hand: 0: Main hand, 1: Off hand . |

---

### OPEN_SCREEN

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.8 | 0x2D | 45 |
| 1.9 - 1.12.1 | 0x13 | 19 |
| 1.13 | 0x14 | 20 |
| 1.14 - 1.14.4 | 0x2E | 46 |
| 1.15 | 0x2F | 47 |
| 1.16 - 1.16.1 | 0x2E | 46 |
| 1.16.2 | 0x2D | 45 |
| 1.17 - 1.18 | 0x2E | 46 |
| 1.19 - 1.19.0 | 0x2B | 43 |
| 1.19.1 - 1.19.2 | 0x2D | 45 |
| 1.19.3 | 0x2C | 44 |
| 1.19.4 - 1.20.1 | 0x30 | 48 |
| 1.20.2 - 1.20.4 | 0x31 | 49 |
| 1.20.5 - 1.21.1 | 0x33 | 51 |
| 1.21.2 - 1.21.4 | 0x35 | 53 |
| 1.21.5 - 1.21.8 | 0x34 | 52 |
| 1.21.9 | 0x39 | 57 |

**Description:**

This is sent to the client when it should open an inventory, such as a chest, workbench, furnace, or other container. Resending this packet with the already existing window ID, will update the window title and window type without closing the window. This message is not sent to clients opening their own inventory, nor do clients inform the server in any way when doing so. From the server's perspective, the inventory is always "open" whenever no other windows are. For horses, use Open Horse Screen.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `VAR_INT` | Window ID: An identifier for the window to be displayed. The vanilla server implementation is a counter, starting at 1. There can only be one window at a time; this is only used to ignore outdated packets targeting already-closed windows. Note also that the Window ID field in most other packets is only a single byte, and indeed, the vanilla server wraps around after 100. |
| `VAR_INT` | Window Type: The window type to use for display. Contained in the minecraft:menu registry; see Inventory for the different values. |
| `TEXT_COMPONENT` | Window Title: The title of the window. |
| `VAR_INT` | Window ID: An identifier for the window to be displayed. The vanilla server implementation is a counter, starting at 1. There can only be one window at a time; this is only used to ignore outdated packets targeting already-closed windows. Note also that the Window ID field in most other packets is only a single byte, and indeed, the vanilla server wraps around after 100. |
| `VAR_INT` | Window Type: The window type to use for display. Contained in the minecraft:menu registry; see Inventory for the different values. |
| `TEXT_COMPONENT` | Window Title: The title of the window. |

---

### OPEN_SIGN_EDITOR

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.8 | 0x36 | 54 |
| 1.9 - 1.12.1 | 0x2A | 42 |
| 1.13 | 0x2C | 44 |
| 1.14 - 1.14.4 | 0x2F | 47 |
| 1.15 | 0x30 | 48 |
| 1.16 - 1.16.1 | 0x2F | 47 |
| 1.16.2 | 0x2E | 46 |
| 1.17 - 1.18 | 0x2F | 47 |
| 1.19 - 1.19.0 | 0x2C | 44 |
| 1.19.1 - 1.19.2 | 0x2E | 46 |
| 1.19.3 | 0x2D | 45 |
| 1.19.4 - 1.20.1 | 0x31 | 49 |
| 1.20.2 - 1.20.4 | 0x32 | 50 |
| 1.20.5 - 1.21.1 | 0x34 | 52 |
| 1.21.2 - 1.21.4 | 0x36 | 54 |
| 1.21.5 - 1.21.8 | 0x35 | 53 |
| 1.21.9 | 0x3A | 58 |

**Description:**

Sent when the client has placed a sign and is allowed to send Update Sign.  There must already be a sign at the given location (which the client does not do automatically) - send a Block Update first.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `POSITION` | Location |
| `BOOLEAN` | Is Front Text: Whether the opened editor is for the front or on the back of the sign |
| `POSITION` | Location |
| `BOOLEAN` | Is Front Text: Whether the opened editor is for the front or on the back of the sign |

---

### PING

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.17 - 1.18 | 0x30 | 48 |
| 1.19 - 1.19.0 | 0x2D | 45 |
| 1.19.1 - 1.19.2 | 0x2F | 47 |
| 1.19.3 | 0x2E | 46 |
| 1.19.4 - 1.20.1 | 0x32 | 50 |
| 1.20.2 - 1.20.4 | 0x33 | 51 |
| 1.20.5 - 1.21.1 | 0x35 | 53 |
| 1.21.2 - 1.21.4 | 0x37 | 55 |
| 1.21.5 - 1.21.8 | 0x36 | 54 |
| 1.21.9 | 0x3B | 59 |

**Description:**

Packet is not used by the vanilla server. When sent to the client, the client responds with a Pong packet with the same ID.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `INT` | ID |
| `INT` | ID |

---

### PLACE_GHOST_RECIPE

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.12.1 | 0x2B | 43 |
| 1.13 | 0x2D | 45 |
| 1.14 - 1.14.4 | 0x30 | 48 |
| 1.15 | 0x31 | 49 |
| 1.16 - 1.16.1 | 0x30 | 48 |
| 1.16.2 | 0x2F | 47 |
| 1.17 - 1.18 | 0x31 | 49 |
| 1.19 - 1.19.0 | 0x2E | 46 |
| 1.19.1 - 1.19.2 | 0x30 | 48 |
| 1.19.3 | 0x2F | 47 |
| 1.19.4 - 1.20.1 | 0x33 | 51 |
| 1.20.2 - 1.20.4 | 0x35 | 53 |
| 1.20.5 - 1.21.1 | 0x37 | 55 |
| 1.21.2 - 1.21.4 | 0x39 | 57 |
| 1.21.5 - 1.21.8 | 0x38 | 56 |
| 1.21.9 | 0x3D | 61 |

**Description:**

Response to the serverbound packet (Place Recipe), with the same recipe ID. Appears to be used to notify the UI.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `VAR_INT` | Window ID |
| `RECIPE_DISPLAY` | Recipe Display |
| `VAR_INT` | Window ID |
| `RECIPE_DISPLAY` | Recipe Display |

---

### PLAYER_ABILITIES

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.8 | 0x39 | 57 |
| 1.9 - 1.12.0 | 0x2B | 43 |
| 1.12.1 | 0x2C | 44 |
| 1.13 | 0x2E | 46 |
| 1.14 - 1.14.4 | 0x31 | 49 |
| 1.15 | 0x32 | 50 |
| 1.16 - 1.16.1 | 0x31 | 49 |
| 1.16.2 | 0x30 | 48 |
| 1.17 - 1.18 | 0x32 | 50 |
| 1.19 - 1.19.0 | 0x2F | 47 |
| 1.19.1 - 1.19.2 | 0x31 | 49 |
| 1.19.3 | 0x30 | 48 |
| 1.19.4 - 1.20.1 | 0x34 | 52 |
| 1.20.2 - 1.20.4 | 0x36 | 54 |
| 1.20.5 - 1.21.1 | 0x38 | 56 |
| 1.21.2 - 1.21.4 | 0x3A | 58 |
| 1.21.5 - 1.21.8 | 0x39 | 57 |
| 1.21.9 | 0x3E | 62 |

**Description:**

The latter 2 floats are used to indicate the flying speed and field of view respectively, while the first byte is used to determine the value of 4 booleans.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `BYTE` | Flags: Bit field, see below. |
| `FLOAT` | Flying Speed: 0.05 by default. |
| `FLOAT` | Field of View Modifier: Modifies the field of view, like a speed potion. A vanilla server will use the same value as the movement speed sent in the Update Attributes packet, which defaults to 0.1 for players. |

---

### PLAYER_CHAT

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.19 - 1.19.0 | 0x30 | 48 |
| 1.19.1 - 1.19.2 | 0x33 | 51 |
| 1.19.3 | 0x31 | 49 |
| 1.19.4 - 1.20.1 | 0x35 | 53 |
| 1.20.2 - 1.20.4 | 0x37 | 55 |
| 1.20.5 - 1.21.1 | 0x39 | 57 |
| 1.21.2 - 1.21.4 | 0x3B | 59 |
| 1.21.5 - 1.21.8 | 0x3A | 58 |
| 1.21.9 | 0x3F | 63 |

**Description:**

Sends the client a chat message from a player. Currently, a lot is unknown about this packet, blank descriptions are for those that are unknown This is used as the content parameter when formatting the message on the client. This is used as the sender parameter when formatting the message on the client. This is used as the target parameter when formatting the message on the client.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `VAR_INT` | Global Index: A counter that starts at zero and gets increased by one for each chat message sent to the client. Each client has its own counter. |
| `UUID` | Sender: Used by the vanilla client for the disableChat launch option. Setting both longs to 0 will always display the message regardless of the setting. |
| `VAR_INT` | Index |
| `BYTE` | Message Signature bytes: Cryptography, the signature consists of the Sender UUID, Session UUID from the Player Session packet, Index, Salt, Timestamp in epoch seconds, the length of the original chat content, the original content itself, the length of Previous Messages, and all of the Previous message signatures. These values are hashed with SHA-256 and signed using the RSA cryptosystem. Modifying any of these values in the packet will cause this signature to fail. This buffer is always 256 bytes long and it is not length-prefixed. |
| `STRING` | Message: Raw (optionally) signed sent message content.
This is used as the content parameter when formatting the message on the client. |
| `LONG` | Timestamp: Represents the time the message was signed as milliseconds since the epoch, used to check if the message was received within 2 minutes of it being sent. |
| `LONG` | Salt: Cryptography, used for validating the message signature. |
| `VAR_INT` | Message ID: The message ID + 1, used for validating message signature. The next field is present only when value of this field is equal to 0. |
| `BYTE` | Signature: The previous message's signature. Contains the same type of data as Message Signature bytes (256 bytes) above. Not length-prefixed. |
| `PREFIXED_OPTIONAL_TEXT_COMPONENT` | Unsigned Content |
| `VAR_INT` | Filter Type: If the message has been filtered |
| `OPTIONAL_BITSET` | Filter Type Bits: Only present if the Filter Type is Partially Filtered. Specifies the indices at which characters in the original message string should be replaced with the # symbol (i.e., filtered) by the vanilla client |
| `COMPONENT` | Chat Type: Either the type of chat in the minecraft:chat_type registry, defined by the Registry Data packet, or an inline definition. |
| `TEXT_COMPONENT` | Sender Name: The name of the one sending the message, usually the sender's display name.
This is used as the sender parameter when formatting the message on the client. |
| `PREFIXED_OPTIONAL_TEXT_COMPONENT` | Target Name: The name of the one receiving the message, usually the receiver's display name.
This is used as the target parameter when formatting the message on the client. |

---

### PLAYER_CHAT_HEADER

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.19.1 | 0x32 | 50 |

---

### PLAYER_COMBAT

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.8 | 0x42 | 66 |
| 1.9 - 1.12.0 | 0x2C | 44 |
| 1.12.1 | 0x2D | 45 |
| 1.13 | 0x2F | 47 |
| 1.14 - 1.14.4 | 0x32 | 50 |
| 1.15 | 0x33 | 51 |
| 1.16 - 1.16.1 | 0x32 | 50 |
| 1.16.2 | 0x31 | 49 |

---

### PLAYER_COMBAT_END

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.17 - 1.18 | 0x33 | 51 |
| 1.19 - 1.19.0 | 0x31 | 49 |
| 1.19.1 - 1.19.2 | 0x34 | 52 |
| 1.19.3 | 0x32 | 50 |
| 1.19.4 - 1.20.1 | 0x36 | 54 |
| 1.20.2 - 1.20.4 | 0x38 | 56 |
| 1.20.5 - 1.21.1 | 0x3A | 58 |
| 1.21.2 - 1.21.4 | 0x3C | 60 |
| 1.21.5 - 1.21.8 | 0x3B | 59 |
| 1.21.9 | 0x40 | 64 |

**Description:**

Unused by the vanilla client.  This data was once used for twitch.tv metadata circa 1.8.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `VAR_INT` | Duration: Length of the combat in ticks. |

---

### PLAYER_COMBAT_ENTER

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.17 - 1.18 | 0x34 | 52 |
| 1.19 - 1.19.0 | 0x32 | 50 |
| 1.19.1 - 1.19.2 | 0x35 | 53 |
| 1.19.3 | 0x33 | 51 |
| 1.19.4 - 1.20.1 | 0x37 | 55 |
| 1.20.2 - 1.20.4 | 0x39 | 57 |
| 1.20.5 - 1.21.1 | 0x3B | 59 |
| 1.21.2 - 1.21.4 | 0x3D | 61 |
| 1.21.5 - 1.21.8 | 0x3C | 60 |
| 1.21.9 | 0x41 | 65 |

**Description:**

Unused by the vanilla client.  This data was once used for twitch.tv metadata circa 1.8.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `CLIENT` | Play: no fields |

---

### PLAYER_COMBAT_KILL

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.17 - 1.18 | 0x35 | 53 |
| 1.19 - 1.19.0 | 0x33 | 51 |
| 1.19.1 - 1.19.2 | 0x36 | 54 |
| 1.19.3 | 0x34 | 52 |
| 1.19.4 - 1.20.1 | 0x38 | 56 |
| 1.20.2 - 1.20.4 | 0x3A | 58 |
| 1.20.5 - 1.21.1 | 0x3C | 60 |
| 1.21.2 - 1.21.4 | 0x3E | 62 |
| 1.21.5 - 1.21.8 | 0x3D | 61 |
| 1.21.9 | 0x42 | 66 |

**Description:**

Used to send a respawn screen.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `VAR_INT` | Player ID: Entity ID of the player that died (should match the client's entity ID). |
| `TEXT_COMPONENT` | Message: The death message. |

---

### PLAYER_INFO

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.8 | 0x38 | 56 |
| 1.9 - 1.12.0 | 0x2D | 45 |
| 1.12.1 | 0x2E | 46 |
| 1.13 | 0x30 | 48 |
| 1.14 - 1.14.4 | 0x33 | 51 |
| 1.15 | 0x34 | 52 |
| 1.16 - 1.16.1 | 0x33 | 51 |
| 1.16.2 | 0x32 | 50 |
| 1.17 - 1.18 | 0x36 | 54 |
| 1.19 - 1.19.0 | 0x34 | 52 |
| 1.19.1 | 0x37 | 55 |

---

### PLAYER_INFO_REMOVE

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.19.3 | 0x35 | 53 |
| 1.19.4 - 1.20.1 | 0x39 | 57 |
| 1.20.2 - 1.20.4 | 0x3B | 59 |
| 1.20.5 - 1.21.1 | 0x3D | 61 |
| 1.21.2 - 1.21.4 | 0x3F | 63 |
| 1.21.5 - 1.21.8 | 0x3E | 62 |
| 1.21.9 | 0x43 | 67 |

**Description:**

Used by the server to remove players from the player list.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `UUID` | UUIDs: UUIDs of players to remove. |
| `UUID` | UUIDs: UUIDs of players to remove. |

---

### PLAYER_INFO_UPDATE

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.19.3 | 0x36 | 54 |
| 1.19.4 - 1.20.1 | 0x3A | 58 |
| 1.20.2 - 1.20.4 | 0x3C | 60 |
| 1.20.5 - 1.21.1 | 0x3E | 62 |
| 1.21.2 - 1.21.4 | 0x40 | 64 |
| 1.21.5 - 1.21.8 | 0x3F | 63 |
| 1.21.9 | 0x44 | 68 |

**Description:**

Sent by the server to update the user list ( in the client).

**Packet Fields:**

| Type | Description |
| --- | --- |
| `ENUMSET` | Actions: Determines what actions are present. |
| `UUID` | Prefixed Array: The player UUID |
| `ARRAY_OF_PLAYERACTIONS` | Player Actions: The length of this array is determined by the number of Player Actions that give a non-zero value when applying its mask to the actions flag. For example, given the decimal number 5, binary 00000101. The masks 0x01 and 0x04 would return a non-zero value, meaning the Player Actions array would include two actions: Add Player and Update Game Mode. |
| `ENUMSET` | Actions: Determines what actions are present. |
| `UUID` | Prefixed Array: The player UUID |
| `ARRAY_OF_PLAYERACTIONS` | Player Actions: The length of this array is determined by the number of Player Actions that give a non-zero value when applying its mask to the actions flag. For example, given the decimal number 5, binary 00000101. The masks 0x01 and 0x04 would return a non-zero value, meaning the Player Actions array would include two actions: Add Player and Update Game Mode. |
| `NAME` | 0x01: String (16) |
| `STRING` | Value |
| `STRING` | Signature |
| `LONG` | Public key expiry time: Key expiry time, as a UNIX timestamp in milliseconds. Only sent if Has Signature Data is true. |
| `BYTE` | Encoded public key: The player's public key, in bytes. Only sent if Has Signature Data is true. |
| `BYTE` | Public key signature: The public key's digital signature. Only sent if Has Signature Data is true. |
| `GAME_MODE` | 0x04: VarInt |

---

### PLAYER_LOOK_AT

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.13 | 0x31 | 49 |
| 1.14 - 1.14.4 | 0x34 | 52 |
| 1.15 | 0x35 | 53 |
| 1.16 - 1.16.1 | 0x34 | 52 |
| 1.16.2 | 0x33 | 51 |
| 1.17 - 1.18 | 0x37 | 55 |
| 1.19 - 1.19.0 | 0x35 | 53 |
| 1.19.1 - 1.19.2 | 0x38 | 56 |
| 1.19.3 | 0x37 | 55 |
| 1.19.4 - 1.20.1 | 0x3B | 59 |
| 1.20.2 - 1.20.4 | 0x3D | 61 |
| 1.20.5 - 1.21.1 | 0x3F | 63 |
| 1.21.2 - 1.21.4 | 0x41 | 65 |
| 1.21.5 - 1.21.8 | 0x40 | 64 |
| 1.21.9 | 0x45 | 69 |

**Description:**

Used to rotate the client player to face the given location or entity (for /teleport []    facing).

**Packet Fields:**

| Type | Description |
| --- | --- |
| `PLAY` | protocol:0x40resource:player_look_at: Client |
| `VAR_INT` | Feet/eyes: Values are feet=0, eyes=1.  If set to eyes, aims using the head position; otherwise, aims using the feet position. |
| `DOUBLE` | Target x: x coordinate of the point to face towards. |
| `DOUBLE` | Target y: y coordinate of the point to face towards. |
| `DOUBLE` | Target z: z coordinate of the point to face towards. |
| `BOOLEAN` | Is entity: If true, additional information about an entity is provided. |
| `VAR_INT` | Entity ID: Only if is entity is true — the entity to face towards. |
| `VAR_INT` | Entity feet/eyes: Whether to look at the entity's eyes or feet.  Same values and meanings as before, just for the entity's head/feet. |

---

### PLAYER_POSITION

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.8 | 0x8 | 8 |
| 1.9 - 1.12.0 | 0x2E | 46 |
| 1.12.1 | 0x2F | 47 |
| 1.13 | 0x32 | 50 |
| 1.14 - 1.14.4 | 0x35 | 53 |
| 1.15 | 0x36 | 54 |
| 1.16 - 1.16.1 | 0x35 | 53 |
| 1.16.2 | 0x34 | 52 |
| 1.17 - 1.18 | 0x38 | 56 |
| 1.19 - 1.19.0 | 0x36 | 54 |
| 1.19.1 - 1.19.2 | 0x39 | 57 |
| 1.19.3 | 0x38 | 56 |
| 1.19.4 - 1.20.1 | 0x3C | 60 |
| 1.20.2 - 1.20.4 | 0x3E | 62 |
| 1.20.5 - 1.21.1 | 0x40 | 64 |
| 1.21.2 - 1.21.4 | 0x42 | 66 |
| 1.21.5 - 1.21.8 | 0x41 | 65 |
| 1.21.9 | 0x46 | 70 |

**Description:**

Teleports the client, e.g., during login, when using an ender pearl, in response to invalid move packets, etc. Due to latency, the server may receive outdated movement packets sent before the client was aware of the teleport. To account for this, the server ignores all movement packets from the client until a Confirm Teleportation packet with an ID matching the one sent in the teleport packet is received. The vanilla client will also send a Set Player Position and Rotation packet after the Confirm Teleportation packet with the position and rotation received from this packet, and horizontal collision and on ground set to false. Yaw is measured in degrees and does not follow classical trigonometry rules. The unit circle of yaw on the XZ-plane starts at (0, 1) and turns counterclockwise, with 90 at (-1, 0), 180 at (0, -1) and 270 at (1, 0). Additionally, yaw is not clamped to between 0 and 360 degrees; any number is valid, including negative numbers and numbers greater than 360 (see MC-90097). Pitch is measured in degrees, where 0 is looking straight ahead, -90 is looking straight up, and 90 is looking straight down. If the player is riding a vehicle, this packet has no effect, but both the Confirm Teleportation and Set Player Position and Rotation packets are still sent.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `VAR_INT` | Teleport ID: Client should confirm this packet with Confirm Teleportation containing the same Teleport ID. |
| `DOUBLE` | X: Absolute or relative position, depending on Flags. |
| `DOUBLE` | Y: Absolute or relative position, depending on Flags. |
| `DOUBLE` | Z: Absolute or relative position, depending on Flags. |
| `DOUBLE` | Velocity X |
| `DOUBLE` | Velocity Y |
| `DOUBLE` | Velocity Z |
| `FLOAT` | Yaw: Absolute or relative rotation on the X axis, in degrees. |
| `FLOAT` | Pitch: Absolute or relative rotation on the Y axis, in degrees. |
| `TELEPORT_FLAGS` | Flags |

---

### PLAYER_ROTATION

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.21.2 - 1.21.4 | 0x43 | 67 |
| 1.21.5 - 1.21.8 | 0x42 | 66 |
| 1.21.9 | 0x47 | 71 |

**Packet Fields:**

| Type | Description |
| --- | --- |
| `FLOAT` | Yaw: Rotation on the X axis, in degrees. |
| `FLOAT` | Pitch: Rotation on the Y axis, in degrees. |
| `FLOAT` | Yaw: Rotation on the X axis, in degrees. |
| `FLOAT` | Pitch: Rotation on the Y axis, in degrees. |

---

### PLAYER_SLEEP

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.8 | 0xA | 10 |
| 1.9 - 1.12.0 | 0x2F | 47 |
| 1.12.1 | 0x30 | 48 |
| 1.13 | 0x33 | 51 |

---

### PONG_RESPONSE

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.20.2 - 1.20.4 | 0x34 | 52 |
| 1.20.5 - 1.21.1 | 0x36 | 54 |
| 1.21.2 - 1.21.4 | 0x38 | 56 |
| 1.21.5 - 1.21.8 | 0x37 | 55 |
| 1.21.9 | 0x3C | 60 |

**Packet Fields:**

| Type | Description |
| --- | --- |
| `LONG` | Timestamp: Should match the one sent by the client. |
| `LONG` | Payload: Should be the same as sent by the client. |

---

### PROJECTILE_POWER

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.20.5 - 1.21.1 | 0x79 | 121 |
| 1.21.2 - 1.21.8 | 0x80 | 128 |
| 1.21.9 | 0x85 | 133 |

**Packet Fields:**

| Type | Description |
| --- | --- |
| `VAR_INT` | Entity ID |
| `DOUBLE` | Power |
| `VAR_INT` | Entity ID |
| `DOUBLE` | Power |

---

### RECIPE

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.12 - 1.12.0 | 0x30 | 48 |
| 1.12.1 | 0x31 | 49 |
| 1.13 | 0x34 | 52 |
| 1.14 - 1.14.4 | 0x36 | 54 |
| 1.15 | 0x37 | 55 |
| 1.16 - 1.16.1 | 0x36 | 54 |
| 1.16.2 | 0x35 | 53 |
| 1.17 - 1.18 | 0x39 | 57 |
| 1.19 - 1.19.0 | 0x37 | 55 |
| 1.19.1 - 1.19.2 | 0x3A | 58 |
| 1.19.3 | 0x39 | 57 |
| 1.19.4 - 1.20.1 | 0x3D | 61 |
| 1.20.2 - 1.20.4 | 0x3F | 63 |
| 1.20.5 - 1.21 | 0x41 | 65 |

---

### RECIPE_BOOK_ADD

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.21.2 - 1.21.4 | 0x44 | 68 |
| 1.21.5 - 1.21.8 | 0x43 | 67 |
| 1.21.9 | 0x48 | 72 |

**Packet Fields:**

| Type | Description |
| --- | --- |
| `RECIPE_ID` | Recipes: Prefixed Array |
| `RECIPE_DISPLAY` | Display |
| `VAR_INT` | Group ID |
| `VAR_INT` | Category ID: ID in the minecraft:recipe_book_category registry. |
| `ARRAY` | Ingredients: IDs in the minecraft:item registry, or an inline definition. |
| `BYTE` | Flags: 0x01: show notification; 0x02: highlight as new |
| `BOOLEAN` | Replace: Replace or Add to known recipes |
| `RECIPE_ID` | Recipes: Prefixed Array |
| `RECIPE_DISPLAY` | Display |
| `VAR_INT` | Group ID |
| `VAR_INT` | Category ID: ID in the minecraft:recipe_book_category registry. |
| `ARRAY` | Ingredients: IDs in the minecraft:item registry, or an inline definition. |
| `BYTE` | Flags: 0x01: show notification; 0x02: highlight as new |
| `BOOLEAN` | Replace: Replace or Add to known recipes |

---

### RECIPE_BOOK_REMOVE

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.21.2 - 1.21.4 | 0x45 | 69 |
| 1.21.5 - 1.21.8 | 0x44 | 68 |
| 1.21.9 | 0x49 | 73 |

**Packet Fields:**

| Type | Description |
| --- | --- |
| `VAR_INT` | Recipes: IDs of recipes to remove. |
| `VAR_INT` | Recipes: IDs of recipes to remove. |

---

### RECIPE_BOOK_SETTINGS

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.21.2 - 1.21.4 | 0x46 | 70 |
| 1.21.5 - 1.21.8 | 0x45 | 69 |
| 1.21.9 | 0x4A | 74 |

**Packet Fields:**

| Type | Description |
| --- | --- |
| `BOOLEAN` | Crafting Recipe Book Open: If true, then the crafting recipe book will be open when the player opens its inventory. |
| `BOOLEAN` | Crafting Recipe Book Filter Active: If true, then the filtering option is active when the player opens its inventory. |
| `BOOLEAN` | Smelting Recipe Book Open: If true, then the smelting recipe book will be open when the player opens its inventory. |
| `BOOLEAN` | Smelting Recipe Book Filter Active: If true, then the filtering option is active when the player opens its inventory. |
| `BOOLEAN` | Blast Furnace Recipe Book Open: If true, then the blast furnace recipe book will be open when the player opens its inventory. |
| `BOOLEAN` | Blast Furnace Recipe Book Filter Active: If true, then the filtering option is active when the player opens its inventory. |
| `BOOLEAN` | Smoker Recipe Book Open: If true, then the smoker recipe book will be open when the player opens its inventory. |
| `BOOLEAN` | Smoker Recipe Book Filter Active: If true, then the filtering option is active when the player opens its inventory. |
| `BOOLEAN` | Crafting Recipe Book Open: If true, then the crafting recipe book will be open when the player opens its inventory. |
| `BOOLEAN` | Crafting Recipe Book Filter Active: If true, then the filtering option is active when the player opens its inventory. |
| `BOOLEAN` | Smelting Recipe Book Open: If true, then the smelting recipe book will be open when the player opens its inventory. |
| `BOOLEAN` | Smelting Recipe Book Filter Active: If true, then the filtering option is active when the player opens its inventory. |
| `BOOLEAN` | Blast Furnace Recipe Book Open: If true, then the blast furnace recipe book will be open when the player opens its inventory. |
| `BOOLEAN` | Blast Furnace Recipe Book Filter Active: If true, then the filtering option is active when the player opens its inventory. |
| `BOOLEAN` | Smoker Recipe Book Open: If true, then the smoker recipe book will be open when the player opens its inventory. |
| `BOOLEAN` | Smoker Recipe Book Filter Active: If true, then the filtering option is active when the player opens its inventory. |

---

### REMOVE_ENTITIES

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.8 | 0x13 | 19 |
| 1.9 - 1.11 | 0x30 | 48 |
| 1.12 - 1.12.0 | 0x31 | 49 |
| 1.12.1 | 0x32 | 50 |
| 1.13 | 0x35 | 53 |
| 1.14 - 1.14.4 | 0x37 | 55 |
| 1.15 | 0x38 | 56 |
| 1.16 - 1.16.1 | 0x37 | 55 |
| 1.16.2 - 1.17.0 | 0x36 | 54 |
| 1.17.1 - 1.18 | 0x3A | 58 |
| 1.19 - 1.19.0 | 0x38 | 56 |
| 1.19.1 - 1.19.2 | 0x3B | 59 |
| 1.19.3 | 0x3A | 58 |
| 1.19.4 - 1.20.1 | 0x3E | 62 |
| 1.20.2 - 1.20.4 | 0x40 | 64 |
| 1.20.5 - 1.21.1 | 0x42 | 66 |
| 1.21.2 - 1.21.4 | 0x47 | 71 |
| 1.21.5 - 1.21.8 | 0x46 | 70 |
| 1.21.9 | 0x4B | 75 |

**Description:**

Sent by the server when an entity is to be destroyed on the client.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `VAR_INT` | Entity IDs: The list of entities to destroy. |
| `VAR_INT` | Entity IDs: The list of entities to destroy. |

---

### REMOVE_ENTITY

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.17 | 0x3A | 58 |

---

### REMOVE_MOB_EFFECT

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.8 | 0x1E | 30 |
| 1.9 - 1.11 | 0x31 | 49 |
| 1.12 - 1.12.0 | 0x32 | 50 |
| 1.12.1 | 0x33 | 51 |
| 1.13 | 0x36 | 54 |
| 1.14 - 1.14.4 | 0x38 | 56 |
| 1.15 | 0x39 | 57 |
| 1.16 - 1.16.1 | 0x38 | 56 |
| 1.16.2 | 0x37 | 55 |
| 1.17 - 1.18 | 0x3B | 59 |
| 1.19 - 1.19.0 | 0x39 | 57 |
| 1.19.1 - 1.19.2 | 0x3C | 60 |
| 1.19.3 | 0x3B | 59 |
| 1.19.4 - 1.20.1 | 0x3F | 63 |
| 1.20.2 - 1.20.4 | 0x41 | 65 |
| 1.20.5 - 1.21.1 | 0x43 | 67 |
| 1.21.2 - 1.21.4 | 0x48 | 72 |
| 1.21.5 - 1.21.8 | 0x47 | 71 |
| 1.21.9 | 0x4C | 76 |

**Packet Fields:**

| Type | Description |
| --- | --- |
| `VAR_INT` | Entity ID |
| `VAR_INT` | Effect ID: See this table. |

---

### RESET_SCORE

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.20.3 - 1.20.4 | 0x42 | 66 |
| 1.20.5 - 1.21.1 | 0x44 | 68 |
| 1.21.2 - 1.21.4 | 0x49 | 73 |
| 1.21.5 - 1.21.8 | 0x48 | 72 |
| 1.21.9 | 0x4D | 77 |

**Description:**

This is sent to the client when it should remove a scoreboard item.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `STRING` | Entity Name: The entity whose score this is. For players, this is their username; for other entities, it is their UUID. |
| `STRING` | Objective Name: The name of the objective the score belongs to. |
| `STRING` | Entity Name: The entity whose score this is. For players, this is their username; for other entities, it is their UUID. |
| `STRING` | Objective Name: The name of the objective the score belongs to. |

---

### RESOURCE_PACK

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.8 | 0x48 | 72 |
| 1.9 - 1.11 | 0x32 | 50 |
| 1.12 - 1.12.0 | 0x33 | 51 |
| 1.12.1 | 0x34 | 52 |
| 1.13 | 0x37 | 55 |
| 1.14 - 1.14.4 | 0x39 | 57 |
| 1.15 | 0x3A | 58 |
| 1.16 - 1.16.1 | 0x39 | 57 |
| 1.16.2 | 0x38 | 56 |
| 1.17 - 1.18 | 0x3C | 60 |
| 1.19 - 1.19.0 | 0x3A | 58 |
| 1.19.1 - 1.19.2 | 0x3D | 61 |
| 1.19.3 | 0x3C | 60 |
| 1.19.4 - 1.20.1 | 0x40 | 64 |
| 1.20.2 | 0x42 | 66 |

---

### RESOURCE_PACK_POP

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.20.3 - 1.20.4 | 0x43 | 67 |
| 1.20.5 - 1.21.1 | 0x45 | 69 |
| 1.21.2 - 1.21.4 | 0x4A | 74 |
| 1.21.5 - 1.21.8 | 0x49 | 73 |
| 1.21.9 | 0x4E | 78 |

**Packet Fields:**

| Type | Description |
| --- | --- |
| `UUID` | UUID: The UUID of the resource pack to be removed. If not present, every resource pack will be removed. |
| `UUID` | UUID: The UUID of the resource pack to be removed. |

---

### RESOURCE_PACK_PUSH

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.20.3 - 1.20.4 | 0x44 | 68 |
| 1.20.5 - 1.21.1 | 0x46 | 70 |
| 1.21.2 - 1.21.4 | 0x4B | 75 |
| 1.21.5 - 1.21.8 | 0x4A | 74 |
| 1.21.9 | 0x4F | 79 |

**Packet Fields:**

| Type | Description |
| --- | --- |
| `UUID` | UUID: The unique identifier of the resource pack. |
| `STRING` | URL: The URL to the resource pack. |
| `STRING` | Hash: A 40 character hexadecimal, case-insensitive SHA-1 hash of the resource pack file.If it's not a 40-character hexadecimal string, the client will not use it for hash verification and likely waste bandwidth. |
| `BOOLEAN` | Forced: The vanilla client will be forced to use the resource pack from the server. If they decline, they will be kicked from the server. |
| `PREFIXED_OPTIONAL_TEXT_COMPONENT` | Prompt Message: This is shown in the prompt making the client accept or decline the resource pack (only if present). |
| `UUID` | UUID: The unique identifier of the resource pack. |
| `STRING` | URL: The URL to the resource pack. |
| `STRING` | Hash: A 40 character hexadecimal, case-insensitive SHA-1 hash of the resource pack file.If it's not a 40-character hexadecimal string, the client will not use it for hash verification and likely waste bandwidth. |
| `BOOLEAN` | Forced: The vanilla client will be forced to use the resource pack from the server. If they decline, they will be kicked from the server. |
| `PREFIXED_OPTIONAL_TEXT_COMPONENT` | Prompt Message: This is shown in the prompt making the client accept or decline the resource pack. |

---

### RESPAWN

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.8 | 0x7 | 7 |
| 1.9 - 1.11 | 0x33 | 51 |
| 1.12 - 1.12.0 | 0x34 | 52 |
| 1.12.1 | 0x35 | 53 |
| 1.13 | 0x38 | 56 |
| 1.14 - 1.14.4 | 0x3A | 58 |
| 1.15 | 0x3B | 59 |
| 1.16 - 1.16.1 | 0x3A | 58 |
| 1.16.2 | 0x39 | 57 |
| 1.17 - 1.18 | 0x3D | 61 |
| 1.19 - 1.19.0 | 0x3B | 59 |
| 1.19.1 - 1.19.2 | 0x3E | 62 |
| 1.19.3 | 0x3D | 61 |
| 1.19.4 - 1.20.1 | 0x41 | 65 |
| 1.20.2 | 0x43 | 67 |
| 1.20.3 - 1.20.4 | 0x45 | 69 |
| 1.20.5 - 1.21.1 | 0x47 | 71 |
| 1.21.2 - 1.21.4 | 0x4C | 76 |
| 1.21.5 - 1.21.8 | 0x4B | 75 |
| 1.21.9 | 0x50 | 80 |

**Description:**

To change the player's dimension (overworld/nether/end), send them a respawn packet with the appropriate dimension, followed by prechunks/chunks for the new dimension, and finally a position and look packet. You do not need to unload chunks; the client will do it automatically. The background of the loading screen is determined based on the Dimension Name specified in this packet and the one specified in the previous Login or Respawn packet. If either the current or the previous dimension is minecraft:nether, the Nether portal background is used. Otherwise, if the current or the previous dimension is minecraft:the_end, the End portal background is used. If the player is dead (health is 0), the default background is always used. In the vanilla implementation, this is context-dependent:

**Packet Fields:**

| Type | Description |
| --- | --- |
| `VAR_INT` | Dimension Type: The ID of type of dimension in the minecraft:dimension_type registry, defined by the Registry Data packet. |
| `STRING` | Dimension Name: Name of the dimension being spawned into. |
| `LONG` | Hashed seed: First 8 bytes of the SHA-256 hash of the world's seed. Used client-side for biome noise |
| `BYTE` | Game mode: 0: Survival, 1: Creative, 2: Adventure, 3: Spectator. |
| `BYTE` | Previous Game mode: -1: Undefined (null), 0: Survival, 1: Creative, 2: Adventure, 3: Spectator. The previous game mode. Vanilla client uses this for the debug (F3 + N & F3 + F4) game mode switch. (More information needed) |
| `BOOLEAN` | Is Debug: True if the world is a debug mode world; debug mode worlds cannot be modified and have predefined blocks. |
| `BOOLEAN` | Is Flat: True if the world is a superflat world; flat worlds have different void fog and a horizon at y=0 instead of y=63. |
| `BOOLEAN` | Has death location: If true, then the next two fields are present. |
| `STRING` | Death dimension Name: Name of the dimension the player died in. |
| `POSITION` | Death location: The location that the player died at. |
| `VAR_INT` | Portal cooldown: The number of ticks until the player can use the portal again. |
| `VAR_INT` | Sea level |
| `BYTE` | Data kept: Bit mask. 0x01: Keep attributes, 0x02: Keep metadata. Tells which data should be kept on the client side once the player has respawned.
In the vanilla implementation, this is context-dependent:

normal respawns (after death) keep no data;
exiting the end poem/credits keeps the attributes;
other dimension changes (portals or teleports) keep all data. |
| `VAR_INT` | Dimension Type: The ID of type of dimension in the minecraft:dimension_type registry, defined by the Registry Data packet. |
| `STRING` | Dimension Name: Name of the dimension being spawned into. |
| `LONG` | Hashed seed: First 8 bytes of the SHA-256 hash of the world's seed. Used client-side for biome noise |
| `BYTE` | Game mode: 0: Survival, 1: Creative, 2: Adventure, 3: Spectator. |
| `BYTE` | Previous Game mode: -1: Undefined (null), 0: Survival, 1: Creative, 2: Adventure, 3: Spectator. The previous game mode. Vanilla client uses this for the debug (F3 + N & F3 + F4) game mode switch. (More information needed) |
| `BOOLEAN` | Is Debug: True if the world is a debug mode world; debug mode worlds cannot be modified and have predefined blocks. |
| `BOOLEAN` | Is Flat: True if the world is a superflat world; flat worlds have different void fog and a horizon at y=0 instead of y=63. |
| `BOOLEAN` | Has death location: If true, then the next two fields are present. |
| `STRING` | Death dimension Name: Name of the dimension the player died in. |
| `POSITION` | Death location: The location that the player died at. |
| `VAR_INT` | Portal cooldown: The number of ticks until the player can use the portal again. |
| `VAR_INT` | Sea level |
| `BYTE` | Data kept: Bit mask. 0x01: Keep attributes, 0x02: Keep metadata. Tells which data should be kept on the client side once the player has respawned.
In the vanilla implementation, this is context-dependent:

normal respawns (after death) keep no data;
exiting the end poem/credits keeps the attributes;
other dimension changes (portals or teleports) keep all data. |

---

### ROTATE_HEAD

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.8 | 0x19 | 25 |
| 1.9 - 1.11 | 0x34 | 52 |
| 1.12 - 1.12.0 | 0x35 | 53 |
| 1.12.1 | 0x36 | 54 |
| 1.13 | 0x39 | 57 |
| 1.14 - 1.14.4 | 0x3B | 59 |
| 1.15 | 0x3C | 60 |
| 1.16 - 1.16.1 | 0x3B | 59 |
| 1.16.2 | 0x3A | 58 |
| 1.17 - 1.18 | 0x3E | 62 |
| 1.19 - 1.19.0 | 0x3C | 60 |
| 1.19.1 - 1.19.2 | 0x3F | 63 |
| 1.19.3 | 0x3E | 62 |
| 1.19.4 - 1.20.1 | 0x42 | 66 |
| 1.20.2 | 0x44 | 68 |
| 1.20.3 - 1.20.4 | 0x46 | 70 |
| 1.20.5 - 1.21.1 | 0x48 | 72 |
| 1.21.2 - 1.21.4 | 0x4D | 77 |
| 1.21.5 - 1.21.8 | 0x4C | 76 |
| 1.21.9 | 0x51 | 81 |

**Description:**

Changes the direction an entity's head is facing. While sending the Entity Look packet changes the vertical rotation of the head, sending this packet appears to be necessary to rotate the head horizontally.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `VAR_INT` | Entity ID |
| `BYTE` | Head Yaw: New angle, not a delta. |

---

### SECTION_BLOCKS_UPDATE

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.16.2 | 0x3B | 59 |
| 1.17 - 1.18 | 0x3F | 63 |
| 1.19 - 1.19.0 | 0x3D | 61 |
| 1.19.1 - 1.19.2 | 0x40 | 64 |
| 1.19.3 | 0x3F | 63 |
| 1.19.4 - 1.20.1 | 0x43 | 67 |
| 1.20.2 | 0x45 | 69 |
| 1.20.3 - 1.20.4 | 0x47 | 71 |
| 1.20.5 - 1.21.1 | 0x49 | 73 |
| 1.21.2 - 1.21.4 | 0x4E | 78 |
| 1.21.5 - 1.21.8 | 0x4D | 77 |
| 1.21.9 | 0x52 | 82 |

**Description:**

Fired whenever 2 or more blocks are changed within the same chunk on the same tick.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `LONG` | Chunk section position: Chunk section coordinate (encoded chunk x and z with each 22 bits, and section y with 20 bits, from left to right). |
| `VAR_LONG` | Blocks: Each entry is composed of the block state id, shifted left by 12, and the relative block position in the chunk section (4 bits for x, z, and y, from left to right). |

---

### SELECT_ADVANCEMENTS_TAB

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.12 - 1.12.0 | 0x36 | 54 |
| 1.12.1 | 0x37 | 55 |
| 1.13 | 0x3A | 58 |
| 1.14 - 1.14.4 | 0x3C | 60 |
| 1.15 | 0x3D | 61 |
| 1.16 - 1.16.2 | 0x3C | 60 |
| 1.17 - 1.18 | 0x40 | 64 |
| 1.19 - 1.19.0 | 0x3E | 62 |
| 1.19.1 - 1.19.2 | 0x41 | 65 |
| 1.19.3 | 0x40 | 64 |
| 1.19.4 - 1.20.1 | 0x44 | 68 |
| 1.20.2 | 0x46 | 70 |
| 1.20.3 - 1.20.4 | 0x48 | 72 |
| 1.20.5 - 1.21.1 | 0x4A | 74 |
| 1.21.2 - 1.21.4 | 0x4F | 79 |
| 1.21.5 - 1.21.8 | 0x4E | 78 |
| 1.21.9 | 0x53 | 83 |

**Description:**

Sent by the server to indicate that the client should switch advancement tab. Sent either when the client switches tab in the GUI or when an advancement is made in another tab.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `STRING` | Identifier: See below. |
| `STRING` | Identifier: See below. |

---

### SERVER_DATA

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.19 - 1.19.0 | 0x3F | 63 |
| 1.19.1 - 1.19.2 | 0x42 | 66 |
| 1.19.3 | 0x41 | 65 |
| 1.19.4 - 1.20.1 | 0x45 | 69 |
| 1.20.2 | 0x47 | 71 |
| 1.20.3 - 1.20.4 | 0x49 | 73 |
| 1.20.5 - 1.21.1 | 0x4B | 75 |
| 1.21.2 - 1.21.4 | 0x50 | 80 |
| 1.21.5 - 1.21.8 | 0x4F | 79 |
| 1.21.9 | 0x54 | 84 |

**Packet Fields:**

| Type | Description |
| --- | --- |
| `TEXT_COMPONENT` | MOTD |
| `BYTE` | Icon: Icon bytes in the PNG format. |
| `TEXT_COMPONENT` | MOTD |
| `BYTE` | Icon: Icon bytes in the PNG format. |

---

### SERVER_LINKS

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.21 - 1.21.1 | 0x7B | 123 |
| 1.21.2 - 1.21.8 | 0x82 | 130 |
| 1.21.9 | 0x87 | 135 |

**Description:**

This packet contains a list of links that the vanilla client will display in the menu available from the pause menu. Link labels can be built-in or custom (i.e., any text).

**Packet Fields:**

| Type | Description |
| --- | --- |
| `LABEL` | Links: Prefixed Array |
| `STRING` | URL: Valid URL. |
| `IS_BUILTIN` | Links: Prefixed Array |
| `VAR_INT` | Label: See below. |
| `STRING` | URL: Valid URL. |
| `IS_BUILTIN` | Links: Prefixed Array |
| `VAR_INT` | Label: See below. |
| `STRING` | URL: Valid URL. |

---

### SET_ACTION_BAR_TEXT

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.17 - 1.18 | 0x41 | 65 |
| 1.19 - 1.19.0 | 0x40 | 64 |
| 1.19.1 - 1.19.2 | 0x43 | 67 |
| 1.19.3 | 0x42 | 66 |
| 1.19.4 - 1.20.1 | 0x46 | 70 |
| 1.20.2 | 0x48 | 72 |
| 1.20.3 - 1.20.4 | 0x4A | 74 |
| 1.20.5 - 1.21.1 | 0x4C | 76 |
| 1.21.2 - 1.21.4 | 0x51 | 81 |
| 1.21.5 - 1.21.8 | 0x50 | 80 |
| 1.21.9 | 0x55 | 85 |

**Description:**

Displays a message above the hotbar. Equivalent to System Chat Message with Overlay set to true, except that chat message blocking isn't performed. Used by the vanilla server only to implement the /title command.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `ACTION_BAR_TEXT` | Client: Text Component |
| `ACTION_BAR_TEXT` | Client: Text Component |

---

### SET_BORDER

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.8 | 0x44 | 68 |
| 1.9 - 1.11 | 0x35 | 53 |
| 1.12 - 1.12.0 | 0x37 | 55 |
| 1.12.1 | 0x38 | 56 |
| 1.13 | 0x3B | 59 |
| 1.14 - 1.14.4 | 0x3D | 61 |
| 1.15 | 0x3E | 62 |
| 1.16 - 1.16.2 | 0x3D | 61 |

---

### SET_BORDER_CENTER

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.17 - 1.18 | 0x42 | 66 |
| 1.19 - 1.19.0 | 0x41 | 65 |
| 1.19.1 - 1.19.2 | 0x44 | 68 |
| 1.19.3 | 0x43 | 67 |
| 1.19.4 - 1.20.1 | 0x47 | 71 |
| 1.20.2 | 0x49 | 73 |
| 1.20.3 - 1.20.4 | 0x4B | 75 |
| 1.20.5 - 1.21.1 | 0x4D | 77 |
| 1.21.2 - 1.21.4 | 0x52 | 82 |
| 1.21.5 - 1.21.8 | 0x51 | 81 |
| 1.21.9 | 0x56 | 86 |

**Packet Fields:**

| Type | Description |
| --- | --- |
| `DOUBLE` | X |
| `DOUBLE` | Z |
| `DOUBLE` | X |
| `DOUBLE` | Z |

---

### SET_BORDER_LERP_SIZE

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.17 - 1.18 | 0x43 | 67 |
| 1.19 - 1.19.0 | 0x42 | 66 |
| 1.19.1 - 1.19.2 | 0x45 | 69 |
| 1.19.3 | 0x44 | 68 |
| 1.19.4 - 1.20.1 | 0x48 | 72 |
| 1.20.2 | 0x4A | 74 |
| 1.20.3 - 1.20.4 | 0x4C | 76 |
| 1.20.5 - 1.21.1 | 0x4E | 78 |
| 1.21.2 - 1.21.4 | 0x53 | 83 |
| 1.21.5 - 1.21.8 | 0x52 | 82 |
| 1.21.9 | 0x57 | 87 |

**Packet Fields:**

| Type | Description |
| --- | --- |
| `DOUBLE` | Old Diameter: Current length of a single side of the world border, in meters. |
| `DOUBLE` | New Diameter: Target length of a single side of the world border, in meters. |
| `VAR_LONG` | Speed: Number of real-time milliseconds until New Diameter is reached. It appears that vanilla server does not sync world border speed to game ticks, so it gets out of sync with server lag. If the world border is not moving, this is set to 0. |
| `DOUBLE` | Old Diameter: Current length of a single side of the world border, in meters. |
| `DOUBLE` | New Diameter: Target length of a single side of the world border, in meters. |
| `VAR_LONG` | Speed: Number of real-time milliseconds until New Diameter is reached. It appears that vanilla server does not sync world border speed to game ticks, so it gets out of sync with server lag. If the world border is not moving, this is set to 0. |

---

### SET_BORDER_SIZE

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.17 - 1.18 | 0x44 | 68 |
| 1.19 - 1.19.0 | 0x43 | 67 |
| 1.19.1 - 1.19.2 | 0x46 | 70 |
| 1.19.3 | 0x45 | 69 |
| 1.19.4 - 1.20.1 | 0x49 | 73 |
| 1.20.2 | 0x4B | 75 |
| 1.20.3 - 1.20.4 | 0x4D | 77 |
| 1.20.5 - 1.21.1 | 0x4F | 79 |
| 1.21.2 - 1.21.4 | 0x54 | 84 |
| 1.21.5 - 1.21.8 | 0x53 | 83 |
| 1.21.9 | 0x58 | 88 |

**Packet Fields:**

| Type | Description |
| --- | --- |
| `DOUBLE` | Diameter: Length of a single side of the world border, in meters. |
| `DOUBLE` | Diameter: Length of a single side of the world border, in meters. |

---

### SET_BORDER_WARNING_DELAY

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.17 - 1.18 | 0x45 | 69 |
| 1.19 - 1.19.0 | 0x44 | 68 |
| 1.19.1 - 1.19.2 | 0x47 | 71 |
| 1.19.3 | 0x46 | 70 |
| 1.19.4 - 1.20.1 | 0x4A | 74 |
| 1.20.2 | 0x4C | 76 |
| 1.20.3 - 1.20.4 | 0x4E | 78 |
| 1.20.5 - 1.21.1 | 0x50 | 80 |
| 1.21.2 - 1.21.4 | 0x55 | 85 |
| 1.21.5 - 1.21.8 | 0x54 | 84 |
| 1.21.9 | 0x59 | 89 |

**Packet Fields:**

| Type | Description |
| --- | --- |
| `VAR_INT` | Warning Time: In seconds as set by /worldborder warning time. |
| `VAR_INT` | Warning Time: In seconds as set by /worldborder warning time. |

---

### SET_BORDER_WARNING_DISTANCE

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.17 - 1.18 | 0x46 | 70 |
| 1.19 - 1.19.0 | 0x45 | 69 |
| 1.19.1 - 1.19.2 | 0x48 | 72 |
| 1.19.3 | 0x47 | 71 |
| 1.19.4 - 1.20.1 | 0x4B | 75 |
| 1.20.2 | 0x4D | 77 |
| 1.20.3 - 1.20.4 | 0x4F | 79 |
| 1.20.5 - 1.21.1 | 0x51 | 81 |
| 1.21.2 - 1.21.4 | 0x56 | 86 |
| 1.21.5 - 1.21.8 | 0x55 | 85 |
| 1.21.9 | 0x5A | 90 |

**Packet Fields:**

| Type | Description |
| --- | --- |
| `VAR_INT` | Warning Blocks: In meters. |
| `VAR_INT` | Warning Blocks: In meters. |

---

### SET_CAMERA

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.8 | 0x43 | 67 |
| 1.9 - 1.11 | 0x36 | 54 |
| 1.12 - 1.12.0 | 0x38 | 56 |
| 1.12.1 | 0x39 | 57 |
| 1.13 | 0x3C | 60 |
| 1.14 - 1.14.4 | 0x3E | 62 |
| 1.15 | 0x3F | 63 |
| 1.16 - 1.16.2 | 0x3E | 62 |
| 1.17 - 1.18 | 0x47 | 71 |
| 1.19 - 1.19.0 | 0x46 | 70 |
| 1.19.1 - 1.19.2 | 0x49 | 73 |
| 1.19.3 | 0x48 | 72 |
| 1.19.4 - 1.20.1 | 0x4C | 76 |
| 1.20.2 | 0x4E | 78 |
| 1.20.3 - 1.20.4 | 0x50 | 80 |
| 1.20.5 - 1.21.1 | 0x52 | 82 |
| 1.21.2 - 1.21.4 | 0x57 | 87 |
| 1.21.5 - 1.21.8 | 0x56 | 86 |
| 1.21.9 | 0x5B | 91 |

**Description:**

Sets the entity that the player renders from. This is normally used when the player left-clicks an entity while in spectator mode. The player's camera will move with the entity and look where it is looking. The entity is often another player, but can be any type of entity.  The player is unable to move this entity (move packets will act as if they are coming from the other entity). If the given entity is not loaded by the player, this packet is ignored.  To return control to the player, send this packet with their entity ID. The vanilla server resets this (sends it back to the default entity) whenever the spectated entity is killed or the player sneaks, but only if they were spectating an entity. It also sends this packet whenever the player switches out of spectator mode (even if they weren't spectating an entity).

**Packet Fields:**

| Type | Description |
| --- | --- |
| `VAR_INT` | Camera ID: ID of the entity to set the client's camera to. |
| `VAR_INT` | Camera ID: ID of the entity to set the client's camera to. |

---

### SET_CARRIED_ITEM

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.8 | 0x9 | 9 |
| 1.9 - 1.11 | 0x37 | 55 |
| 1.12 - 1.12.0 | 0x39 | 57 |
| 1.12.1 | 0x3A | 58 |
| 1.13 | 0x3D | 61 |
| 1.14 - 1.14.4 | 0x3F | 63 |
| 1.15 | 0x40 | 64 |
| 1.16 - 1.16.2 | 0x3F | 63 |
| 1.17 - 1.18 | 0x48 | 72 |
| 1.19 - 1.19.0 | 0x47 | 71 |
| 1.19.1 - 1.19.2 | 0x4A | 74 |
| 1.19.3 | 0x49 | 73 |
| 1.19.4 - 1.20.1 | 0x4D | 77 |
| 1.20.2 | 0x4F | 79 |
| 1.20.3 - 1.20.4 | 0x51 | 81 |
| 1.20.5 - 1.21 | 0x53 | 83 |

---

### SET_CHUNK_CACHE_CENTER

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.14 - 1.14.4 | 0x40 | 64 |
| 1.15 | 0x41 | 65 |
| 1.16 - 1.16.2 | 0x40 | 64 |
| 1.17 - 1.18 | 0x49 | 73 |
| 1.19 - 1.19.0 | 0x48 | 72 |
| 1.19.1 - 1.19.2 | 0x4B | 75 |
| 1.19.3 | 0x4A | 74 |
| 1.19.4 - 1.20.1 | 0x4E | 78 |
| 1.20.2 | 0x50 | 80 |
| 1.20.3 - 1.20.4 | 0x52 | 82 |
| 1.20.5 - 1.21.1 | 0x54 | 84 |
| 1.21.2 - 1.21.4 | 0x58 | 88 |
| 1.21.5 - 1.21.8 | 0x57 | 87 |
| 1.21.9 | 0x5C | 92 |

**Description:**

Sets the center position of the client's chunk loading area. The area is square-shaped, spanning 2 × server view distance + 7 chunks on both axes (width, not radius!). Since the area's width is always an odd number, there is no ambiguity as to which chunk is the center. The vanilla client never renders or simulates chunks located outside the loading area, but keeps them in memory (unless explicitly unloaded by the server while still in range), and only automatically unloads a chunk when another chunk is loaded at coordinates congruent to the old chunk's coordinates modulo (2 × server view distance + 7). This means that a chunk may reappear after leaving and later re-entering the loading area through successive uses of this packet, unless it is replaced in the meantime by a different chunk in the same "slot". The vanilla client ignores attempts to load or unload chunks located outside the loading area. This applies even to unloads targeting chunks that are still loaded, but currently located outside the loading area (per the previous paragraph). The vanilla server does not rely on any specific behavior for chunks leaving the loading area, and custom clients need not replicate the above exactly. A client may instead choose to immediately unload any chunks outside the loading area, to use a different modulus, or to ignore the loading area completely and keep chunks loaded regardless of their location until the server requests to unload them. Servers aiming for maximal interoperability should always explicitly unload any loaded chunks before they go outside the loading area. The center chunk is normally the chunk the player is in, but apart from the implications on chunk loading, the (vanilla) client takes no issue with this not being the case. Indeed, as long as chunks are sent only within the default loading area centered on the world origin, it is not necessary to send this packet at all. This may be useful for servers with small bounded worlds, such as minigames, since it ensures chunks never need to be resent after the client has joined, saving on bandwidth. The vanilla server sends this packet whenever the player moves across a chunk border horizontally, and also (according to testing) for any integer change in the vertical axis, even if it doesn't go across a chunk section border.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `VAR_INT` | Chunk X: Chunk X coordinate of the loading area center. |
| `VAR_INT` | Chunk Z: Chunk Z coordinate of the loading area center. |

---

### SET_CHUNK_CACHE_RADIUS

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.14 - 1.14.4 | 0x41 | 65 |
| 1.15 | 0x42 | 66 |
| 1.16 - 1.16.2 | 0x41 | 65 |
| 1.17 - 1.18 | 0x4A | 74 |
| 1.19 - 1.19.0 | 0x49 | 73 |
| 1.19.1 - 1.19.2 | 0x4C | 76 |
| 1.19.3 | 0x4B | 75 |
| 1.19.4 - 1.20.1 | 0x4F | 79 |
| 1.20.2 | 0x51 | 81 |
| 1.20.3 - 1.20.4 | 0x53 | 83 |
| 1.20.5 - 1.21.1 | 0x55 | 85 |
| 1.21.2 - 1.21.4 | 0x59 | 89 |
| 1.21.5 - 1.21.8 | 0x58 | 88 |
| 1.21.9 | 0x5D | 93 |

**Description:**

Sent by the integrated singleplayer server when changing render distance.  This packet is sent by the server when the client reappears in the overworld after leaving the end.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `VAR_INT` | View Distance: Render distance (2-32). |

---

### SET_COMPRESSION

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.8 | 0x46 | 70 |

**Description:**

Enables compression.  If compression is enabled, all following packets are encoded in the compressed packet format.  Negative values will disable compression, meaning the packet format should remain in the uncompressed packet format.  However, this packet is entirely optional, and if not sent, compression will also not be enabled (the vanilla server does not send the packet when compression is disabled).

**Packet Fields:**

| Type | Description |
| --- | --- |
| `VAR_INT` | Threshold: Maximum size of a packet before it is compressed. |

---

### SET_CURSOR_ITEM

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.21.2 - 1.21.4 | 0x5A | 90 |
| 1.21.5 - 1.21.8 | 0x59 | 89 |
| 1.21.9 | 0x5E | 94 |

**Description:**

Replaces or sets the inventory item that's being dragged with the mouse.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `SLOT` | Carried item |
| `SLOT` | Carried item |

---

### SET_DEFAULT_SPAWN_POSITION

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.8 | 0x5 | 5 |
| 1.9 - 1.11 | 0x43 | 67 |
| 1.12 - 1.12.0 | 0x45 | 69 |
| 1.12.1 | 0x46 | 70 |
| 1.13 | 0x49 | 73 |
| 1.14 - 1.14.4 | 0x4D | 77 |
| 1.15 | 0x4E | 78 |
| 1.16 - 1.16.2 | 0x42 | 66 |
| 1.17 - 1.18 | 0x4B | 75 |
| 1.19 - 1.19.0 | 0x4A | 74 |
| 1.19.1 - 1.19.2 | 0x4D | 77 |
| 1.19.3 | 0x4C | 76 |
| 1.19.4 - 1.20.1 | 0x50 | 80 |
| 1.20.2 | 0x52 | 82 |
| 1.20.3 - 1.20.4 | 0x54 | 84 |
| 1.20.5 - 1.21.1 | 0x56 | 86 |
| 1.21.2 - 1.21.4 | 0x5B | 91 |
| 1.21.5 - 1.21.8 | 0x5A | 90 |
| 1.21.9 | 0x5F | 95 |

**Description:**

Sent by the server after login to specify the coordinates of the spawn point (the point at which players spawn at, and which the compass points to). It can be sent at any time to update the point compasses point at. Before receiving this packet, the client uses the default position 8, 64, 8, and angle 0.0.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `POSITION` | Location: Spawn location. |
| `FLOAT` | Angle: The angle at which to respawn. |
| `POSITION` | Location: Spawn location. |
| `FLOAT` | Angle: The angle at which to respawn. |

---

### SET_DISPLAY_CHAT_PREVIEW

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.19 - 1.19.0 | 0x4B | 75 |
| 1.19.1 | 0x4E | 78 |

---

### SET_DISPLAY_OBJECTIVE

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.8 | 0x3D | 61 |
| 1.9 - 1.11 | 0x38 | 56 |
| 1.12 - 1.12.0 | 0x3A | 58 |
| 1.12.1 | 0x3B | 59 |
| 1.13 | 0x3E | 62 |
| 1.14 - 1.14.4 | 0x42 | 66 |
| 1.15 - 1.16.2 | 0x43 | 67 |
| 1.17 - 1.19.0 | 0x4C | 76 |
| 1.19.1 - 1.19.2 | 0x4F | 79 |
| 1.19.3 | 0x4D | 77 |
| 1.19.4 - 1.20.1 | 0x51 | 81 |
| 1.20.2 | 0x53 | 83 |
| 1.20.3 - 1.20.4 | 0x55 | 85 |
| 1.20.5 - 1.21.1 | 0x57 | 87 |
| 1.21.2 - 1.21.4 | 0x5C | 92 |
| 1.21.5 - 1.21.8 | 0x5B | 91 |
| 1.21.9 | 0x60 | 96 |

**Description:**

This is sent to the client when it should display a scoreboard.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `VAR_INT` | Position: The position of the scoreboard. 0: list, 1: sidebar, 2: below name, 3 - 18: team-specific sidebar, indexed as 3 + team color. |
| `STRING` | Score Name: The unique name for the scoreboard to be displayed. |

---

### SET_ENTITY_DATA

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.8 | 0x1C | 28 |
| 1.9 - 1.11 | 0x39 | 57 |
| 1.12 - 1.12.0 | 0x3B | 59 |
| 1.12.1 | 0x3C | 60 |
| 1.13 | 0x3F | 63 |
| 1.14 - 1.14.4 | 0x43 | 67 |
| 1.15 - 1.16.2 | 0x44 | 68 |
| 1.17 - 1.19.0 | 0x4D | 77 |
| 1.19.1 - 1.19.2 | 0x50 | 80 |
| 1.19.3 | 0x4E | 78 |
| 1.19.4 - 1.20.1 | 0x52 | 82 |
| 1.20.2 | 0x54 | 84 |
| 1.20.3 - 1.20.4 | 0x56 | 86 |
| 1.20.5 - 1.21.1 | 0x58 | 88 |
| 1.21.2 - 1.21.4 | 0x5D | 93 |
| 1.21.5 - 1.21.8 | 0x5C | 92 |
| 1.21.9 | 0x61 | 97 |

**Description:**

Updates one or more metadata properties for an existing entity. Any properties not included in the Metadata field are left unchanged.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `VAR_INT` | Entity ID |
| `ENTITY_METADATA` | Metadata |

---

### SET_ENTITY_LINK

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.8 | 0x1B | 27 |
| 1.9 - 1.11 | 0x3A | 58 |
| 1.12 - 1.12.0 | 0x3C | 60 |
| 1.12.1 | 0x3D | 61 |
| 1.13 | 0x40 | 64 |
| 1.14 - 1.14.4 | 0x44 | 68 |
| 1.15 - 1.16.2 | 0x45 | 69 |
| 1.17 - 1.19.0 | 0x4E | 78 |
| 1.19.1 - 1.19.2 | 0x51 | 81 |
| 1.19.3 | 0x4F | 79 |
| 1.19.4 - 1.20.1 | 0x53 | 83 |
| 1.20.2 | 0x55 | 85 |
| 1.20.3 - 1.20.4 | 0x57 | 87 |
| 1.20.5 - 1.21.1 | 0x59 | 89 |
| 1.21.2 - 1.21.4 | 0x5E | 94 |
| 1.21.5 - 1.21.8 | 0x5D | 93 |
| 1.21.9 | 0x62 | 98 |

**Description:**

This packet is sent when an entity has been leashed to another entity.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `INT` | Attached Entity ID: Attached entity's EID. |
| `INT` | Holding Entity ID: ID of the entity holding the lead. Set to -1 to detach. |

---

### SET_ENTITY_MOTION

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.8 | 0x12 | 18 |
| 1.9 - 1.11 | 0x3B | 59 |
| 1.12 - 1.12.0 | 0x3D | 61 |
| 1.12.1 | 0x3E | 62 |
| 1.13 | 0x41 | 65 |
| 1.14 - 1.14.4 | 0x45 | 69 |
| 1.15 - 1.16.2 | 0x46 | 70 |
| 1.17 - 1.19.0 | 0x4F | 79 |
| 1.19.1 - 1.19.2 | 0x52 | 82 |
| 1.19.3 | 0x50 | 80 |
| 1.19.4 - 1.20.1 | 0x54 | 84 |
| 1.20.2 | 0x56 | 86 |
| 1.20.3 - 1.20.4 | 0x58 | 88 |
| 1.20.5 - 1.21.1 | 0x5A | 90 |
| 1.21.2 - 1.21.4 | 0x5F | 95 |
| 1.21.5 - 1.21.8 | 0x5E | 94 |
| 1.21.9 | 0x63 | 99 |

**Description:**

Velocity is in units of 1/8000 of a block per server tick (50ms); for example, -1343 would move (-1343 / 8000) = −0.167875 blocks per tick (or −3.3575 blocks per second).

**Packet Fields:**

| Type | Description |
| --- | --- |
| `VAR_INT` | Entity ID |
| `SHORT` | Velocity X: Velocity on the X axis. |
| `SHORT` | Velocity Y: Velocity on the Y axis. |
| `SHORT` | Velocity Z: Velocity on the Z axis. |

---

### SET_EQUIPMENT

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.16 - 1.16.2 | 0x47 | 71 |
| 1.17 - 1.19.0 | 0x50 | 80 |
| 1.19.1 - 1.19.2 | 0x53 | 83 |
| 1.19.3 | 0x51 | 81 |
| 1.19.4 - 1.20.1 | 0x55 | 85 |
| 1.20.2 | 0x57 | 87 |
| 1.20.3 - 1.20.4 | 0x59 | 89 |
| 1.20.5 - 1.21.1 | 0x5B | 91 |
| 1.21.2 - 1.21.4 | 0x60 | 96 |
| 1.21.5 - 1.21.8 | 0x5F | 95 |
| 1.21.9 | 0x64 | 100 |

**Description:**

Equipment slot can be one of the following:

**Packet Fields:**

| Type | Description |
| --- | --- |
| `VAR_INT` | Entity ID: Entity's ID. |
| `THE_LENGTH_OF_THE_ARRAY_IS_NOT_KNOWN_BEFOREHAND_AND_HAS_TO_BE_DETERMINED_BY_READING_ALL_ENTRIES_AS_THE_MOST_SIGNIFICANT_BIT_OF_THE_SLOT_INDICATES_IF_THERE_IS_A_NEXT_ENTRY` | Byte Enum: Equipment slot (see below).  Also has the top bit set if another entry follows, and otherwise unset if this is the last item in the array. |
| `SLOT` | Item |
| `VAR_INT` | Entity ID: Entity's ID. |
| `THE_LENGTH_OF_THE_ARRAY_IS_NOT_KNOWN_BEFOREHAND_AND_HAS_TO_BE_DETERMINED_BY_READING_ALL_ENTRIES_AS_THE_MOST_SIGNIFICANT_BIT_OF_THE_SLOT_INDICATES_IF_THERE_IS_A_NEXT_ENTRY` | Byte Enum: Equipment slot (see below).  Also has the top bit set if another entry follows, and otherwise unset if this is the last item in the array. |
| `SLOT` | Item |

---

### SET_EQUIPPED_ITEM

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.8 | 0x4 | 4 |
| 1.9 - 1.11 | 0x3C | 60 |
| 1.12 - 1.12.0 | 0x3E | 62 |
| 1.12.1 | 0x3F | 63 |
| 1.13 | 0x42 | 66 |
| 1.14 - 1.14.4 | 0x46 | 70 |
| 1.15 | 0x47 | 71 |

---

### SET_EXPERIENCE

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.8 | 0x1F | 31 |
| 1.9 - 1.11 | 0x3D | 61 |
| 1.12 - 1.12.0 | 0x3F | 63 |
| 1.12.1 | 0x40 | 64 |
| 1.13 | 0x43 | 67 |
| 1.14 - 1.14.4 | 0x47 | 71 |
| 1.15 - 1.16.2 | 0x48 | 72 |
| 1.17 - 1.19.0 | 0x51 | 81 |
| 1.19.1 - 1.19.2 | 0x54 | 84 |
| 1.19.3 | 0x52 | 82 |
| 1.19.4 - 1.20.1 | 0x56 | 86 |
| 1.20.2 | 0x58 | 88 |
| 1.20.3 - 1.20.4 | 0x5A | 90 |
| 1.20.5 - 1.21.1 | 0x5C | 92 |
| 1.21.2 - 1.21.4 | 0x61 | 97 |
| 1.21.5 - 1.21.8 | 0x60 | 96 |
| 1.21.9 | 0x65 | 101 |

**Description:**

Sent by the server when the client should change experience levels.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `FLOAT` | Experience bar: Between 0 and 1. |
| `VAR_INT` | Level |
| `VAR_INT` | Total Experience: See Experience#Leveling up on the Minecraft Wiki for Total Experience to Level conversion. |
| `FLOAT` | Experience bar: Between 0 and 1. |
| `VAR_INT` | Level |
| `VAR_INT` | Total Experience: See Experience#Leveling up on the Minecraft Wiki for Total Experience to Level conversion. |

---

### SET_HEALTH

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.8 | 0x6 | 6 |
| 1.9 - 1.11 | 0x3E | 62 |
| 1.12 - 1.12.0 | 0x40 | 64 |
| 1.12.1 | 0x41 | 65 |
| 1.13 | 0x44 | 68 |
| 1.14 - 1.14.4 | 0x48 | 72 |
| 1.15 - 1.16.2 | 0x49 | 73 |
| 1.17 - 1.19.0 | 0x52 | 82 |
| 1.19.1 - 1.19.2 | 0x55 | 85 |
| 1.19.3 | 0x53 | 83 |
| 1.19.4 - 1.20.1 | 0x57 | 87 |
| 1.20.2 | 0x59 | 89 |
| 1.20.3 - 1.20.4 | 0x5B | 91 |
| 1.20.5 - 1.21.1 | 0x5D | 93 |
| 1.21.2 - 1.21.4 | 0x62 | 98 |
| 1.21.5 - 1.21.8 | 0x61 | 97 |
| 1.21.9 | 0x66 | 102 |

**Description:**

Sent by the server to set the health of the player it is sent to. Food saturation acts as a food “overcharge”. Food values will not decrease while the saturation is over zero. New players logging in or respawning automatically get a saturation of 5.0. Eating food increases the saturation as well as the food bar.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `FLOAT` | Health: 0 or less = dead, 20 = full HP. |
| `VAR_INT` | Food: 0–20. |
| `FLOAT` | Food Saturation: Seems to vary from 0.0 to 5.0 in integer increments. |
| `FLOAT` | Health: 0 or less = dead, 20 = full HP. |
| `VAR_INT` | Food: 0–20. |
| `FLOAT` | Food Saturation: Seems to vary from 0.0 to 5.0 in integer increments. |

---

### SET_HELD_SLOT

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.21.2 - 1.21.4 | 0x63 | 99 |
| 1.21.5 - 1.21.8 | 0x62 | 98 |
| 1.21.9 | 0x67 | 103 |

**Description:**

Sent to change the player's slot selection.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `VAR_INT` | Slot: The slot which the player has selected (0–8). |

---

### SET_OBJECTIVE

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.8 | 0x3B | 59 |
| 1.9 - 1.11 | 0x3F | 63 |
| 1.12 - 1.12.0 | 0x41 | 65 |
| 1.12.1 | 0x42 | 66 |
| 1.13 | 0x45 | 69 |
| 1.14 - 1.14.4 | 0x49 | 73 |
| 1.15 - 1.16.2 | 0x4A | 74 |
| 1.17 - 1.19.0 | 0x53 | 83 |
| 1.19.1 - 1.19.2 | 0x56 | 86 |
| 1.19.3 | 0x54 | 84 |
| 1.19.4 - 1.20.1 | 0x58 | 88 |
| 1.20.2 | 0x5A | 90 |
| 1.20.3 - 1.20.4 | 0x5C | 92 |
| 1.20.5 - 1.21.1 | 0x5E | 94 |
| 1.21.2 - 1.21.4 | 0x64 | 100 |
| 1.21.5 - 1.21.8 | 0x63 | 99 |
| 1.21.9 | 0x68 | 104 |

**Description:**

This is sent to the client when it should create a new scoreboard objective or remove one.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `STRING` | Objective Name: A unique name for the objective. |
| `BYTE` | Mode: 0 to create the scoreboard. 1 to remove the scoreboard. 2 to update the display text. |
| `OPTIONAL_TEXT_COMPONENT` | Objective Value: Only if mode is 0 or 2.The text to be displayed for the score. |
| `VAR_INT` | Type: Only if mode is 0 or 2. 0 = "integer", 1 = "hearts". |
| `BOOLEAN` | Has Number Format: Only if mode is 0 or 2. Whether this objective has a set number format for the scores. |
| `VAR_INT` | Number Format: Only if mode is 0 or 2 and the previous boolean is true. Determines how the score number should be formatted. |
| `NO_FIELDS` | 0: blank: Show nothing. |
| `COMPOUND_TAG` | Styling: The styling to be used when formatting the score number. Contains the text component styling fields. |
| `TEXT_COMPONENT` | Content: The text to be used as placeholder. |

---

### SET_PASSENGERS

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.9 - 1.11 | 0x40 | 64 |
| 1.12 - 1.12.0 | 0x42 | 66 |
| 1.12.1 | 0x43 | 67 |
| 1.13 | 0x46 | 70 |
| 1.14 - 1.14.4 | 0x4A | 74 |
| 1.15 - 1.16.2 | 0x4B | 75 |
| 1.17 - 1.19.0 | 0x54 | 84 |
| 1.19.1 - 1.19.2 | 0x57 | 87 |
| 1.19.3 | 0x55 | 85 |
| 1.19.4 - 1.20.1 | 0x59 | 89 |
| 1.20.2 | 0x5B | 91 |
| 1.20.3 - 1.20.4 | 0x5D | 93 |
| 1.20.5 - 1.21.1 | 0x5F | 95 |
| 1.21.2 - 1.21.4 | 0x65 | 101 |
| 1.21.5 - 1.21.8 | 0x64 | 100 |
| 1.21.9 | 0x69 | 105 |

**Packet Fields:**

| Type | Description |
| --- | --- |
| `VAR_INT` | Entity ID: Vehicle's EID. |
| `VAR_INT` | Passengers: EIDs of entity's passengers. |
| `VAR_INT` | Entity ID: Vehicle's EID. |
| `VAR_INT` | Passengers: EIDs of entity's passengers. |

---

### SET_PLAYER_INVENTORY

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.21.2 - 1.21.4 | 0x66 | 102 |
| 1.21.5 - 1.21.8 | 0x65 | 101 |
| 1.21.9 | 0x6A | 106 |

**Packet Fields:**

| Type | Description |
| --- | --- |
| `VAR_INT` | Slot |
| `SLOT` | Slot Data |

---

### SET_PLAYER_TEAM

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.8 | 0x3E | 62 |
| 1.9 - 1.11 | 0x41 | 65 |
| 1.12 - 1.12.0 | 0x43 | 67 |
| 1.12.1 | 0x44 | 68 |
| 1.13 | 0x47 | 71 |
| 1.14 - 1.14.4 | 0x4B | 75 |
| 1.15 - 1.16.2 | 0x4C | 76 |
| 1.17 - 1.19.0 | 0x55 | 85 |
| 1.19.1 - 1.19.2 | 0x58 | 88 |
| 1.19.3 | 0x56 | 86 |
| 1.19.4 - 1.20.1 | 0x5A | 90 |
| 1.20.2 | 0x5C | 92 |
| 1.20.3 - 1.20.4 | 0x5E | 94 |
| 1.20.5 - 1.21.1 | 0x60 | 96 |
| 1.21.2 - 1.21.4 | 0x67 | 103 |
| 1.21.5 - 1.21.8 | 0x66 | 102 |
| 1.21.9 | 0x6B | 107 |

**Description:**

Creates and updates teams.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `STRING` | Team Name: A unique name for the team. (Shared with scoreboard). |
| `BYTE` | Method: Determines the layout of the remaining packet. |
| `TEXT_COMPONENT` | Team Display Name |
| `BYTE` | Friendly Flags: Bit mask. 0x01: Allow friendly fire, 0x02: can see invisible players on the same team. |
| `VAR_INT` | Name Tag Visibility: 0 = ALWAYS, 1 = NEVER, 2 = HIDE_FOR_OTHER_TEAMS, 3 = HIDE_FOR_OWN_TEAMS |
| `VAR_INT` | Collision Rule: 0 = ALWAYS, 1 = NEVER, 2 = PUSH_OTHER_TEAMS, 3 = PUSH_OWN_TEAM |
| `VAR_INT` | Team Color: Used to color the names of players on the team; see below. |
| `TEXT_COMPONENT` | Team Prefix: Displayed before the names of players that are part of this team. |
| `TEXT_COMPONENT` | Team Suffix: Displayed after the names of players that are part of this team. |
| `STRING` | Entities: Identifiers for the entities in this team.  For players, this is their username; for other entities, it is their UUID. |
| `NO_FIELDS` | no fields |
| `TEXT_COMPONENT` | Team Display Name |
| `BYTE` | Friendly Flags: Bit mask. 0x01: Allow friendly fire, 0x02: can see invisible entities on the same team. |
| `VAR_INT` | Name Tag Visibility: 0 = ALWAYS, 1 = NEVER, 2 = HIDE_FOR_OTHER_TEAMS, 3 = HIDE_FOR_OWN_TEAMS |
| `VAR_INT` | Collision Rule: 0 = ALWAYS, 1 = NEVER, 2 = PUSH_OTHER_TEAMS, 3 = PUSH_OWN_TEAM |
| `VAR_INT` | Team Color: Used to color the names of players on the team; see below. |
| `TEXT_COMPONENT` | Team Prefix: Displayed before the names of players that are part of this team. |
| `TEXT_COMPONENT` | Team Suffix: Displayed after the names of players that are part of this team. |
| `STRING` | Entities: Identifiers for the added entities.  For players, this is their username; for other entities, it is their UUID. |
| `STRING` | Entities: Identifiers for the removed entities.  For players, this is their username; for other entities, it is their UUID. |

---

### SET_SCORE

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.8 | 0x3C | 60 |
| 1.9 - 1.11 | 0x42 | 66 |
| 1.12 - 1.12.0 | 0x44 | 68 |
| 1.12.1 | 0x45 | 69 |
| 1.13 | 0x48 | 72 |
| 1.14 - 1.14.4 | 0x4C | 76 |
| 1.15 - 1.16.2 | 0x4D | 77 |
| 1.17 - 1.19.0 | 0x56 | 86 |
| 1.19.1 - 1.19.2 | 0x59 | 89 |
| 1.19.3 | 0x57 | 87 |
| 1.19.4 - 1.20.1 | 0x5B | 91 |
| 1.20.2 | 0x5D | 93 |
| 1.20.3 - 1.20.4 | 0x5F | 95 |
| 1.20.5 - 1.21.1 | 0x61 | 97 |
| 1.21.2 - 1.21.4 | 0x68 | 104 |
| 1.21.5 - 1.21.8 | 0x67 | 103 |
| 1.21.9 | 0x6C | 108 |

**Description:**

This is sent to the client when it should update a scoreboard item.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `STRING` | Entity Name: The entity whose score this is. For players, this is their username; for other entities, it is their UUID. |
| `STRING` | Objective Name: The name of the objective the score belongs to. |
| `VAR_INT` | Value: The score to be displayed next to the entry. |
| `PREFIXED_OPTIONAL_TEXT_COMPONENT` | Display Name: The custom display name. |
| `VAR_INT` | Number Format: Determines how the score number should be formatted. |
| `NO_FIELDS` | 0: blank: Show nothing. |
| `COMPOUND_TAG` | Styling: The styling to be used when formatting the score number. Contains the text component styling fields. |
| `TEXT_COMPONENT` | Content: The text to be used as placeholder. |

---

### SET_SIMULATION_DISTANCE

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.18 - 1.19.0 | 0x57 | 87 |
| 1.19.1 - 1.19.2 | 0x5A | 90 |
| 1.19.3 | 0x58 | 88 |
| 1.19.4 - 1.20.1 | 0x5C | 92 |
| 1.20.2 | 0x5E | 94 |
| 1.20.3 - 1.20.4 | 0x60 | 96 |
| 1.20.5 - 1.21.1 | 0x62 | 98 |
| 1.21.2 - 1.21.4 | 0x69 | 105 |
| 1.21.5 - 1.21.8 | 0x68 | 104 |
| 1.21.9 | 0x6D | 109 |

**Packet Fields:**

| Type | Description |
| --- | --- |
| `VAR_INT` | Simulation Distance: The distance that the client will process specific things, such as entities. |
| `VAR_INT` | Simulation Distance: The distance that the client will process specific things, such as entities. |

---

### SET_SUBTITLE_TEXT

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.17 - 1.17.1 | 0x57 | 87 |
| 1.18 - 1.19.0 | 0x58 | 88 |
| 1.19.1 - 1.19.2 | 0x5B | 91 |
| 1.19.3 | 0x59 | 89 |
| 1.19.4 - 1.20.1 | 0x5D | 93 |
| 1.20.2 | 0x5F | 95 |
| 1.20.3 - 1.20.4 | 0x61 | 97 |
| 1.20.5 - 1.21.1 | 0x63 | 99 |
| 1.21.2 - 1.21.4 | 0x6A | 106 |
| 1.21.5 - 1.21.8 | 0x69 | 105 |
| 1.21.9 | 0x6E | 110 |

**Packet Fields:**

| Type | Description |
| --- | --- |
| `TEXT_COMPONENT` | Subtitle Text |
| `TEXT_COMPONENT` | Subtitle Text |

---

### SET_TIME

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.8 | 0x3 | 3 |
| 1.9 - 1.11 | 0x44 | 68 |
| 1.12 - 1.12.0 | 0x46 | 70 |
| 1.12.1 | 0x47 | 71 |
| 1.13 | 0x4A | 74 |
| 1.14 - 1.14.4 | 0x4E | 78 |
| 1.15 | 0x4F | 79 |
| 1.16 - 1.16.2 | 0x4E | 78 |
| 1.17 - 1.17.1 | 0x58 | 88 |
| 1.18 - 1.19.0 | 0x59 | 89 |
| 1.19.1 - 1.19.2 | 0x5C | 92 |
| 1.19.3 | 0x5A | 90 |
| 1.19.4 - 1.20.1 | 0x5E | 94 |
| 1.20.2 | 0x60 | 96 |
| 1.20.3 - 1.20.4 | 0x62 | 98 |
| 1.20.5 - 1.21.1 | 0x64 | 100 |
| 1.21.2 - 1.21.4 | 0x6B | 107 |
| 1.21.5 - 1.21.8 | 0x6A | 106 |
| 1.21.9 | 0x6F | 111 |

**Description:**

Time is based on ticks, where 20 ticks happen every second. There are 24000 ticks in a day, making Minecraft days exactly 20 minutes long. The time of day is based on the timestamp modulo 24000. 0 is sunrise, 6000 is noon, 12000 is sunset, and 18000 is midnight. The default SMP server increments the time by 20 every second.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `LONG` | World Age: In ticks; not changed by server commands. |
| `LONG` | Time of day: The world (or region) time, in ticks. |
| `BOOLEAN` | Time of day increasing: If true, the client should automatically advance the time of day according to its ticking rate. |

---

### SET_TITLES

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.8 - 1.11 | 0x45 | 69 |
| 1.12 - 1.12.0 | 0x47 | 71 |
| 1.12.1 | 0x48 | 72 |
| 1.13 | 0x4B | 75 |
| 1.14 - 1.14.4 | 0x4F | 79 |
| 1.15 | 0x50 | 80 |
| 1.16 - 1.16.2 | 0x4F | 79 |

---

### SET_TITLES_ANIMATION

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.17 - 1.17.1 | 0x5A | 90 |
| 1.18 - 1.19.0 | 0x5B | 91 |
| 1.19.1 - 1.19.2 | 0x5E | 94 |
| 1.19.3 | 0x5C | 92 |
| 1.19.4 - 1.20.1 | 0x60 | 96 |
| 1.20.2 | 0x62 | 98 |
| 1.20.3 - 1.20.4 | 0x64 | 100 |
| 1.20.5 - 1.21.1 | 0x66 | 102 |
| 1.21.2 - 1.21.4 | 0x6D | 109 |
| 1.21.5 - 1.21.8 | 0x6C | 108 |
| 1.21.9 | 0x71 | 113 |

**Packet Fields:**

| Type | Description |
| --- | --- |
| `INT` | Fade In: Ticks to spend fading in. |
| `INT` | Stay: Ticks to keep the title displayed. |
| `INT` | Fade Out: Ticks to spend fading out, not when to start fading out. |

---

### SET_TITLE_TEXT

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.17 - 1.17.1 | 0x59 | 89 |
| 1.18 - 1.19.0 | 0x5A | 90 |
| 1.19.1 - 1.19.2 | 0x5D | 93 |
| 1.19.3 | 0x5B | 91 |
| 1.19.4 - 1.20.1 | 0x5F | 95 |
| 1.20.2 | 0x61 | 97 |
| 1.20.3 - 1.20.4 | 0x63 | 99 |
| 1.20.5 - 1.21.1 | 0x65 | 101 |
| 1.21.2 - 1.21.4 | 0x6C | 108 |
| 1.21.5 - 1.21.8 | 0x6B | 107 |
| 1.21.9 | 0x70 | 112 |

**Packet Fields:**

| Type | Description |
| --- | --- |
| `TEXT_COMPONENT` | Title Text |
| `TEXT_COMPONENT` | Title Text |

---

### SHOW_DIALOG

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.21.6 - 1.21.8 | 0x85 | 133 |
| 1.21.9 | 0x8A | 138 |

**Description:**

Show a custom dialog screen to the client.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `NBT` | Dialog: Inline definition as described at Registry_data#Dialog. |
| `ID_OR_NBT` | Dialog: ID in the minecraft:dialog registry, or an inline definition as described at Registry_data#Dialog. |

---

### SOUND

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.9 - 1.9.2 | 0x47 | 71 |
| 1.9.3 - 1.11 | 0x46 | 70 |
| 1.12 - 1.12.0 | 0x48 | 72 |
| 1.12.1 | 0x49 | 73 |
| 1.13 | 0x4D | 77 |
| 1.14 - 1.14.4 | 0x51 | 81 |
| 1.15 | 0x52 | 82 |
| 1.16 - 1.16.2 | 0x51 | 81 |
| 1.17 - 1.17.1 | 0x5C | 92 |
| 1.18 - 1.19.0 | 0x5D | 93 |
| 1.19.1 - 1.19.2 | 0x60 | 96 |
| 1.19.3 | 0x5E | 94 |
| 1.19.4 - 1.20.1 | 0x62 | 98 |
| 1.20.2 | 0x64 | 100 |
| 1.20.3 - 1.20.4 | 0x66 | 102 |
| 1.20.5 - 1.21.1 | 0x68 | 104 |
| 1.21.2 - 1.21.4 | 0x6F | 111 |
| 1.21.5 - 1.21.8 | 0x6E | 110 |
| 1.21.9 | 0x73 | 115 |

**Description:**

Plays a sound effect at the given location, either by hardcoded ID or Identifier. Sound IDs and names can be found here.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `ID_OR_SOUND_EVENT` | Sound Event: ID in the minecraft:sound_event registry, or an inline definition. |
| `VAR_INT` | Sound Category: The category that this sound will be played from (current categories). |
| `INT` | Effect Position X: Effect X multiplied by 8 (fixed-point number with only 3 bits dedicated to the fractional part). |
| `INT` | Effect Position Y: Effect Y multiplied by 8 (fixed-point number with only 3 bits dedicated to the fractional part). |
| `INT` | Effect Position Z: Effect Z multiplied by 8 (fixed-point number with only 3 bits dedicated to the fractional part). |
| `FLOAT` | Volume: 1.0 is 100%, capped between 0.0 and 1.0 by vanilla clients. |
| `FLOAT` | Pitch: Float between 0.5 and 2.0 by vanilla clients. |
| `LONG` | Seed: Seed used to pick sound variant. |

---

### SOUND_ENTITY

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.14 - 1.14.4 | 0x50 | 80 |
| 1.15 | 0x51 | 81 |
| 1.16 - 1.16.2 | 0x50 | 80 |
| 1.17 - 1.17.1 | 0x5B | 91 |
| 1.18 - 1.19.0 | 0x5C | 92 |
| 1.19.1 - 1.19.2 | 0x5F | 95 |
| 1.19.3 | 0x5D | 93 |
| 1.19.4 - 1.20.1 | 0x61 | 97 |
| 1.20.2 | 0x63 | 99 |
| 1.20.3 - 1.20.4 | 0x65 | 101 |
| 1.20.5 - 1.21.1 | 0x67 | 103 |
| 1.21.2 - 1.21.4 | 0x6E | 110 |
| 1.21.5 - 1.21.8 | 0x6D | 109 |
| 1.21.9 | 0x72 | 114 |

**Description:**

Plays a sound effect from an entity, either by hardcoded ID or Identifier. Sound IDs and names can be found here.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `ID_OR_SOUND_EVENT` | Sound Event: ID in the minecraft:sound_event registry, or an inline definition. |
| `VAR_INT` | Sound Category: The category that this sound will be played from (current categories). |
| `VAR_INT` | Entity ID |
| `FLOAT` | Volume: 1.0 is 100%, capped between 0.0 and 1.0 by vanilla clients. |
| `FLOAT` | Pitch: Float between 0.5 and 2.0 by vanilla clients. |
| `LONG` | Seed: Seed used to pick sound variant. |

---

### START_CONFIGURATION

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.20.2 | 0x65 | 101 |
| 1.20.3 - 1.20.4 | 0x67 | 103 |
| 1.20.5 - 1.21.1 | 0x69 | 105 |
| 1.21.2 - 1.21.4 | 0x70 | 112 |
| 1.21.5 - 1.21.8 | 0x6F | 111 |
| 1.21.9 | 0x74 | 116 |

**Description:**

Sent during gameplay in order to redo the configuration process. The client must respond with Acknowledge Configuration for the process to start.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `CLIENT` | Play: no fields |
| `CLIENT` | Play: no fields |

---

### STOP_SOUND

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.13 | 0x4C | 76 |
| 1.14 - 1.14.4 | 0x52 | 82 |
| 1.15 | 0x53 | 83 |
| 1.16 - 1.16.2 | 0x52 | 82 |
| 1.17 - 1.17.1 | 0x5D | 93 |
| 1.18 - 1.19.0 | 0x5E | 94 |
| 1.19.1 - 1.19.2 | 0x61 | 97 |
| 1.19.3 | 0x5F | 95 |
| 1.19.4 - 1.20.1 | 0x63 | 99 |
| 1.20.2 | 0x66 | 102 |
| 1.20.3 - 1.20.4 | 0x68 | 104 |
| 1.20.5 - 1.21.1 | 0x6A | 106 |
| 1.21.2 - 1.21.4 | 0x71 | 113 |
| 1.21.5 - 1.21.8 | 0x70 | 112 |
| 1.21.9 | 0x75 | 117 |

**Description:**

Categories:

**Packet Fields:**

| Type | Description |
| --- | --- |
| `BYTE` | Flags: Controls which fields are present. |
| `VAR_INT` | Source: Only if flags is 3 or 1 (bit mask 0x1). See below. If not present, then sounds from all sources are cleared. |
| `STRING` | Sound: Only if flags is 2 or 3 (bit mask 0x2).  A sound effect name, see Custom Sound Effect. If not present, then all sounds are cleared. |
| `BYTE` | Flags: Controls which fields are present. |
| `VAR_INT` | Source: Only if flags is 3 or 1 (bit mask 0x1). See below. If not present, then sounds from all sources are cleared. |
| `STRING` | Sound: Only if flags is 2 or 3 (bit mask 0x2).  A sound effect name, see Custom Sound Effect. If not present, then all sounds are cleared. |

---

### STORE_COOKIE

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.20.5 - 1.21.1 | 0x6B | 107 |
| 1.21.2 - 1.21.4 | 0x72 | 114 |
| 1.21.5 - 1.21.8 | 0x71 | 113 |
| 1.21.9 | 0x76 | 118 |

**Description:**

Stores some arbitrary data on the client, which persists between server transfers. The vanilla client only accepts cookies of up to 5 kiB in size.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `STRING` | Key: The identifier of the cookie. |
| `BYTE` | Payload: The data of the cookie. |
| `STRING` | Key: The identifier of the cookie. |
| `BYTE` | Payload: The data of the cookie. |

---

### SYSTEM_CHAT

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.19 - 1.19.0 | 0x5F | 95 |
| 1.19.1 - 1.19.2 | 0x62 | 98 |
| 1.19.3 | 0x60 | 96 |
| 1.19.4 - 1.20.1 | 0x64 | 100 |
| 1.20.2 | 0x67 | 103 |
| 1.20.3 - 1.20.4 | 0x69 | 105 |
| 1.20.5 - 1.21.1 | 0x6C | 108 |
| 1.21.2 - 1.21.4 | 0x73 | 115 |
| 1.21.5 - 1.21.8 | 0x72 | 114 |
| 1.21.9 | 0x77 | 119 |

**Description:**

Sends the client a raw system message.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `TEXT_COMPONENT` | Content: Limited to 262144 bytes. |
| `BOOLEAN` | Overlay: Whether the message is an actionbar or chat message. See also #Set Action Bar Text. |

---

### TAB_LIST

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.8 | 0x47 | 71 |
| 1.9 - 1.9.2 | 0x48 | 72 |
| 1.9.3 - 1.11 | 0x47 | 71 |
| 1.12 - 1.12.0 | 0x49 | 73 |
| 1.12.1 | 0x4A | 74 |
| 1.13 | 0x4E | 78 |
| 1.14 - 1.14.4 | 0x53 | 83 |
| 1.15 | 0x54 | 84 |
| 1.16 - 1.16.2 | 0x53 | 83 |
| 1.17 - 1.17.1 | 0x5E | 94 |
| 1.18 | 0x5F | 95 |
| 1.19 - 1.19.0 | 0x60 | 96 |
| 1.19.1 - 1.19.2 | 0x63 | 99 |
| 1.19.3 | 0x61 | 97 |
| 1.19.4 - 1.20.1 | 0x65 | 101 |
| 1.20.2 | 0x68 | 104 |
| 1.20.3 - 1.20.4 | 0x6A | 106 |
| 1.20.5 - 1.21.1 | 0x6D | 109 |
| 1.21.2 - 1.21.4 | 0x74 | 116 |
| 1.21.5 - 1.21.8 | 0x73 | 115 |
| 1.21.9 | 0x78 | 120 |

**Description:**

This packet may be used by custom servers to display additional information above/below the player list. It is never sent by the vanilla server.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `TEXT_COMPONENT` | Header: To remove the header, send an empty text component: {"text":""}. |
| `TEXT_COMPONENT` | Footer: To remove the footer, send an empty text component: {"text":""}. |

---

### TAG_QUERY

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.13 | 0x1D | 29 |
| 1.14 - 1.14.4 | 0x54 | 84 |
| 1.15 | 0x55 | 85 |
| 1.16 - 1.16.2 | 0x54 | 84 |
| 1.17 - 1.17.1 | 0x5F | 95 |
| 1.18 | 0x60 | 96 |
| 1.19 - 1.19.0 | 0x61 | 97 |
| 1.19.1 - 1.19.2 | 0x64 | 100 |
| 1.19.3 | 0x62 | 98 |
| 1.19.4 - 1.20.1 | 0x66 | 102 |
| 1.20.2 | 0x69 | 105 |
| 1.20.3 - 1.20.4 | 0x6B | 107 |
| 1.20.5 - 1.21.1 | 0x6E | 110 |
| 1.21.2 - 1.21.4 | 0x75 | 117 |
| 1.21.5 - 1.21.8 | 0x74 | 116 |
| 1.21.9 | 0x79 | 121 |

**Description:**

Sent in response to Query Block Entity Tag or Query Entity Tag.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `VAR_INT` | Transaction ID: Can be compared to the one sent in the original query packet. |
| `NBT` | NBT: The NBT of the block or entity. May be a TAG_END (0), in which case no NBT is present. |

---

### TAKE_ITEM_ENTITY

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.8 | 0xD | 13 |
| 1.9 - 1.9.2 | 0x49 | 73 |
| 1.9.3 - 1.11 | 0x48 | 72 |
| 1.12 - 1.12.0 | 0x4A | 74 |
| 1.12.1 | 0x4B | 75 |
| 1.13 | 0x4F | 79 |
| 1.14 - 1.14.4 | 0x55 | 85 |
| 1.15 | 0x56 | 86 |
| 1.16 - 1.16.2 | 0x55 | 85 |
| 1.17 - 1.17.1 | 0x60 | 96 |
| 1.18 | 0x61 | 97 |
| 1.19 - 1.19.0 | 0x62 | 98 |
| 1.19.1 - 1.19.2 | 0x65 | 101 |
| 1.19.3 | 0x63 | 99 |
| 1.19.4 - 1.20.1 | 0x67 | 103 |
| 1.20.2 | 0x6A | 106 |
| 1.20.3 - 1.20.4 | 0x6C | 108 |
| 1.20.5 - 1.21.1 | 0x6F | 111 |
| 1.21.2 - 1.21.4 | 0x76 | 118 |
| 1.21.5 - 1.21.8 | 0x75 | 117 |
| 1.21.9 | 0x7A | 122 |

**Description:**

Sent by the server when someone picks up an item lying on the ground — its sole purpose appears to be the animation of the item flying towards you. It doesn't destroy the entity in the client memory, and it doesn't add it to your inventory. The server only checks for items to be picked up after each Set Player Position (and Set Player Position And Rotation) packet sent by the client. The collector entity can be any entity; it does not have to be a player. The collected entity can also be any entity, but the vanilla server only uses this for items, experience orbs, and the different varieties of arrows.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `VAR_INT` | Collected Entity ID |
| `VAR_INT` | Collector Entity ID |
| `VAR_INT` | Pickup Item Count: Seems to be 1 for XP orbs, otherwise the number of items in the stack. |

---

### TELEPORT_ENTITY

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.8 | 0x18 | 24 |
| 1.9 - 1.9.2 | 0x4A | 74 |
| 1.9.3 - 1.11 | 0x49 | 73 |
| 1.12 - 1.12.0 | 0x4B | 75 |
| 1.12.1 | 0x4C | 76 |
| 1.13 | 0x50 | 80 |
| 1.14 - 1.14.4 | 0x56 | 86 |
| 1.15 | 0x57 | 87 |
| 1.16 - 1.16.2 | 0x56 | 86 |
| 1.17 - 1.17.1 | 0x61 | 97 |
| 1.18 | 0x62 | 98 |
| 1.19 - 1.19.0 | 0x63 | 99 |
| 1.19.1 - 1.19.2 | 0x66 | 102 |
| 1.19.3 | 0x64 | 100 |
| 1.19.4 - 1.20.1 | 0x68 | 104 |
| 1.20.2 | 0x6B | 107 |
| 1.20.3 - 1.20.4 | 0x6D | 109 |
| 1.20.5 - 1.21.1 | 0x70 | 112 |
| 1.21.2 - 1.21.4 | 0x77 | 119 |
| 1.21.5 - 1.21.8 | 0x76 | 118 |
| 1.21.9 | 0x7B | 123 |

**Description:**

This packet is sent by the server when an entity moves more than 8 blocks.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `VAR_INT` | Entity ID |
| `DOUBLE` | X |
| `DOUBLE` | Y |
| `DOUBLE` | Z |
| `DOUBLE` | Velocity X |
| `DOUBLE` | Velocity Y |
| `DOUBLE` | Velocity Z |
| `FLOAT` | Yaw: Rotation on the X axis, in degrees. |
| `FLOAT` | Pitch: Rotation on the Y axis, in degrees. |
| `BOOLEAN` | On Ground |
| `VAR_INT` | Entity ID |
| `DOUBLE` | X |
| `DOUBLE` | Y |
| `DOUBLE` | Z |
| `DOUBLE` | Velocity X |
| `DOUBLE` | Velocity Y |
| `DOUBLE` | Velocity Z |
| `FLOAT` | Yaw: Rotation on the Y axis, in degrees. |
| `FLOAT` | Pitch: Rotation on the Y axis, in degrees. |
| `TELEPORT_FLAGS` | Flags |
| `BOOLEAN` | On Ground |

---

### TEST_INSTANCE_BLOCK_STATUS

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.21.5 - 1.21.8 | 0x77 | 119 |
| 1.21.9 | 0x7C | 124 |

**Description:**

Updates the status of the currently open Test Instance Block screen, if any.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `TEXT_COMPONENT` | Status |
| `BOOLEAN` | Has Size |
| `DOUBLE` | Size X: Only present if Has Size is true. |
| `DOUBLE` | Size Y: Only present if Has Size is true. |
| `DOUBLE` | Size Z: Only present if Has Size is true. |
| `TEXT_COMPONENT` | Status |
| `BOOLEAN` | Has Size |
| `DOUBLE` | Size X: Only present if Has Size is true. |
| `DOUBLE` | Size Y: Only present if Has Size is true. |
| `DOUBLE` | Size Z: Only present if Has Size is true. |

---

### TICKING_STATE

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.20.3 - 1.20.4 | 0x6E | 110 |
| 1.20.5 - 1.21.1 | 0x71 | 113 |
| 1.21.2 - 1.21.8 | 0x78 | 120 |
| 1.21.9 | 0x7D | 125 |

**Description:**

Used to adjust the ticking rate of the client, and whether it's frozen.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `FLOAT` | Tick rate |
| `BOOLEAN` | Is frozen |

---

### TICKING_STEP

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.20.3 - 1.20.4 | 0x6F | 111 |
| 1.20.5 - 1.21.1 | 0x72 | 114 |
| 1.21.2 - 1.21.8 | 0x79 | 121 |
| 1.21.9 | 0x7E | 126 |

**Description:**

Advances the client processing by the specified number of ticks. Has no effect unless client ticking is frozen.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `VAR_INT` | Tick steps |

---

### TRACKED_WAYPOINT

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.21.6 - 1.21.8 | 0x83 | 131 |
| 1.21.9 | 0x88 | 136 |

---

### TRANSFER

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.20.5 - 1.21.1 | 0x73 | 115 |
| 1.21.2 - 1.21.8 | 0x7A | 122 |
| 1.21.9 | 0x7F | 127 |

**Description:**

Notifies the client that it should transfer to the given server. Cookies previously stored are preserved between server transfers.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `STRING` | Host: The hostname or IP of the server. |
| `VAR_INT` | Port: The port of the server. |
| `STRING` | Host: The hostname or IP of the server. |
| `VAR_INT` | Port: The port of the server. |

---

### UPDATE_ADVANCEMENTS

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.12 - 1.12.0 | 0x4C | 76 |
| 1.12.1 | 0x4D | 77 |
| 1.13 | 0x51 | 81 |
| 1.14 - 1.14.4 | 0x57 | 87 |
| 1.15 | 0x58 | 88 |
| 1.16 - 1.16.2 | 0x57 | 87 |
| 1.17 - 1.17.1 | 0x62 | 98 |
| 1.18 | 0x63 | 99 |
| 1.19 - 1.19.0 | 0x64 | 100 |
| 1.19.1 - 1.19.2 | 0x67 | 103 |
| 1.19.3 | 0x65 | 101 |
| 1.19.4 - 1.20.1 | 0x69 | 105 |
| 1.20.2 | 0x6C | 108 |
| 1.20.3 - 1.20.4 | 0x70 | 112 |
| 1.20.5 - 1.21.1 | 0x74 | 116 |
| 1.21.2 - 1.21.8 | 0x7B | 123 |
| 1.21.9 | 0x80 | 128 |

**Description:**

Advancement structure: These booleans must be mapped with the AND operator to get the result. The vanilla client only sends data for advancements on the minecraft namespace.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `BOOLEAN` | Reset/Clear: Whether to reset/clear the current advancements. |
| `STRING` | Prefixed Array: The identifier of the advancement. |
| `ADVANCEMENT` | Value: See below |
| `STRING` | Identifiers: The identifiers of the advancements that should be removed. |
| `STRING` | Prefixed Array: The identifier of the advancement. |
| `ADVANCEMENT_PROGRESS` | Value: See below. |
| `BOOLEAN` | Show advancements |
| `BOOLEAN` | Reset/Clear: Whether to reset/clear the current advancements. |
| `STRING` | Prefixed Array: The identifier of the advancement. |
| `ADVANCEMENT` | Value: See below |
| `STRING` | Identifiers: The identifiers of the advancements that should be removed. |
| `STRING` | Prefixed Array: The identifier of the advancement. |
| `ADVANCEMENT_PROGRESS` | Value: See below. |
| `BOOLEAN` | Show advancements |
| `STRING` | Parent id: The identifier of the parent advancement. |
| `PREFIXED_OPTIONAL_ADVANCEMENT_DISPLAY` | Display data: See below. |
| `ARRAY` | Nested requirements: Prefixed Array of String (32767) |
| `BOOLEAN` | Sends telemetry data: Whether the client should include this achievement in the telemetry data when it's completed.
The vanilla client only sends data for advancements on the minecraft namespace. |
| `TEXT_COMPONENT` | Title |
| `TEXT_COMPONENT` | Description |
| `SLOT` | Icon |
| `VAR_INT` | Frame type: 0 = task, 1 = challenge, 2 = goal. |
| `INT` | Flags: 0x01: has background texture; 0x02: show_toast; 0x04: hidden. |
| `STRING` | Background texture: Background texture location.  Only if flags indicates it. |
| `FLOAT` | X coord |
| `FLOAT` | Y coord |
| `STRING` | Criteria: Prefixed Array |
| `LONG` | Date of achieving: Present if achieved. As returned by Date.getTime. |

---

### UPDATE_ATTRIBUTES

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.8 | 0x20 | 32 |
| 1.9 - 1.9.2 | 0x4B | 75 |
| 1.9.3 - 1.11 | 0x4A | 74 |
| 1.12 - 1.12.0 | 0x4D | 77 |
| 1.12.1 | 0x4E | 78 |
| 1.13 | 0x52 | 82 |
| 1.14 - 1.14.4 | 0x58 | 88 |
| 1.15 | 0x59 | 89 |
| 1.16 - 1.16.2 | 0x58 | 88 |
| 1.17 - 1.17.1 | 0x63 | 99 |
| 1.18 | 0x64 | 100 |
| 1.19 - 1.19.0 | 0x65 | 101 |
| 1.19.1 - 1.19.2 | 0x68 | 104 |
| 1.19.3 | 0x66 | 102 |
| 1.19.4 - 1.20.1 | 0x6A | 106 |
| 1.20.2 | 0x6D | 109 |
| 1.20.3 - 1.20.4 | 0x71 | 113 |
| 1.20.5 - 1.21.1 | 0x75 | 117 |
| 1.21.2 - 1.21.8 | 0x7C | 124 |
| 1.21.9 | 0x81 | 129 |

**Description:**

Sets attributes on the given entity.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `VAR_INT` | Entity ID |
| `VAR_INT` | Prefixed Array: ID in the minecraft:attribute registry. See also Attribute#Attributes. |
| `DOUBLE` | Value: See below. |
| `ARRAY` | Modifiers: See Attribute#Modifiers. Modifier Data defined below. |
| `VAR_INT` | Entity ID |
| `VAR_INT` | Prefixed Array: ID in the minecraft:attribute registry. See also Attribute#Attributes. |
| `DOUBLE` | Value: See below. |
| `ARRAY` | Modifiers: See Attribute#Modifiers. Modifier Data defined below. |
| `STRING` | Id |
| `DOUBLE` | Amount: May be positive or negative. |
| `BYTE` | Operation: See below. |

---

### UPDATE_ENABLED_FEATURES

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.19.3 | 0x67 | 103 |
| 1.19.4 | 0x6B | 107 |

**Description:**

Used to enable and disable features, generally experimental ones, on the client.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `STRING` | Feature Flags |

---

### UPDATE_ENTITY_NBT

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.8 | 0x49 | 73 |

---

### UPDATE_MOB_EFFECT

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.8 | 0x1D | 29 |
| 1.9 - 1.9.2 | 0x4C | 76 |
| 1.9.3 - 1.11 | 0x4B | 75 |
| 1.12 - 1.12.0 | 0x4E | 78 |
| 1.12.1 | 0x4F | 79 |
| 1.13 | 0x53 | 83 |
| 1.14 - 1.14.4 | 0x59 | 89 |
| 1.15 | 0x5A | 90 |
| 1.16 - 1.16.2 | 0x59 | 89 |
| 1.17 - 1.17.1 | 0x64 | 100 |
| 1.18 | 0x65 | 101 |
| 1.19 - 1.19.0 | 0x66 | 102 |
| 1.19.1 - 1.19.2 | 0x69 | 105 |
| 1.19.3 | 0x68 | 104 |
| 1.19.4 - 1.20.1 | 0x6C | 108 |
| 1.20.2 | 0x6E | 110 |
| 1.20.3 - 1.20.4 | 0x72 | 114 |
| 1.20.5 - 1.21.1 | 0x76 | 118 |
| 1.21.2 - 1.21.8 | 0x7D | 125 |
| 1.21.9 | 0x82 | 130 |

**Packet Fields:**

| Type | Description |
| --- | --- |
| `VAR_INT` | Entity ID |
| `VAR_INT` | Effect ID: See this table. |
| `VAR_INT` | Amplifier: Vanilla client displays effect level as Amplifier + 1. |
| `VAR_INT` | Duration: Duration in ticks. (-1 for infinite) |
| `BYTE` | Flags: Bit field, see below. |

---

### UPDATE_RECIPES

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.13 | 0x54 | 84 |
| 1.14 - 1.14.4 | 0x5A | 90 |
| 1.15 | 0x5B | 91 |
| 1.16 - 1.16.2 | 0x5A | 90 |
| 1.17 - 1.17.1 | 0x65 | 101 |
| 1.18 | 0x66 | 102 |
| 1.19 - 1.19.0 | 0x67 | 103 |
| 1.19.1 - 1.19.2 | 0x6A | 106 |
| 1.19.3 | 0x69 | 105 |
| 1.19.4 - 1.20.1 | 0x6D | 109 |
| 1.20.2 | 0x6F | 111 |
| 1.20.3 - 1.20.4 | 0x73 | 115 |
| 1.20.5 - 1.21.1 | 0x77 | 119 |
| 1.21.2 - 1.21.8 | 0x7E | 126 |
| 1.21.9 | 0x83 | 131 |

**Packet Fields:**

| Type | Description |
| --- | --- |
| `PROPERTY_SET_ID` | Property Sets: Prefixed Array |
| `VAR_INT` | Items: IDs in the minecraft:item registry. |
| `ID_SET` | Prefixed Array |
| `SLOT_DISPLAY` | Slot Display |
| `PROPERTY_SET_ID` | Property Sets: Prefixed Array |
| `VAR_INT` | Items: IDs in the minecraft:item registry. |
| `ID_SET` | Prefixed Array |
| `SLOT_DISPLAY` | Slot Display |

---

### UPDATE_SIGN

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.8 | 0x33 | 51 |
| 1.9 | 0x46 | 70 |

---

### UPDATE_TAGS

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.13 | 0x55 | 85 |
| 1.14 - 1.14.4 | 0x5B | 91 |
| 1.15 | 0x5C | 92 |
| 1.16 - 1.16.2 | 0x5B | 91 |
| 1.17 - 1.17.1 | 0x66 | 102 |
| 1.18 | 0x67 | 103 |
| 1.19 - 1.19.0 | 0x68 | 104 |
| 1.19.1 - 1.19.2 | 0x6B | 107 |
| 1.19.3 | 0x6A | 106 |
| 1.19.4 - 1.20.1 | 0x6E | 110 |
| 1.20.2 | 0x70 | 112 |
| 1.20.3 - 1.20.4 | 0x74 | 116 |
| 1.20.5 - 1.21.1 | 0x78 | 120 |
| 1.21.2 - 1.21.8 | 0x7F | 127 |
| 1.21.9 | 0x84 | 132 |

**Packet Fields:**

| Type | Description |
| --- | --- |
| `REGISTRY` | Array of tags: Prefixed Array |
| `REGISTRY` | Registry to tags map: Prefixed Array |
| `ARRAY` | Tags |
## Serverbound Packets

**Serverbound packets** are sent from client to server. Total: **71 packets**.

### ACCEPT_TELEPORTATION

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.9 - 1.21.6 | 0x0 | 0 |

**Description:**

Sent by client as confirmation of Synchronize Player Position.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `VAR_INT` | Teleport ID: The ID given by the Synchronize Player Position packet. |

---

### BLOCK_ENTITY_TAG_QUERY

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.13 - 1.21.6 | 0x1 | 1 |

**Description:**

Used when F3+I is pressed while looking at a block.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `VAR_INT` | Transaction ID: An incremental ID so that the client can verify that the response matches. |
| `POSITION` | Location: The location of the block to check. |

---

### BUNDLE_ITEM_SELECTED

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.21.2 - 1.21.6 | 0x2 | 2 |

**Packet Fields:**

| Type | Description |
| --- | --- |
| `VAR_INT` | Slot of Bundle |
| `VAR_INT` | Slot in Bundle |
| `VAR_INT` | Slot of Bundle |
| `VAR_INT` | Slot in Bundle |

---

### CHANGE_DIFFICULTY

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.14 - 1.21.1 | 0x2 | 2 |
| 1.21.2 - 1.21.6 | 0x3 | 3 |

**Description:**

Must have at least op level 2 to use.  Appears to only be used on singleplayer; the difficulty buttons are still disabled in multiplayer.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `BYTE` | New difficulty: 0: peaceful, 1: easy, 2: normal, 3: hard. |

---

### CHANGE_GAME_MODE

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.21.6 | 0x4 | 4 |

**Description:**

Requests for the server to update our game mode. Has no effect on vanilla servers if the client doesn't have the required permissions.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `VAR_INT` | Game mode: 0: survival, 1: creative, 2: adventure, 3: spectator. |
| `VAR_INT` | Game mode: 0: survival, 1: creative, 2: adventure, 3: spectator. |

---

### CHAT

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.8 | 0x1 | 1 |
| 1.9 - 1.11 | 0x2 | 2 |
| 1.12 - 1.12.0 | 0x3 | 3 |
| 1.12.1 - 1.13 | 0x2 | 2 |
| 1.14 - 1.18 | 0x3 | 3 |
| 1.19 - 1.19.0 | 0x4 | 4 |
| 1.19.1 - 1.20.4 | 0x5 | 5 |
| 1.20.5 - 1.21.1 | 0x6 | 6 |
| 1.21.2 - 1.21.5 | 0x7 | 7 |
| 1.21.6 | 0x8 | 8 |

**Description:**

Used to send a chat message to the server.  The message may not be longer than 256 characters or else the server will kick the client. The server will broadcast a Player Chat Message packet with Chat Type minecraft:chat to all players that haven't disabled chat (including the player that sent the message). See Chat#Processing chat for more information. This is a SHA256 with RSA digital signature computed over the following: The client's chat private key is used for the message signature. Bitmask of which message signatures from the last seen set were used to sign this message. The most recent is the highest bit. If there are fewer than 20 messages in the last seen set, the lower bits will be zeros.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `STRING` | Message: Content of the message |
| `LONG` | Timestamp: Number of milliseconds since the epoch (1 Jan 1970, midnight, UTC) |
| `LONG` | Salt: The salt used to verify the signature hash. Randomly generated by the client |
| `BYTE` | Signature: The signature used to verify the chat message's authentication. When present, always 256 bytes and not length-prefixed.
This is a SHA256 with RSA digital signature computed over the following:

The number 1 as a 4-byte int. Always 00 00 00 01.
The player's 16-byte UUID.
The chat session (a 16-byte UUID randomly generated by the client).
The index of the message within this chat session as a 4-byte int. First message is 0, next message is 1, etc. Incremented each time the client sends a chat message.
The salt (from above) as an 8-byte long.
The timestamp (from above) converted from milliseconds to seconds, so divide by 1000, as an 8-byte long.
The length of the message in bytes (from above) as a 4-byte int.
The message bytes.
The number of messages in the last seen set, as a 4-byte int. Always in the range [0,20].
For each message in the last seen set, from oldest to newest, the 256-byte signature of that message.

The client's chat private key is used for the message signature. |
| `VAR_INT` | Message Count: Number of signed clientbound chat messages the client has seen from the server since the last serverbound chat message from this client. The server will use this to update its last seen list for the client. |
| `FIXED_BITSET` | Acknowledged: Bitmask of which message signatures from the last seen set were used to sign this message. The most recent is the highest bit. If there are fewer than 20 messages in the last seen set, the lower bits will be zeros. |
| `BYTE` | Checksum |

---

### CHAT_ACK

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.19.1 - 1.21.1 | 0x3 | 3 |
| 1.21.2 - 1.21.5 | 0x4 | 4 |
| 1.21.6 | 0x5 | 5 |

**Packet Fields:**

| Type | Description |
| --- | --- |
| `VAR_INT` | Message Count |

---

### CHAT_COMMAND

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.19 - 1.19.0 | 0x3 | 3 |
| 1.19.1 - 1.21.1 | 0x4 | 4 |
| 1.21.2 - 1.21.5 | 0x5 | 5 |
| 1.21.6 | 0x6 | 6 |

**Packet Fields:**

| Type | Description |
| --- | --- |
| `STRING` | Command: The command typed by the client excluding the /. |
| `STRING` | Command: The command typed by the client excluding the /. |

---

### CHAT_COMMAND_SIGNED

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.20.5 - 1.21.1 | 0x5 | 5 |
| 1.21.2 - 1.21.5 | 0x6 | 6 |
| 1.21.6 | 0x7 | 7 |

**Packet Fields:**

| Type | Description |
| --- | --- |
| `STRING` | Command: The command typed by the client excluding the /. |
| `LONG` | Timestamp: The timestamp that the command was executed. |
| `LONG` | Salt: The salt for the following argument signatures. |
| `STRING` | Prefixed Array (8): The name of the argument that is signed by the following signature. |
| `BYTE` | Signature: The signature that verifies the argument. Always 256 bytes and is not length-prefixed. |
| `VAR_INT` | Message Count |
| `FIXED_BITSET` | Acknowledged |
| `BYTE` | Checksum |

---

### CHAT_PREVIEW

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.19 - 1.19.0 | 0x5 | 5 |
| 1.19.1 | 0x6 | 6 |

---

### CHAT_SESSION_UPDATE

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.19.3 | 0x20 | 32 |
| 1.19.4 - 1.20.4 | 0x6 | 6 |
| 1.20.5 - 1.21.1 | 0x7 | 7 |
| 1.21.2 - 1.21.5 | 0x8 | 8 |
| 1.21.6 | 0x9 | 9 |

**Packet Fields:**

| Type | Description |
| --- | --- |
| `UUID` | Session Id |
| `LONG` | Expires At: The time the play session key expires in epoch milliseconds. |
| `BYTE` | Public Key: A byte array of an X.509-encoded public key. |
| `BYTE` | Key Signature: The signature consists of the player UUID, the key expiration timestamp, and the public key data. These values are hashed using SHA-1 and signed using Mojang's private RSA key. |

---

### CHUNK_BATCH_RECEIVED

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.20.2 - 1.20.4 | 0x7 | 7 |
| 1.20.5 - 1.21.1 | 0x8 | 8 |
| 1.21.2 - 1.21.5 | 0x9 | 9 |
| 1.21.6 | 0xA | 10 |

**Description:**

Notifies the server that the chunk batch has been received by the client. The server uses the value sent in this packet to adjust the number of chunks to be sent in a batch. The vanilla server will stop sending further chunk data until the client acknowledges the sent chunk batch. After the first acknowledgement, the server adjusts this number to allow up to 10 unacknowledged batches.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `FLOAT` | Chunks per tick: Desired chunks per tick. |
| `FLOAT` | Chunks per tick: Desired chunks per tick. |

---

### CLIENT_COMMAND

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.8 | 0x16 | 22 |
| 1.9 - 1.11 | 0x3 | 3 |
| 1.12 - 1.12.0 | 0x4 | 4 |
| 1.12.1 - 1.13 | 0x3 | 3 |
| 1.14 - 1.18 | 0x4 | 4 |
| 1.19 - 1.19.0 | 0x6 | 6 |
| 1.19.1 - 1.19.2 | 0x7 | 7 |
| 1.19.3 | 0x6 | 6 |
| 1.19.4 - 1.20.1 | 0x7 | 7 |
| 1.20.2 - 1.20.4 | 0x8 | 8 |
| 1.20.5 - 1.21.1 | 0x9 | 9 |
| 1.21.2 - 1.21.5 | 0xA | 10 |
| 1.21.6 | 0xB | 11 |

**Packet Fields:**

| Type | Description |
| --- | --- |
| `VAR_INT` | Action ID: See below |

---

### CLIENT_INFORMATION

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.8 | 0x15 | 21 |
| 1.9 - 1.11 | 0x4 | 4 |
| 1.12 - 1.12.0 | 0x5 | 5 |
| 1.12.1 - 1.13 | 0x4 | 4 |
| 1.14 - 1.18 | 0x5 | 5 |
| 1.19 - 1.19.0 | 0x7 | 7 |
| 1.19.1 - 1.19.2 | 0x8 | 8 |
| 1.19.3 | 0x7 | 7 |
| 1.19.4 - 1.20.1 | 0x8 | 8 |
| 1.20.2 - 1.20.4 | 0x9 | 9 |
| 1.20.5 - 1.21.1 | 0xA | 10 |
| 1.21.2 - 1.21.5 | 0xC | 12 |
| 1.21.6 | 0xD | 13 |

**Description:**

Sent when the player connects, or when settings are changed.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `STRING` | Locale: e.g. en_GB. |
| `BYTE` | View Distance: Client-side render distance, in chunks. |
| `VAR_INT` | Chat Mode: 0: enabled, 1: commands only, 2: hidden.  See Chat#Client chat mode for more information. |
| `BOOLEAN` | Chat Colors: “Colors” multiplayer setting. The vanilla server stores this value but does nothing with it (see MC-64867). Some third-party servers disable all coloring in chat and system messages when it is false. |
| `BYTE` | Displayed Skin Parts: Bit mask, see below. |
| `VAR_INT` | Main Hand: 0: Left, 1: Right. |
| `BOOLEAN` | Enable text filtering: Enables filtering of text on signs and written book titles. The vanilla client sets this according to the profanityFilterPreferences.profanityFilterOn account attribute indicated by the /player/attributes Mojang API endpoint. In offline mode, it is always false. |
| `BOOLEAN` | Allow server listings: Servers usually list online players; this option should let you not show up in that list. |
| `VAR_INT` | Particle Status: 0: all, 1: decreased, 2: minimal |
| `STRING` | Locale: e.g. en_GB. |
| `BYTE` | View Distance: Client-side render distance, in chunks. |
| `VAR_INT` | Chat Mode: 0: enabled, 1: commands only, 2: hidden.  See Chat#Client chat mode for more information. |
| `BOOLEAN` | Chat Colors: “Colors” multiplayer setting. The vanilla server stores this value but does nothing with it (see MC-64867). Some third-party servers disable all coloring in chat and system messages when it is false. |
| `BYTE` | Displayed Skin Parts: Bit mask, see below. |
| `VAR_INT` | Main Hand: 0: Left, 1: Right. |
| `BOOLEAN` | Enable text filtering: Enables filtering of text on signs and written book titles. The vanilla client sets this according to the profanityFilterPreferences.profanityFilterOn account attribute indicated by the /player/attributes Mojang API endpoint. In offline mode, it is always false. |
| `BOOLEAN` | Allow server listings: Servers usually list online players; this option should let you not show up in that list. |
| `VAR_INT` | Particle Status: 0: all, 1: decreased, 2: minimal |

---

### CLIENT_TICK_END

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.21.2 - 1.21.5 | 0xB | 11 |
| 1.21.6 | 0xC | 12 |

**Packet Fields:**

| Type | Description |
| --- | --- |
| `SERVER` | Play: no fields |
| `SERVER` | Play: no fields |

---

### COMMAND_SUGGESTION

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.8 | 0x14 | 20 |
| 1.9 - 1.11 | 0x1 | 1 |
| 1.12 - 1.12.0 | 0x2 | 2 |
| 1.12.1 | 0x1 | 1 |
| 1.13 | 0x5 | 5 |
| 1.14 - 1.18 | 0x6 | 6 |
| 1.19 - 1.19.0 | 0x8 | 8 |
| 1.19.1 - 1.19.2 | 0x9 | 9 |
| 1.19.3 | 0x8 | 8 |
| 1.19.4 - 1.20.1 | 0x9 | 9 |
| 1.20.2 - 1.20.4 | 0xA | 10 |
| 1.20.5 - 1.21.1 | 0xB | 11 |
| 1.21.2 - 1.21.5 | 0xD | 13 |
| 1.21.6 | 0xE | 14 |

**Description:**

Sent when the client needs to tab-complete a minecraft:ask_server suggestion type.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `VAR_INT` | Transaction Id: The ID of the transaction that the server will send back to the client in the response of this packet. Client generates this and increments it each time it sends another tab completion that doesn't get a response. |
| `STRING` | Text: All the text behind the cursor including the / (e.g. to the left of the cursor in left-to-right languages like English). |

---

### CONFIGURATION_ACKNOWLEDGED

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.20.2 - 1.20.4 | 0xB | 11 |
| 1.20.5 - 1.21.1 | 0xC | 12 |
| 1.21.2 - 1.21.5 | 0xE | 14 |
| 1.21.6 | 0xF | 15 |

**Description:**

Sent by the client upon receiving a Start Configuration packet from the server.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `SERVER` | Play: no fields |

---

### CONTAINER_ACK

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.8 | 0xF | 15 |
| 1.9 - 1.11 | 0x5 | 5 |
| 1.12 - 1.12.0 | 0x6 | 6 |
| 1.12.1 | 0x5 | 5 |
| 1.13 | 0x6 | 6 |
| 1.14 - 1.16.2 | 0x7 | 7 |

---

### CONTAINER_BUTTON_CLICK

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.8 | 0x11 | 17 |
| 1.9 - 1.11 | 0x6 | 6 |
| 1.12 - 1.12.0 | 0x7 | 7 |
| 1.12.1 | 0x6 | 6 |
| 1.13 | 0x7 | 7 |
| 1.14 - 1.16.2 | 0x8 | 8 |
| 1.17 - 1.18 | 0x7 | 7 |
| 1.19 - 1.19.0 | 0x9 | 9 |
| 1.19.1 - 1.19.2 | 0xA | 10 |
| 1.19.3 | 0x9 | 9 |
| 1.19.4 - 1.20.1 | 0xA | 10 |
| 1.20.2 - 1.20.4 | 0xC | 12 |
| 1.20.5 - 1.21.1 | 0xD | 13 |
| 1.21.2 - 1.21.5 | 0xF | 15 |
| 1.21.6 | 0x10 | 16 |

**Description:**

Used when clicking on window buttons. Until 1.14, this was only used by enchantment tables.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `VAR_INT` | Window ID: The ID of the window sent by Open Screen. |
| `VAR_INT` | Button ID: Meaning depends on window type; see below. |

---

### CONTAINER_CLICK

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.8 | 0xE | 14 |
| 1.9 - 1.11 | 0x7 | 7 |
| 1.12 - 1.12.0 | 0x8 | 8 |
| 1.12.1 | 0x7 | 7 |
| 1.13 | 0x8 | 8 |
| 1.14 - 1.16.2 | 0x9 | 9 |
| 1.17 - 1.18 | 0x8 | 8 |
| 1.19 - 1.19.0 | 0xA | 10 |
| 1.19.1 - 1.19.2 | 0xB | 11 |
| 1.19.3 | 0xA | 10 |
| 1.19.4 - 1.20.1 | 0xB | 11 |
| 1.20.2 - 1.20.4 | 0xD | 13 |
| 1.20.5 - 1.21.1 | 0xE | 14 |
| 1.21.2 - 1.21.5 | 0x10 | 16 |
| 1.21.6 | 0x11 | 17 |

**Description:**

This packet is sent by the client when the player clicks on a slot in a window.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `VAR_INT` | Window ID: The ID of the window that was clicked. 0 for player inventory. The server ignores any packets targeting a Window ID other than the current one, including ignoring 0 when any other window is open. |
| `VAR_INT` | State ID: The last received State ID from either a Set Container Slot or a Set Container Content packet. |
| `SHORT` | Slot: The clicked slot number, see below. |
| `BYTE` | Button: The button used in the click, see below. |
| `VAR_INT` | Mode: Inventory operation mode, see below. |
| `SHORT` | Prefixed Array (128) |
| `HASHED_SLOT` | Slot data: New data for this slot, in the client's opinion; see below. |
| `HASHED_SLOT` | Carried item: Item carried by the cursor. |

---

### CONTAINER_CLOSE

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.8 | 0xD | 13 |
| 1.9 - 1.11 | 0x8 | 8 |
| 1.12 - 1.12.0 | 0x9 | 9 |
| 1.12.1 | 0x8 | 8 |
| 1.13 | 0x9 | 9 |
| 1.14 - 1.16.2 | 0xA | 10 |
| 1.17 - 1.18 | 0x9 | 9 |
| 1.19 - 1.19.0 | 0xB | 11 |
| 1.19.1 - 1.19.2 | 0xC | 12 |
| 1.19.3 | 0xB | 11 |
| 1.19.4 - 1.20.1 | 0xC | 12 |
| 1.20.2 - 1.20.4 | 0xE | 14 |
| 1.20.5 - 1.21.1 | 0xF | 15 |
| 1.21.2 - 1.21.5 | 0x11 | 17 |
| 1.21.6 | 0x12 | 18 |

**Description:**

This packet is sent by the client when closing a window. vanilla clients send a Close Window packet with Window ID 0 to close their inventory, even though there is never an Open Screen packet for the inventory.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `VAR_INT` | Window ID: This is the ID of the window that was closed. 0 for player inventory. |

---

### CONTAINER_SLOT_STATE_CHANGED

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.20.3 - 1.20.4 | 0xF | 15 |
| 1.20.5 - 1.21.1 | 0x10 | 16 |
| 1.21.2 - 1.21.5 | 0x12 | 18 |
| 1.21.6 | 0x13 | 19 |

**Description:**

This packet is sent by the client when toggling the state of a Crafter.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `VAR_INT` | Slot ID: This is the ID of the slot that was changed. |
| `VAR_INT` | Window ID: This is the ID of the window that was changed. |

---

### COOKIE_RESPONSE

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.20.5 - 1.21.1 | 0x11 | 17 |
| 1.21.2 - 1.21.5 | 0x13 | 19 |
| 1.21.6 | 0x14 | 20 |

**Description:**

Response to a Cookie Request (login) from the server. The vanilla server only accepts responses of up to 5 kiB in size.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `STRING` | Key: The identifier of the cookie. |
| `BYTE` | Payload: The data of the cookie. |
| `STRING` | Key: The identifier of the cookie. |
| `BYTE` | Payload: The data of the cookie. |
| `STRING` | Key: The identifier of the cookie. |
| `BYTE` | Payload: The data of the cookie. |

---

### CRAFTING_RECIPE_PLACEMENT

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.12 | 0x1 | 1 |

---

### CUSTOM_CLICK_ACTION

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.21.6 | 0x41 | 65 |

**Description:**

Sent when the client clicks a Text Component with the minecraft:custom click action. This is meant as an alternative to running a command, but it will not have any effect on vanilla servers.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `STRING` | ID: The identifier for the click action. |
| `NBT` | Payload: The data to send with the click action. May be a TAG_END (0). |
| `STRING` | ID: The identifier for the click action. |
| `NBT` | Payload: The data to send with the click action. May be a TAG_END (0). |

---

### CUSTOM_PAYLOAD

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.8 | 0x17 | 23 |
| 1.9 - 1.11 | 0x9 | 9 |
| 1.12 - 1.12.0 | 0xA | 10 |
| 1.12.1 | 0x9 | 9 |
| 1.13 | 0xA | 10 |
| 1.14 - 1.16.2 | 0xB | 11 |
| 1.17 - 1.18 | 0xA | 10 |
| 1.19 - 1.19.0 | 0xC | 12 |
| 1.19.1 - 1.19.2 | 0xD | 13 |
| 1.19.3 | 0xC | 12 |
| 1.19.4 - 1.20.1 | 0xD | 13 |
| 1.20.2 | 0xF | 15 |
| 1.20.3 - 1.20.4 | 0x10 | 16 |
| 1.20.5 - 1.21.1 | 0x12 | 18 |
| 1.21.2 - 1.21.5 | 0x14 | 20 |
| 1.21.6 | 0x15 | 21 |

**Description:**

Mods and plugins can use this to send their data. Minecraft itself uses some plugin channels. These internal channels are in the minecraft namespace. More documentation on this: https://dinnerbone.com/blog/2012/01/13/minecraft-plugin-channels-messaging/ Note that the length of Data is known only from the packet length, since the packet has no length field of any kind.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `STRING` | Channel: Name of the plugin channel used to send the data. |
| `BYTE` | Data: Any data, depending on the channel. minecraft: channels are documented here. The length of this array must be inferred from the packet length. |
| `STRING` | Channel: Name of the plugin channel used to send the data. |
| `BYTE` | Data: Any data, depending on the channel. minecraft: channels are documented here. The length of this array must be inferred from the packet length. |

---

### DEBUG_SAMPLE_SUBSCRIPTION

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.20.5 - 1.21.1 | 0x13 | 19 |
| 1.21.2 - 1.21.5 | 0x15 | 21 |
| 1.21.6 | 0x16 | 22 |

**Description:**

Subscribes to the specified type of debug sample data, which is then sent periodically to the client via Debug Sample. The subscription is retained for 10 seconds (the vanilla server checks that both 10.001 real-time seconds and 201 ticks have elapsed), after which the client is automatically unsubscribed. The vanilla client resends this packet every 5 seconds to keep up the subscription. The vanilla server only allows subscriptions from players who are server operators.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `VAR_INT` | Sample Type: The type of debug sample to subscribe to. Can be one of the following:
0 - Tick time |
| `VAR_INT` | Sample Type: The type of debug sample to subscribe to. Can be one of the following:
0 - Tick time |

---

### EDIT_BOOK

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.13 | 0xB | 11 |
| 1.14 - 1.16.2 | 0xC | 12 |
| 1.17 - 1.18 | 0xB | 11 |
| 1.19 - 1.19.0 | 0xD | 13 |
| 1.19.1 - 1.19.2 | 0xE | 14 |
| 1.19.3 | 0xD | 13 |
| 1.19.4 - 1.20.1 | 0xE | 14 |
| 1.20.2 | 0x10 | 16 |
| 1.20.3 - 1.20.4 | 0x11 | 17 |
| 1.20.5 - 1.21.1 | 0x14 | 20 |
| 1.21.2 - 1.21.5 | 0x16 | 22 |
| 1.21.6 | 0x17 | 23 |

**Packet Fields:**

| Type | Description |
| --- | --- |
| `VAR_INT` | Slot: The hotbar slot where the written book is located |
| `STRING` | Entries: Text from each page. Maximum string length is 1024 chars. |
| `STRING` | Title: Title of book. Present if book is being signed, not present if book is being edited. |
| `VAR_INT` | Slot: The hotbar slot where the written book is located |
| `STRING` | Entries: Text from each page. Maximum string length is 1024 chars. |
| `STRING` | Title: Title of book. Present if book is being signed, not present if book is being edited. |

---

### ENTITY_TAG_QUERY

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.13 | 0xC | 12 |
| 1.14 - 1.16.2 | 0xD | 13 |
| 1.17 - 1.18 | 0xC | 12 |
| 1.19 - 1.19.0 | 0xE | 14 |
| 1.19.1 - 1.19.2 | 0xF | 15 |
| 1.19.3 | 0xE | 14 |
| 1.19.4 - 1.20.1 | 0xF | 15 |
| 1.20.2 | 0x11 | 17 |
| 1.20.3 - 1.20.4 | 0x12 | 18 |
| 1.20.5 - 1.21.1 | 0x15 | 21 |
| 1.21.2 - 1.21.5 | 0x17 | 23 |
| 1.21.6 | 0x18 | 24 |

**Description:**

Used when F3+I is pressed while looking at an entity.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `VAR_INT` | Transaction ID: An incremental ID so that the client can verify that the response matches. |
| `VAR_INT` | Entity ID: The ID of the entity to query. |

---

### INTERACT

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.8 | 0x2 | 2 |
| 1.9 - 1.11 | 0xA | 10 |
| 1.12 - 1.12.0 | 0xB | 11 |
| 1.12.1 | 0xA | 10 |
| 1.13 | 0xD | 13 |
| 1.14 - 1.16.2 | 0xE | 14 |
| 1.17 - 1.18 | 0xD | 13 |
| 1.19 - 1.19.0 | 0xF | 15 |
| 1.19.1 - 1.19.2 | 0x10 | 16 |
| 1.19.3 | 0xF | 15 |
| 1.19.4 - 1.20.1 | 0x10 | 16 |
| 1.20.2 | 0x12 | 18 |
| 1.20.3 - 1.20.4 | 0x13 | 19 |
| 1.20.5 - 1.21.1 | 0x16 | 22 |
| 1.21.2 - 1.21.5 | 0x18 | 24 |
| 1.21.6 | 0x19 | 25 |

**Description:**

This packet is sent from the client to the server when the client attacks or right-clicks another entity (a player, minecart, etc). A vanilla server only accepts this packet if the entity being attacked/used is visible without obstruction and within a 4-unit radius of the player's position. The target X, Y, and Z fields represent the difference between the vector location of the cursor at the time of the packet and the entity's position. Note that middle-click in creative mode is interpreted by the client and sent as a Set Creative Mode Slot packet instead.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `VAR_INT` | Entity ID: The ID of the entity to interact. Note the special case described below. |
| `VAR_INT` | Type: 0: interact, 1: attack, 2: interact at. |
| `FLOAT` | Target X: Only if Type is interact at. |
| `FLOAT` | Target Y: Only if Type is interact at. |
| `FLOAT` | Target Z: Only if Type is interact at. |
| `VAR_INT` | Hand: Only if Type is interact or interact at; 0: main hand, 1: off hand. |
| `BOOLEAN` | Sneak Key Pressed: If the client is pressing the sneak key. Has the same effect as a Player Command Press/Release sneak key preceding the interaction, and the state is permanently changed. |
| `VAR_INT` | Entity ID: The ID of the entity to interact. Note the special case described below. |
| `VAR_INT` | Type: 0: interact, 1: attack, 2: interact at. |
| `FLOAT` | Target X: Only if Type is interact at. |
| `FLOAT` | Target Y: Only if Type is interact at. |
| `FLOAT` | Target Z: Only if Type is interact at. |
| `VAR_INT` | Hand: Only if Type is interact or interact at; 0: main hand, 1: off hand. |
| `BOOLEAN` | Sneak Key Pressed: If the client is pressing the sneak key. Has the same effect as a Player Command Press/Release sneak key preceding the interaction, and the state is permanently changed. |

---

### JIGSAW_GENERATE

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.16 - 1.16.2 | 0xF | 15 |
| 1.17 - 1.18 | 0xE | 14 |
| 1.19 - 1.19.0 | 0x10 | 16 |
| 1.19.1 - 1.19.2 | 0x11 | 17 |
| 1.19.3 | 0x10 | 16 |
| 1.19.4 - 1.20.1 | 0x11 | 17 |
| 1.20.2 | 0x13 | 19 |
| 1.20.3 - 1.20.4 | 0x14 | 20 |
| 1.20.5 - 1.21.1 | 0x17 | 23 |
| 1.21.2 - 1.21.5 | 0x19 | 25 |
| 1.21.6 | 0x1A | 26 |

**Description:**

Sent when Generate is pressed on the Jigsaw Block interface.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `POSITION` | Location: Block entity location. |
| `VAR_INT` | Levels: Value of the levels slider/max depth to generate. |
| `BOOLEAN` | Keep Jigsaws |
| `POSITION` | Location: Block entity location. |
| `VAR_INT` | Levels: Value of the levels slider/max depth to generate. |
| `BOOLEAN` | Keep Jigsaws |

---

### KEEP_ALIVE

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.8 | 0x0 | 0 |
| 1.9 - 1.11 | 0xB | 11 |
| 1.12 - 1.12.0 | 0xC | 12 |
| 1.12.1 | 0xB | 11 |
| 1.13 | 0xE | 14 |
| 1.14 - 1.15 | 0xF | 15 |
| 1.16 - 1.16.2 | 0x10 | 16 |
| 1.17 - 1.18 | 0xF | 15 |
| 1.19 - 1.19.0 | 0x11 | 17 |
| 1.19.1 - 1.19.2 | 0x12 | 18 |
| 1.19.3 | 0x11 | 17 |
| 1.19.4 - 1.20.1 | 0x12 | 18 |
| 1.20.2 | 0x14 | 20 |
| 1.20.3 - 1.20.4 | 0x15 | 21 |
| 1.20.5 - 1.21.1 | 0x18 | 24 |
| 1.21.2 - 1.21.5 | 0x1A | 26 |
| 1.21.6 | 0x1B | 27 |

**Description:**

The server will frequently send out a keep-alive (see Clientbound Keep Alive), each containing a random ID. The client must respond with the same packet.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `LONG` | Keep Alive ID |
| `LONG` | Keep Alive ID |

---

### LOCK_DIFFICULTY

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.14 - 1.15 | 0x10 | 16 |
| 1.16 - 1.16.2 | 0x11 | 17 |
| 1.17 - 1.18 | 0x10 | 16 |
| 1.19 - 1.19.0 | 0x12 | 18 |
| 1.19.1 - 1.19.2 | 0x13 | 19 |
| 1.19.3 | 0x12 | 18 |
| 1.19.4 - 1.20.1 | 0x13 | 19 |
| 1.20.2 | 0x15 | 21 |
| 1.20.3 - 1.20.4 | 0x16 | 22 |
| 1.20.5 - 1.21.1 | 0x19 | 25 |
| 1.21.2 - 1.21.5 | 0x1B | 27 |
| 1.21.6 | 0x1C | 28 |

**Description:**

Must have at least op level 2 to use.  Appears to only be used on singleplayer; the difficulty buttons are still disabled in multiplayer.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `BOOLEAN` | Locked |
| `BOOLEAN` | Locked |

---

### MOVE_PLAYER_POS

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.8 | 0x4 | 4 |
| 1.9 - 1.11 | 0xC | 12 |
| 1.12 - 1.12.0 | 0xE | 14 |
| 1.12.1 | 0xD | 13 |
| 1.13 | 0x10 | 16 |
| 1.14 - 1.15 | 0x11 | 17 |
| 1.16 - 1.16.2 | 0x12 | 18 |
| 1.17 - 1.18 | 0x11 | 17 |
| 1.19 - 1.19.0 | 0x13 | 19 |
| 1.19.1 - 1.19.2 | 0x14 | 20 |
| 1.19.3 | 0x13 | 19 |
| 1.19.4 - 1.20.1 | 0x14 | 20 |
| 1.20.2 | 0x16 | 22 |
| 1.20.3 - 1.20.4 | 0x17 | 23 |
| 1.20.5 - 1.21.1 | 0x1A | 26 |
| 1.21.2 - 1.21.5 | 0x1C | 28 |
| 1.21.6 | 0x1D | 29 |

**Description:**

Updates the player's XYZ position on the server. If the player is in a vehicle, the position is ignored (but in case of Set Player Position and Rotation, the rotation is still used as normal). No validation steps other than value range clamping are performed in this case. If the player is sleeping, the position (or rotation) is not changed, and a Synchronize Player Position is sent if the received position deviated from the server's view by more than a meter. The vanilla server silently clamps the x and z coordinates between -30,000,000 and 30,000,000, and the y coordinate between -20,000,000 and 20,000,000. A similar condition has historically caused a kick for "Illegal position"; this is no longer the case. However, infinite or NaN coordinates (or angles) still result in a kick for multiplayer.disconnect.invalid_player_movement. As of 1.20.6, checking for moving too fast is achieved like this (sic): If the player is moving too fast, it is logged that " moved too quickly! " followed by the change in x, y, and z, and the player is teleported back to their current (before this packet) server-side position. Checking for block collisions is achieved like this: Checking for illegal flight is achieved like this:

**Packet Fields:**

| Type | Description |
| --- | --- |
| `DOUBLE` | X: Absolute position. |
| `DOUBLE` | Feet Y: Absolute feet position, normally Head Y - 1.62. |
| `DOUBLE` | Z: Absolute position. |
| `BYTE` | Flags: Bit field: 0x01: on ground, 0x02: pushing against wall. |

---

### MOVE_PLAYER_POS_ROT

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.8 | 0x6 | 6 |
| 1.9 - 1.11 | 0xD | 13 |
| 1.12 - 1.12.0 | 0xF | 15 |
| 1.12.1 | 0xE | 14 |
| 1.13 | 0x11 | 17 |
| 1.14 - 1.15 | 0x12 | 18 |
| 1.16 - 1.16.2 | 0x13 | 19 |
| 1.17 - 1.18 | 0x12 | 18 |
| 1.19 - 1.19.0 | 0x14 | 20 |
| 1.19.1 - 1.19.2 | 0x15 | 21 |
| 1.19.3 | 0x14 | 20 |
| 1.19.4 - 1.20.1 | 0x15 | 21 |
| 1.20.2 | 0x17 | 23 |
| 1.20.3 - 1.20.4 | 0x18 | 24 |
| 1.20.5 - 1.21.1 | 0x1B | 27 |
| 1.21.2 - 1.21.5 | 0x1D | 29 |
| 1.21.6 | 0x1E | 30 |

**Description:**

A combination of Move Player Rotation and Move Player Position.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `DOUBLE` | X: Absolute position. |
| `DOUBLE` | Feet Y: Absolute feet position, normally Head Y - 1.62. |
| `DOUBLE` | Z: Absolute position. |
| `FLOAT` | Yaw: Absolute rotation on the X Axis, in degrees. |
| `FLOAT` | Pitch: Absolute rotation on the Y Axis, in degrees. |
| `BYTE` | Flags: Bit field: 0x01: on ground, 0x02: pushing against wall. |

---

### MOVE_PLAYER_ROT

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.8 | 0x5 | 5 |
| 1.9 - 1.11 | 0xE | 14 |
| 1.12 - 1.12.0 | 0x10 | 16 |
| 1.12.1 | 0xF | 15 |
| 1.13 | 0x12 | 18 |
| 1.14 - 1.15 | 0x13 | 19 |
| 1.16 - 1.16.2 | 0x14 | 20 |
| 1.17 - 1.18 | 0x13 | 19 |
| 1.19 - 1.19.0 | 0x15 | 21 |
| 1.19.1 - 1.19.2 | 0x16 | 22 |
| 1.19.3 | 0x15 | 21 |
| 1.19.4 - 1.20.1 | 0x16 | 22 |
| 1.20.2 | 0x18 | 24 |
| 1.20.3 - 1.20.4 | 0x19 | 25 |
| 1.20.5 - 1.21.1 | 0x1C | 28 |
| 1.21.2 - 1.21.5 | 0x1E | 30 |
| 1.21.6 | 0x1F | 31 |

**Description:**

Updates the direction the player is looking in. Yaw is measured in degrees and does not follow classical trigonometry rules. The unit circle of yaw on the XZ-plane starts at (0, 1) and turns counterclockwise, with 90 at (-1, 0), 180 at (0,-1) and 270 at (1, 0). Additionally, yaw is not clamped to between 0 and 360 degrees; any number is valid, including negative numbers and numbers greater than 360. Pitch is measured in degrees, where 0 is looking straight ahead, -90 is looking straight up, and 90 is looking straight down. The yaw and pitch of the player (in degrees), standing at point (x0, y0, z0) and looking towards point (x, y, z) can be calculated with: You can get a unit vector from a given yaw/pitch via:

**Packet Fields:**

| Type | Description |
| --- | --- |
| `FLOAT` | Yaw: Absolute rotation on the X Axis, in degrees. |
| `FLOAT` | Pitch: Absolute rotation on the Y Axis, in degrees. |
| `BYTE` | Flags: Bit field: 0x01: on ground, 0x02: pushing against wall. |

---

### MOVE_PLAYER_STATUS_ONLY

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.8 | 0x3 | 3 |
| 1.9 - 1.11 | 0xF | 15 |
| 1.12 - 1.12.0 | 0xD | 13 |
| 1.12.1 | 0xC | 12 |
| 1.13 | 0xF | 15 |
| 1.14 - 1.15 | 0x14 | 20 |
| 1.16 - 1.16.2 | 0x15 | 21 |
| 1.17 - 1.18 | 0x14 | 20 |
| 1.19 - 1.19.0 | 0x16 | 22 |
| 1.19.1 - 1.19.2 | 0x17 | 23 |
| 1.19.3 | 0x16 | 22 |
| 1.19.4 - 1.20.1 | 0x17 | 23 |
| 1.20.2 | 0x19 | 25 |
| 1.20.3 - 1.20.4 | 0x1A | 26 |
| 1.20.5 - 1.21.1 | 0x1D | 29 |
| 1.21.2 - 1.21.5 | 0x1F | 31 |
| 1.21.6 | 0x20 | 32 |

**Description:**

This packet, as well as Set Player Position, Set Player Rotation, and Set Player Position and Rotation are called the “serverbound movement packets”. Vanilla clients will send Move Player Position once every 20 ticks, even for a stationary player. This packet is used to indicate whether the player is on ground (walking/swimming) or airborne (jumping/falling). When dropping from a sufficient height, fall damage is applied when this state goes from false to true. The amount of damage applied is based on the point where it last changed from true to false. Note that there are several movement related packets containing this state.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `BYTE` | Flags: Bit field: 0x01: on ground, 0x02: pushing against wall. |

---

### MOVE_VEHICLE

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.9 - 1.11 | 0x10 | 16 |
| 1.12 - 1.12.0 | 0x11 | 17 |
| 1.12.1 | 0x10 | 16 |
| 1.13 | 0x13 | 19 |
| 1.14 - 1.15 | 0x15 | 21 |
| 1.16 - 1.16.2 | 0x16 | 22 |
| 1.17 - 1.18 | 0x15 | 21 |
| 1.19 - 1.19.0 | 0x17 | 23 |
| 1.19.1 - 1.19.2 | 0x18 | 24 |
| 1.19.3 | 0x17 | 23 |
| 1.19.4 - 1.20.1 | 0x18 | 24 |
| 1.20.2 | 0x1A | 26 |
| 1.20.3 - 1.20.4 | 0x1B | 27 |
| 1.20.5 - 1.21.1 | 0x1E | 30 |
| 1.21.2 - 1.21.5 | 0x20 | 32 |
| 1.21.6 | 0x21 | 33 |

**Description:**

Sent when a player moves in a client-side-controlled vehicle. Fields are the same as in Set Player Position and Rotation. Note that all fields use absolute positioning and do not allow for relative positioning.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `DOUBLE` | X: Absolute position (X coordinate). |
| `DOUBLE` | Y: Absolute position (Y coordinate). |
| `DOUBLE` | Z: Absolute position (Z coordinate). |
| `FLOAT` | Yaw: Absolute rotation on the vertical axis, in degrees. |
| `FLOAT` | Pitch: Absolute rotation on the horizontal axis, in degrees. |
| `BOOLEAN` | On Ground: (This value does not seem to exist) |

---

### PADDLE_BOAT

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.9 - 1.11 | 0x11 | 17 |
| 1.12 - 1.12.0 | 0x12 | 18 |
| 1.12.1 | 0x11 | 17 |
| 1.13 | 0x14 | 20 |
| 1.14 - 1.15 | 0x16 | 22 |
| 1.16 - 1.16.2 | 0x17 | 23 |
| 1.17 - 1.18 | 0x16 | 22 |
| 1.19 - 1.19.0 | 0x18 | 24 |
| 1.19.1 - 1.19.2 | 0x19 | 25 |
| 1.19.3 | 0x18 | 24 |
| 1.19.4 - 1.20.1 | 0x19 | 25 |
| 1.20.2 | 0x1B | 27 |
| 1.20.3 - 1.20.4 | 0x1C | 28 |
| 1.20.5 - 1.21.1 | 0x1F | 31 |
| 1.21.2 - 1.21.5 | 0x21 | 33 |
| 1.21.6 | 0x22 | 34 |

**Description:**

Used to visually update whether boat paddles are turning.  The server will update the Boat entity metadata to match the values here.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `BOOLEAN` | Left paddle turning |
| `BOOLEAN` | Right paddle turning |
| `BOOLEAN` | Left paddle turning |
| `BOOLEAN` | Right paddle turning |

---

### PICK_ITEM

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.13 | 0x15 | 21 |
| 1.14 - 1.15 | 0x17 | 23 |
| 1.16 - 1.16.2 | 0x18 | 24 |
| 1.17 - 1.18 | 0x17 | 23 |
| 1.19 - 1.19.0 | 0x19 | 25 |
| 1.19.1 - 1.19.2 | 0x1A | 26 |
| 1.19.3 | 0x19 | 25 |
| 1.19.4 - 1.20.1 | 0x1A | 26 |
| 1.20.2 | 0x1C | 28 |
| 1.20.3 - 1.20.4 | 0x1D | 29 |
| 1.20.5 - 1.21.1 | 0x20 | 32 |
| 1.21.2 | 0x22 | 34 |

---

### PICK_ITEM_FROM_BLOCK

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.21.4 - 1.21.5 | 0x22 | 34 |
| 1.21.6 | 0x23 | 35 |

**Description:**

Used for pick block functionality (middle click) on blocks to retrieve items from the inventory in survival or creative mode or create them in creative mode.  See Controls#Pick_Block for more information.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `POSITION` | Location: The location of the block. |
| `BOOLEAN` | Include Data: Used to tell the server to include block data in the new stack, works only if in creative mode. |
| `POSITION` | Location: The location of the block. |
| `BOOLEAN` | Include Data: Used to tell the server to include block data in the new stack, works only if in creative mode. |

---

### PICK_ITEM_FROM_ENTITY

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.21.4 - 1.21.5 | 0x23 | 35 |
| 1.21.6 | 0x24 | 36 |

**Description:**

Used for pick block functionality (middle click) on entities to retrieve items from the inventory in survival or creative mode or create them in creative mode.  See Controls#Pick_Block for more information.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `VAR_INT` | Entity ID: The ID of the entity to pick. |
| `BOOLEAN` | Include Data: Unused by the vanilla server. |
| `VAR_INT` | Entity ID: The ID of the entity to pick. |
| `BOOLEAN` | Include Data: Unused by the vanilla server. |

---

### PING_REQUEST

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.20.2 | 0x1D | 29 |
| 1.20.3 - 1.20.4 | 0x1E | 30 |
| 1.20.5 - 1.21.1 | 0x21 | 33 |
| 1.21.2 - 1.21.3 | 0x23 | 35 |
| 1.21.4 - 1.21.5 | 0x24 | 36 |
| 1.21.6 | 0x25 | 37 |

**Packet Fields:**

| Type | Description |
| --- | --- |
| `LONG` | Timestamp: May be any number, but vanilla clients will always use the timestamp in milliseconds. |
| `LONG` | Payload: May be any number. vanilla clients use a system-dependent time value, which is counted in milliseconds. |

---

### PLACE_RECIPE

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.12.1 | 0x12 | 18 |
| 1.13 | 0x16 | 22 |
| 1.14 - 1.15 | 0x18 | 24 |
| 1.16 - 1.16.2 | 0x19 | 25 |
| 1.17 - 1.18 | 0x18 | 24 |
| 1.19 - 1.19.0 | 0x1A | 26 |
| 1.19.1 - 1.19.2 | 0x1B | 27 |
| 1.19.3 | 0x1A | 26 |
| 1.19.4 - 1.20.1 | 0x1B | 27 |
| 1.20.2 | 0x1E | 30 |
| 1.20.3 - 1.20.4 | 0x1F | 31 |
| 1.20.5 - 1.21.1 | 0x22 | 34 |
| 1.21.2 - 1.21.3 | 0x24 | 36 |
| 1.21.4 - 1.21.5 | 0x25 | 37 |
| 1.21.6 | 0x26 | 38 |

**Description:**

This packet is sent when a player clicks a recipe in the crafting book that is craftable (white border).

**Packet Fields:**

| Type | Description |
| --- | --- |
| `VAR_INT` | Window ID |
| `VAR_INT` | Recipe ID: ID of recipe previously defined in Recipe Book Add. |
| `BOOLEAN` | Make all: Affects the amount of items processed; true if shift is down when clicked. |
| `VAR_INT` | Window ID |
| `VAR_INT` | Recipe ID: ID of recipe previously defined in Recipe Book Add. |
| `BOOLEAN` | Make all: Affects the amount of items processed; true if shift is down when clicked. |

---

### PLAYER_ABILITIES

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.8 | 0x13 | 19 |
| 1.9 - 1.11 | 0x12 | 18 |
| 1.12 - 1.12.1 | 0x13 | 19 |
| 1.13 | 0x17 | 23 |
| 1.14 - 1.15 | 0x19 | 25 |
| 1.16 - 1.16.2 | 0x1A | 26 |
| 1.17 - 1.18 | 0x19 | 25 |
| 1.19 - 1.19.0 | 0x1B | 27 |
| 1.19.1 - 1.19.2 | 0x1C | 28 |
| 1.19.3 | 0x1B | 27 |
| 1.19.4 - 1.20.1 | 0x1C | 28 |
| 1.20.2 | 0x1F | 31 |
| 1.20.3 - 1.20.4 | 0x20 | 32 |
| 1.20.5 - 1.21.1 | 0x23 | 35 |
| 1.21.2 - 1.21.3 | 0x25 | 37 |
| 1.21.4 - 1.21.5 | 0x26 | 38 |
| 1.21.6 | 0x27 | 39 |

**Description:**

The vanilla client sends this packet when the player starts/stops flying with the Flags parameter changed accordingly.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `BYTE` | Flags: Bit mask. 0x02: is flying. |

---

### PLAYER_ACTION

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.8 | 0x7 | 7 |
| 1.9 - 1.11 | 0x13 | 19 |
| 1.12 - 1.12.1 | 0x14 | 20 |
| 1.13 | 0x18 | 24 |
| 1.14 - 1.15 | 0x1A | 26 |
| 1.16 - 1.16.2 | 0x1B | 27 |
| 1.17 - 1.18 | 0x1A | 26 |
| 1.19 - 1.19.0 | 0x1C | 28 |
| 1.19.1 - 1.19.2 | 0x1D | 29 |
| 1.19.3 | 0x1C | 28 |
| 1.19.4 - 1.20.1 | 0x1D | 29 |
| 1.20.2 | 0x20 | 32 |
| 1.20.3 - 1.20.4 | 0x21 | 33 |
| 1.20.5 - 1.21.1 | 0x24 | 36 |
| 1.21.2 - 1.21.3 | 0x26 | 38 |
| 1.21.4 - 1.21.5 | 0x27 | 39 |
| 1.21.6 | 0x28 | 40 |

**Description:**

Sent when the player mines a block. A vanilla server only accepts digging packets with coordinates within a 6-unit radius between the center of the block and the player's eyes.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `VAR_INT` | Status: The action the player is taking against the block (see below). |
| `POSITION` | Location: Block position. |
| `BYTE` | Face: The face being hit (see below). |
| `VAR_INT` | Sequence: Block change sequence number (see #Acknowledge Block Change). |
| `VAR_INT` | Status: The action the player is taking against the block (see below). |
| `POSITION` | Location: Block position. |
| `BYTE` | Face: The face being hit (see below). |
| `VAR_INT` | Sequence: Block change sequence number (see #Acknowledge Block Change). |

---

### PLAYER_COMMAND

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.8 | 0xB | 11 |
| 1.9 - 1.11 | 0x14 | 20 |
| 1.12 - 1.12.1 | 0x15 | 21 |
| 1.13 | 0x19 | 25 |
| 1.14 - 1.15 | 0x1B | 27 |
| 1.16 - 1.16.2 | 0x1C | 28 |
| 1.17 - 1.18 | 0x1B | 27 |
| 1.19 - 1.19.0 | 0x1D | 29 |
| 1.19.1 - 1.19.2 | 0x1E | 30 |
| 1.19.3 | 0x1D | 29 |
| 1.19.4 - 1.20.1 | 0x1E | 30 |
| 1.20.2 | 0x21 | 33 |
| 1.20.3 - 1.20.4 | 0x22 | 34 |
| 1.20.5 - 1.21.1 | 0x25 | 37 |
| 1.21.2 - 1.21.3 | 0x27 | 39 |
| 1.21.4 - 1.21.5 | 0x28 | 40 |
| 1.21.6 | 0x29 | 41 |

**Description:**

Sent by the client to indicate that it has performed certain actions: sprinting, exiting a bed, jumping with a horse, and opening a horse's inventory while riding it.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `VAR_INT` | Entity ID: Player ID (ignored by the vanilla server) |
| `VAR_INT` | Action ID: The ID of the action, see below. |
| `VAR_INT` | Jump Boost: Only used by the “start jump with horse” action, in which case it ranges from 0 to 100. In all other cases it is 0. |
| `VAR_INT` | Entity ID: Player ID (ignored by the vanilla server) |
| `VAR_INT` | Action ID: The ID of the action, see below. |
| `VAR_INT` | Jump Boost: Only used by the “start jump with horse” action, in which case it ranges from 0 to 100. In all other cases it is 0. |

---

### PLAYER_INPUT

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.8 | 0xC | 12 |
| 1.9 - 1.11 | 0x15 | 21 |
| 1.12 - 1.12.1 | 0x16 | 22 |
| 1.13 | 0x1A | 26 |
| 1.14 - 1.15 | 0x1C | 28 |
| 1.16 - 1.16.2 | 0x1D | 29 |
| 1.17 - 1.18 | 0x1C | 28 |
| 1.19 - 1.19.0 | 0x1E | 30 |
| 1.19.1 - 1.19.2 | 0x1F | 31 |
| 1.19.3 | 0x1E | 30 |
| 1.19.4 - 1.20.1 | 0x1F | 31 |
| 1.20.2 | 0x22 | 34 |
| 1.20.3 - 1.20.4 | 0x23 | 35 |
| 1.20.5 - 1.21.1 | 0x26 | 38 |
| 1.21.2 - 1.21.3 | 0x28 | 40 |
| 1.21.4 - 1.21.5 | 0x29 | 41 |
| 1.21.6 | 0x2A | 42 |

**Description:**

Sent whenever the player presses or releases certain keys. The flags correspond directly to the states of their corresponding keys—the Sprint flag does not depend on whether the player is actually able to sprint at the moment, etc. Used by the vanilla server for minecart controls, player inputs in the entity_properties predicate, and sneaking (sprinting is still controlled by Player Command).

**Packet Fields:**

| Type | Description |
| --- | --- |
| `BYTE` | Flags: Bit mask; see below |
| `BYTE` | Flags: Bit mask; see below |

---

### PLAYER_LOADED

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.21.4 - 1.21.5 | 0x2A | 42 |
| 1.21.6 | 0x2B | 43 |

**Description:**

Sent by the client to indicate that it is ready to start simulating the player. The vanilla client sends this when the "Loading terrain..." screen is closed. (But see the caveat below.) The vanilla client skips ticking the player entity until the tick on which this packet is sent (the first tick will happen between this packet and the next Client Tick End). Other entities and objects will still be ticked. Once 60 ticks have elapsed since the last Login or Respawn packet, the vanilla client will start ticking the player and skip sending this packet completely, even after the usual conditions for it have been met. This can happen even before the "Start waiting for level chunks" Game Event is received. The loading screen is not affected in any way by this timer (except indirectly by the player falling into the void after ticking has started). Likewise, the vanilla server will assume that the client has loaded if it takes longer than 60 server ticks to send this packet. A more robust way to detect this condition is to count the number of Client Tick End packets sent by the client. The first player tick will occur after 60 Client Tick End packets have been sent. To determine when this counter should be restarted following a respawn, the Respawn packet can be sent in a bundle together with a Ping packet.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `SERVER` | Play: no fields |
| `SERVER` | Play: no fields |

---

### PONG

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.17 - 1.18 | 0x1D | 29 |
| 1.19 - 1.19.0 | 0x1F | 31 |
| 1.19.1 - 1.19.2 | 0x20 | 32 |
| 1.19.3 | 0x1F | 31 |
| 1.19.4 - 1.20.1 | 0x20 | 32 |
| 1.20.2 | 0x23 | 35 |
| 1.20.3 - 1.20.4 | 0x24 | 36 |
| 1.20.5 - 1.21.1 | 0x27 | 39 |
| 1.21.2 - 1.21.3 | 0x29 | 41 |
| 1.21.4 - 1.21.5 | 0x2B | 43 |
| 1.21.6 | 0x2C | 44 |

**Description:**

Response to the clientbound packet (Ping) with the same id.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `INT` | ID |
| `INT` | ID: id is the same as the ping packet |

---

### RECIPE_BOOK_CHANGE_SETTINGS

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.16.2 - 1.18 | 0x1E | 30 |
| 1.19 - 1.19.0 | 0x20 | 32 |
| 1.19.1 - 1.20.1 | 0x21 | 33 |
| 1.20.2 | 0x24 | 36 |
| 1.20.3 - 1.20.4 | 0x25 | 37 |
| 1.20.5 - 1.21.1 | 0x28 | 40 |
| 1.21.2 - 1.21.3 | 0x2A | 42 |
| 1.21.4 - 1.21.5 | 0x2C | 44 |
| 1.21.6 | 0x2D | 45 |

**Description:**

Replaces Recipe Book Data, type 1.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `VAR_INT` | Book ID: 0: crafting, 1: furnace, 2: blast furnace, 3: smoker. |
| `BOOLEAN` | Book Open |
| `BOOLEAN` | Filter Active |

---

### RECIPE_BOOK_SEEN_RECIPE

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.16.2 - 1.18 | 0x1F | 31 |
| 1.19 - 1.19.0 | 0x21 | 33 |
| 1.19.1 - 1.20.1 | 0x22 | 34 |
| 1.20.2 | 0x25 | 37 |
| 1.20.3 - 1.20.4 | 0x26 | 38 |
| 1.20.5 - 1.21.1 | 0x29 | 41 |
| 1.21.2 - 1.21.3 | 0x2B | 43 |
| 1.21.4 - 1.21.5 | 0x2D | 45 |
| 1.21.6 | 0x2E | 46 |

**Description:**

Sent when recipe is first seen in recipe book. Replaces Recipe Book Data, type 0.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `VAR_INT` | Recipe ID: ID of recipe previously defined in Recipe Book Add. |

---

### RECIPE_BOOK_UPDATE

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.12 - 1.12.1 | 0x17 | 23 |
| 1.13 | 0x1B | 27 |
| 1.14 - 1.15 | 0x1D | 29 |
| 1.16 | 0x1E | 30 |

---

### RENAME_ITEM

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.13 | 0x1C | 28 |
| 1.14 - 1.15 | 0x1E | 30 |
| 1.16 - 1.16.1 | 0x1F | 31 |
| 1.16.2 - 1.18 | 0x20 | 32 |
| 1.19 - 1.19.0 | 0x22 | 34 |
| 1.19.1 - 1.20.1 | 0x23 | 35 |
| 1.20.2 | 0x26 | 38 |
| 1.20.3 - 1.20.4 | 0x27 | 39 |
| 1.20.5 - 1.21.1 | 0x2A | 42 |
| 1.21.2 - 1.21.3 | 0x2C | 44 |
| 1.21.4 - 1.21.5 | 0x2E | 46 |
| 1.21.6 | 0x2F | 47 |

**Description:**

Sent as a player is renaming an item in an anvil (each keypress in the anvil UI sends a new Rename Item packet). If the new name is empty, then the item loses its custom name (this is different from setting the custom name to the normal name of the item). The item name may be no longer than 50 characters, and if it is longer than that, then the rename is silently ignored.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `STRING` | Item name: The new name of the item. |
| `STRING` | Item name: The new name of the item. |

---

### RESOURCE_PACK

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.8 | 0x19 | 25 |
| 1.9 - 1.11 | 0x16 | 22 |
| 1.12 - 1.12.1 | 0x18 | 24 |
| 1.13 | 0x1D | 29 |
| 1.14 - 1.15 | 0x1F | 31 |
| 1.16 - 1.16.1 | 0x20 | 32 |
| 1.16.2 - 1.18 | 0x21 | 33 |
| 1.19 - 1.19.0 | 0x23 | 35 |
| 1.19.1 - 1.20.1 | 0x24 | 36 |
| 1.20.2 | 0x27 | 39 |
| 1.20.3 - 1.20.4 | 0x28 | 40 |
| 1.20.5 - 1.21.1 | 0x2B | 43 |
| 1.21.2 - 1.21.3 | 0x2D | 45 |
| 1.21.4 - 1.21.5 | 0x2F | 47 |
| 1.21.6 | 0x30 | 48 |

**Packet Fields:**

| Type | Description |
| --- | --- |
| `UUID` | UUID: The unique identifier of the resource pack received in the Add Resource Pack (configuration) request. |
| `VAR_INT` | Result: Result ID (see below). |
| `UUID` | UUID: The unique identifier of the resource pack received in the Add Resource Pack (play) request. |
| `VAR_INT` | Result: Result ID (see below). |

---

### SEEN_ADVANCEMENTS

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.12 - 1.12.1 | 0x19 | 25 |
| 1.13 | 0x1E | 30 |
| 1.14 - 1.15 | 0x20 | 32 |
| 1.16 - 1.16.1 | 0x21 | 33 |
| 1.16.2 - 1.18 | 0x22 | 34 |
| 1.19 - 1.19.0 | 0x24 | 36 |
| 1.19.1 - 1.20.1 | 0x25 | 37 |
| 1.20.2 | 0x28 | 40 |
| 1.20.3 - 1.20.4 | 0x29 | 41 |
| 1.20.5 - 1.21.1 | 0x2C | 44 |
| 1.21.2 - 1.21.3 | 0x2E | 46 |
| 1.21.4 - 1.21.5 | 0x30 | 48 |
| 1.21.6 | 0x31 | 49 |

**Packet Fields:**

| Type | Description |
| --- | --- |
| `VAR_INT` | Action: 0: Opened tab, 1: Closed screen. |
| `STRING` | Tab ID: Only present if action is Opened tab. |
| `VAR_INT` | Action: 0: Opened tab, 1: Closed screen. |
| `STRING` | Tab ID: Only present if action is Opened tab. |

---

### SELECT_TRADE

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.13 | 0x1F | 31 |
| 1.14 - 1.15 | 0x21 | 33 |
| 1.16 - 1.16.1 | 0x22 | 34 |
| 1.16.2 - 1.18 | 0x23 | 35 |
| 1.19 - 1.19.0 | 0x25 | 37 |
| 1.19.1 - 1.20.1 | 0x26 | 38 |
| 1.20.2 | 0x29 | 41 |
| 1.20.3 - 1.20.4 | 0x2A | 42 |
| 1.20.5 - 1.21.1 | 0x2D | 45 |
| 1.21.2 - 1.21.3 | 0x2F | 47 |
| 1.21.4 - 1.21.5 | 0x31 | 49 |
| 1.21.6 | 0x32 | 50 |

**Description:**

When a player selects a specific trade offered by a villager NPC.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `VAR_INT` | Selected slot: The selected slot in the player's current (trading) inventory. |
| `VAR_INT` | Selected slot: The selected slot in the player's current (trading) inventory. |

---

### SET_BEACON

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.13 | 0x20 | 32 |
| 1.14 - 1.15 | 0x22 | 34 |
| 1.16 - 1.16.1 | 0x23 | 35 |
| 1.16.2 - 1.18 | 0x24 | 36 |
| 1.19 - 1.19.0 | 0x26 | 38 |
| 1.19.1 - 1.20.1 | 0x27 | 39 |
| 1.20.2 | 0x2A | 42 |
| 1.20.3 - 1.20.4 | 0x2B | 43 |
| 1.20.5 - 1.21.1 | 0x2E | 46 |
| 1.21.2 - 1.21.3 | 0x30 | 48 |
| 1.21.4 - 1.21.5 | 0x32 | 50 |
| 1.21.6 | 0x33 | 51 |

**Description:**

Changes the effect of the current beacon.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `VAR_INT` | Primary Effect: A Potion ID. |
| `VAR_INT` | Secondary Effect: A Potion ID. |

---

### SET_CARRIED_ITEM

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.8 | 0x9 | 9 |
| 1.9 - 1.11 | 0x17 | 23 |
| 1.12 - 1.12.1 | 0x1A | 26 |
| 1.13 | 0x21 | 33 |
| 1.14 - 1.15 | 0x23 | 35 |
| 1.16 - 1.16.1 | 0x24 | 36 |
| 1.16.2 - 1.18 | 0x25 | 37 |
| 1.19 - 1.19.0 | 0x27 | 39 |
| 1.19.1 - 1.20.1 | 0x28 | 40 |
| 1.20.2 | 0x2B | 43 |
| 1.20.3 - 1.20.4 | 0x2C | 44 |
| 1.20.5 - 1.21.1 | 0x2F | 47 |
| 1.21.2 - 1.21.3 | 0x31 | 49 |
| 1.21.4 - 1.21.5 | 0x33 | 51 |
| 1.21.6 | 0x34 | 52 |

**Description:**

Sent when the player changes the slot selection.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `SHORT` | Slot: The slot which the player has selected (0–8). |

---

### SET_COMMAND_BLOCK

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.13 | 0x22 | 34 |
| 1.14 - 1.15 | 0x24 | 36 |
| 1.16 - 1.16.1 | 0x25 | 37 |
| 1.16.2 - 1.18 | 0x26 | 38 |
| 1.19 - 1.19.0 | 0x28 | 40 |
| 1.19.1 - 1.20.1 | 0x29 | 41 |
| 1.20.2 | 0x2C | 44 |
| 1.20.3 - 1.20.4 | 0x2D | 45 |
| 1.20.5 - 1.21.1 | 0x30 | 48 |
| 1.21.2 - 1.21.3 | 0x32 | 50 |
| 1.21.4 - 1.21.5 | 0x34 | 52 |
| 1.21.6 | 0x35 | 53 |

**Packet Fields:**

| Type | Description |
| --- | --- |
| `POSITION` | Location |
| `STRING` | Command |
| `VAR_INT` | Mode: 0: chain, 1: repeating, 2: impulse. |
| `BYTE` | Flags: 0x01: Track Output (if false, the output of the previous command will not be stored within the command block); 0x02: Is conditional; 0x04: Automatic. |

---

### SET_COMMAND_MINECART

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.13 | 0x23 | 35 |
| 1.14 - 1.15 | 0x25 | 37 |
| 1.16 - 1.16.1 | 0x26 | 38 |
| 1.16.2 - 1.18 | 0x27 | 39 |
| 1.19 - 1.19.0 | 0x29 | 41 |
| 1.19.1 - 1.20.1 | 0x2A | 42 |
| 1.20.2 | 0x2D | 45 |
| 1.20.3 - 1.20.4 | 0x2E | 46 |
| 1.20.5 - 1.21.1 | 0x31 | 49 |
| 1.21.2 - 1.21.3 | 0x33 | 51 |
| 1.21.4 - 1.21.5 | 0x35 | 53 |
| 1.21.6 | 0x36 | 54 |

**Packet Fields:**

| Type | Description |
| --- | --- |
| `VAR_INT` | Entity ID |
| `STRING` | Command |
| `BOOLEAN` | Track Output: If false, the output of the previous command will not be stored within the command block. |

---

### SET_CREATIVE_MODE_SLOT

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.8 | 0x10 | 16 |
| 1.9 - 1.11 | 0x18 | 24 |
| 1.12 - 1.12.1 | 0x1B | 27 |
| 1.13 | 0x24 | 36 |
| 1.14 - 1.15 | 0x26 | 38 |
| 1.16 - 1.16.1 | 0x27 | 39 |
| 1.16.2 - 1.18 | 0x28 | 40 |
| 1.19 - 1.19.0 | 0x2A | 42 |
| 1.19.1 - 1.20.1 | 0x2B | 43 |
| 1.20.2 | 0x2E | 46 |
| 1.20.3 - 1.20.4 | 0x2F | 47 |
| 1.20.5 - 1.21.1 | 0x32 | 50 |
| 1.21.2 - 1.21.3 | 0x34 | 52 |
| 1.21.4 - 1.21.5 | 0x36 | 54 |
| 1.21.6 | 0x37 | 55 |

**Description:**

While the user is in the standard inventory (i.e., not a crafting bench) in Creative mode, the player will send this packet. Clicking in the creative inventory menu is quite different from non-creative inventory management. Picking up an item with the mouse actually deletes the item from the server, and placing an item into a slot or dropping it out of the inventory actually tells the server to create the item from scratch. (This can be verified by clicking an item that you don't mind deleting, then severing the connection to the server; the item will be nowhere to be found when you log back in.) As a result of this implementation strategy, the "Destroy Item" slot is just a client-side implementation detail that means "I don't intend to recreate this item.". Additionally, the long listings of items (by category, etc.) are a client-side interface for choosing which item to create. Picking up an item from such listings sends no packets to the server; only when you put it somewhere does it tell the server to create the item in that location. This action can be described as "set inventory slot". Picking up an item sets the slot to item ID -1. Placing an item into an inventory slot sets the slot to the specified item. Dropping an item (by clicking outside the window) effectively sets slot -1 to the specified item, which causes the server to spawn the item entity, etc.. All other inventory slots are numbered the same as the non-creative inventory (including slots for the 2x2 crafting menu, even though they aren't visible in the vanilla client).

**Packet Fields:**

| Type | Description |
| --- | --- |
| `SHORT` | Slot: Inventory slot. |
| `SLOT` | Clicked Item |
| `SHORT` | Slot: Inventory slot. |
| `SLOT` | Clicked Item |

---

### SET_JIGSAW_BLOCK

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.14 - 1.15 | 0x27 | 39 |
| 1.16 - 1.16.1 | 0x28 | 40 |
| 1.16.2 - 1.18 | 0x29 | 41 |
| 1.19 - 1.19.0 | 0x2B | 43 |
| 1.19.1 - 1.20.1 | 0x2C | 44 |
| 1.20.2 | 0x2F | 47 |
| 1.20.3 - 1.20.4 | 0x30 | 48 |
| 1.20.5 - 1.21.1 | 0x33 | 51 |
| 1.21.2 - 1.21.3 | 0x35 | 53 |
| 1.21.4 - 1.21.5 | 0x37 | 55 |
| 1.21.6 | 0x38 | 56 |

**Description:**

Sent when Done is pressed on the Jigsaw Block interface.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `POSITION` | Location: Block entity location |
| `STRING` | Name |
| `STRING` | Target |
| `STRING` | Pool |
| `STRING` | Final state: "Turns into" on the GUI, final_state in NBT. |
| `STRING` | Joint type: rollable if the attached piece can be rotated, else aligned. |
| `VAR_INT` | Selection priority |
| `VAR_INT` | Placement priority |

---

### SET_STRUCTURE_BLOCK

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.13 | 0x25 | 37 |
| 1.14 - 1.15 | 0x28 | 40 |
| 1.16 - 1.16.1 | 0x29 | 41 |
| 1.16.2 - 1.18 | 0x2A | 42 |
| 1.19 - 1.19.0 | 0x2C | 44 |
| 1.19.1 - 1.20.1 | 0x2D | 45 |
| 1.20.2 | 0x30 | 48 |
| 1.20.3 - 1.20.4 | 0x31 | 49 |
| 1.20.5 - 1.21.1 | 0x34 | 52 |
| 1.21.2 - 1.21.3 | 0x36 | 54 |
| 1.21.4 - 1.21.5 | 0x38 | 56 |
| 1.21.6 | 0x39 | 57 |

**Packet Fields:**

| Type | Description |
| --- | --- |
| `PLAY` | protocol:0x39resource:set_structure_block: Server |
| `POSITION` | Location: Block entity location. |
| `VAR_INT` | Action: An additional action to perform beyond simply saving the given data; see below. |
| `VAR_INT` | Mode: One of SAVE (0), LOAD (1), CORNER (2), DATA (3). |
| `STRING` | Name |
| `BYTE` | Offset X: Between -48 and 48. |
| `BYTE` | Offset Y: Between -48 and 48. |
| `BYTE` | Offset Z: Between -48 and 48. |
| `BYTE` | Size X: Between 0 and 48. |
| `BYTE` | Size Y: Between 0 and 48. |
| `BYTE` | Size Z: Between 0 and 48. |
| `VAR_INT` | Mirror: One of NONE (0), LEFT_RIGHT (1), FRONT_BACK (2). |
| `VAR_INT` | Rotation: One of NONE (0), CLOCKWISE_90 (1), CLOCKWISE_180 (2), COUNTERCLOCKWISE_90 (3). |
| `STRING` | Metadata |
| `FLOAT` | Integrity: Between 0 and 1. |
| `VAR_LONG` | Seed |
| `BYTE` | Flags: 0x01: Ignore entities; 0x02: Show air; 0x04: Show bounding box; 0x08: Strict placement. |

---

### SET_TEST_BLOCK

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.21.5 | 0x39 | 57 |
| 1.21.6 | 0x3A | 58 |

**Description:**

Updates the value of the Test Block at the given position.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `POSITION` | Position |
| `VAR_INT` | Mode: 0: start, 1: log, 2: fail, 3: accept |
| `STRING` | Message |
| `POSITION` | Position |
| `VAR_INT` | Mode: 0: start, 1: log, 2: fail, 3: accept |
| `STRING` | Message |

---

### SIGN_UPDATE

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.8 | 0x12 | 18 |
| 1.9 - 1.11 | 0x19 | 25 |
| 1.12 - 1.12.1 | 0x1C | 28 |
| 1.13 | 0x26 | 38 |
| 1.14 - 1.15 | 0x29 | 41 |
| 1.16 - 1.16.1 | 0x2A | 42 |
| 1.16.2 - 1.18 | 0x2B | 43 |
| 1.19 - 1.19.0 | 0x2D | 45 |
| 1.19.1 - 1.20.1 | 0x2E | 46 |
| 1.20.2 | 0x31 | 49 |
| 1.20.3 - 1.20.4 | 0x32 | 50 |
| 1.20.5 - 1.21.1 | 0x35 | 53 |
| 1.21.2 - 1.21.3 | 0x37 | 55 |
| 1.21.4 | 0x39 | 57 |
| 1.21.5 | 0x3A | 58 |
| 1.21.6 | 0x3B | 59 |

**Description:**

This message is sent from the client to the server when the “Done” button is pushed after placing a sign. The server only accepts this packet after Open Sign Editor, otherwise this packet is silently ignored.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `POSITION` | Location: Block Coordinates. |
| `BOOLEAN` | Is Front Text: Whether the updated text is in front or on the back of the sign |
| `STRING` | Line 1: First line of text in the sign. |
| `STRING` | Line 2: Second line of text in the sign. |
| `STRING` | Line 3: Third line of text in the sign. |
| `STRING` | Line 4: Fourth line of text in the sign. |

---

### SWING

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.8 | 0xA | 10 |
| 1.9 - 1.11 | 0x1A | 26 |
| 1.12 - 1.12.1 | 0x1D | 29 |
| 1.13 | 0x27 | 39 |
| 1.14 - 1.15 | 0x2A | 42 |
| 1.16 - 1.16.1 | 0x2B | 43 |
| 1.16.2 - 1.18 | 0x2C | 44 |
| 1.19 - 1.19.0 | 0x2E | 46 |
| 1.19.1 - 1.20.1 | 0x2F | 47 |
| 1.20.2 | 0x32 | 50 |
| 1.20.3 - 1.20.4 | 0x33 | 51 |
| 1.20.5 - 1.21.1 | 0x36 | 54 |
| 1.21.2 - 1.21.3 | 0x38 | 56 |
| 1.21.4 | 0x3A | 58 |
| 1.21.5 | 0x3B | 59 |
| 1.21.6 | 0x3C | 60 |

**Description:**

Sent when the player's arm swings.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `VAR_INT` | Hand: Hand used for the animation. 0: main hand, 1: off hand. |

---

### TELEPORT_TO_ENTITY

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.8 | 0x18 | 24 |
| 1.9 - 1.11 | 0x1B | 27 |
| 1.12 - 1.12.1 | 0x1E | 30 |
| 1.13 | 0x28 | 40 |
| 1.14 - 1.15 | 0x2B | 43 |
| 1.16 - 1.16.1 | 0x2C | 44 |
| 1.16.2 - 1.18 | 0x2D | 45 |
| 1.19 - 1.19.0 | 0x2F | 47 |
| 1.19.1 - 1.20.1 | 0x30 | 48 |
| 1.20.2 | 0x33 | 51 |
| 1.20.3 - 1.20.4 | 0x34 | 52 |
| 1.20.5 - 1.21.1 | 0x37 | 55 |
| 1.21.2 - 1.21.3 | 0x39 | 57 |
| 1.21.4 | 0x3B | 59 |
| 1.21.5 | 0x3C | 60 |
| 1.21.6 | 0x3D | 61 |

**Description:**

Teleports the player to the given entity.  The player must be in spectator mode. The vanilla client only uses this to teleport to players, but it appears to accept any type of entity.  The entity does not need to be in the same dimension as the player; if necessary, the player will be respawned in the right world.  If the given entity cannot be found (or isn't loaded), this packet will be ignored.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `UUID` | Target Player: UUID of the player to teleport to (can also be an entity UUID). |
| `UUID` | Target Player: UUID of the player to teleport to (can also be an entity UUID). |

---

### TEST_INSTANCE_BLOCK_ACTION

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.21.5 | 0x3D | 61 |
| 1.21.6 | 0x3E | 62 |

**Description:**

Tries to perform an action the Test Instance Block at the given position.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `POSITION` | Position |
| `VAR_INT` | Action: 0: init, 1: query, 2: set, 3: reset, 4: save, 5: export, 6: run. |
| `STRING` | Test: ID in the minecraft:test_instance registry. |
| `VAR_INT` | Size X |
| `VAR_INT` | Size Y |
| `VAR_INT` | Size Z |
| `VAR_INT` | Rotation: 0: none, 1: clockwise 90°, 2: clockwise 180°, 3: counter-clockwise 90°. |
| `BOOLEAN` | Ignore Entities |
| `VAR_INT` | Status: 0: cleared, 1: running, 2: finished. |
| `PREFIXED_OPTIONAL_TEXT_COMPONENT` | Error Message |
| `POSITION` | Position |
| `VAR_INT` | Action: 0: init, 1: query, 2: set, 3: reset, 4: save, 5: export, 6: run. |
| `STRING` | Test: ID in the minecraft:test_instance registry. |
| `VAR_INT` | Size X |
| `VAR_INT` | Size Y |
| `VAR_INT` | Size Z |
| `VAR_INT` | Rotation: 0: none, 1: clockwise 90°, 2: clockwise 180°, 3: counter-clockwise 90°. |
| `BOOLEAN` | Ignore Entities |
| `VAR_INT` | Status: 0: cleared, 1: running, 2: finished. |
| `PREFIXED_OPTIONAL_TEXT_COMPONENT` | Error Message |

---

### USE_ITEM

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.9 - 1.11 | 0x1D | 29 |
| 1.12 - 1.12.1 | 0x20 | 32 |
| 1.13 | 0x2A | 42 |
| 1.14 - 1.15 | 0x2D | 45 |
| 1.16 - 1.16.1 | 0x2E | 46 |
| 1.16.2 - 1.18 | 0x2F | 47 |
| 1.19 - 1.19.0 | 0x31 | 49 |
| 1.19.1 - 1.20.1 | 0x32 | 50 |
| 1.20.2 | 0x35 | 53 |
| 1.20.3 - 1.20.4 | 0x36 | 54 |
| 1.20.5 - 1.21.1 | 0x39 | 57 |
| 1.21.2 - 1.21.3 | 0x3B | 59 |
| 1.21.4 | 0x3D | 61 |
| 1.21.5 | 0x3F | 63 |
| 1.21.6 | 0x40 | 64 |

**Description:**

Sent when pressing the Use Item key (default: right click) with an item in hand.

**Packet Fields:**

| Type | Description |
| --- | --- |
| `VAR_INT` | Hand: Hand used for the animation. 0: main hand, 1: off hand. |
| `VAR_INT` | Sequence: Block change sequence number (see #Acknowledge Block Change). |
| `FLOAT` | Yaw: Player head rotation around the Y-Axis. |
| `FLOAT` | Pitch: Player head rotation around the X-Axis. |
| `VAR_INT` | Hand: Hand used for the animation. 0: main hand, 1: off hand. |
| `VAR_INT` | Sequence: Block change sequence number (see #Acknowledge Block Change). |
| `FLOAT` | Yaw: Player head rotation around the Y-Axis. |
| `FLOAT` | Pitch: Player head rotation around the X-Axis. |

---

### USE_ITEM_ON

| Version Range | ID (hex) | ID (dec) |
| --- | --- | --- |
| 1.8 | 0x8 | 8 |
| 1.9 - 1.11 | 0x1C | 28 |
| 1.12 - 1.12.1 | 0x1F | 31 |
| 1.13 | 0x29 | 41 |
| 1.14 - 1.15 | 0x2C | 44 |
| 1.16 - 1.16.1 | 0x2D | 45 |
| 1.16.2 - 1.18 | 0x2E | 46 |
| 1.19 - 1.19.0 | 0x30 | 48 |
| 1.19.1 - 1.20.1 | 0x31 | 49 |
| 1.20.2 | 0x34 | 52 |
| 1.20.3 - 1.20.4 | 0x35 | 53 |
| 1.20.5 - 1.21.1 | 0x38 | 56 |
| 1.21.2 - 1.21.3 | 0x3A | 58 |
| 1.21.4 | 0x3C | 60 |
| 1.21.5 | 0x3E | 62 |
| 1.21.6 | 0x3F | 63 |

**Packet Fields:**

| Type | Description |
| --- | --- |
| `VAR_INT` | Hand: The hand from which the block is placed; 0: main hand, 1: off hand. |
| `POSITION` | Location: Block position. |
| `VAR_INT` | Face: The face on which the block is placed (as documented at Player Action). |
| `FLOAT` | Cursor Position X: The position of the crosshair on the block, from 0 to 1 increasing from west to east. |
| `FLOAT` | Cursor Position Y: The position of the crosshair on the block, from 0 to 1 increasing from bottom to top. |
| `FLOAT` | Cursor Position Z: The position of the crosshair on the block, from 0 to 1 increasing from north to south. |
| `BOOLEAN` | Inside block: True when the player's head is inside of a block. |
| `BOOLEAN` | World Border Hit: Seems to always be false, even when interacting with blocks around or outside the world border, or while the player is outside the border. |
| `VAR_INT` | Sequence: Block change sequence number (see #Acknowledge Block Change). |
| `VAR_INT` | Hand: The hand from which the block is placed; 0: main hand, 1: off hand. |
| `POSITION` | Location: Block position. |
| `VAR_INT` | Face: The face on which the block is placed (as documented at Player Action). |
| `FLOAT` | Cursor Position X: The position of the crosshair on the block, from 0 to 1 increasing from west to east. |
| `FLOAT` | Cursor Position Y: The position of the crosshair on the block, from 0 to 1 increasing from bottom to top. |
| `FLOAT` | Cursor Position Z: The position of the crosshair on the block, from 0 to 1 increasing from north to south. |
| `BOOLEAN` | Inside block: True when the player's head is inside of a block. |
| `BOOLEAN` | World Border Hit: Seems to always be false, even when interacting with blocks around or outside the world border, or while the player is outside the border. |
| `VAR_INT` | Sequence: Block change sequence number (see #Acknowledge Block Change). |

---

## Frequently Asked Questions (FAQ)

### What is a Minecraft packet ID?

A packet ID is a unique numeric identifier assigned to each type of packet in the Minecraft protocol. Packet IDs change between Minecraft versions, so you need to use the correct ID for your target version.

### How do I find a packet ID for a specific Minecraft version?

1. Search for the packet name using Ctrl+F (Cmd+F on Mac)
2. Find the version range that includes your Minecraft version
3. Use the packet ID shown in hexadecimal (0x...) or decimal format

### What is the difference between clientbound and serverbound packets?

- **Clientbound packets**: Sent from the Minecraft server to the client (e.g., player position updates, chat messages)
- **Serverbound packets**: Sent from the Minecraft client to the server (e.g., player movement, chat input)

### Why do packet IDs change between versions?

Mojang modifies the Minecraft protocol with each update, adding new packets, removing old ones, and reorganizing packet IDs. This reference tracks these changes across all Minecraft versions.

### Can I use this for Minecraft Bedrock Edition?

No, this reference is specifically for **Minecraft Java Edition**. Bedrock Edition uses a completely different protocol.

---

## Related Resources

- [Minecraft Protocol Wiki](https://wiki.vg/Minecraft_Protocol) - Official protocol documentation
- [ViaVersion](https://github.com/ViaVersion/ViaVersion) - Protocol version translation library
- [Minecraft Version History](https://minecraft.wiki/w/Java_Edition_version_history) - Version release dates

## Keywords

Minecraft packet ID, Minecraft protocol, packet reference, clientbound packets, serverbound packets, Minecraft version compatibility, protocol version, packet IDs by version, Minecraft Java Edition protocol, network protocol packets

---

*Last updated: 2025-11-15 14:10:04 UTC*

*This reference is automatically generated from ViaVersion sources and Minecraft Wiki data.*
