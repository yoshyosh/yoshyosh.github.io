---

title: "Learning iOS: Week 1/7 Homework"
date: 2018-02-04 06:58 UTC
tags: 

---

_Creating UIViews programatically 
Creating UIImage views 
Creating and positioning Labels 
Exporting assets from sketch 
Simple IBAction/Outlet_

I started off [Week 1 homework](http://guides.thecodepath.com/ios/Week-1-Homework) by programming the views. It required a lot of CGRect and absolute positioning. The code started to feel verbose but after checking in with the mentors that's the way the code looks when doing it programmatically. I learned how to make things tidier.

```Objective-C
CGRect postBgRect = CGRectMake(0, 0, 300, 570);
postBgRect.origin = CGPointMake(10, 10);
UIView *postBgView = [[UIView alloc] initWithFrame:postBgRect];
postBgView.backgroundColor = [UIColor whiteColor];
postBgView.layer.cornerRadius = 2;
[backgroundView addSubview:postBgView];
```

Instead of using a separate line to do 
`postBgRect.origin = CGPointMake(10, 10)`

It's better to combine it in the original CGRect 
`CGRect postBgRect = CGRectMake(10, 10, 300, 570);`

Origin is just a separate method on CGRect. It is the first two inputs (of four) in CGRectMake. That helps clean up one line. Another mistake I was making was adding the subViews at the VERY end of the file, rather than right underneath the newly created view section (the correct way is displayed above). The reason why this is better is because everything about whats happening with this newly created view is in one spot. You dont't have to bounce back and forth from the bottom of the file to the lines of code that created this view.

Nesting the views and absolute positioning with the CGRectMake's was a common pattern. I started getting worried about how much absolute positioning was going on. With a web background it's bad practice to position absolute everything. After discussing this with the mentors he pointed out that by doing this, if the iPhone screen was a different size or flipped to landscape orientation, the elements would all be positioned incorrectly. So we discussed focusing on nibs moving forward (we will be able to use things like autolayout to keep things positioned properly).

I re-did the homework using nibs and it was much faster. I didn't have to worry about programatically creating the sizes and positions since it was all visual in the nibs. A good way to size and position using the visual nib is to use the size inspector pictured below.

Using nibs was faster. It required IBOutlets so that I could create variables that could be changed easily in the code.

### Design/Sketch

I also learned about exporting assets. Most of the designs in sketch are done at 2x (since we are using 640x1168 layouts) which means 2 times the original size. So it's important to remember how big the icons you are making will be at 1x for the editor. Sketch automatically does 1x and 2x assets but you have to remember where you are benchmarking the sizes from. For example if you pull in a 320x568 image of the interface, and you measure the height and width of an icon, you will be measuring it at 1x (one times it's size), so you must create 1x assets with the height and width you measured. This may sound obvious but when first getting started you can get a little confused and forget which layout you are measuring off of.

Overall I learned a lot when it comes to laying things out on the screen. To the point where I can make single page mockups with navigation. This week we haven't gone over any events/touch animations so the prototypes won't do much. There will be a lot more of that in next week's lesson as we go over UIScrollView as well as event handling on touch/tap.