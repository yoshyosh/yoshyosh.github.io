---

title: "Wikipedia SERP redesign contest Part 3: Conclusion"
date: 2014-02-18 04:01 UTC
tags: 

---

![Wikipedia redesign with suggest search results dropdown](https://lh4.googleusercontent.com/-pupn3D4CsLA/Tl7iWEQXbbI/AAAAAAAAAfs/0Qkq9NFLmis/s560/wikiPreview.jpg)

The contest ended about 2 weeks ago and here are my final designs. I am going to go over the lessons and subtle design tricks I learned during this process. The key points I will discuss are text colors, interaction design, and why I designed or chose certain ways to layout content. Let’s start by going over the typography and text color. 
TL;DR Final Design Pics: [Part 1](https://lh3.googleusercontent.com/-t672hZWTQYk/Tl7w4WY6E6I/AAAAAAAAAiQ/Qns0JXXeZnk/s1160/wikipediaSearchResultsRedux.png) [Part 2](https://lh5.googleusercontent.com/-hKMSPDPiGZc/Tl8GYsS3KGI/AAAAAAAAAiw/BysnhF92yHA/s1160/wikipediaSearchResultsPicturePrev.png) [Part 3](https://lh4.googleusercontent.com/-gNmD3c0aOm4/Tl8G9CsZfpI/AAAAAAAAAjA/th3cG7GbL3A/s1160/wikipediaSearchBox.png)

Old Redesign:
![One search result with multiple blue colors](https://lh6.googleusercontent.com/-ja_GdY9JePE/Tl7kBy1jBJI/AAAAAAAAAgM/F6Q9sJh3arE/s500/wikiOldtextcolors.jpg)

New Redesign:
![Two search results with uniform blue color](https://lh4.googleusercontent.com/-Qtoqg33FGck/Tl7ji5mVflI/AAAAAAAAAf8/nReTt4z8L9c/s560/wikitextcolors.jpg)

Here you see both the final version and initial version of the text color and layout I chose. You’ll notice that the top image does not use underlined text and appears more vibrant. There are a couple of things going on here. First brighter blue text, this made the search results look less dull and boring. Second bigger font and Georgia rather than pure Arial. If you ever find yourself having a hard time differentiating 2 pieces of text try messing with the type font. Georgia as a header followed by Arial body text looks really nice. Lastly, probably the least noticeable is the gray en.wikipedia.org text at the bottom. Since every article on this SERP (Search engine results page) leads to an internal wikipedia article, the only purpose that gray text serves is to assure the reader that they are staying on wikipedia. Since most SERP like Google, or Bing lead to external sites, you normally see them using these links in green.

![One Google search result](https://lh6.googleusercontent.com/-ZQQVM9gUPVA/Tl7naxNNxKI/AAAAAAAAAgc/zZjBnwl6H0M/s530/googleSerp.jpg)

Using gray for en.wikipedia.org gives it less visual weight and doesn’t take away from the more important content on the site.

There were 2 key dynamic interactions that were designed in hopes of improving content discovery. The first was the standard auto complete upon searching but it includes a little twist.

![Wikipedia redesign with suggested search results that include images](https://lh3.googleusercontent.com/-4CSUDJTAyMg/Tl7oz72jl_I/AAAAAAAAAgs/9BQ23h0LPcU/s560/wikiAutocomplete.jpg)

The top half acts the same way an ordinary google search would. As you type in the search bar the auto completer starts listing the most common searched phrases. The second half lists the most popular articles based on the search. If any of the pictures/titles catch the users eye they can dive right into the content. If that wasn’t quite the information they were looking for, they can go through the regular SERP process.

The second dynamic interaction occurs while browsing images on the SERP. When the user hovers over an image, it overlays its neighbor images, giving the user a better view on what it may be and enticing them to click.

Before hover:
![Grid of dinosaur photos](https://lh5.googleusercontent.com/-7QOoMpYlVlg/Tl7rogCIYEI/AAAAAAAAAhM/EjFzuT-GldI/s560/wikipopoutimg_before.jpg)

After hover:
![Slightly popped out dinosaur photo over other grid of photos](https://lh3.googleusercontent.com/-DqlYUi1Qz-o/Tl7rO8n7m0I/AAAAAAAAAg8/4IN1l94abNU/s560/wikipopoutimg.jpg)

Once the user clicks the hovered image, rather than taking them directly to an article, a large version of the picture with accompanying leading article text will appear.

![Modal card containing dinosaur photo and text description](https://lh3.googleusercontent.com/-mwC7I50DKJA/Tl7tlUrYhDI/AAAAAAAAAhw/MSwKhpL8eGY/s560/wikiSERPpreview.png)

If the user wanted to disable this effect/get rid of the picture all they would have to do is ‘hover out’ from either the large or smaller image. Another way this could be done is using the classic modal window layout, where everything is grayed out in the background, forcing the user to focus only on that article. The reason I chose the ‘hover out’ to disable idea is because I am hoping the user will explore more content as quickly and seamlessly as possible due to how quickly they can enter and leave a clicked photo.

Finally, heres a link to the [final result](https://lh3.googleusercontent.com/-t672hZWTQYk/Tl7w4WY6E6I/AAAAAAAAAiQ/Qns0JXXeZnk/s1160/wikipediaSearchResultsRedux.png). Two parts of the layout that I did not mention will be easier to understand when looking at the overall design.

The first part is the ‘Results Filter.’ It was designed so that users could browse content by both articles and (potential) Multimedia. These would be things like images, audio, and video. I believe those forms of content inevitably will play a larger role on an internet based encyclopedia. So this filter mechanism would allow the user to easily browse through more engaging multimedia or stick with the more academic article approach.

The second part is the categories and subcategories section. This is something I found hidden deep within Wikipedia, as I navigated the site. The purpose of it is to serve as further content discovery. It lists articles and sections that can be very quickly scanned, exposing the user to topics they might not have known existed.

Overall the redesign helps improve content discovery. Design wise it is not far from normal SERPs. For the contest this is both positive and negative. Usability wise, users who are accustomed to regular SERPs, will have an easy time adjusting to this page. The bad part is it doesn’t have the ‘radically different redesign’ factor. I’ll definitely take usability over that anyday.


