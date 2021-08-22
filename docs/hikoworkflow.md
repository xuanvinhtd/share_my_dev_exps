# WorkFlow HIKO Mobile Team

This workflow is a rule, convention that make you and your teamwork smooth, easy, quickly in process app development.

 ## Git workflow

1. We have 4 main branch

- `master/main`: This branch stores all the official codes of the project
- `develop`: This branch stores all code that your team developing to UPDATE FEATURES for the project
- `feature/...`: You will create this branch from the `master/main` branch or the `develop` branch to implement new feature for the project
- `bugfix/...`: You will create this branch from the `master/main` branch or the `develop` branch to fix some bug for the project

2. Team convention when creating a new branch

We use Jira for managing projects. [What is Jira Software?](https://www.atlassian.com/software/jira)
And in Jira, we have the ticket or the card to tracking the task for the project.
The ticket have ticket code(Ex: `AM18-621`), title, link and so on.

- `Developer` create a new feature branch with the format:

```
feature/[ticket code]
Ex: feature/AM18-621
```

In case, have not ticket:

```
feature/[to do someting]
Ex: feature/add_home_page
```

- `Developer` create a new branch to fix bug with the format:

```
bugfix/[ticket code]
Ex: bugfix/AM18-621
```

In case, have not ticket:

```
bugfix/[fix someting]
Ex: bugfix/home_logo
```

After finish task, `Developer` creating a Pull Request(PR) to `other members` review your code and merge it to the `master/main` branch.

3. Team convention when creating a Pull Request(PR)

- Title and contents with format:

```
Title: 
[Ticket code] #[Ticket title]
Content:
Issue related:
- Link jira ticket
```

Ex:

```
Title: 
AM18-621 #Add home screen
Content:
Issue related:
- https://demo.atlassian.net/browse/AM99-621

```

- And assign `other members` review your code
- Finally, get link PR, post in Mobile Team room, and tag members to review it.

!> Note: `One` PR only `One` commit, this mean you must to merge all your commit to one commit by `rebase` and `squash` in your branch.

## Work with Jira

1. Dev Board consist of columns:
- Open: Task/ Bug - created but not process (QC or Team Leader create it)
- Reopen: Task/ Bug - implemented by DEV and QC tested/verified but not it yet done (QC drag and drop it)
- In Progress: Task/ Bug - DEV in process (DEV drag and drop it) 
- In Review: Task/ Bug - DEV has processed & send Merge Request (DEV drag and drop it)
- Already In Build: Task/ Bug - DEV has processed and Team Leader already build for QC(Team Leader drag and drop it)
- Pending: Task/ Bug - relate to API or need check again on Production
- Integration test: Task/ Bug - QC testing/ verifing (QC drag and drop it)
- DONE: Task/ Bug - QC have tested & confirmed (QC drag and drop it) 

2. Log Work

!> Developer, you must `log Work` in Jira.

- [Guide to Log Work](https://docs.google.com/document/d/1n0CPdC-TNNYIr2vjcnwvrdK4Yhfa-gvPptl_CLZjkWQ/edit)

## Daily Report

`Developer` must daily report in project group to everyone tracking the progress of the project.

Format Report:

```
[Mobile][Daily Report] dd/mm/yy
Yesterday Actual: 
+ Task title that have did it on yesterday - Link Jira - % progress
+ .....
Today goals:
+ Task title that will to to on today - Link Jira - % expect progress
+ ........
```

## Use VPN

!> When developing, you must `turn on` VPN. Please contact with Mobile Team leader to get an account.

## Other issue

- Would like to contribute something for this company, this guide...
- Need to support..
- Need more tasks..
- Need to share or learn something...
- Or so on.

?> Please contact with Mobile Team Leader

