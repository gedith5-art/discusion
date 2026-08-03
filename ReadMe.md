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


| | | | | | | | |--_sn_UnknowVisual_preset_6_horn_21_box.stl
| | | | | | | | |--_sn_cocacola_prim_3_cyl.stl
| | | | | | | | |--_sn_cocacola_prim_1_cyl.stl
| | | | | | | | |--_sn_UnknowVisual_preset_6_horn_16_box.stl
| | | | | | | | |--_sn_UnknowVisual_preset_6_horn_10_box.stl
| | | | | | | | |--_sn_UnknowVisual_preset_6_horn_18_box.stl
| | | | | | | | |--_sn_UnknowVisual_preset_6_horn_19_box.stl
| | | | | | | | |--_sn_UnknowVisual_preset_6_horn_11_box.stl
| | | | | | | | |--_sn_UnknowVisual_preset_6_horn_9_box.stl
| | | | | | | | |--_sn_UnknowVisual_preset_6_horn_12_box.stl
| | | | | | | | |--_sn_cocacola_prim_5_cyl.stl
| | | | | | | | |--_sn_UnknowVisual_preset_6_horn_20_box.stl
| | | | | | | | |--_sn_UnknowVisual_preset_6_horn_6_box.stl
| | | | | | | | |--_sn_UnknowVisual_preset_6_horn_2_box.stl
| | | | | | | | |--_sn_UnknowVisual_preset_6_horn_14_box.stl
| | | | | | | | |--_sn_UnknowVisual_preset_6_horn_13_box.stl
| | | | | | | | |--_sn_UnknowVisual_preset_6_horn_22_box.stl
| | | | | | | |--manual_collision.json
| | | | | | | |--coacd
| | | | | | | | |--coacd.json
| | | | | | | |--primitive
| | | | | | | | |--primitive.json
| | | | | | | | |--convex_decomposition
| | | | | | | | | |--convex_decomposition.stl
| | | | | | | | |--mesh
| | | | | | | | | |--_sn_UnknowVisual_preset_6_horn.stl
| | | | | | | | | |--_sn_UnknowVisual_preset_6_horn_3_box.stl
| | | | | | | | | |--_sn_cocacola_prim_4_cyl.stl
| | | | | | | | | |--_sn_UnknowVisual_preset_6_horn_24_box.stl
| | | | | | | | | |--_sn_UnknowVisual_preset_6_horn_5_box.stl
| | | | | | | | | |--_sn_UnknowVisual_preset_6_horn_17_box.stl
| | | | | | | | | |--_sn_UnknowVisual_preset_6_horn_23_box.stl
| | | | | | | | | |--_sn_UnknowVisual_preset_6_horn_7_box.stl
| | | | | | | | | |--_sn_cocacola_prim_2_cyl.stl
| | | | | | | | | |--_sn_UnknowVisual_preset_6_horn_15_box.stl
| | | | | | | | | |--_sn_UnknowVisual_preset_6_horn_4_box.stl
| | | | | | | | | |--_sn_UnknowVisual_preset_6_horn_1_box.stl
| | | | | | | | | |--_sn_UnknowVisual_preset_6_horn_8_box.stl
| | | | | | | | | |--_sn_UnknowVisual_preset_6_horn_21_box.stl
| | | | | | | | | |--_sn_cocacola_prim_3_cyl.stl
| | | | | | | | | |--_sn_cocacola_prim_1_cyl.stl
| | | | | | | | | |--_sn_UnknowVisual_preset_6_horn_16_box.stl
| | | | | | | | | |--_sn_UnknowVisual_preset_6_horn_10_box.stl
| | | | | | | | | |--_sn_UnknowVisual_preset_6_horn_18_box.stl
| | | | | | | | | |--_sn_UnknowVisual_preset_6_horn_19_box.stl
| | | | | | | | | |--_sn_UnknowVisual_preset_6_horn_11_box.stl
| | | | | | | | | |--_sn_UnknowVisual_preset_6_horn_9_box.stl
| | | | | | | | | |--_sn_UnknowVisual_preset_6_horn_12_box.stl
| | | | | | | | | |--_sn_cocacola_prim_5_cyl.stl
| | | | | | | | | |--_sn_UnknowVisual_preset_6_horn_20_box.stl
| | | | | | | | | |--_sn_UnknowVisual_preset_6_horn_6_box.stl
| | | | | | | | | |--_sn_UnknowVisual_preset_6_horn_2_box.stl
| | | | | | | | | |--_sn_UnknowVisual_preset_6_horn_14_box.stl
| | | | | | | | | |--_sn_UnknowVisual_preset_6_horn_13_box.stl
| | | | | | | | | |--_sn_UnknowVisual_preset_6_horn_22_box.stl
| | | | | | | | |--primfit_mesh
| | | | | | | | | |--cocacola_collision_001.stl
| | | | | | | | | |--_sn_UnknowVisual_preset_6_horn_collision_020.stl
| | | | | | | | | |--_sn_UnknowVisual_preset_6_horn_collision_010.stl
| | | | | | | | | |--_sn_UnknowVisual_preset_6_horn_collision_022.stl
| | | | | | | | | |--_sn_UnknowVisual_preset_6_horn_collision_013.stl
| | | | | | | | | |--cocacola_collision_000.stl
| | | | | | | | | |--_sn_UnknowVisual_preset_6_horn_collision_018.stl
| | | | | | | | | |--_sn_UnknowVisual_preset_6_horn_collision_016.stl
| | | | | | | | | |--_sn_UnknowVisual_preset_6_horn_collision_007.stl
| | | | | | | | | |--_sn_UnknowVisual_preset_6_horn_collision_011.stl
| | | | | | | | | |--cocacola_collision_003.stl
| | | | | | | | | |--_sn_UnknowVisual_preset_6_horn_collision_009.stl
| | | | | | | | | |--cocacola_collision_002.stl
| | | | | | | | | |--_sn_UnknowVisual_preset_6_horn_collision_015.stl
| | | | | | | | | |--_sn_UnknowVisual_preset_6_horn_collision_021.stl
| | | | | | | | | |--_sn_UnknowVisual_preset_6_horn_collision_003.stl
| | | | | | | | | |--cocacola_collision_004.stl
| | | | | | | | | |--_sn_UnknowVisual_preset_6_horn_collision_014.stl
| | | | | | | | | |--_sn_UnknowVisual_preset_6_horn_collision_008.stl
| | | | | | | | | |--_sn_UnknowVisual_preset_6_horn_collision_017.stl
| | | | | | | | | |--_sn_UnknowVisual_preset_6_horn_collision_001.stl
| | | | | | | | | |--_sn_UnknowVisual_preset_6_horn_collision_006.stl
| | | | | | | | | |--_sn_UnknowVisual_preset_6_horn_collision_004.stl
| | | | | | | | | |--_sn_UnknowVisual_preset_6_horn_collision_005.stl
| | | | | | | | | |--_sn_UnknowVisual_preset_6_horn_collision_002.stl
| | | | | | | | | |--_sn_UnknowVisual_preset_6_horn_collision_023.stl
| | | | | | | | | |--_sn_UnknowVisual_preset_6_horn_collision_000.stl
| | | | | | | | | |--_sn_UnknowVisual_preset_6_horn_collision_012.stl
| | | | | | | | | |--_sn_UnknowVisual_preset_6_horn_collision_019.stl
| | | | | | | | |--primitive.xml
| | | | | | | |--pengzhuangti.blend
| | | | | |--usd_layers
| | | | | | |--collision_layer
| | | | | | | |--manual_collision_layer.usda
| | | | | | |--base_usd
| | | | | | | |--shaders
| | | | | | | | |--WA.mdl
| | | | | | | | |--TPL.mdl
| | | | | | | |--textures
| | | | | | | | |--kekoukelehantangkele300ml_Basecolor.png
| | | | | | | | |--kekoukelehantangkele300ml_Normal.png
| | | | | | | |--base.usd
| | | | | | |--articulation_layer
| | | | | | |--phys_layer
| | | | | | | |--massFirst_phys_layer.usda
| | | | | |--thumbnail.png
| | | | | |--simready.usda
| | | | | |--vlm_annotation
| | | | | | |--annotation.json
| | | | |--art_source
| | | | | |--manual_source
| | | | | | |--measured.json
| | | | | | |--collision
| | | | | | | |--convex_decomposition
| | | | | | | |--manual_collision.xml
| | | | | | | |--meshes
| | | | | | | | |--_sn_UnknowVisual_preset_6_horn.stl
| | | | | | | | |--_sn_UnknowVisual_preset_6_horn_3_box.stl
| | | | | | | | |--_sn_cocacola_prim_4_cyl.stl
| | | | | | | | |--_sn_UnknowVisual_preset_6_horn_24_box.stl
| | | | | | | | |--_sn_UnknowVisual_preset_6_horn_5_box.stl
| | | | | | | | |--_sn_UnknowVisual_preset_6_horn_17_box.stl
| | | | | | | | |--_sn_UnknowVisual_preset_6_horn_23_box.stl
| | | | | | | | |--_sn_UnknowVisual_preset_6_horn_7_box.stl
| | | | | | | | |--_sn_cocacola_prim_2_cyl.stl
| | | | | | | | |--_sn_UnknowVisual_preset_6_horn_15_box.stl
| | | | | | | | |--_sn_UnknowVisual_preset_6_horn_4_box.stl
| | | | | | | | |--_sn_UnknowVisual_preset_6_horn_1_box.stl
| | | | | | | | |--_sn_UnknowVisual_preset_6_horn_8_box.stl
| | | | | | | | |--_sn_UnknowVisual_preset_6_horn_21_box.stl
| | | | | | | | |--_sn_cocacola_prim_3_cyl.stl
| | | | | | | | |--_sn_cocacola_prim_1_cyl.stl
| | | | | | | | |--_sn_UnknowVisual_preset_6_horn_16_box.stl
| | | | | | | | |--_sn_UnknowVisual_preset_6_horn_10_box.stl
| | | | | | | | |--_sn_UnknowVisual_preset_6_horn_18_box.stl
| | | | | | | | |--_sn_UnknowVisual_preset_6_horn_19_box.stl
| | | | | | | | |--_sn_UnknowVisual_preset_6_horn_11_box.stl
| | | | | | | | |--_sn_UnknowVisual_preset_6_horn_9_box.stl
| | | | | | | | |--_sn_UnknowVisual_preset_6_horn_12_box.stl
| | | | | | | | |--_sn_cocacola_prim_5_cyl.stl
| | | | | | | | |--_sn_UnknowVisual_preset_6_horn_20_box.stl
| | | | | | | | |--_sn_UnknowVisual_preset_6_horn_6_box.stl
| | | | | | | | |--_sn_UnknowVisual_preset_6_horn_2_box.stl
| | | | | | | | |--_sn_UnknowVisual_preset_6_horn_14_box.stl
| | | | | | | | |--_sn_UnknowVisual_preset_6_horn_13_box.stl
| | | | | | | | |--_sn_UnknowVisual_preset_6_horn_22_box.stl
| | | | | | | |--manual_collision.json
| | | | | | | |--coacd
| | | | | | | | |--coacd.json
| | | | | | | |--primitive
| | | | | | | | |--primitive.json
| | | | | | | | |--convex_decomposition
| | | | | | | | | |--convex_decomposition.stl
| | | | | | | | |--mesh
| | | | | | | | | |--_sn_UnknowVisual_preset_6_horn.stl
| | | | | | | | | |--_sn_UnknowVisual_preset_6_horn_3_box.stl
| | | | | | | | | |--_sn_cocacola_prim_4_cyl.stl
| | | | | | | | | |--_sn_UnknowVisual_preset_6_horn_24_box.stl
| | | | | | | | | |--_sn_UnknowVisual_preset_6_horn_5_box.stl
| | | | | | | | | |--_sn_UnknowVisual_preset_6_horn_17_box.stl
| | | | | | | | | |--_sn_UnknowVisual_preset_6_horn_23_box.stl
| | | | | | | | | |--_sn_UnknowVisual_preset_6_horn_7_box.stl
| | | | | | | | | |--_sn_cocacola_prim_2_cyl.stl
| | | | | | | | | |--_sn_UnknowVisual_preset_6_horn_15_box.stl
| | | | | | | | | |--_sn_UnknowVisual_preset_6_horn_4_box.stl
| | | | | | | | | |--_sn_UnknowVisual_preset_6_horn_1_box.stl
| | | | | | | | | |--_sn_UnknowVisual_preset_6_horn_8_box.stl
| | | | | | | | | |--_sn_UnknowVisual_preset_6_horn_21_box.stl
| | | | | | | | | |--_sn_cocacola_prim_3_cyl.stl
| | | | | | | | | |--_sn_cocacola_prim_1_cyl.stl
| | | | | | | | | |--_sn_UnknowVisual_preset_6_horn_16_box.stl
| | | | | | | | | |--_sn_UnknowVisual_preset_6_horn_10_box.stl
| | | | | | | | | |--_sn_UnknowVisual_preset_6_horn_18_box.stl
| | | | | | | | | |--_sn_UnknowVisual_preset_6_horn_19_box.stl
| | | | | | | | | |--_sn_UnknowVisual_preset_6_horn_11_box.stl
| | | | | | | | | |--_sn_UnknowVisual_preset_6_horn_9_box.stl
| | | | | | | | | |--_sn_UnknowVisual_preset_6_horn_12_box.stl
| | | | | | | | | |--_sn_cocacola_prim_5_cyl.stl
| | | | | | | | | |--_sn_UnknowVisual_preset_6_horn_20_box.stl
| | | | | | | | | |--_sn_UnknowVisual_preset_6_horn_6_box.stl
| | | | | | | | | |--_sn_UnknowVisual_preset_6_horn_2_box.stl
| | | | | | | | | |--_sn_UnknowVisual_preset_6_horn_14_box.stl
| | | | | | | | | |--_sn_UnknowVisual_preset_6_horn_13_box.stl
| | | | | | | | | |--_sn_UnknowVisual_preset_6_horn_22_box.stl
| | | | | | | | |--primfit_mesh
| | | | | | | | | |--cocacola_collision_001.stl
| | | | | | | | | |--_sn_UnknowVisual_preset_6_horn_collision_020.stl
| | | | | | | | | |--_sn_UnknowVisual_preset_6_horn_collision_010.stl
| | | | | | | | | |--_sn_UnknowVisual_preset_6_horn_collision_022.stl
| | | | | | | | | |--_sn_UnknowVisual_preset_6_horn_collision_013.stl
| | | | | | | | | |--cocacola_collision_000.stl
| | | | | | | | | |--_sn_UnknowVisual_preset_6_horn_collision_018.stl
| | | | | | | | | |--_sn_UnknowVisual_preset_6_horn_collision_016.stl
| | | | | | | | | |--_sn_UnknowVisual_preset_6_horn_collision_007.stl
| | | | | | | | | |--_sn_UnknowVisual_preset_6_horn_collision_011.stl
| | | | | | | | | |--cocacola_collision_003.stl
| | | | | | | | | |--_sn_UnknowVisual_preset_6_horn_collision_009.stl
| | | | | | | | | |--cocacola_collision_002.stl
| | | | | | | | | |--_sn_UnknowVisual_preset_6_horn_collision_015.stl
| | | | | | | | | |--_sn_UnknowVisual_preset_6_horn_collision_021.stl
| | | | | | | | | |--_sn_UnknowVisual_preset_6_horn_collision_003.stl
| | | | | | | | | |--cocacola_collision_004.stl
| | | | | | | | | |--_sn_UnknowVisual_preset_6_horn_collision_014.stl
| | | | | | | | | |--_sn_UnknowVisual_preset_6_horn_collision_008.stl
| | | | | | | | | |--_sn_UnknowVisual_preset_6_horn_collision_017.stl
| | | | | | | | | |--_sn_UnknowVisual_preset_6_horn_collision_001.stl
| | | | | | | | | |--_sn_UnknowVisual_preset_6_horn_collision_006.stl
| | | | | | | | | |--_sn_UnknowVisual_preset_6_horn_collision_004.stl
| | | | | | | | | |--_sn_UnknowVisual_preset_6_horn_collision_005.stl
| | | | | | | | | |--_sn_UnknowVisual_preset_6_horn_collision_002.stl
| | | | | | | | | |--_sn_UnknowVisual_preset_6_horn_collision_023.stl
| | | | | | | | | |--_sn_UnknowVisual_preset_6_horn_collision_000.stl
| | | | | | | | | |--_sn_UnknowVisual_preset_6_horn_collision_012.stl
| | | | | | | | | |--_sn_UnknowVisual_preset_6_horn_collision_019.stl
| | | | | | | | |--primitive.xml
| | | | | | | |--pengzhuangti.blend
| | | | | |--shaders
| | | | | | |--WA.mdl
| | | | | | |--TPL.mdl
| | | | | |--thumbnail.png
| | | | | |--cocacola.blend
| | | | | |--textures
| | | | | | |--cocacola_Normal.png
| | | | | | |--cocacola_Basecolor.png
| | | | | |--cocacola.usd
| | |--final
| | | |--floor.usda
| | | |--textures
| | | | |--wall_south_long_4k_outer_z180.png
| | | | |--wall_west_short_4k_outer_z180.png
| | | | |--carpet_roughness.png
| | | | |--wall_east_short_4k_outer_z180.png
| | | | |--wall_north_long_4k.png
| | | | |--wall_east_short_4k.png
| | | | |--wall_north_long_4k_outer_z180.png
| | | | |--carpet_normal_gl.png
| | | | |--wall_south_long_4k.png
| | | | |--carpet_ao.png
| | | | |--carpet_basecolor.png
| | | | |--wall_west_short_4k.png
| | | |--final.usda
| | |--trays
| | | |--Tray01
| | | | |--simready_asset
| | | | | |--thumbnail.png
| | | | | |--model
| | | | | | |--obj
| | | | | | | |--normalized.obj
| | | | | | | |--normalized.mtl
| | | | | | |--usd
| | | | | | | |--usd_layers
| | | | | | | | |--collision_layer
| | | | | | | | | |--manual_collision_layer.usd
| | | | | | | | |--phys_layer
| | | | | | | | | |--massFirst_phys_layer.usd
| | | | | | | |--base_usd
| | | | | | | | |--textures
| | | | | | | | | |--Wood052_1K-PNG_Roughness.png
| | | | | | | | | |--Wood052_1K-PNG_Color.png
| | | | | | | | | |--Wood052_1K-PNG_NormalGL.png
| | | | | | | | |--base.usd
| | | | | | | |--simready.usd
| | | | | | |--hull
| | | | | | | |--convex_hull.stl
| | | | | | |--decomposition
| | | | | | | |--convex_decomposition.stl
| | | | | | |--mjcf
| | | | | | | |--mjcf_simready.xml
| | | | | | | |--mjcf_simready
| | | | | | | | |--materials
| | | | | | | | |--meshes
| | | | | | | | | |--stl
| | | | | | | | | | |--SM_sn_Tray01_prim_10_box.stl
| | | | | | | | | | |--SM_sn_Tray01_prim_6_box.stl
| | | | | | | | | | |--SM_sn_Tray01_prim_8_box.stl
| | | | | | | | | | |--SM_sn_Tray01_prim_7_box.stl
| | | | | | | | | | |--SM_sn_Tray01_prim_9_box.stl
| | | | | | | | |--textures
| | | | | |--config.json
| | | | |--simready_source
| | | | | |--manual_source
| | | | | | |--collision
| | | | | | | |--Tray01.blend
| | | | | | | |--manual_collision.xml
| | | | | | | |--Tray02.blend
| | | | | | | |--Tray02.blend1
| | | | | | | |--meshes
| | | | | | | | |--sn_Tray01_prim_9_box.stl
| | | | | | | | |--sn_Tray01_prim_10_box.stl
| | | | | | | | |--sn_Tray01_prim_8_box.stl
| | | | | | | | |--sn_Tray01_prim_6_box.stl
| | | | | | | | |--sn_Tray01_prim_7_box.stl
| | | | | | | |--manual_collision.json
| | | | | | | |--manual_collision_blender.json
| | | | | | | |--Tray01.blend1
| | | | | |--usd_layers
| | | | | | |--collision_layer
| | | | | | | |--manual_collision_layer.usda
| | | | | | |--base_usd
| | | | | | | |--textures
| | | | | | | | |--Wood052_1K-PNG_Roughness.png
| | | | | | | | |--Wood052_1K-PNG_Color.png
| | | | | | | | |--Wood052_1K-PNG_NormalGL.png
| | | | | | | |--base.usd
| | | | | | |--articulation_layer
| | | | | | |--phys_layer
| | | | | | | |--massFirst_phys_layer.usda
| | | | | |--thumbnail.png
| | | | | |--simready.usda
| | | | | |--vlm_annotation
| | | | | | |--annotation.json
| | | | |--art_source
| | | | | |--Tray01.blend
| | | | | |--manual_source
| | | | | | |--collision
| | | | | | | |--Tray01.blend
| | | | | | | |--manual_collision.xml
| | | | | | | |--Tray02.blend
| | | | | | | |--Tray02.blend1
| | | | | | | |--meshes
| | | | | | | | |--sn_Tray01_prim_9_box.stl
| | | | | | | | |--sn_Tray01_prim_10_box.stl
| | | | | | | | |--sn_Tray01_prim_8_box.stl
| | | | | | | | |--sn_Tray01_prim_6_box.stl
| | | | | | | | |--sn_Tray01_prim_7_box.stl
| | | | | | | |--manual_collision.json
| | | | | | | |--manual_collision_blender.json
| | | | | | | |--Tray01.blend1
| | | | | |--Tray01.usd
| | | | | |--textures
| | | | | | |--Wood052_1K-PNG_Roughness.png
| | | | | | |--Wood052_1K-PNG_Color.png
| | | | | | |--Wood052_1K-PNG_NormalGL.png
| | | | | |--Tray01_thumbnail.png
| | | |--Tray02
| | | | |--simready_asset
| | | | | |--thumbnail.png
| | | | | |--model
| | | | | | |--obj
| | | | | | | |--normalized.obj
| | | | | | | |--normalized.mtl
| | | | | | |--usd
| | | | | | | |--usd_layers
| | | | | | | | |--collision_layer
| | | | | | | | | |--manual_collision_layer.usd
| | | | | | | | |--phys_layer
| | | | | | | | | |--massFirst_phys_layer.usd
| | | | | | | |--base_usd
| | | | | | | | |--textures
| | | | | | | | | |--MuWen_Roughness.png
| | | | | | | | | |--MuWen_Normal.png
| | | | | | | | | |--MuWen_Color.png
| | | | | | | | |--base.usd
| | | | | | | |--simready.usd
| | | | | | |--hull
| | | | | | | |--convex_hull.stl
| | | | | | |--decomposition
| | | | | | | |--convex_decomposition.stl
| | | | | | |--mjcf
| | | | | | | |--mjcf_simready.xml
| | | | | | | |--mjcf_simready
| | | | | | | | |--materials
| | | | | | | | |--meshes
| | | | | | | | | |--stl
| | | | | | | | | | |--SM_sn_Tray02_prim_8_box.stl
| | | | | | | | | | |--SM_sn_Tray02_prim_7_box.stl
| | | | | | | | | | |--SM_sn_Tray02_prim_9_box.stl
| | | | | | | | | | |--SM_sn_Tray02_prim_10_box.stl
| | | | | | | | | | |--SM_sn_Tray02_prim_6_box.stl
| | | | | | | | |--textures
| | | | | |--config.json
| | | | |--simready_source
| | | | | |--manual_source
| | | | | | |--collision
| | | | | | | |--manual_collision.xml
| | | | | | | |--Tray02.blend
| | | | | | | |--Tray02.blend1
| | | | | | | |--meshes
| | | | | | | | |--sn_Tray02_prim_7_box.stl
| | | | | | | | |--sn_Tray02_prim_10_box.stl
| | | | | | | | |--sn_Tray02_prim_6_box.stl
| | | | | | | | |--sn_Tray02_prim_9_box.stl
| | | | | | | | |--sn_Tray02_prim_8_box.stl
| | | | | | | |--manual_collision.json
| | | | | | | |--manual_collision_blender.json
| | | | | |--usd_layers
| | | | | | |--collision_layer
| | | | | | | |--manual_collision_layer.usda
| | | | | | |--base_usd
| | | | | | | |--textures
| | | | | | | | |--MuWen_Roughness.png
| | | | | | | | |--MuWen_Normal.png
| | | | | | | | |--MuWen_Color.png
| | | | | | | |--base.usd
| | | | | | |--articulation_layer
| | | | | | |--phys_layer
| | | | | | | |--massFirst_phys_layer.usda
| | | | | |--thumbnail.png
| | | | | |--simready.usda
| | | | | |--vlm_annotation
| | | | | | |--annotation.json
| | | | |--art_source
| | | | | |--manual_source
| | | | | | |--collision
| | | | | | | |--manual_collision.xml
| | | | | | | |--Tray02.blend
| | | | | | | |--Tray02.blend1
| | | | | | | |--meshes
| | | | | | | | |--sn_Tray02_prim_7_box.stl
| | | | | | | | |--sn_Tray02_prim_10_box.stl
| | | | | | | | |--sn_Tray02_prim_6_box.stl
| | | | | | | | |--sn_Tray02_prim_9_box.stl
| | | | | | | | |--sn_Tray02_prim_8_box.stl
| | | | | | | |--manual_collision.json
| | | | | | | |--manual_collision_blender.json
| | | | | |--Tray02.blend
| | | | | |--textures
| | | | | | |--WoodGrain_Color.png
| | | | | | |--WoodGrain_Normal.png
| | | | | | |--WoodGrain_Roughness.png
| | | | | |--Tray02.usd
| | | | | |--Tray02_thumbnail.png
| | |--table
| | | |--folding_table
| | | | |--simready_asset
| | | | | |--thumbnail.png
| | | | | |--model
| | | | | | |--obj
| | | | | | | |--normalized.obj
| | | | | | | |--normalized.mtl
| | | | | | |--usd
| | | | | | | |--usd_layers
| | | | | | | | |--collision_layer
| | | | | | | | | |--manual_collision_layer.usd
| | | | | | | | |--phys_layer
| | | | | | | | | |--massFirst_phys_layer.usd
| | | | | | | |--base_usd
| | | | | | | | |--textures
| | | | | | | | | |--ZheDieZhuo_Metallic.png
| | | | | | | | | |--ZheDieZhuo_Color.png
| | | | | | | | | |--ZheDieZhuo_Roughness.png
| | | | | | | | | |--ZheDieZhuo_Normal.png
| | | | | | | | |--base.usd
| | | | | | | |--simready.usd
| | | | | | |--hull
| | | | | | | |--convex_hull.stl
| | | | | | |--decomposition
| | | | | | | |--convex_decomposition.stl
| | | | | | |--mjcf
| | | | | | | |--mjcf_simready.xml
| | | | | | | |--mjcf_simready
| | | | | | | | |--meshes
| | | | | | | | | |--stl
| | | | | | | | | | |--SM_sn_ZheDieZhuo01_prim_10_box.stl
| | | | | | | | | | |--SM_sn_ZheDieZhuo01_prim_1_box.stl
| | | | | | | | | | |--SM_sn_ZheDieZhuo01_prim_2_box.stl
| | | | | | | | | | |--SM_sn_ZheDieZhuo01_prim_12_box.stl
| | | | | | | | | | |--SM_sn_ZheDieZhuo01_prim_4_box.stl
| | | | | | | | | | |--SM_sn_ZheDieZhuo01_prim_18_box.stl
| | | | | | | | | | |--SM_sn_ZheDieZhuo01_prim_16_box.stl
| | | | | | | | | | |--SM_sn_ZheDieZhuo01_prim_9_box.stl
| | | | | | | | | | |--SM_sn_ZheDieZhuo01_prim_14_box.stl
| | | | | | | | | | |--SM_sn_ZheDieZhuo01_prim_5_box.stl
| | | | | | | | | | |--SM_sn_ZheDieZhuo01_prim_6_box.stl
| | | | | | | | | | |--SM_sn_ZheDieZhuo01_prim_19_box.stl
| | | | | | | | | | |--SM_sn_ZheDieZhuo01_prim_8_box.stl
| | | | | | | | | | |--SM_sn_ZheDieZhuo01_prim_13_box.stl
| | | | | | | | | | |--SM_sn_ZheDieZhuo01_prim_17_box.stl
| | | | | |--config.json
| | | | |--simready_source
| | | | | |--manual_source
| | | | | | |--collision
| | | | | | | |--manual_collision.xml
| | | | | | | |--meshes
| | | | | | | | |--sn_ZheDieZhuo01_prim_18_box.stl
| | | | | | | | |--sn_ZheDieZhuo01_prim_1_box.stl
| | | | | | | | |--sn_ZheDieZhuo01_prim_8_box.stl
| | | | | | | | |--sn_ZheDieZhuo01_prim_5_box.stl
| | | | | | | | |--sn_ZheDieZhuo01_prim_2_box.stl
| | | | | | | | |--sn_ZheDieZhuo01_prim_13_box.stl
| | | | | | | | |--sn_ZheDieZhuo01_prim_4_box.stl
| | | | | | | | |--sn_ZheDieZhuo01_prim_9_box.stl
| | | | | | | | |--sn_ZheDieZhuo01_prim_12_box.stl
| | | | | | | | |--sn_ZheDieZhuo01_prim_17_box.stl
| | | | | | | | |--sn_ZheDieZhuo01_prim_16_box.stl
| | | | | | | | |--sn_ZheDieZhuo01_prim_10_box.stl
| | | | | | | | |--sn_ZheDieZhuo01_prim_6_box.stl
| | | | | | | | |--sn_ZheDieZhuo01_prim_19_box.stl
| | | | | | | | |--sn_ZheDieZhuo01_prim_14_box.stl
| | | | | | | |--manual_collision.json
| | | | | | | |--ZheDieZhuo.blend1
| | | | | | | |--ZheDieZhuo.blend
| | | | | |--usd_layers
| | | | | | |--collision_layer
| | | | | | | |--manual_collision_layer.usda
| | | | | | |--base_usd
| | | | | | | |--textures
| | | | | | | | |--ZheDieZhuo_Metallic.png
| | | | | | | | |--ZheDieZhuo_Color.png
| | | | | | | | |--ZheDieZhuo_Roughness.png
| | | | | | | | |--ZheDieZhuo_Normal.png
| | | | | | | |--base.usd
| | | | | | |--phys_layer
| | | | | | | |--massFirst_phys_layer.usda
| | | | | |--thumbnail.png
| | | | | |--simready.usda
| | | | | |--vlm_annotation
| | | | | | |--annotation.json
| | | | |--art_source
| | | | | |--manual_source
| | | | | | |--collision
| | | | | | | |--manual_collision.xml
| | | | | | | |--meshes
| | | | | | | | |--sn_ZheDieZhuo01_prim_18_box.stl
| | | | | | | | |--sn_ZheDieZhuo01_prim_1_box.stl
| | | | | | | | |--sn_ZheDieZhuo01_prim_8_box.stl
| | | | | | | | |--sn_ZheDieZhuo01_prim_5_box.stl
| | | | | | | | |--sn_ZheDieZhuo01_prim_2_box.stl
| | | | | | | | |--sn_ZheDieZhuo01_prim_13_box.stl
| | | | | | | | |--sn_ZheDieZhuo01_prim_4_box.stl
| | | | | | | | |--sn_ZheDieZhuo01_prim_9_box.stl
| | | | | | | | |--sn_ZheDieZhuo01_prim_12_box.stl
| | | | | | | | |--sn_ZheDieZhuo01_prim_17_box.stl
| | | | | | | | |--sn_ZheDieZhuo01_prim_16_box.stl
| | | | | | | | |--sn_ZheDieZhuo01_prim_10_box.stl
| | | | | | | | |--sn_ZheDieZhuo01_prim_6_box.stl
| | | | | | | | |--sn_ZheDieZhuo01_prim_19_box.stl
| | | | | | | | |--sn_ZheDieZhuo01_prim_14_box.stl
| | | | | | | |--manual_collision.json
| | | | | | | |--ZheDieZhuo.blend1
| | | | | | | |--ZheDieZhuo.blend
| | | | | |--ZheDieZhuo.usd
| | | | | |--textures
| | | | | | |--ZheDieZhuo_Metallic.png
| | | | | | |--ZheDieZhuo_Color.png
| | | | | | |--ZheDieZhuo_Roughness.png
| | | | | | |--ZheDieZhuo_Normal.png
| | | | | |--ZheDieZhuo_thumbnail.png
| | | | | |--ZheDieZhuo.blend
| | |--shelves
| | | |--Shelf5Tier02
| | | | |--simready_asset
| | | | | |--thumbnail.png
| | | | | |--model
| | | | | | |--obj
| | | | | | | |--normalized.obj
| | | | | | | |--normalized.mtl
| | | | | | |--usd
| | | | | | | |--usd_layers
| | | | | | | | |--collision_layer
| | | | | | | | | |--manual_collision_layer.usd
| | | | | | | | |--phys_layer
| | | | | | | | | |--massFirst_phys_layer.usd
| | | | | | | |--base_usd
| | | | | | | | |--textures
| | | | | | | | | |--huojia_Roughness.png
| | | | | | | | | |--huojia_Normal.png
| | | | | | | | | |--huojia_Metallic.png
| | | | | | | | | |--huojia_Color.png
| | | | | | | | |--base.usd
| | | | | | | |--simready.usd
| | | | | | |--hull
| | | | | | | |--convex_hull.stl
| | | | | | |--decomposition
| | | | | | | |--convex_decomposition.stl
| | | | | | |--mjcf
| | | | | | | |--mjcf_simready.xml
| | | | | | | |--mjcf_simready
| | | | | | | | |--materials
| | | | | | | | |--meshes
| | | | | | | | | |--stl
| | | | | | | | | | |--SM_sn_Shelf6Tier01_prim_37_box.stl
| | | | | | | | | | |--SM_sn_Shelf6Tier01_prim_3_box.stl
| | | | | | | | | | |--SM_sn_Shelf6Tier01_prim_12_box.stl
| | | | | | | | | | |--SM_sn_Shelf6Tier01_prim_29_box.stl
| | | | | | | | | | |--SM_sn_Shelf6Tier01_prim_5_box.stl
| | | | | | | | | | |--SM_sn_Shelf6Tier01_prim_7_box.stl
| | | | | | | | | | |--SM_sn_Shelf6Tier01_prim_27_box.stl
| | | | | | | | | | |--SM_sn_Shelf6Tier01_prim_19_box.stl
| | | | | | | | | | |--SM_sn_Shelf6Tier01_prim_22_box.stl
| | | | | | | | | | |--SM_sn_Shelf6Tier01_prim_9_box.stl
| | | | | | | | | | |--SM_sn_Shelf6Tier01_prim_10_box.stl
| | | | | | | | | | |--SM_sn_Shelf6Tier01_prim_23_box.stl
| | | | | | | | | | |--SM_sn_Shelf6Tier01_prim_8_box.stl
| | | | | | | | | | |--SM_sn_Shelf6Tier01_prim_20_box.stl
| | | | | | | | | | |--SM_sn_Shelf6Tier01_prim_33_box.stl
| | | | | | | | | | |--SM_sn_Shelf6Tier01_prim_40_box.stl
| | | | | | | | | | |--SM_sn_Shelf6Tier01_prim_14_box.stl
| | | | | | | | | | |--SM_sn_Shelf6Tier01_prim_1_box.stl
| | | | | | | | | | |--SM_sn_Shelf6Tier01_prim_13_box.stl
| | | | | | | | | | |--SM_sn_Shelf6Tier01_prim_30_box.stl
| | | | | | | | | | |--SM_sn_Shelf6Tier01_prim_21_box.stl
| | | | | | | | | | |--SM_sn_Shelf6Tier01_prim_18_box.stl
| | | | | | | | | | |--SM_sn_Shelf6Tier01_prim_34_box.stl
| | | | | | | | | | |--SM_sn_Shelf6Tier01_prim_25_box.stl
| | | | | | | | | | |--SM_sn_Shelf6Tier01_prim_28_box.stl
| | | | | | | | | | |--SM_sn_Shelf6Tier01_prim_4_box.stl
| | | | | | | | | | |--SM_sn_Shelf6Tier01_prim_15_box.stl
| | | | | | | | | | |--SM_sn_Shelf6Tier01_prim_24_box.stl
| | | | | | | | | | |--SM_sn_Shelf6Tier01_prim_17_box.stl
| | | | | | | | | | |--SM_sn_Shelf6Tier01_prim_26_box.stl
| | | | | | | | | | |--SM_sn_Shelf6Tier01_prim_6_box.stl
| | | | | | | | | | |--SM_sn_Shelf6Tier01_prim_16_box.stl
| | | | | | | | | | |--SM_sn_Shelf6Tier01_prim_11_box.stl
| | | | | | | | | | |--SM_sn_Shelf6Tier01_prim_2_box.stl
| | | | | | | | |--textures
| | | | | |--config.json
| | | | |--simready_source
| | | | | |--manual_source
| | | | | | |--collision
| | | | | | | |--manual_collision.xml
| | | | | | | |--meshes
| | | | | | | | |--sn_Shelf6Tier01_prim_28_box.stl
| | | | | | | | |--sn_Shelf6Tier01_prim_8_box.stl
| | | | | | | | |--sn_Shelf6Tier01_prim_15_box.stl
| | | | | | | | |--sn_Shelf6Tier01_prim_12_box.stl
| | | | | | | | |--sn_Shelf6Tier01_prim_9_box.stl
| | | | | | | | |--sn_Shelf6Tier01_prim_6_box.stl
| | | | | | | | |--sn_Shelf6Tier01_prim_29_box.stl
| | | | | | | | |--sn_Shelf6Tier01_prim_16_box.stl
| | | | | | | | |--sn_Shelf6Tier01_prim_11_box.stl
| | | | | | | | |--sn_Shelf6Tier01_prim_3_box.stl
| | | | | | | | |--sn_Shelf6Tier01_prim_27_box.stl
| | | | | | | | |--sn_Shelf6Tier01_prim_23_box.stl
| | | | | | | | |--sn_Shelf6Tier01_prim_4_box.stl
| | | | | | | | |--sn_Shelf6Tier01_prim_19_box.stl
| | | | | | | | |--sn_Shelf6Tier01_prim_34_box.stl
| | | | | | | | |--sn_Shelf6Tier01_prim_10_box.stl
| | | | | | | | |--sn_Shelf6Tier01_prim_2_box.stl
| | | | | | | | |--sn_Shelf6Tier01_prim_17_box.stl
| | | | | | | | |--sn_Shelf6Tier01_prim_40_box.stl
| | | | | | | | |--sn_Shelf6Tier01_prim_26_box.stl
| | | | | | | | |--sn_Shelf6Tier01_prim_1_box.stl
| | | | | | | | |--sn_Shelf6Tier01_prim_24_box.stl
| | | | | | | | |--sn_Shelf6Tier01_prim_37_box.stl
| | | | | | | | |--sn_Shelf6Tier01_prim_22_box.stl
| | | | | | | | |--sn_Shelf6Tier01_prim_33_box.stl
| | | | | | | | |--sn_Shelf6Tier01_prim_20_box.stl
| | | | | | | | |--sn_Shelf6Tier01_prim_13_box.stl
| | | | | | | | |--sn_Shelf6Tier01_prim_18_box.stl
| | | | | | | | |--sn_Shelf6Tier01_prim_25_box.stl
| | | | | | | | |--sn_Shelf6Tier01_prim_21_box.stl
| | | | | | | | |--sn_Shelf6Tier01_prim_7_box.stl
| | | | | | | | |--sn_Shelf6Tier01_prim_30_box.stl
| | | | | | | | |--sn_Shelf6Tier01_prim_5_box.stl
| | | | | | | | |--sn_Shelf6Tier01_prim_14_box.stl
| | | | | | | |--manual_collision.json
| | | | | | | |--Shelf5Tier02.blend1
| | | | | | | |--manual_collision_blender.json
| | | | | | | |--Shelf5Tier02.blend
| | | | | |--usd_layers
| | | | | | |--collision_layer
| | | | | | | |--manual_collision_layer.usda
| | | | | | |--base_usd
| | | | | | | |--textures
| | | | | | | | |--huojia_Roughness.png
| | | | | | | | |--huojia_Normal.png
| | | | | | | | |--huojia_Metallic.png
| | | | | | | | |--huojia_Color.png
| | | | | | | |--base.usd
| | | | | | |--articulation_layer
| | | | | | |--phys_layer
| | | | | | | |--massFirst_phys_layer.usda
| | | | | |--thumbnail.png
| | | | | |--simready.usda
| | | | | |--vlm_annotation
| | | | | | |--annotation.json
| | | | |--art_source
| | | | | |--manual_source
| | | | | | |--collision
| | | | | | | |--manual_collision.xml
| | | | | | | |--meshes
| | | | | | | | |--sn_Shelf6Tier01_prim_28_box.stl
| | | | | | | | |--sn_Shelf6Tier01_prim_8_box.stl
| | | | | | | | |--sn_Shelf6Tier01_prim_15_box.stl
| | | | | | | | |--sn_Shelf6Tier01_prim_12_box.stl
| | | | | | | | |--sn_Shelf6Tier01_prim_9_box.stl
| | | | | | | | |--sn_Shelf6Tier01_prim_6_box.stl
| | | | | | | | |--sn_Shelf6Tier01_prim_29_box.stl
| | | | | | | | |--sn_Shelf6Tier01_prim_16_box.stl
| | | | | | | | |--sn_Shelf6Tier01_prim_11_box.stl
| | | | | | | | |--sn_Shelf6Tier01_prim_3_box.stl
| | | | | | | | |--sn_Shelf6Tier01_prim_27_box.stl
| | | | | | | | |--sn_Shelf6Tier01_prim_23_box.stl
| | | | | | | | |--sn_Shelf6Tier01_prim_4_box.stl
| | | | | | | | |--sn_Shelf6Tier01_prim_19_box.stl
| | | | | | | | |--sn_Shelf6Tier01_prim_34_box.stl
| | | | | | | | |--sn_Shelf6Tier01_prim_10_box.stl
| | | | | | | | |--sn_Shelf6Tier01_prim_2_box.stl
| | | | | | | | |--sn_Shelf6Tier01_prim_17_box.stl
| | | | | | | | |--sn_Shelf6Tier01_prim_40_box.stl
| | | | | | | | |--sn_Shelf6Tier01_prim_26_box.stl
| | | | | | | | |--sn_Shelf6Tier01_prim_1_box.stl
| | | | | | | | |--sn_Shelf6Tier01_prim_24_box.stl
| | | | | | | | |--sn_Shelf6Tier01_prim_37_box.stl
| | | | | | | | |--sn_Shelf6Tier01_prim_22_box.stl
| | | | | | | | |--sn_Shelf6Tier01_prim_33_box.stl
| | | | | | | | |--sn_Shelf6Tier01_prim_20_box.stl
| | | | | | | | |--sn_Shelf6Tier01_prim_13_box.stl
| | | | | | | | |--sn_Shelf6Tier01_prim_18_box.stl
| | | | | | | | |--sn_Shelf6Tier01_prim_25_box.stl
| | | | | | | | |--sn_Shelf6Tier01_prim_21_box.stl
| | | | | | | | |--sn_Shelf6Tier01_prim_7_box.stl
| | | | | | | | |--sn_Shelf6Tier01_prim_30_box.stl
| | | | | | | | |--sn_Shelf6Tier01_prim_5_box.stl
| | | | | | | | |--sn_Shelf6Tier01_prim_14_box.stl
| | | | | | | |--manual_collision.json
| | | | | | | |--Shelf5Tier02.blend1
| | | | | | | |--manual_collision_blender.json
| | | | | | | |--Shelf5Tier02.blend
| | | | | |--Shelf5Tier02.usd
| | | | | |--textures
| | | | | | |--huojia_Roughness.png
| | | | | | |--huojia_Normal.png
| | | | | | |--huojia_Metallic.png
| | | | | | |--huojia_Color.png
| | | | | |--Shelf5Tier02_thumbnail.png
| | | | | |--Shelf5Tier02.blend
|--AGENTS.md
|--playground
| |--Datasets
| | |--Datasets
| | | |--default_dataset
| | | | |--front_head_rgb_camera
| | | | | |--labels
| | | | | | |--test
| | | | | | | |--0078.txt
| | | | | | | |--0070.txt
| | | | | | | |--0088.txt
| | | | | | | |--0079.txt
| | | | | | | |--0072.txt
| | | | | | | |--0075.txt
| | | | | | | |--0081.txt
| | | | | | | |--0086.txt
| | | | | | | |--0089.txt
| | | | | | | |--0082.txt
| | | | | | | |--0073.txt
| | | | | | | |--0080.txt
| | | | | | | |--0085.txt
| | | | | | | |--0084.txt
| | | | | | | |--0087.txt
| | | | | | | |--0077.txt
| | | | | | | |--0083.txt
| | | | | | | |--0071.txt
| | | | | | | |--0074.txt
| | | | | | | |--0076.txt
| | | | | | |--val
| | | | | | | |--0091.txt
| | | | | | | |--0093.txt
| | | | | | | |--0098.txt
| | | | | | | |--0097.txt
| | | | | | | |--0090.txt
| | | | | | | |--0092.txt
| | | | | | | |--0094.txt
| | | | | | | |--0096.txt
| | | | | | | |--0099.txt
| | | | | | | |--0095.txt
| | | | | | |--train.cache
| | | | | | |--train
| | | | | | | |--0037.txt
| | | | | | | |--0062.txt
| | | | | | | |--0061.txt
| | | | | | | |--0056.txt
| | | | | | | |--0002.txt
| | | | | | | |--0029.txt
| | | | | | | |--0007.txt
| | | | | | | |--0005.txt
| | | | | | | |--0011.txt
| | | | | | | |--0031.txt
| | | | | | | |--0023.txt
| | | | | | | |--0026.txt
| | | | | | | |--0018.txt
| | | | | | | |--0058.txt
| | | | | | | |--0066.txt
| | | | | | | |--0045.txt
| | | | | | | |--0054.txt
| | | | | | | |--0063.txt
| | | | | | | |--0040.txt
| | | | | | | |--0001.txt
| | | | | | | |--0035.txt
| | | | | | | |--0047.txt
| | | | | | | |--0060.txt
| | | | | | | |--0032.txt
| | | | | | | |--0009.txt
| | | | | | | |--0067.txt
| | | | | | | |--0051.txt
| | | | | | | |--0044.txt
| | | | | | | |--0013.txt
| | | | | | | |--0043.txt
| | | | | | | |--0021.txt
| | | | | | | |--0024.txt
| | | | | | | |--0053.txt
| | | | | | | |--0057.txt
| | | | | | | |--0065.txt
| | | | | | | |--0038.txt
| | | | | | | |--0046.txt
| | | | | | | |--0020.txt
| | | | | | | |--0008.txt
| | | | | | | |--0052.txt
| | | | | | | |--0055.txt
| | | | | | | |--0036.txt
| | | | | | | |--0034.txt
| | | | | | | |--0017.txt
| | | | | | | |--0010.txt
| | | | | | | |--0041.txt
| | | | | | | |--0033.txt
| | | | | | | |--0050.txt
| | | | | | | |--0027.txt
| | | | | | | |--0064.txt
| | | | | | | |--0028.txt
| | | | | | | |--0012.txt
| | | | | | | |--0006.txt
| | | | | | | |--0049.txt
| | | | | | | |--0042.txt
| | | | | | | |--0048.txt
| | | | | | | |--0014.txt
| | | | | | | |--0015.txt
| | | | | | | |--0025.txt
| | | | | | | |--0069.txt
| | | | | | | |--0068.txt
| | | | | | | |--0019.txt
| | | | | | | |--0003.txt
| | | | | | | |--0059.txt
| | | | | | | |--0000.txt
| | | | | | | |--0004.txt
| | | | | | | |--0022.txt
| | | | | | | |--0016.txt
| | | | | | | |--0039.txt
| | | | | | | |--0030.txt
| | | | | | |--val.cache
| | | | | |--data.yaml
| | | | | |--classes.txt
| | | | | |--yolo_seg.yaml
| | | | | |--images
| | | | | | |--test
| | | | | | | |--0084.png
| | | | | | | |--0087.png
| | | | | | | |--0076.png
| | | | | | | |--0074.png
| | | | | | | |--0082.png
| | | | | | | |--0078.png
| | | | | | | |--0081.png
| | | | | | | |--0073.png
| | | | | | | |--0070.png
| | | | | | | |--0079.png
| | | | | | | |--0072.png
| | | | | | | |--0077.png
| | | | | | | |--0083.png
| | | | | | | |--0080.png
| | | | | | | |--0075.png
| | | | | | | |--0088.png
| | | | | | | |--0086.png
| | | | | | | |--0085.png
| | | | | | | |--0071.png
| | | | | | | |--0089.png
| | | | | | |--val
| | | | | | | |--0098.png
| | | | | | | |--0092.png
| | | | | | | |--0099.png
| | | | | | | |--0094.png
| | | | | | | |--0096.png
| | | | | | | |--0097.png
| | | | | | | |--0091.png
| | | | | | | |--0093.png
| | | | | | | |--0095.png
| | | | | | | |--0090.png
| | | | | | |--train
| | | | | | | |--0013.png
| | | | | | | |--0038.png
| | | | | | | |--0022.png
| | | | | | | |--0025.png
| | | | | | | |--0014.png
| | | | | | | |--0028.png
| | | | | | | |--0035.png
| | | | | | | |--0050.png
| | | | | | | |--0019.png
| | | | | | | |--0049.png
| | | | | | | |--0055.png
| | | | | | | |--0043.png
| | | | | | | |--0044.png
| | | | | | | |--0011.png
| | | | | | | |--0067.png
| | | | | | | |--0010.png
| | | | | | | |--0000.png
| | | | | | | |--0001.png
| | | | | | | |--0004.png
| | | | | | | |--0007.png
| | | | | | | |--0034.png
| | | | | | | |--0005.png
| | | | | | | |--0012.png
| | | | | | | |--0054.png
| | | | | | | |--0059.png
| | | | | | | |--0039.png
| | | | | | | |--0058.png
| | | | | | | |--0061.png
| | | | | | | |--0040.png
| | | | | | | |--0008.png
| | | | | | | |--0041.png
| | | | | | | |--0024.png
| | | | | | | |--0009.png
| | | | | | | |--0060.png
| | | | | | | |--0023.png
| | | | | | | |--0045.png
| | | | | | | |--0047.png
| | | | | | | |--0062.png
| | | | | | | |--0029.png
| | | | | | | |--0048.png
| | | | | | | |--0033.png
| | | | | | | |--0046.png
| | | | | | | |--0052.png
| | | | | | | |--0042.png
| | | | | | | |--0020.png
| | | | | | | |--0065.png
| | | | | | | |--0002.png
| | | | | | | |--0064.png
| | | | | | | |--0051.png
| | | | | | | |--0030.png
| | | | | | | |--0003.png
| | | | | | | |--0031.png
| | | | | | | |--0066.png
| | | | | | | |--0036.png
| | | | | | | |--0027.png
| | | | | | | |--0032.png
| | | | | | | |--0069.png
| | | | | | | |--0018.png
| | | | | | | |--0006.png
| | | | | | | |--0063.png
| | | | | | | |--0053.png
| | | | | | | |--0026.png
| | | | | | | |--0068.png
| | | | | | | |--0037.png
| | | | | | | |--0057.png
| | | | | | | |--0021.png
| | | | | | | |--0017.png
| | | | | | | |--0016.png
| | | | | | | |--0015.png
| | | | | | | |--0056.png
| | |--__MACOSX
| | | |--Datasets
| | | | |--default_dataset
| | | | | |--front_head_rgb_camera
| | | | | | |--labels
| | | | | | | |--test
| | | | | | | |--val
| | | | | | | |--train
| | | | | | |--images
| | | | | | | |--test
| | | | | | | |--val
| | | | | | | |--train
|--book.toml
|--weights
| |--2023-10-28-18-33-37
| | |--model_best.pth
| | |--config.yml
| |--2024-01-11-20-02-45
| | |--model_best.pth
| | |--config.yml
|--outputs
| |--ioai_sim_scene_place
| | |--water
| | | |--inference
| | | | |--config.json
| | | | |--model_inference.pth
| | | | |--action_norm_params.json
| | | |--inference.zip
| | |--pringles
| | | |--inference
| | | | |--config.json
| | | | |--model_inference.pth
| | | | |--action_norm_params.json
| | | |--inference.zip
| | |--pepsichips
| | | |--inference
| | | | |--config.json
| | | | |--model_inference.pth
| | | | |--action_norm_params.json
| | | |--inference.zip
| | |--gum
| | | |--inference
| | | | |--config.json
| | | | |--model_inference.pth
| | | | |--action_norm_params.json
| | | |--inference.zip
| | |--applejuice
| | | |--inference
| | | | |--config.json
| | | | |--model_inference.pth
| | | | |--action_norm_params.json
| | | |--inference.zip
| | |--beefnoodle
| | | |--inference
| | | | |--config.json
| | | | |--model_inference.pth
| | | | |--action_norm_params.json
| | | |--inference.zip
| | |--orangejuice
| | | |--inference
| | | | |--config.json
| | | | |--model_inference.pth
| | | | |--action_norm_params.json
| | | |--inference.zip
| | |--coffee
| | | |--inference
| | | | |--config.json
| | | | |--model_inference.pth
| | | | |--action_norm_params.json
| | | |--inference.zip
| | |--cocacola
| | | |--inference
| | | | |--config.json
| | | | |--model_inference.pth
| | | | |--action_norm_params.json
| |--ioai_sim_scene_pick
| | |--gum
| | | |--inference
| | | | |--config.json
| | | | |--model_inference.pth
| | | | |--action_norm_params.json
| | |--cocacola
| | | |--inference
| | | | |--config.json
| | | | |--model_inference.pth
| | | | |--action_norm_params.json
| |--ioai_policy_baseline.yaml
| |--ioai_table_layout.yaml
|--uv.lock

Official scoring is based on the task performance observed when the organizers run the final submitted solution. Internal logs or structured JSON result files produced by an official baseline are useful for development, but they are not the official competition score.
