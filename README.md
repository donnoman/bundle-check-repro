# bundle-check-repro

## Repro Steps
```
~/code/bundle-check-repro/app

2.3.1 in app/ on master
› git log -n1
commit 87921c99934068616e297075919aaa48019d49cf
Author: donnoman <donovan@lendinghome.com>
Date:   Tue May 24 15:09:48 2016 -0700

    initial scenario setup

2.3.1 in app/ on master
› bundle check
Resolving dependencies...
The Gemfile's dependencies are satisfied

2.3.1 in app/ on master
› echo $?
0

2.3.1 in app/ on master
› git status
On branch master
nothing to commit, working directory clean

2.3.1 in app/ on master
› git log -n1
commit b7074989033a80c37caa6bec65983e924d6aae29
Author: donnoman <donovan@lendinghome.com>
Date:   Tue May 24 15:13:19 2016 -0700

    update version in core

2.3.1 in app/ on master
› bundle check
Resolving dependencies...
The Gemfile's dependencies are satisfied

2.3.1 in app/ on master
› echo $?
0

2.3.1 in app/ on master
› git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

    modified:   Gemfile.lock

no changes added to commit (use "git add" and/or "git commit -a")

2.3.1 in app/ on master
› git diff
diff --git a/app/Gemfile.lock b/app/Gemfile.lock
index 2c19229..4c78cf2 100644
--- a/app/Gemfile.lock
+++ b/app/Gemfile.lock
@@ -1,7 +1,7 @@
 PATH
   remote: ../gems/core
   specs:
-    core (0.1.0)
+    core (0.1.1)

 GEM
   remote: https://rubygems.org/

2.3.1 in app/ on master
›
```

I expected `bundle check` to exit with an error code, with terminology that the bundle could not be satisfied, and not write to the Gemfile.lock silently.
