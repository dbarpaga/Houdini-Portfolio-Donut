# Houdini-Portfolio-Donut

Hello, this will be a Donut piece made in Houdini

We will start with the Torus obj 

![torus1](https://user-images.githubusercontent.com/103074186/163476330-cd17f871-3fff-47ee-83ad-86a4d17646e5.PNG)

Enter the torus geometry

![torus2](https://user-images.githubusercontent.com/103074186/163476716-df755dc0-2ada-4df2-8fcb-73dfc5bcb4e9.PNG)

Increase the rows and columns to 64 and 144 respectively. This will increase the level of detail we can add later

Next we add a normal node to the torus node

![normal1](https://user-images.githubusercontent.com/103074186/163477501-612a18c3-5ce5-49b1-aa09-8e1d1a5df58b.PNG)

We now display normals 

![displaynormals](https://user-images.githubusercontent.com/103074186/163478025-b84e3d64-5d2f-4550-bb12-ef735ae06860.PNG)

We then add our normals to points instead of vertices

Next we add a group, with points as the type and disabling the base group and enable keep in bounding regions

![group2](https://user-images.githubusercontent.com/103074186/163479427-24e51115-b09c-4c7d-a28b-c5cafd4d5c52.PNG)

We will set the size of the bounding region to 4, 0.05, 4

Then create an attribcreate node, we will name this weight. Attaching to our group. Set the Value to 1

![weight1](https://user-images.githubusercontent.com/103074186/163480101-893449a5-87ba-487d-8976-98c140adab64.PNG)

Next create a visualize tab, attach to the weight. We will display our weight attribute as a ramped attribute. 

![weight2](https://user-images.githubusercontent.com/103074186/163480875-f3f3f588-045a-480e-895f-6eba867d316e.PNG)

Add an attribute blur node, and set our attribute as weight. Then set the blur iterations to a value that you're comfortable with

![blur1](https://user-images.githubusercontent.com/103074186/163481462-01882f06-f9e3-434b-b58d-76518c731cad.PNG)

Next add a pointvop node, attach to the blur and the visualize node to the vop node

Double click the vopnode

![vopnode1](https://user-images.githubusercontent.com/103074186/163481896-ae479ce0-68ad-44fe-bd94-80fb3a11888e.PNG)

You will then see 2 default nodes. Global input and Global output








