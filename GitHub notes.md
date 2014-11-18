
# Mike's GitHub notes 
## Learning GitHub & Markdown 

Let's see if ***these*** changes show up :)

**Resources I'm using**
- [ReadWrite tutorial for GitHub](http://readwrite.com/2013/10/02/github-for-beginners-part-2) 
- [Write with Markdown on Google Drive](https://www.youtube.com/watch?v=VAx_Xf0KNfg)
- [SatckEdit on GitHub](https://github.com/benweet/stackedit)
- [Markdown cheatsheet](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet),  [Markdown basics](https://help.github.com/articles/markdown-basics/) and [GitHub Flavored Markdown (GFM)](https://help.github.com/articles/github-flavored-markdown/)
- [GitHub code school](https://try.github.io/levels/1) 
- [Git
- sdf 

----------

**git commands**
  - git status
  - git add
  - git commit
  - git push
  - git pull

----------------


**Mike took 'data objects' from Automatic. What do Fitbit, Jawbone, & Nest say? let's benchmark with them. Keep it simple.**

  - Specify read-only. Jawbone & Fitbit are read & write.
  - Specify JSON response only. Fitbit does JSON & XML.
  - 

**Jawbone** 

  - [pull data](https://jawbone.com/up/developer/structure) contains data (common objects & collections) and metadata (info related to the request itself)
  - [push notifications](https://jawbone.com/up/developer/pubsub) are "pub sub"
    - **Berman**, is there a different between a "callback" and a "push event"? 
  - [jawbone oauth diagram](https://jawbone.com/up/developer/authentication)

**Fitbit**

  - [pull Resources](https://wiki.fitbit.com/display/API/Fitbit+Resource+Access+API)
  - [push Subscriptions](https://wiki.fitbit.com/display/API/Fitbit+Subscriptions+API) "**subscribe** to any changes in a user's data." "notify via an HTTP callback"
  - [fitbit oath diagram](https://wiki.fitbit.com/display/API/OAuth+Authentication+in+the+Fitbit+API#OAuthAuthenticationintheFitbitAPI-TheOAuthFlow)

**Nest**

  - [subscriptions](https://developer.nest.com/documentation/cloud/nest-api-intro) that clients "listen" to for event changes
  - they don't seem to have the ability to pull datasets   
  - [Nest's oauth diagram](https://developer.nest.com/documentation/cloud/authorization-overview)




