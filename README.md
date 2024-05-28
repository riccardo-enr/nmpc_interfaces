# nmpc_interfaces

## Description
`nmpc_interfaces` is a package designed for Nonlinear Model Predictive Control (NMPC) applications. It provides message definitions for reference inputs necessary for NMPC algorithms, typically used in controlling unmanned aerial vehicles (UAVs).

## Message Definition: `nmpc_ref`

This message contains the following fields:

- `std_msgs/Header header`: Standard ROS message header.
- `geometry_msgs/Pose pose`: Pose of the UAV, which includes position (x, y, z) and orientation (represented as a quaternion).
- `geometry_msgs/Twist twist`: Twist of the UAV, which includes linear velocities (v_x, v_y, v_z) and angular velocities (p, q, r).

### State Vector

The state vector for the NMPC reference is defined as follows:

$$
xref = \begin{bmatrix}
x \\ 
y \\ 
z \\ 
v_x \\ 
v_y \\ 
v_z \\ 
q_w \\ 
q_x \\ 
q_y \\ 
q_z \\ 
p \\ 
q \\ 
r 
\end{bmatrix}
$$

Where:
- \( x, y, z \): Position coordinates
- \( v_x, v_y, v_z \): Linear velocities
- \( qw, qx, qy, qz \): Quaternion components representing orientation
- \( p, q, r \): Angular velocities (roll, pitch, and yaw rates)

### Message organization

```mermaid
graph LR
    A[PoseStamped] --> B[x, y, z]
    A[PoseStamped] --> C[qw, qx, qy, qz]
    D[Twist] --> E[vx, vy, vz]
    D[Twist] --> F[p, q, r]
