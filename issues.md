# Issues

 <a name="what-issue"></a>
## [What's issue in Frisk?](#what-is-issue)
Think of an issue as a box filled with errors, but those errors are the same. When Frisk app receive a new error, it looks for an old open issue that has the same criteria as the new error and if it's the same then it added to the old issue and if not then it create a new issue.

 <a name="issue-basic-information"></a>
## [Issue basic information](#issue-basic-information)
Most basic information that saved for an issue entity is the exception and message of the first error in its list, and affected users and sessions number. The detailed information is saved under each session (error) in an issue list.

 <a name="issue-statuses"></a>
## [Difference between issue statuses](#issue-statuses)
There are three types of issue's status. Open means it's new or not yet taken action for it. Closed status means it's been looked at and probably a member marked it closed because it's fixed. Suspended status means a member might found the issue repetitive and annoying so he suspended it for a while until an action is taken. If an issue is suspended then no errors will be logged to it during this time.

 <a name="issue-seen"></a>
## [Difference between last seen and first seen](#issue-seen)
An issue has two time fields. First seen means the first time an error in this issue was saved, and last seen is the saving time of last error (session).

 <a name="issue-counts"></a>
## [Why sessions (errors) count are not equal to users count](#issue-counts)
Frisk only recognize (if not disabled) registered users to the client application, if guest account is affected then it's considered a session but not a user. Also some users might be affected twice or thrice and that counted as sessions by one user.
