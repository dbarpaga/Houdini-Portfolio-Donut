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

We will create a bind for our weight in. tab > bind and it will be for weight and a float type. 

![bind](https://user-images.githubusercontent.com/103074186/163490824-00b1198f-9aca-4e54-82c9-d459fbe0127e.PNG)

Attach the nodes as so and change the scale 

![displace1](https://user-images.githubusercontent.com/103074186/163491205-5191d987-efad-4aaf-9cdb-6cb0ffbf7519.PNG)

Next is to add a mountain node to our original tree, NOTE: For the sake of brevity I will only be adding screen shots sparingly going forward.

Adjust the scale and noise to your liking. we are simply giving the donut a slightly irregular shape. 

We will be adding a color node to adjust the color of our donut

Set the color type to be ramp from attribute, with weight as our attribute

Adjust colors to your choice, we can add a subdivide node if needed to increase the resolution

![donutcolors](https://user-images.githubusercontent.com/103074186/163500676-5ca17789-748b-4ea5-a695-fbfa8053d771.PNG)

We use an attribute delete node to remove our weight attribute in order to see our donut. Then we create a new group node. Disable base group, choose points and enable keep by normals

Adjust the spread angle to cover the top section of the donut. Adjust direction to 0,1,0

![topdonut](https://user-images.githubusercontent.com/103074186/163502399-c8d05d3f-9329-4232-a2cf-ba92adf20b64.PNG)

Add a noise node to attributedelete, change the attribute to N. This is to randomize our icing that we will be adding shortly. Noise volume to multiplicative 

Add a second normal node after the group

Another attribute create after the second normal

Naming this as weight, setting the value as 1 for group 2 and 0 everywhere else

Add another attribblur


























