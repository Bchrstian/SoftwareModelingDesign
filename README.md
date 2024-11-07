# Gishushu Traffic Lights State Machine

This README file documents the state machine for the Gishushu intersection's traffic light system, as represented in the provided diagram. The intersection is controlled by four main traffic lights, each with three states (Red, Yellow, and Green) to manage traffic flow efficiently.

## Traffic Lights

The Gishushu intersection has four main traffic lights:

1. **East_West_Light**
2. **West_East_Light**
3. **North_South_Light**
4. **South_East_Light**

Each light follows a sequence of states: **Green**, **Yellow**, and **Red**.

### State Definitions

- **Green**: Allows vehicles to pass in the direction indicated by the light.
- **Yellow**: Signals that the light is about to turn red, prompting vehicles to prepare to stop.
- **Red**: Vehicles must stop and wait for the next Green signal.

## State Transitions

The traffic lights change states in a defined sequence to ensure a smooth flow of traffic through the intersection. Each light’s state changes are triggered by a **timer** that, when expired, advances the state from Green to Yellow, Yellow to Red, and so forth.

### State Transition Flow

1. **East_West_Light** begins with:

   - **Red** -> **Green** -> **Yellow** -> **Red**
   - **Transition**: Once the **East_West_Light** turns Yellow and then Red, it triggers **North_South_Light** to turn Green.

2. **North_South_Light** then goes through its sequence:

   - **Red** -> **Green** -> **Yellow** -> **Red**
   - **Transition**: When **North_South_Light** completes its cycle, it passes control to **South_East_Light**.

3. **South_East_Light** sequence:

   - **Red** -> **Green** -> **Yellow** -> **Red**
   - **Transition**: At the end of its cycle, **South_East_Light** turns Red and allows **West_East_Light** to turn Green.

4. **West_East_Light** sequence:
   - **Red** -> **Green** -> **Yellow** -> **Red**
   - **Transition**: Once **West_East_Light** completes its Yellow to Red transition, control is returned to **East_West_Light**, restarting the sequence.

### Diagram Key

- **Timer Expired**: Each state transition is initiated by a timer expiration.
- **To Next Light**: After completing a full sequence (Green -> Yellow -> Red), each light hands control over to the next light in the specified sequence.

### Transition Summary

| Traffic Light     | Initial State | Transition Order       | Next Light Triggered      |
| ----------------- | ------------- | ---------------------- | ------------------------- |
| East_West_Light   | Red           | Green -> Yellow -> Red | North_South_Light         |
| North_South_Light | Red           | Green -> Yellow -> Red | South_East_Light          |
| South_East_Light  | Red           | Green -> Yellow -> Red | West_East_Light           |
| West_East_Light   | Red           | Green -> Yellow -> Red | East_West_Light (restart) |

### Transition Narration

- **Step 1**: **East_West_Light** turns Green, allowing traffic to pass. After a timer expires, it changes to Yellow, then Red.
- **Step 2**: **North_South_Light** turns Green after East_West_Light goes Red, allowing traffic in the north-south direction.
- **Step 3**: **South_East_Light** takes over once North_South_Light completes its cycle, switching to Green.
- **Step 4**: **West_East_Light** becomes Green after South_East_Light's cycle, allowing west-east traffic.
- **Repeat**: This sequence repeats in a continuous loop to manage the intersection.
