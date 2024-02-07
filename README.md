# SALT Publishing Guide

> How-to guide for publishing from CCHMC onto the Situational Awareness Learning Tool (SALT) Posit Connect sever

## Login to Posit Connect

1. Go to [dev.salt.cchmc.org](https://dev.salt.cchmc.org)

1. On the landing page, scroll down and click on the link to register with SALT  
  a. This will link to a brief REDCap survey where you can enter your basic information and agree to the SALT use terms  
  b. A SALT admin will create a user account with your CCHMC email that you can use for access
  
1.  Once you have been confirmed to have access, back at the SALT landing page, in the top-right corner, click on the "login" button.  
  a.  This should send you to a familiar-looking CCHMC login page; enter your credentials as normal  
  
1.  This should bring you to the SALT Posit Connect dasbhoard: ![content landing page](figs/content_landing_page.png)

## Git-backed Deployment

For SALT, content is deployed using the git version control system and GitHub, which allows for continuous integration and testing of data content. To publish to SALT using a git repository on GitHub:
    
i. In your project, create a "dev" branch to deploy from

ii. Deploy the "dev" branch to Posit Connect as private

iii. Once you're happy with the deployment, create a pull request of your "dev" branch and request a review from a SALT admin; merge into "main"

iv. Deploy your "main" branch publicly; delete "dev" deployment

v. Iteratively merge in future "dev" branches to update your "main" deployment


### On GitHub
1. Fork your project repository into the [CCHMC-SALT](https://github.com/orgs/CCHMC-SALT/repositories) organization
    a. If your project is not on GitHub, add it to the CCHMC-SALT organization. For more information on GitHub generally, read [here](https://docs.github.com/en/get-started/quickstart/hello-world) and for a great tutorial on using GitHub with R and RStudio, check out this [book](https://happygitwithr.com/)
2. Create a branch called "dev"

### In your RStudio project

Use [`rsconnect::writeManifest()`](https://rstudio.github.io/rsconnect/) in R to add or update a [`manifest.json` file](https://rstudio.github.io/rsconnect/reference/writeManifest.html). Commit this file and push to GitHub.
    
### On the SALT Posit Connect Server
1. On the "Content" tab of Posit Connect, click the blue "Publish" button and select "Import from Git" from the dropdown menu
2. In the text box, paste the URL of your Git repository (on GitHub, select "Code" -> copy for the correct URL)
3. Select your branch
    a. If this is your first time publishing this project, select your "dev" branch
    b. If you have gone trough the approval process, select your "main" branch; For more information on this, see the section below entitled "Production Deployment"
4. Select your root folder. This will be the folder where your `manifest.json` was written and stored
6. Title your content. For clarity, if this is a "dev" branch, please title your content as "[dev]_{your_title}"
6. Select "Deploy Content"

### Production Deployment
1. After you have successfully deployed your "dev" branch and are happy with how it presents online, return to your project's GitHub repository and create a pull request for your "dev" branch
2. Request a review from a SALT admin, either Andrew Vancil (andrew-vancil) or Cole Brokamp (cole-brokamp)
    a. Once approved, the admin will merge your branch into main
3. Return to the SALT Posit Connect interface and follow the steps listed above, but this time select the "main" branch when prompted
4. Delete your "[dev]_{your_title}" deployment


### Publishing Options
- Access
    - There are three available options for visibility: 
        i. Publicly available to anyone with the URL
        ii. Require a CCHMC login
        iii. Limit to specific users/email addresses
    - Adjust these settings by first, while your content is pulled up, selecting the gear icon, then the open padlock icon called "Access".
- Web address
    - While the URL will always begin with "https://dev.salt.cchmc.org", you have the ability to create a custom suffix. Under the "Access" tab in settings, enter the suffix you would like in the Path text box. For example, if you type "my_app", your new URL will be "https://dev.salt.cchmc.org/my_app"
- Scheduling
    - If you are publishing a document like an Rmarkdown or Quarto, you have the option to schedule regular renderings of that document under the "Schedule" tab
- After adjusting any of these settings, be sure to hit the Save button near the top of the panel

### Tags
- For tracking purposes, a SALT admin will create a tag for your project/group. This will primarily be used for usage monitoring, but may be used to determine costs of hosting the object. Simply click the box relevant for your content

### Troubleshooting
- If you click on the symbol that looks like a little notebook, that will pull up the log of your content. In here, you will be able to see both the posit connect log and a log that looks like your typical R console. Here, you will find error messages, making this a great place to start if your app or document is not publishing correctly
- For more information on git-backed deployment, please see the documentation [here](https://docs.posit.co/connect/user/git-backed/).
- For additonal help, please reach out to Cole Brokamp at [cole.brokamp\@cchmc.org](mailto:cole.brokamp@cchmc.org){.email} or Andrew Vancil at [andrew.vancil\@cchmc.org](mailto:andrew.vancil@cchmc.org){.email}




