# GAME_PROGRAM-EX--5
## Making Player to collect the ammo and increase the bullet spawn count.
##  Aim
To implement a gameplay feature where the player collects ammo pickups in the game world. Upon collecting ammo, the player's ammo count increases, enabling more bullet spawns (shots).

---

## Procedure

### 1. Setup Player Character

- Open your `PlayerCharacter` Blueprint.s
- Add a new **Integer** variable named `AmmoCount`.
- Set an initial default value (e.g., `AmmoCount = 10`).
- Ensure you have a shooting mechanism in place that uses `AmmoCount` to determine if a bullet can be fired.

### 2. Create Ammo Pickup Blueprint

- Go to the Content Browser → Right-click → **Blueprint Class** → Select **Actor** → Name it `BP_AmmoPickup`.
- Add components:
  - **Static Mesh**: Representing the ammo (e.g., a bullet or crate).
  - **Sphere Collision**: To detect overlap with the player.
- In the Event Graph of `BP_AmmoPickup`:
  - Use `OnComponentBeginOverlap` on the Sphere Collision.
  - Cast to `PlayerCharacter`.
  - Increase the player’s `AmmoCount` (e.g., `AmmoCount += 5`).
  - Optionally, play a pickup sound or effect.
  - Destroy the ammo pickup actor.

### 3. Update Shooting Logic (Optional)

- In your player’s shooting logic:
  - Before spawning a bullet, check `if AmmoCount > 0`.
  - If true:
    - Spawn bullet.
    - Decrease `AmmoCount` by 1.

### 4. Place Ammo in the World

- Drag instances of `BP_AmmoPickup` into your level from the Content Browser.
- Adjust position, mesh, and pickup range as needed.

---

## Output

<img width="1134" height="765" alt="4" src="https://github.com/user-attachments/assets/1ae4ceb9-9978-4150-8a7e-b4e7651e4213" />
<img width="1919" height="1013" alt="3" src="https://github.com/user-attachments/assets/e4ef98ac-8a7f-48cf-b011-453c29b00847" />
<img width="1335" height="839" alt="2" src="https://github.com/user-attachments/assets/2c6e69d7-eac8-4703-9601-e0f22276b39e" />
<img width="1918" height="856" alt="1" src="https://github.com/user-attachments/assets/3c6036d2-61e8-4da3-9643-6e9c82275d84" />



##  Result

- The player starts with a limited number of bullets.
- When the player overlaps with an ammo pickup:
  - The ammo is collected.
  - The player's `AmmoCount` increases.
- The player can now fire additional bullets based on the updated ammo count.

