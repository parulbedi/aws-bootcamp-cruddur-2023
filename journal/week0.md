Before jumping into the bootcamp there are few services where I have to create account, out of those there were few services where I already have account and for another I need to register:

•	Github Account – Already created

•	Gitpod Account - and also install its extension (I am using Microsoft Edge and it is compatible with the browser)

•	AWS account – Already created

•	Lucid Chart Account – Similar to draw.io but here you can share your diagrams with url to anyone.

# Week 0 — Billing, Architecture, Security
I learned about billing, security, and architecture of AWS with respect to security.

### 1. Few key points which I learned and were very crucial while working with AWS or any other cloud provider:
•	Pricing of services or resources vary and dependent of region to region

•	Setting billing alarm so that we remain under our desired budget and don’t get huge bills.

•	Attaching Administrator Access & billing policy to IAM user (i got stuck here,but found a way to how to get billing details in IAM user account)

•	I have my AWS free tier active and resources needed for this bootcamp is accessible to me.

•	Learned about TOGAF and C4 Model and few others, those all are created to tackle one problem i.e “How to break a complex Architecture in to a simpler task”

•	Got to know about various section of billing dashboard alog with its other components including Cost explorer, AWS Calculator, Billing alerts



### 2. High Level Logical Diagram:

logical architecture design of micro blogging app - cruddur. worked around with this Lucid Charts tool for a day and understand most of its options. 
it can be break down in to 4 main areas:
1. Frontend -  Java Script
2. Backend - Python
3. Authentication - Cognito
4. 3rd Party Caching - Momento

![Architecture image](https://github.com/parulbedi/aws-bootcamp-cruddur-2023/blob/main/Logical%20Diagram.jpeg)

shareable link added below:

https://lucid.app/lucidchart/3163b124-8e5f-4677-acc6-d78f701e6522/edit?viewport_loc=-790%2C-176%2C2994%2C1495%2C0_0&invitationId=inv_2a05406c-3db3-4e44-8644-d9f71e0e5070


### 3. Napkin Design (Draft design):

just a basic design (On a Napkin) 😜. Will draw a daigram in lucid charts soon.
![Architecture image](https://github.com/parulbedi/aws-bootcamp-cruddur-2023/blob/main/napkin_design_v2.jpg)

### 4. Got stuck when i was not able to see billing details from IAM user account

![Architecture image](https://github.com/parulbedi/aws-bootcamp-cruddur-2023/blob/main/msedge_5FyBJzPN9.png)

I followed 2 steps to configure the settings and then billing dashboard was accessible in IAM user account (that is my IAM account)

#### Step 1: Activate IAM Access

to acheive this i followed the following steps:
##### a. Login to the root account, Click on --> root --> Account
![Architecture image](https://github.com/parulbedi/aws-bootcamp-cruddur-2023/blob/main/msedge_zHnqsOcsew.png)

##### b. Scroll down to --> "IAM User and Role access to billing Information" Section and Click on "Edit"
![Architecture image](https://github.com/parulbedi/aws-bootcamp-cruddur-2023/blob/main/msedge_Gj9e2eH04r.png)

##### c. Click on the checkbox and click on "Update"
![Architecture image](https://github.com/parulbedi/aws-bootcamp-cruddur-2023/blob/main/msedge_E78l88O6lr.png)
