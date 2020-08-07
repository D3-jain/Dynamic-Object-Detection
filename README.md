# Akatsuki_Hologram

## Objective

<img align="right" src="Akatsuki-Hologram.gif">
So the main objective of this project is to detect dynamic object using Background Subtraction method with MOG2 algorithm under it. But to make it a little innovative and fun we can add a static filter moving in the screen instead of just printing the masked area, therefore the target of this project would be to generate something as close to the one shown in the right in this section. This is a scene from the famous anime called <b>Naruto</b> that depicts a hologram with a static filter of the person instead of the person physically being there.
<br><br><br><br><br>

## Idea Implementation

<img align="right" height="280" width="500" src="Naruto-Run.gif">
The idea behind this project can be explained with the following steps:

* Import and  resize the static image in order to be the same size as the background being captured (i.e. 640,480 )
* Record a background in order to blend it with static image using addWeighted method
* For better efficiency we initialize MOG2() background subtractor object.
* Capture video frame by frame and read it in while loop to perform the object detection step
* Apply the initialized background subtractor object to each frame obtained to get the mask of the dynamic object.
* Obtain an inverted mask of the dynamic object's mask using bitwise_not.
* Using bitwise_and apply the actual frame image over the inverted mask and similarly apply blended image to the dynamic object mask. And since unmasked area represent black color it's pixel value is 0 and it remains unaffected by the operation, whereas masked area's color white has pixel value equal to 255 and 0b11111111 in binary it gives output of the image which we want to apply.
* Add both the obtained results in the above step using addWeighted method and write the output.
The above mentioned steps keep performing untill either cap.read() returns False or the user presses "q" button on the keyboard.
