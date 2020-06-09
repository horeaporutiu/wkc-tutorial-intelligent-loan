# Implement data governance to manage and secure clients’ data

It's no secret that data breaches are one of the worst ways
to reach the headlines, and that even one breach can mean an [average cost of 3.9 million USD](https://www.varonis.com/blog/data-breach-statistics/). With data 
becoming more and more of a competitive advantage, and the amount of data that is produced world-wide 
projected to double [from 2020 to 2023](https://www.statista.com/statistics/871513/worldwide-data-created/), 
the process of organizing, managing, and securing your data is more 
important than ever. It's no surprise that the tools to take that data, organize it, govern it, and ensure quality and searchability are what is needed at 
this point. 


As companies are building up their journey to take advantage of their data 
through AI, many businesses already have the first step of collecting data completed. They
store data in a database, and they use that data to inform customers of their previous 
transactions, conversations, and other information related to a customer. The second step, or "organize" is
focused on creating the foundation of analytics. More specifically,
it's about enabling your data scientists and business analysts to do their job efficiently. 
The focus of this tutorial will be around the "organize" step of the AI Ladder. 

These tools will help power the needs of data scientists and business analysts
through self-service analytics, while keeping sensitive data masked, and ultimately enable you 
to take advantage of your data all while minimizing the risk of a data breach. 


This is 
where a secure metadata management platform like Watson Knowledge Catalog comes in. At its core
Watson Knowledge Catalog (or WKC for short) connects data and knowledge with the people who need 
to use it. Some of the typical use cases for a tool like Watson Knowledge Catalog is 
ensuring regulatory compliance, data quality management, data delivery, and others, but for the
purpose of this tutorial, we will focus on privacy and protection - with the goal of 
minimizing the chance for a data breach.

Some of the challenges with organizing your data.

1. data preparation is usually manual. This means that 
it is time-consuming, and not repeatable. 

2. Sharing data needs to be safe and compliant. There is data inside and outside the firewall, and that 
your employees have access to the data, but not too much access to the data. 

3. Protect personal data and keep up with regulations.


This leads us directly to what Watson Knowledge Studio is built to do: 

1. Automating data preparation. WKC will do this out of the box.

2. Automatically classifying data and assigning business terms. This will enable us to have a consistent 
data vocabulary across the company and the industry.

3. Maybe the most important of all. Automatically detect sensitive data and enforce privacy rules. This way
we can minimize risk and maximize compliance. 

4. Track use of data, so we can create reports for compliance.

Furthermore, Watson Knowledge Studio is awarded as being a "Leader" in the October 2019 edition of 
Metadata Management solutions by Gartner. So you know that it an industry-leader for what it does. 

Let's start by diving into the tutorial. We will focus on the use case of a bank. We want to ensure that 
we are providing loans in an efficient and fair process. To do this, we will take 6 main steps to transform
our business to organize our data to enable our data scientists and business analysts to do their best work.

1. We will start by importing business terms. This will form the foundational vocabulary that will comply 
with industry-standards and will enable consistent and precise data-driven dialog in our company.

2. We will import categories. This will help us classify data assets as sensitive or non-sensitive. We 
need this to create rules to automatically mask data later on.

3. We will add data classes. This will help us profile our assets and help us when creating rules for 
sensitive data as well.

4. Add rules for policies. This will help us mask sensitive data, so that when we share it with data 
scientists, they will not be able to access sensitive customer information.

5. Check the data quality.

<!-- # Pre-work

Follow these steps to begin your hands-on tutorial. 

## Log into Cloud Pak for Data
Launch a browser and navigate to your Cloud Pak for Data deployment.

## Create a new project 
Launch a browser and navigate to your Cloud Pak for Data deployment.

<img width="1383" alt="cpd-login" src="https://user-images.githubusercontent.com/10428517/84182042-a3bd2e00-aa3e-11ea-9e22-916e67ebfe1d.png">

In Cloud Pak for Data, we use the concept of a project to collect / organize the resources used to achieve a particular goal (resources to build a solution to a problem). Your project resources can include data, collaborators, and analytic assets like notebooks and models, etc.
* Go the (☰) menu and click `Projects`.

<img width="696" alt="cpd-projects-menu" src="https://user-images.githubusercontent.com/10428517/84182036-a0c23d80-aa3e-11ea-8a0f-005730bf489f.png">

Create an `Analytics` project for the project type and click on `Next`.

<img width="1388" alt="cpd-new-project" src="https://user-images.githubusercontent.com/10428517/84182041-a3249780-aa3e-11ea-936b-cb49af7554d9.png"> -->


This exercise demonstrates how to solve the problems of enterprise data governance using Watson Knowledge Catalog on the Cloud Pak for Data platform. We'll explain how to use governance, data quality and active policy management in order to help your organization protect and govern sensitive data, trace data lineage and manage data lakes. This knowledge will help users quickly discover, curate, categorize and share data assets, data sets, analytical models and their relationships with other members of your organization. It serves as a single source of truth for data engineers, data stewards, data scientists and business analysts to gain self-service access to data they can trust.

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

First we'll create a catalog and load some data

### Create the catalog

#### Provision Watson Knowledge Catalog the First Time

If you haven't yet started Watson Knowledge Catalog, you'll need to provision it.

* Open Watson Knowledge Catalog by clicking the *Services* icon at the top right of the home page:

![click services icon](/images/wkc-admin/wkc-click-services-icon.png)

* Under the *Data Governance* section, click on the *Watson Knowledge Catalog* tile:

![open wkc](/images/wkc-admin/wkc-open-service.png)


![select classification type](../.gitbook/assets/images/wkc-admin/wkc-add-classifications.png)

* Click `New classification` dropdown and select `Create new classification`. These classifications can then be added to your category as a *Type*: 

![select classification type](../.gitbook/assets/images/wkc-admin/wkc-add-classifications-2.png)

## 4. Add data classes

When you profile your assets, a data class will be inferred from the contents where possible. We'll see more on this later. You can also add your own data classes.

* Add a data class for your assets by going to the upper-left (☰) hamburger menu, choose `Organize` -> `Data and AI Governance` -> `Data classes`, then click `New data class` -> `Create new data class`:

![organize data classes](../.gitbook/assets/images/wkc-admin/wkc-menu-organize-data-classes.png)

* Give your new data class a name, i.e. *alphanumeric*, and an optional Primary category and/or description, and click `Save as draft`:

![new data class](../.gitbook/assets/images/wkc-admin/wkc-create-data-class.png)

* Once the data class is created, we can add *Stewards* for this class, and also associate *classifications* and *business terms*. When you are ready, click `Publish`:

![tools for data class](../.gitbook/assets/images/wkc-admin/wkc-data-class-add-term-publish.png)

![publish comment data class](../.gitbook/assets/images/wkc-admin/wkc-data-publish-comment.png)

Now let's add that data class to a column in our *Telco-Customer-Churn.csv* asset.

* Go back to your Telco catalog and open it up to the column view ((☰) hamburger menu `Organize` -> `All catalogs` and choose `Telco catalog`). Under the *Browse assets* tab, click on the data set *Telco-Customer-Churn.csv* to get the column/row preview. Scroll right to get to the *CustomerID* column and click the down arrow next to "Customer Number" and then *View all*:

![change data class](../.gitbook/assets/images/wkc-admin/wkc-admin-existing-data-class.png)

* In the window that opens, search for your newly created data class, *alphanumeric* and click it when it returns in the search. Then click *Select*:

![Set column to numerical data class](../.gitbook/assets/images/wkc-admin/wkc-admin-alphanumeric-data-class.png)

## 5. Add Business terms

You can use [Business terms](https://dataplatform.cloud.ibm.com/docs/content/wsj/governance/dmg16.html) to standardize definitions of business concepts so that your data is described in a uniform and easily understood way across your enterprise.

You already saw how to create a category and make it a *business term*. You can also create the business term as it's own entity.

* From the upper-left (☰) hamburger menu, choose `Organize` -> `Data and AI Governance` -> `Business terms`:

![organize Data Business terms](../.gitbook/assets/images/wkc-admin/wkc-organize-data-business-terms.png)

* Click on the upper-right `New business term` drop down and choose `Create new business term` button:

![create business term](../.gitbook/assets/images/wkc-admin/wkc-create-business-term.png)

* Give the new Business term a name such as *Billing* and optional description, and click `Save as draft`. NOTE that others on the platform will be creating a business term for this workshop, so perhaps pre-pend your term with something unique, i.e *scottda-Billing*:

![name new business term](../.gitbook/assets/images/wkc-admin/wkc-name-new-business-term.png)

* A window will come up once the term is created. You can see a rich set of options for creating related terms and adding other metadata. For now, click `Publish` to make this term available to users of the platform:

![publish business term](../.gitbook/assets/images/wkc-admin/wkc-publish-business-term.png)

* Add an optional comment and click `Publish` in the new window:

![verify publish business term](../.gitbook/assets/images/wkc-admin/wkc-click-publish.png)

* Now go back to your Telco catalog and open it up to the column view ((☰) hamburger menu `Organize` -> `All catalogs` and choose `Telco catalog`). Under the *Browse assets* tab, click on the data set *Telco-Customer-Churn.csv* to get the column/row preview. Scroll right to get to the *TotalCharges* column and click the *Column information* icon (looks like an "eye"):

![choose TotalCharges column information](../.gitbook/assets/images/wkc-admin/wkc-totalcharges-column-information.png)

* In the window that opens, click the *edit* icon (looks like a "pencil") next to *Business terms* :

![edit business terms](../.gitbook/assets/images/wkc-admin/wkc-assign-terms-to-column.png)

* Enter *Billing* (or your uniquely named term such as *scottda-Billing*) under *Business terms* and the term will be searched for. Click on the `Billing` term that is found, and click `Apply`:

![edit business terms](../.gitbook/assets/images/wkc-admin/wkc-search-billing-to-assign-term.png)

Close that window once the term has been applied.
Now, do the same thing to add the *Billing* Business term to the *MonthlyCharges* column.

* You will now be able to search for these terms from within the platform. For example, going back to your top level *Telco Catalog*, in the search bar with the comment "What assets are you searching for?" enter your unique *<unique_string>Billing* term:

![search using business terms](../.gitbook/assets/images/wkc-admin/wkc-search-business-terms.png)

The *Telco-Customer-Churn.csv* data set will show up, since it contains columns tagged with the *Billing* business term.

## 6. Add rules for policies

We can now create rules to control how a user can access data.

* Create a business term called *CustomerID* and assign it to your *CustomerID* column in the data set using the instructions above. See below if you need details, but try it yourself first, and skip to *Adding a rule* below if you do not need a reminder.

### How to create a Business term review

* From the upper-left (☰) hamburger menu, choose `Organize` -> `Data and AI Governance` -> `Business terms`.

* Click on the upper-right `+ Create Business term` button.

* Give the new Business term the name *CustomerID* and optional description, and click `Save as draft`. In the next window, click `Publish`.

* Now go back to your Telco catalog and open it up to the column view ((☰) hamburger menu `Organize` -> `All catalogs` and choose `Telco catalog`). Under the *Browse assets* tab, click on the data set *Telco-Customer-Churn.csv* to get the column/row preview. Scroll right to get to the *CustomerID* column and click the *Column information* icon (looks like an "eye"):

* In the window that opens, click the *edit* icon (looks like a "pencil") next to *Business terms* :

* Enter *CustomerID* under *Business terms* and the term will be searched for. Click on the `CustumerID` term that is found, and click `Apply`.

### Adding a rule

* From the upper-left (☰) hamburger menu, choose `Organize` -> `Data and AI Governance` -> `Rules`, 

![select rule](../.gitbook/assets/images/wkc-admin/wkc-rules-menu.png)

* then click `New rule` -> `Create new rule`.

![create rule](../.gitbook/assets/images/wkc-admin/wkc-create-rule.png)

* For the *New rule* -> *Select the type of rule to create* choose `Data protection rule`.

![data protection](../.gitbook/assets/images/wkc-admin/wkc-data-protection.png)

* Under *Details* give your rule a *Name*, *Type* = *Access*, and a *Business definition*.

* Next, under *Rule builder* *Condition1* fill out If *Business term* *Contains any* *CustomerID*  and Action then *mask data* *in columns containing* *alphanumeric*. Choose the tile for `Substitute`, which will make a non-identifiable hash. This obscures the actual CustomerID, but allows actions like database joins to still work. Click `Create`:

![define rule for masking customerID](../.gitbook/assets/images/wkc-admin/wkc-rule-substitute-customer-id.png)

* Now if we go back to our *Telco-Customer-Churn.csv* asset in the catalog at the *CustomerID* column, it will look the same as before. But a non-admin user will see the "lock" icon and see that the customerID has now been substituted with a hash value:

![customerID is now masked](../.gitbook/assets/images/wkc-admin/wkc-masked-column-customer-id.png)

* To add a rule to *Obfuscate* data, go to the `Profile` tab and scroll to the *TotalCharges* column. You can see that the data has been inferred to be classified as a *Quantity*:

![TotalCharges classified as Quantity](../.gitbook/assets/images/wkc-admin/wkc-inferred-classifier-totalcharges.png)

Here is where you could change the classification if the inferred one was not what you wanted.

* You can build a rule to *Obfuscate* this *TotalCharges* column:

![TotalCharges obfuscate rule ](../.gitbook/assets/images/wkc-admin/wkc-build-obfuscate-rule.png)

* And now that column will have data that is replaced with similarly formatted data:

![TotalCharges column obfuscated](../.gitbook/assets/images/wkc-admin/wkc-obfuscated-totalchurn-column.png)

This ends the Watson Knowledge Catalog for Admins lab.