Tools : Alteryx was used to establish a connection to the database. The initial plan was to get a basic understanding of the data and create all necessary joins using Alteryx. Since the relevant table (tasks_used_da) only contained a few columns, I stopped using Alteryx and switched to Tableau to build out the calculations and queries.

Process : A key concept for this project is the accurate identification of active and churned users. Having segmented users into these two categories, I felt that more granular insight was required. I therefore further segmented active users into four additional subcategories (weekly users, bi-weekly users, active users who have a moderate risk of churn and active users with a high risk of churn). The query that was used to generate this calculation is below;

These categories were used as the lens to view customer behavior throughout the dashboard. 

Please note : The MakeDate YYMMDD calculated field was created as the source date column was represented in the year 2017. For the sake of the analysis (and given the 28 day criteria for active users), I therefore assumed today’s date was June 05, 2017.

A key concept that emerged in the data discovery, analysis and visualization phase was that of a user cohort - defined as the amount of time (represented in days) that has elapsed since the user first signed up for the service. My working hypothesis was that this was a useful way to further segment and explore an individuals behaviour and interaction with the platform.

Packaging : The final deliverable is a Tableau dashboard (.twb file). This will work on any machine with Tableau Desktop or Tableau Reader installed. Note : Tableau Reader is a light version of Tableau Desktop that will allow you to interact with the dashboard view, and has some of the full features removed.

Recommendations : The active customer base is comprised of a core group of weekly user's (individuals who have logged into the platform within the past 7 days and had more than 1 task in a given session) who are familiar and heavily engaged with the platform for around 5 months. This statement is reflected in the dashboard with the number of days using Zapier, as well as an average of 60 tasks per session (considerably higher than all other segments). Further analysis is required within the core group of weekly active users, to better understand the variables and characteristics of this customer segment. 

Across all user segments, there was little sign of a spike in recent product adoption, with small / moderate customers numbers in the left tail of the customer lifetime distribution visual. There is a significant increase in product engagement (reflected via task creation and tasks per session) around the 150 days since joining point in time. 

Content specific recommendations include a tailored outbound marketing strategy driven by the user segmentation, as well as the length of time since joining the platform. This content should furthermore be tagged, so that clickstream data is able to be tracked, reported out and optimized. 
