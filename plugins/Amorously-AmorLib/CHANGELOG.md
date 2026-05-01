# Changelog
## v1.2.1
- Added safety checks to ZoneGraphUtil to avoid errors caused by other mod issues.

## v1.2.0
- Added new ZoneGraphUtil.

## v1.1.2
- Fixed an issue with the enabled state of light mods.
- Removed reflection in InjectLib_Wrapper.
- Added overload for CourseNodeUtil.GetCourseNode.

## v1.1.1
- Made the Prefix string in SyncedEvents virtual.

## v1.1.0
- Updated Thunderstore README.
- Fixed a logic issue with LightWorkers where modifiers were not fully reset or removed.
- Added new DataBlockUtil. 
- Added IStateReplicatorHolder interface.

## v1.0.5
- Fixed a null reference exception in CourseNodeUtil when a course node is null.

## v1.0.4
- Fixed an issue with the InjectLib and PartialData wrappers throwing an exception if either were not present in the profile.

## v1.0.3
- Hotfix for CourseNodeUtil mistakenly running on each factory batch instead of after the last AIGraph batch.

## v1.0.2
- Added new GameObject extension method `ClonePrefabSpawners`.

## v1.0.1
- Fixed an issue with CourseNodeUtil failing on consecutive drops.