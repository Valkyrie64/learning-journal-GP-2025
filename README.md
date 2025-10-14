# Learning-Journal-GP-2025
My learning journal for Game Programming

## 14/10/25
Learning Journal has been created.

Problem: The player bounces when hitting the wall colliders and can phase through one of the walls if pressed against another.

Solution: I first tried using rigidbody.AddForce instead of transform.Translate, but this caused an issue of moving the character when the keyboard keys weren't pressed. My second solution which worked was using rigidbody.velocity, which only moves the character when the keys are pressed.

Time Spent: 30 mins, 18:48 - 19:18

Problem: Bullet wasn't destroying enemy when contacting it

Solution: I first changed the OnTriggerEnter to be for 3d instead of 2d, as I mostly use 2d code and my code defaulted. I then had to change the CompareTag function to be for the other game object, as I had accidently written gameObject.CompareTag instead of collision.CompareTag.

Time Spent: 1:20 mins, 19:30 - 20:50

Problem: Random.Range isn't working when trying to spawn enemies at random intervals

Solution: I first tried making the random number get created inside of an if statement in Update. This didn't work as it defaulted to always using the number set as "spawn time" outside of the if statement.

After changing where the spawn time number would be set, I encountered a problem where the enemy would spawn at random intervals for a couple seconds, then spawn infinitly. To fix this, I added a statement in the if statement to reset the timer that increases by Time.deltaTime in order to see if a new random spawn interval has been passed.

Time Spent: 40 mins, 21:30 - 22:10

Problem: Stopping the enemies when they get to a certain point on the screen, and only letting a certain amount on screen at a time.

Solution: I didn't run into any specific problems, but did learn that the Physics.OverlapBox function can't return a bool, which the Physics2D version can. Instead I used a simple OnTriggerEnter function to see if the enemy has hit a collider that zeros their speed.

I also used the List<GameObject> variable and the List.Add() function to add the enemy game objects to a list and only allow for 5 to exist on screen at the same time.

Time Spent: 18 mins, 22:15 - 22:33
