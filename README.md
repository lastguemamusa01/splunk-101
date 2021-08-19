# splunk-101
splunk basic courses

Splunk course

Machine data -> splunk use it -> operational intelligence in your business

Labs do in localhost

Machine data – everywhere – devices(building, cars, server, phones) – data is different format – some have structure some not.

Difficult to process – messy

Different servers have different sources of data

Error on user – it support – dev – application – data base admin – 9 hrs for one issue to fix

With machine data – error on user – it support log the issue, devs search for data for events for purchase events – pinpoint event have in the url get the parameters – paramtersw are correlated to an entry in slow query log -> escalate to application dev
-	Can set alarm when detect fail, before customer report
-	Pinpoint, correlate and alert on specific event – splunk

Splunk is like a filter to a data to search index with structure, allowing extract info you need(application issues, security, user behaviour, hardware monitoring, sales total, etc)

-	Translator for you data monster

-	Five main functions in splunk

o	Index data – collects data from virtually any source, indexer is the factory and data ir raw materials, inspectors work(look at the data and how to process it), when thy match the data type the label data with a source type, works use that data to break the data into single events(with time stamp normalized), the events are then store in the splunk index

o	Search and investigate – search events that cotain that value, across multiple data sources(allowing analyze and run statistics on events using splunk search language).
o	Add Knowledge – add knowledge objects to your data. How your data is interpreted. Fucking tag(give classification and enrichment, normalize it and save reports for future use)
o	Monitor and alert – montor all your infrastructure in real-time, to identify issues, problems and attacks before they impact your customers and services. Create alerts to monitor for specific conditions and automatically respond with a variety of actions
o	Report and analyze – allows collect reports and visualization into dashboards

3 mains components(basic component, there are more components) in splunk that make enterprise – indexer(process incoming data and process as events and store in slunk index, its organize files in directories by time(for search)), search head(allows search use splunk language to search indexed data, search head handle search requests form users and distributes the requests to the indexers, perform actual searches on data. Consolidate and enrich the results from the indexers, before returning to the users, provide dashboard, reports and visualizations ) and forwarder(consume data and forward it to the indexers for processing(require minimal resources, little impact on performance, reside on the machines where the data originates ) ).

Example in the web server, install forwarder and this server with forwarder send data to indexer. Most splunk deployments, forwarders serve as the primary way data is supplied for indexing.

How I scales indexer, search head and forwarder


Deployments and scaling splunk

Splunk can scale from single instances to a full distributed infrastructure.

Single instance deployment – one instance of splunk enterprise handles all the functions of splunk(input, parsing, indexing and searching) – perfect for proor of concept, personal use, learning and might serve the needs of smaill, department-sized enviroments


Production environment – need full distributed infrastructure, divide the features, multiple search head(can be cluster), indexers, etc.

Installing splunk for 3 os or splunk cloud –

Splunk app and roles – app have search, datasets, reports, alerts and dashboards. Admin role can define roles. Roles what users see or do. Admin(can do anything, create user with roles, intall a apps, create knowledge objects for all users), power(create and hsare knowledge objects for users of an app and do realtime searches), user(will only see their own knowledge objects and those shared with them)

Have default 2 apps in left , apps config and search&reporting

There are more apps or you can create you own app.


Adding data is done by the admin user for the deployment

Admin -> add data -> get data from cloud computing, networking, OS and security configuration
Or
Upload from file like csv, monitor(files, directories, http events, network ports like tcp/udp or data gathering scripts. For windows splunk there are more options for windows specific data like active directory.) or forward( you can receive data from external forwarder installed in remote machine, main source of data input).

Upload input option data(Upload from file like csv) not for production, is for testing or for need to search a small dataset that never get updated.
 
Splunk use sourcetype to categorize the type of data being indexed.

When save source type you need name it, category and for what app is this sourcetype for.
Then select host name -> shoud be the name of the machine from which these events originate(you can use constant value, regular expression on path or segment in path ). 

Set an index to import the data into or create new one

Indexes are directories where the data will be stored.

First tendency was store all data in the main index that allow search all data.

Separate indexes can make your searches more efficient like
Web data, main and security index.

Also multiple indexes allow limiting access by user role. Also depending what kin of data or indexes you can set different time intervals for storing by time(set retention policy by index)

When the data you want to index comes from files or ports on an indexer – use monitor – 

Example – monitor an apache log file on this server – click files and directories – browser button and locate the log file selecting -> access.log. you can continuously monitor or index once. Select continuously monitor. You can select black and white list.

Splunk select predefined source type of data. In here we can select which app context to use for the input(search and reporting(search)).

Setting up forwareders is not in this course.

Splunk uses ___sourcetype_____ to categorize the type of data being indexed.



Search and reporting app. – create knowledge object, reports and dashboards and more.

7 main components for search and reporting app menu

splunk bar to switch between app, edit your account, system level messages, settings, activity, help – header
Below of splunk bar – there are app bar – this is app menus

Below is search bar to do searches – you have specific time period to select

Below is search history menu – allows you to view and rerun past searches.

Below – how to search panel – we are button to documentation and tutorial
In the right – what to search panel – give summary of the data that is indexed on this server (indexed events, earliest event and latest event).
Click data summary button to see the specific indexed data information
You can see by sourcetypes(classification of your data), source(file or directory path, network port, or script from which the event originated) and hosts(is ip address or fully qualified domain name)


Using the search bar –

To search someone wanted to access with wrong credentials

Search – failed – with last 7 days
You have options in save as – to save your result
Have search result tabs, search actions buttons, search mode selector and time line
-	Patterns tab can show you some statistics  or patterns.
-	Statics and visualization tabs – if you have it shows, if not you can create by pivot, quick Reports and search commands(this are called transforming commands, transform data to data tables)
Events contain the search text
Left have fileds that have extracted
We can see total of the events and start date and end date, random samples of this events

In job drop down – you can edit job, inspect job and delete job, send job to background
-	There are pause, stop, share, print and export the job

By default – a search job will remain active for 10 minutes.
Shared search jobs – remain active for 7 days and will be readable for anyones.

Export to csv, xml or json format. 
There are 3 search modes you can choose from the search mode selector (fast(field discovery is disable in this mode, return only default field and required field), smart (toggle between 2 mode depending your search) and verbose(returns as much field and event data as possible))

-	Timeline is visualization of the events occurred in the time. – number of event on time- time range drage to zoom, event list is update the selected , zoom in and out

Zoom in is done in the original search and zoom out need to do new search to get the recent changes.


Using the events and field to dig it. – exploring the events list

Returned search in the events the searched text is highlited with time – showing always the recent events

We will see time difference by the GMT time, from where you are

We have default host, source and sourcetype

You can also allow you to add that text to the search – add to search, exclude from search or new search with the text your courses is on – its has button to open in new browser option


In the left we have info filed, when you expand you can see all the extracted fields for the event – this have event actions and column of actions that is a link for field actions

You can see as raw, list or table – view options for the data

Exploring search term options in splunk

fail* -> search all words that start fail word – wildcards
you can use uppercase Booleans like – NOT, OR, AND

failed NOT password
failed password – implicit and

Boolean operations – first – Not, second Or, third AND

Adding parenthesis emphasys that this Boolean is first

failed NOT (success OR accepted)

exact search with quote – “failed password”

for search word with quotes use backslash

info=”user \”chrisV4\” not in database”



Using the fields sidebar – side bar its shows selected fields and interesting fields(have values in at least 20% of the events). a is string value y # is numeral. Clicking its shows the values that fields.
You can create reports and add in the select clicking in yes -> add to the currently search

When click top values -> return the most repeated 5 values in the visualization and statistics

Click all fields to see al fields – you can filter field, number of the values, event coverage and type.


You can refine and run more efficient searches by using fields in them

sourcetype="linux_secure"   -> search only in linux secure source type

fieldname is case sensitive and values are not case sensitive

field operators is = , !=.     can be used with numerical or string values

>, => , < , <= can be used for numerical values only

Field can be added in you search by click the value of the fields on the side bar

host!=mail* is the same as.  NOT host=mail* ,   but the results are different, 


index=web status IN(“500”,”503”,”505”).  -> this is like using OR various times


NOT (host=mail* OR host=www1) – search condition


Best practices – general search practices

Using time to limit the events returned(ex. last 7 days than all time), less data to search will be more fast.

Use index, source, host and source type -> 
More you tell the search engine – the more likely it is that you will get good results

Better failed password than password

Inclusion is better than exclusion -> 
“access denied” better than.  NOT “access granted”

Use early Filtering commands  -> sourcetype =

Splunk has preset of time ranges, relative and data and time range
There are real time option

There are advance option -> time abbreviations – s,m,h,d,w,mon,y    
-30m@h    -> @ round down -> 9:37 now -> search 9:30

Also you can use in the search
Earliest=-2h latest=-1h.  -> ealiest start time and latest end time

Ealiest= 01/08/2018:12:00:00      -> month/day/year hour/minutes/seconds

Most efficient way of sarch is by time

Using indexes -> indexes are where splunk stores event data for searching

Splunk adminstrators will often use multiple indexes to segregate data

Like web data, security data. -> search more efficient, and limit by role to access index for security reasons.

In the search input -> index=web OR index=security.  Or index=ma*

Index = main


Splunk search language

Build by 5 components

Search terms – 
Commands – tell what we want to do with the search results – include creating charts, computing statistics and formatting.

Functions – how we want to chart, compute and evaluate the results
Arguments – are the variables that we want to apply to the function
Clauses – explain how we want results grouped, or defined

Sourcetype=acc* status=200 | stats list(product_name) as “Games Sold” |

Sourcetype=acc* status=200   -> search term

| stats list(product_name) as “Games Sold”. -> first search components |
inside the stats command there is a function of list with an argument of product_name
as is the clause.  This is separate by 2 pipes.->. |

we use a pipe to tell splunk to pass the current results to next component -> pass the search termns result to next component

splunk include visuable tools to help craft your search
visual syntax tools for SPL -> as you type search assistant provide auto-complete features and parts of the search string are automatically color coded.

Boolean operators and command modifiers will display in orange
Commands is in blue
Command arguments show up in green
While functions dipsly in purple
When you put the cursor in the end of parenthesis, its show the open parenthesis

Command(cmd)+\   ->  move to new line the each pipe.

In the preferences,  SPL editor -> you can set 


Search limitations -> the left to right flow of search terms,  all search is in ram or memory – what you removed in pipe its no available for the next pipe

The fields command – limit fields and search faster.

To include fields

Index=web sourcetype=access_combined
| fields status clientip

Return clientip and status -> fileds showed in the left side bar

To exclude fields
Index=web sourcetype=access_combined
| fields - status clientip

Return all fields but status client ip is dissapared

Field extraction is one of the most costly parts of searching in splunk

Limit your fields can make your search more efficient

Field inclusion happens before fields extraction and can improve performance
Field exclusion happens after field extraction, only affecting displayed results.  

Better inclusion than exclusion

The table command – is similar to the fields command, 
Retains searched data in a tabulated format. 

Index=web sourcetype=access* status=200
Product_name=*
|table JSESSIONID, product_name, price

We get only 3 columns in table -> each row represent event

Change order of argument in the search table to reareange 

The rename command – use to rename fields

Index=web sourcetype=access* status=200
Product_name=*
|table JSESSIONID, product_name, price
| rename JSESSIONID as “User Session”
Product_name as “Purchased Game” price as “Purchase Price”

Once renamed, original name is not availab to subsequent search commands

Fir subsequent command you need to use new name


Index=web sourcetype=access* status=200
Product_name=*
|table JSESSIONID, product_name, price
| rename JSESSIONID as “User Session”
Product_name as “Purchased Game” price as “Purchase Price”
| fields – “User Session”

We need to wrap the name of the field in quotes if the name is a phrase

The dedup command – removes events with duplicate values

Index = security sorucetype= history*
Address_Description=”San Francisco”
| dedup Username
| table Username First_Name Last_Name

Or you can use combinations of the values

| dedup First_Name Last_Name

The sort command let you display your results in asceding or descending order

Sourcetype=vendor_sales
| table Vendor product_name sale_price
| sort Vendor product_name

String data is sorted alphnumerically and numeric data is sorted numerically

By default is ascending order

|sort + sale_price        -   ascending order

|sort - sale_price        -   descending order

| sort – sales_price Vendor    - the space between minus and sales price affect to all.

| sort –sales_price Vendor    - no space between minus only affect sales price descending order

Sort command also lets you limit the number of events



Sourcetype=vendor_sales
| table Vendor product_name sale_price
| sort -sale_price Vendor limit=20

First 20 events will display
As a best practice and for best performance, place dedup as early in the search as possible. 

Splunk’s transforming commands – order search results into a data table for statistical purposes. Need this if you want to transform search results to visualization. 

Top command – finds the most common values of a given field in a result set


Index=sales sourcetype=vendor_sales 
| top Vendor

This return count of top ten vendors

| top Vendor limit 20.   – 20 results

| top Vendor limit 0.  – all results

| top Vendor product_name limit 0.  – multiple fields applied and all results


Clauses can also be used with the top command

Limit = int
Countfield = string
Percentedfield = string
Showcount = true/false
Showperc = true/false
Showother = true/false
Otherstr=string

| top Vendor limit 5 showperc=False .  – top 5 vender remove percentage colum n
Countfield=”Number of Sales” useother=True . – rename the countfield as number of sales and add a row for the number of sells for vendors not listed in the top 5. ( show below top 5 as OTHER)


| top product_name by Vendor limit=3
Countfield=”Number of Sales” showperc=False
-	Show top times split by another field, top 3 product sold by each vendor in the last 7 days

Top 3 product sold by each vendor


Rare command – has the same options as the top command, but shows the least common values of a field set

| rare Vendor limit=5 showperc=False             
Countfield=”Number of Sales” useother=True

- get the vendors who have sold the least amount of product this week

You can use by clause also here

Stats command – produce statistics of our search results

Common stats functions are – count, distinct count, sum, average, min, max, list, values

Count – return a number of events matching certain criteria

Distint count – returns a count of unique values for a field

Sum -returns the sum of numerica values


| stats count.   – create count column

| stats count “total sells by vendors”
By product_name,categoryid


| stats count(action) as ActionEvents.    – only the events that contain actian are counted


| stats count(action) as ActionEvents, count as “Total events”    – now you can compare


| stats distinct_count(product_name) as “Number of games for sale by vendors” 
By sale_price 
.  – splitting our count of games sold, by the price they were sold for

| stats dc (product_name) as “Number of games for sale by vendors” 
By sale_price 


| stats sum(price) as “Gross Sales” by product_name – show total of sales by product name

| stats count as “Unit Sold”
Sum(price) as “Gross sales” by product_name.  – the count and sum must be in the same pipe


| stats avg(sales_price) as “average price”
Min(sales_price) as “min price”
Max(sales_price) as “max price” by categoryId


| stats list(Asset) as “company assets” by Employee

-	Value – is like list but, return unique values for given filed

Index=network sourcetype=cisco_wsa_squid
| stats values(s_hostname) by cs_username      


This is for statistics and visualization(on chart)


Reports - Search for future or share the search with other users

Save as  -> title – description, time range picker show or not

Need naming conventions

Group of report for_type of object_simple description of report contains

Security_Report_FailedSshAttempts




When you run report -> its run the search 
In the reports tab – you can have access all your reports

In here you can edit description, permission, schedule and acceleration. Clone, embed and delete

Edit permissions – you can set permissions by user

Edit schedule – running time of intervals –

Edit acceleration – the result is store in to summary of data instead of the index.

You can also save the statics and visualization report

Visualization have various type of chart in splunk

Charts is based on numbers, time or location.


Dashboard – collection of the reports – compiled into a single pane of glass

f = false

| timechart count as “Units Sold” by product_name usenull=f useother=f

Select visualization tab
You can customize you chart type
You can customize format like x or y label

Save as dashboard panel 

New dashboard
Give title
Description
Permissions
Panel title
Panel content can be line chart or statics- table
-	Save and view dashboard

You can save existing dashboard to add more in the existing dashboard

You can add some number of sume or average to show the number in the dashboard

In the dashboards panel
You can click edit to move the dashboard and resize it
Source – you can see in xml

You can add panel and add input y dark theme options

Each chart – you can edit search, select visualization, format visualization and more actions with button

-	Add panel – from report, clone dhasboard , new



Edit -> add input -> time

When added time click edit icon is pencil – edit label, search on change, token for panel to use to reconized the input, default last 24 hours -> 7 days – click apply

The time range picker will only work on panels with an inline search

Location chart not working for time range, so click in view report, clone to inline, clone to inline search. Now this icon is edit search button – time range select the shared time picker (token) in time range. You need to this for all panels, then save

When you select time range this dashboard will going to updated

Pivot allows design the report simple format with ui

Data models – knowledge objects that provide the data structure that drives pivots

Admin and power role can create data models.
Data model is the framework and pivot as the interface to the data

Each data model has data sets

Data set – smaller collection of data defined specific purpose. They are represented as tables. Fields names for columns and fields values for the cells

Creating data model they can use pivot to not created every specific reports. With the pivot they can change fast what they want

Settings -> data models -> pivot
A list of datasets appears for the data model
Data set is slice of data

Select ime and categories – add table to showing table, split rows, split columns
Filter plus match is not Accessories , add filter to remove tee

Side bar to visualize the chart to save the report and add to dashboard

Instant pivot – less experienced user need to create report, but data model doesn’t exist. This working pivot without first data model.

When you search en statidistics or visualization tab – show options pivot

Show fields dialog – all fields, selected fields or fields covered by percentage.
Click ok – pivot interface – filter by time, split rows, split columns, change the type of chart in side bar, and save as report or add in the dashboard

Data sets – that make up data models – allow user access small set of data can help them gain operational intelligence from the data.

Select datasets tab – click table – field names are column headers, event field data is displayed as row.
You can view summarize fields option tab. – information field name and value
In explore button visualize with pivot or investigate in search.
Explore options also available in datasets page

Datasets help users find data and get answers faster

Splunk also has a datasets add-on that you can download at splunkbase, this allows you to rapidly build dataset tables, without using splunk search language


Lookups – allow you to add other fields and values to your events not included in the indexed data.  We can combine fields form sources external to the index.
With search events – cs files, script etc
RFID , product id , 
After configure your look up – you can search, and sidebar appared

A lookup is categorized as a dataset.

2 steps to set up look up files

1  Define lookup table
2 – defin the lookup

Optionally you can configure your lookup configure automatically

Once defined, lookup field values are case sensitive by default

Settings – select lookups

Click in add new in lookup table files

Destination app – search(app)

Upload lookup file

Choose a name for splunk to call the file on the server -> destionation filename - > http_status.csv

Click save

You can see list of look up table files, you can change permission,  move(another app) or delete

In the search

| inputlookup http_status.csv     -> to see input uploaded lookup table file


Defin the lookup –
Settings – lookups – lookup definitions – click add new

Select destination app like search
Name – http_stattus
Type file-based
Looukup file -> http_status.csv 

You can configure time based lookup – checking up

Advanced options – allow minimum and maximum matches. In here you can check off case sensitive match 
For huge file – batch index query improve the search performance by grouping index queries

Match type – set up non exact matching for you lookups

Filter lookup – use splunk search language to filter results form the lookup table before returning the data






Lookup command in search

Index=web sourcetype=access_combined NOT status=200
| lookup http_status code as status       – we are matching status values to code values

Now you see description field from look up table

By default, all fileds in the look up table are returned as output fields, except the input field

Index=web sourcetype=access_combined NOT status=200
| lookup http_status code as status       – we are matching status values to code values
OUTPUT code as “HTTP Code”   
Description as “HTTP Description”
 – we can choose what fields our lookup returns by adding an OUTPUT clause

OUTPUTNEW –  when you do not want to overwrite exiting fields. Because OUTPUT overwrite existing fields.

| table host,”HTTP Code”, “HTTP Description”.   – we can report more redable



Creating an automatic lookup – use lookup automatically instead of using lookup commands

Settings -> lookups -> automatic lookups -> create new
Select destination app – search
Name – http_status_lookup
Select lookup table – http_status_lookup
Choose what data to apply the automatic lookup for
Apply to sourcetype -> Named = access_combined
Lookup input fields code(look up) = status(from sourcetype)

Multiple fields can be used

Lookup output field
code = Code
description = Description

click save button

return list of automatic lokkups is returned

you can see the new automatic look up you have created -> have look up command 


in seach now, we don’t need look up commands

Index=web sourcetype=access_combined NOT status=200
| table host,”HTTP Code”, “HTTP Description”.   – we can report more redable


Additional lookup options – populate lookup table with search results, instead of using file.

Define lookup based on external script or command

Use splunk db connect application – to create lookups based on external databases.

Use geospatial lookups to create queries that can be used to generate choropleth map visualizations

Populate events with kv store fields


Schedule reports – is a report that runs on a scheduled interval and can trigger an action each time it runs.
Weekly or monthly report, dashboard and automatically sending reports via email

Creating schedule reports 

-	First you need to create the search, save as   repots
Give name title
You can add time range picker to report – is schedule so not need time range

After save -> select schedule options

Edit schedule window open – 
Select schedule report –
Schedule – select frequence of time to send report and time

Time range – relative schedule – over the last 7 days

Running concurrent reports and the searches behind them, can put a big demand on your system hardware. Even if everything is configured to the recommended specs

-	(admin) So you can set schedule priority and set a schedule window(if there are some another report in the same time and date, you can set the minutes ) to run it


Include a schedule window only if the report doesn’t have to start at specific time and you are ok with the delay.

Setting the schedule windows to auto will splunk to automatically determine the best time window in which to run the report.

You can choose what actions(add actions button) when a scheduled report is run. Log event, output results to lookup, output result to telemetry endpoint, run a script, send wemail and webhook. Or you can install or build custom alert actions depending or your user role. Admin can manage and add prebuild alert actions(manage actions).

Send email – to whom, priority, subject, message. -> save

Managing scheduled reports –

Settings – searches, reports and alerts

You can see table of your report and next scheduled time
Clicking name of report – we get quick access to change the search string and time range
Edit actions -> edit search, permission, schedule, acceleration, summary indexing. Disable, clone, embed,move and delete.


Also you can enter reports - In the search -> report tab

Clicking name of report, display search result

Edit button -> open in search, edit description,permissions, schedule,acceleration.   Clone, embed delete

Make this report available to folks at buttercup games but do not have acces to the splunk instance -> use embed -> enable embedding -> cautions ->anyon with access to the web page will be able to see the report. We have code for iframe(you can use in any html page). Done click

An embedded report will not show data until the scheduled search is run. Once embedding is enabled. You are no longer be able to edit attributes for the report
Add a schedule report to a dashboard -> add to dashboard


Alerts – based on searches that run on a scheduled interval or in real-time

Alert notify you when the results of a search meet defined conditions

Alerts are triggered once the search is completed

Alerts can be – list in interface, log events, output to lookup, send to a telemetry endpoint, trigger scripts, send emails, use a webhook and run a custom alert.

Creating alerts –
First define the search
-	Save as alert
Enter title
Permissions – private(only you can access, view and edit alert), shared in app( the results will be displayed for all users of the app). By default everyone has read acess, power users have write access to the alert. There are 2 alerts type, schedule(allows you to set a schedule and time range for the search to be run)(you can use predefined time range or use cron expression) or real-time(will run the search continuously in the background, as soon as alert conditions are satisfied an action is triggered).

Real time alerts – run continuously and can place more overhead on system performance

(trigger conditions)
Trigger alert when – per-result, number of results, number of hosts, number of sources, custom(using splunk search language)

Number of results
Is greated than 1
In 5 minutes. (interval)

Trigger setting -> once or for each result

Throttle -> how ofter the alert is executed

Trigger actions -> add actions -> add to triggered alerts(add severity of the alert), log event(are sent your splunk deployment for indexing), output results to lookup(create or update csv lookup table) , output results to telemetry endpoint, run a script(execute script or bash – this action is officially deprecated and we suggest using a custom alert action(in manage actions) instead), send email,  web hook(allow you to define custom callbacks on a particular web resource -> set up a webhook to make an alert message pop up in a chat room or create a ticket in a support app ).

Admin clicking manage actions find pre built actions -> you can build your own.

View and edit alerts –

In activity -> triggered alerts – to see what alerts have triggered

In this table we can view results, edit search or delete

Or
Settings -> searches, reports and alerts

Or in the search -> alerts tab







Reuse you data in everywhere


Investigate tool – real time base

Schema on the fly – schema on the read - 

Splunk cloud for cloud


Work on on premise, cloud, sass

Splunk forwarders – collect data from wire data, api, skd, http, tcp/udp, rdbms ,containers, cloud services

Splunk indexers- where the data lives – scalable
-	Splunk search heads – scalable – to search


Machine data is complex but valuable

App and add ons – extends splunk functionality – dashboards, rerpots, alertrs, visualizations and workflows

Addons focus specific related data ingestion or configurations.




eval – allows you to calculate and manipulate filed values In your report – calculate and manipulate

developer options – sdk and rest api of splunk
you can create you app or adds-on 






