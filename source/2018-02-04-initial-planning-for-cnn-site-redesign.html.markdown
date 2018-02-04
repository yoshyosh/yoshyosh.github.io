---

title: Initial planning for CNN site redesign
date: 2018-02-04 00:27 UTC
tags: 

---

# Initial planning for CNN site redesign

The current state of any news site is overwhelming. A majority of the industry has just translated print practices onto the internet. With physical printing in steady decline, newspaper companies want to innovate but have fell short every time. Their current solution is typical. Plenty of ad’s, with disruptive pay walls to accompany huge bricks of text and over 100 links on a single page. This is where user first design has failed.

Do you read newspapers? Why or why not? Do you ever see children reading newspapers? Fundamentally, people are looking for something interesting or captivating to devote their attention to. The headlines on the front page are the most important to catch your eye. This is where bold headlines, beautifully colored pictures, and brief insight into what may be featured in the paper take their best shot. Now as you dive deeper into the paper there are even more headlines, not as bold, as well as smaller pictures and huge walls of text. It’s not particularly inviting especially when on cheap shoddy paper. The user’s goal is to find news of interest to them as quickly as possible. Why is it that the internet news sites put up pay walls, cut you short on a story, and display ad’s in offensive places that perturb your ability to explore content? The same content is literally a google search away, for free. This is where innovation must happen.

Newspapers fundamentally have made most of their money from advertisements. Big brands and less lucrative local ad placement. Subscriptions have also played a role in the business model but again as information and news becomes more readily available there is no restriction to how you obtain it. In the past you learned about what was going on in the world by talking to others, watching TV, maybe seeing a paper at the office, or on your way to work. In order to innovate there are 2 key things to focus on. First, how can we help the user get the stories he wants to read with as little friction as possible. Second, how can we monetize this interaction without destroying the user experience.

Goals — Make it easy to browse content to discover interesting news quickly. Figure out ways to place ads effectively and encourage more use of the product/site.

Roles — Visitors, logged in members, admins, and publishers should be able to use the site. Logged in members will have more personalized views with content that they saved for later as well as insights into what their friends find interesting to read. Publishers will have easy accessiblity to adding/editing their content including pictures and video. Admins will have the ability to access analytics and delete publishers as well as malicious users.

Features — User registration, User commenting, rating systems, saving stories to read for later, following content/stories, following internal and external themes (finance vs twitter feeds), breaking news made readily available (articles and videos), Admin/Publishers: editing content.

User Stories 
- As a User I want to skim headlines so that I can find news stories that interest me in that moment. - As a User I want to save stories so that I can read them later when I have more time. - As a User I want to read story ratings so that I can prioritize what is worth reading now vs later. - As a User I want to be able to follow a story so that I can see how it progresses over time. - As a User I want to see what my friends found interesting so that I can talk with them about the news. - As a User I want to see beautiful pictures so that I understand what a news story may be about just through its picture and enjoy the content. - As a User I want to share news I find interesting with my friends so that they can enjoy the content too.

There are far more interesting things we can do with the back end of the site given how much data and relationships we create but since we are just making a prototype I am going to focus on the bare essentials of the Stories model.

Stories 
Index – List of latest news stories 
Show – View of the individual story 
New – “Create a story” 
Edit – “Update the story” 
Destroy – “Remove story from view”

Initial Html 

![Initial HTML skeleton](https://lh3.googleusercontent.com/-heAqMIRYB7Q/ThN4JPH8XiI/AAAAAAAAAPw/8G0l6kWHN3o/s560/cnn_initial.png)

This should allow developers to start making models to populate these fields and create functionality.