# Using reviewboard in a git world

To use reviewboard this assumes that rbtools are installed and the repo is configured to use it.

To start the workflow conversation I'll give an example:

```
[jbean@jbean ~/git]$ git clone git@git.example.com:product/notebooks.git
[jbean@jbean ~/git]$ cd notebooks
[jbean@jbean ~/git/notebooks] (master)$ git checkout develop
[jbean@jbean ~/git/notebooks] (develop)$ vim README.md
[jbean@jbean ~/git/notebooks] (develop *)$ git add README.md
[jbean@jbean ~/git/notebooks] (develop +)$ git commit -m "Edit README comment local commit"
[develop f2f9b5c] adding stuff to README
 1 file changed, 1 insertion(+)
[jbean@jbean ~/git/notebooks] (develop)$ rbt post
Review request #15 posted.

http://rb.example.com/r/15/
http://rb.example.com/r/15/diff/
[jbean@jbean ~/git/notebooks] (develop)$
```

## Topic Branch style

```
[jbean@jbean ~/git]$ git clone git@git.example.com:product/notebooks.git
[jbean@jbean ~/git]$ cd notebooks
[jbean@jbean ~/git/notebooks] (master)$ git branch --track foobar origin/develop
Branch foobar set up to track remote branch develop from origin.
[jbean@jbean ~/git/notebooks] (master)$ git checkout foobar
[jbean@jbean ~/git/notebooks] (foobar)$ git branch -vv
* develop  f2f9b5c [origin/develop: ahead 1] adding stuff to README
  foobar   9005630 [origin/develop] adding workaround for docker device mapper bug
[jbean@jbean ~/git/notebooks] (foobar)$ vim README.md
[jbean@jbean ~/git/notebooks] (foobar *)$ git add README.md
[jbean@jbean ~/git/notebooks] (foobar +)$ git commit -m "Edit README comment local commit"
[develop f2f9b5c] adding stuff to README
 1 file changed, 1 insertion(+)
[jbean@jbean ~/git/notebooks] (foobar)$ rbt post
Review request #15 posted.

http://rb.example.com/r/15/
http://rb.example.com/r/15/diff/
[jbean@jbean ~/git/notebooks] (foobar)$ git push
[jbean@jbean ~/git/notebooks] (foobar)$ git checkout develop
[jbean@jbean ~/git/notebooks] (develop)$ git branch -d foobar
Deleted branch foobar (was 9005630).
[jbean@jbean ~/git/notebooks] (develop)$
```

## Installing pre-reqs
Install python setuptools and [install](https://www.reviewboard.org/docs/rbtools/dev/) rbtools.

```
sudo apt-get install python-setuptools
sudo easy_install-2.7 RBTools
```

# configuration


in order to setup your repo for reviewboard posts run the following:

```
rbt setup-repo
```

NOTE: This will assume that the repo is configured in the reviewboard admin.
