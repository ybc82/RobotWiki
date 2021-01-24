---
description: 代码阅读笔记
---

# Stanford Pupper

## Summary

Stanford Pupper 一方面使用的是舵机而非FOC控制的电机，另一方面又有完整的每条腿3个关节的配置，有完整的自由度用于四足机器人的控制。

代码框架已经在git上有框图给出了说明。算法实现是参照经典作品Legged Robots That Balance。在了解了书中的对多足机器人的控制框架后，摘录笔记如下，一是梳理几何关系帮助理解基本物理概念，二是打通代码中机器人变量与算法间的关系。总的来说项目作者写的还是挺清楚的。

{% file src="../.gitbook/assets/pupper-kinematics.pptx" caption="Pupper Kinematics" %}

另外，作者在处理Kinematics的时候，没有算Jacobian，而是在位移这个层面算几何关系，然后做差分，得到Jacobian等效的效果（当然差分总有差分的坏处）。不知是有什么好处还是单纯的想算得简单一点。

## References

1. Pupper Github page. [https://github.com/stanfordroboticsclub/StanfordQuadruped](https://github.com/stanfordroboticsclub/StanfordQuadruped)
2. Kau, Nathan, et al. "Woofer and Pupper: Low-Cost Open-Source Quadrupeds for Research and Education." [\[Pdf Link\]](https://www.seas.upenn.edu/~posa/DynamicWalking2020/695-1037-1-RV.pdf)





