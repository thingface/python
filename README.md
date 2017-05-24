# The thingface client library for python
simple client library as pip package for python

## Installation

```sh
pip install thingface-client
```

## Code Example

A few lines of code and you're ready to control or monitor your device.

```python
from thingface import Client

# define command handler if needed
def command_handler(sender_type, sender_id, command, args):
    print(sender_type, sender_id, command, args)

c = Client()
c.tls_set('ca.crt')  # certificate for ssl
c.connect('device_id', 'secret_key', 'host')  # connect to thingface gateway
c.on_command(commnad_handler)  #  command handler if defined
c.send_sensor_value('sensor_name', 36.5)
c.disconnect()
```

## API Reference
API is very simple. Have a look to api reference.

### Client()
thingface client constructor

### thingface.tls_set(certFilePath)
set certificate for mqtt connection to specified certFilePath.

### thingface.connect(deviceId, deviceSecretKey, host)
connect to the thingface device gateway specified by the given host name with current device ID and device secret key.
- `deviceId` - device ID
- `deviceSecretKey` - secret key for that device
- `host` - device gateway hostname

### thingface.disconnect()
disconnect from thingface device gateway

### thingface.is_connected()
check active connection state

### thingface.on_error(callback)
set event handler for error events

### thingface.on_connection_state(callback)
set event handler for connection_state events

### thingface.on_command(commandHandler, senderType, senderId)
set event handler of command events
subscribe for commands from sender
- `commandHandler` function to handle commands
- `senderType`(optional) - sender type User or Device
- `senderId` (optional) - sender ID (username or device ID), if sender is not provided device will receive commands from every user or device

### thingface.send_sensor_value(sensorId, sensorValue)
send sensor value to thingface gateway
- `sensorId` - sensor ID from the device
- `sensorValue` - current sensor value

## More Information
- [https://github.com/thingface](https://github.com/thingface)
- [http://thingface.io](http://thingface.io/)
