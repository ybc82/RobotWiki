# Publications

## Software and control design for the MIT Cheetah quadruped robots

Behaviors: walk, run, and do a backflip

Dynamics simulation: how to verify? 1. Total energy of the system was conserved. And important to measure how long time it takes to simulate a step forward.

Contact model: terrain modeled as a collection of planes and boxes, while the robot contains a number of ground contact POINTS on various bodies. Consider ground contact as a very stiff nonlinear sprint and damper. Takeaway: spring contact is faster than the hard contact model, but must be simulated with a 10 times smaller time-step (otherwise it would sink) and therefore ends up being slower in the end.

Exception handling: robot controller exception will be caught by the robot control framework and sent to the simulator over shared memory.&#x20;

Comms: LCM (cannot handle high bandwidth) over to POSIX shared memory.

Gait: Why galloping is challenging and a good starting point?

* It requires the robot's body to deviate from being level - the body will roll, pitch, and yaw significantly, which requires a fully 3D orientation model.
* It requires a controller or a plan which anticipates the upcoming changes in contact sequence. Without knowledge of the upcoming stepping pattern, it is impossible to effectively stabilize these types of gaits.
* The challenge when only one or two feet are on the ground, where the dynamics of the body are uncontrollable.
* The constraints imposed by contact with the ground. The robot cannot use its feet to pull itself closer to the ground and must apply forces to the ground that do not cause the feet to slip, limiting the wrench which can be applied to the body even further.

Gait definition (in this work): a sequence of contact states. The contact states are defined at evenly spaced time steps, typically spaced around 30 ms apart, because it is fine enough to accurately specify the timing of a gait, but course enough to have a reasonable number of contact states in a plan. $$c[i] \in \{0, 1\}^4$$to indicate the contact states of all four legs at time-step i.

In typical gaits considered in this work, the robot completes one cycle in anywhere from 200 to 500 ms, while each gait cycle is divided into 10 time-steps. The author always includes at least one full cycle of the gait in the controller's plan. However, there may be some gaits which are not periodic or have a tool long period to fully consider in the plan. In these cases, consider a long enough (e.g. 250 ms) plan to anticipate a contact sequence which is not unreasonably long for a high-level planner to generate. Current work with terrain detection in the lab considers the terrain 1 meter in front of the robot, while traveling at around 0.25 m/s, so that the planner would be able to plan for the next 250 ms.

Formulating the problem in MPC:

*



TODO:

The Dynamics algorithm is derived in \[9], and an alternative intuitive way is in Appendix A.

Contact model described in \[3]

\[11] for hardware?

\[20] Running on four legs as though they were one

\[4] Patrick Wensing's state estimator that combines the IMU data with leg kinematics to determine the robot's position and velocity





[Reference Link](https://dspace.mit.edu/handle/1721.1/129877)
