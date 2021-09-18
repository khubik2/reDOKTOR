# reDOKTOR
Шизоредактор для шизоигры написанный шизом для шизов

## Things to avoid
- Avoid creating situations when keys couldn't spawn or something like that, game will crash
- Making 20x20 level, game has a stroke rendering huge chunks
- Don't go overboard with editing the textures for the triggers, game can't really render most of them here
- DON'T YOU EVER DARE TO FORCE 5-IN-RAW/5-in-a-row BONUS
- Don't make gray balls metallic unless you want a true psychodelic experience of no textures

## Roadmap

- [ ] ~~Clean code up a bit~~ NO
- [ ] Edit hints (i sorta do that already? IDK)
- [ ] Figure out ~~every field~~ iData4 of an entity
- [x] ~~Figure out why entities cluster size is always 1 and if it's possible to make a real schizo level~~ Each entity cluster has its own goal condition, if there are multiple entity clusters, entities from nex cluster will spawn after completing previous cluster's goal, until you clear them all, which opens up possibilities for real schizo levels
- [x] ~~Figure out all fields of the level header besides the metallic features size and how much balls to spawn~~ All of them are padding, I can confirm that
