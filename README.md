# 🧱 Minecraft Mob Generator via Node-RED
This project integrates **Minecraft**, **Node-RED**, and **MQTT** to create a fully interactive web-based **Mob Generator** that changes an **LED Strip's** color based on the mob you spawned.

---

## 🚀 Features

- **Node-RED Web Dashboard**:  
  User-friendly Mob Generator interface with buttons for each Minecraft mob type.

- **Minecraft Integration**:  
  Custom Node-RED nodes send commands to your Minecraft server (e.g., spawn mobs, eliminate players, fetch stats).

- **LED Feedback via MQTT**:  
  Each mob sends a color-coded MQTT message to control an RGB LED strip.

- **Modular Flow**:  
  Built for expandability—easy to add new mobs, commands, or MQTT behaviors.

---

## 🛠️ Architecture

- **Node-RED Flow**  
  ↳ Logic and UI interaction

- **Mob Generator Dashboard**  
  ↳ Web interface for spawning mobs and triggering effects

- **Minecraft Server & MQTT Server**  
  ↳ Commands and communication layer

- **LED Strip (RGB read from the MQTT server)**  
  ↳ Visual feedback based on mob type

---

## 👾 Mobs

<details>
  <summary><strong>Hostile Mobs</strong></summary>
  
  - Blaze  
  - Creeper  
  - Zombie  
  - Skeleton  
  - Wither Skeleton  
  - Spider  
  - Witch  
  - Enderman

</details>

<details>
  <summary><strong>Friendly Mobs</strong></summary>
  
  - Cow  
  - Chicken  
  - Pig  
  - Sheep
  
</details>

---

## 🎉 Extra Buttons

- **Spawn Random Mob**  
- **BOOM** (Spawns 1 TNT)  
- **Teleport to Random Mob**

---

## 📝 How to Use

### 1. Import the Node-RED Flow
- Download the JSON flow "Mob_Generator".
- Open **Node-RED**.
- Click on the **hamburger menu** (top right) → **Import** → **Clipboard**.
- Paste the JSON flow into the clipboard and click **Import**.
- The flow should now appear in your Node-RED workspace.

### 2. Set Up the MQTT Server
- In Node-RED, locate the MQTT nodes in the flow.
![MQTT Node]("C:\Users\tamer\Pictures\Screenshots\Screenshot 2025-05-14 142115.png")
- Double-click on each MQTT node and configure the server:
  - Set the **MQTT Broker** to your own MQTT server (e.g., **IP address** or **hostname**).
  - Enter the **MQTT topic** you are using to control the LED strip (you may need to configure this in your MQTT broker).

### 3. Configure the Minecraft Server
- Locate the **RCON** nodes in the flow (for Minecraft integration).
- Double-click the RCON node and configure the Minecraft server:
  - Set the **RCON Host** to your Minecraft server’s **IP address**.
  - Set the **RCON Port** to your server’s RCON port (default is usually 25575).
  - Enter your **RCON Password** for authentication.

### 4. Access the Dashboard
- After importing the flow and configuring the servers, deploy the flow in Node-RED.
- Open a browser and navigate to your Node-RED dashboard (usually `http://<your-ip>:1880/ui`).
- You should now see the **Mob Generator Dashboard** with buttons to spawn mobs, trigger actions, and see the LED strip feedback.

---

Once everything is set up, you can interact with the dashboard, spawn mobs, and watch as the LED strip changes color based on the mob you spawn!

