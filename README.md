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
