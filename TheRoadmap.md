## Bootstrap ##

The goal of bootstrap activity is to create the easiest way to run open-source project from source to start fixing bugs and experimenting as soon as possible. In other words the goal is to create accessible _entrypoints_.

  * (Planning) [bugs.python.org ](http://wiki.python.org/moin/TrackerDevelopment) using [dev-in-a-box](https://bitbucket.org/techtonik/devinabox/) port
    * [ ] Split b.p.o modifications into separate patches

  * ([Frozen](https://bitbucket.org/techtonik/trac-bootstrap-script/src)) Trac
    * Hard dependency on setuptools ([can't be helped](http://trac.edgewall.org/ticket/10419))


---


  * (Done) [Spyder IDE](http://code.google.com/p/spyderlib)
```
# creates project in spyder/ directory, needs mercurial, needs python
hg clone https://code.google.com/p/spyderlib/ spyder
cd spyder
python bootstrap.py
```
  * (Done) [Roundup issue tracker](http://roundup-tracker.org/)
```
hg clone http://hg.code.sf.net/p/roundup/code roundup
cd roundup
python demo.py
# or
#python roundup/scripts/roundup_admin.py
```
  * (Done) [SCons](http://www.scons.org/)
```
hg clone https://bitbucket.org/scons/scons
python scons/src/script/scons.py
# note: if SCons is installed as a Python package, this
#       way will probably launch installed version
```

## Workflow ##

Optimize project development workflow. Remove barriers for contributors to participate in the project by taking routine stuff out of the process. Try to save people time making contributions as effective as possible and keeping collaboration fun.

  * GoogleCodeChecklist - lists some points for tuning project hosting

## Spread Good Usability Practices ##

Keyboard shortcuts:
  * mouseless.js - add shortcuts that work regardless of keyboard layout (adopt MIT-licensed https://github.com/madrobby/keymaster by Thomas Fuchs). See [Rietveld example](http://codereview.appspot.com).