# Tuning

TODO - INTRODUCTIONARY INFO HERE
## Updating Drive Classes
### Step 1 - Updating Motor Names

Ensure that in the `TuningOpModes.java` class the `DRIVE_CLASS` variable is updated to match either MecanumDrive.class or TankDrive.class
Open either `MecanumDrive.java` or `TankDrive.java` depending on your bot in Android studio under the `teamcode` package.
**If using MecanumDrive:** Ensure that when configuring the hardware the motor names are `"leftFront"`,  `"leftBack"`, `"rightBack"`, `"rightFront"`

TODO - IMAGE OF INITIALIZATION

**If using TankDrive:** TODO

**If using dead wheels:** Make sure that your configuration has odometry modules plugged in the motor encoder ports, and the corresponding names of par0, par1 and perp should be modified in the `ThreeDeadWheelLocalizer.java` or `TwoDeadWheelLocalizer.java`.

For more information see [this page](https://ftc-docs.firstinspires.org/en/latest/hardware_and_software_configuration/configuring/index.html)

### Step 2 - Updating IMU setup according to orientation

TODO - PICTURE OF WHERE IMU IS INITIALIZED

Locate where the IMU is initialized in the drive class.
Update the `RevHubOrientationOnRobot.LogoFacingDirection.UP` parameter based on how the Rev Control Hub is oriented in your robot. Change to UP / DOWN / LEFT / RIGHT / FORWARD / BACKWARD as in robot
Update the `RevHubOrientationOnRobot.UsbFacingDirection.FORWARD` parameter based on how the USB port of the Rev Control Hub is oriented in your robot. Change to UP / DOWN / LEFT / RIGHT / FORWARD / BACKWARD as in robot

[This page](https://ftc-docs.firstinspires.org/en/latest/programming_resources/imu/imu.html?highlight=imu#physical-hub-mounting) has visuals describing which orientation corresponds to which direction.

### Step 3 - Selecting Localizer Based Tracking Systems
The main built-in localizers are Drive encoders, Two Dead Wheel, and Three Dead Wheel.
* **Drive Encoder**: This is the default selection. The IMU is used alongside the drive encoders to improve the heading. The code should look like `localizer = new DriveLocalizer();` 
* **Two Dead Wheel**: The localizer should look like `localizer = to new TwoDeadWheelLocalizer(hardwareMap, imu, PARAMS.inPerTick).` The parallel encoder that is forward facing should be named `"par"` and the perpendicular encoder should be named `"perp"`.
* **Three Dead Wheel**: The process is similar for three dead wheels. The localizer should be `localizer = to new ThreeDeadWheelLocalizer(hardwareMap, PARAMS.inPerTick).` The two parallel encoders should be named `"par0"` and `"par1"` respectively. The perpendicular encoder should be named `"perp"`.

Download the code on to the control hub.

### Step 4 - Calibrating motor movement direction

::: warning The robot is needed for this step, please ensure that battery level is over 12.5 V :::

On the driver hub



