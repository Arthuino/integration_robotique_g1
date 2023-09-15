# integration_robotique_g1

## setup  

Requis :  
--> Ubuntu 20  
--> ROS noetic  
--> package ros "ros-noetic-industrial-core"  

L'erreur ``` "Could not find a package configuration file provided by "industrial_msgs" ``` signifie que le package industrial-core n'est pas installé.

```bash
sudo apt install ros-noetic-industrial-core
```

## source

source de ROS :

```bash
source /opt/ros/noetic/setup.bash 
```

Build :

```bash
catkin build
```

source du workspace :

```bash
source devel/setup.bash 
```

## launch

test du urdf sur Rviz

```bash
roslaunch motoman_hc10_support test_hc10.launch
```

test de gazebo

```bash
roslaunch hc10_moveit_config demo_gazebo.launch
```

Robot + environement de la cellule

- Avec object simple (gourde)
```bash
roslaunch hc10_moveit_config demo_environment.launch obj_to_scan:=bottle obj_x:=0.64
```

- Avec object complexe (champignon)
```bash
roslaunch hc10_moveit_config demo_environment.launch obj_to_scan:=mushroom obj_x:=0.71
```

Lance Rviz et Gazebo et tourne en fond en attendant les coordonnées de trajectoire

```bash
roslaunch hc10_moveit_config demo_environment.launch 
```

Envoie les coordonnées à atteindre pour le robot via le script Python

```bash
roslaunch hc10_scan_traj scan_traj.launch
```
