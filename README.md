# ESX-GetSharedObject
Fix Old ESX to New ESX
# ADD THIS IN CLIENT AND SERVER - ESX = exports["es_extended"]:getSharedObject()
shared_scripts {'@es_extended/imports.lua'}


# REMOVE 
# ESX = nil
# TriggerEvent('esx:getSharedObject', function(obj) ESX = obj end)



**ESX = nil

Citizen.CreateThread(function()
	while ESX == nil do
		TriggerEvent('esx:getSharedObject', function(obj) ESX = obj end)
		Citizen.Wait(0)
	end
end)**
