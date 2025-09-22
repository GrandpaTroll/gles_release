
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

#### gles.GetServerTick()

| Parameter | Type     | Description                |
| :-------- | :------- | :------------------------- |
| **return** | `int` | Returns the tickcount from the server |

#### gles.GetClientTick()

| Parameter | Type     | Description                |
| :-------- | :------- | :------------------------- |
| **return** | `int` | Returns the tickcount predicted from the client |

#### gles.GetChokedPackets()

| Parameter | Type     | Description                |
| :-------- | :------- | :------------------------- |
| **return** | `int` | Returns the current amount of choked packets |

#### gles.GetOutSeqNum()

| Parameter | Type     | Description                |
| :-------- | :------- | :------------------------- |
| **return** | `int` | Returns the current out sequence number |

#### gles.SetOutSeqNum(`seq_num`)

| Parameter | Type     | Description                |
| :-------- | :------- | :------------------------- |
| `seq_num` | `int` | the integer number to set the out sequence number to |
| **return** | `none` | |

#### gles.LoadFile(`luastate_realm`, `filename`, `spoofed_name = filename`)

| Parameter | Type     | Description                |
| :-------- | :------- | :------------------------- |
| `luastate_realm` | `int` | the luastate realm type [**LUASTATE_**](#link_luastate_type) |
| `filename` | `string` | the lua file you want to load from gles/luas/... |
| `spoofed_name` | `string` | if set: will use the spoofed_name instead of the real file name for debug information |
| **return** | `none` | |

#### gles.SetCmdNum(`ucmd`, `number`)

| Parameter | Type     | Description                |
| :-------- | :------- | :------------------------- |
| `ucmd` | `CUserCmd` | the userCmd object |
| `number` | `int` | the integer number you want to set your command number to. |
| **return** | `none` | |

#### gles.SetTickCount(`ucmd`, `number`)

| Parameter | Type     | Description                |
| :-------- | :------- | :------------------------- |
| `ucmd` | `CUserCmd` | the userCmd object |
| `number` | `int` | the integer number you want to set your tickcount to. |
| **return** | `none` | |

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

<a name="link_luastate_type"> </a>
#### LUASTATE_ types

```
LUASTATE_CLIENT = 0
LUASTATE_SERVER = 1
LUASTATE_MENU = 2
```
