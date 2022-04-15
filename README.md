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

Add another attribblur, set iterations to 8

Next we add a remap node, adjust the scale in order to define our icing further

Next add a scatter node, and we will use density and weight as our attribute

Increase the force count to 32,000 and the relax iterations to 32

![scatter1](https://user-images.githubusercontent.com/103074186/163520075-3316c99e-78e6-4ea7-9296-7c2a6f632b69.PNG)

Next add a peak node to lift the icing off of the donut slightly, a value of 0.02 or less should be sufficient. as always adjust it to your liking. 

Next node is VDB from particles, change voxel size to 0.01 and the point radius scale to 0.03

![lookinglikefrosting](https://user-images.githubusercontent.com/103074186/163521320-02dc7e19-8dcc-41fb-a52b-20bcfaa8a083.PNG)

add attribnoise node to the peak node. pscale for the attribute. click the box saying enable remap ramp. click the left arrow, put the value as 0.8 the right as 1.3 and then set element size under noise pattern to 0.5   

![remapramp](https://user-images.githubusercontent.com/103074186/163523285-c9cac686-2c91-4a6a-8ddb-6c82af432e97.PNG)

Add a remap node before our pscale node

Temporarily disable attribnoise node. in attribremap we will change weight to pscale. expand the ramp and we then set up points to make a b spline

![moreramp](https://user-images.githubusercontent.com/103074186/163523835-deb76018-a0db-44ec-8164-7b2385bcdff9.PNG)

Re-enable attribnoise. set the noise level operation to multiply. Add VDbreshape node to VBDparticles. Then add a VDB Smooth SDF Node to the VDB reshape node

![moreicinglike](https://user-images.githubusercontent.com/103074186/163524372-363fbbd8-1835-4e75-8aaa-18c8797292bd.PNG)

As we can see, our "icing" is beginning to take shape

Increase Iterations to smooth out the icing

Add VDB Reshape and set it to erode, offset is 1. This will decrease the thickness of the icing

Add convert VDB node, set to polygons

Attach another normal node and attribblur. Set normal to point normals. Blur to P and N and 4 bluur iterations. 

Create two Null nodes, attach one to this last blur and the other to the subdivide for the dough

Create a merge node to connect the two null nodes 

The Icing will be black, now we can add another color node before the null node for the icing to chaqnge it to whatever color we like

![pinkdonut](https://user-images.githubusercontent.com/103074186/163530321-1a671b1f-824f-4b32-b89b-60140df6e741.PNG)

Next up, sprinkles

We start from our color node that we have before the merge node

Group node> set to primitives, disable base group. Enable keep by normals. Direction to 0,1,0. Spread angle to where sprinkles looks viable. 

Add scatter node, relax iterations to 1. Select the group that was just created. 

Attach a peak node after the scatter. Distance of 0.01

Create a tube > Polygon type > Endcaps > Add vertex Normals >  Radius Scale is 0.2 and on the Z- Axis

Create a poly bevel node for the tube > Round shape > Divisions to 4 > Exclusions > Ignore Flat Edges should be enabled > Increase Max normal angle to 45
Offset distance to 0.1

![flatedges](https://user-images.githubusercontent.com/103074186/163540991-062f3a0b-2515-4e5f-9cf1-966cfdf46cb8.PNG)

Add normal node > point normals

Then we will copy these point normals over to our peak for the icing with Copy To Points node.

Then create attribrandomize. Change attribute name to scale. Adjust min and max sizes

![sprinklesettings](https://user-images.githubusercontent.com/103074186/163542166-ca38ba8d-9ec7-438c-8f81-c39284feb623.PNG)

Add another attribrandomize 

Change the attribute to orient and change dimesnions to 4. Change to direction or orientation. Enable Cone Angle, randomize cone angle and the bias toward direction.

One more attribrandomize this time for the color of the sprinkles. Change distribution to two values. Adjust the values for the colors you want.

Create Null node, attach to the copytopoints node and then the merge node we have from before. 

We now have a donut with sprinkles on it. We will be rendering this next.


![almostthere](https://user-images.githubusercontent.com/103074186/163543683-78d25da4-f09b-4e33-94fb-9e0cca6b7998.PNG)


I used Houdini's inhouse render, there are 3rd party render programs that can be used and each has their own pros and cons.


![renderedfdoniut](https://user-images.githubusercontent.com/103074186/163634851-63f44eaf-92ab-488c-bc83-64157097cfa8.PNG)












