# Midterm Project

Please check the `midterm_final` branch for final midterm code.

## Command usage

(if running with the real robot, please run `jinx_master` for all terminal)

1. Under the directory where the simulation and urdf reside:

Start up gazebo and spawn mobot (don't run this if run real robot)
`roslaunch mobot_urdf mobot_in_pen.lauch`

Load map of the lab (please `cd` to the directory that contains the map):

`rosrun map_server map_server lab_map.yaml`

2. Under the directory where the mobot_controller resides:

Run AMCL to localize the robot in the map.  AMCL updates are only about 1Hz, and thus
unsuitable for steering feedback.

`rosrun amcl amcl`

Start mobot_controller's nodes:

`rosrun mobot_controller current_state_publisher`

`rosrun mobot_controller des_state_publisher_service`

`rosrun mobot_controller lin_steering_wrt_amcl_and_odom`

## Running path planner
In rviz, give the robot an approximate starting pose.
Move the robot (under open-loop control), so AMCL will publish updated pose estimates.

`rosrun mobot_controller navigation_coordinator`  

Add the axes of `base_link` for the robot representation.
  
