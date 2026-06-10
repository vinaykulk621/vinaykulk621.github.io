+++
date = '2026-06-10T22:59:33+05:30'
title = 'BitTorrent Wire Protocol'
description = 'BitTorrent Wire Protocol Introduction and Implementation'
+++

Once a handshake between peers happen via [BitTorrent Handshake protocol]({{< ref "/blog/BitTorrent-handshake-protocol.md" >}}), these peers talk and share data via this wire protocol.

All the messages shared via this protocol has this following structure:

| field      | size (bytes) | desc                                                                   |
| ---------- | ------------ | ---------------------------------------------------------------------- |
| Length     | 4            | length of message-id + payload (big-endian format), `0` for keep alive |
| Message ID | 1            | type of message being shared (ex: 0 for choke, 6 for req)              |
| Payload    | variable     | depends on the data                                                    |

---

following are all the different types of `Message ID` possible and what they mean:

| Message Type   | Message ID | Payload Format                                  | Description                                             |
| -------------- | ---------- | ----------------------------------------------- | ------------------------------------------------------- |
| Choke          | 0          | None                                            | Tells the peer to **stop sending requests**.            |
| Unchoke        | 1          | None                                            | Tells the peer it **can send requests**.                |
| Interested     | 2          | None                                            | Indicates **interest** in downloading from the peer.    |
| Not Interested | 3          | None                                            | Indicates **no interest** in downloading from the peer. |
| Have           | 4          | 4 bytes (piece index, big-endian)               | Announces that the sender **has a piece**.              |
| Bitfield       | 5          | Variable (bitfield)                             | A **bitmask** showing which pieces the sender has.      |
| Request        | 6          | 12 bytes (index, begin, length, all big-endian) | Requests a **block** of data from a piece.              |
| Piece          | 7          | 8 + `length` bytes (index, begin, block data)   | Contains the **requested block** of data.               |
| Cancel         | 8          | 12 bytes (index, begin, length, all big-endian) | Cancels a **pending request**.                          |
| Port           | 9          | IDK                                             | IDK... port number IG                                   |
