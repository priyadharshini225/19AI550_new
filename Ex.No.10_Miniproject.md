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
```
using UnityEngine;

public class PlayerMovement : MonoBehaviour
{
    public float speed = 5f;
    public float turnSpeed = 150f;

    Rigidbody rb;

    void Start()
    {
        rb = GetComponent<Rigidbody>();
    }

    void FixedUpdate()
    {
        float move = Input.GetAxis("Vertical");
        float turn = Input.GetAxis("Horizontal");

        // Rotate player
        transform.Rotate(Vector3.up * turn * turnSpeed * Time.deltaTime);

        // Move player
        Vector3 movement = transform.forward * move * speed * Time.fixedDeltaTime;
        rb.MovePosition(rb.position + movement);
    }
}
```
### Output:
<img width="1055" height="559" alt="image" src="https://github.com/user-attachments/assets/c173720e-ca0c-40ae-b33e-b014d327ad12" />

<img width="1055" height="559" alt="image" src="https://github.com/user-attachments/assets/16202156-d6e3-4ae9-a268-7d0cea9d042c" />

### Result:
Thus the game was developed using Unity and adopted basic game logic and user interaction techniques.
