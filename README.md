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

## Tower defence for the control player
- Coins are the one currency: flashlight upgrades, towers, walls and traps all cost coins. Enemies pay out double what they used to.
- Towers (max 6): Lantern (shoots), Frost (slows enemies in range), Tesla (chain lightning), Battery (recharges the VR flashlight). Tap a built tower to upgrade it (3 levels) or sell it for half back.
- Walls (max 12): ground enemies walk around them, so lines of walls steer the crowd. Flyers (wisps, bats) and teleporters ignore the maze. Ground enemies within about 3.5 m of a tower or wall go for it and chew it until it breaks (walls have 8 HP, towers 10/14/18 by level), so walls also work as bait and towers need protecting. Sell and rebuild, or upgrade a tower to refill its health.
- Bot skill: Test tools (control page) and the headset test options both have a Bot skill button cycling Beginner, Average, Good and Expert. It changes how well the practice bots shoot and how smartly they build.
- The control player's headset-view panel shows only the game footage, without the VR player's HUD.
- Traps: Freeze, Decoy and Bomb now cost coins. Push and Ping stay as quick abilities (Push uses build points).
- Between waves you get 8 seconds of build time, with a preview of the next wave. The red zone on the map shows where enemies will appear (the 180 degrees in front of the VR player).
- Keys: 1-4 towers, 5 wall, 6 Freeze, 7 Decoy, 8 Bomb, 9 Push, 0 Ping, Q/W/E flashlight upgrades, B Big blast, U upgrade and X sell the selected tower.

## VR player extras
- Rally cry: squeeze both grips, or squeeze a grip with a hand raised above your head, to boost every tower's fire rate by 50% for 6 s (recharges after about 20 s more; the VR HUD shows READY or the countdown).
- Shatter: your shots do double damage to frozen or chilled enemies.
- Combo: kills within 3 s of each other build a coin multiplier up to x5.
- Bomb chain: shooting a bomb that catches several enemies pays bonus coins.
- Headshots that kill give +2 coins and a small battery refund.

## Score and scoreboard
- Kills score by enemy type (ghost 100 up to brute 400, phantom 300), multiplied by the combo (x1 to x5), plus a bonus of 250 x wave for each wave cleared. The score shows on the VR HUD and in the control page's top bar.
- When a run ends and the score makes the top 10, the control page asks for the VR player's and the controller's initials and saves them. The VR death card says "TOP 10" and waits (the VR trigger will not restart the run) until the controller has saved or skipped.
- Shared online board: create a free Firebase project, add a Realtime Database, paste its URL into `SCORE_DB_URL` near the top of the game code in `index.html`, and set the database rules to:

```json
{
  "rules": {
    "scores": {
      ".read": true,
      ".indexOn": ["score"],
      "$id": {
        ".write": "!data.exists()",
        ".validate": "newData.hasChildren(['score','wave','vr','ctl','t']) && newData.child('score').isNumber() && newData.child('score').val() >= 0 && newData.child('score').val() < 10000000 && newData.child('vr').isString() && newData.child('vr').val().length <= 3 && newData.child('ctl').isString() && newData.child('ctl').val().length <= 3"
      }
    }
  }
}
```
- Until a URL is set (or if the database can't be reached) scores are kept on that device only, and the board says so.
