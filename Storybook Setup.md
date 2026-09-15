# Setting Up Your Storybook Scene

## Hierarchy
For this project, you will only have one scene you will be working with. You will want to have your hierarchy look something like this: 

Page_One (Canvas)
  *    Background (Image)
  *    Text (optional)
  *    UI Button (Next)

Page_Two (Canvas)
*  Background(Image)
*  Text (Optional)
*  UI Button (Next)

Once you have at minimum two Pages operating as Parents with the Image, Text, and Button as equal children within, you will want to begin establishing your button functions.

## Setting Up Buttons
Start by checking to turn OFF your Page_Two in the ```Inspector``` panel. You must do this in the Inspector, not in your Hierarchy.

Navigate to Page_One Button. Scroll down in the Inspector, until you see the ```onClick()``` function.

Using the ```+``` button, add a new function to your button.
*  Drag Page_Two from your hierarchy into the empty object container (labeled None (Object))
*  Click the ```No function``` dropdown menu
*  gameObject > gameObject.setActive(bool)
*  Check the box underneath to indicate you want to turn on Page_Two

Repeat the same process by adding another function to the same button to turn off the current Page_One.
*  Use the ```+``` button
*  Drag Page_One from your hierarchy into the empty object container (labeled None (Object))
*  Click the ```No function ```  dropdown menu
*  gameObject > gameObject.setActive(bool)
*  Uncheck the box underneath to indicate you want to turn off Page_One

Add Page_Three. Create the same setup, and repeat the above steps in order to work through all your storybook pages.

## Additional things to Add

You can use this process to similarly make a 'Back' button on pages, create a Title and/or Credits page at the beginning and end, etc.

If you do not want to have a button that says 'Next" you can remove the TextMeshPro/leave the textbox blank and replace the button sprite with one of your own. (i.e. an arrow, a round button, etc)

## Troubleshooting

First and foremost, your PAGES should be the outmost ```gameObjects``` in your hierarchy.

* Page_One
  *  Image
  *  Text
  *  Button
* Page_Two
  *  Image
  *  Text
  *  Button

 Then remember to use those gameObjects that are furthest out and contain BOTH your background and next button as children at equal levels for your ```onClick``` functions. Common errors incude turning on and off your images alone which will not work!

 If you are having issues with pages not turning on and off, make sure you have:
 * Checked off all ```gameOjbect``` Pages except for Page 1 in the inspector

Turning off each individual UI object within your Page (Image, Text, Button) in the Inspector will cause these elements to not be turned on when the Page ```gameObject``` is turned on. 

To relink these, you need to:
* Turn on Page_Two and all its elements manually (checkbox in inspector, NOT the eye icon in hierarchy)
* ONLY turn off Page_Two ```gameObject``` - every child linked to this object will turn off as well
* Ensure your ```onClick()``` function turns ON the Page_Two ```gameObject``` and OFF the Page_One ```gameObject```
