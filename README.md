pyNotificationCenter
====================

Python helper methods for Mountain Lion's notification center

Usage:

Just copy the pyNotificationCenter.py file into your source tree and import it.
e.g.:

    import pyNotificationCenter
    # show a message instantly
    pyNotificationCenter.notify("Test message", "Subtitle", "Show instantly", sound=True)
    # show a message after 20 seconds
    pyNotificationCenter.notify("Another test", None, "Show after 20 seconds", 20)

Handling clicks
---------------

To handle clicks, you must provide a userInfo variable, which should containt a
dictionary to help you determine the notification's contents. Then, in your
app delegate, implement the
`(void)applicationDidFinishLaunching:(NSNotification *)aNotification`
method. From there, you can check the notification's userInfo and handle it.

e.g.

In your notification:

    pyNotificationCenter.notify("Test message", "Subtitle", "Show instantly", userInfo={"action":"open_url", "value":"http://www.ganglionsoftware.com"})

In your app delegate:

    def applicationDidFinishLaunching_(self, sender):
      ...
      # check if the application launch sender's userInfo
      userInfo = sender.userInfo()
      if userInfo["action"] == "open_url":
        // open url
      ...
      
