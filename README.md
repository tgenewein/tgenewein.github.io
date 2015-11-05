# tgenewein.github.io

Source for personal homepage - using [Jekyll](http://jekyllrb.com/). The website is based on the theme *Minimal Mistakes* (https://github.com/mmistakes/minimal-mistakes) - kudos to Michel Rose for providing this awesome theme that comes with a very good documentation.

The original theme has been modified to allow for the following:
* Posts can be marked as `publication: true` - in this case the post will get a special footer and will be automatically pulled into the publication list.
* Publication list (automatically populated from posts)
  * distinguishes between Papers, Posters and Talks and sorts them into corresponding lists
  * has a navigation panel based on the automatic TOC
* Custom footer for posts that announce a publication
  * link and download buttons
  * citation-string
  * in order for this to work the following must be specified in the frontmatter:
    * `publication: true`
    * `pubtype: "paper"` can also be `"poster"` or `"talk"`
    * `publink: ""` (optional) string pointing to website of publication (will produce a button below the title)
    * `downloadlink: ""` (optional) string pointing to (internal or external) download location of publication (will produce a button below the title)
    * `pubtitle: ""` string for publication list entry
    * `citeas: ""` string that provides citation in plain-text
* Research topic navigation bar (based on automatic TOC)
  * any page can be marked with `researchtopicpage: true` to indicate that it is a page for a special research (sub-)topic. On the research-overview page, links to all the researchtopic-pages are automatically provided in a sidebar panel (based on automatic TOC)
  * additionally specify `shorttitle:` which will be the title for display in the navigation panel (TOC)


The changes made here were done with one specific site in mind and are therefore sometimes quite crude - this is not meant to be a universal template (unlike the well written original theme). Feel free to look at the source on github or the live website [here](http://tim.inversetemperature.net), clone or fork and modify in which ever way you want (everything is MIT licenced). No need to mention me (but go ahead if you feel like it) - but please consider giving credits to Michael Rose and the original Minimal Mistakes theme.
