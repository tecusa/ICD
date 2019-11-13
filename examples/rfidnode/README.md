# RFID Node

The RFID node will send raw scan data, GPS located scan data, or updates of asset positions based on it's own awareness of previous GPS asset data.

## Sample Data Packet

The following packet is defined to allow all network devies to provide RFID node scan data and state information.

### Discussion of RFID Node

The unique element in the packet is the parametername "state". State data elements are expected to have a numeric value, or "v", of 1.

### Raw Data Example of RFID Node

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
      "t":"2019-11-01T13:33:21.000Z",
      "h": "",
      "j":{
        "device":"RFID0000"
      }
    },
    {
      "n":"rfidraw",
      "t":"2019-11-01T13:33:22.000Z",
      "h": "",
      "j":{
        "device":"RFID0000"
      }
    },
    {
      "n":"rfidraw",
      "t":"2019-11-01T13:33:23.000Z",
      "h": "",
      "j":{
        "device":"RFID0000"
      }
    }
  ]
}
```

### Scan and GPS Data Example of RFID Node

```json
{
  "h":{
    "n":"RFID0000",
    "t":"2019-11-01T13:33:23.003Z"
  },
  "d":[
    {
      "n":"rfidscan",
      "h": "",
      "t":"2019-11-01T13:33:22.000Z",
      "j":{
        "device":"RFID0000",
        "epc":"",
        "sn":"",
        "rssi": 10,
      }
    },
    {
      "n":"rfidgps",
      "t":"2019-11-01T13:33:21.000Z",
      "j":{
        "device":"RFID0000",
        "epc":"",
        "sn":"",
        "lat": 30.00,
        "lng": -90.00,
        "alt": 10,
        "hae": -27.2556,
        "radius": 1,
        "direction": 20
      }
    }
  ]
}
```

### rfidraw Details

h is the hex response of the rfid capture

### rfidscan Details

j.device is the device name that performs the scan.

j.epc is the Electronic Product Code™ stored in the tag that was scanned.

j.sn is the serial number stored in the tag that was scanned.

j.rssi is the receive signal strength indicator in dBm.

### rfidgps Details

j.lat is always North up to 90. Use negative number to go South.

j.lng is always East, up to 180. Use negativ number to go West.

j.alt is altitude in meters above sea level (optional)

j.hae is height above ellipsoide in meters, measuring meters above sea level. The example is negative, demonstrating the sea level is over actual ellipsoid by 27 meters. (optional)

j.radius is the radius of GPS accuracy in meters (optional)

j.direction is degrees from North

## Asset List Updates - Command

```json
{
    h:{
        n:"RFID0000",
        t:"2014-03-14T16:00:00.000Z"
    },
    c:[
        {
        "n":"rfidgps",
        "t":"2019-11-01T13:33:21.000Z",
        "j":{
          "epc":"",
          "sn":"",
          "lat": 30.00,
          "lng": -90.00,
          "alt": 10,
          "hae": -27.2556,
          "radius": 1,
          "direction": 20
        }
      }
    ]
}
```
