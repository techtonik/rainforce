
## User stories ##
### Corrections for Python site documentation ###
I would like to fix a mistake in one of Python documentation pages at http://docs.python.org but there is a

**Problem:** _Python documentation is a bunch of static pages that doesn't allow edits_

**Development:**
  1. To fix a page mistake I need to
    1. Find [Python documentation sources](http://www.google.com/search?q=python+documentation+sources)
    1. Find a repository and checkout the source
    1. Find a source file for corresponding page
    1. Patch source file
    1. Regenerate documentation
    1. Review generated page in browser
    1. Create a patch
    1. Find bug tracker for documentation enhancements requests
    1. Login to tracker
    1. Create ticket
    1. Attach a patch
  1. Source for documentation page is already available from page menu
  1. Source is in restructured text format that is easy to edit
  1. Although an edit form can be added to source view, the edits should be saved to repository
  1. Repository access requires commit privileges
  1. Commit privileges are granted to limited set of authenticated users
  1. Edits can be represented as patches
  1. The most popular format for patches is unified diff
  1. People without commit privileges would like to receive feedback and credits
  1. Users without commit right should be authenticated to get them in the future (see also CentralizedLogin)

**Use case:**
  1. I notice a typo on some/doc.page
  1. I login using the link from page menu titled "Login to edit this page" near "Show source" link
  1. After login I see "Edit this page" link that opens reST editor
  1. I edit a page, using preview button to watch the results
  1. When finished I add one line description of my comment and click submit
  1. System displays message "Thanks for you contribution. Your patch is placed into Moderation Queue. If you setup a email address in your profile, you will be notified when it's integrated."
  1. System generates a patch and places it into review queue with status "New"
  1. User with commit privileges looks at review queue, loads my patch, reviews it
  1. If patch requires discussion, a link to create an issue and add patch to tracker is provided automatically, the status is changed to "chatting", author is automatically subscribed to an issue
  1. If patch is ok, moderator pushes "Commit" button
    1. Current version of page is patched in local checkout
    1. Diff is compared to original patch
    1. Document is committed to repository with appropriate [credits](http://subversion.apache.org/docs/community-guide/conventions.html#crediting), patch description and "reviewed by" signature.

### Screenshots for Ubuntu installable applications ###
Needed to transmit music from my notebook to an audio system connected to desktop station. Know that MPD (Music Player Daemon) can do this. Ubuntu menu "Applications->Add/Remove..." didn't provide this choice, so I've discovered "System->Administration->Synaptic Package Manager" which shows libraries and application and in addition can display screenshots for applications, but there is a

**Problem:** _There are almost no screenshots in Synaptic descriptions_

**Development:**
  1. First reason is that developers are too busy to upload screens
  1. The second reason is that others don't have access
  1. Even if there is access there is no easy way to contribute screen for a given package
  1. Even if others are given convenient access to upload images, they should be moderated to allow only screens uploads

**Use case:**
  1. I see there is no screen for my favorite package
  1. I select "contribute screen" from context menu
  1. New dialog (or web page) is opened with a form to upload an image
  1. Form shows stats about current queue state (screens uploaded, waiting for moderation)
  1. Form asks for required and optional fields for this specific Moderation Queue which in case of package screenshot include package name, package version, optional contact info/login
  1. Image placed in moderation queue and an optional email is sent with a link to it
  1. Developer opens web-interface that queries Moderation Queue and provides "approve", "decline" actions along with item content and information
  1. Upon "approve" or "decline" command from web-interface Moderation Queue executes associated actions
  1. Approved screen is uploaded to SVN/Mercurial/Whatever repository under Developer's credentials, but with User's contribution in comments

## See also ##
code.google.com support [issue #3603](http://code.google.com/p/support/issues/detail?id=3603): wiki patch queues