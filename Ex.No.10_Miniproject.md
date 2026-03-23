# Ex.No: 10  Implementation of simple maze game
### DATE: 23/03/26                                                                           
### REGISTER NUMBER : 212223240129
### AIM: 
To develop a game Simple 3D Maze Game in Unity.
### Algorithm:
```
1. Start the Unity application.
2. Create a new 3D project.
3. Add a Plane object to act as the ground.
4. Create Cube objects and arrange them to form maze walls.
5. Add a Player object (Capsule) to navigate the maze.
6. Attach Rigidbody and Collider to the player.
7. Write a C# script to control player movement using keyboard input.
8. Attach the script to the player object.
9. Add an Exit point using a Cube with trigger collider.
10. Write a script to detect collision with the exit.
11. Display "You Win" message when player reaches exit.
12. Run the game and test movement and collision.
13. Stop the game.
```  
### Program:
Playermovement.cs
```
using UnityEngine;

public class PlayerMoveSimple : MonoBehaviour
{
    public float speed = 5f;
    public float turnSpeed = 200f;

    CharacterController controller;

    void Start()
    {
        controller = GetComponent<CharacterController>();
    }

    void Update()
    {
        float move = 0f;
        float turn = 0f;

        // Key input (no Input Axis problem)
        if (Input.GetKey(KeyCode.W)) move = 1f;
        if (Input.GetKey(KeyCode.S)) move = -1f;
        if (Input.GetKey(KeyCode.A)) turn = -1f;
        if (Input.GetKey(KeyCode.D)) turn = 1f;

        // Rotate
        transform.Rotate(0, turn * turnSpeed * Time.deltaTime, 0);

        // Move
        Vector3 movement = transform.forward * move * speed;
        controller.Move(movement * Time.deltaTime);
    }
}
```
enemy.cs
```
using UnityEngine;

public class EnemyAI : MonoBehaviour
{
    public Transform player;
    public float speed = 2f;

    void Update()
    {
        if (player == null) return;

        // Move toward player
        Vector3 direction = (player.position - transform.position).normalized;
        transform.position += direction * speed * Time.deltaTime;

        // Face player
        transform.LookAt(new Vector3(player.position.x, transform.position.y, player.position.z));
    }
}
```
### Output:
<img width="1052" height="561" alt="image" src="https://github.com/user-attachments/assets/98886df3-0c0c-4e61-af2a-e24b2caec23e" />

<img width="1049" height="588" alt="image" src="https://github.com/user-attachments/assets/a66686fc-23b8-4657-9ee5-0709938bd0b2" />

### Result:
Thus the game was developed using Unity and adopted basic game logic and user interaction techniques.
