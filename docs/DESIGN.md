## PROTOCOL PHASES

### HANDSHAKE PHASE

- C2S_Handshake:
  - Protocol version (u32)
  - Client Intention (u8)
    - 0: Status (Switch to Status Phase)
    - 1: Login (Switch to Configuration Phase)
    - 2: Transfer (Switch to Configuration Phase)

#### STATUS PHASE

- S2C_Status_Response:
  - Body (JSON):
    - Version:
      - Name (String)
      - Protocol (u32)
    - Players:
      - Max (u32)
      - Online (u32)
      - Sample (Array of Player objects)
        - Name (String)
        - ID (UUID)
    - Description (Text component)
- C2S_Ping
- S2C_Pong

#### CONFIGURATION PHASE

- S2C_Disconnect:
  - Reason (Text component)
- C2S_Login start
- S2C_Start Encryption
- C2S_Complete Encryption
- S2C_Login success
- S2C_Open_Channel_List

#### GAME PHASE

- S2C_Disconnect:
  - Reason (Text component)
- C2S_Ping
- S2C_Pong
- S2C_Channel_Payload
- C2S_Channel_Payload
- S2C_Open_Channel_List
- S2C_Close_Channel_List
- S2C_Server_Transfer_Request

## AUTHENTICATION

Broker through a session server (Minecraft style)

Session server authentication optional depending on server configuration, but all packets are required!

## CHANNELS

Channels have the following properties:
- Name (Namespaced ID)
- Reliability (Reliable, Unreliable, Sequenced)
- Ordering (Ordered, Unordered)
