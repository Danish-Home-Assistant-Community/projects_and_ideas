**Smashrun**

This sensors show running data from Smashrun. Smashrun have autosync from many other sites including Garmin Connect.

**Screenshot(s):**

![Screenshot 3](https://github.com/Danish-Home-Assistant-Community/projects_and_ideas/blob/master/Smashrun/screenshot_2.jpg)

![Screenshot 2](https://github.com/Danish-Home-Assistant-Community/projects_and_ideas/blob/master/Smashrun/screenshot_1.jpg)

![Screenshot 1](https://github.com/Danish-Home-Assistant-Community/projects_and_ideas/blob/master/Smashrun/screenshot.jpg)

**Configuration:**

1: If you not already have a Smashrun account visit https://smashrun.com/allan.persson/invite and make your account, and setup auto sync to the fitness trackers you want to sync with.

2: Go to https://api.smashrun.com/v1/explorer and write *client* in top left corner and press Smashrun Link and authorize.

2a: Full api documentation can be found here: https://api.smashrun.com/documentation

3: When authorized (in top left corner you will now see a token) go to the api you want to use and click execute, the one used for last run distance is *Get all activities in summary format (ordered by StartDate)*

The full url including token is copied to the clipboard and you can now insert it in ressources in the sensor, if not copied go back to **3:** and repeat the steps.
