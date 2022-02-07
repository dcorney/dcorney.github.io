## Sources for my personal website, dcorney.com

Now hosted on Github

Locally, cd dc/website, then `jekyll serve` for local editing.

There's no need to do `jekyll build` to actually create site files before pushing to git, as github pages have their own jekyll builder. Just push changes to a new branch, then can merge (or push to main if you feel brave). The new HTML will appear at dcorney.com a few minutes later.

Slight bodge: pages with a date in the year 8888 appear only in an unlinked-to folder dcorney.com/ideas - the logic of this bodge is in _pages/08_blog.md

TODO: maybe try post.categories "contains" thought?

[Based on the tutorial](http://taniarascia.com/make-a-static-website-with-jekyll)

[Handy documentation here](https://shopify.dev/docs/themes/liquid/reference/basics/operators)