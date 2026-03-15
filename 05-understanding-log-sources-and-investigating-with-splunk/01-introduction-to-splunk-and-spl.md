
# Introduction To Splunk & SPL

## What Splunk Is (my understanding)

Splunk is basically a log analysis platform that can:

- ingest logs
- index them
- search them
- visualize them

In SOC environments it's used as a **SIEM**.

So instead of manually checking logs on one machine, we can query logs across the entire network.

## Important Architecture Components

From the module:

- Forwarders (collect logs)
- Indexers (store logs)
- Search Head (where analysts query data)

This made it clearer how logs actually flow inside a SIEM.

## SPL Basics

Some commands I used a lot:

### Basic Search

index="main"

This means search inside the **main index**.

### Filtering

index="main" EventCode=1

Find process creation events.

### Useful Commands

table → display fields

stats → aggregate data

dedup → remove duplicates

sort → sort results

eval → create fields

rex → extract data using regex

lookup → compare values with external lists

## One Thing I Realized

The biggest skill is **knowing what to search for**.

Anyone can run queries but if you don't understand attacker behavior you won't know what to hunt.
