---
title: Fix gh-pages rejection of new pushes
createdAt: 2020-04-17T23:10:44Z
---

# Fix gh-pages rejection of new pushes

https://stackoverflow.com/questions/52087783/git-push-to-gh-pages-updates-were-rejected

````
git checkout master # you can avoid this line if you are in master...
git subtree split --prefix build_production -b gh-pages # create a local gh-pages branch containing the splitted output folder
git push -f origin gh-pages:gh-pages # force the push of the gh-pages branch to the remote gh-pages branch at origin
git branch -D gh-pages # delete the local gh-pages 
````