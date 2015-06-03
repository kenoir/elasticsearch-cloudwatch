elasticsearch-cloudwatch
========================

This is an Elasticsearch plugin which posts ES stats to CloudWatch.

# Generating the installable plugin

To generate the plugin for installation you need to use maven:

    $ mvn clean package

# Installing the plugin

Install it from the Elasticsearch installation directory, by running (change the location of your file):

    $ bin/plugin -url kenoir/elasticsearch-cloudwatch -install CloudwatchPlugin

To uninstall it you can run:

    $ bin/plugin -remove CloudwatchPlugin

# Configuring the plugin

The plugin has some options that you can configure in the elasticsearch.yml:

  - **metrics.cloudwatch.enabled**: To enable or disable the plugin itself. True by default.
  - **metrics.cloudwatch.aws.region**: Which region to use, of the AWS account. Default is eu-west-1 
  - **metrics.cloudwatch.frequency**: How often to post stats. Default is "1m", every minute.
  - **metrics.cloudwatch.index_stats_enabled**: To enable or disable stats per index. You don't want the explosion of metrics if you have too many indexes, such as for example with Logstash where there is an index per day. False by default.
  - **metrics.cloudwatch metrics.cloudwatch.namespace**: To set the cloudwatch namespace of the metric. 

## AWS Credentials
  
  - **metrics.cloudwatch.aws.access_key**
  - **metrics.cloudwatch.aws.secret_key**

If these keys aren't set, the plugin will attempt to use system properties, environment variables and IAM role credentials if available.  

# Acknowledgements

This plugin is forked from https://github.com/9apps/elasticsearch-cloudwatch
