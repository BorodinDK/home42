# Home42
### Deployment
```bash
git clone https://github.com/BorodinDK/home42
cd home42
sudo docker-compose up -d
```
### Configuration
#### Connect to CC2531
1. Identify your device
```bash
ls -l /dev/serial/by-id
```
2. Edit file `/home42/data/zigbee2mqtt/configuration.yaml`
```bash
serial:
  # Location of CC2531 USB sniffer
  port: port: /dev/ttyUSB0
```
3. Restart containers
```bash
sudo docker-compose restart
```
#### Add new devices
1. Set property `friendly_name` in file `/home42/data/zigbee2mqtt/configuration.yaml`

```yaml
devices:
  '0x54ef4410001d184a':
    friendly_name: p1
```
2. And restart containers
```bash
sudo docker-compose restart
```

## Interfaces
Use `localhost` or device ip address

* Node-red: `http://localhost:1880/`
* MQTT server: `mqtt://localhost:1883/`