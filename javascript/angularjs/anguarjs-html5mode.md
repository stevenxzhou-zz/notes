## Reasons to use html5mode in AngularJS?

### About html5mode
AngularJS $lcoation provides an option to make use of HistoryAPI in HTML5 standard. By setting html5mode to be true, it will not only make HistoryAPI ready to use, but also, it provides fallback for older browsers which means it will automatically turn back to hashbang mode when it comes to an older broweser.

### What advantages and disadvantages by using html5mode over hashbang mode?
By setting html5mode to true to enable HistoryAPI will reduce the times for refreshing a page by redirecting the urls user stored in HistoryAPI(pushState). When user click the "Back" button on the browser, popState will get called, and get the url in the history. We can manually refresh teh key parts of the page by using that URL or AngularJS has taken care of that part for the code writen in Angular, to refresh the parts only when angularjs sees it's  necessary.

### Why does angularjs keep hashbang as default mode?
At the moment they provide this option, only few latest version of browsers support this, so they haven't done enough tests on all the old and modern browsers and not sure what other implicit problems would be caused by HistoryAPI of HTML5, so they implemented it in a more conservative way. It's up to user's own will fo whether or not it's necessary to enable the html5mode.

It might also because they do it to endorse Google's search engine.


### Reference
[1] Chris Sevilleja: [Pretty URLs in AngularJS: Removing the #](https://scotch.io/tutorials/pretty-urls-in-angularjs-removing-the-hashtag)  
[2] [MANIPULATING HISTORY FOR FUN & PROFIT](http://diveintohtml5.info/history.html)  
[3] [Why should we avoid using hashbang url?](https://www.quora.com/Are-hashbang-URLs-a-recommended-practice)  
[4] Tim Bray [Broken Links](http://www.tbray.org/ongoing/When/201x/2011/02/09/Hash-Blecch)  
