# CreaNexusCore
**CreaNexusCore** is an ambitious, open-source server architecture designed to unify modifiable games and custom-server environments under a single, streamlined ecosystem.


Our mission is to bridge the gap between diverse sandbox gaming communities, providing a centralized core that facilitates interoperability, cross-platform management, and modular extensibility for titles such as **Minecraft** (Java, Bedrock, NetEase, etc.), **ClassiCube**, **Luanti** (formerly Minetest), **Hytale**, **Roblox**, **Polytoria**, and more.

## 🌍 Supported Ecosystems & Status
We track the progress of each engine and protocol bridge. Contributions, bug reports, and pull requests are highly encouraged for items marked as "Experimental" or "In Development."

### ✅ Stable / Semi-Stable
These integrations are functional but may still have edge-case bugs.
- **Minecraft (Java Edition)**: Full support (Release/Beta/April Fools).
- **Minecraft (Bedrock Edition)**: Full support. (1.2-1.26)
- **Minecraft (NetEase Edition)**: Functional bridge.
- **EaglerCraft**: Fully integrated.
- **Discord Chat**: Stable connectivity.

### ⚠️ Experimental / W.I.P.
These implementations are currently in a testing phase or have limited functionality.
- **Minecraft PE 0.15.x**: Currently in "Spectator Mode" (Limited rendering; no entity support or terrain generation).
- **ClassiCube**: Initial connection established (Handshake successful, chat preview active; suffers from occasional byte-stream packet errors).

### 🏗️ Planned / In Development
We are currently architecting the protocol bridges for these titles.
- **Hytale**
- **Luanti / Minetest**
- **Roblox**
- **Polytoria**

## ⚙️ The Core Architecture: Nukkit MOT
The heart of **CreaNexusCore** is powered by Nukkit MOT, a highly specialized fork of the Nukkit server software. This core handles the heavy lifting of multi-protocol communication, allowing us to bridge the vast gap between Bedrock versions.

### Core Capabilities:
- **Version Support**: Extensive support ranging from v1.2 to v1.26 (Bedrock).
- **NetEase Integration**: Native support for the NetEase protocol variants.
- **Experimental Legacy Support**: Preliminary support for v1.1.

## 🔗 Protocol Translation Layer: ViaProxy
To ensure cross-version compatibility for Java and Bedrock clients, we utilize **ViaProxy**. This module acts as the "universal translator," allowing legacy, modern, and experimental Minecraft clients to communicate with our core.

### Supported Protocol Versions
- **Java Edition**: Full spectrum support from Alpha (a1.0.15) to modern Releases (1.21.11).
- **Beta/Alpha**: Extensive legacy support (a1.0.15 – b1.8.1).
- **April Fools**: Specialized support for 3D Shareware, 20w14infinite, and 25w14craftmine.
- **Combat Snapshots**: Combat Test 8c.
- **Bedrock Edition**: Support for v1.26.0+.

### 🛡️ Deployment Flexibility: ViaProxyNoCommandRun
We understand that not every hosting environment allows you to modify the Java startup arguments. **ViaProxyNoCommandRun** is our solution for deploying **ViaProxy** within restrictive environments (like standard shared Minecraft hostings).
- **How it works**: This specialized .jar bypasses command-line argument requirements, enabling the proxy to initiate successfully in environments where you only have access to a "Start" button or a standard JAR selector.
- **Best for**: Shared hostings, pre-configured game panels, and quick deployment scenarios where command-line control is unavailable.

(ViaProxyNoCommandRun)[https://github.com/Creadores-Program/ViaProxyNoCommandRun]

### Configuration for CreaNexusCore
ViaProxy must be linked to your **Nukkit MOT** instance (ip and port, ViaBedrock mode) to successfully bridge these versions.

## 🔗 Protocol Translation Layer: ViaProxy & Beta2Release
To achieve seamless interoperability across Minecraft's history, **CreaNexusCore** leverages **ViaProxy** as the main traffic mediator, enhanced by the **ViaProxyBeta2Release** plugin.

### The Translation Stack
This combination enables a unified experience for players across widely disparate versions:
- **ViaProxy Core**: Handles the heavy lifting of multi-protocol communication (Java Alpha to modern Release, Bedrock 1.26.0, and Combat Snapshots).
- **ViaProxyBeta2Release Plugin**: Specifically bridges the **Beta (b1.0 - b1.8.1)** protocols into the modern Release environment.

## 🌐 EaglerCraft Integration: ayunViaProxyEagUtils
We bridge the browser-based world of **EaglerCraft** (v1.5.2 and v1.8.8) directly into our server infrastructure. By utilizing the ayunViaProxyEagUtils plugin within **ViaProxy**, we enable WebSocket-to-TCP communication on the same port as your Java traffic.

### Key Features:
- **WebSocket Support**: Seamlessly handles ws:// connections.
- **Dual-Version Support**: Compatible with both 1.5.2 and 1.8.8 EaglerCraft clients.
- **Smart Passthrough**: Supports legacy passthrough and ProtocolSupport, ensuring compatibility even if the backend server does not natively support older protocols.
  [!NOTE]
  Please be aware that custom skin files are excluded from this bridge.

## 💬 Community Bridge: Discord Integration
To maintain a unified community, **CreaNexusCore** includes a native **DiscordChat**. This plugin synchronizes your in-game chat with your Discord server, ensuring seamless communication between players on the server and players on Discord.

### Core Features
- **Two-Way Sync**: Messages sent in the game are relayed to a specified Discord channel, and messages from that channel are broadcasted in the game.
- **Bot-Driven**: Powered by a dedicated Discord bot configured within your Nukkit MOT instance.
- **Management**: Real-time visibility of server activity, player joins/leaves, and chat logs directly from your server's Discord hub.