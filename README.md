Tools : Alteryx was used to establish a connection to the database. The initial plan was to get a basic understanding of the data and create all necessary joins using Alteryx. Since the relevant table (tasks_used_da) only contained a few columns, I stopped using Alteryx and switched to Tableau to build out the calculations and queries.

Process : A key concept for this project is the accurate identification of active and churned users. Having segmented users into these two categories, I felt that more granular insight was required. I therefore further segmented active users into four additional subcategories (weekly users, bi-weekly users, active users who have a moderate risk of churn and active users with a high risk of churn). These categories were used as the lens to view customer behavior throughout the dashboard. The query that was used to generate this calculation is below;

IF DATEDIFF('day', {FIXED [User Id] : MAX([Date])},[Makedate YYMDD]) <= 28
AND DATEDIFF('day', {FIXED [User Id] : MAX([Date])},[Makedate YYMDD]) >= 21
AND {FIXED [User ID] : MAX([Sum Tasks Used])} > 0
THEN 'Risk of Churn'

ELSEIF DATEDIFF('day', {FIXED [User Id] : MAX([Date])},[Makedate YYMDD]) < 21
AND DATEDIFF('day', {FIXED [User Id] : MAX([Date])},[Makedate YYMDD]) >= 14
AND {FIXED [User ID] : MAX([Sum Tasks Used])} > 0
THEN 'Moderate Churn'

ELSEIF DATEDIFF('day', {FIXED [User Id] : MAX([Date])},[Makedate YYMDD]) < 14
AND DATEDIFF('day', {FIXED [User Id] : MAX([Date])},[Makedate YYMDD]) >= 7
AND {FIXED [User ID] : MAX([Sum Tasks Used])} > 0
THEN 'Bi-Weekly Users'

ELSEIF DATEDIFF('day', {FIXED [User Id] : MAX([Date])},[Makedate YYMDD]) < 7
AND DATEDIFF('day', {FIXED [User Id] : MAX([Date])},[Makedate YYMDD]) >= 0
AND {FIXED [User ID] : MAX([Sum Tasks Used])} > 0
THEN 'Weekly Users'

END

Please note : The MakeDate YYMMDD calculated field was created as the source date column was represented in the year 2017. For the sake of the analysis (and given the 28 day criteria for active users), I therefore assumed today’s date was June 04, 2017.

A key concept that emerged in the data discovery, analysis and visualization was that of a user cohort - defined as the amount of time (represented in days) that has elapsed since the user first signed up for the service. My working hypothesis was that this was a useful way to further segment and explore an individuals behaviour and interaction with the platform. Bucketing users based on their sign-up date highlighted a number of findings and user behavior.

Another point to highlight is the Average number of tasks. This components of this metric are the summation of user tasks divided by the number of days an individual has been on the platform. This KPI is then averaged out within each of the 7 day bin intervals. It is aparent that the older (154 day) customers are using the platform far more extensively than all other cohorts. This is across all user segments, but is most pronounced within the weekly user base. A further customer trend that is worth highlighting is the relative flatness of this engagement metric for all other user segments (hovering in the mid-single digits to low teens). 

Recommendations : The active customer base is comprised of a core group of weekly user's who have been using Zapier for around 5 months. These users are very familiar and heavily engaged with the platform. This is reflected in the dashboard via the number of days using Zapier, as well as an average of 60 tasks per session (considerably higher than all other segments). This segment of the population needs to be extensively researched - their behavior and interaction with the product is starkly different to that of all other user segments.  Further analysis is required within the core group of weekly active users, to better understand the variables, use cases and characteristics of this customer segment. 

Across all user segments, there was little sign of a spike in recent product adoption, with small / moderate customers numbers in the left tail of the customer lifetime distribution visual. This is somewhat concerning and a healthy concentration of new users signaling product acquisition. There is a significant increase in product engagement (reflected via task creation and tasks per session) around the 150 days since joining point in time. Little is known as to the root cause of this customer trend, however, subsequent effort should be dedicated to understanding this spike in engagement. 

Content specific recommendations include a tailored outbound marketing strategy driven by the user segmentation, as well consideration to regarding the length of time since joining the platform. This content should furthermore be properly tagged, so that clickstream data is able to be tracked, reported out and optimized for subsequent analysis. 

The final recommendation is to set performance KPI's for all user segments, across all product signup timeframes, for example an average task completion of 15 for all user segments within the first 28 days of joining Zapier. Continuously tracking the level of sustained engagement is critical to understanding user interaction as well as the sustained longevity of the platform.  

Packaging : The final deliverable is a Tableau dashboard (.twbx file). This will work on any machine with Tableau Desktop or Tableau Reader installed. Note : Tableau Reader is a light version of Tableau Desktop that will allow you to interact with the dashboard view, and has some of the full features removed.
