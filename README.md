# Blitz_1

# Purpose:

Load testing the Python URL Shortening application (from [deployment 3](https://github.com/kaedmond24/python_url_shortener_app_deployment_3)) on AWS Elastic Beanstalk. 

Blitz 1 uses Apache JMeter to flood the python URL shortening application with requests (1000 requests total). This process informs us on how well the application and infrastructure would perform under heavy traffic.  

# Overview:
1.  What happened during the blitz?

- The blitz started with verifying that the python url shortening application was up, running, and accessible. Deployed on an EC2 instance, the Apache JMeter application was configured to send 1000 simultaneous requests to the URL shortening app’s URL. During this time the applications latency was being monitored to observe the impact of the requests. Both the URL shortening app and Apache JMeter app were running on infrastructure located in the AWS US East 1 region. This information should be taken into account when reviewing due to the close proximity of the applications. Once the test finished running, a latency time of approximately 40ms was recorded for the URL shortening app. Prior to the test the application's latency was measured at approximately 9ms. 

2. What did you do to resolve the issue?

- The latency experienced during the load test was not ideal for handling an increase in user traffic. In order to reduce overall latency to the URL shortener application a CDN should be implemented. A CDN (content delivery network) delivers performance enhancements by reducing latency to web applications. These enhancements are done by having static and some dynamic content distributed and cached to edge servers (data centers) geographically dispersed. [AWS CloudFront](https://aws.amazon.com/cloudfront/) service was configured as CDN for the URL shortening app. Once configured, AWS CloudFront produced a new URL to access the application; providing low-latency access to cached content. Another Apache JMeter load test with the same parameters was run against the new URL for the application. The latency to the URL shortening app using AWS CloudFront was measured at approximately 8.50ms under the test load.  

3. What was the purpose?

- The purpose of this load testing scenario was to determine how the python URL shortening application would perform under heavy request load. Providing a baseline metric for the applications latency then stress testing that metric allowed us to optimize the applications infrastructure. Vital data was provided that drove a decision to implement additional infrastructure resources in the form of a CDN. 

