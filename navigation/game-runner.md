
## Basic Game: Desert Adventure

{% capture challenge1 %}
Run the basic desert adventure game. Use WASD or arrow keys to move Chill Guy around the desert. Walk up to R2D2 to trigger a mini-game!
{% endcapture %}

{% capture code1 %}
// Import for GameRunner
import GameControl from '/assets/js/GameEnginev1/essentials/GameControl.js';
// Level Code
import GameEnvBackground from '/assets/js/GameEnginev1/essentials/GameEnvBackground.js';
import Player from '/assets/js/GameEnginev1/essentials/Player.js';

class CustomLevel {
  constructor(gameEnv) {
    const path = gameEnv.path;
    const width = gameEnv.innerWidth;
    const height = gameEnv.innerHeight;
    const bgData = {
        name: 'custom_bg',
        src: path + "/images/gamebuilder/clouds.jpg",
        pixels: { height: 720, width: 1280 }
    };
    const playerData = {
      id: 'Hero',
      src: path + "/images/gamify/chillguy.png",
      SCALE_FACTOR: 5,
      STEP_FACTOR: 1000,
      ANIMATION_RATE: 50,
      INIT_POSITION: { x: 100, y: 300 },
      pixels: { height: 512, width: 384 },
      orientation: { rows: 4, columns: 3 },
      down: { row: 0, start: 0, columns: 3 },
      downRight: { row: Math.min(1, 4 - 1), start: 0, columns: 3, rotate: Math.PI/16 },
      downLeft: { row: Math.min(2, 4 - 1), start: 0, columns: 3, rotate: -Math.PI/16 },
      right: { row: Math.min(1, 4 - 1), start: 0, columns: 3 },
      left: { row: Math.min(2, 4 - 1), start: 0, columns: 3 },
      up: { row: Math.min(3, 4 - 1), start: 0, columns: 3 },
      upRight: { row: Math.min(1, 4 - 1), start: 0, columns: 3, rotate: -Math.PI/16 },
      upLeft: { row: Math.min(2, 4 - 1), start: 0, columns: 3, rotate: Math.PI/16 },
      hitbox: { widthPercentage: 0.45, heightPercentage: 0.2 },
      keypress: { up: 87, left: 65, down: 83, right: 68 }
    };

    this.classes = [
      { class: GameEnvBackground, data: bgData },
      { class: Player, data: playerData },
    ];
  }
}
export const gameLevelClasses = [CustomLevel];
// Export for game runner
export { GameControl };
{% endcapture %}

{% include game-runner.html
  runner_id="game1"
  challenge=challenge1
  code=code1
  height="150px"
%}
