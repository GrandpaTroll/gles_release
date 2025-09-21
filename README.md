
# Gmod Lua Executor Support

A injectable DLL that imports engine functionality to the lua realms.

When running your scripts make sure to create a local `local gles(or whatever you want) = _G._gles` to keep the functions while preventing anticheats from picking it up.


## API Reference

#### gles.GetLatency(`flow_type`)

| Parameter | Type     | Description                |
| :-------- | :------- | :------------------------- |
| `flow_type` | `integer` | the flow type [**FLOW_**](#link_flow_type) |
| **return** | `float` | Returns decimal of your current latency. (50 ping = 0.05) |

#### gles.TimeToTicks(`time`)

| Parameter | Type     | Description                |
| :-------- | :------- | :------------------------- |
| `time` | `float` | the float number to convert into game ticks amount. |
| **return** | `int` | Returns integer of ticks from the time |

#### gles.TicksToTime(`tick`)

| Parameter | Type     | Description                |
| :-------- | :------- | :------------------------- |
| `tick` | `int` | the integer number to convert into float amount. |
| **return** | `float` | Returns float of time from game ticks. |


#### gles.RoundToTicks(`time`)

| Parameter | Type     | Description                |
| :-------- | :------- | :------------------------- |
| `time` | `float` | the float number to round into the nearest tick. |
| **return** | `int` | Returns float of closet tick from time. |

#### gles.ForceFullUpdate()

| Parameter | Type     | Description                |
| :-------- | :------- | :------------------------- |
| **return** | `none` | Request a full update from the server (fixes visual bugs) |

 more to come...
## Global Variables

These global variables will be available and can be accessed via gles.[global var]

*They're in a table to prevent anticheats from seeing the globals and use them as a detection vector.*

<a name="link_flow_type"> </a>
#### FLOW_ types

```
FLOW_OUTGOING = 0
FLOW_INCOMING = 1
```

