# Description
Makes the bots smarter by improving their combat and make them more reliable. 

# PATCH NOTES
## Ver 0.2.3
    - suddenly human friendly fire working badly, fixed
    - fixed typo Launcing -> Launching (lul)
	
## Ver 0.2.2
    - bots should really extract even better now (fighting a cornercase where bots ignore)
	
## Ver 0.2.1
    - bot sentries started doing friendly fire on 0.2.0, oops. fixed.
	- bot that has just been revived and is playing the "getting up" animation are no longer teleported
	- bots should now join extraction without warp business, sentries stay deployed

## Ver 0.2.0
    - all sentries (incl level spawned) should work better
	- improved ff layermask handling, should work better even host-only. no harm in installing on all players.
    - dino taught me valuable stuff again. thanks.

## Ver 0.1.9
    - upon feedback: betterbots now survives Unity Explorer (and maybe even cconsole) better
    - no other changes
	
## Ver 0.1.8
    - upon request: added configuration option to skip making stealth scans red (m_hasAlarm true)
	- there is a risk bots will ignore some scans, vanilla and modded, use at your own risk

## Ver 0.1.7
    - integer and ferrydown inspired improvements to bot scanning (stupid t-scans)
	- bots should scan teamscans and t-scans much better now.
	
## Ver 0.1.6
    - integer rundown with many extrachainpuzzlecust scans inspired a change:
    - if teleport is allowed in config, bots now tp snap to the bioscan their followme is standing in
    - if teleport is not allowed, function as before
	- works great with integer dual duo scans 2human 2bot
	- known problems: integer a2 t-scan, enemy proximity makes bots abandon scanning. will try to find fix to prevent future team wipes due to bots being #%"¤&#¤/"# .. FFFF#"#&#%/!
	
## Ver 0.1.5
    - bots observed to bug out when ladders and scans exist in the same tile. offending travel action removed. sorry.
	- logic improved, not spamming a fail + assign loop if assignment is done by this mod, might make a bot more consistent in carrying out the bioscan action.

## Ver 0.1.4
    - user request: bot bioscan logspam twice a second, removed
	- bots bouncing between multiple bioscan cores, should be somewhat mitigated. ish.

## Ver 0.1.3
    - user request: config option for bot opening containers automatically (default true)
	- user request: config option for bots teleporting around (default true)
	- bots will again aggressively join extraction scan

## Ver 0.1.2
    - thank you n3onzim for reporting a problem with dc scans, preloading a sector got the bots all confused and broken about scanning
	- bulkhead dc related scans are now ignored, not set m_hasAlarm true and no bot summoning commands will be sent for them

## Ver 0.1.1
    - No longer depends on GTFO-API (VRmod users rejoice)
    - You can now disable friendly fire between humans too (configurable, default ff enabled) .. Only works if all players install the mod (same as bot ff)
	- Due to config file addition, please check bepinex/config/betterbots.cfg after first launch, after update. Your aim accuracy: true may revert to false. do check, thanks.
	- Bots will now be instructed to bioscan more than just the warden extraction scan, they are told to follow their leader to scans they might sometimes ignore.
	  (Examples: certain synchronous duo-scans from standalone competition, rundownx custom team scans)

## Ver 0.1.0
    - in 0.0.9 the bots had damage multiplier 0.75 and damage resistance multiplier 0.75 built in. removed in this patch. thanks lout3nant for reporting.

## Ver 0.0.9 (Beta)
    - hirnukuono added to team to contribute to BB, starting with this one.
	- Bot friendly fire fixed, identical to NoBotFriendlyFire and HitTheLights. Requires all players (not just host) to run this mod.
	- "Cannot receive commands while on ladder" after bot-teleport, fixed. Bots will no longer teleport while climbing ladders.
	- Bots will now be summoned to join host in Warden extraction scan if they are less than 50 meters away.

## Ver 0.0.8 (Beta)
	- Bots will no longer friendly fire, the bullets that bots fire will phase through players and bots.

## Ver 0.0.7 (Beta)
	- Made a config file for the mod
	- Added "Improved Aim" config to toggle aimbot on or off.

## Ver 0.0.6 (Beta)
	- Bots will now priotize shooting weak spots on the enemies (Such as the ones on the Tanks and Mothers).

## Ver 0.0.5 (Beta)
	- Removed the 10% weapon bonus damage.
	- Removed the 10% damage resistance.

## Ver 0.0.4 (Beta)
	- Improved the bot's shooting accuracy.
	- Bots can now pick up objective items during combat, and they will drop it if attacking monsters are too close.
	- Bots will cancel picking up items inside resource containers if any human players are close.
	- Bots will inflict 10% weapon damage.
	- Bots have a 10% damage resistance to melee and projectile attacks.
	
## Ver 0.0.3 (Beta)
	- Bot's can now open resource containers if they are not locked.

## Ver 0.0.2 (Beta)
	- Set the revive priority back to default.

## Ver 0.0.1 (Beta)
	- Initial release
	- Bots will cancel revives if too many attacking monsters are nearby or taking consistent damage.
	- Bots will do more evasive manuvers and use their guns more often in a horde of monsters or if a monster is nearby that takes away 40% of health with a melee attack.
	- Bots will cancel their attempts to ping resources when being attacked.
	- During combat, bots will run over to the resource packs to grab them instead of walking.	

## Installation
	- Place `BetterBots.dll` into the `BepInEx\plugins` folder.
	- Unzipping the zip into your game folder should work as well.