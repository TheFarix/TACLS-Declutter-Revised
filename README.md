#TAC Life Support Declutter Revised

Somnambulist had previously released a [declutter script](http://forum.kerbalspaceprogram.com/threads/40667?p=1519118) that reduces the number of parts from 30 to 2. However, it uses TweekScale, which I dislike and consider cheaty. After some time, I developed my own version that reduced it down to 6 parts.

##Requirements

* [TAC Life Support](http://forum.kerbalspaceprogram.com/threads/40667)
* [ModuleManager](http://forum.kerbalspaceprogram.com/threads/55219)
* [Firespitter](http://forum.kerbalspaceprogram.com/threads/24551) (DLL only)

##Enhancements from Somnambulist's Declutter

* Waste containers now start empty.
* Cost of containers adjust based on the type of container.
* The amount of resources in each container match the original containers.

##Known issues

Just like Somnambulist's script, this script creates a new part that can be configured. The original TAC Life Support parts will continue to function on existing craft, but will no longer be available in the VAB or SPH. However, any craft built after the script is installed will break if you uninstall the script.

##FAQ

###I use [Interstellar Fuel Switch](http://forum.kerbalspaceprogram.com/threads/117932). Can I use that instead of FireSpitter?

Yes, simply replace all instances of _Firespitter_ and _FSfuelSwitch_ with _InterstellarFuelSwitch_ and all instances of _FStextureSwitch2_ with _InterstellarTextureSwitch2_. I was originally going to use Interstellar Fuel Switch, but since I already had another mod installed that used Firespitter, I didn't want the duplication.

###I like TweekScale. Can I still use this script?

Of course. If TweekScale is installed, the small and large containers are automatically disabled. Then you simply need to create _TACLS Declutter TweakScale.cfg_ and add this code.

```
@PART[ConfigurableHexCanTACLifeSupport]:NEEDS[TweakScale]
{
	@description = A configurable resource canister containing Life Support supplies.

	@MODULE[FSfuelSwitch]
	{
		@tankCost = 0;0;0;0;0
	}

	MODULE
	{
		name = TweakScale
		type = surface
		freeScale = false
		defaultScale = 1.0
		scaleFactors = 0.5, 1.0, 2.0, 4.0
		scaleNames = 50%, 100%, 200%, 400%
		techRequired = survivability, survivability, heavyRocketry, experimentalRocketry
	}
}

@PART[ConfigurableTacLifeSupportContainer]:NEEDS[TweakScale]
{
	@description = A configurable container full of Life Support supplies.
	
	@MODULE[FSfuelSwitch]
	{
		@tankCost = 0;0;0;0;0
	}

	MODULE
	{
		name = TweakScale
		type = stack
		freeScale = false
		defaultScale = 1.0
		scaleFactors = 0.5, 1.0, 2.0, 4.0
		scaleNames = 50%, 100%, 200%, 400%
		techRequired = survivability, survivability, heavyRocketry, experimentalRocketry
	}
}
```

###Can I replace Somnambulist's script with this one?

Not without breaking your existing ships. That is because I used different part names than he did.

###I have a retexture pack for TAC Life Support. Will this script support it?

Unless the retexture pack copies over the original texture files, no. Because of the many different ways in which a retextures pack can be added, it is practically impossible to support them. Therefore, I will leave that up to the texture pack developer or the end user to figure out.

###I have a problem…

I have no intentions of supporting this script beyond its initial release. That is because I created this primarily for my own personal use and simply want to share it with others who may find it useful. If you have a problem, you are pretty much on your own. But if you have a fix, please post it and I may incorporate it—if my interests haven't wondered to something else entirely.

##Credits and Acknowledgements


* Somnambulist – for the original declutter script
* TaranisElsu – create/developer of TAC Life Support
* Ialdabaoth, sarbian – developers of ModuleManager plugin
* Snjo, Roverdude – developers of Firespitter
