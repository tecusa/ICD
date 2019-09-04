# State

## Sample Packet

The following packet is defined to allow all network devies to provide state information.

### Discussion State

The unique element in the packet is the parametername "state". State data elements are expected to have a numeric value, or "v", of 1.

### Full Example of State

[State JSON Example File](https://github.com/RadioBro/ICD/blob/master/examples/state/stateexample.json)

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
    }
  ]
}
```
