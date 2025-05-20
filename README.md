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
- Download the JSON file "MobGeneratorFlow".
- Open **Node-RED**.
- Click on the **hamburger menu** (top right) → **Import** → **Clipboard**.
- Paste the JSON flow into the clipboard and click **Import**.
- The flow should now appear in your Node-RED workspace.

### 2. Set Up the MQTT Server
- In Node-RED, locate the MQTT nodes in the flow.
-  ![mqtt node](https://private-user-images.githubusercontent.com/125493371/443660937-e7a806be-ff9a-49c4-87eb-b68c045413de.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NDc3MjE4NTAsIm5iZiI6MTc0NzcyMTU1MCwicGF0aCI6Ii8xMjU0OTMzNzEvNDQzNjYwOTM3LWU3YTgwNmJlLWZmOWEtNDljNC04N2ViLWI2OGMwNDU0MTNkZS5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjUwNTIwJTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI1MDUyMFQwNjEyMzBaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT1hOTcyNjMyY2Y2NzU2MTdjYWIzM2ZkNmI2N2Y3YWVhNTkyNjc1MWRjNjEwYzcxZjAwMmIzNzZhY2ZmY2UxMTU2JlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCJ9.Tr53ByEM0R5E7HdxaqnvJtyLYCSd5ut2KTM9J4YfR9I)
- Double-click on each MQTT node and configure the server:
  - Set the **MQTT Broker** to your own MQTT server (e.g., **IP address** or **hostname**).
  - Enter the **MQTT topic** you are using to control the LED strip (you may need to configure this in your MQTT broker).

### 3. Configure the Minecraft Server
- Locate the **RCON** nodes in the flow (for Minecraft integration).
-  ![rcon node](https://private-user-images.githubusercontent.com/125493371/443660969-6728e20f-4e68-4769-b632-7fbe12bd3981.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NDc3MjE5NDksIm5iZiI6MTc0NzcyMTY0OSwicGF0aCI6Ii8xMjU0OTMzNzEvNDQzNjYwOTY5LTY3MjhlMjBmLTRlNjgtNDc2OS1iNjMyLTdmYmUxMmJkMzk4MS5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjUwNTIwJTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI1MDUyMFQwNjE0MDlaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT1hMDJjYWFlMmI5YmM5MjA2MzVjOGIzNzA2Y2I4OGI2NmQ0NDU1YjA1MmU5NDIxY2QzYTRhMGQzODgyZGJmYWRlJlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCJ9.0MO__2XTL9Qps7OS6OwezmFFd3sLBwFX9FiHjWVrrAI)
- Double-click the RCON node and configure the Minecraft server:
  - Set the **RCON Host** to your Minecraft server’s **IP address**.
  - Set the **RCON Port** to your server’s RCON port (default is usually 25575).
  - Enter your **RCON Password** for authentication.

### 4. Access the Dashboard
- After importing the flow and configuring the servers, deploy the flow in Node-RED.
- Open a browser and navigate to your Node-RED dashboard (usually `http://<your-ip>:1880/ui`), or click on the top right button with the square and arrow.
-  ![dashboard button](https://private-user-images.githubusercontent.com/125493371/443661002-4df8b141-266f-4727-b1f4-0e008e423299.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NDc3MjE5NDksIm5iZiI6MTc0NzcyMTY0OSwicGF0aCI6Ii8xMjU0OTMzNzEvNDQzNjYxMDAyLTRkZjhiMTQxLTI2NmYtNDcyNy1iMWY0LTBlMDA4ZTQyMzI5OS5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjUwNTIwJTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI1MDUyMFQwNjE0MDlaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT1iY2EwOWEwOWZiZTNjMGQzOTlmNjZlZmYwODUwNGFjNzg4ZGVjZTI0NjJhMTYwZTY0ZDcwYjJlY2JjNzY3ZmQ5JlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCJ9.bhyzJ2bvFzevxbZ4L3tduuOWJKDDu5aWHnXNUUOkiNI)
- You should now see the **Mob Generator Dashboard** with buttons to spawn mobs, trigger actions, and see the LED strip feedback, as well as the mobs/commands working in minecraft!
- That's it, expand, change and do whatever you want with it.
- ![mob gen](https://private-user-images.githubusercontent.com/125493371/445461698-2b219568-c993-437c-898e-e2a9a1176032.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NDc3MjM5ODgsIm5iZiI6MTc0NzcyMzY4OCwicGF0aCI6Ii8xMjU0OTMzNzEvNDQ1NDYxNjk4LTJiMjE5NTY4LWM5OTMtNDM3Yy04OThlLWUyYTlhMTE3NjAzMi5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjUwNTIwJTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI1MDUyMFQwNjQ4MDhaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT1lMGQwM2Y0ZTNmOGRkMjMyYWFmNjcyZTQ3M2Y0ZTZjOWMwY2NlYmE2MzZmYjdkY2RlYWNkNDgyZjE1NTZlNGJiJlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCJ9.-bhPoFrntLozcq7hjkijjmOsGVndLGz53H-VlxllVWA)

### 5. Optional
- To test if LEDS work with a specific MQTT server, you can use the "LEDSim" flow and just import it into Node-Red the same way you imported the other file, just make sure to use the same mqtt server in both flows.
- It should look like this at the end, and the leds should change color depending on what button you clicked:
- ![led sim](https://private-user-images.githubusercontent.com/125493371/445461570-d143e080-3060-4265-a687-07e0f29f969b.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NDc3MjM5ODgsIm5iZiI6MTc0NzcyMzY4OCwicGF0aCI6Ii8xMjU0OTMzNzEvNDQ1NDYxNTcwLWQxNDNlMDgwLTMwNjAtNDI2NS1hNjg3LTA3ZTBmMjlmOTY5Yi5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjUwNTIwJTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI1MDUyMFQwNjQ4MDhaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT1hNmE3MjNhNTIxZWYzYjUwYTdlZjQxNTE2MGFmOTdlMDM0NmJlZTAzY2RhZmExNWRhOTIwYzMyNjFiNGFlZDU0JlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCJ9.dEllsHdt1_8B8qhxt-c1N_0NyUrwavHexRzgzcBjKWY)
