# cribl-splunk-license-util-dashboard
Dashboard to monitor both Cribl and Splunk license consumption

----

# LogStream License Metrics Dashboard
Presenting the License Metrics Dashboard!

### This Tutorial will Cover
- Sending Cribl Logs/Metrics to Splunk
- Creating a Cribl Metrics Index in Splunk
- Installing and using the Splunk Dashboard

### Prerequisites
- Your Cribl LogStream instance
- Your Splunk deployment
- Ability to Create Indexes and Dashboards

### Source Files:
- Splunk [`Dashboard`](https://link-to-license-example.com).
- Original Cribl LogStream Metrics app [`on Splunkbase`](https://splunkbase.splunk.com/app/5339/).

# Start Here
### Configure Splunk
1. Create a Splunk Index for logstream_metrics (Index Data Type = Metrics)
3. Create a NEW "Classic" Dashboard
4. Click Edit > Source > Paste in the Dashboard
### Configure Cribl LogStream
1. Set up your Sources in Cribl (Data > Sources > Cribl Internal)
2. Activate your Metrics Source
3. Set up you Splunk Destination in LogStream (Data > Destinations > Splunk)
### Modify and Create Routes
1. Edit the PreProcessing Route. ( Routes > cribl_metrics_rollup)
2. Add the required fields below using the supplied Eval function

- __inputId==‘cribl:CriblMetrics’
- criblMetrics[0].dims : […criblMetrics[0].dims,'index']
- index : ‘logstream_metrics’
- sourcetype : ‘cribl_metrics’

### Create a Metrics Route
1. Enable a Route for Cribl Metrics

- Route Name: CriblMetrics
- Filter: __inputId=='cribl:CriblMetrics'
- Pipeline: passthru
- Output: “your splunk output”

# You are done!!!
