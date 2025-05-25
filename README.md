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
``` mermaid
graph TD
    %% User Interaction
    A[User Opens Website] --> B[Request Bluetooth Access]
    B --> C{Granted?}
    C -->|Yes| D[Start Scanning]
    C -->|No| E[Show Error Message]

    %% Bluetooth Scanning
    D --> F[Detect Nearby Devices]
    F --> G[Estimate Distance via RSSI]
    G --> H[Plot Positions on Leaflet Map]

    %% Backend Flow (Optional)
    H --> I{Backend Enabled?}
    I -->|Yes| J[Send Anonymized Data to Server]
    I -->|No| K[Render Locally Only]

    %% Server-Side Processing
    J --> L[Store in SQLite Database]
    L --> M[Aggregate Foot Traffic Data]
    M --> N[Generate Heatmaps]

    %% Beacon Integration
    subgraph "Bluetooth Beacons (Old Phones)"
        O[Beacon Broadcasts ID] --> F
    end

    %% Data Flow
    N -->|API Call| H
    K --> Q[Update Map in Real-Time]
    ```
