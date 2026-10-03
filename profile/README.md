<h1 align="center">VECTOR FIVE</h1>

<p align="center">A competitive 5v5 tactical shooter, built so that every shot can be explained.</p>

## The game

V5 is a first-person shooter for two teams of five, with one life each round. Its main mode,
Override, is a plant-and-defuse format. Breach carries the Key, an encrypted device, to one of two
nodes, installs it and protects it until the override completes. Guard stops that by running the
clock down or by purging the Key once it's in. Eliminating the whole other team wins the round for
either side. Sides swap after nine rounds and the first team to ten takes the match.

A round opens with the Spawn Draft. Each side has five authored spawn points, everyone picks one
during planning, and the other team doesn't see the choices until the round starts. Ranked never
puts anyone on a random spawn.

There are no heroes. Every operator has 100 HP and the same protection. Armour isn't for sale, so a
team's credits go on weapons and utility.

## Shooting

Each weapon has a fixed recoil pattern you can learn. Stand still with a rifle or a sidearm and the
first shot lands exactly on the crosshair. Spread opens up when you move or keep firing. It follows
a fixed pattern too, and the crosshair always shows how far the next shot can stray. Nothing about a
shot is random. Shotgun pellets follow a fixed lattice as well.

Firearms are hitscan, and the server decides every hit. Your client draws the muzzle flash and the
tracer at once, but damage only counts when the server confirms it. After the round you'll be able
to review any shot as the server resolved it.

Ranked matches will end with an integrity receipt for every player, listing the build and rule
version, the server, the network conditions, a checksum of the replay and the exact rating change.
No graphics setting can thin out smoke or remove cover, and enemies are never outlined through
walls.

## One game, two engines

V5 is being built twice. One build runs on [DriftEngine](https://driftengine.dev): TypeScript, in
the browser on WebGPU with a WebGL2 fallback, with a dedicated server on Node. The other is native
C++ on Aver Engine, for Windows.

The two share no code. They share the game: the schemas, the data, the assets, and a suite of
conformance tests both builds have to pass. The expected results in those tests are worked out from
the written rules, so neither engine's behaviour becomes the rule by accident. Every gameplay number
lives in data, and the values that decide a match are integers, since JavaScript and C++ can't be
relied on to round floating point the same way. In the DriftEngine build the rules themselves are
[DriftScript](https://script.driftengine.dev) systems.

## Status

It's early, and everything you'd see is graybox. The match rules run and pass their conformance
tests, and you can walk Relay, the first map, in first person. Weapons are going in now. Carrying
and installing the Key, the Spawn Draft, buying and bots come next, so one person can play a full
5v5 offline. Networking follows, then Foundry and Atrium, the other two maps. The Aver Engine build
is just starting, against the same tests.

Art waits until the game plays. Placeholders go through an asset registry, so the final
photorealistic models replace them without a change to gameplay code.

The game's repository is private.
