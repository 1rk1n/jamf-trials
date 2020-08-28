# jamf-trials
# https://www.jamf.com/jamf-nation/discussions/35181/how-to-add-application-in-screen-recording-in-macos-catalina

#!/bin/sh

# Get currently logged in user and their home directory
loggedInUser=`/bin/ls -l /dev/console | /usr/bin/awk '{ print $3 }'`
loggedInUserHome=`dscl . -read /Users/$loggedInUser | grep NFSHomeDirectory: | cut -c 19- | head -n 1`

# Fix Permissions
chown -f -R $loggedInUser:staff $loggedInUserHome
