# RFID Node

## Sample Packet

The following packet is defined to allow all network devies to provide RFID node scan data and state information.

### Discussion of RFID Node

The unique element in the packet is the parametername "state". State data elements are expected to have a numeric value, or "v", of 1.

### Full Example of RFID Node

[RFID Node JSON Example File](https://github.com/RadioBro/ICD/blob/master/examples/rfidnode/rfidnodeexample.json)

```json
{
  "h":{
    "n":"RFID0000",
    "t":"2019-11-01T13:33:23.003Z"
  },
  "d":[
    {
      "n":"state",
      "v": 1
    },
    {
      "n":"rfidraw",
      "h": ""
    },
    {
      "n":"rfidgps",
      "j":{
        "device":"RFID0000",
        "epc":"",
        "sn":"",
        "type":"gps",
        "t":"2019-11-01T13:33:23.003Z",
        "lat": 30.00,
        "lng": -90.00,
        "alt": 10,
        "gae": -27.2556
      }
    }
  ]
}
```
