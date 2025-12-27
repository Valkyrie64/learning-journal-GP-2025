# Learning-Journal-GP-2025
My learning journal for Game Programming

## Problem: The player bounces when hitting the wall colliders and can phase through one of the walls if pressed against another.

Solution: I first tried using rigidbody.AddForce instead of transform.Translate, but this caused an issue of moving the character when the keyboard keys weren't pressed. My second solution which worked was using rigidbody.velocity, which only moves the character when the keys are pressed.

Time Spent: 30 mins, 18:48 - 19:18

## Problem: Bullet wasn't destroying enemy when contacting it

Solution: I first changed the OnTriggerEnter to be for 3d instead of 2d, as I mostly use 2d code and my code defaulted. I then had to change the CompareTag function to be for the other game object, as I had accidently written gameObject.CompareTag instead of collision.CompareTag.

Time Spent: 1:20 mins, 19:30 - 20:50

## Problem: Random.Range isn't working when trying to spawn enemies at random intervals

Solution: I first tried making the random number get created inside of an if statement in Update. This didn't work as it defaulted to always using the number set as "spawn time" outside of the if statement.

After changing where the spawn time number would be set, I encountered a problem where the enemy would spawn at random intervals for a couple seconds, then spawn infinitly. To fix this, I added a statement in the if statement to reset the timer that increases by Time.deltaTime in order to see if a new random spawn interval has been passed.

Time Spent: 40 mins, 21:30 - 22:10

## Problem: Stopping the enemies when they get to a certain point on the screen, and only letting a certain amount on screen at a time.

Solution: I didn't run into any specific problems, but did learn that the Physics.OverlapBox function can't return a bool, which the Physics2D version can. Instead I used a simple OnTriggerEnter function to see if the enemy has hit a collider that zeros their speed.

I also used the List<GameObject> variable and the List.Add() function to add the enemy game objects to a list and only allow for 5 to exist on screen at the same time.

Time Spent: 18 mins, 22:15 - 22:33

## Problem: Moving the camera with code

Solution: I started with using simple transform.position and transform.rotation to make sure I had the camera in the 2 places that I would want it. Afterwards I looked into getting the camera to move dynamically instead of just setting. I first tried using Translate and Rotate. An issue that arose was that as the camera was rotating, the Vector3 that I was using for the translate would move the camera into a different position.

The solution that I had to this was to use the SmoothDamp and Slerp functions for position and rotation respectively. This allowed for the player to see the camera move instead of just set to the position needed.

Time Spent: 1:20 mins, 23:00 - 00:30

## Problem: Camera Movement not completing in full

Solution: Originally the camera would only move as long as the button was pressed. What I wanted was for the process to fully complete when I press the button, instead of hold. To achieve this I used a coroutine that waits for the camera movement to finish by adding a wait time until a new function can start.

There is the issue of if both buttons are pressed at a similar time, then the camera will get stuck between the 2 positions, however this is not an issue I need to fix as the camera movement will be done by a trigger event instead of a button press and therefore both coroutines should never be triggered at the same time.

Time Spent: 1 hour, 11:00 - 12:00

## Problem: Enemy List not updating correctly

Solution: The code originally looked for an object with the "Enemy" tag to add to the List, but this ended up adding the first object tagged "Enemy" to the list multiple times. The fix was to make the Instantiate line a variable and add that variable to the list instead.

Time Spent: 40 mins, 10:00 - 10:40

## Problem: Camera move speed didn't work with win condition

Solution: Once enough enemies were killed the camera would move to the other space, however it wouldn't move quick enough to be in the correct place for the player to move. To fix this I had to increase the Quaternion.Slerp time in order for the rotation to be complete quicker

Time Spent: 45 mins, 12:05 - 12:50

## Problem: Enemy Bullets

Solution: After creating a bullet prefab for the enemy and instantiating it, the enemy object would immediately be destroyed. This is because the script for destroying enemies is based on whether a bullet collides with an object tagged "Enemy". To fix this I added an if statement to the bullet that checks a bool to see if the bullet is firing from the player or the enemy, and if its the enemy then to not check for the "Enemy" tag.

Another issue was that the enemies would be creating bullets on every frame. The fix for this was to add a time parameter to when they can fire and how often.

Time Spent: 30 mins, 10:20 - 10:50

## Problem: Score

Solution: Once an enemy was killed, the score in the top left should increase by 10, but this wasn't happening. The reason why was because I was using the legacy UI system scripting to try and access TMP related components.

Time Spent: 30 mins, 11:00 - 11:30

##Problem: Removing Enemies After Level Transition

Solution: First I tried iterating through the game object list that had been created to keep only 5 enemies on screen, then destroy the game object and remove the element reference. After some trial and error with checking that the for loop was targeting the right list index and that the correct list was being iterated through, I was unable to make this work.

Next I tried making the enemies instantiate into an empty game object that I could then delete all the children of. This also didn't work as I would have needed to restructure a lot of the previous code and it would have been a better choice if I couldn't find another fix.

Finally, I tried a much simpler process of finding any game object with the tag "Enemy" in the hierarchy and destroying them from there. This worked very well, after reordering some of the lines of code so that the destroyed objects in the transition didn't count towards enemies killed by the player.

Time Spent: 95 mins, 15:00 - 16:35
