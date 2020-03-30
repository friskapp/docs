# Project Notifications


 <a name="supported-webhooks"></a>
## [Supported Webhooks](#supported-webhooks)
In Frisk, users can customize email notifications for each project. Each project have its own notification channels and can be configured separately. Frisk supports Slack, Discord, and generic channels. 
![project-notifications-1](/images/docs/project-notifications-1.png)

 <a name="types-of-notifications"></a>
## [Types of notifications](#types-of-notifications)
Frisk will notify webhook/email for two things: 
- Status change: when an issue status change to something else.
- New Session: when an issue gets a new occurrence of an error or first session.

![project-notifications-2](/images/docs/project-notifications-2.png)

 <a name="generic-webhook"></a>
## [What is generic webhook](#generic-webhook)
You can use Generic webhook with services that support raw data manipulation, or with services that forward any webhook to other services (like: zapier or ifttt).

Here's the explained raw JSON data we send to a generic webhook so you can understand how to parse it:

    {
        "url": link to the issue on Frisk app,
        "file": file of where the error occurred,
        "message": error message,
        "class": class of where the error occurred,
        "line": error line number,
        "snippet": code snippet of where the error occurred,
        "project": project title,
        "stage": environment stage during error occurrence,
        "exception": error exception,
        "versions": framework version, then comma then language version,
        "sessionsCount": number of error occurrences,
        "usersCount": number of affected users,
        "solution": solution to the error if there is any or null,
        "closedAction": link to change status to closed,
        "suspended6hAction": link to change status to suspended for 6 hours,
        "suspended1wAction": link to change status to suspended for 1 week
    ];