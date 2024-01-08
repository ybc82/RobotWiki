# Contact Model Fusion for Event-Based Locomotion in Unstructured Terrains

The contact point may not be as expected. And MIT Cheetah 3 is moving around using 'terrain-blind locomotion'. The robot control / gait control is symmetric by nature. It's hybrid control with trajectory control in the swing phase and impedance control in stance phase. Without a force sensor, a probabilistic model is presented based on the leg model. Then contact point is determined by the model (with threshold) instead of the predicted time. Intentially, a delay is added after when the contact is 'determined', because it could also be model error, during which the leg only holds position, so that there won't be catastrophic response if the estimation is wrong.

