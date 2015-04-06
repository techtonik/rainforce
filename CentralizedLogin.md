## Why? ##

It is very annoying to maintain multiple passwords for a single domain.

### login.python.org ###

This started with [issue #7](https://code.google.com/p/rainforce/issues/detail?id=#7) about numerous logins for various [python.org](http://python.org) sites, and the need to create login.python.org service. Quoting sites in this domain:

**sites that require user login**
  * wiki
    * main: http://wiki.python.org/moin/
    * jython: http://wiki.python.org/jython/
  * pypi: http://pypi.python.org
  * bug trackers
    * main: http://bugs.python.org
    * meta: http://psf.upfronthosting.co.za/roundup/meta/
    * setuptools: http://bugs.python.org/setuptools/
    * pypi: http://sourceforge.net/tracker/?group_id=66150&atid=513503
  * mailing list subscription management
  * mailman private archives
    * http://mail.python.org/mailman/private/pydotorg/
    * http://mail.python.org/mailman/private/soc2010-mentors/
  * buildbot: http://buildbot.python.org/all/waterfall

**web pages** (that would be nice to see [editable from web](ModerationQueue#Corrections_for_Python_site_documentation.md))
  * http://python.org
  * http://docs.python.org

In addition many python.org sites don't have valid **SSL/TLS certificate** for secure authentication that protects users against man-in-the-middle attacks.

### PySide ###

It is also very annoying to have multiple logins for PySide (Qt) development sites:

  * wiki: http://qt-project.org/wiki/
  * bug tracker: https://bugreports.qt-project.org/
  * code reviews: https://codereview.qt-project.org/

### SCons ###

SCons has a wiki at http://scons.org/wiki which requires login/password, while it is possible to alternatively require only email.


### Blender ###
  * http://wiki.blender.org/ - keyboardless login wanted
  * https://projects.blender.org/ -


## How? ##

Site logins are all about cookies. When a web site logs you in, it sets [a cookie](http://simple.wikipedia.org/wiki/HTTP_cookie) which is then sent by browser again and again each time you travel from one page to another. Browser doesn't maintain your session automatically - the web site needs to set cookie explicitly even for the session that lasts only while your browser is open.

Cookies are domain specific. You can not command browser to set cookie for example.com web site from the other domain.

So, to login user to some web app, you need three things:
  * be on the same root domain (you can set cookie for web.example.com from example.com)
  * know the cookie format
  * make sure the user exists in web app

## Assorted Notes (for confusion) ##

Probably something like OAuth works. Several implementation levels - basic, intermediate, advanced, ...

Server map:
```
[Login Server] --- [Other Site]
               --- [Another Site]
                   ...
```

`[Login Server]`
  * login and registration
  * user id (email)
  * transforming user info in the way `[Other Site]` requires
  * send user data to `[Other Site]`
    * choose communication way with `[Other Site]`

Inspiration links:
  * https://openhatch.org/wiki/Authentication_integration
