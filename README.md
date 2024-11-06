Traffic Light State Machine Specification for Gishushu Intersection

1. Introduction
This document defines the specifications for the Traffic Light State Machine at the Gishushu intersection, which is responsible for managing traffic flow in both the North-South (NS) and East-West (EW) directions. The state machine controls the traffic lights to ensure smooth, safe, and efficient traffic flow by alternating between different traffic light phases.

2. Purpose
The purpose of this state machine is to:

Control the traffic lights at the Gishushu intersection based on a fixed sequence of light phases.
Manage the flow of traffic in a way that ensures the safety of vehicles and pedestrians.
Minimize delays and optimize traffic throughput.

3. Assumptions
The intersection has two directions of traffic flow: North-South (NS) and East-West (EW).
The traffic light system operates in a fixed cycle, alternating between North-South and East-West traffic phases.
Yellow light duration is fixed at 5 seconds as a transitional phase.
Red light duration is implicitly governed by the duration of the opposite green phase.
No simultaneous green lights in both NS and EW directions to prevent accidents.
Pedestrian signals are not included in this simple state machine but can be added as an extension.

5. Components of the State Machine
The traffic light system consists of:

States: Define the various phases of the traffic light (Green, Yellow, Red).
Transitions: Rules that define when the system changes from one state to another.
Timing: Duration of each traffic light phase (Green, Yellow, Red).
Actions: The operations that occur during a state, such as switching the light colors.
States:

NS_GREEN_EW_RED: North-South is Green, East-West is Red.
NS_YELLOW_EW_RED: North-South is Yellow, East-West is Red.
NS_RED_EW_GREEN: North-South is Red, East-West is Green.
NS_RED_EW_YELLOW: North-South is Red, East-West is Yellow.
Transitions:
NS_GREEN_EW_RED → NS_YELLOW_EW_RED: After the green light duration for North-South (typically 30 seconds), transition to Yellow for North-South.
NS_YELLOW_EW_RED → NS_RED_EW_GREEN: After a brief yellow phase for North-South (typically 5 seconds), transition to red for North-South and green for East-West.
NS_RED_EW_GREEN → NS_RED_EW_YELLOW: After the green light duration for East-West (typically 30 seconds), transition to yellow for East-West.
NS_RED_EW_YELLOW → NS_GREEN_EW_RED: After the yellow phase for East-West (typically 5 seconds), transition to green for North-South and red for East-West.
Actions:
Turn on the Green, Yellow, or Red light for the corresponding direction.
Update traffic flow indicators (Green or Red) for vehicles and pedestrians (if extended in the future).

5. State Descriptions and Timing
The state machine operates in a repetitive cycle that alternates between North-South and East-West traffic flows. The states are described in detail below:

State 1: NS_GREEN_EW_RED
Description: The traffic light for North-South direction is Green, and for East-West direction, it is Red.
Duration: Typically 30 seconds (adjustable depending on traffic conditions).
Action:
North-South traffic moves freely.
East-West traffic must stop.

State 2: NS_YELLOW_EW_RED
Description: The traffic light for North-South direction is Yellow, and for East-West direction, it is Red.
Duration: 5 seconds.
Action:
North-South traffic prepares to stop.
East-West traffic remains stopped.

State 3: NS_RED_EW_GREEN
Description: The traffic light for North-South direction is Red, and for East-West direction, it is Green.
Duration: Typically 30 seconds (adjustable depending on traffic conditions).
Action:
East-West traffic moves freely.
North-South traffic must stop.

State 4: NS_RED_EW_YELLOW
Description: The traffic light for North-South direction is Red, and for East-West direction, it is Yellow.
Duration: 5 seconds.
Action:
East-West traffic prepares to stop.
North-South traffic remains stopped.

6. State Transition Diagram (Flow)
The state transition diagram follows a fixed cycle as illustrated below:

NS_GREEN_EW_RED → NS_YELLOW_EW_RED → NS_RED_EW_GREEN → NS_RED_EW_YELLOW → back to NS_GREEN_EW_RED.
The states and transitions can be summarized with these basic timing assumptions:

Green light duration: 30 seconds for NS or EW.
Yellow light duration: 5 seconds for NS or EW.
The total cycle time is typically around 70 seconds (30s + 5s + 30s + 5s), but it can vary depending on real-time traffic flow analysis.

7. Timing and Adjustments
Green Light Duration: 30 seconds for each direction (adjustable depending on real-time traffic).
Yellow Light Duration: 5 seconds for each direction (adjustable if needed).
Cycle Time: The total time for one complete cycle (NS Green → NS Yellow → EW Green → EW Yellow) is 70 seconds (adjustable based on traffic).

9. System Behavior
At the start of the system, North-South traffic will get a Green light and East-West traffic will stop (Red).
After the Green light duration for North-South, the system transitions to Yellow for North-South and remains Red for East-West.
After Yellow for North-South, the system transitions to Red for North-South and Green for East-West.
After the Green light duration for East-West, the system transitions to Yellow for East-West and remains Red for North-South.
The cycle then repeats.

11. Considerations for Future Extensions
Pedestrian Signals: Additional phases could be added to allow pedestrian crossings during red lights.
Emergency Vehicle Preemption: Mechanism to override normal cycles to allow emergency vehicles to pass through the intersection with priority.
Real-time Adjustment: Sensor-based control for adjusting green light durations based on traffic flow in real-time.

13. Conclusion
The Traffic Light State Machine for the Gishushu intersection is designed to control traffic in a safe and efficient manner, alternating between North-South and East-West phases. The fixed light cycles ensure fairness in traffic flow and prevent accidents by never allowing both directions to have a green light simultaneously. The system is modular, so it can be extended to support pedestrian crossings, emergency vehicle preemption, or real-time dynamic control based on traffic conditions.

This system ensures smooth operation at the intersection and improves overall traffic management.

