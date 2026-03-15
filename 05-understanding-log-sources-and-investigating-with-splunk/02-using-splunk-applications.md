
# Using Splunk Applications

In this section we used the **Sysmon App for Splunk**.

These apps basically add dashboards, queries, and detection logic.

## Installing Sysmon App

Steps:

1. Create account on Splunkbase
2. Download Sysmon App
3. Upload app to Splunk
4. Configure macros

After that the dashboards started working.

## Fixing the Dashboard

There was an issue where the dashboard wasn't showing results.

Problem:

The dashboard was using the field **Computer** but Sysmon logs actually use **ComputerName**.

So the search needed to be edited.

After changing the field everything worked.

## Lab Question 1

Fix the search for the **Net - net view** report.

Answer:

net view /DOMAIN:uniwaldo.local

## Lab Question 2

Find how many network connections SharpHound.exe initiated.

Query used:

sysmon EventCode=3 Image="*SharpHound.exe" | stats count

Answer:

6

## What I Learned

Splunk apps are basically **prebuilt detection tools**.

But they still require tuning because the data fields might not always match.
