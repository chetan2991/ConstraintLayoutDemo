Constraint Layout In Android


-Constraint layout is a ViewGroup which allows you to position and size widgets  in a flexible way

-Constraint layout is available as support library that you can use on Android system starting with api level 9 which is Gingerbread.


there are various type of constraints that we can use with constraint layout


Requirement or Setting for constraint layout to work
 
1. required android studio 2.2 and above
2. 


——
1— The layout engine uses constraints specified for each widget to determine their positions within the layout.

You can specify the constraints either manually or automatically by inference within the Android Studio layout editor. To understand constraints better, let's look at the basic handles available on a selected widget.




Constraints
Constraints help you keep widgets aligned. You can use anchors, such as the constraint handles described below, to determine alignment rules between various widgets. For example, setting a constraint from the left constraint handle of button 2 (see figure A below) to the right constraint handle of button 1 means that the button 2 widget will be positioned 56dp to the right of button 1.





4. Constraints System Overview
The layout engine uses constraints specified for each widget to determine their positions within the layout. You can specify the constraints either manually or automatically by inference within the Android Studio layout editor. To understand constraints better, let's look at the basic handles available on a selected widget.



Constraints
Constraints help you keep widgets aligned. You can use anchors, such as the constraint handles described below, to determine alignment rules between various widgets. For example, setting a constraint from the left constraint handle of button 2 (see figure A below) to the right constraint handle of button 1 means that the button 2 widget will be positioned 56dp to the right of button 1.
￼
Figure A.
Types of Handles:
￼
Figure B. In this widget, we see the different handles.
Resize Handle: Similar to other design/draw applications you may have used, the resize handles allow you to resize the widget.
￼
Side Constraint Handle: The side constraint handles, represented as circles on the sides of each widget, let you specify the location of the widget. For example, you can use a widget's left side constraint handle to always be to the right of another widget by 24dp. These are also referred to as anchors throughout this codelab.
￼
Baseline Constraint Handle:
The baseline constraint handle helps you align the text fields of any two widgets, irrespective of the widget sizes. This is helpful for example, when you have two widgets of different sizes but want the text inside to be aligned horizontally.
￼
Rules for the Constraint System
An anchor of a widget in the layout can be connected to any anchor of another widget, with the following exceptions:
Anchors of different types cannot be connected.
* Anchors on different axis, such as left and top anchor cannot be connected.
* Baseline constraint handles can only be constrained to another baseline.
Connecting anchors that would result in a cycle are not permitted.

================================================================



5. Build the starter app
Now you're ready to build on top of the starter project and build your constraint layout.
Open the res/layout/activity_main_start.xml from the left navigation bar.
Including the dependency on constraint-layout
The constraint-layout is built as a separate support library that works on all Android versions back to Android 2.3 (Gingerbread). The starter app already includes the dependency in app/build.gradle. For apps that you intend to build with ConstraintLayout, add the following compile dependency:
dependencies {
  ...
  compile 'com.android.support.constraint:constraint-layout:1.0.0'
}
Navigate to res/layout/activity_main_start.xml
The XML version of the layout already has an empty ConstraintLayout element included in the codelab project. ConstraintLayout was built from the ground up to be used in conjunction with the UI Builder as we believe it makes for a more intuitive and powerful experience. Nonetheless, you still have access to, and can edit, the corresponding XML.
<?xml version="1.0" encoding="utf-8"?>
<android.support.constraint.ConstraintLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    android:layout_width="match_parent"
    android:layout_height="match_parent">

</android.support.constraint.ConstraintLayout>
Switch to the Design view shown as a tab at the bottom of the editor window.
￼
Add an ImageView to the layout
The first task is to add an ImageView to the layout. In the design window, find the ImageView on the Palette and drag it into the layout.
￼
As soon as an ImageView is dragged onto the layout, the UI Builder asks for a resource to use. The constraint-layout-start sample already includes resources to make it convenient for the codelab. Go ahead and choose the @drawable/singapore resource.
Once selected, the ImageView appears on the layout you can click and hold the corner to resize the image as mentioned in the 'Constraint System Overview'
￼
Add a TextView to the layout
Now let's drag a TextView from the palette onto the layout.
￼
We see a few warnings in the UI Builder which are due to missing contentDescription attribute on the ImageViewand the hardcoded text on the TextView. Content Description attributes are important for building accessible applications. For this codelab, let's use an already available resource @string/dummy for the attribute.
On the right, an Inspector pane lets you change the various attributes of the selected widget.
￼
1. Select the ImageView and add @string/dummy into it's contentDescription attribute.
2. In the Inspector pane, you can also see the other attributes of the ImageView. Change the scaleType to be centerCrop for the purposes of this codelab.
3. Next, we select the TextView and use the Inspector pane to modify the text value of the TextView to be @string/singapore.
At this point, we have two views in the layout. In the next section, we'll learn about how to create constraints between the views.





==================================================================================






6. Creating Manual Constraints
To create a constraint, you need to click and hold the mouse on a given handle, and drag it to another widget's constraint handle. Once the anchor is green, you can release the mouse to finalize the constraint creation.
￼
Important: The UI Builder automatically starts with "Autoconnect" mode enabled. Since we are learning about manual constraints in this section, disable "Autoconnect" mode by clicking on the 
￼
 action or ensure that it's already disabled.
Before we start, ensure that we have an ImageView and a TextView in the layout. Our goal here is to create constraints between the ImageView, the container and the TextView widgets already on the layout.
Let's assume that we want the TextView to be below the ImageView in our final layout. To accomplish this, we can create a constraint between the top anchor of the the TextView and the bottom anchor of the ImageView as shown.
￼
Deleting a Constraint
Use the 
￼
 delete constraints button that appears in the layout to remove all constraints on the selected widget.
To delete a single constraint, click on the specific anchor that sets the constraint.
If you instead want to delete all constraints in the entire layout, use the menu icon.
The next step is to create a constraint between the top anchor of the ImageView to the top of the layout.
￼
Finally, we can also use the left and right constraints to anchor the ImageView at the center of the layout.
￼
This section showed the basics of how to create constraints between widgets by dragging connection lines. At this point you can explore the views and the UI Builder by adding other elements. In the next section we'll learn about the Inspector.
Creating a baseline constraint
To connect the baseline of a widget to another baseline, mouse over the widget and wait for a few seconds for the baseline constraint to appear before connecting.
￼







===============================================




7. Getting familiar with the Inspector
In this section we take a look at the view Inspector. The Inspector is on the right side of the UI Builder. In addition to listing the various properties of the selected widget, it also shows how the view is aligned and any constraints.
* Go ahead and remove the TextView from the layout.
* Create a constraint between the bottom anchor of the ImageView and the bottom of the container.
The UI Builder should look like the following.
￼
The inspector shows the widget in the center in a square block. The following section describes the various elements and their uses.
Margins: To the left, right, top and bottom outside the widget are the margins. You can change the margins by clicking on the value and setting it to a different value. In the screenshot above, the margins are set to 16dp.
Deleting a constraint: Clicking on the lines connecting the widget to the container in the Inspector, also gives you an option to delete the constraint. Note that deleting a constraint can also be accomplished by clicking on the existing constraint handle.
Positioning the widget relative to constraints: When you have at least two opposing connections on a widget, such as the top and the bottom, or the left and the right, you can see a slider which lets you adjust the position of the widget along the axis of the opposing connections. This is also known as horizontal or vertical bias. You can adjust the horizontal and vertical bias and change the orientation to see that the bias is maintained. Alternatively this can also be achieved by moving the widget to the desired location.
Go ahead and change the vertical bias to 75% and the horizontal bias to 75%. The image below can be used as a guide.
￼
Controlling the inner dimensions of the widget: The inner lines within a widget let you control the dimensions. You can click on the particular lines to see it in action.
Here is a zoomed in view of the widget in the Inspector pane. Clicking on the inner lines of the inspector pane widget cycles through the options mentioned below.
￼
￼
Fixed: This option lets you specify the width/height of the widget.
￼
AnySize: This option lets the widget occupy all available space to satisfy the constraint. In other words, this is more like match constraint. This is different from match_parent, which makes the widget occupy all available space of the parent view.
￼
Wrap Content: This option only expands to fill the widget with the contained element such as text or a drawable.
￼
AnySize is independent of the container. If the ImageView is constrained to a button, making it AnySize would only expand it to fit up to the button.
￼
Figure A: Shows the ImageView before 'AnySize' is applied to its width.
￼
Figure B: Shows the ImageView after 'AnySize' is applied to its width.
To view and edit all other attributes for a given widget, click 
￼
 at the top right of the Properties pane.
In this section, we explored the Inspector. The goal of the Inspector is to let you edit all properties and constraints without leaving the UI Builder.


===============================================================================
