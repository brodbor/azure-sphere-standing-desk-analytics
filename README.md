# azure-sphere-standing-desk-analytics
This code performs analysis of distance based on the proximity of the user and sends telemetry to Azure IoT Hub. Stream Analytics used to aggregate and cleanse telemetry data before forwarding it to multiple outputs.

## Hardware/Software Used
1. Seeed [MT3620](https://www.seeedstudio.com/Azure-Sphere-MT3620-Development-Kit-US-Version-p-3052.html) Azure Sphere Board
2. 2 X Sonar Sensor-[LV-MaxSonar-EZ1 Ultrasonic Range Finder](https://www.amazon.com/Maxbotix-MB1010-LV-MaxSonar-EZ1-Ultrasonic-Finder/dp/B00A7YGVJI)
3. Visual Studio Code with number of extensions. Please check this [guide](https://docs.microsoft.com/en-us/azure/iot-hub/iot-hub-arduino-iot-devkit-az3166-get-started) for additional details


##  Wiring Diagram
![](https://borisbrodsky.com/wp-content/uploads/2021/01/mt3620_desk.png)

## Project Config
Add configuration to azure-sphere-standing-desk-analytics\hl_Azure_Sphere_IoT\app_manifest.json
 - [authenticate using device provisioning service](https://docs.microsoft.com/en-us/azure-sphere/app-development/setup-iot-hub#authenticate-using-the-device-provisioning-service)

```{
  "SchemaVersion": 1,
  "Name": "hl_Azure_Sphere_IoT",
  "ComponentId": "ed4e667a-ce81-448b-aa64-85d28083559e",
  "EntryPoint": "/bin/app",
  "CmdArgs": [ "--HostName", "<IOT HUB HOST>", "--ScopeID", "<scope id>" ],
  "Capabilities": {
    "AllowedConnections": [ "global.azure-devices-provisioning.net", "<IOT HUB HOST>"],
    "AllowedApplicationConnections": [ "e4c61359-a32e-4206-8127-2c5735b887e6" ],
    "DeviceAuthentication": "221d2bf5-23b6-43d6-9ce0-9fb314a9af0d"
  },
  "ApplicationType": "Default",
  "WifiConfig": true
}```
