# Welcome to my first blog
Why I am using github pages? Here's the answer-
http://jmcglone.com/notes/2014/05/03/using-github-to-create-and-host-a-personal-website

Link(s) to get started (I clicked on almost all guides there :P) -

https://jekyllrb.com/resources/

Going through jekyll official tutorials, i came about [this series by Giraffe Academy](https://www.youtube.com/watch?v=T1itpPvFWHI&list=PLLAZ4kZ9dFpOPV5C5Ay0pHaa0RJFhcmcB&index=1)

started on 23-05-19
at 12:05
started the youtube playlist

and installing the basic jekyll and bundler library through an error. Yay!
started reinstalling ruby it but got an upgrade for my linux distro
after about half an hour or so done!

coming back to installing ruby, this time doing it manually from their
git repo instead of relying on my package manager.

installed rbenv (a ruby environment like venv for python).

installed ruby 2.6.3 (the latest one) and then made it globally available

and it didn't work!

using the package manager again :(

used root permissions and tried using my brain for a custom install it so it failed miserably (don't want to go in the details). Reinstalled it using the [official instructions](https://jekyllrb.com/docs/installation/ubuntu/) and finally it worked!

create a website using jekyll and served it on localhost (my computer)
```bash
$ jekyll new blog
$ cd blog
$ bundle exec jekyll serve
```
