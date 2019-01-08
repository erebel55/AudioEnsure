# AudioEnsure
This repo demonstrates an audio bug with Unreal Engine 4.21 that causes an ensure condition failed: Lhs.CurrentNum == Lhs.InitialNum

### Reproducing with this project
1. Click Play
2. Walk around for several minutes while pressing and releasing the c button. Stop walking sometimes as well.
   You will eventually get a very noticeable hitch and the ensure will show up in the logs.

### Creating your own project
The steps I took to create this project are below.

1. Create a new first person template project (I used BP only for simplicity but that isn't a requirement)
2. Set the CharacterMovement -> Can Crouch property to true within the character blueprint.
3. In the character blueprint, setup an input so that when pressed it calls Crouch and when released it calls UnCrouch.
4. Import a sound to use for footsteps.
5. In the character blueprint, create a function that calls SpawnSoundAttached and attaches the sound to the character's root component.
6. Create a new anim notify on the run animation and have this call the function created in step #5.
7. Walk around for a few minutes and keep pressing the crouch input and releasing. You will eventually get a hitch caused by the ensure. Check your logs and you will see it.
