# Standing

### Keywords

Inverted Pendulum Model \(IPM\)   
Ankle Strategy, COP, ZMP and Polygon of Support   
Hip Strategy and Flywheel Extension   
Stepping Strategy and Linear Inverted Pendulum Model \(LIPM\)   
Capture Points in 2D  
Bilateral Leg Loading

## _Human balance and posture control during standing and walking_

This is a review paper on human balance control. The purpose of this review is "to introduce the reader to the basic anatomy, mechanics, and neuromuscular control that is seen in the current literature related to balance control".

This paper was written in 1995 \(Canada\), yet already considering problems in dealing with aging population.

### Definitions

These terms are different:

* COM: Center of mass
* COG: The vertical projection of the COM onto the ground
* COP: Center of Pressure. This represents the point location of the VERTICAL ground reaction force vector. Unless the system is static, it doesn't have to be the same as COG.

And by modeling, we find out that the difference between the COP and COM is proportional to the horizontal acceleration of the COM. \(Inverted pendulum model\)

## _Capture Point: A Step toward Humanoid Push Recovery \*_

Assumption: $$z \equiv z_0$$，at least within second order. Consider this as very motion in z-axis.

Thus, the Linear Inverted Pendulum Plus Flywheel Model looks like a LIPM plus a joint servo model.

When computing the Capture Point: 

* Step I, calculate without controlling the flywheel, i.e. $$\tau_h = 0$$. Use Orbital Energy for analysis, which remains CONSTANT within one step. Orbital Energy of zero leads to a stable step. So, $$x_{capture}=\dot{x} \sqrt{\frac{z_0}{g}}$$. _When the flywheel is made available, this point will grow to Capture Region_. The optimal trajectory turns into an optimal region.

Ground reaction forces are considered, and different from normal LIPM. Friction Cone is used to provide the condition for optimization.

Dimensional analysis: it simplifies the math and shows us the remaining parameters that are critical to the dynamics of the system.

What we learned for biped design consideration: "Increasing the amount of available non-dimensional torque, or rotation angle, increases the size of the Capture Region. However, if one of the values is fixed, there is diminishing returns in increasing the other. In addition, the maximum torque must not exceed the the value that would cause slipping."



