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