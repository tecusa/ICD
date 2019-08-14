# JSON Open Data Format

There is a need to use JSON data format between devices.

## Data and Commands

JSON is used for two primary tasks: to send data and send commands. The JSON format offers a standard convention for the JSON format that supports the sender, receiver, routers, proxies, and archives.

Between many devices, the JSON data format is a reasonable standard format. To facilitate common software, an open standard is used.

## Basic Frame
```
{
    h:{
        n:"devicename",
        t:"2014-03-14T16:00:00.000Z"
    },
    d:[]
}
```
or
```
{
    h:{
        n:"devicename",
        t:"2014-03-14T16:00:00.000Z"
    },
    c:[]
}
```

The object must have an 'h' item, which is the header.

The header includes 'n', the unique network device name. This is an alphanumeric unique name for the device, no spaces.

The header includes 't', the ISO timestamp of when the packet is sent by the source machine.

If desired, the header can include 't_exp', the ISO timestamp of when to expire the packet.

The object contains data or commands within a 'd' or 'c' item, respectively. These are arrays of objects.

### Data Object
```
{
    h:{
        n:"devicename",
        t:"2014-03-14T16:00:00.000Z"
    },
    d:[
        {
            n:"voltage",
            v:4.99
        },
        {
            n:"error",
            a:"Low Voltage"
        }
    ]
}
```

Each data object takes a similar format.

The object includes 'n', the unique parameter name. This is an alphanumeric unique name for the parameter from this device. The parser will use this for routing and algorithm selection.

The object value can be stored in four formats. 

'v' is a numeric value. 'a' is an ascii value. 'h' is a hex value. 'j' is a JSON object.

The object can include a custom timestamp 't', the ISO timestamp of when the data is generated. This is often used when the data is stored, then transmitted later.

If desired, the object can include 'tsn', the nanoseconds of the timestamp. This is used in high-accuracy time scenarios.

### Command Object
```
{
    h:{
        n:"devicename",
        t:"2014-03-14T16:00:00.000Z"
    },
    c:[
        {
            n:"setupdate",
            v:10,
            t:"2014-03-14T16:30:00.000Z",
            t_exp:"2014-03-14T17:00:00.000Z"
        },
        {
            n:"setcameraserver",
            a:"192.168.0.1",
            t:"2014-03-14T16:30:00.000Z",
            t_exp:"2014-03-14T17:00:00.000Z"
         }
    ]
}
```

Each command object takes a similar format.

The object includes 'n', the unique command name. This is an alphanumeric unique name for the command to the end device.

The object value can be stored in four formats. 

'v' is a numeric value. 'a' is an ascii value. 'h' is a hex value. 'j' is a JSON object.

The object can include a custom timestamp 't', the ISO timestamp of when the command can be acted on. This is often used when the command is transmitted ahead of the activity window.

The object should include 't_exp', the ISO timestamp of when to expire the packet.

## Directionality

There is a clear directionality for the packets. Data is sent from a device to a pre-determined router. Commands are sent to the target device by a pre-determined router.

## Routing and Security

In setup, each device is issued routing paths and credentials. These can use a variety of messaging transports including GET, Socket-IO, and MQTT. The transporter is responsible for creating a secure tunnel to pass messages. The payload can also be secured within the JSON by the applications using the messages.

## OSI Model

The JSON format is used at Layer 6 of the OSI model, the Presentation Layer.

