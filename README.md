# CROSS - CAD and ROS, Open-Source Synergy

CROSS is a FreeCAD workbench to generate robot description packages (xacro or URDF) for the Robot Operating System, [ROS].

# This fork inludes all of CROSS and new features such as:
1. Material selection of link or whole robot
1. Auto calculation of mass and inertia
1. Launcher for Gazebo
1. New some icons and icons reordering
1. Bug fixes
1. Others

Tools of FreeCAD CROSS
![Tools of FreeCAD CROSS](https://github.com/drfenixion/freecad.cross/assets/13005708/d3d44e65-a9cc-45cc-937a-be5008b98608)
Generated inertia blocks and centers of mass in Gazebo
![Generated inertia blocks and centers of mass in Gazebo](https://github.com/drfenixion/freecad.cross/assets/13005708/a46715a0-0dc6-4f6e-b80e-e4c644589477)
Launched Rviz and Gazebo from gazebo launcher
![Launched Rviz and Gazebo from gazebo launcher](https://github.com/drfenixion/freecad.cross/assets/13005708/9017aec4-70e5-45fa-82ad-6b4646453767)


CROSS is a powerful ROS workbench for [FreeCAD](https://www.freecad.org/), a popular open-source 3D parametric modelling software.
As the field of robotics continues to evolve rapidly, the need for comprehensive and efficient tools for robot development and simulation has become increasingly essential.
CROSS emerges as a versatile solution, empowering engineers, researchers, and hobbyists to leverage the capabilities of both ROS and FreeCAD in a cohesive environment.
At the time of writing (June 2023), CROSS is the only available open-source solution to generate robot description files for ROS with a graphical user interface with direct visual feedback.

With CROSS, users gain the ability to combine the flexibility of FreeCAD's 3D modeling capabilities with the extensive functionality of ROS, allowing for seamless collaboration between mechanical design and robotics development.
    By bridging the gap between these two powerful platforms, CROSS streamlines the process of designing, and visualizing robotic systems, ultimately accelerating the development cycle.

The key features of CROSS are:

* ROS Integration: CROSS offers native integration with ROS, an open-source framework widely adopted in the robotics community.
        This integration enables users to leverage the vast ecosystem of ROS packages, libraries, and tools while working within the familiar FreeCAD environment.
* 3D Modelling and Simulation: FreeCAD's 3D modelling capabilities empower users to design intricate mechanical components and complete robot systems.
        With CROSS, these designs can be seamlessly integrated with ROS simulations, allowing for realistic and accurate testing of robot behaviors and interactions.
* Visualization and Analysis: CROSS provides advanced visualization and analysis tools provided by FreeCAD itself, enabling users to inspect, analyze, and validate their robot designs.
* Collaborative Development: CROSS supports collaborative development by facilitating the sharing of robot models through the use of complex macro written in the Python language where a full robot can be generated by code.
        This encourages teamwork, knowledge sharing, and accelerates the pace of innovation within the robotics community.
* Extensibility: As an open-source project, CROSS encourages contributions from the community, allowing users to extend its functionality and adapt it to their specific needs.
        By leveraging the collective expertise of the ROS and FreeCAD communities, CROSS continues to evolve and provide cutting-edge features for robot development.

## Compatibility

Compatible with FreeCAD v0.19 (or earlier version with the local coordinate system feature) but tested on FreeCAD v0.21.
Compatible with ROS2 (for now).

## Features

- Export `Part::Box`, `Part::Sphere`, and `Part::Cylinder` as text to be included in a URDF file,
- Generate an enclosing box or sphere as collision object (only axis-aligned box for now),
- Build a robot from scratch and generate the URDF file for it,
- Set a value for each actuated joint of a robot and have the links move accordingly,
- Import URDF/xacro files,
- Import xacro definitions, i.e. import xacro files that only define some macros and ask the user to choose a macro and its parameters to generate a full-feature URDF,
- Export the xacro as xacro that includes (`xacro:include`) the original xacro file and uses the macro.
- Combine several xacros files (i.e. also URDF) into a workcell and export them as a xacro file.
- Get the current planning scene (relies on the /get_planning_scene service of type `moveit_msgs/srv/GetPlanningScene`)
- Define a pose and possibly bring a specific link to it. All links that are fixed to this link will follow but the inverse kinematic solutions are not shown.

## Installation

You need a recent version of FreeCAD v0.21 with the ability to configure custom repositories for the Addon Manager to install the workbench via the Addon Manager. On earlier version you're on your own, see instructions for local install below.

- In FreeCAD, menu "Edit / Preferences ..."
- Category "Addon Manager"
- Add an entry to "Custom repository" by clicking on the "+" sign.
- Repository URL: `https://github.com/galou/freecad.cross.git`, branch: `main`
- Click on "OK" to close the dialog "Preferences"
- Back to FreeCAD's main window, menu "Tools / Addon manager"
- Search and install the workbench via the [Addon Manager](https://wiki.freecad.org/Std_AddonMgr)

## Launching FreeCAD with ROS

The CROSS workbench is supposed to load also without ROS, with limited functionality.
If this is not the case, please report.

You will probably want to be able to use ROS-related functionalities and this requires launching FreeCAD from the command line:

- Open a terminal
- Source your ROS workspace
- Launch FreeCAD with extra Python modules set by ROS, `freecad --module-path ${PYTHONPATH//:/' --module-path '}` (replace `freecad` by your FreeCAD executable). This bash magic will add for example ` --module-path path1 --module-path path2 ` if `$PYTHONPATH` is `path1:path2`.

## Testing/developing the workbench

If you want to work on this workbench you have the following options:

- Clone the repository directory in FreeCAD's `Mod` directory: `cd ~/.local/share/FreeCAD/Mod && git clone https://github.com/galou/freecad.cross.git` on Linux
- Start FreeCAD from the root-directory of this repository in a terminal (by default `freecad.cross`)
- Clone this repository and create a symbolic link to the directory `freecad.cross` (or the directory containing this repository if you changed the name) to FreeCAD's `Mod` directory (`~/.local/share/FreeCAD/Mod` on Linux).
- `pip install -e .` adds the root-directory to `easy_install.path`.


--------------------------------------------------------------------------------

[ROS]: https://www.ros.org/
