# Issues

 <a name="what-issue"></a>
## [What's an issue in Frisk?](#what-is-issue)
Think of an issue as a box filled with errors, but these errors are the same. When Frisk app receive a new error, it looks for an old open issue that has the same criteria as the new error and if it's the same then it's added to the old issue and if not then it creates a new issue.

 <a name="issue-basic-information"></a>
## [Issue basic information](#issue-basic-information)
Most basic information that's saved for an issue entity is the exception and message of the first error in its list, and affected users and sessions number. The detailed information is saved under each session (error) in an issue list.

 <a name="issue-statuses"></a>
## [Difference between issue statuses](#issue-statuses)
There are three statuses of an issue. _Open_ means it's new or not yet taken action for it. _Closed_ status means it's been looked at and probably a member marked it closed because it's fixed. _Suspended_ status means a member might found the issue repetitive and annoying so he suspended it for a while until an action is taken. If an issue is suspended then no errors will be logged to it during this time.

 <a name="issue-seen"></a>
## [Difference between last seen and first seen](#issue-seen)
First seen means the first time an error in this issue was saved, and last seen is the saving time of last error (session).

 <a name="issue-counts"></a>
## [Why sessions (errors) count are not equal to users count](#issue-counts)
Frisk only recognize (if not disabled) registered users to the client application, if guest account is affected then it's considered a session but not a user. Also some users might be affected twice or thrice and that's counted as multiple sessions by one user.
