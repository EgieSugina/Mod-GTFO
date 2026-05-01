# ModifierAPI

Adds an API for plugin developers to modify certain values without conflicting with other mods.

Currently supports:
- Movement Speed
- Melee Attack Speed
  - Can specify Light, Charged, Push, or All
- Melee Range

## API

Currently exposes 2 APIs:
- MovementSpeedAPI
- MeleeAttackSpeedAPI
- MeleeRangeAPI

To add a modifier, call an AddModifier function from an API, e.g.:

```cs
IStatModifier MoveSpeedAPI.AddModifier(float mod, StackLayer layer = StackLayer.Multiply, string groupName = "Default");
```
Where the parameters are:
- `mod`: The value of the modifier to apply.
- `layer`: Which layer the modifier is added to. Determines how it stacks with other modifiers.
  - Options: Multiply, Add, Max, Min, Override
- `groupName`: Which group to put the modifier in. Layers only apply within each group; separate groups are multiplied.

All `AddModifier` functions return the created `IStatModifier` object. The modifier provides methods to update its value or remove itself:

```cs
public interface IStatModifier
{
  // The value of the modifier. Updates when modified if active.
  public float Mod { get; set; }

  // The layer the modifier is on.
  public StackLayer Layer { get; }

  // Whether the modifier is active.
  public bool Active { get; }

  // Enables the modifier if it is inactive.
  public void Enable();

  // Sets Mod to the value and enables the modifier if it is inactive.
  public void Enable(float mod);

  // Disables/removes the modifier.
  public void Disable();
}
```

*Note: Speed modifiers are disabled on level cleanup. If you wish to use the same speed modifier across drops, make sure to Enable it.*

## Examples

#### Simple Timed Buff

```cs
public void AddSpeedBuff(float mod, float duration) {
  CoroutineManager.StartCoroutine(RunSpeedBuff(mod, duration).WrapToIl2Cpp());
}

private IEnumerator RunSpeedBuff(float mod, float duration) {
  var modifier = MoveSpeedAPI.AddModifier(mod);
  yield new WaitForSeconds(duration);
  modifier.Disable();
}
```

#### Simple Persistent Buff

```cs
IStatModifier? _activeModifier = null;

public void SetAttackSpeedBuff(float mod) {
  if (_activeModifier == null)
  {
    _activeModifier = MeleeAttackSpeedAPI.AddModifier(mod);
  }
  else
  {
    _activeModifier.Enable(mod);
  }
}
```