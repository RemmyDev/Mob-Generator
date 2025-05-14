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

