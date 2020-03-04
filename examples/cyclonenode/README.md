# Cyclone Node

## Sample Packet

The following packet is defined to allow Cyclone Nodes to be the network gateway for Cyclone Sensors.

Cyclone Node supports state data, as defined [here](https://github.com/RadioBro/ICD/tree/master/examples/state).

### Cyclone Binary 2

The Cyclone Node will submit data in a binary format, often Cyclone Binary 2. This data can be received in the data 'h' for hex. [Example Packet](cyclonenodebinary2example.json)

### Discussion CS

The unique element in the packet is the parametername "cs". CS data elements are expected to have a JSON, or "j", payload with the following data:

* JSON payload
  + n the sensor name, required, factory set variable
  + p the parameter name, required
  + v the numeric value for the parameter, optional
  + a the ascii value for the parameter, optional
  + h the hex value for the parameter, optional
  + j the JSON value for the parameter, optional

### Short Example of CS

```json
{
  "h":{
    "n":"CN0000",
    "t":"2019-09-04T13:33:23.003Z"
  },
  "d":[
    {
      "n":"cs",
      "j":{
          "n":"CS0000",
          "p":"Val1",
          "v": 1.34
      }
    }
  ]
}
```

### Full Example

[Cyclone Node Example JSON](cyclonenodeexample.json)

```json
{
  "h":{
    "n":"CN0000",
    "t":"2019-09-04T13:33:23.003Z"
  },
  "d":[
    {
      "n":"state",
      "v": 1
    },
    {
      "n":"cs",
      "j":{
          "n":"CS0000",
          "p":"Val1",
          "v": 1.34
      }
    },
    {
      "n":"cs",
      "j":{
        "n":"CS0000",
        "p":"Temp1",
        "v": 24.1
      }
    },
    {
      "n":"cs",
      "j":{
        "n":"CS0001",
        "p":"Val1",
        "v": 1.25
      }
    },
    {
      "n":"cs",
      "j":{
        "n":"CS0001",
        "p":"Temp1",
        "v": 23.2
      }
    }
  ]
}
```
