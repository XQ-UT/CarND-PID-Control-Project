# CarND-Controls-PID

## Effect of the P, I, D component of the PID algorithm

The first component of the PID algorithm is the simplest to understand and the most crucial to the performance of the controller. The P stands for proportional. It means that the control variable (steering angle in our case) should be adjusted proportionally to the amount of error in the system. The problem with using a proportional-only controller is that it usually results in a steady-state error. As the error gets smaller and smaller, the result of the error multiplied by the proportional coefficient eventually becomes too small to have any affect on the process variable. 

The integral component of the control algorithm can remove any steady-state error in the system because it accumulates that error over time and compensates for it, rather than just looking at an instantaneous snapshot of the error at one moment in time.

The derivative component is responsible for compensating for sudden changes in the error. The derivative component is mostly useful when the system is already at or near steady state. At steady state, the P and I components are both very small because the error is very small. If the error suddenly increases it takes a while before the P and I components start kicking in again. However, the D component respond to the sudden change in error and begin compensating immediately. For this reason, it is often said that the D component is responsible for compensating for future error; it sees the error changing and tries to prevent it from changing more.

## Hyperparameters (P, I, D coefficients) Tuning
I chose the hyperparameters through manual tuning. Firstly, I choose `Kp = 1.0`, `Ki = 1.0` and `Kd = 1.0`. It turned out that the steering angle is very large and the car always turned to one direction. Then I reduced `Kp` and `Ki`, the car started to kind of staying in the road but it swag back and forth. Then I increased value of `Kd` to compensate the overshoot problem. The final PID hyperparameter is `0.3, 0.001, 10.0`.