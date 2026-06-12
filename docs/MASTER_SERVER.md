# Master Server

The master server is responsible for providing clients with:
1. Server discovery
2. Friend presence
3. P2P/NAT connection brokering through ICE (Interactive Connectivity Establishment)
4. Session verification

It is not responsible for authentication, which is handled by an IdP (Identity Provider).
