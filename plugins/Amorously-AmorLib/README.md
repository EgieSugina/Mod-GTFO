# AmorLib
Adds an API for plugin developers to modify lights without conflicting with other mods. Decouples StateReplicators from FloLib and SyncedEvents from [EEC](https://thunderstore.io/c/gtfo/p/hirnukuono/EEC_H/) for convenient host-client syncing. With safe dependency wrappers for [InjectLib](https://thunderstore.io/c/gtfo/p/GTFOModding/InjectLib/) and [PartialData](https://thunderstore.io/c/gtfo/p/Flowaria/MTFO_Extension_PartialData/) reflection and JsonSerializerOptions. And various other consolidated fixes and utilities.

Basically, a common library so that I don't have to copy paste the same code for each plugin.

Documentation is still a work in progress. Please refer to the GitHub repo or ask in my [plugin feedback thread](https://discord.com/channels/782438773690597389/1264277162685628528) for how to use.

## Terminals
Contains the following vanilla bug fixes:
- FlowGeos modded reactor terminal instantiation.
- Hidden terminal commands are fully hidden (not able to be tabbed).
- Reactor terminals are appended to their zone's TerminalsSpawnedInZone.

## API
Currently exposes `LightAPI`. Major thanks to [Dinorush](https://thunderstore.io/c/gtfo/p/Dinorush/) for the help with putting this together.

<details>
  <summary>(Expand)</summary>

First, you need to pull  `LightWorker`(s) of the lights you want to change. (LightAPI has several helper methods to get certain LightWorkers in a zone or within range of a position.) Then, to add a modifier, call AddModifier on the LightWorker. For example, if you are applying the same modifier to multiple lights:
```
IEnumerable<LightWorker> workersInZone = LightAPI.GetLightWorkersInZone((0, 0, 0));
GetLightWorkersInZone<ILightModifier> lightMod = workersInZone.AddLightModifiers("red", 1.0f, true, LightPriority.Normal);
```
This will instantly enable all lights in the elevator zone, set intensity to 1, and change the color to red. 

If you want to lerp light settings for individual lights, create a modifier with the current light settings as to not immediately apply new settings:
```
LightWorker worker = MyCoolWorkers[i]; // example list of LightWorkers
LG_Light light = worker.Light;
ILightModifier mod = worker.AddModifier(light.m_color, light.m_intensity, light.enabled);
// Go to MyCoolCoroutine...
while (time <= duration)
{
    time += Time.deltaTime;
    progress = Mathf.Clamp01(time / duration);
    mod.Color = Color.Lerp(startColor, endColor, progress);
    mod.Intensity = Mathf.Lerp(startIntensity, endIntensity, progress);
    yield return null;
}
```

All ``AddModifier`` methods return the created ``ILightModifier`` object(s), which provide methods to update or remove itself.
```
public interface ILightModifier
{
    // The color of this modifier.
    public Color Color { get; set; }

    // The intensity of this modifier.
    public float Intensity { get; set; }

    // The (light) enabled/disabled state of this modifer.
    public bool Enabled { get; set; }

    // The priority of the modifier. Highest priority takes affect; FIFO.
    public int Priority { get; }

    // Whether the modifier is currently active on the light.
    public bool Active { get; }

    // Sets a new light color, intensity, and enabled state for the modifier, if Active
    public void Set(Color color, float intensity, bool enabled) { }

    // Adds the full modifier back to the top of the stack.
    public bool Register(); 

    // Disables the modifier and removes it from the light.
    public void Remove();
}
```

Note: LightWorkers do not persist between levels.

</details>

## Other Features
- Dependencies
  - InjectLib wrapper
  - PData wrapper
- Events
  - Additional level-related events
  - SNetEvents-related events
- Networking
  - StateReplicators
  - SyncedEvents
- Utils
  - Json-related
    - BoolBase
    - ValueBase
    - LocaleText
  - CourseNodeUtil
  - GlobalBase & GlobalIndexUtil
  - JsonSerializerUtil
  - ZoneGraphUtil