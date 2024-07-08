# Bring-up Notes

In addition to README, there are additional observations to watch out for.

1. Sim configuration should match the controller. E.g. if controller is launched as `./user/MIT_Controller/mit_ctrl m s`, then before clicking `start` in Sim, you should select `Mini Cheetah` and `Simulator`
2. If you see warning of estop in the console for controller, set cheater\_mode from 0 to 1, control\_mode from 0 to 1, and use\_rc from 1 to 0
3. For some reason (which is different than before), jpos\_ctrl is failing and triggering std::exception for me immediately after JPos\_Controller is launched, but MIT\_Controller still works fine.
