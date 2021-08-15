# Introduction to Splunk
+ Splunk is described as a solution to aggregate, analyze and extract valuable infomration of machine data from any source. 

+ Splunk can be used for **Application Management**, **Operations Management**, **Security** & **Compliance**.


+ When it comes to security, Splunk can be used as a log management soultion. Splunk can enhance investigations of dynamic, multi-step attacks with detailed visualizations and even enhance an organization's detection capabilities through User Behavior Analytics. 

+ Splunk can swallow any data from almost any source, through both an agent-less and a forwarder approach.


![[data_type.png]]


#### Splunk Architecture Overview

![[architecture.png]]

Splunk architectures consist of:
+ **Forwarder** component:
	+ **Universal Forwarders**: collect data from remote sources and send them to one or more Splunk Indexers. They are separate downloads that can be installed on any source, less impact on network or host performance.


	+ **Heavy Forwarders**: also collect data from remote sources, but they are typically used for heavy data aggregation tasks, from sources like firewalls or data routing/filtering passing points. According to Splexicon, heavy forwarders parse data beforce forwarding them and can route data based on criteria such as source or type of event. They can also index data locally while forwarding the data to another indexer. Heavy Forwarders are usually run as **data collection nodes** for **API/scripted** data access, and they are only compatible with **Splunk Enterprise**.


	+ **Universal Forwarders** is mainly used for small amount of data? while **Heavy Forwarders** is good for large amount of data that requires heavy filtering?

*Note*: **HTTP Event Collector** (**HECs**) also exists to collect data directly from applications, at-scale, through a token-based JSON or raw API way.


+ **Indexer** component
	+ The Indexer **processes machine data**, storing the results in indexes as events, enabling fast search and analysis. As the indexer indexes data, it creates a number of files organized in sets of directories by age. Each directory contains raw data (compressed) and indexes (points to the raw data).



+ **Seach Head** component
	+ The **Seach Head** component allows users to use the Seach language to search for indexed data. It distributes user search requests to the Indexers and consolidates the results as well as extracts field value pairs from the vents to the users. Knowledge Objects on the Seach Head can be created to extract additional fields and transform the data without changing the underlying index data. It should be noted that Seach Head also provide tools to enhace the search experience such as reports, dashboards, and visualizations.


#### Splunk Apps and Technology Add-ons (TAs)

+ **Splunk Apps** are designed to address a wide variety of use cases and to extend the power of Splunk. Essentially, they are collections of files containing data inputs, UI elements, and/or knowledge objects. Splunk Apps also allow multiple workspaces for difference use cases/user roles to co-exist on a single Splunk instance.


	+ Apps are available at **Splunkbase**.


+ Splunk Technology Add-ons abstract the collection methodology and they are typically include relevant field extractions. They also include relevant config files (props/transforms) and ancillary scripts binaries.


#### Splunk Users and Roles
+ Splunk users are assigned roles which determine their capabilities and data access. There are three main roles:
	+ **admin**: This role has the most capabilities assigned to it.
	+ **power**: This role can edit all shared objects (saved searches, etc) and alerts, tag events, and other similar tasks.
	+ **user**: This role can create and edit its own saved searches, run searches, edit its own references, create and edit event types. and other similar tasks.


#### Splunk's Search and Reporting App
+ Navigation

![[navigation1.png]]

![[navigation2.png]]

+ **Data Summary** will summary data of hosts, sources or sourcetypes.

![[navigation3.png]]

+ This is how the **Events** might look like.

![[navigation4.png]]



###### **Splunk's  Search Processing Language (SPL)**:
+ SPL combines the best capabilities of SQL with the Unix pipeline syntax that allows you to:
	+ Access all data in its original format.
	+ Optimize for time-series events.
	+ Use the same language for visualizations.

SPL provides over 140 commands that allow user to search, correlate, analyze and visualize any data.

Example of SPL:

![[SPL_syntax.png]]

Searches are created based of **five main components**:
1. **Search term**: where you specify what you are looking for. Search terms contain keywords, phrases, Booleans, etc.


2. **Command**: where you specify how you want to manipulate the result. For example, create a visualization, chart or statistic, etc...


3. **Functions**: where you specify how exactly do you want to chart, compute or evaluate the results.


4. **Arguments**: in case there are variables you want to apply to a function.

5. **Clauses**: where you specify how exactly you want to group or rename the fields in the results. 

As you notice, there are some search string are automatically colored. The color is based on the synxtax. As the following image:

![[SPL_syntax2.png]]

Something else to consider while submitting searches is Splunk's search modes.

There are three main search modes:

+ **Fast Mode**: Field discovery off for event searches. No event or field data for stats searches.

+ **Smart Mode**: Field discovery on for event searches. No event or field data for stats searches. (recommended* for beginner)

+ **Verbose Mode**: All event & field data.