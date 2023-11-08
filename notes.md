Nexaro
======

### slack channels

* `#robot-gitlab-builds` / https://app.slack.com/client/T01MXHTCNCS/C04LTKCRCRH: to find new releases
* `robot-vr7-frost-common-codebase`
* `team-galaxy-nexaro-help`

Robwerk
=======

In robwerk repo
---------------

Start from clean state:

```
cd robwerk
git submodule update --init --recursive
git checkout main
git pull
git submodule update
git status
```

At this point I should be in a clean state. Now create Tron branch:

```
git checkout -b PRVR-14164-ota-auto-resume
cd tron
git checkout PRVR-14164-ota-auto-resume
cd ..
git status
```

Make sure only tron dir changed, then do:

```
git add tron
git ci -am "PRVR-14164-ota-auto-resume"
git push
```

Open a MR on the robwerk repo. When pipeline has finished:

* get approval for tron MR
* merge it to `main`
* go back to terminal, robwerk repo, and do:

```
cd tron
git checkout main
git pull
cd ..
git add tron
git ci -am "update reference to main tron"
git push
```

Now go to robwerk GitLab MR and press "merge when pipeline finished".
