# Visor HUD (vrasync)

Metroid-style visor HUD for Meta Quest 3 (WebXR) with a Control page that helps the VR player with abilities and upgrades.

1. Open the site in the Quest browser. It shows a 4-letter code.
2. Open the same site on a tablet/phone/computer, choose Control, type the code.
3. Enter VR or MR on the headset. On the control page pick an ability, then tap the map.

Pairing is peer to peer (PeerJS); nothing is stored.

## Game: flashlight defence

The headset player holds a flashlight in each controller and squeezes the trigger to shoot light orbs at the pumpkin ghosts walking in from all sides (head shots do double damage). Ghosts do not throw anything. They drain suit energy while touching the player.
Every shot uses battery. The control player spends build points on **Recharge**, and on crowd control: **Freeze** zone, **Push** wave, **Decoy** lantern and **Bomb**. **Ping** shows the player where enemies are coming from.
Flashlight direction can be tuned in "Flashlight setup" on the headset page.

Enemy types unlock by wave: Runner (wave 2, packs of three, fast, one hit), Wisp (wave 3, floats at head height and weaves), Brute (wave 4, big, slow, lots of health, drains energy fast, hard to push) and Splitter (wave 5, breaks into two minis). Each type has its own 3D spawn sound, and the headset has ambient wind, crickets, owls, crows, bells and creaks while a game runs.

Update: one touch from an enemy ends the run. The flashlight has a small battery (10 shots) that refills by itself when you stop shooting, and the visor HUD is now a big flashlight meter, one segment per shot. Bombs only go off when the VR player shoots them. Enemies sometimes drop battery pickups that the control player taps on the map to send an instant boost. The flashlight model is a yellow low-poly torch and the scene is now a night scene.

Control page hot keys: 1 Freeze, 2 Push, 3 Decoy, 4 Bomb, 5 Ping, 6 Damage, 7 Battery, 8 Range upgrades, 9 Big blast (when you have one). The key number shows on each button.

Atmosphere: drifting ground fog, fences, crooked crosses, lit mausoleums, flickering lantern posts, fireflies, marsh lights, bats and distant lightning with thunder. Whispers and moans come from the edge of the arena, enemies make footsteps as they walk in, and a heartbeat speeds up when one gets close.

Coins and upgrades: every kill gives coins straight to the control player (ghost 2, runner 1, wisp 3, brute 8, splitter 4, mini 1). Spend them on Damage, Battery (more shots per charge) and Range, five levels each costing 5, 10, 15, 20, 30 coins. Upgrades reset every run. The light ball is now a glowing ball of light and its default range is 9 m.

## Rounds, power-ups and new enemies
- A 3-2-1-GO countdown starts the run; each wave has a banner, a sting and a light flash, and "WAVE CLEARED" shows between waves. Dying plays a slow-motion red fade and a score card; the VR player can pull a trigger to play again.
- When the control player buys an upgrade, or anyone picks something up, a floating text appears in front of the VR player.
- Enemies drop power-ups that the control player taps on the map: Rapid fire, Piercing shots, Shield (survives one touch), Slow time (both players), Free builds, Double coins, Big blast (one giant explosion, tap the map to fire it) and Magnet.
- New enemies: Teleporter (wave 5, blinks forward, warning sound first), Shielded ghost (wave 6, shoot it when its shield swings aside), Bat swarm (wave 7, six fast zig-zaggers), Phantom (wave 8, only hurt while visible).
