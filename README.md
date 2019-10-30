Time Series Insights Hands on Lab - Guide
-----------------------------------------

Azure Time Series Insights (TSI) is an end-to-end PaaS offering to ingest, process, store, and query highly contextualized, time-series-optimized, IoT-scale data. Time Series Insights is tailored towards the unique needs of industrial IoT deployments with capabilities including multi-layered storage, time series modeling, and cost-effective queries over decades of data. Time Series Insights provides rich asset-based operational intelligence together with ad-hoc data exploration to address the IoT analytics needs.

(This assumes that a TSI instance, IoTHub, and PnPDevice sending data have already been configured...)

**Step 1: Create an Azure Time Series Insights Preview environment**

1. Sign-in to the Azure portal by using your subscription account.
2. Select Create a resource > Internet of Things > Time Series Insights.

[Search the market place](media/search-the-marketplace.png)

3. In the Create Time Series Insights environment pane, on the Basics tab, set the following parameters:

**Parameter**|**Action**
-----|-----
Environment name|Enter a unique name for the Azure Time Series Insights Preview environment.
Subscription|Enter the subscription where you want to create the Azure Time Series Insights Preview environment. A best practice is to use the same subscription as the rest of the IoT resources that are created by the device simulator.
Resource group|Select an existing resource group or create a new resource group for the Azure Time Series Insights Preview environment resource. A resource group is a container for Azure resources. A best practice is to use the same resource group as the other IoT resources that are created by the device simulator.
Location|Select a datacenter region for your Azure Time Series Insights Preview environment. To avoid additional latency, it's best to create your Azure Time Series Insights Preview environment in the same region as your IoT Hub created by the device simulator.
Tier|Select PAYG (pay-as-you-go). This is the SKU for the Azure Time Series Insights Preview product.
Property ID|Enter a value that uniquely identifies your time series instance. The value you enter in the Property ID box is immutable. You can't change it later. For this tutorial, enter iothub-connection-device-id. To learn more about Time Series ID, see Best practices for choosing a Time Series ID.
Storage account name|Enter a globally unique name for a new storage account.
Enable Warm Store?|Select Yes to enable warm store.
Data Retention (days)|Choose the default option of 7 days

4. Click on “Next: Event Source” in this section we will establish a connection between our existing hub and TSI:

**Parameter**|**Action**
-----|-----
Create an event source?|Select Yes.
Name|Enter a unique value for the event source name.
Source type|Select IoT Hub.
Select a hub|Choose Select existing.
Subscription|Select the subscription that you're using for the lab.
IoT Hub name|Select the IoT Hub that was created in a previous step.
IoT Hub access policy|Select iothubowner.
IoT Hub consumer group|Select New, enter a unique name, and then select Add. The consumer group must be a unique value in Azure Time Series Insights Preview.
Timestamp property|This value is used to identify the Timestamp property in your incoming telemetry data. Leave this box empty. When left empty, Time Series Insights will default to the message enqueued timestamp set by IoT Hub or Event Hub. This is sufficient for the lab.

[Create an environment](media/createTsiEnvironment.png)

5. Click on “Review + create”

[Review and create](media/review-and-create.png)

6. Click “Create”

7. Once your deployment is complete, navigate to your new Time Series Insights resource in the Azure portal. You should have access to your environment by default. To verify, select "Data Access Policies" under "Settings." If you do not see your credentials listed, grant yourself access by clicking "Add" and searching for your identity.

[Verify access](media/verify-accesss.png)

**Step 2: Explore data in your TSI Environment**

In this section, you will explore data in your new environment via the Azure Time Series Insights Preview explorer.

1. On the "Overview" pane you'll see the link to your TSI explorer:

[Overview pane](media/overview-pane.png)

2.  Wait for the environment to load in the browser. Once it loads, you'll be on the default landing page. Some of the key features include:

Selecting a time range: You can select a different time range by dragging the handles of the availability picker, or using the date-time selector in the top right corner. Any time selection that is within the orange bar boundary will query your Time Series Insights environment's warm store. Warm storage is configurable for upto 31 days retention, and is designed for frequent querying of recent data. There is no charge for these queries. 

Plotting: In the middle of the page is the charting pane, after charting time series, you'll see the time series event values in the chart and the instances will appear in the well below with additional settings, which we will explore in a future step.

Hierachy: On the left, you'll see the Time Series Model (TSM) hierachy, expand “Time Series Instances” to see all the time series in the environment.

3. Click on the first time series ToDO “device1” and then click on “Show humidity”. You will see a time series chart to the right. EventCount, humidity, messageId and temperature are the default variables created in the environment. Step __ ToDo will demostrate further analysis using the charting pane. 

ToDo image

Step ToDo: Contextualize and Analyze data

In the previous section, you explored raw data without contextualization. In this section, you will add time series model entities to contextualize your IoT data.
Time Series Model (preview) has 3 components: Types, Hierarchies and Instances.
Types allow users to define calculations and aggregates over raw telemetry data and specify a tag for the sensor (example: Temperature sensor, Pressure sensor). In this lab you will use the ‘default type’ that performs a count operation.
Hierarchies allow users to specify the structure of their assets. For example, an organization has buildings and buildings have rooms which contain IoT devices. The hierarchy structure in this case will be (Building -> Room).
Instances enrich incoming IoT data with device metadata. An instance links to 1 type definition and multiple hierarchy definitions.

1. In the upper left part of the explorer select the Model tab:

ToDo image

2. Type ToDo --variables

3. The next step is to add a hierarchy. In the Hierarchies section, select + Add
ToDo image

4. Tab will open on the right-hand side. Add the following values:
ToDo image -- table
ToDo image

5. Click “Create” at the bottom
You will see a hierarchy created:
ToDo image

6. Next, click on “Instances” and click on ToDo “device 1”. To edit this Instance, click on “Edit”

ToDo image

7. On the Right-Hand Side, enter the following fields
ToDo image -- table
ToDo image







