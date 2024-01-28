# Into to Splunk
1. What is splunk?
=> Splunk is a software platform designed for searching, monitoring, and analyzing machine-generated data. It is commonly used for log analysis, security information and event management (SIEM), and business intelligence. Splunk can index and correlate data from various sources, providing powerful search and visualization capabilities to extract meaningful insights from large and diverse datasets.

![Screenshot from 2024-01-28 21-22-52](https://github.com/SuzilSK/Cyber-sec/assets/129137449/a3ecdeb4-d628-427e-b4b7-8f7ab095a387)

2. Using splunk web
=> Splunk web is pre configured environment, there are three pre defined roles in splunk enterprise a. Admin - Full access b. Power - It will perform real time searches. c. User - user can access own knowleadge object.

![Screenshot from 2024-01-28 21-24-03](https://github.com/SuzilSK/Cyber-sec/assets/129137449/fc1a4a5c-4dc5-4cc7-97ba-b8a7ca0ce627)

Splunk default lauch environment

![Screenshot from 2024-01-28 21-24-45](https://github.com/SuzilSK/Cyber-sec/assets/129137449/32b83315-14d7-425d-98ab-dc01428da4fb)

3. Using search
Search option is used to search the incident log with time span.

# Limiting a search by time is a key to faster result and is a best pratice.

Eg. Installing hollywood in remote VM (Kali) and we can see the installation logs in splunk enterprises.

![Screenshot from 2024-01-28 21-26-49](https://github.com/SuzilSK/Cyber-sec/assets/129137449/1a4c0824-c4e7-4817-afe2-dfe202a0c714)

Commands that create statics and visualisation are called transforming commands.

We can share the share job log with other user it will remian active for 7 days, and every 10 min we need to refresh the log search.

We can dowload the report in csv,xml,json.

4. Exploring Events

![Screenshot from 2024-01-28 21-27-40](https://github.com/SuzilSK/Cyber-sec/assets/129137449/6205f014-2e70-4cd0-ba9f-5d150f8338b7)

Many events actions filter will be available.

5. Using search term

In filters we can use terms of keywords.

Eg. fail*, failed, FAILURE
![image](https://github.com/SuzilSK/Cyber-sec/assets/129137449/a0ca681a-e929-44a4-891f-4b157ce27e11)

search terms are not case senstive and booleans also we can use

Boolean operations have an order of evaluation a. NOT b. OR c. AND Note: parenthesis () should be used

![image](https://github.com/SuzilSK/Cyber-sec/assets/129137449/9f5bf60a-69ff-426c-90cd-47bee932163d)

![image](https://github.com/SuzilSK/Cyber-sec/assets/129137449/4604081f-c486-46d0-a372-4671776bd89b)

User can customize the filter as per the requirements.

6. What are commands ?

Search splunk language contain 5 component’s

a. search term - Fiundation of search query. b. commands - Commands is used to customize the log as per the need like charts, statistics and formatting. c. functions - How we need to display the charts and evaluate the results. d. arguments - It is the variables which we want to apply in the functions. e. clauses - It will group the result as per the requirement.

![image](https://github.com/SuzilSK/Cyber-sec/assets/129137449/5198f24c-bffc-49fc-a1a5-cb39b94ab9e0)

7. What are knowledge objects?

It is tools that help you discover and analyse the data, will be grouped in 5 categories .

a.Data Interpretation b.Data classifications c.Data Enrichment d.Data Normalisation e.Data Model

Knowleage object is use full for several reasons it can be create by one user and share with other user with permission granted. It is powerful tool for your deployment

Data Interpretation - Fields

![image](https://github.com/SuzilSK/Cyber-sec/assets/129137449/afc77696-bba3-45c6-8315-ba4fa4a8f1f0)

Data Classification - Event Type

![image](https://github.com/SuzilSK/Cyber-sec/assets/129137449/a7998452-70fc-4dda-944f-d2475df12895)

8. Creating Reports

Customize the report using visualization trick and statistics charts

![Screenshot from 2024-01-28 21-32-21](https://github.com/SuzilSK/Cyber-sec/assets/129137449/2c1fda9c-e172-4044-b6b2-4bc039c7c9f1)

9. Creating Dashboards

Creating new dashboard for User

![image](https://github.com/SuzilSK/Cyber-sec/assets/129137449/bf30f34d-6d01-430b-8dc2-0f0186645a16)

![image](https://github.com/SuzilSK/Cyber-sec/assets/129137449/506ccdbd-9e68-44ba-9286-63ad0f59622d)

![image](https://github.com/SuzilSK/Cyber-sec/assets/129137449/11bdef23-b535-4b68-9a73-9a8bbc6ea5a0)

As per the requirement of the report and analyses we can customize the dashboard accordingly.

10. Dashboard Studio

Classic Dashboard

![image](https://github.com/SuzilSK/Cyber-sec/assets/129137449/ca24ec86-9bbc-4d6f-8f80-c46148906b01)

Cloning exisitng dashboard into studio dashboard

![image](https://github.com/SuzilSK/Cyber-sec/assets/129137449/15d20375-8872-494b-bd50-1873016933cd)

Multiple customisation available to update the classic dahsboard

![image](https://github.com/SuzilSK/Cyber-sec/assets/129137449/4aceaeed-c851-4352-9bb3-d8205f820f13)

