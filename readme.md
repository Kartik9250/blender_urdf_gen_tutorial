# Blender to URDF Tutorial

## What is URDF?
URDF (Unified Robot Description Format) is an XML-based file format used in robotics to describe the structure, kinematics, dynamics, and visual aspects of robots. It is commonly used in robot simulation and control, enabling accurate modeling and visualization of robotic systems.

## What is Blender?
Blender is a versatile and open-source 3D creation software that empowers artists, designers, and developers to generate stunning visual content. It offers tools for modeling, animation, rendering, texturing, and more, making it a popular choice for creating everything from intricate 3D models to immersive animations and visual effects.

## Methods of generating URDF models:
- **SolidWorks:** SolidWorks offers tools for designing and exporting URDF files for use in robot simulation and control.

- **Blender:** Blender has add-ons and scripts that facilitate the creation of URDF files for robots, making it useful for both visualization and simulation.

- **Gazebo:** Gazebo is a popular robot simulation environment that works with URDF models. It can be used to create, simulate, and test robotic systems.

- **Fusion360:** Fusion2urdf is a plugin for Autodesk Fusion360 that enables the creation of URDF files for robots designed in Fusion360.

## Why blender?
- **Visual Modeling:** Blender's powerful 3D modeling capabilities allow you to create detailed and visually appealing robot models, helping you accurately represent the physical structure of your robot.

- **Customization:** Blender lets you design and modify robot components with precision, enabling you to create custom shapes and textures that suit your specific robot design.

- **Animation and Simulation:** Blender's animation tools enable you to animate the movement of your robot's joints and components. You can also simulate the robot's motion, helping you validate its kinematics and dynamics before implementing it in real-world scenarios.

- **Realistic Visualization:** Blender's rendering capabilities produce high-quality images and videos, making it easier to communicate your robot's design and behavior to others, whether it's for research, documentation, or presentations.

- **Integration with ROS and Gazebo:** Blender's URDF exporter allows you to seamlessly integrate your robot models into ROS and Gazebo simulation environments, enhancing your ability to simulate and test your robot's behavior.

- **Open Source:** Blender is open-source software, meaning it's freely available and continuously developed by a global community. This ensures access to updates, improvements, and community-generated resources.

- **Flexibility:** Blender's scripting capabilities allow for automation and batch processing of URDF generation tasks, which can be particularly helpful when dealing with multiple robot models.

## How to generate URDF from Blender?
Since Blender is so versetile and easy to use, this makes it the perfect candidate for begineers and infact experienced users to utilise it for 3modeling. Thanks to the Phobos add-on, URDF can directly be generation through blender, it supports other formats also.

**Phobos:** is a versatile tool and add-on for Blender v3.3LTS, aiding in the creation and editing of robot models. It supports various formats like URDF, SDF, and common mesh formats, facilitating seamless integration with robot frameworks and simulations like ROS, Gazebo, and MARS. Developed by DFKI's Robotics Innovation Center and the University of Bremen, Phobos streamlines robot model development for research and applications.

# Installation:
- Head over to the [Phobos's official github repository](https://github.com/dfki-ric/phobos) and download the latest release zip.

- Open Blender, if you have installed it you can head over to their [website](https://www.blender.org/download/).

- Inside the `Edit tab` you will find `Preference section` over there look for `Addons`.(`Blender->Edit->Preferences->Addons`)

- Click on Install and browse to the `phobos.zip` file that you just downloaded.

- Now lets enable our add-on, search `phobos` and select it to enable.

# Creating a 3d model for your URDF:
- Create a model of according to your desired requirements. If you have any models ready already, you can import them models inside blender and move ahead.

- **Assigning Phobotype:** Set `Phobotype` of your every body in model to `visual` in `Object-properties->Phobos Object Information->Phobotype`

- **Adding Links:** Select your body, add a links to it by the using `Sidebar->Phobos->Kinematics->Create link(s)`. This will create bones, which will be used as links and joints in URDF. You can turn on `In Front` option so that bones are always visible by `Data->Viewport Display->In Front`
    **Note:** You should change the location from `3D Cursor` to `Selected Objected` Creating an link. This will spwan the link at the origin of that body.

- **Defining joints:** The Links that you just added their joint type should also be defined. There are four types of joints(Revolute, Prismatic, Fixed, Continous, Floating, Planar, Floating). You can define it by `Sidebar->Phobos->Kinematics->Define Joint(s)`.

- **Joining links together:** Now lets join our links that we just created. By using `Shift+Mouse1` select all the links and then select the base_link or the main parent link. Press `Ctrl+P` to join those link to the base_link, select the `Bone Relative option`.

- **Joining Bodies and Links:** Select the Visual body then their respective links by using `Shift+Mouse1` and join them together by `Ctrl+P`, select `Object(Keep Transform)`.

- **Defining Visual Geometry:** Give you bodies the appropriate visual geometry by selecting one from these four types(box,cylinder,sphere,mesh) in `Sidebar->Phobos->Visual/Collision->Define Geometry`.

- **Creating Collision Objects:** Select the body and then create collision object by `Sidebar->Phobos->Visual/Collision->Create Collision Object(s)`.

- **Joining Collision Object and links together:** Select the newly created Collision body then their respective links by using `Shift+Mouse1` and join them together by `Ctrl+P`, select `Object(Keep Transform)`.

- **Adding Inertia:** Select the Link and then create inertial by `Sidebar->Phobos->Mass & Inertia->Create Inertials`, you can add objects mass over here and also change inertia vectors once creating inertials by `Sidebar->Phobos->Mass & Inertia->Edit Mass/Inertia->Change Inertia`.

- **Adding Motors:** You can add motors to your joints by selecting the joint and using Add Motor operator in `Sidebar->Phobos->Hardware`.

- **Exporting URDF:** Select all bodies and links by tapping `A` and then you can edit some parameter for URDF that you will be exporting:
    - **Naming your model:** `Sidebar->Phobos->Model Editor->Name Model`
    - **Export Parameters:** `Sidebar->Phobos->Export`
        - Select your Path
        - Select URDF in `Models`. Select Gazebo_xacro if you will be using it with Gazebo and ROS
        - Select dae/stl/obj in `Meshes`.
    - Now you are ready to export your URDF model, Click on `Export Model` to export your URDF.


This Repository contains am example ros-package and a blend file which would help you guide how you can use the URDF that you just created in Gazebo and control it via ROS publishers and Subscribers.