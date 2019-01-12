# InfectedHordesPlus
A complete server side horde script for DayZ Standalone.

Check Change Log: [Here](https://github.com/VanillaPlusPlus/InfectedHordesPlus/releases)

## Installation:
- Before you add this mod, you must make sure that you had a profile set for your server, if not than you will not be able to configure the mod, and the mod will not launch correctly.
- If you don't already have them added then add the following to your start up command while changing "ProfileName" to whatever you wish to name the profile folder:
```
-profiles=ProfileName
```

- Download the projects zip file. [Here](https://github.com/VanillaPlusPlus/InfectedHordes/archive/master.zip)
- Uncompress the Zip folder, and move the InfectedHordesPlus folder into the same location where init.c is located.

**Example location:** ```/mpmission/dayzOffline.chernarusplus/```

**Note: If you are using any other mission name other than** ```dayzOffline.chernarusplus```**, you will have to change the includes inside of InfectedHordesPlusSpawner.c to match the name of your mission**

- At the top of your init.c file append the following:

```c
#include "$CurrentDir:\\mpmissions\\dayzOffline.chernarusplus\\InfectedHordesPlus\\InfectedHordesPlusSpawner.c"
```

- Inside of your init.c you need to find your MissionServer class.

**By default, it displayed as:** ```class CustomMission : MissionServer```

- Inside of your CustomMission class append the following:
```
	ref InfectedHordesPlusSpawner infectedHordes;
	void CustomMission(){
		infectedHordes = new InfectedHordesPlusSpawner();
	}

	override void OnUpdate(float timeslice){
		super.OnUpdate(timeslice);

		infectedHordes.onUpdate(timeslice);
	}
```

**Note: If you already have override void OnUpdate, and void CustomMission written you can add the following code in the following locations:**

- Above void CustomMission()
```
ref InfectedHordesPlusSpawner infectedHordes;
```

- Inside of void CustomMission()
```
infectedHordes = new InfectedHordesPlusSpawner();
```

- Inside of void OnUpdate(float timeslice)
```
infectedHordes.onUpdate(timeslice);
```

## Configuration:
- Inside of your profile folder, which should be in the same folder that you set in the installation process with -profiles, open ```InfectedHordesPlus.json``` and changes it's values. Have fun.


**Note: If you set lifetime to 0 inside of the json file, hordes will not despawn with a time; however, they will be removed as a valid "horde" when all horde members are killed off, dead bodies are despawned with normal despawn timer. This allows hordes to stick around to get to know the players. ;D**
