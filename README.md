Time Series Insights Hands on Lab - Guide
-----------------------------------------

Azure Time Series Insights (TSI) is an end-to-end PaaS offering to ingest, process, store, and query highly contextualized, time-series-optimized, IoT-scale data. Time Series Insights is tailored towards the unique needs of industrial IoT deployments with capabilities including multi-layered storage, time series modeling, and cost-effective queries over decades of data. Time Series Insights provides rich asset-based operational intelligence together with ad-hoc data exploration to address the IoT analytics needs.

(This assumes that a TSI instance, IoTHub, and PnPDevice sending data have already been configured...)

**Step 1: Create an Azure Time Series Insights Preview environment**

* Sign-in to the Azure portal by using your subscription account.
* Select Create a resource > Internet of Things > Time Series Insights.

[]media/search-the-marketplace.png)

* In the Create Time Series Insights environment pane, on the Basics tab, set the following parameters:

**Parameter**|**Action**
:-----:|:-----:
Environment name|Enter a unique name for the Azure Time Series Insights Preview environment.
Subscription|Enter the subscription where you want to create the Azure Time Series Insights Preview environment. A best practice is to use the same subscription as the rest of the IoT resources created during the lab.
Resource group|Select an existing resource group or create a new resource group for the Azure Time Series Insights Preview environment resource.
Location|Select a datacenter region for your Azure Time Series Insights Preview environment. To avoid additional latency, it's best to create your Azure Time Series Insights Preview environment in the same region as your IoT Hub created previously.
Tier|Select PAYG (pay-as-you-go). This is the SKU for the Azure Time Series Insights Preview product.
Property ID|Enter a value that uniquely identifies your time series instance. The value you enter in the Property ID box is immutable. You can't change it later. For this lab, enter iothub-connection-device-id. To learn more about Time Series ID, see [Best practices for choosing a Time Series ID](https://docs.microsoft.com/en-us/azure/time-series-insights/time-series-insights-update-how-to-id).

**Step ToDo X: Explore data in your TSI Environment**

In this section, you will explore data in your new environment via the Azure Time Series Insights Preview explorer before moving on to an environment with a larger historical data-set

1.  The TSI explorer is a compliemenatry application that ships with your TSI environment. Navigate to your explorer by selecting the URL
    from the resource page in the [Azure portal](https://portal.azure.com/).

ToDo image![](media/15b6dddd4a3b1ce452b106dd2211b1f1.png)

2.  Wait for the environment to load in the browser. Once it loads, you'll be on the default landing page. Some of the key features include:

Selecting a time range: You can select a different time range by dragging the __ ToDo of the availability picker, or using the date-time picker above. Any time selection that is within the orange bar boundary will query your Time Series Insights environment's warm store. Warm storage is configurable for upto 31 days retention and is designed for frequent querying of recent data. There is no charge for these queries. 

Plotting: In the middle of the page is the charting pane, after charting time series you'll see those instances appear in the well below with additional settings, which will be explored in a future step. 

Hierachy: On the left, you'll see the Time Series Model (TSM) hierachy, expand “Time Series Instances” to see all the time series in the environment.

ToDo image

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







