---

title: "Learning iOS: Week 3/7 Homework"
date: 2014-04-30 07:31 UTC
tags: 

---

This week, we start to learn how to use custom data in our static views. Real apps will use real data, so we finally get a chance to see how things can look and feel as we get closer to dynamic data.

##Creating Custom Cells

This was harder than it looked (starting from scratch), but after doing it once it isn't so bad. 
First you start by creating a CustomTableCell class that inherits from UITableViewCell 

Now in the xib file, adjust the height so the cell is much larger. This can be found in the right side panel under "Show the size inspector", it's an icon that looks like a mini ruler. Then add your labels and UIImageViews. Once that's done, create IBOutlets in your CustomTableCell.h file.

Also be sure to click the table view cell, then in the right panel click "Show the attributes inspector" and add some name to the Identifier. I used "myCell".

In the CustomTableCell.m file add this line of code

```Objective-C
- (id)initWithStyle:(UITableViewCellStyle)style reuseIdentifier:(NSString *)reuseIdentifier {
    self = [super initWithStyle:style reuseIdentifier:reuseIdentifier];
    if (self) {
        //
    }
    return self;
}
```

##Create your TableView

Create a new file that is a subclass of UITableViewController. Import your CustomTableCell.h file. Create an IBOutlet from the tableview to your TableView.m file. Then Create datasource and delegate for the table

```Objective-C
self.tableView.datasource = self; 
self.tableView.delegate = self; 
```

This will give you access to the methods that power table view, so you can customize information in cells and tell the table view what/how many cells to use.

Uncomment and edit some of the lines below

```Objective-C
- (NSInteger)numberOfSectionsInTableView:(UITableView *)tableView
{
    // Return the number of sections.
    return 1;
}
```

This tells the tableview how many sections are in this view. Since we are listing the same items over and over we can just return 1;

```Objective-C
- (NSInteger)tableView:(UITableView *)tableView numberOfRowsInSection:(NSInteger)section
{
    // Return the number of rows in the section.
    return self.menuTableItems.count;
}
```

I created an array and stored it in self.menuTableItems so here I am just returning the total number of rows I need the table to have.

```Objective-C
- (UITableViewCell *)tableView:(UITableView *)tableView cellForRowAtIndexPath:(NSIndexPath *)indexPath
{
MenuTableViewCell *cell = [tableView         dequeueReusableCellWithIdentifier:@"myCell"];

if (!cell) {
[tableView registerNib:[UINib nibWithNibName:@"MenuTableViewCell" bundle:nil] forCellReuseIdentifier:@"myCell"];
cell = [tableView dequeueReusableCellWithIdentifier:@"myCell"]; 

}

cell.menuLabel.text = [NSString stringWithFormat:@"%@", self.menuTableItems[indexPath.row]];
    return cell;
}
```

This one is pretty hefty, but ultimately it is the data that tells the tableview what cell to use in each row. This is where we define our custom cell and tell the tableview how to use and reuse them. This is where you would tell the cell what image to use, what text for the labels, etc.

##AFNetworking setting imageview on a cell

First you need to install the AFNetworking pod. Once that is done, import into your main view controller 
`#import "UIImageView+AFNetworking.h"`

Then you will have access to a method that can set an imageview using urls like this for example 

```Objective-C
[cell.profilePic setImageWithURL:[NSURL URLWithString:@"https://pbs.twimg.com/profile_images/421403454104297472/zgjnoNmf.jpeg"]
```

It handles all the fetching, caching, and asynchronous requests for you!

##Creating models and fake data

When creating models its important to think of the attributes of your model. For example if you are making a notification model, we need to know things like 
* The type of notification * Who it was from * A short snippet of what it is * When it was done (timestamp)

This will help when we need to build notification objects from the json response.

The `-(id)initWithDictionary` method is an instance method so it acts on an instance of notification e.g.

`Notification *newNotification = [Notification alloc] initWithDictionary:....;`

So this will take a dictionary and then go to the initWithDictionary method and build the object. We of course have define initWithDictionary in the implementation file Notification.m. Ultimately what it does is it sets all the values for the Notification object and returns it.

`+ (NSArray *)notificationsWithArray:(NSArray *)array`

This class method can be called on the class like so

`[Notification notificationsWithArray:[NSArray arrayWithObjects...]]`

class itself. This is because its a method/helper relevant to the Notification class we made, rather than a direct manipulation of a notification object (like changing the objects data)

So all this method will do is it will accept an array of dictionaries (from the json response) and then loop through each of them running `initWithDictionary` on it and adding that to a new array. Then once its done looping through all of the dictionaries it will return an array of notification objects. These objects are what we will loop through to create our different table cells.

Lastly the `fakeNotifications` method just creates a fake hardcoded array of dictionaries, which we then pass to notificationsWithArray to create a fake array of notifications (dummy data).

I didn't show any code so we could stay focused on the concepts that each method is trying to perform!

Next week we dive into animations