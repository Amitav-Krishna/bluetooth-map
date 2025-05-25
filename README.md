# Bluetooth Map
A website that visualizes foot traffic nearby by allowing people to connect to a Bluetooth device and then visualizing their relative positions on a map.

## Tech Stack
### Frontend (Client):
- Web Bluetooth API
- WebSocket

### Backend (Raspberry Pi):
- Python with:
	- Flask (web server)
	- Flask-SocketIO (WebSocket support)

### Beacons
- Android phones running [Beacon Simulator](https://apkpure.com/beacon-simulator/net.alea.beaconsimulator#google_vignette)


## Project Flow
```mermaid
graph TD
A[User opens website] --> B[Raspberry Pi serves webpage]
A --> C[Website requests Bluetooth access]
C --> D{Yes}
C --> E{No}
E --> K[Close website]
D --> F[Phone scans for the beacons]
F --> G[Client reads RSSI from found beacons]
G --> H[Client sends {beacon-ID, RSSI} pairs via WebSocket to Raspberry Pi]
H --> I[Raspberry Pi broadcasts positions to all clients via WebSocket]
I --> J[Client renders dots on a simple HTML canvas]
```
