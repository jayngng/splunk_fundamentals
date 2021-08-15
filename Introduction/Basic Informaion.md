# Effectively Using Splunk (Scenario 1)

## LAB 8

# Scenario

The organization you work for (**Wayne Enterprises**) is using [Splunk](https://www.splunk.com/) as a SIEM solution to enhance its intrusion detection capabilities. The SOC manager informed you that the organization has been hit by an APT group. He tasked you with responding to this incident by heavily utilizing Splunk and all the data that it ingested.

The data that Splunk has ingested consist of Windows event logs, Sysmon logs, Fortinet next-generation firewall logs, Suricata logs, etc.

**Note**: This lab is based on the [Boss Of The SOC (BOTS) v1 dataset](https://github.com/splunk/botsv1) released by Splunk. Credits to [Ryan Kovar](https://twitter.com/meansec), [Dave Herrald](https://twitter.com/daveherrald?lang=el) and [John Stoner](https://twitter.com/stonerpsu) for sharing the Splunk detection tips this lab covers with the public, through this dataset.

# Learning Objectives

The learning objective of this lab is to not only get familiar with Splunk's architecture and detection capabilities but also to learn effective Splunk search writing.

Specifically, you will learn how to use Splunk's capabilities in order to:

-   Have better visibility over a network
    
-   Respond to incidents timely and effectively
    
-   Proactively hunt for threats