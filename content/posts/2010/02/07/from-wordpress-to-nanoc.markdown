Welcome to the new and improved userprimary.net.  In the spirit of
*static is the new dynamic*, I took on the project of converting this
blog from [Wordpress](http://wordpress.org/) to an autogenerated, yet
entirely static, site using [nanoc](http://nanoc.stoneship.org/).

Why would I do this?
--------------------

* With a static site, I can avoid having to keep up with Wordpress
  updates.  The upgrade dance was occuring more frequently than my
  actual posts.  Despite the streamlined update process in recent
  versions of Wordpress, it is a chore I don't need on my list.
  Besides, it is nice to worry less about security issues (oh, I'm
  asking for it now, aren't I).
  
* Everyone else is doing it.  Right?
  
* Earn a [nerd merit badge](http://www.nerdmeritbadges.com/).

* Have an opportunity to learn more about site design and CSS.  I'm a
  far way from expert, but it has been fun to start from scratch with
  an idea for the design and take a stab at making it go.

The migration
-------------

I modified the Wordpress conversion script from
[Jekyl](http://github.com/mojombo/jekyll) to suit Nanoc and added a
bit of code to extract tag data for posts and write it to the
metadata file for each post.

Using posts found on the
[Nanoc user group](http://groups.google.com/group/nanoc/) as a guide,
I built up tag and archive pages using a ``preprocess`` block in the
``Rules`` file.  Since I reorganized the site a bit, I setup some
redirects using an Apache .htaccess file.  Then all that was left was
the site design itself.

In terms of the migration, the only bit I wish I had done better was
how the feed was handled.  The blogging helper that comes with nanoc
sets an updated timestamp on each article based on its output change
time.  The result is that all entries in my feed ended up with a
recent updated time and I didn't realize this until it was out in the
wild.  The solution I came up with was to modify the blogging helper
to look for an ``updated_at`` attribute on posts.  It is used if
present and otherwise ``created_at`` is used.  This leads to more
sensible timestamps, but means that updates have to managed manually.
For now that seems good enough.  The worst part was that in finding
this solution, my feed items will change once again.  So to those few
that actually subscribe to my feed, sorry about the churn it should
not continue.

