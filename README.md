# Bluetooth Map
A website that visualizes foot traffic nearby by allowing people to connect to a Bluetooth device and then visualizing their relative positions on a map.

## Tech Stack
### Frontend
  - **Mapping**: Leaflet.js
  - **Visualization**: Canvas API

### Backend
  - **Database**: SQLite
  - **Server**: Node.js with Express.js

### Bluetooth Beacons
  - **Phones**: [Bluetooth Simulator](https://apkpure.com/beacon-simulator/net.alea.beaconsimulator)
  - **Server(Raspberry Pi)**: Node.js + Express.js

## Project Flow
```mermaid
graph TD
A[User visits website] --> B[Raspberry Pi sends client-side code to client]
C[User connect to the three beacons] --> D[User sends real-time RSSIs of beacon connections to Raspberry Pi]
D --> E[Raspberry Pi uses all RSSIs in order to calculate the relative location of the devices]
E --> F[Raspberry Pi sends the relative locations of all of the devices to the client]
F --> G[Client renders map of devices]
B --> G
```
