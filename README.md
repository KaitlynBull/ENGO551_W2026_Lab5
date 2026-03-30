# ENGO551_W2026_Lab5
Repository Created for ENGO 551 - Lab 5 - IoT Geoweb APP 

## Project Description 
This project is a single page web application that uses a browser's native Geolocation API to capture the users real-time coordinates, simulates a random temperature reading (between -40 and 60 degreese celcius), and publishes the data as a GeoJSON payload to a public MQTT broker (`test.mosquitto.org`) using WebSockets. 

The app also features an interactive web map built with Leaflet.js that acts as a MQTT subscriber to its own topic. Using this connection the map dynamically plots and updates whenever a new message is recieved. The map markers are color coded based on the random temperature payload assigned (Blue: -40-10, Green: 10-30, and Red: 30-60). 

## Repository Contents
* index.html: The entire application is contained within this single file which is connected to GitHub pages to host it on any device. 
* README.md: Project documentation and testing instructions.

## Additional Information for Staff / TAs

**MQTT Topic Structure**
The application publishes and subscribes to the following topic:
`ENGO_551/Kaitlyn_Bull/my_temperature`

**Secure WebSockets (WSS)**
Because this application is hosted on GitHub Pages (which enforces HTTPS), the connection to `test.mosquitto.org` has been intentionally set to use **Port 8081** with SSL enabled (`useSSL: true`). This prevents the browser from blocking the connection and ensures that the Geolocation API functions correctly on mobile devices.

**How to Test**
1. Open the live GitHub Pages link on a smartphone or desktop browser (https://kaitlynbull.github.io/ENGO551_W2026_Lab5/).
2. Connect to the broker using the default settings (Port 8081).
3. Connect a desktop client like MQTTX to `test.mosquitto.org` on standard TCP Port `1883` and subscribe to `ENGO_551/Kaitlyn_Bull/my_temperature`.
4. Click **"Share My Status"** in the web app to see the GeoJSON arrive in MQTTX and the map update locally.
5. Alternatively, publish a formatted GeoJSON string directly from MQTTX to watch the web map update remotely.
