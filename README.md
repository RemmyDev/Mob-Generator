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
-  ![mqtt node]([https://private-user-images.githubusercontent.com/125493371/443660937-e7a806be-ff9a-49c4-87eb-b68c045413de.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NDcyMjY4MDcsIm5iZiI6MTc0NzIyNjUwNywicGF0aCI6Ii8xMjU0OTMzNzEvNDQzNjYwOTM3LWU3YTgwNmJlLWZmOWEtNDljNC04N2ViLWI2OGMwNDU0MTNkZS5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjUwNTE0JTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI1MDUxNFQxMjQxNDdaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT00ZjUzYTg2YzY0YzQ0MmI5M2VhMTA3NzgxZDY3ZjU3Mjk5Nzc4ZjM0Y2IwNjBkMjY0NTFiNGZhMThhMWE5NzE5JlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCJ9.uEGt9DiwtfoGDO8uNgJZ1AavMBotdE0YmKnu209bMww](https://private-user-images.githubusercontent.com/125493371/443660937-e7a806be-ff9a-49c4-87eb-b68c045413de.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NDc3MjE3OTAsIm5iZiI6MTc0NzcyMTQ5MCwicGF0aCI6Ii8xMjU0OTMzNzEvNDQzNjYwOTM3LWU3YTgwNmJlLWZmOWEtNDljNC04N2ViLWI2OGMwNDU0MTNkZS5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjUwNTIwJTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI1MDUyMFQwNjExMzBaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT02MDViY2JjNjAwOGIyYjBjNzM5MzRlYjZjZmY3ZTY4ZWFmYjU4YzgzNTkzNmVmNjA0NjM1MjUyZGU0ZTJjYjg3JlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCJ9.e5iU6ikSPtR1o7U1fZq1DCuiqE2MjcZDRhz4_fPrc_w))
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

