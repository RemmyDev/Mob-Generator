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
- Copy the provided JSON flow below.
- Open **Node-RED**.
- Click on the **hamburger menu** (top right) → **Import** → **Clipboard**.
- Paste the JSON flow into the clipboard and click **Import**.
- The flow should now appear in your Node-RED workspace.

<details>
  <summary><strong>Click to view the JSON flow</strong></summary>

```json
{
[
    {
        "id": "93bc9b581a312155",
        "type": "tab",
        "label": "Flow 6",
        "disabled": false,
        "info": "",
        "env": []
    },
    {
        "id": "9a1dca304799dc4e",
        "type": "ui_text",
        "z": "93bc9b581a312155",
        "group": "ab8d52c8070607ed",
        "order": 1,
        "width": 0,
        "height": 0,
        "name": "",
        "label": "Mob Generator",
        "format": "",
        "layout": "col-center",
        "className": "",
        "style": true,
        "font": "Trebuchet MS,Helvetica,sans-serif",
        "fontSize": "40",
        "color": "#000000",
        "x": 1760,
        "y": 200,
        "wires": []
    },
    {
        "id": "3811e813afe59832",
        "type": "rcon",
        "z": "93bc9b581a312155",
        "name": "",
        "server": "974b018728e661cc",
        "command": "",
        "x": 1890,
        "y": 760,
        "wires": [
            []
        ]
    },
    {
        "id": "d4a20b893906a160",
        "type": "function",
        "z": "93bc9b581a312155",
        "name": "function 8",
        "func": "function hexToRgb(hexColor) {\n    const hex = hexColor.replace(/^#/, '');\n    const r = parseInt(hex.substring(0, 2), 16);\n    const g = parseInt(hex.substring(2, 4), 16);\n    const b = parseInt(hex.substring(4, 6), 16);\n\n    return {\n        r: r,\n        g: g,\n        b: b,\n        a: 1\n    };\n}\n\n// Always use zombie green color\nconst zombieColorHex = '#00ff00';\nconst rgbObject = hexToRgb(zombieColorHex);\nmsg.payload = Array(16).fill(rgbObject);\n\nreturn msg;\n",
        "outputs": 1,
        "timeout": 0,
        "noerr": 0,
        "initialize": "",
        "finalize": "",
        "libs": [],
        "x": 1760,
        "y": 680,
        "wires": [
            [
                "d61cf564d0ca07e0"
            ]
        ]
    },
    {
        "id": "d61cf564d0ca07e0",
        "type": "mqtt out",
        "z": "93bc9b581a312155",
        "name": "",
        "topic": "led",
        "qos": "",
        "retain": "",
        "respTopic": "",
        "contentType": "",
        "userProps": "",
        "correl": "",
        "expiry": "",
        "broker": "5058bca32a4f00c3",
        "x": 1910,
        "y": 660,
        "wires": []
    },
    {
        "id": "e0a5f72590311980",
        "type": "ui_button",
        "z": "93bc9b581a312155",
        "name": "",
        "group": "ab8d52c8070607ed",
        "order": 6,
        "width": 0,
        "height": 0,
        "passthru": false,
        "label": "Zombie",
        "tooltip": "",
        "color": "",
        "bgcolor": "green",
        "className": "zombie",
        "icon": "",
        "payload": "zombie",
        "payloadType": "str",
        "topic": "payload",
        "topicType": "msg",
        "x": 1560,
        "y": 700,
        "wires": [
            [
                "d4a20b893906a160",
                "fa712774de43dc12",
                "5cb0188b5dea4c53"
            ]
        ]
    },
    {
        "id": "9306c491bdc98310",
        "type": "rcon",
        "z": "93bc9b581a312155",
        "name": "",
        "server": "974b018728e661cc",
        "command": "",
        "x": 1970,
        "y": 940,
        "wires": [
            []
        ]
    },
    {
        "id": "49fb5c7a55a4dfd4",
        "type": "function",
        "z": "93bc9b581a312155",
        "name": "function 9",
        "func": "function hexToRgb(hexColor) {\n    const hex = hexColor.replace(/^#/, '');\n    const r = parseInt(hex.substring(0, 2), 16);\n    const g = parseInt(hex.substring(2, 4), 16);\n    const b = parseInt(hex.substring(4, 6), 16);\n\n    return {\n        r: r,\n        g: g,\n        b: b,\n        a: 1\n    };\n}\n\n// Creeper green and black colors\nconst green = hexToRgb('#00ff00');\nconst black = { r: 0, g: 0, b: 0, a: 1 };\n\n// 4 green, 4 black, 8 green\nmsg.payload = [\n    ...Array(4).fill(green),\n    ...Array(4).fill(black),\n    ...Array(8).fill(green)\n];\n\nreturn msg;\n",
        "outputs": 1,
        "timeout": 0,
        "noerr": 0,
        "initialize": "",
        "finalize": "",
        "libs": [],
        "x": 1800,
        "y": 820,
        "wires": [
            [
                "7cae7acefca23741"
            ]
        ]
    },
    {
        "id": "7cae7acefca23741",
        "type": "mqtt out",
        "z": "93bc9b581a312155",
        "name": "",
        "topic": "led",
        "qos": "",
        "retain": "",
        "respTopic": "",
        "contentType": "",
        "userProps": "",
        "correl": "",
        "expiry": "",
        "broker": "5058bca32a4f00c3",
        "x": 1950,
        "y": 840,
        "wires": []
    },
    {
        "id": "4894efe08e32e8d4",
        "type": "ui_button",
        "z": "93bc9b581a312155",
        "name": "",
        "group": "ab8d52c8070607ed",
        "order": 7,
        "width": 0,
        "height": 0,
        "passthru": false,
        "label": "Creeper",
        "tooltip": "",
        "color": "",
        "bgcolor": "",
        "className": "creeper",
        "icon": "",
        "payload": "creeper",
        "payloadType": "str",
        "topic": "payload",
        "topicType": "msg",
        "x": 1580,
        "y": 840,
        "wires": [
            [
                "49fb5c7a55a4dfd4",
                "3332273acd08501e",
                "5cb0188b5dea4c53"
            ]
        ]
    },
    {
        "id": "6a9d430692141c12",
        "type": "ui_text_input",
        "z": "93bc9b581a312155",
        "d": true,
        "name": "",
        "label": "Amount:",
        "tooltip": "",
        "group": "ab8d52c8070607ed",
        "order": 4,
        "width": 0,
        "height": 0,
        "passthru": true,
        "mode": "text",
        "delay": 300,
        "topic": "topic",
        "sendOnBlur": true,
        "className": "",
        "topicType": "msg",
        "x": 1660,
        "y": 460,
        "wires": [
            [
                "5faeccea24c098c8"
            ]
        ]
    },
    {
        "id": "5faeccea24c098c8",
        "type": "function",
        "z": "93bc9b581a312155",
        "d": true,
        "name": "function 10",
        "func": "// Ensure the payload is a number\nlet count = parseInt(msg.payload, 10);\n\nif (isNaN(count) || count < 1) {\n    node.warn(\"Payload is not a valid number greater than 0\");\n    return null;\n}\n\n// Create an array of messages to summon zombies\nlet messages = [];\n\nfor (let i = 0; i < count; i++) {\n    messages.push({\n        payload: \"/summon minecraft:zombie ~ ~ ~\"\n    });\n}\n\n// Send all summon commands\nreturn [messages];\n",
        "outputs": 1,
        "timeout": 0,
        "noerr": 0,
        "initialize": "",
        "finalize": "",
        "libs": [],
        "x": 1850,
        "y": 460,
        "wires": [
            []
        ]
    },
    {
        "id": "fa712774de43dc12",
        "type": "change",
        "z": "93bc9b581a312155",
        "name": "",
        "rules": [
            {
                "t": "set",
                "p": "payload",
                "pt": "msg",
                "to": "/execute at remked run summon zombie ~ ~ ~",
                "tot": "str"
            }
        ],
        "action": "",
        "property": "",
        "from": "",
        "to": "",
        "reg": false,
        "x": 1720,
        "y": 760,
        "wires": [
            [
                "3811e813afe59832"
            ]
        ]
    },
    {
        "id": "3332273acd08501e",
        "type": "change",
        "z": "93bc9b581a312155",
        "name": "",
        "rules": [
            {
                "t": "set",
                "p": "payload",
                "pt": "msg",
                "to": "/execute at remked run summon creeper ~ ~ ~",
                "tot": "str"
            }
        ],
        "action": "",
        "property": "",
        "from": "",
        "to": "",
        "reg": false,
        "x": 1740,
        "y": 900,
        "wires": [
            [
                "9306c491bdc98310"
            ]
        ]
    },
    {
        "id": "fdb4397d96d6255e",
        "type": "rcon",
        "z": "93bc9b581a312155",
        "name": "",
        "server": "974b018728e661cc",
        "command": "",
        "x": 1980,
        "y": 1140,
        "wires": [
            []
        ]
    },
    {
        "id": "12c80f51b33a7b4d",
        "type": "function",
        "z": "93bc9b581a312155",
        "name": "function 11",
        "func": "function hexToRgb(hexColor) {\n    const hex = hexColor.replace(/^#/, '');\n    const r = parseInt(hex.substring(0, 2), 16);\n    const g = parseInt(hex.substring(2, 4), 16);\n    const b = parseInt(hex.substring(4, 6), 16);\n\n    return {\n        r: r,\n        g: g,\n        b: b,\n        a: 1\n    };\n}\n\n// Function to interpolate between two RGB colors\nfunction interpolateColor(color1, color2, factor) {\n    return {\n        r: Math.round(color1.r + factor * (color2.r - color1.r)),\n        g: Math.round(color1.g + factor * (color2.g - color1.g)),\n        b: Math.round(color1.b + factor * (color2.b - color1.b)),\n        a: 1\n    };\n}\n\nconst red = hexToRgb('#ff0000');\nconst yellow = hexToRgb('#ffff00');\n\n// Create a gradient of 16 colors from red to yellow\nconst gradient = [];\nfor (let i = 0; i < 16; i++) {\n    const factor = i / 15;  // goes from 0 to 1\n    gradient.push(interpolateColor(red, yellow, factor));\n}\n\nmsg.payload = gradient;\nreturn msg;\n",
        "outputs": 1,
        "timeout": 0,
        "noerr": 0,
        "initialize": "",
        "finalize": "",
        "libs": [],
        "x": 1790,
        "y": 1020,
        "wires": [
            [
                "6587dda01956f8d4"
            ]
        ]
    },
    {
        "id": "6587dda01956f8d4",
        "type": "mqtt out",
        "z": "93bc9b581a312155",
        "name": "",
        "topic": "led",
        "qos": "",
        "retain": "",
        "respTopic": "",
        "contentType": "",
        "userProps": "",
        "correl": "",
        "expiry": "",
        "broker": "5058bca32a4f00c3",
        "x": 1960,
        "y": 1040,
        "wires": []
    },
    {
        "id": "65c9d53cc8c8d1e3",
        "type": "ui_button",
        "z": "93bc9b581a312155",
        "name": "",
        "group": "ab8d52c8070607ed",
        "order": 12,
        "width": 0,
        "height": 0,
        "passthru": false,
        "label": "Blaze",
        "tooltip": "",
        "color": "",
        "bgcolor": "",
        "className": "blaze",
        "icon": "",
        "payload": "blaze",
        "payloadType": "str",
        "topic": "payload",
        "topicType": "msg",
        "x": 1610,
        "y": 1040,
        "wires": [
            [
                "12c80f51b33a7b4d",
                "72f94aaf02c71f6f",
                "5cb0188b5dea4c53"
            ]
        ]
    },
    {
        "id": "72f94aaf02c71f6f",
        "type": "change",
        "z": "93bc9b581a312155",
        "name": "",
        "rules": [
            {
                "t": "set",
                "p": "payload",
                "pt": "msg",
                "to": "/execute at remked run summon blaze ~ ~ ~",
                "tot": "str"
            }
        ],
        "action": "",
        "property": "",
        "from": "",
        "to": "",
        "reg": false,
        "x": 1770,
        "y": 1100,
        "wires": [
            [
                "fdb4397d96d6255e"
            ]
        ]
    },
    {
        "id": "8c483790369c0ccd",
        "type": "ui_template",
        "z": "93bc9b581a312155",
        "group": "",
        "name": "",
        "order": 0,
        "width": 0,
        "height": 0,
        "format": "<style>\n/* Base button transition and rounded corners for all styled buttons */\n.zombie button,\n.creeper button,\n.blaze button,\n.enderman button,\n.skeleton button,\n.wskeleton button,\n.witch button,\n.spider button,\n.pig button,\n.sheep button,\n.cow button,\n.chicken button,\n.kill button {\nfont-weight: bold;\nborder: 4px solid black;\nborder-radius: 12px;\ntransition: all 0.3s ease;\ncursor: pointer;\n}\n\n/* Hover scale effect for all buttons */\n.zombie button:hover,\n.creeper button:hover,\n.blaze button:hover,\n.enderman button:hover,\n.skeleton button:hover,\n.wskeleton button:hover,\n.witch button:hover,\n.spider button:hover,\n.pig button:hover,\n.sheep button:hover,\n.cow button:hover,\n.chicken button:hover,\n.kill button:hover {\ntransform: scale(1.05);\n}\n\n/* Specific styles for each class remain the same */\n.creeper button {\nbackground-image: linear-gradient(to right, rgba(0, 0, 0, 1), rgba(0, 128, 0, 1));\n}\n\n.blaze button {\nbackground-image: linear-gradient(to right, rgba(255, 255, 0, 1), rgba(255, 0, 0, 1));\n}\n\n.enderman button {\nbackground-image: linear-gradient(to right, rgba(128, 0, 128, 1), rgba(0, 0, 0, 1));\n}\n\n.skeleton button {\ncolor: black;\n}\n\n.witch button {\ncolor: white;\nbackground-image: linear-gradient(to right,\nrgba(128, 0, 128, 1) 0%,\nrgba(0, 0, 0, 1) 20%,\nrgba(0, 100, 0, 1) 50%,\nrgba(0, 0, 0, 1) 80%,\nrgba(128, 0, 128, 1) 100%\n);\n}\n\n.spider button {\ncolor: white;\nbackground-image: linear-gradient(to right, black 0%, red 50%, black 100%);\n}\n\n.pig button {\nbackground-image: linear-gradient(to right,\nrgba(255, 182, 193, 1) 0%,\nrgba(255, 99, 71, 1) 50%,\nrgba(255, 182, 193, 1) 100%\n);\nborder-color: darkred;\n}\n\n.sheep button {\nbackground-image: linear-gradient(to right,\nrgba(255, 255, 255, 1) 0%,\nrgba(255, 182, 193, 1) 50%,\nrgba(255, 255, 255, 1) 100%\n);\nborder-color: darkgray;\n}\n\n.cow button {\nbackground-image: linear-gradient(to right,\nrgba(139, 69, 19, 1) 0%,\nrgba(255, 255, 255, 1) 50%,\nrgba(139, 69, 19, 1) 100%\n);\n}\n\n.chicken button {\nbackground-image: linear-gradient(to right,\nrgba(255, 255, 255, 1) 0%,\nrgba(255, 255, 0, 1) 50%,\nrgba(255, 255, 255, 1) 100%\n);\nborder-color: orange;\n}\n\n/* Special kill button animation */\n.kill button {\ncolor: white;\nbackground-image: linear-gradient(to right, #8B0000, #000000, #8B0000);\nborder: 4px solid crimson;\nbox-shadow: 0 0 15px crimson, inset 0 0 10px black;\ntext-shadow: 1px 1px 4px black;\nanimation: pulse-glow 2s infinite;\n}\n\n.kill button:hover {\nbackground-image: linear-gradient(to right, #ff0000, #000000, #ff0000);\nbox-shadow: 0 0 20px red, inset 0 0 15px darkred;\n}\n\n.random button {\nfont-weight: bold;\nborder: 4px solid black;\nborder-radius: 12px;\ncursor: pointer;\ncolor: white;\nbackground-image: linear-gradient(45deg, red, orange, yellow, green, blue, indigo, violet);\nbackground-size: 400% 400%; /* Ensures the gradient is large enough to move */\nanimation: gradientMove 5s ease infinite, glowEffect 2s alternate infinite;\ntext-shadow: 1px 1px 3px black;\npadding: 15px 30px;\nfont-size: 16px;\nposition: relative;\ntransition: transform 0.3s ease; /* Transition for the scale effect */\n}\n\n.random button:hover {\ntransform: scale(1.1);\n}\n\n/* Animation to move the rainbow gradient */\n@keyframes gradientMove {\n  0% {\n    background-position: 0% 50%;\n  }\n  50% {\n    background-position: 100% 50%;\n  }\n  100% {\n    background-position: 0% 50%;\n  }\n}\n\n/* Glow effect that makes the button pulsate */\n@keyframes glowEffect {\n  0% {\n    box-shadow: 0 0 10px rgba(255, 165, 0, 0.8), inset 0 0 5px rgba(0, 255, 255, 0.6);\n  }\n  50% {\n    box-shadow: 0 0 30px rgba(0, 255, 255, 1), inset 0 0 20px rgba(255, 165, 0, 0.8);\n  }\n  100% {\n    box-shadow: 0 0 10px rgba(255, 165, 0, 0.8), inset 0 0 5px rgba(0, 255, 255, 0.6);\n  }\n}\n.boom button {\n  font-weight: bold;\n  border: 4px solid black;\n  border-radius: 12px;\n  cursor: pointer;\n  color: white;\n  background-image: linear-gradient(45deg, red, orange, yellow, #ff4500);\n  background-size: 400% 400%; /* Big enough to move the gradient */\n  animation: gradientMove 5s ease infinite, explodeEffect 1.5s alternate infinite;\n  text-shadow: 1px 1px 3px black;\n  padding: 15px 30px;\n  font-size: 18px;\n  position: relative;\n  box-shadow: 0 0 10px rgba(255, 69, 0, 0.6), inset 0 0 5px rgba(255, 69, 0, 0.3);\n  transition: all 0.3s ease;\n}\n\n.boom button:hover {\n  transform: scale(1.1);\n}\n\n/* Moving fiery gradient for explosion effect */\n@keyframes gradientMove {\n  0% {\n    background-position: 0% 50%;\n  }\n  50% {\n    background-position: 100% 50%;\n  }\n  100% {\n    background-position: 0% 50%;\n  }\n}\n\n@keyframes explodeEffect {\n  0% {\n    box-shadow: 0 0 20px rgba(255, 69, 0, 1), inset 0 0 10px rgba(255, 69, 0, 0.8);\n    transform: scale(1);\n  }\n  50% {\n    box-shadow: 0 0 40px rgba(255, 69, 0, 1), inset 0 0 20px rgba(255, 69, 0, 0.9);\n    transform: scale(1.1);  /* Reduced scale */\n  }\n  100% {\n    box-shadow: 0 0 20px rgba(255, 69, 0, 1), inset 0 0 10px rgba(255, 69, 0, 0.8);\n    transform: scale(1.05);  /* Reduced scale */\n  }\n}\n\n\n/* Adding some additional sparks effect */\n@keyframes sparkEffect {\n  0% {\n    content: \"\";\n    position: absolute;\n    top: 50%;\n    left: 50%;\n    width: 2px;\n    height: 2px;\n    background-color: white;\n    opacity: 0;\n  }\n  50% {\n    content: \"\";\n    position: absolute;\n    top: 50%;\n    left: 50%;\n    width: 5px;\n    height: 5px;\n    background-color: white;\n    opacity: 1;\n    animation: sparkMove 0.5s infinite;\n  }\n  100% {\n    opacity: 0;\n  }\n}\n\n@keyframes sparkMove {\n  0% {\n    transform: translate(-50%, -50%) scale(0.5);\n  }\n  50% {\n    transform: translate(-70%, -70%) scale(1);\n  }\n  100% {\n    transform: translate(-50%, -50%) scale(0.5);\n  }\n}\n\n.text {\n  font-size: 32px;\n  text-align: center;\n  background: linear-gradient(270deg, #00f0ff, #ff00f7, #00ff6a, #ffe600, #00f0ff);\n  background-size: 1000% 1000%;\n  -webkit-background-clip: text;\n  -webkit-text-fill-color: transparent;\n  animation: gradientGlow 6s ease infinite, glow 2s ease-in-out infinite alternate;\n  padding: 20px 0;\n  margin-bottom: 20px;\n}\n\n/* Animated gradient colors */\n@keyframes gradientGlow {\n  0% {\n    background-position: 0% 50%;\n  }\n  50% {\n    background-position: 100% 50%;\n  }\n  100% {\n    background-position: 0% 50%;\n  }\n}\n\n/* Animated glow effect around the text */\n@keyframes glow {\n  from {\n    text-shadow: 0 0 10px #00f0ff, 0 0 20px #00f0ff, 0 0 30px #00f0ff;\n  }\n  to {\n    text-shadow: 0 0 20px #ff00f7, 0 0 30px #00ff6a, 0 0 40px #ffe600;\n  }\n}\n.teleport button {\nfont-weight: bold;\nborder: 4px solid #6a0dad;\nborder-radius: 12px;\ncursor: pointer;\ncolor: white;\nbackground-image: linear-gradient(45deg, #8a2be2, #4b0082, #000000, #4b0082, #8a2be2);\nbackground-size: 300% 300%;\nanimation: teleportPulse 3s ease-in-out infinite, teleportGlow 1.5s ease-in-out infinite;\ntext-shadow: 1px 1px 3px black;\npadding: 15px 30px;\nfont-size: 18px;\nposition: relative;\nbox-shadow: 0 0 15px rgba(138, 43, 226, 0.6), inset 0 0 10px rgba(75, 0, 130, 0.4);\ntransition: transform 0.3s ease;\n}\n\n.teleport button:hover {\ntransform: scale(1.1) rotate(1deg);\nbox-shadow: 0 0 25px rgba(138, 43, 226, 0.9), inset 0 0 15px rgba(75, 0, 130, 0.7);\n}\n\n/* Animation for a pulsating teleport energy */\n@keyframes teleportPulse {\n0% {\nbackground-position: 0% 50%;\n}\n50% {\nbackground-position: 100% 50%;\n}\n100% {\nbackground-position: 0% 50%;\n}\n}\n\n/* Subtle glow fluctuation like magical energy */\n@keyframes teleportGlow {\n0% {\nbox-shadow: 0 0 10px #6a0dad, inset 0 0 5px #4b0082;\n}\n50% {\nbox-shadow: 0 0 25px #b266ff, inset 0 0 15px #8a2be2;\n}\n100% {\nbox-shadow: 0 0 10px #6a0dad, inset 0 0 5px #4b0082;\n}\n}\n\n</style>",
        "storeOutMessages": true,
        "fwdInMessages": true,
        "resendOnRefresh": true,
        "templateScope": "global",
        "className": "",
        "x": 2560,
        "y": 1120,
        "wires": [
            []
        ]
    },
    {
        "id": "71aba73a14356e68",
        "type": "rcon",
        "z": "93bc9b581a312155",
        "name": "",
        "server": "974b018728e661cc",
        "command": "",
        "x": 1950,
        "y": 1340,
        "wires": [
            []
        ]
    },
    {
        "id": "c4c94c39ec040cd5",
        "type": "function",
        "z": "93bc9b581a312155",
        "name": "function 12",
        "func": "function hexToRgb(hexColor) {\n    const hex = hexColor.replace(/^#/, '');\n    const r = parseInt(hex.substring(0, 2), 16);\n    const g = parseInt(hex.substring(2, 4), 16);\n    const b = parseInt(hex.substring(4, 6), 16);\n\n    return {\n        r: r,\n        g: g,\n        b: b,\n        a: 1\n    };\n}\n\n// Function to interpolate between two RGB colors\nfunction interpolateColor(color1, color2, factor) {\n    return {\n        r: Math.round(color1.r + factor * (color2.r - color1.r)),\n        g: Math.round(color1.g + factor * (color2.g - color1.g)),\n        b: Math.round(color1.b + factor * (color2.b - color1.b)),\n        a: 1\n    };\n}\n\nconst purple = hexToRgb('#800080');  // purple\nconst black = hexToRgb('#000000');   // black\n\n// Create a gradient of 16 colors from purple to black\nconst gradient = [];\nfor (let i = 0; i < 16; i++) {\n    const factor = i / 15;  // goes from 0 to 1\n    gradient.push(interpolateColor(purple, black, factor));\n}\n\nmsg.payload = gradient;\nreturn msg;\n",
        "outputs": 1,
        "timeout": 0,
        "noerr": 0,
        "initialize": "",
        "finalize": "",
        "libs": [],
        "x": 1830,
        "y": 1200,
        "wires": [
            [
                "a24a843b06bced35"
            ]
        ]
    },
    {
        "id": "a24a843b06bced35",
        "type": "mqtt out",
        "z": "93bc9b581a312155",
        "name": "",
        "topic": "led",
        "qos": "",
        "retain": "",
        "respTopic": "",
        "contentType": "",
        "userProps": "",
        "correl": "",
        "expiry": "",
        "broker": "5058bca32a4f00c3",
        "x": 1970,
        "y": 1240,
        "wires": []
    },
    {
        "id": "6a3e08e530895150",
        "type": "ui_button",
        "z": "93bc9b581a312155",
        "name": "",
        "group": "ab8d52c8070607ed",
        "order": 9,
        "width": 0,
        "height": 0,
        "passthru": false,
        "label": "Enderman",
        "tooltip": "",
        "color": "",
        "bgcolor": "",
        "className": "enderman",
        "icon": "",
        "payload": "enderman",
        "payloadType": "str",
        "topic": "payload",
        "topicType": "msg",
        "x": 1600,
        "y": 1240,
        "wires": [
            [
                "c4c94c39ec040cd5",
                "bfaf919a2c559d2b",
                "5cb0188b5dea4c53"
            ]
        ]
    },
    {
        "id": "bfaf919a2c559d2b",
        "type": "change",
        "z": "93bc9b581a312155",
        "name": "",
        "rules": [
            {
                "t": "set",
                "p": "payload",
                "pt": "msg",
                "to": "/execute at remked run summon enderman ~ ~ ~",
                "tot": "str"
            }
        ],
        "action": "",
        "property": "",
        "from": "",
        "to": "",
        "reg": false,
        "x": 1740,
        "y": 1300,
        "wires": [
            [
                "71aba73a14356e68"
            ]
        ]
    },
    {
        "id": "2d96715e764a10f2",
        "type": "rcon",
        "z": "93bc9b581a312155",
        "name": "",
        "server": "974b018728e661cc",
        "command": "",
        "x": 1930,
        "y": 1520,
        "wires": [
            []
        ]
    },
    {
        "id": "912ded125b464c7d",
        "type": "mqtt out",
        "z": "93bc9b581a312155",
        "name": "",
        "topic": "led",
        "qos": "",
        "retain": "",
        "respTopic": "",
        "contentType": "",
        "userProps": "",
        "correl": "",
        "expiry": "",
        "broker": "5058bca32a4f00c3",
        "x": 1950,
        "y": 1420,
        "wires": []
    },
    {
        "id": "d890ba9589801d26",
        "type": "ui_button",
        "z": "93bc9b581a312155",
        "name": "",
        "group": "ab8d52c8070607ed",
        "order": 5,
        "width": 0,
        "height": 0,
        "passthru": false,
        "label": "Skeleton",
        "tooltip": "",
        "color": "black",
        "bgcolor": "white",
        "className": "skeleton",
        "icon": "",
        "payload": "skeleton",
        "payloadType": "str",
        "topic": "payload",
        "topicType": "msg",
        "x": 1580,
        "y": 1400,
        "wires": [
            [
                "eda5332d69d52f83",
                "7625f780cacd9446",
                "5cb0188b5dea4c53"
            ]
        ]
    },
    {
        "id": "eda5332d69d52f83",
        "type": "change",
        "z": "93bc9b581a312155",
        "name": "",
        "rules": [
            {
                "t": "set",
                "p": "payload",
                "pt": "msg",
                "to": "/execute at remked run summon skeleton ~ ~ ~",
                "tot": "str"
            }
        ],
        "action": "",
        "property": "",
        "from": "",
        "to": "",
        "reg": false,
        "x": 1720,
        "y": 1480,
        "wires": [
            [
                "2d96715e764a10f2"
            ]
        ]
    },
    {
        "id": "7625f780cacd9446",
        "type": "function",
        "z": "93bc9b581a312155",
        "name": "function 13",
        "func": "function hexToRgb(hexColor) {\n    const hex = hexColor.replace(/^#/, '');\n    const r = parseInt(hex.substring(0, 2), 16);\n    const g = parseInt(hex.substring(2, 4), 16);\n    const b = parseInt(hex.substring(4, 6), 16);\n\n    return {\n        r: r,\n        g: g,\n        b: b,\n        a: 1\n    };\n}\n\nconst white = hexToRgb('#ffffff');  // white\n\nmsg.payload = Array(16).fill(white);\nreturn msg;\n",
        "outputs": 1,
        "timeout": 0,
        "noerr": 0,
        "initialize": "",
        "finalize": "",
        "libs": [],
        "x": 1770,
        "y": 1400,
        "wires": [
            [
                "912ded125b464c7d"
            ]
        ]
    },
    {
        "id": "3cb2d9adc8ddb394",
        "type": "rcon",
        "z": "93bc9b581a312155",
        "name": "",
        "server": "974b018728e661cc",
        "command": "",
        "x": 1910,
        "y": 1700,
        "wires": [
            []
        ]
    },
    {
        "id": "8f211a5ea0293e4c",
        "type": "mqtt out",
        "z": "93bc9b581a312155",
        "name": "",
        "topic": "led",
        "qos": "",
        "retain": "",
        "respTopic": "",
        "contentType": "",
        "userProps": "",
        "correl": "",
        "expiry": "",
        "broker": "5058bca32a4f00c3",
        "x": 1930,
        "y": 1600,
        "wires": []
    },
    {
        "id": "87cfbafe0c4d2ae6",
        "type": "ui_button",
        "z": "93bc9b581a312155",
        "name": "",
        "group": "ab8d52c8070607ed",
        "order": 8,
        "width": 0,
        "height": 0,
        "passthru": false,
        "label": "Witch",
        "tooltip": "",
        "color": "",
        "bgcolor": "",
        "className": "witch",
        "icon": "",
        "payload": "witch",
        "payloadType": "str",
        "topic": "payload",
        "topicType": "msg",
        "x": 1550,
        "y": 1580,
        "wires": [
            [
                "875246e007418ea8",
                "131ad328e1e3651b",
                "5cb0188b5dea4c53"
            ]
        ]
    },
    {
        "id": "875246e007418ea8",
        "type": "change",
        "z": "93bc9b581a312155",
        "name": "",
        "rules": [
            {
                "t": "set",
                "p": "payload",
                "pt": "msg",
                "to": "/execute at remked run summon witch ~ ~ ~",
                "tot": "str"
            }
        ],
        "action": "",
        "property": "",
        "from": "",
        "to": "",
        "reg": false,
        "x": 1700,
        "y": 1660,
        "wires": [
            [
                "3cb2d9adc8ddb394"
            ]
        ]
    },
    {
        "id": "131ad328e1e3651b",
        "type": "function",
        "z": "93bc9b581a312155",
        "name": "function 14",
        "func": "function hexToRgb(hexColor) {\n    const hex = hexColor.replace(/^#/, '');\n    const r = parseInt(hex.substring(0, 2), 16);\n    const g = parseInt(hex.substring(2, 4), 16);\n    const b = parseInt(hex.substring(4, 6), 16);\n\n    return { r, g, b, a: 1 };\n}\n\nconst purple = hexToRgb('#800080');\nconst green  = hexToRgb('#00ff00');\n\nconst leds = [];\n\nfor (let i = 0; i < 16; i++) {\n    if (i >= 6 && i <= 9) {\n        leds[i] = green;\n    } else {\n        leds[i] = purple;\n    }\n}\n\nmsg.payload = leds;\nreturn msg;\n",
        "outputs": 1,
        "timeout": 0,
        "noerr": 0,
        "initialize": "",
        "finalize": "",
        "libs": [],
        "x": 1750,
        "y": 1580,
        "wires": [
            [
                "8f211a5ea0293e4c"
            ]
        ]
    },
    {
        "id": "be430d0c65675ce7",
        "type": "rcon",
        "z": "93bc9b581a312155",
        "name": "",
        "server": "974b018728e661cc",
        "command": "",
        "x": 1870,
        "y": 1920,
        "wires": [
            []
        ]
    },
    {
        "id": "2f52f7a20ab5525a",
        "type": "mqtt out",
        "z": "93bc9b581a312155",
        "name": "",
        "topic": "led",
        "qos": "",
        "retain": "",
        "respTopic": "",
        "contentType": "",
        "userProps": "",
        "correl": "",
        "expiry": "",
        "broker": "5058bca32a4f00c3",
        "x": 1890,
        "y": 1820,
        "wires": []
    },
    {
        "id": "18c1a04133ee8e61",
        "type": "ui_button",
        "z": "93bc9b581a312155",
        "name": "",
        "group": "ab8d52c8070607ed",
        "order": 11,
        "width": 0,
        "height": 0,
        "passthru": false,
        "label": "Spider",
        "tooltip": "",
        "color": "",
        "bgcolor": "",
        "className": "spider",
        "icon": "",
        "payload": "spider",
        "payloadType": "str",
        "topic": "payload",
        "topicType": "msg",
        "x": 1510,
        "y": 1800,
        "wires": [
            [
                "028c20fb4027fe34",
                "5748cfc52df35e99",
                "5cb0188b5dea4c53"
            ]
        ]
    },
    {
        "id": "028c20fb4027fe34",
        "type": "change",
        "z": "93bc9b581a312155",
        "name": "",
        "rules": [
            {
                "t": "set",
                "p": "payload",
                "pt": "msg",
                "to": "/execute at remked run summon spider ~ ~ ~",
                "tot": "str"
            }
        ],
        "action": "",
        "property": "",
        "from": "",
        "to": "",
        "reg": false,
        "x": 1660,
        "y": 1880,
        "wires": [
            [
                "be430d0c65675ce7"
            ]
        ]
    },
    {
        "id": "5748cfc52df35e99",
        "type": "function",
        "z": "93bc9b581a312155",
        "name": "function 15",
        "func": "function hexToRgb(hexColor) {\n    const hex = hexColor.replace(/^#/, '');\n    const r = parseInt(hex.substring(0, 2), 16);\n    const g = parseInt(hex.substring(2, 4), 16);\n    const b = parseInt(hex.substring(4, 6), 16);\n\n    return { r, g, b, a: 1 };\n}\n\nfunction interpolateColor(color1, color2, factor) {\n    return {\n        r: Math.round(color1.r + (color2.r - color1.r) * factor),\n        g: Math.round(color1.g + (color2.g - color1.g) * factor),\n        b: Math.round(color1.b + (color2.b - color1.b) * factor),\n        a: 1\n    };\n}\n\nconst black = hexToRgb('#000000'); // black\nconst red = hexToRgb('#ff0000');   // red\n\nconst leds = [];\n\nfor (let i = 0; i < 16; i++) {\n    if (i < 4) {\n        // black -> red (first few LEDs)\n        const factor = i / 3;\n        leds[i] = interpolateColor(black, red, factor);\n    } else if (i >= 12) {\n        // red -> black (last few LEDs)\n        const factor = (i - 12) / 3;\n        leds[i] = interpolateColor(red, black, factor);\n    } else {\n        // middle LEDs are mostly red\n        leds[i] = red;\n    }\n}\n\nmsg.payload = leds;\nreturn msg;\n",
        "outputs": 1,
        "timeout": 0,
        "noerr": 0,
        "initialize": "",
        "finalize": "",
        "libs": [],
        "x": 1710,
        "y": 1800,
        "wires": [
            [
                "2f52f7a20ab5525a"
            ]
        ]
    },
    {
        "id": "8b0e1dd606733abf",
        "type": "rcon",
        "z": "93bc9b581a312155",
        "name": "",
        "server": "974b018728e661cc",
        "command": "",
        "x": 1850,
        "y": 2120,
        "wires": [
            []
        ]
    },
    {
        "id": "aa8cfb308571680a",
        "type": "mqtt out",
        "z": "93bc9b581a312155",
        "name": "",
        "topic": "led",
        "qos": "",
        "retain": "",
        "respTopic": "",
        "contentType": "",
        "userProps": "",
        "correl": "",
        "expiry": "",
        "broker": "5058bca32a4f00c3",
        "x": 1870,
        "y": 2020,
        "wires": []
    },
    {
        "id": "a3e4d168d7917da5",
        "type": "ui_button",
        "z": "93bc9b581a312155",
        "name": "",
        "group": "ab8d52c8070607ed",
        "order": 10,
        "width": 0,
        "height": 0,
        "passthru": false,
        "label": "Wither Skeleton",
        "tooltip": "",
        "color": "white",
        "bgcolor": "black",
        "className": "wskeleton",
        "icon": "",
        "payload": "wither skeleton",
        "payloadType": "str",
        "topic": "payload",
        "topicType": "msg",
        "x": 1520,
        "y": 1980,
        "wires": [
            [
                "c6369a9445def82f",
                "c91af1bdcec8d0ca",
                "5cb0188b5dea4c53"
            ]
        ]
    },
    {
        "id": "c6369a9445def82f",
        "type": "change",
        "z": "93bc9b581a312155",
        "name": "",
        "rules": [
            {
                "t": "set",
                "p": "payload",
                "pt": "msg",
                "to": "/execute at remked run summon wither_skeleton ~ ~ ~",
                "tot": "str"
            }
        ],
        "action": "",
        "property": "",
        "from": "",
        "to": "",
        "reg": false,
        "x": 1640,
        "y": 2080,
        "wires": [
            [
                "8b0e1dd606733abf"
            ]
        ]
    },
    {
        "id": "c91af1bdcec8d0ca",
        "type": "function",
        "z": "93bc9b581a312155",
        "name": "function 16",
        "func": "function hexToRgb(hexColor) {\n    const hex = hexColor.replace(/^#/, '');\n    const r = parseInt(hex.substring(0, 2), 16);\n    const g = parseInt(hex.substring(2, 4), 16);\n    const b = parseInt(hex.substring(4, 6), 16);\n\n    return {\n        r: r,\n        g: g,\n        b: b,\n        a: 1\n    };\n}\n\nconst color = hexToRgb('00000');  // black\n\nmsg.payload = Array(16).fill(color);\nreturn msg;\n",
        "outputs": 1,
        "timeout": 0,
        "noerr": 0,
        "initialize": "",
        "finalize": "",
        "libs": [],
        "x": 1730,
        "y": 2000,
        "wires": [
            [
                "aa8cfb308571680a"
            ]
        ]
    },
    {
        "id": "9cdc91ef2ff8110b",
        "type": "ui_text",
        "z": "93bc9b581a312155",
        "group": "ab8d52c8070607ed",
        "order": 13,
        "width": 0,
        "height": 0,
        "name": "",
        "label": "Friendly Mobs",
        "format": "",
        "layout": "col-center",
        "className": "",
        "style": true,
        "font": "Trebuchet MS,Helvetica,sans-serif",
        "fontSize": "30",
        "color": "#000000",
        "x": 2640,
        "y": 1560,
        "wires": []
    },
    {
        "id": "4973123287d66a2c",
        "type": "ui_text",
        "z": "93bc9b581a312155",
        "group": "ab8d52c8070607ed",
        "order": 3,
        "width": 0,
        "height": 0,
        "name": "",
        "label": "Hostile mobs",
        "format": "",
        "layout": "col-center",
        "className": "",
        "style": true,
        "font": "Trebuchet MS,Helvetica,sans-serif",
        "fontSize": "30",
        "color": "#000000",
        "x": 1770,
        "y": 580,
        "wires": []
    },
    {
        "id": "5cb0188b5dea4c53",
        "type": "ui_toast",
        "z": "93bc9b581a312155",
        "position": "top right",
        "displayTime": "3",
        "highlight": "black",
        "sendall": true,
        "outputs": 0,
        "ok": "OK",
        "cancel": "",
        "raw": false,
        "className": "",
        "topic": "added mob",
        "name": "added mob",
        "x": 2570,
        "y": 1200,
        "wires": []
    },
    {
        "id": "51fc7d87a7ddc0b8",
        "type": "ui_text",
        "z": "93bc9b581a312155",
        "group": "ab8d52c8070607ed",
        "order": 2,
        "width": 0,
        "height": 0,
        "name": "",
        "label": "",
        "format": "{{msg.payload}}",
        "layout": "row-spread",
        "className": "",
        "style": true,
        "font": "",
        "fontSize": "10",
        "color": "#000000",
        "x": 1750,
        "y": 280,
        "wires": []
    },
    {
        "id": "5efbd494560a13b7",
        "type": "rcon",
        "z": "93bc9b581a312155",
        "name": "",
        "server": "974b018728e661cc",
        "command": "",
        "x": 2730,
        "y": 1780,
        "wires": [
            []
        ]
    },
    {
        "id": "422b5838d1cc1b5a",
        "type": "ui_button",
        "z": "93bc9b581a312155",
        "name": "",
        "group": "ab8d52c8070607ed",
        "order": 14,
        "width": 0,
        "height": 0,
        "passthru": false,
        "label": "Cow",
        "tooltip": "",
        "color": "black",
        "bgcolor": "",
        "className": "cow",
        "icon": "",
        "payload": "cow",
        "payloadType": "str",
        "topic": "payload",
        "topicType": "msg",
        "x": 2310,
        "y": 1660,
        "wires": [
            [
                "2a4e041678de97a8",
                "dee338ee44d7eca4",
                "5cb0188b5dea4c53"
            ]
        ]
    },
    {
        "id": "2a4e041678de97a8",
        "type": "change",
        "z": "93bc9b581a312155",
        "name": "",
        "rules": [
            {
                "t": "set",
                "p": "payload",
                "pt": "msg",
                "to": "/execute at remked run summon cow ~ ~ ~",
                "tot": "str"
            }
        ],
        "action": "",
        "property": "",
        "from": "",
        "to": "",
        "reg": false,
        "x": 2520,
        "y": 1740,
        "wires": [
            [
                "5efbd494560a13b7"
            ]
        ]
    },
    {
        "id": "dee338ee44d7eca4",
        "type": "function",
        "z": "93bc9b581a312155",
        "name": "function 17",
        "func": "function hexToRgb(hexColor) {\n    const hex = hexColor.replace(/^#/, '');\n    const r = parseInt(hex.substring(0, 2), 16);\n    const g = parseInt(hex.substring(2, 4), 16);\n    const b = parseInt(hex.substring(4, 6), 16);\n\n    return { r, g, b, a: 1 };\n}\n\nfunction interpolateColor(color1, color2, factor) {\n    return {\n        r: Math.round(color1.r + (color2.r - color1.r) * factor),\n        g: Math.round(color1.g + (color2.g - color1.g) * factor),\n        b: Math.round(color1.b + (color2.b - color1.b) * factor),\n        a: 1\n    };\n}\n\nconst brown = hexToRgb('#8B4513'); // brown\nconst white = hexToRgb('#FFFFFF'); // white\n\nconst leds = [];\n\nfor (let i = 0; i < 16; i++) {\n    if (i < 4) {\n        // brown -> white (first few LEDs)\n        const factor = i / 3;\n        leds[i] = interpolateColor(brown, white, factor);\n    } else if (i >= 12) {\n        // white -> brown (last few LEDs)\n        const factor = (i - 12) / 3;\n        leds[i] = interpolateColor(white, brown, factor);\n    } else {\n        // middle LEDs are white\n        leds[i] = white;\n    }\n}\n\nmsg.payload = leds;\nreturn msg;\n",
        "outputs": 1,
        "timeout": 0,
        "noerr": 0,
        "initialize": "",
        "finalize": "",
        "libs": [],
        "x": 2570,
        "y": 1660,
        "wires": [
            [
                "e15c8bad93c0898a"
            ]
        ]
    },
    {
        "id": "e15c8bad93c0898a",
        "type": "mqtt out",
        "z": "93bc9b581a312155",
        "name": "",
        "topic": "led",
        "qos": "",
        "retain": "",
        "respTopic": "",
        "contentType": "",
        "userProps": "",
        "correl": "",
        "expiry": "",
        "broker": "5058bca32a4f00c3",
        "x": 2730,
        "y": 1700,
        "wires": []
    },
    {
        "id": "a2c968caa24e47c7",
        "type": "rcon",
        "z": "93bc9b581a312155",
        "name": "",
        "server": "974b018728e661cc",
        "command": "",
        "x": 2670,
        "y": 1940,
        "wires": [
            []
        ]
    },
    {
        "id": "3f15d387d773e494",
        "type": "ui_button",
        "z": "93bc9b581a312155",
        "name": "",
        "group": "ab8d52c8070607ed",
        "order": 15,
        "width": 0,
        "height": 0,
        "passthru": false,
        "label": "Pig",
        "tooltip": "",
        "color": "black",
        "bgcolor": "",
        "className": "pig",
        "icon": "",
        "payload": "pig",
        "payloadType": "str",
        "topic": "payload",
        "topicType": "msg",
        "x": 2310,
        "y": 1820,
        "wires": [
            [
                "14f2276cb5c3497a",
                "bbfcd24392046909",
                "5cb0188b5dea4c53"
            ]
        ]
    },
    {
        "id": "14f2276cb5c3497a",
        "type": "change",
        "z": "93bc9b581a312155",
        "name": "",
        "rules": [
            {
                "t": "set",
                "p": "payload",
                "pt": "msg",
                "to": "/execute at remked run summon pig ~ ~ ~",
                "tot": "str"
            }
        ],
        "action": "",
        "property": "",
        "from": "",
        "to": "",
        "reg": false,
        "x": 2460,
        "y": 1900,
        "wires": [
            [
                "a2c968caa24e47c7"
            ]
        ]
    },
    {
        "id": "bbfcd24392046909",
        "type": "function",
        "z": "93bc9b581a312155",
        "name": "function 18",
        "func": "function hexToRgb(hexColor) {\n    const hex = hexColor.replace(/^#/, '');\n    const r = parseInt(hex.substring(0, 2), 16);\n    const g = parseInt(hex.substring(2, 4), 16);\n    const b = parseInt(hex.substring(4, 6), 16);\n\n    return { r, g, b, a: 1 };\n}\n\nfunction interpolateColor(color1, color2, factor) {\n    return {\n        r: Math.round(color1.r + (color2.r - color1.r) * factor),\n        g: Math.round(color1.g + (color2.g - color1.g) * factor),\n        b: Math.round(color1.b + (color2.b - color1.b) * factor),\n        a: 1\n    };\n}\n\nconst red = hexToRgb('#FF0000');    // red\nconst pink = hexToRgb('#FFC0CB');   // pink\n\nconst leds = [];\n\nfor (let i = 0; i < 8; i++) {\n    const factor = i / 7; // from 0 to 1\n    leds[i] = interpolateColor(red, pink, factor);\n}\n\nfor (let i = 8; i < 16; i++) {\n    const factor = (i - 8) / 7; // from 0 to 1\n    leds[i] = interpolateColor(pink, red, factor);\n}\n\nmsg.payload = leds;\nreturn msg;\n",
        "outputs": 1,
        "timeout": 0,
        "noerr": 0,
        "initialize": "",
        "finalize": "",
        "libs": [],
        "x": 2510,
        "y": 1820,
        "wires": [
            [
                "c27969e065b70fa8"
            ]
        ]
    },
    {
        "id": "c27969e065b70fa8",
        "type": "mqtt out",
        "z": "93bc9b581a312155",
        "name": "",
        "topic": "led",
        "qos": "",
        "retain": "",
        "respTopic": "",
        "contentType": "",
        "userProps": "",
        "correl": "",
        "expiry": "",
        "broker": "5058bca32a4f00c3",
        "x": 2670,
        "y": 1860,
        "wires": []
    },
    {
        "id": "a614e76dd871c1c9",
        "type": "rcon",
        "z": "93bc9b581a312155",
        "name": "",
        "server": "974b018728e661cc",
        "command": "",
        "x": 2650,
        "y": 2120,
        "wires": [
            []
        ]
    },
    {
        "id": "29342984d69a8deb",
        "type": "ui_button",
        "z": "93bc9b581a312155",
        "name": "",
        "group": "ab8d52c8070607ed",
        "order": 16,
        "width": 0,
        "height": 0,
        "passthru": false,
        "label": "Sheep",
        "tooltip": "",
        "color": "black",
        "bgcolor": "",
        "className": "sheep",
        "icon": "",
        "payload": "sheep",
        "payloadType": "str",
        "topic": "payload",
        "topicType": "msg",
        "x": 2290,
        "y": 2000,
        "wires": [
            [
                "a0425afb66de63aa",
                "be100e42f1b1bfa3",
                "5cb0188b5dea4c53"
            ]
        ]
    },
    {
        "id": "a0425afb66de63aa",
        "type": "change",
        "z": "93bc9b581a312155",
        "name": "",
        "rules": [
            {
                "t": "set",
                "p": "payload",
                "pt": "msg",
                "to": "/execute at remked run summon sheep ~ ~ ~",
                "tot": "str"
            }
        ],
        "action": "",
        "property": "",
        "from": "",
        "to": "",
        "reg": false,
        "x": 2440,
        "y": 2080,
        "wires": [
            [
                "a614e76dd871c1c9"
            ]
        ]
    },
    {
        "id": "be100e42f1b1bfa3",
        "type": "function",
        "z": "93bc9b581a312155",
        "name": "function 19",
        "func": "function hexToRgb(hexColor) {\n    const hex = hexColor.replace(/^#/, '');\n    const r = parseInt(hex.substring(0, 2), 16);\n    const g = parseInt(hex.substring(2, 4), 16);\n    const b = parseInt(hex.substring(4, 6), 16);\n\n    return { r, g, b, a: 1 };\n}\n\nfunction interpolateColor(color1, color2, factor) {\n    return {\n        r: Math.round(color1.r + (color2.r - color1.r) * factor),\n        g: Math.round(color1.g + (color2.g - color1.g) * factor),\n        b: Math.round(color1.b + (color2.b - color1.b) * factor),\n        a: 1\n    };\n}\n\nconst white = hexToRgb('#FFFFFF');  // white\nconst pink  = hexToRgb('#FFC0CB');  // pink\n\nconst leds = [];\n\nfor (let i = 0; i < 8; i++) {\n    const factor = i / 7; // smoothly go from white to pink\n    leds[i] = interpolateColor(white, pink, factor);\n}\n\nfor (let i = 8; i < 16; i++) {\n    const factor = (i - 8) / 7; // smoothly go from pink back to white\n    leds[i] = interpolateColor(pink, white, factor);\n}\n\nmsg.payload = leds;\nreturn msg;\n",
        "outputs": 1,
        "timeout": 0,
        "noerr": 0,
        "initialize": "",
        "finalize": "",
        "libs": [],
        "x": 2490,
        "y": 2000,
        "wires": [
            [
                "94e7a2fd4f6236db"
            ]
        ]
    },
    {
        "id": "94e7a2fd4f6236db",
        "type": "mqtt out",
        "z": "93bc9b581a312155",
        "name": "",
        "topic": "led",
        "qos": "",
        "retain": "",
        "respTopic": "",
        "contentType": "",
        "userProps": "",
        "correl": "",
        "expiry": "",
        "broker": "5058bca32a4f00c3",
        "x": 2650,
        "y": 2040,
        "wires": []
    },
    {
        "id": "acc1f9eee92b237f",
        "type": "rcon",
        "z": "93bc9b581a312155",
        "name": "",
        "server": "974b018728e661cc",
        "command": "",
        "x": 2670,
        "y": 2320,
        "wires": [
            []
        ]
    },
    {
        "id": "5f1c247318301db9",
        "type": "ui_button",
        "z": "93bc9b581a312155",
        "name": "",
        "group": "ab8d52c8070607ed",
        "order": 17,
        "width": 0,
        "height": 0,
        "passthru": false,
        "label": "Chicken",
        "tooltip": "",
        "color": "black",
        "bgcolor": "",
        "className": "chicken",
        "icon": "",
        "payload": "chicken",
        "payloadType": "str",
        "topic": "payload",
        "topicType": "msg",
        "x": 2260,
        "y": 2200,
        "wires": [
            [
                "3c9ec1efff2b8788",
                "d5abe642ebf6e2e8",
                "5cb0188b5dea4c53"
            ]
        ]
    },
    {
        "id": "3c9ec1efff2b8788",
        "type": "change",
        "z": "93bc9b581a312155",
        "name": "",
        "rules": [
            {
                "t": "set",
                "p": "payload",
                "pt": "msg",
                "to": "/execute at remked run summon chicken ~ ~ ~",
                "tot": "str"
            }
        ],
        "action": "",
        "property": "",
        "from": "",
        "to": "",
        "reg": false,
        "x": 2460,
        "y": 2280,
        "wires": [
            [
                "acc1f9eee92b237f"
            ]
        ]
    },
    {
        "id": "d5abe642ebf6e2e8",
        "type": "function",
        "z": "93bc9b581a312155",
        "name": "function 20",
        "func": "function hexToRgb(hexColor) {\n    const hex = hexColor.replace(/^#/, '');\n    const r = parseInt(hex.substring(0, 2), 16);\n    const g = parseInt(hex.substring(2, 4), 16);\n    const b = parseInt(hex.substring(4, 6), 16);\n\n    return { r, g, b, a: 1 };\n}\n\nfunction interpolateColor(color1, color2, factor) {\n    return {\n        r: Math.round(color1.r + (color2.r - color1.r) * factor),\n        g: Math.round(color1.g + (color2.g - color1.g) * factor),\n        b: Math.round(color1.b + (color2.b - color1.b) * factor),\n        a: 1\n    };\n}\n\nconst white = hexToRgb('#FFFFFF');  // white\nconst orange = hexToRgb('#FFA500'); // orange\n\nconst leds = [];\n\nfor (let i = 0; i < 8; i++) {\n    const factor = i / 7; // white to orange\n    leds[i] = interpolateColor(white, orange, factor);\n}\n\nfor (let i = 8; i < 16; i++) {\n    const factor = (i - 8) / 7; // orange back to white\n    leds[i] = interpolateColor(orange, white, factor);\n}\n\nmsg.payload = leds;\nreturn msg;\n",
        "outputs": 1,
        "timeout": 0,
        "noerr": 0,
        "initialize": "",
        "finalize": "",
        "libs": [],
        "x": 2510,
        "y": 2200,
        "wires": [
            [
                "9c1405614134e5f8"
            ]
        ]
    },
    {
        "id": "9c1405614134e5f8",
        "type": "mqtt out",
        "z": "93bc9b581a312155",
        "name": "",
        "topic": "led",
        "qos": "",
        "retain": "",
        "respTopic": "",
        "contentType": "",
        "userProps": "",
        "correl": "",
        "expiry": "",
        "broker": "5058bca32a4f00c3",
        "x": 2670,
        "y": 2240,
        "wires": []
    },
    {
        "id": "414830095fe057db",
        "type": "ui_text",
        "z": "93bc9b581a312155",
        "group": "ab8d52c8070607ed",
        "order": 18,
        "width": 0,
        "height": 0,
        "name": "",
        "label": "Extras",
        "format": "",
        "layout": "col-center",
        "className": "text",
        "style": true,
        "font": "Trebuchet MS,Helvetica,sans-serif",
        "fontSize": "30",
        "color": "#000000",
        "x": 550,
        "y": 1020,
        "wires": []
    },
    {
        "id": "2162707bb7d3ae3a",
        "type": "ui_button",
        "z": "93bc9b581a312155",
        "d": true,
        "name": "",
        "group": "ab8d52c8070607ed",
        "order": 19,
        "width": 0,
        "height": 0,
        "passthru": false,
        "label": "Kill nearest mob",
        "tooltip": "",
        "color": "white",
        "bgcolor": "",
        "className": "kill",
        "icon": "",
        "payload": "",
        "payloadType": "str",
        "topic": "payload",
        "topicType": "msg",
        "x": 400,
        "y": 1180,
        "wires": [
            [
                "9250b9942717656a",
                "9d70a5c2cd4bc88e"
            ]
        ]
    },
    {
        "id": "9250b9942717656a",
        "type": "change",
        "z": "93bc9b581a312155",
        "d": true,
        "name": "",
        "rules": [
            {
                "t": "set",
                "p": "payload",
                "pt": "msg",
                "to": "/kill @e[tag=hostile,sort=nearest,limit=1]",
                "tot": "str"
            }
        ],
        "action": "",
        "property": "",
        "from": "",
        "to": "",
        "reg": false,
        "x": 600,
        "y": 1280,
        "wires": [
            [
                "1213fd5366d71329"
            ]
        ]
    },
    {
        "id": "9d70a5c2cd4bc88e",
        "type": "function",
        "z": "93bc9b581a312155",
        "d": true,
        "name": "function 21",
        "func": "function hexToRgb(hexColor) {\n    const hex = hexColor.replace(/^#/, '');\n    const r = parseInt(hex.substring(0, 2), 16);\n    const g = parseInt(hex.substring(2, 4), 16);\n    const b = parseInt(hex.substring(4, 6), 16);\n\n    return {\n        r: r,\n        g: g,\n        b: b,\n        a: 1\n    };\n}\n\nconst white = hexToRgb('#FF0000');  // red!!!\n\nmsg.payload = Array(16).fill(white);\nreturn msg;\n",
        "outputs": 1,
        "timeout": 0,
        "noerr": 0,
        "initialize": "",
        "finalize": "",
        "libs": [],
        "x": 650,
        "y": 1180,
        "wires": [
            [
                "fea0236e6ec31832"
            ]
        ]
    },
    {
        "id": "fea0236e6ec31832",
        "type": "mqtt out",
        "z": "93bc9b581a312155",
        "d": true,
        "name": "",
        "topic": "led",
        "qos": "",
        "retain": "",
        "respTopic": "",
        "contentType": "",
        "userProps": "",
        "correl": "",
        "expiry": "",
        "broker": "5058bca32a4f00c3",
        "x": 810,
        "y": 1220,
        "wires": []
    },
    {
        "id": "1213fd5366d71329",
        "type": "rcon",
        "z": "93bc9b581a312155",
        "d": true,
        "name": "",
        "server": "974b018728e661cc",
        "command": "",
        "x": 810,
        "y": 1280,
        "wires": [
            [
                "c25ab8cea3db2e41"
            ]
        ]
    },
    {
        "id": "c25ab8cea3db2e41",
        "type": "debug",
        "z": "93bc9b581a312155",
        "d": true,
        "name": "debug 4",
        "active": true,
        "tosidebar": true,
        "console": false,
        "tostatus": false,
        "complete": "false",
        "statusVal": "",
        "statusType": "auto",
        "x": 780,
        "y": 1340,
        "wires": []
    },
    {
        "id": "73446cb08be22060",
        "type": "comment",
        "z": "93bc9b581a312155",
        "name": "",
        "info": "Doesn't work, doesn't detect mobs",
        "x": 540,
        "y": 1120,
        "wires": []
    },
    {
        "id": "e7c5afa9327e94b1",
        "type": "ui_button",
        "z": "93bc9b581a312155",
        "name": "",
        "group": "ab8d52c8070607ed",
        "order": 19,
        "width": 0,
        "height": 0,
        "passthru": false,
        "label": "Spawn Random Mob",
        "tooltip": "",
        "color": "white",
        "bgcolor": "",
        "className": "random",
        "icon": "",
        "payload": "",
        "payloadType": "str",
        "topic": "payload",
        "topicType": "msg",
        "x": 400,
        "y": 1540,
        "wires": [
            [
                "246500e26a620f35"
            ]
        ]
    },
    {
        "id": "246500e26a620f35",
        "type": "random",
        "z": "93bc9b581a312155",
        "name": "",
        "low": 1,
        "high": "12",
        "inte": "true",
        "property": "random",
        "x": 660,
        "y": 1560,
        "wires": [
            [
                "5f5272976bc1cb7a"
            ]
        ]
    },
    {
        "id": "5f5272976bc1cb7a",
        "type": "switch",
        "z": "93bc9b581a312155",
        "name": "",
        "property": "random",
        "propertyType": "msg",
        "rules": [
            {
                "t": "eq",
                "v": "1",
                "vt": "str"
            },
            {
                "t": "eq",
                "v": "2",
                "vt": "str"
            },
            {
                "t": "eq",
                "v": "3",
                "vt": "str"
            },
            {
                "t": "eq",
                "v": "4",
                "vt": "str"
            },
            {
                "t": "eq",
                "v": "5",
                "vt": "str"
            },
            {
                "t": "eq",
                "v": "6",
                "vt": "str"
            },
            {
                "t": "eq",
                "v": "7",
                "vt": "str"
            },
            {
                "t": "eq",
                "v": "8",
                "vt": "str"
            },
            {
                "t": "eq",
                "v": "9",
                "vt": "str"
            },
            {
                "t": "eq",
                "v": "10",
                "vt": "str"
            },
            {
                "t": "eq",
                "v": "11",
                "vt": "str"
            },
            {
                "t": "eq",
                "v": "12",
                "vt": "str"
            }
        ],
        "checkall": "true",
        "repair": false,
        "outputs": 12,
        "x": 870,
        "y": 1560,
        "wires": [
            [
                "d4a20b893906a160",
                "fa712774de43dc12"
            ],
            [
                "49fb5c7a55a4dfd4",
                "3332273acd08501e"
            ],
            [
                "12c80f51b33a7b4d",
                "72f94aaf02c71f6f"
            ],
            [
                "c4c94c39ec040cd5",
                "bfaf919a2c559d2b"
            ],
            [
                "7625f780cacd9446",
                "eda5332d69d52f83"
            ],
            [
                "131ad328e1e3651b",
                "875246e007418ea8"
            ],
            [
                "5748cfc52df35e99",
                "028c20fb4027fe34"
            ],
            [
                "c91af1bdcec8d0ca",
                "c6369a9445def82f"
            ],
            [
                "dee338ee44d7eca4",
                "2a4e041678de97a8"
            ],
            [
                "bbfcd24392046909",
                "14f2276cb5c3497a"
            ],
            [
                "be100e42f1b1bfa3",
                "a0425afb66de63aa"
            ],
            [
                "d5abe642ebf6e2e8",
                "3c9ec1efff2b8788"
            ]
        ]
    },
    {
        "id": "0fc3c2ce9a99d3f6",
        "type": "ui_button",
        "z": "93bc9b581a312155",
        "name": "",
        "group": "ab8d52c8070607ed",
        "order": 19,
        "width": 0,
        "height": 0,
        "passthru": false,
        "label": "BOOM",
        "tooltip": "",
        "color": "white",
        "bgcolor": "",
        "className": "boom",
        "icon": "",
        "payload": "",
        "payloadType": "str",
        "topic": "payload",
        "topicType": "msg",
        "x": 350,
        "y": 1800,
        "wires": [
            [
                "017afc886c017182",
                "0124360fc46f9575"
            ]
        ]
    },
    {
        "id": "a078a338ea07de65",
        "type": "rcon",
        "z": "93bc9b581a312155",
        "name": "",
        "server": "974b018728e661cc",
        "command": "",
        "x": 830,
        "y": 1880,
        "wires": [
            [
                "7f964870993fca44"
            ]
        ]
    },
    {
        "id": "0124360fc46f9575",
        "type": "change",
        "z": "93bc9b581a312155",
        "name": "",
        "rules": [
            {
                "t": "set",
                "p": "payload",
                "pt": "msg",
                "to": "/execute at remked run summon tnt ~ ~ ~",
                "tot": "str"
            }
        ],
        "action": "",
        "property": "",
        "from": "",
        "to": "",
        "reg": false,
        "x": 620,
        "y": 1840,
        "wires": [
            [
                "a078a338ea07de65"
            ]
        ]
    },
    {
        "id": "017afc886c017182",
        "type": "function",
        "z": "93bc9b581a312155",
        "name": "function 22",
        "func": "function hexToRgb(hexColor) {\n    const hex = hexColor.replace(/^#/, '');\n    const r = parseInt(hex.substring(0, 2), 16);\n    const g = parseInt(hex.substring(2, 4), 16);\n    const b = parseInt(hex.substring(4, 6), 16);\n\n    return { r, g, b, a: 1 };\n}\n\nconst red = hexToRgb('#FF0000');  // red\n\nconst leds = Array(16).fill(red);  // all LEDs will be red\n\nmsg.payload = leds;\nreturn msg;\n",
        "outputs": 1,
        "timeout": 0,
        "noerr": 0,
        "initialize": "",
        "finalize": "",
        "libs": [],
        "x": 670,
        "y": 1760,
        "wires": [
            [
                "3edcbad9a78a665d"
            ]
        ]
    },
    {
        "id": "3edcbad9a78a665d",
        "type": "mqtt out",
        "z": "93bc9b581a312155",
        "name": "",
        "topic": "led",
        "qos": "",
        "retain": "",
        "respTopic": "",
        "contentType": "",
        "userProps": "",
        "correl": "",
        "expiry": "",
        "broker": "5058bca32a4f00c3",
        "x": 830,
        "y": 1800,
        "wires": []
    },
    {
        "id": "078342cc3cb41a30",
        "type": "inject",
        "z": "93bc9b581a312155",
        "name": "",
        "props": [
            {
                "p": "payload"
            },
            {
                "p": "topic",
                "vt": "str"
            }
        ],
        "repeat": "1",
        "crontab": "",
        "once": true,
        "onceDelay": 0.1,
        "topic": "",
        "payload": "",
        "payloadType": "date",
        "x": 110,
        "y": 1280,
        "wires": [
            []
        ]
    },
    {
        "id": "03edb993bd731a85",
        "type": "comment",
        "z": "93bc9b581a312155",
        "name": "",
        "info": "Connect to anything to quickly test without having to press buttons",
        "x": 100,
        "y": 1220,
        "wires": []
    },
    {
        "id": "27738c73c2c4f481",
        "type": "ui_button",
        "z": "93bc9b581a312155",
        "name": "",
        "group": "ab8d52c8070607ed",
        "order": 19,
        "width": 0,
        "height": 0,
        "passthru": false,
        "label": "TP To Random Mob",
        "tooltip": "",
        "color": "white",
        "bgcolor": "",
        "className": "teleport",
        "icon": "",
        "payload": "",
        "payloadType": "str",
        "topic": "payload",
        "topicType": "msg",
        "x": 400,
        "y": 2020,
        "wires": [
            [
                "4b98d1d1d3c2183f",
                "03c216f7c413963f"
            ]
        ]
    },
    {
        "id": "32087847a56defab",
        "type": "rcon",
        "z": "93bc9b581a312155",
        "name": "",
        "server": "974b018728e661cc",
        "command": "",
        "x": 830,
        "y": 2100,
        "wires": [
            []
        ]
    },
    {
        "id": "03c216f7c413963f",
        "type": "change",
        "z": "93bc9b581a312155",
        "name": "",
        "rules": [
            {
                "t": "set",
                "p": "payload",
                "pt": "msg",
                "to": "/execute as remked at @s run tp @s @e[type=!player,limit=1,sort=random]",
                "tot": "str"
            }
        ],
        "action": "",
        "property": "",
        "from": "",
        "to": "",
        "reg": false,
        "x": 620,
        "y": 2060,
        "wires": [
            [
                "32087847a56defab"
            ]
        ]
    },
    {
        "id": "4b98d1d1d3c2183f",
        "type": "function",
        "z": "93bc9b581a312155",
        "name": "function 23",
        "func": "function hexToRgb(hexColor) {\n    const hex = hexColor.replace(/^#/, '');\n    const r = parseInt(hex.substring(0, 2), 16);\n    const g = parseInt(hex.substring(2, 4), 16);\n    const b = parseInt(hex.substring(4, 6), 16);\n\n    return { r, g, b, a: 1 };\n}\n\nconst red = hexToRgb('#FF0000');  // red\n\nconst leds = Array(16).fill(red);  // all LEDs will be red\n\nmsg.payload = leds;\nreturn msg;\n",
        "outputs": 1,
        "timeout": 0,
        "noerr": 0,
        "initialize": "",
        "finalize": "",
        "libs": [],
        "x": 670,
        "y": 1980,
        "wires": [
            [
                "bb042392083e5dd1"
            ]
        ]
    },
    {
        "id": "bb042392083e5dd1",
        "type": "mqtt out",
        "z": "93bc9b581a312155",
        "name": "",
        "topic": "led",
        "qos": "",
        "retain": "",
        "respTopic": "",
        "contentType": "",
        "userProps": "",
        "correl": "",
        "expiry": "",
        "broker": "5058bca32a4f00c3",
        "x": 830,
        "y": 2020,
        "wires": []
    },
    {
        "id": "7f964870993fca44",
        "type": "debug",
        "z": "93bc9b581a312155",
        "name": "debug 7",
        "active": true,
        "tosidebar": true,
        "console": false,
        "tostatus": false,
        "complete": "false",
        "statusVal": "",
        "statusType": "auto",
        "x": 960,
        "y": 1880,
        "wires": []
    },
    {
        "id": "bb2d1a7164c6a231",
        "type": "inject",
        "z": "93bc9b581a312155",
        "name": "",
        "props": [
            {
                "p": "payload"
            },
            {
                "p": "topic",
                "vt": "str"
            }
        ],
        "repeat": "0.05",
        "crontab": "",
        "once": true,
        "onceDelay": 0.1,
        "topic": "",
        "payload": "",
        "payloadType": "date",
        "x": 110,
        "y": 1420,
        "wires": [
            []
        ]
    },
    {
        "id": "8ddabc4631f4206f",
        "type": "comment",
        "z": "93bc9b581a312155",
        "name": "",
        "info": "Connect to anything to quickly spam",
        "x": 100,
        "y": 1380,
        "wires": []
    },
    {
        "id": "ab8d52c8070607ed",
        "type": "ui_group",
        "name": "",
        "tab": "6c444e83aa18f545",
        "order": 1,
        "disp": true,
        "width": 6,
        "collapse": false,
        "className": ""
    },
    {
        "id": "974b018728e661cc",
        "type": "serverconfig",
        "host": "tome.lu",
        "rconPort": 25575,
        "rconPassword": "teinf"
    },
    {
        "id": "5058bca32a4f00c3",
        "type": "mqtt-broker",
        "name": "",
        "broker": "tome.lu",
        "port": 1883,
        "clientid": "",
        "autoConnect": true,
        "usetls": false,
        "protocolVersion": 4,
        "keepalive": 60,
        "cleansession": true,
        "autoUnsubscribe": true,
        "birthTopic": "",
        "birthQos": "0",
        "birthRetain": "false",
        "birthPayload": "",
        "birthMsg": {},
        "closeTopic": "",
        "closeQos": "0",
        "closeRetain": "false",
        "closePayload": "",
        "closeMsg": {},
        "willTopic": "",
        "willQos": "0",
        "willRetain": "false",
        "willPayload": "",
        "willMsg": {},
        "userProps": "",
        "sessionExpiry": ""
    },
    {
        "id": "6c444e83aa18f545",
        "type": "ui_tab",
        "name": "McMobProject",
        "icon": "dashboard",
        "disabled": false,
        "hidden": false
    }
]
}

### 2. Set Up the MQTT Server
- In Node-RED, locate the MQTT nodes in the flow.
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

