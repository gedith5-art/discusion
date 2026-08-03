1. Competition Task
1.1 The Store That Never Sleeps
At 3:00 a.m. in Astana, the streets are quiet, but a convenience store is already preparing for the morning rush. A late delivery has left four products waiting to be restocked, while another item has been left where it does not belong. The night clerk is closing the shift, so Galbot G1 takes over: identify the waiting products, transport them one by one to the appropriate locations, place the shelf products beside matching stock, and move the misplaced item into the dark wooden return tray while leaving the arranged shelves undisturbed. By opening time, every product must be where customers and staff expect to find it.

1.2 Task Objective
Use Galbot G1 to restock four products from the light-colored wooden product tray into their matching empty shelf locations and transfer one misplaced item from the light-colored wooden product tray to the dark wooden return tray.

At the beginning of each simulation task run (episode):

five movable task objects are located on the light-colored wooden product tray;
four of those objects are shelf products that belong in four currently empty shelf locations;
the fifth object is a misplaced item that belongs in the dark wooden return tray; and
the other products already arranged on the shelf, along with the table, trays, shelf, barriers, and other fixed scene elements, are not task targets.
For each task object, the robot must complete three steps in sequence:

Pick: acquire and lift the correct object from the light-colored wooden product tray;
Navigation: maintain control of the object and use the mobile base to carry it to the correct destination; and
Placement: release the object inside that destination.
The four shelf products go to their matching empty shelf locations, and the misplaced item goes to the dark wooden return tray. Sections 2.2 and 2.3 define the scoring and success criteria for each step.

All five task items are complete when the four shelf products are stably placed in their matching shelf locations and the misplaced item is stably placed in the dark wooden return tray. Non-target products and fixed scene elements should remain undisturbed; interference with them is penalized separately under Section 2.6 and does not change the definition of whether the five task items have been completed.

1.3 Competition Scene
The competition scene consists of the robot, operating area, worktable, two trays with different functions, five task objects, product shelf, and products already stocked on the shelf. The following table explains the purpose of each scene element and the rules for interacting with it.

Official competition scene

Figure 1. Official scene overview: the light-colored wooden product tray and dark wooden return tray are on the table; the target shelf is across the task area.

Scene element	Purpose	Interaction requirement
Galbot G1	The team's wheeled, dual-arm mobile manipulator	Use its sensors for observations and control its base, arms, and grippers to complete the task
Operating area, floor, and barriers	Define the robot's operating space and provide the driving surface	The floor supports normal driving; barriers and other fixed facilities must not be moved or struck severely
Worktable	Supports the two trays	A fixed scene object, not a transport target
Light-colored wooden product tray	Starting area for all five task objects	Pick task objects from it; do not move the tray itself
Dark wooden return tray	Destination for the misplaced item	Receives only the misplaced item; do not move the tray itself
Five task objects	All external objects that the task requires the robot to move	Four shelf products go to the shelf; one misplaced item goes to the return tray
Product shelf	Destination area for the four shelf products	Place each product in its matching empty location; do not move the shelf itself
Products already on the shelf	Show product grouping and form the completed display	They are not task targets; do not pick, move, or knock them over
Galbot G1 Robot
Galbot G1 is the only robot controlled by teams in this challenge. It is a wheeled, dual-arm mobile manipulator: an omnidirectional mobile base moves between the worktable and shelf; the upper-body mechanisms adjust its viewing and manipulation posture; and two arms with grippers grasp, carry, and place objects.

In the following table, a degree of freedom (DoF) is one independently controllable joint motion.

Actuator or movable mechanism	Composition	Role in this task
Omnidirectional mobile base	Four driven omni wheels	Move forward, backward, sideways, and rotate in place while transporting the robot and a grasped object
Articulated torso-support mechanism	Five joints	Adjust upper-body height, forward reach, and manipulation posture
Movable head	Two joints	Adjust head orientation and the head-camera viewpoint
Left and right arms	Seven DoF per arm	Move a gripper to the poses required for grasping, carrying, and placement
Left and right two-finger grippers	One primary open/close control DoF per gripper	Grasp and release task objects; the remaining finger joints follow the coupled opening mechanism
Galbot G1 has multiple sensors. In the simulation challenge, the official baseline uses only the forward head camera by default. Teams that wish to use other sensors must enable, configure, and connect them by following the simulator documentation.

Observation source	Information it can provide	Use in the simulation challenge
Forward head camera	A broad visual observation of the worktable, task objects, driving direction, and shelf	Used by the official Vision Baseline by default; IOAI Lab supports RGB, depth, or RGB-D configurations
Left-wrist camera	A close visual observation of the left gripper and nearby objects	Not used by the baseline by default; teams must configure it themselves in accordance with the simulator documentation
Right-wrist camera	A close visual observation of the right gripper and nearby objects	Not used by the baseline by default; teams must configure it themselves in accordance with the simulator documentation
Chassis LiDAR	Distance or geometric information about the robot's surroundings	Not used by the baseline by default; teams must configure it themselves in accordance with the simulator documentation
Robot proprioceptive state	Control feedback such as joint positions, joint velocities, and mobile-base motion state	Read through the robot-state interfaces described in the simulator documentation; it must not be used to obtain environment or task-object ground truth
The robot composition above is based on the official G1 Robot Assets description, and the camera capabilities are based on the G1 sensor configuration in IOAI Lab. Repository links are provided in Section 5.7.

Any sensor configured by a team must correspond to an onboard sensor on the physical Galbot G1. Its type, mounting position, and sensing capability must not exceed those of the physical robot. External or global-view sensors that do not exist on the physical robot are prohibited, and simulator ground truth must not be used as a substitute for sensor observations. Configuration procedures are governed by the simulator documentation.

Worktable and the Two Trays
The worktable is located on one side of the operating area and supports the light-colored wooden product tray and the dark wooden return tray. The two trays have different colors and functions:

the light-colored wooden product tray is the common starting point for all five task objects: four shelf products and one misplaced item; and
the dark wooden return tray receives only the misplaced item. Do not place any of the four shelf products in it.
Product tray and return tray

Figure 2. The light-colored wooden product tray and the dark wooden return tray.

Five Task Objects
The five task objects are the only external objects in the scene that the robot must intentionally move. Each of the four shelf products corresponds to one empty shelf location; the misplaced item corresponds to the dark wooden return tray. The specific product set and starting positions are generated from the official task configuration, as described in Appendix A.

Example of the five task objects

Figure 3. Example arrangement of the five task objects. All five begin on the light-colored wooden product tray. The product set and starting positions shown are illustrative and are not a fixed official-task configuration.

Product Shelf and Existing Products
At the beginning of a simulation task run, four locations on the shelf are empty. Each empty location belongs to the same product group as one of the four shelf products on the light-colored wooden product tray. That empty location is the product's restocking target. The official task configuration and the grouping of matching products already on the shelf define this relationship; teams do not need to define an additional mapping rule.

Product shelf

Figure 4. Product shelf. Products are grouped by product type; four target positions begin empty.

Task objects and their matching destinations

Figure 5. Red arrows illustrate the destination of each task object: the four shelf products go to empty locations in their matching product groups, while the misplaced item goes into the dark wooden return tray. The product combination shown is illustrative; the team's official configuration determines the competition task.

Products already present on the shelf are scene objects, not task targets. Do not pick, move, or knock them over.

Operating Area and Fixed Scene Objects
The floor is the normal driving surface for the mobile base, and the barriers mark the competition area. The worktable, both trays, shelf, barriers, and other fixed facilities form the task environment. They are not transport targets and must not be intentionally moved, dismantled, or used to bypass the required task flow.

1.4 Required Outcomes at a Glance
Task item	Starting point	Required destination
Shelf product 1	Light-colored wooden product tray	Its matching empty shelf location
Shelf product 2	Light-colored wooden product tray	Its matching empty shelf location
Shelf product 3	Light-colored wooden product tray	Its matching empty shelf location
Shelf product 4	Light-colored wooden product tray	Its matching empty shelf location
Misplaced item	Light-colored wooden product tray	Dark wooden return tray
2. Scoring Rules
2.1 Score Structure
The final score combines base points, the time bonus, and penalties:

Score category	Maximum
Five object-transfer tasks	100 points
Time bonus available only after all five task objects are complete and continuously decaying from the start of timing	20 points
Maximum total score	120 points
The scoring system has a theoretical maximum of 120 points. The time bonus starts at 20 points when t = 0 and begins decaying as soon as the scored episode starts. Because completing the task necessarily requires t > 0, no actual run can receive a 20.00-point time bonus or reach 120.00 points. Section 2.4 gives the calculation.

The five task objects can earn up to 100 base points in total. Ordinary penalties are subtracted from earned base points, with the base-task score floored at 0; an eligible time bonus is then added. If a serious safety incident defined in Section 2.6 occurs, the final score for that run is 0; neither base points nor a time bonus are retained.

ordinary case: final_score = max(0, base_points - deductions) + time_bonus
serious safety incident: final_score = 0
Deductions enter the formula as a positive total. For example, one -3 penalty adds 3 to that total.

Official scoring is based on the task performance observed when the organizers run the final submitted solution. Internal logs or structured JSON result files produced by an official baseline are useful for development, but they are not the official competition score.
