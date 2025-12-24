# IMU Read Test

## Purpose
Verify that the IMU can be read reliably and that its outputs change in predictable ways when the robot is moved.

## Expected Physical Behavior
When the robot is held still, accelerometer values should be stable with small noise, and gyroscope values should be near zero.
When the robot is tilted, the accelerometer axis aligned with gravity should change in a consistent direction.
When the robot is rotated, the gyroscope axis aligned with the rotation should change in a consistent direction while moving, then return near zero when stopped.

## What This Test Does
- Initializes the IMU
- Reads raw accelerometer and gyroscope values
- Prints values to Serial at a fixed rate

## What This Test Does Not Do
- Does not drive motors
- Does not compute angles
- Does not perform filtering
- Does not attempt balancing

## Pass Criteria
- Serial output updates consistently
- Values change immediately and repeatably with motion
- At rest: gyro values stay near zero and accel values remain stable
- No lockups, resets, or I2C timeouts during normal handling

## Common Failure Modes
- No output: wiring or wrong I2C pins
- Output frozen: I2C bus hang or incorrect address
- Values are constant: reading the wrong registers or failed init
- Values jump wildly at rest: power noise or bad ground
