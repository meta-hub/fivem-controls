# fivem-controls
Simple control module for FiveM, mostly used for returning the control label name.

## Installation
Clone the git into your fxservers `resources` folder.
Add `start fivem-controls` to your server.cfg.

## Usage
To use the controls module in another script, add the following to the scripts fxmanifest.lua/__resource.lua:

```lua
dependency 'fivem-controls'
client_script '@fivem-controls/controls.lua'
```

Example usage is as follows:
```lua
local resource = GetCurrentResourceName()
local control_index = 38
local control = Controls.GetControl(control_index)
local interact_label = string.format("~%s~ - Interact",control.name)
local label_name = string.format("%s_INTERACT",resource:upper())
AddTextEntry(label_name,interact_label)

while true do
  BeginTextCommandDisplayHelp(label_name)
  EndTextCommandDisplayHelp(0,false,true,-1)
  if Controls.JustPressed(control_index,0) then
    -- do stuff
  end
  Wait(0)
end
```