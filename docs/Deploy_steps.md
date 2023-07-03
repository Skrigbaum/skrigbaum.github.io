---
layout: default
title: Deploy Steps
nav_order: 2
---

# How To Release/Timeline:

## First time Deploying?

-   Make sure you can ssh into production (you’ll need to git push to prod)
    
-   Make sure you have access to qa/production databases for any post-release tasks
    
-   Ensure that you have the github cli tools installed: [https://github.com/cli/cli#installation](https://github.com/cli/cli#installation)
    
-   Ask for help if anything is tricky or even if you just want someone there for moral support!
    


## Deploy to QA Env.

### Engineering Coordination
    

-   Create a copy of the deploy notes doc. found within the Engineering Google Drive. Update with current date. *Link Removed for privacy* 
    
-   Start a release thread in slack engineering channel including the new document and @ all teams and determine status of stories
    
-   Determine which repos need to be deployed with the teams, and record them in “Deploy Order Of Operations” section.

-   Are there any other tasks that need to be done BEFORE the release? Record them in the “Pre-release Tasks” section
    -   Ex: Manual data changes

-   Are there any other tasks that need to be done AFTER the release? Record them in the “Post-release Tasks” section    

### Deploying
    

-   Once everything is ready for qa, make PR’s for each repo from dev to qa. There is a script under *REDACTED* that makes this easy
    

-   PRE-REQS
    
	-   ensure that you have the github cli tools installed: [https://github.com/cli/cli#installation](https://github.com/cli/cli#installation) you’ll have to generate an api key and whatnot…

    

-   Run the *REDACTED* script under the *REDACTED* to create the PR's

-   Post to the engineering channel with links to the PR's
    
-   Once PR’s are approved Execute any pre-release task in qa and merge
    
-   CI will automatically deploy to qa
    
-   Execute any post-release tasks in qa
    

 ### Regression Testing
    

-   QA will post regression test links and bug report spreadsheet
        
-   Any fixes will be merged directly into qa
    

## Deploy to Prod

### Engineering Coordination
        
-   Keep channel updated about any pending bug regression fixes and timeline for deploy
    

 ### Merge to Prod
    

-   Use the deploy script to make prs to prod 

-   Get them approved
    
-   Wait to merge until you are ready to deploy
    

-   **DO NOT MERGE *REDACTED* until you are ready to deploy it!** It currently deploys automatically on merge.
    

 ### Manual Deployment

-   Notify the company channel about deployment starting. Use @here in the Sales channel so that sales and biz is aware.
    
-   Merge the PRs into prod for the repos being deployed
    
-   Run any pre-deploy tasks in Prod
    
For each repo, in order of the deploy notes

1.  Navigate to the repo’s “Actions” page
    
2.  Open the “Deploy to Remote” workflow on the left-hand list
    
3.  Click the “Run workflow” drop-down and within it change the branch to prod, then click the “Run workflow” button
    

4.  A new “Deploy to Remote” run should start (might take a couple of seconds)
    
5.   Watch the output of that workflow for anything funky or any failures. You should just see the app building, running migrations, etc.
    
### Post Deploy
-  Run any post deploy tasks in Prod
    
-   Let the company channel know deploy was successful
    

### Perform Backmerge
    
-   The prod merge should automatically create new PRs for each repo to merge prod back into dev
    
-   Get those approved and merge
    

### Create Release Notes
    

-   Follow the instructions here *REDACTED*
    
-   Paste a link to the new Release Notes doc in the company channel thread about the release
    

-   Congrats! You’re done 🎉
    

## Failure Procedures

-   If the deploy fails for any reason, communicate this promptly to the engineering channel. Include any error messages and status of various repo’s
    

-   Elicit help from appropriate team members to resolve the issue
    
-   Start a Zoom meeting to facilitate discussion and resolution of the issue
    
-   Work with QA to determine status of customer instances in the case of partial migration or other issues that might leave instances in an error state.
    

-   Once the issue is resolved, consider scheduling a post mortem to discuss the issue and come up with any ways to avoid it in the future.

---

  

# Known Issues

-   Sometime CI deploys will fail with `Command failed with exit code 1: *REDACTED**` Just re-run the action till it works... Investigation is ongoing.
  
**