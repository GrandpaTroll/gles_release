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

#### gles.LoadFile(`luastate_realm`, `filename`, `spoofed_name = "lua/autorun/init.lua"`)

| Parameter | Type     | Description                |
| :-------- | :------- | :------------------------- |
| `luastate_realm` | `int` | the luastate realm type [**LUASTATE_**](#link_luastate_type) |
| `filename` | `string` | the lua file you want to load from gles/luas/... |
| `spoofed_name` | `string` | if set: set spoofed_name instead default |
| **return** | `none` | |

#### gles.LoadString(`luastate_realm`, `code`, `spoofed_name = "lua/autorun/init.lua"`)

| Parameter | Type     | Description                |
| :-------- | :------- | :------------------------- |
| `luastate_realm` | `int` | the luastate realm type [**LUASTATE_**](#link_luastate_type) |
| `code` | `string` | the lua code you want to run. |
| `spoofed_name` | `string` | if set: set spoofed_name instead default |
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

#### gles.GetNetVar(`entity`, `datatable_name`, `datatable_variable`, `datatable_type`)

| Parameter | Type     | Description                |
| :-------- | :------- | :------------------------- |
| `entity` | `Entity` | The entity you want to grab the netvar info from |
| `datatable_name` | `string` | the datatable name `i.e. DT_BasePlayer` |
| `datatable_variable` | `string` | the datatable variable from the `datatable_name` `i.e DT_BasePlayer->m_flSimulationTime` |
| `datatable_type` | `int` | the datatable type  [**DTVar_**](#link_dtvar_type) |
| **return** | `any` | returns value by the type `datatable_type` given |

#### gles.SetNetVar(`entity`, `datatable_name`, `datatable_variable`, `datatable_type`, `value`)

| Parameter | Type     | Description                |
| :-------- | :------- | :------------------------- |
| `entity` | `Entity` | The entity you want to grab the netvar info from |
| `datatable_name` | `string` | the datatable name `i.e. DT_BasePlayer` |
| `datatable_variable` | `string` | the datatable variable from the `datatable_name` `i.e DT_BasePlayer->m_flSimulationTime` |
| `datatable_type` | `int` | the datatable type  [**DTVar_**](#link_dtvar_type) |
| `value` | `any` | the value to set the netvar (must match the type)  [**DTVar_**](#link_dtvar_type) |
| **return** | `none` |  |


#### gles.GetConVar(`convar_name`)

| Parameter | Type     | Description                |
| :-------- | :------- | :------------------------- |
| `convar_name` | `string` | the convar you want to find |
| **return** | `ConVar` | returns a convar; nil if not found. |

#### gles.SetConVar(`convar_name`, `convar_value`)

| Parameter | Type     | Description                |
| :-------- | :------- | :------------------------- |
| `convar_name` | `string` | the convar you want to change the value |
| `convar_name` | `string`, `float`, `int`, `bool` | the value for the convar |
| **return** | `none` |  |

#### gles.WorldToScreen(`vector_pos`)

| Parameter | Type     | Description                |
| :-------- | :------- | :------------------------- |
| `vector_pos` | `Vector` | The 3d position to be converted into 2d screen pos. |
| **return** | `vec screen_pos`, `bool in_view` | A vector where x and y are screen coordinates and a bool if in view |

#### gles.SetContextAim(`ucmd`, `aim_dir`)

| Parameter | Type     | Description                |
| :-------- | :------- | :------------------------- |
| `ucmd` | `CUserCmd` | the userCmd object |
| `aim_dir` | `Vector` | the direction to set the context aim |
| **return** | `none` | Sets the context aim direction |

#### gles.UpdatePrediction()

| Parameter | Type     | Description                |
| :-------- | :------- | :------------------------- |
| **return** | `none` | Call to update engine variables. |


## Cheat hooks

#### gles.AddCallback(`lua_state_realm`, `hook_name`, `lua_func`)

| Parameter | Type     | Description                |
| :-------- | :------- | :------------------------- |
| `lua_state_realm` | `int` | the luastate realm type [**LUASTATE_**](#link_luastate_type) |
| `hook_name` | `string` | the identifier to tie your lua function to a specific hook |
| `lua_func` | `lua_function` | the in game lua function |
| **return** | `none` | |

#### gles.RemoveCallback(`lua_state_realm`, `hook_name`)

| Parameter | Type     | Description                |
| :-------- | :------- | :------------------------- |
| `lua_state_realm` | `int` | the luastate realm type [**LUASTATE_**](#link_luastate_type) |
| `hook_name` | `string` | the specific hook you want to disable of being called. |
| **return** | `none` | |

#### gles.RemoveCallbacks(`lua_state_realm`)

| Parameter | Type     | Description                |
| :-------- | :------- | :------------------------- |
| `lua_state_realm` | `int` | the luastate realm type [**LUASTATE_**](#link_luastate_type) |
| **return** | `none` | Removes all the hooks connected to that [**lua realm**](#link_luastate_type) |


 more to come...

## Hooks

These are our custom hooks

If you return a variable inside the hooks, it will not be called in the other realms.
(i.e. return on client realm = no call on server or menu.)

the priority follows client->server->menu.

| Hook Name | Description     | arguements                | returns |
| :-------- | :------- | :------------------------- |  :------------------------- |
| "OnClientLuaLoaded" | Called when the client realm is loaded before addon autorun | `none` | `none` |
| "RunOnClient" | Called when the client lua is about to be loaded | `filename`, `code` | `bool steal_file`, `bool dont_run` |
| "OnDisconnect" | Called when the disconnecting from the server | `disconnect_reason` | `str new_reason` |
| "DrawVisuals" | Called when the render is ready for visual drawing | `none` | `none` |
| "OnEntityCreated" | Called when an entity is created. | `entity` | `none` |
| "OnEntityRemoved" | Called when an entity is about to be removed | `entity` | `none` |
| "PreCreateMove" | Called before CreateMove hook | `usercmd` | `bool silent_aim` |
| "PostCreateMove" | Called after CraeteMove hook | `usercmd` | `bool silent_aim` |
| "PreFrameStageNotify" | Called before FrameStageNotify hook | [`framestage_id`](#link_framestage_type) | `none` |
| "PostFrameStageNotify" | Called after FrameStageNotify hook | [`framestage_id`](#link_framestage_type) | `none` |
| "OverrideView" | Edit your view settings | `view_settings {origin, angles, fov}` | `tbl view_settings` |
| "EntityFireBullets" | when a bullet is fired from an entity. | `bullet_data {attacker, src, dir, spread}` | `tbl bullet_data` |

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


<a name="link_dtvar_type"> </a>
#### DTVar__ types

```
DTVar_Int = 0
DTVar_Float = 1
DTVar_Vector = 2
DTVar_Double = 3
DTVar_String = 4
DTVar_Array = 5
DTVar_DataTable = 6
DTVar_Int64 = 7
```

<a name="link_framestage_type"> </a>
#### FRAMESTAGE_ types

```
FRAMESTAGE_UNDEFINED = -1,
FRAMESTAGE_START = 0
FRAMESTAGE_NET_UPDATE_START = 1
FRAMESTAGE_NET_UPDATE_POSTDATAUPDATE_START = 2
FRAMESTAGE_NET_UPDATE_POSTDATAUPDATE_END = 3
FRAMESTAGE_NET_UPDATE_END = 4
FRAMESTAGE_RENDER_START = 5
FRAMESTAGE_RENDER_END = 6
```
