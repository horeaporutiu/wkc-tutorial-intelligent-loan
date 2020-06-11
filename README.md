# Implement data governance to manage and secure clients’ data

It's no secret that data breaches are one of the worst ways
to reach the headlines, and even one breach can mean an [average cost of 3.9 million USD](https://www.varonis.com/blog/data-breach-statistics/). With data 
becoming more and more of a competitive advantage, and the amount of data that is produced world-wide 
projected to double [from 2020 to 2023](https://www.statista.com/statistics/871513/worldwide-data-created/), 
the process of organizing, managing, and securing data is more 
important than ever. It's no surprise that the tools to take that data, organize it, govern it, and ensure quality and searchability are what is needed at 
this point. 


As companies are building up their journey to take advantage of their data 
through AI, many businesses already have the first step of collecting data completed. They
store data in a database, and they use that data to inform customers of their previous 
transactions, conversations, and other information related to a customer. The second step, or "organize" is
focused on creating the foundation of analytics. More specifically,
it's about enabling your data scientists and business analysts to do their job efficiently. 

This is 
where a secure metadata management platform like the [award-winning Watson Knowledge Catalog](https://www.ibmbigdatahub.com/blog/ibm-expands-data-and-ai-excellence-data-cataloging-technology-cloud-pak-data#:~:text=Watson%20Knowledge%20Catalog%20named%20a,winner%20for%20metadata%20management%20tools&text=Describing%20the%20breadth%20of%20IBM's,space%20is%20no%20small%20task.) on the Cloud Pak for Data platform comes in. At its core
Watson Knowledge Catalog (or WKC for short) connects data and knowledge with the people who need 
to use it. Some of the typical use cases for a tool like Watson Knowledge Catalog is 
ensuring regulatory compliance, data quality management, data delivery, and others, but for the
purpose of this tutorial, we will focus on privacy and protection - with the goal of 
minimizing the chance for a data breach.

After completing this hands-on tutorial you will learn how to solve the problems of enterprise data governance on the Cloud Pak for Data platform from the data steward or data admin persona. We'll explain how to use governance, data quality and active policy management in order to help your organization protect and govern sensitive data, trace data lineage and manage data lakes. This knowledge will help you quickly discover, curate, categorize and share data assets, data sets, and analytical models with other members of your organization. It serves as a single source of truth for data engineers, data stewards, data scientists and business analysts to gain self-service access to data they can trust.

![Cloud Pak for Data login](images/seq-diagram.png)

You will need the *Admin* role to create a catalog.

This section is comprised of the following steps:
1. [Set up Catalog and Data](#1-set-up-catalog-and-data)
1. [Add collaborators and control access](#2-add-collaborators-and-control-access)
1. [Add categories](#3-add-categories)
1. [Add data classes](#4-add-data-classes)
1. [Add Business terms](#5-add-business-terms)
1. [Add rules for policies](#6-add-rules-for-policies)

## 1. Set up Catalog and Data

> NOTE: The default catalog is your enterprise catalog. It is created automatically after you install the Watson Knowledge Catalog service and is the only catalog to which advanced data curation tools apply. The default catalog is governed so that data protection rules are enforced. The information assets view shows additional properties of the assets in the default catalog to aid curation. Any subsequent catalogs that you create can be governed or ungoverned, do not have an information assets view, and supply basic data curation tools.

First we'll create a catalog and load some data.

### Create the catalog

#### Provision Watson Knowledge Catalog the First Time

If you haven't yet started Watson Knowledge Catalog, you'll need to provision it.

* Open Watson Knowledge Catalog by clicking the *Services* icon at the top right of the home page:

![click services icon](images/wkc-admin/wkc-click-services-icon.png)

* Under the *Data Governance* section, click on the *Watson Knowledge Catalog* tile:

![open wkc](images/wkc-admin/wkc-open-service.png)

#### Open Watson Knowledge Catalog

* Click open on the top-right corner to launch Watson Knowledge Catalog.

![open wkc](images/wkc-admin/wkc-open-service-2.png)

* Go to the upper-left (☰) hamburger menu and choose `Organize` -> `All catalogs`:

![open catalog menu](images/wkc-admin/wkc-admin-open-catalog-menu.png)

* From the *Your catalogs* page, click either `Create catalog` or `New Catalog`:

![create WKC catalog](images/wkc-admin/wkc-create-catalog.png)

* Give your catalog a name and optional description, check  `Enforce data protection rules` and click `create`:

![name and create wkc catalog](images/wkc-admin/wkc-name-describe-create.png)

* Click `OK` on the pop-up that shows up when you checked the checkbox in the previous screen, then click `Create`.

![enforce data protection](images/wkc-admin/wkc-enforce-data-protection.png)

### Option 1 - Add data assets 

* Under the *Browse Assets* tab, below "Now you can add assets!" click `here` to add your data:

![click here to add assets](images/wkc-admin/wkc-add-data-asset.png)

*OR* you can click `Add to catalog +` in the top right and, for example, choose `Local files`:

![add local files to catalog](images/wkc-admin/wkc-add-to-catalog-local-files.png)

* Browse to where you cloned the repository and go to `/data/split/applicant_personal_data.csv`. Click on `Open`. Add an optional description and click `Add`:

![click add for local files to catalog](images/wkc-admin/wkc-file-selected-now-add.png)

>NOTE: Stay in the catalog until loading is complete! If you leave the catalog, the incomplete asset will be deleted.

* The newly added *applicant_personal_data.csv* file will show up under the *Browse Assets* tab of your catalog:

![newly added data in catalog](images/wkc-admin/wkc-browse-assets.png)

### Option 2 - Add Connection

* You can add a connection to a remote DB, for example *DB2 Warehouse in IBM Cloud*, by choosing `Add to catalog +` -> `Connection`:

![add connection to catalog](images/wkc-admin/wkc-add-connection.png)

* Choose your remote DB and click:

![chose db2 warehouse connection ](images/wkc-admin/wkc-choose-db2-warehouse-conn.png)

* Enter the connection details and click `Create`:

![enter db2 warehouse connection details](images/wkc-admin/wkc-enter-connection-details.png)

* The connection now shows up in the catalog:

![db2 warehouse connection shows up](images/wkc-admin/wkc-new-connection-shows-up.png)

### Options 3 - Add Virtualized Data

Virtualized data can be added to the *Default* catalog by someone with Administrator or Editor access to that catalog.

* Go to the upper-left (☰) hamburger menu and choose `Organize` -> `All catalogs`. Click `Add to Catalog +` -> `Connected asset`:

![add connected asset](images/wkc-admin/wkc-add-connected-asset.png)

* Click *Source* -> `Select source`. Browse under `DV` to you Schema (i.e. UserXYZW) and choose the joined table. Click `Select`.

![seelect source](images/wkc-admin/wkc-select-source.png)

A user can now add this to a project like any other asset from a catalog.

## 2. Add collaborators and control access

* Under the *Access Control* tab you can click `Add Collaborator` to give other users access to your catalog:

![give users access to the catalog](images/wkc-admin/wkc-access-control-add-collaborator.png)

* You can search for a user, click on the name to select them, choose a role for the user - Admin, Editor, or Viewer and click `Add`:

![search for user and add as collaborator](images/wkc-admin/wkc-choose-user-and-add.png)

* To access data in the catalog, click on the name of the data:

![click data name to open](images/wkc-admin/wkc-click-data-name-to-open.png)

* A preview of the data will open, with metadata and the first few rows:

![preview of data](images/wkc-admin/wkc-data-preview.png)

* You can click the `Review` tab and rate the data, as well as comment on it, to provide feedback for your teammates:

![review data](images/wkc-admin/wkc-review-data.png)

## 3. Add categories

The fundamental abstraction in Watson Knowledge Catalog is the Category. A category is analogous to a folder.


* Add a category for your assets by going to the upper-left (☰) hamburger menu, choose `Organize` -> `Data and AI Governance` -> `Categories`, 
![Add category](images/wkc-admin/wkc-add-categories.png)

You can import them in .csv format(option 1) , or you can add categories manually(option 2).

### Option 1 - Import categories

* Click `Import`:

![Import categories](images/wkc-admin/wkc-import-categories.png)

* Click `Add file` and navigate to where you cloned this repository, choosing `data/wkc/glossary-organize-categories.csv`.

![Import csv](images/wkc-admin/wkc-import-csv.png)

* Under `Select merge option` choose `Replace all values` and click `Import`:

![Import select merge option](images/wkc-admin/wkc-import-select-merge-option.png)

* You will see "The import completed successfully" when it is completed.

![Import complete](images/wkc-admin/wkc-import-complete.png)

In this way, you can import Categories, Business Terms, Classifications, Policies, etc. to populate your governance catalogs.

### Option 2 - Add category manually

*  then click `Create category`:

![organize data categories](images/wkc-admin/wkc-menu-organize-categories.png)

* Give your category a name, such as *Personal Data*, and an optional description, and then click `Save`:

### Need to change pic below

![new category billing](images/wkc-admin/wkc-new-category-billing.png)

* Now, if you hit `Create category` again on the *Billing* category screen, you can create a sub-category, such as *Total Charges*:
### Need to change pic below

![sub category total charges](images/wkc-admin/wkc-new-sub-category-totalcharges.png)

* For the *Billing* category you can select a *Type*, such as `Business term`:
### Need to change pic below

![select business term type](images/wkc-admin/wkc-category-select-type.png)

* We can also create classifications for assets, similar to *Confidential*, *Personally Identifiable Information*, or *Sensitive Personal Information* in a similar way, by going to the upper-left (☰) hamburger menu, choose `Organize` -> `Data and AI Governance` -> `Classifications`. 

![select classification type](images/wkc-admin/wkc-add-classifications.png)

* Click `New classification` dropdown and select `Create new classification`. These classifications can then be added to your category as a *Type*: 

![select classification type](images/wkc-admin/wkc-add-classifications-2.png)

## 4. Add data classes

When you profile your assets, a data class will be inferred from the contents where possible. We'll see more on this later. You can also add your own data classes.

* Add a data class for your assets by going to the upper-left (☰) hamburger menu, choose `Organize` -> `Data and AI Governance` -> `Data classes`, then click `New data class` -> `Create new data class`:

![organize data classes](images/wkc-admin/wkc-menu-organize-data-classes.png)

* Give your new data class a name, i.e. *alphanumeric*, and an optional Primary category and/or description, and click `Save as draft`:

![new data class](images/wkc-admin/wkc-create-data-class.png)

* Once the data class is created, we can add *Stewards* for this class, and also associate *classifications* and *business terms*. When you are ready, click `Publish`:

![tools for data class](images/wkc-admin/wkc-data-class-add-term-publish.png)

![publish comment data class](images/wkc-admin/wkc-data-publish-comment.png)

Now let's add that data class to a column in our *applicant_personal_data.csv* asset.

* Go back to your CreditDataCatalog catalog and open it up to the column view ((☰) hamburger menu `Organize` -> `All catalogs` and choose `CreditDataCatalog`). Under the *Browse assets* tab, click on the data set *applicant_personal_data.csv* to get the column/row preview. Scroll right to get to the *CustomerID* column and click the down arrow next to "Customer Number" and then *View all*:
### Need to change pic below

![change data class](images/wkc-admin/wkc-admin-existing-data-class.png)

* In the window that opens, search for your newly created data class, *alphanumeric* and click it when it returns in the search. Then click *Select*:
### Need to change pic below

![Set column to numerical data class](images/wkc-admin/wkc-admin-alphanumeric-data-class.png)

## 5. Add Business terms

You can use [Business terms](https://dataplatform.cloud.ibm.com/docs/content/wsj/governance/dmg16.html) to standardize definitions of business concepts so that your data is described in a uniform and easily understood way across your enterprise.

You already saw how to create a category and make it a *business term*. You can also create the business term as it's own entity.

* From the upper-left (☰) hamburger menu, choose `Organize` -> `Data and AI Governance` -> `Business terms`:

![organize Data Business terms](images/wkc-admin/wkc-organize-data-business-terms.png)

* Click on the upper-right `New business term` drop down and choose `Create new business term` button:

![create business term](images/wkc-admin/wkc-create-business-term.png)

* Give the new Business term a name such as *Billing* and optional description, and click `Save as draft`. NOTE that if others on the platform will be creating a business term as well, pre-pend your term with something unique, i.e *Samaya-Billing*:

![name new business term](images/wkc-admin/wkc-name-new-business-term.png)

* A window will come up once the term is created. You can see a rich set of options for creating related terms and adding other metadata. For now, click `Publish` to make this term available to users of the platform:

![publish business term](images/wkc-admin/wkc-publish-business-term.png)

* Add an optional comment and click `Publish` in the new window:

![verify publish business term](images/wkc-admin/wkc-click-publish.png)

* Now go back to your `CreditDataCatalog` catalog and open it up to the column view ((☰) hamburger menu `Organize` -> `All catalogs` and choose `CreditDataCatalog`). Under the *Browse assets* tab, click on the data set *applicant_personal_data.csv* to get the column/row preview. Scroll right to get to the *TotalCharges* column and click the *Column information* icon (looks like an "eye"):
### Need to change pic below

![choose TotalCharges column information](images/wkc-admin/wkc-totalcharges-column-information.png)

* In the window that opens, click the *edit* icon (looks like a "pencil") next to *Business terms* :

![edit business terms](images/wkc-admin/wkc-assign-terms-to-column.png)

* Enter *Billing* (or your uniquely named term such as *Samaya-Billing*) under *Business terms* and the term will be searched for. Click on the `Billing` term that is found, and click `Apply`:

![edit business terms](images/wkc-admin/wkc-search-billing-to-assign-term.png)

Close that window once the term has been applied.
Now, do the same thing to add the *Billing* Business term to the *MonthlyCharges* column.

* You will now be able to search for these terms from within the platform. For example, going back to your top level *CreditDataCatalog*, in the search bar with the comment "What assets are you searching for?" enter your unique *Samaya-Billing* term:

### Need to change pic below

![search using business terms](images/wkc-admin/wkc-search-business-terms.png)

The *applicant_personal_data.csv* data set will show up, since it contains columns tagged with the *Billing* business term.

## 6. Add rules for policies

We can now create rules to control how a user can access data.

* Create a business term called *CustomerID* and assign it to your *CustomerID* column in the data set using the instructions above. See below if you need details, but try it yourself first, and skip to *Adding a rule* below if you do not need a reminder.

### How to create a Business term review

* From the upper-left (☰) hamburger menu, choose `Organize` -> `Data and AI Governance` -> `Business terms`.

* Click on the upper-right `+ Create Business term` button.

* Give the new Business term the name *CustomerID* and optional description, and click `Save as draft`. In the next window, click `Publish`.

* Now go back to your CreditDataCatalog catalog and open it up to the column view ((☰) hamburger menu `Organize` -> `All catalogs` and choose `CreditDataCatalog`). Under the *Browse assets* tab, click on the data set *applicant_personal_data.csv* to get the column/row preview. Scroll right to get to the *CustomerID* column and click the *Column information* icon (looks like an "eye"):

* In the window that opens, click the *edit* icon (looks like a "pencil") next to *Business terms* :

* Enter *CustomerID* under *Business terms* and the term will be searched for. Click on the `CustumerID` term that is found, and click `Apply`.

### Adding a rule

* From the upper-left (☰) hamburger menu, choose `Organize` -> `Data and AI Governance` -> `Rules`, 

![select rule](images/wkc-admin/wkc-rules-menu.png)

* then click `New rule` -> `Create new rule`.

![create rule](images/wkc-admin/wkc-create-rule.png)

* For the *New rule* -> *Select the type of rule to create* choose `Data protection rule`.

![data protection](images/wkc-admin/wkc-data-protection.png)

* Under *Details* give your rule a *Name*, *Type* = *Access*, and a *Business definition*.

* Next, under *Rule builder* *Condition1* fill out If *Business term* *Contains any* *CustomerID*  and Action then *mask data* *in columns containing* *alphanumeric*. Choose the tile for `Substitute`, which will make a non-identifiable hash. This obscures the actual CustomerID, but allows actions like database joins to still work. Click `Create`:

![define rule for masking customerID](images/wkc-admin/wkc-rule-substitute-customer-id.png)

* Now if we go back to our *applicant_personal_data.csv* asset in the catalog at the *CustomerID* column, it will look the same as before. But a non-admin user will see the "lock" icon and see that the customerID has now been substituted with a hash value:
### Need to change pic below

![customerID is now masked](images/wkc-admin/wkc-masked-column-customer-id.png)

<!-- * To add a rule to *Obfuscate* data, go to the `Profile` tab and scroll to the *TotalCharges* column. You can see that the data has been inferred to be classified as a *Quantity*: -->

* Back in the CreditDataCatalog, under the applicant_personal_data.csv asset, go to the Overview tab and scroll to the Age column. Click the "down arrow" and you can see that the data has been inferred to be classified as a Code
### Need to change pic below

![TotalCharges classified as Quantity](images/wkc-admin/wkc-inferred-classifier-totalcharges.png)

Here is where you could change the classification if the inferred one was not what you wanted.


* You can build a rule to Obfuscate the `Age` column:
### Need to change pic below

![TotalCharges obfuscate rule ](images/wkc-admin/wkc-build-obfuscate-rule.png)

* And now that column will have data that is replaced with similarly formatted data:
### Need to change pic below

![TotalCharges column obfuscated](images/wkc-admin/wkc-obfuscated-totalchurn-column.png)

This ends the Watson Knowledge Catalog for Admins lab.



<!-- ## 1. Pre work

First clone this repository. This will give you access to the data that we need. The 
data we use can be found [here](https://github.ibm.com/ibm-developer-eti-ai-analytics/Intelligent-Bank-Modernizing-your-Bank-Loan-Department/blob/phase2-studio-ml-notebook/data/german_credit_data.csv). 

At this point of the workshop we will be using Cloud Pak for Data for the remaining steps.

### Log into Cloud Pak for Data

Launch a browser and navigate to your Cloud Pak for Data deployment

> **NOTE:** Your instructor will provide a URL and credentials to log into Cloud Pak for Data!

![Cloud Pak for Data login](images/manage/cpd-login.png)

### Create a New project

In Cloud Pak for Data, we use the concept of a project to collect / organize the resources used to achieve a particular goal (resources to build a solution to a problem). Your project resources can include data, collaborators, and analytic assets like notebooks and models, etc.

* Go the (☰) menu and click *Projects*

![(☰) Menu -> Projects](images/manage/cpd-projects-menu.png)

* Click on *New project +*

![Start a new project](images/manage/cpd-new-project.png)

* Select *Analytics project* for the project type and click on *Next*

![Select project type](images/manage/cpd-project-type.png)

* We are going to create a project from an existing file (which contains assets we will use throughout this workshop), as opposed to creating an empty project. Select the _*Create a project from a file*_ option:

![Create project from file](images/openscale-config/openscale-config-create-project-from-sample.png)

* Navigate to where you cloned this repository, then to `projects/` and choose `CreditRiskProject.zip`. Give the project a name and click `Create`:

<!-- ![Browse for project files](images/manage/cpd-importproject.png) -->

<!-- * After successful creation, click on *View new project* -->

<!-- ![Import project success](images/manage/cpd-importprojectsuccess.png) -->
<!-- 
### Create a Deployment Space

Cloud Pak for Data uses the concept of `Deployment Spaces` to configure and manage the deployment of a set of related deployable assets. These assets can be data files, machine learning models, etc.

* Go the (☰) menu and click `Analyze` -> `Analytics deployments`:

![(☰) Menu -> Analytics deployments](images/manage/ChooseAnalyticsDeployments.png)

* Click on `+ New deployment space`:

![Add New deployment space](images/manage/addNewDeploymentSpace.png)

* Select the _*Create an empty space*_ option.

![Create empty deployment space](images/manage/createEmptyDeploymentSpace.png)

* Give your deployment space a unique name, optional description, then click `Create`. You will use this space later when you deploy a machine learning model.

![Create deployment space](images/manage/createDeploymentSpace.png)

* Next, if you want to add a collaborator to the new deployment space, so that assets we deploy can be monitored, you can do so now by following the instructions for `access control` below. 
Otherwise, skip to `Step 2`. 

### Optional (Add collaborators to the space)

* Click on the `Access control` tab and then click on `Add collaborators +` on the right.

* Enter "admin" as a Collaborator and select the user from the drop down list. Then click on the `Add to list +` button.

* Click the `Add` button to finish adding the collaborator. You should be brought back to the deployment space page and see your user ID along with the `Admin` user as collaborators for this space. --> 
