# Asteroids

A from-scratch remake of the 1979 Atari arcade classic [_Asteroids_](https://en.wikipedia.org/wiki/Asteroids_%28video_game%29), built in vanilla JavaScript on top of [p5.js](https://p5js.org/). No game engine, no build step — just a `<canvas>`, some trigonometry, and a lot of exploding rocks.

**[▶ Play it now](https://matteogiorgi.github.io/asteroids/src)** — runs entirely in the browser, nothing to install.

![Asteroids gameplay preview](assets/play.gif)




## Features

- **Classic vector-style visuals** — ship, asteroids, and score rendered as glowing outlines on a black canvas, just like the original cabinet.
- **Physics-based flight** — thrust, drift, and rotation instead of grid movement; momentum carries you across screen edges (screen wrap included).
- **Asteroid breakup** — shoot a big rock and it splinters into smaller, faster ones, each worth more points as they shrink.
- **Bombs** — deploy mines that arm themselves (they glow red 😨) and chain-detonate anything nearby, including *your own* mines and, if you're not careful, you.
- **Endless progression** — clear the field and the next level throws more asteroids at you.
- **Lives, scoring & sound** — three lives, a segmented score counter, and dedicated sound effects for lasers, explosions, and armed bombs.




## Controls

| Key             | Action                                  |
|-----------------|------------------------------------------|
| <kbd>W</kbd>     | Thrust forward                          |
| <kbd>A</kbd>     | Rotate left                             |
| <kbd>D</kbd>     | Rotate right                            |
| <kbd>Space</kbd> | Fire laser                              |
| <kbd>M</kbd>     | Drop a mine (bomb)                      |

> ⚠️ Firing at an armed bomb doesn't defuse it — it makes it bigger, and angrier.




## Running locally

The game is static and dependency-free (p5.js is vendored under `src/libraries/`), so any local web server works:

```bash
cd src
python3 -m http.server 8000
```

Then open `http://localhost:8000` in your browser. A convenience script (`src/script.sh`) does the same and launches Firefox directly — it exists to sidestep Firefox's local file security restrictions, which otherwise block loading assets from `file://`.




## Project structure

| File / dir       | Purpose                                                           |
|------------------|-------------------------------------------------------------------|
| `index.html`     | Entry point, wires up p5.js + game scripts                        |
| `sketch.js`      | p5.js setup/draw loop, game state, collisions between sub-systems |
| `world.js`       | Per-frame update & render orchestration                           |
| `ship.js`        | Player ship: movement, lasers, mines                              |
| `asteroid.js`    | Asteroid spawning, movement & breakup                             |
| `mine.js`        | Bomb entity: arming, chain-reaction blast radius                  |
| `laser.js`       | Projectile entity                                                 |
| `dust.js`        | Explosion particle effect                                         |
| `hud.js`         | Score & lives display                                             |
| `input.js`       | Keyboard event dispatcher                                         |
| `audio/`         | Sound effects                                                     |

_(all under `src/`)_




## License

Released under the [GNU GPLv3](LICENSE).
