# Lucas_Kanade_Tracker
1 Introduction
Lucas Kanade is a method to generate the optical ﬂow of events in a frame. These events are
gathered after considering a pixel and its neighbouring pixels. The least square criterion, an approach in
regression analysis is used to approximate the solution. The displacement of an image and its pixel contents
are studied for two frames and at these two instants these are nearly the same. Thus, optical ﬂow equations
are used to and assumed to be true for all the pixels in a window center.

2 Histogram Equalization
1. Histogram Equalization has been applied for tracking the car under the bridge.
2. This equalizes the darkness thus able to detect the car.
3. Gamma Correction was also tried to equalize the darkness but the output was not that promising.
4. We see that in 1-2 frames the rectangle goes a bit out of car, but the delta-p again converges thus
giving us less error.

3 Pyramid for rapid motion
1. This is used when there is rapid movement in the video frames/ rapid motion (input video of vase in
our case).
2. We have used pyramid by decreasing the frame resolution by 4 times, i.e in total three layers are used,
wherein ﬁrst layer is our normal layer, second layer and third layer have resolution reduced by 2 and 4
as compared to the ﬁrst layer.
3. The parameters are calculated from bottom to top layer. Each time the bottom layer is warped to the
layer above it with updated parameters.
4. Hence in the end the parameters are upgraded to the ﬁrst layer by considering the rapid shifts in the
lower resolution layers.

4 Pipeline
1. Initially a template was deﬁned by drawing a rectangle around the object that needed to be tracked
2. The subsequent frames were checked using Lucas Kanade algorithm, which returns the change in
parameters between two frames (∆p).
3. Parameters are updated in the current frame (p + ∆p)
• For Human and the described pipeline worked accurately
6
• For Car, to counteract the sudden change in intensity, Histogram equalization is used and also, features are extracted at every 100th frame again that are to be tracked in following frames. • For Vase, as there are large and rapid motions between two frames, Pyramid Algorithm is introduced into the pipeline.
4. After the convergence of the error of the parameters below some threshold(usually 0.001) the parameters
are returned.
5. Updated parameters is used to draw the rectangle and warped back to the current frame.
