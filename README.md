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
  Easy to add new mobs, commands, or MQTT behaviors.

---

## 🛠️ Architecture

┌─────────────┐       ┌──────────────┐       ┌───────────────┐
│ Node-RED UI │──────▶│  MQTT Broker │──────▶│  LED Strip    │
└────┬────────┘       └─────┬────────┘       └───────────────┘
     │                      │
     ▼                      ▼
┌─────────────┐       ┌──────────────┐
│ Minecraft   │◀──────│ RCON Nodes   │
│ Server      │       └──────────────┘
└─────────────┘

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
- Download the JSON file "MobGeneratorFlow".
- Open **Node-RED**.
- Click on the **hamburger menu** (top right) → **Import** → **Clipboard**.
- Paste the JSON flow into the clipboard and click **Import**.
- The flow should now appear in your Node-RED workspace.

### 2. Set Up the MQTT Server
- In Node-RED, locate the MQTT nodes in the flow.
-  ![mqtt node](https://github.com/RemmyDev/Mob-Generator/blob/main/Images/Screenshot%202025-05-14%20142115.png?raw=true)
- Double-click on each MQTT node and configure the server:
  - Set the **MQTT Broker** to your own MQTT server (e.g., **IP address** or **hostname**).
  - Enter the **MQTT topic** you are using to control the LED strip (you may need to configure this in your MQTT broker).

### 3. Configure the Minecraft Server
- Locate the **RCON** nodes in the flow (for Minecraft integration).
-  ![rcon node](https://github.com/RemmyDev/Mob-Generator/blob/main/Images/Screenshot%202025-05-14%20142108.png?raw=true)
- Double-click the RCON node and configure the Minecraft server:
  - Set the **RCON Host** to your Minecraft server’s **IP address**.
  - Set the **RCON Port** to your server’s RCON port (default is usually 25575).
  - Enter your **RCON Password** for authentication.

### 4. Access the Dashboard
- After importing the flow and configuring the servers, deploy the flow in Node-RED.
- Open a browser and navigate to your Node-RED dashboard (usually `http://<your-ip>:1880/ui`), or click on the top right button with the square and arrow.
-  ![dashboard button](https://github.com/RemmyDev/Mob-Generator/blob/main/Images/Screenshot%202025-05-14%20142057.png?raw=true)
- You should now see the **Mob Generator Dashboard** with buttons to spawn mobs, trigger actions, and see the LED strip feedback, as well as the mobs/commands working in minecraft!
- That's it, expand, change and do whatever you want with it.
- ![mob gen](https://github.com/RemmyDev/Mob-Generator/blob/main/Images/Screenshot%202025-05-20%20084637.png?raw=true)

### 5. Optional
- To test if LEDS work with a specific MQTT server, you can use the "LEDSim" flow and just import it into Node-Red the same way you imported the other file, just make sure to use the same mqtt server in both flows.
- It should look like this at the end, and the leds should change color depending on what button you clicked:
- ![led sim](https://github.com/RemmyDev/Mob-Generator/blob/main/Images/Screenshot%202025-05-20%20084619.png?raw=true)
