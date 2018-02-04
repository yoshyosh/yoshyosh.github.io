---

title: "Learning iOS: Week 2/7 Homework"
date: 2018-02-04 07:01 UTC
tags: 

---

http://stackoverflow.com/questions/1785008/keeping-a-uibutton-selected-after-a-touch

Creating a login page 
Detecting form field validation 
Loading states for feed view 
Modal view slide ups 
UIScrollView for more content 
Alert and action views

Wooooot! Week 2 and I am already tasting how close we are to building a full app. This week's homework focused a lot on adding some transition logic to our app. Things like incorrect password, transitions if it is correct, scroll views so you can scroll through a lot of content, and using loading indicators with time delays to present content.

There were a few hiccups while getting through the homework. I still have questions on things like button state. When you tap a button it goes into the highlighted state, but I need it to stay in that state while we check for the correct username and password. I'm still not sure how to do this, so I will check in with the mentors and report back.

##How to create & use functions with performSelector

I also learned how to use performSelector. In the web, I could just make functions in javascript and call them by first creating a function

```
function anExampleFunction(){
}
```

Then calling it anywhere in the code like this: `anExampleFunction();`

But in Objective-C, first you need to create the function:

```Objective-C
- (void)anExampleFunction:(id)sender {
}
```

Then to make it run, you need to put it in the viewDidLoad section (this is equivalent to document.ready) and run it like this:

`[self performSelector:@selector(anExampleFunction:) withObject:nil afterDelay:0];`

So you can see how much more verbose this is and possibly confusing. Let's start by explaining

```Objective-C
- (void)anExampleFunction:(id)sender {
}
```

`- (void)` is the return type. In objective-C, you have to be religious about what types you are returning, like when you create a variable, or a function to return a variable. The cool thing about - (void) (doesnt matter if it has a space between the dash) is that it literally returns void, or nothing. So this is what you do when you want to just perform some actions but not return any value.

anExampleFunction is just the name of your function. You should try to keep the naming conventions very descriptive just like Objective-C does with its methods. So for example, if you are checking a password, literally call it checkLoginPassword. The colon at the end is similar to the () in a javascript function, where you will place the object/variable to be passed into this function. Think of it like if I was making a list of items you will need for a camping trip: 
1. Wood 
2. Food

The colon after camping trip: signifies the beginning of what is needed.

`(id)sender` is a wildcard type. It basically says, accept any type of object and dynamically figure out what it is. Sender is the object that invoked this function, you will see this being a lot more useful in things like a table view list of things to bring on a camping trip. When you tap any of those items maybe a screen would slide in giving you more details. By using sender, we will know exactly which object was tapped and be able to get all the properties from it such as the name of the item, its position relative to the rest of the list, etc.

`[self performSelector:@selector(anExampleFunction:) withObject:nil afterDelay:0];`

So here, the [] is syntax to tell the compiler to run this function with these methods. Its equivalent to doing something like:

```Objective-C
user.firstname
[user firstname]
```

In Objective-C you use self alot so you can tell the compiler what object you are performing this method on. In this case, self would be referring to the FeedViewController, or the feed view. You can think of it as a container for all of the things happening in your feed, since you are building the posts inside of it. The main parent, the big daddy, you get the picture.

`performSelector` is just a method that says perform this selector, I think objective-C likes to call what we are used to calling functions, selectors.

`anExampleFunction:` function name and the colon that makes it capable of accepting objects

`withObject:nil` this is where we put a single object that we want to pass. If you want to pass multiple objects, you need to put them in a NSDictionary or NSArray, then loop through them in your function.

`afterDelay:0` is measured in seconds. So you can put a delay on how long it takes before this line of code will run.

With all of these combined, you can now do a ton of stuff. You can chain a bunch of functions based on eachother, and just make the code cleaner and more usable. Functions are a great way to keep your code dry and increase resuability. `willHideKeyboard` and `willShowKeyboard` are good examples of this. There are many times you will need to control the keyboard functionality, these functions will help you use them wherever necessary.

##UIScrollView

`UIScrollView` caused me some trouble because there are so many things that are automatically moved and changed with it. I still don't understand why things shift around automatically. I had to reset the positions of X and Y for both the scrollview and contained view to 0. I also needed to turn off autolayout in the "Show file inspector" for the scrollview.

##For Control Events

Detecting when there is a change in text field 

```Objective-C
[self.emailTextField addTarget:self action:@selector(textFieldDidBeginEditing:) forControlEvents:UIControlEventEditingChanged];
```

This was a little confusing at start. The code above is short form for one of the few control events that happen on a textfield. It will get the job done but there is a better way to handle event delegation.

What is event delegation? It's literally what do you delegate something to do when an event happens. For example, if there is a change in the textfield, first we need to register that there was an event (the change in the textfield) and delegate (tell a function) what should be done when that happens.

`self.emailTextField.delegate = self;`

This tells the code to start listening to all of the events that happen on this emailTextField and listen to them on the parent view controller. Now we still have to do one more step, we have to tell the parent view controller to listen to these events. In the LoginViewController.h file:

`@implementation LoginViewController : UIViewController <UITextFieldDelegate>`

Now if you cmd + click the UITextField class in the LoginViewController.m file and scroll down you will see this:

```Objective-C
- (BOOL)textFieldShouldBeginEditing:(UITextField *)textField;        // return NO to disallow editing.
- (void)textFieldDidBeginEditing:(UITextField *)textField;           // became first responder
- (BOOL)textFieldShouldEndEditing:(UITextField *)textField;          // return YES to allow editing to stop and to resign first responder status. NO to disallow the editing session to end
- (void)textFieldDidEndEditing:(UITextField *)textField;             // may be called if forced even if shouldEndEditing returns NO (e.g. view removed from window) or endEditing:YES called
- (BOOL)textField:(UITextField *)textField shouldChangeCharactersInRange:(NSRange)range replacementString:(NSString *)string;   // return NO to not change text
- (BOOL)textFieldShouldClear:(UITextField *)textField;               // called when clear button pressed. return NO to ignore (no notifications)
- (BOOL)textFieldShouldReturn:(UITextField *)textField;              // called when 'return' key pressed. return NO to ignore.
```

These are all of the delegated functions we now have access to when an event happens. So all we simply do is take something like: 

`- (BOOL)textField:(UITextField *)textField shouldChangeCharactersInRange:(NSRange)range replacementString:(NSString *)string;`

And place it in LoginViewController.m and we will know everytime a change in that text field happens. This allows us to do things like check for the correct password, or do any form validation/button enabling and disabling while the user is typing in the form fields.

Test it with this:

```Objective-C
- (BOOL)textField:(UITextField *)textField shouldChangeCharactersInRange:(NSRange)range replacementString:(NSString *)string 
{
NSLog(@"Text is being changed"); 

}
```

So every class object has certain delegate events. Like `UIScrollView` has a lot that are precise on when you start scrolling, scroll to top, etc. This can be used to hide and show navigation bars to give the user more viewing space while scrolling, but still reveal navigation on a certain directional scroll. Delegates are incredibly powerful, they are literally like your javascript event delegation that you oh so love.

##Custom Tap Events

http://stackoverflow.com/questions/19218080/tap-gesture-not-recognized-on-uiimageview

Here you are creating a gesture to track, in this case tap. After you assign that gesture to be tracked on let's say a UIImage, when you tap the UIImage, then it should perform the selector you assigned to that tap.

So this is similar to using performSelector's and the delegate explained above.

##Modal Views & Screen Transitions

![Mobile view flipping like a card](http://i.imgur.com/4wESHoK.gif)

![Mobile view sliding up another view on tap](http://i.imgur.com/KpX7FcB.gif)

![Mobile view fading out and in](http://i.imgur.com/m0Mn9DU.gif)

As cool as they look, they are actually much easier to implement than you would think (coming from an HTML/CSS/JS background).

First you initialize the view that you will be showing 
`UIViewController *vc = [[UIViewController alloc] init];`

Then you set the modal transition property on this view 
`vc.modalTransitionStyle = UIModalTransitionStyleCrossDissolve;`

Then you just invoke that action 
`[self presentViewController:vc animated:YES completion:nil]`

3 lines of code for all of that awesomeness.

##UIAlert and Action Views

Finally UIAlert and UIAction Views are great ways to get user input or to slow a user down if they have done something and need to be notified. You literally just create a UIAlert or Action by first initializing it:

```Objective-C
UIAlertView *alertView = [[UIAlertView alloc] initWithTitle:@"Incorrect Password" message:@"The password you entered is incorrect. Please try again." delegate:self cancelButtonTitle:@"OK" otherButtonTitles:nil, nil];
```

Then calling it where need be 
`[alertView show]`

This week of the homework literally shows you how to piece together an application. Next week will deal with custom data so we can start customizing the feed and views rather than it just being static.