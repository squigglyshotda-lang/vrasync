# Visor HUD (vrasync)

Metroid-style visor HUD for Meta Quest 3 (WebXR) with a Control page that drops shapes into the VR world.

1. Open the site in the Quest browser. It shows a 4-letter code.
2. Open the same site on a tablet/phone/computer, choose Control, type the code.
3. Enter VR or MR on the headset. Click the map on the control page to drop shapes.

Pairing is peer to peer (PeerJS); nothing is stored.

## Game: flashlight defence

The headset player holds a flashlight in each controller and squeezes the trigger to shoot light orbs at the pumpkin ghosts walking in from all sides (head shots do double damage). Ghosts do not throw anything. They drain suit energy while touching the player.
Every shot uses battery. The control player spends build points on **Recharge**, and on crowd control: **Freeze** zone, **Push** wave, **Decoy** lantern and **Bomb**. **Ping** shows the player where enemies are coming from.
Flashlight direction can be tuned in "Flashlight setup" on the headset page.

Enemy types unlock by wave: Runner (wave 2, packs of three, fast, one hit), Wisp (wave 3, floats at head height and weaves), Brute (wave 4, big, slow, lots of health, drains energy fast, hard to push) and Splitter (wave 5, breaks into two minis). Each type has its own 3D spawn sound, and the headset has ambient wind, crickets, owls, crows, bells and creaks while a game runs.

Update: one touch from an enemy ends the run. The flashlight has a small battery (10 shots) that refills by itself when you stop shooting, and the visor HUD is now a big flashlight meter, one segment per shot. Bombs only go off when the VR player shoots them. Enemies sometimes drop battery pickups that the control player taps on the map to send an instant boost. The flashlight model is a yellow low-poly torch and the scene is now a night scene.

Control page hot keys: 1 Freeze, 2 Push, 3 Decoy, 4 Bomb, 5 Ping, 6 to 0 pick the shapes (cube, sphere, cylinder, cone, torus). The key number shows on each button.

Atmosphere: drifting ground fog, fences, crooked crosses, lit mausoleums, flickering lantern posts, fireflies, marsh lights, bats and distant lightning with thunder. Whispers and moans come from the edge of the arena, enemies make footsteps as they walk in, and a heartbeat speeds up when one gets close.
