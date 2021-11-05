# Overview

After troubleshooting my mod [Aesthetic Terraform Stations](https://steamcommunity.com/sharedfiles/filedetails/?id=2622411084) with [ubet](https://steamcommunity.com/profiles/76561198014040436), the original mod [Advanced Ship Behaviour Modules](https://steamcommunity.com/sharedfiles/filedetails/?id=790455347) was found to be the culprit causing mining stations to somehow use the terraform station graphics entity.  After investigating the script I found that was significantly out of date (being originally for Stellaris 2.0.*) and that syntax errors in its `ship_size` overrides were breaking the `terraform_station` size added by my mod.  This is related to what happens when there are significant errors in a file and how the game loads script files.

The original mod looked interesting, so I decided to revive it by fixing all of the errors.  I avoided adding significant functionality but did add a couple of missing graphics and ensured that "No AI" computers still grant an increasing bonus as computer technology advances.

# Changes

The original mod "Advanced Ship Behaviour Modules" overwrites the majority of built-in ship classes by replacing the file `common/ship_sizes/00_ship_sizes.txt`.  This overwrite is necessary to add the new "AI Behavior" component to the combat ship classes.  This mod overwrites the same file in order to use the most up-to-date code from the base game for all of the affected ship classes (including titans but not juggernauts).

This mod also updates code for all of the ship AI behaviors, special components, and point-defense fighters to be in line with the evolution of Stellaris since 2.0 "Cherryh" (who incidentally _also_ happens to be my favorite science fiction author).  Add graphics for basic and advanced "No AI" computers, give bonuses to the increasing levels of "No AI" computers - the bonus is roughly 1/4 the bonus of each standard role-based computer.

## Compatibility

This mod resolves compatibility conflicts from the original mod "Advanced Ship Behaviour Modules" by overwriting its out-of-date files.  The original mod replaces almost all of the standard, built-in ship classes.  Therefor, both the original and this updated version will conflict with any other mods that make changes to the contents of  the file `common/ship_sizes/00_ship_sizes.txt` - which defines the majority of player-buildable ship classes.  This mod is technically compatible with mods that add new ship classes, but any new ship classes added by other mods will not have the option for custom-defined AI behavior and instead will use the computer provided by that mod.

Built for Stellaris version 3.1.* "Lem."  Not compatible with achievements.

### When to Install

This mod can be safely added after the game has started, but should not be removed from a game in-progress.  Losing access to the new ship components or behaviors could cause problems for the game if any are in use.  Always backup your savegame before attempting to remove a mod.

## Known Issues

None

## Change Log

* 1.0.0 Initial version

## Source Code

Hosted on [Github](https://github.com/corsairmarks/advanced_ship_behaviour_modules_revisited)

### Development Notes

It is best to clone this repository into `<Stellaris User's Directory>/Paradox Interactive/Stellaris/mod`, and then make a connection to the `mod` folder via a `*.mod` file's `path` property.  That will ensure the game can see the files, and also that CWTools will parse them.  Also note that the README.md file exists in the `mod` directory but is symbolically linked in the root directory.