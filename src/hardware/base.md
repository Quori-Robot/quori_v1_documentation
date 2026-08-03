# Mobile Base

Quori's mobile base module — referred to as the **RAMSIS** base in the software — provides omnidirectional ("holonomic") mobility. A differential-drive wheel pair is combined with a continuously rotating turret that carries the mounting plate for the upper body, so the robot can translate in any direction while independently orienting its torso. Caster wheels stabilize the platform.

The turret rotation is also what allows Quori to direct its gaze and camera field of view by turning the whole upper body (see [Head](head.md) and [Sensors for Interaction](hri_sensors.md)).

## Joints

As described in [Robot Description](../software/robot_description.md), the base contributes three continuous joints:

- `l_wheel` - The left wheel joint.
- `r_wheel` - The right wheel joint.
- `turret` - The rotational joint for the mounting plate on top of the base (typically occupied by Quori's torso).

The zero heading of the turret can be adjusted as explained in [Calibration](../software/calibration.md#base).

## Sensors

A 2D LIDAR is mounted in the base and exposed as the `ramsis/base_laser_scanner` frame. It is used by the mapping and navigation stacks (see [Navigation](../software/navigation.md) and the [Testing](../setup/testing.md#lidar) section for how to verify it).

## Electronics and control

The base is driven by a NUCLEO-F303K8 microcontroller running [`quori_base_embedded`](https://github.com/Quori-Robot/quori_base_embedded), with three Pololu Simple Motor Controllers (left wheel, right wheel, and turret). See [Microcode](../software/microcode.md) for flashing instructions and motor-driver settings.

The base connects to the onboard PC over USB and receives 12V power from the robot's main battery through an XT60 connector. It can also be used standalone with your own robot on top: see [Modular Configurations](modular_configurations.md#using-the-base-module-independently) for the power and data requirements.

## Usage

- To drive the base with a gamepad, see [Teleoperation](../software/teleoperation.md).
- To test the base after assembly, see [Testing](../setup/testing.md#base).
- For autonomous navigation, see [Navigation](../software/navigation.md).
