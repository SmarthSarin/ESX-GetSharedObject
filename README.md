
---

# 🔧 ESX - `getSharedObject` Fix (Old ESX ➡️ New ESX)

If you're migrating from **old ESX** to the **new `es_extended` export system**, follow these steps to fix compatibility issues.

---

## ✅ Updated Code for Client and Server

Replace your old initialization method with the new export-based one.

### ✅ Add this (Client & Server):

```lua
-- New ESX export method (client & server)
ESX = exports["es_extended"]:getSharedObject()
```

### ✅ Also add to your `fxmanifest.lua`:

```lua
shared_scripts {
    '@es_extended/imports.lua'
}
```

---

## ❌ Remove Old Code

Delete or comment out any of the following **old-style ESX initialization**:

```lua
-- ❌ Old method to remove
ESX = nil

Citizen.CreateThread(function()
    while ESX == nil do
        TriggerEvent('esx:getSharedObject', function(obj)
            ESX = obj
        end)
        Citizen.Wait(0)
    end
end)
```

Or simply:

```lua
-- ❌ Also remove this (if used alone)
TriggerEvent('esx:getSharedObject', function(obj) ESX = obj end)
```

---

## ✅ Summary

| Task                                                      | Status |
| --------------------------------------------------------- | ------ |
| Use `exports["es_extended"]:getSharedObject()`            | ✅      |
| Add `@es_extended/imports.lua` in `shared_scripts`        | ✅      |
| Remove old `TriggerEvent` or `Citizen.CreateThread` usage | ❌      |

---
