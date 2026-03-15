
# Introduction to Threat Hunting

## What I Think Threat Hunting Is

Threat hunting is basically a proactive approach to security. Instead of waiting for alerts from tools like SIEM or EDR, analysts go out and **actively search for suspicious behavior** inside logs.

One big reason threat hunting exists is because attackers can stay inside a network for weeks or even months before being detected (this is called *dwell time*). fileciteturn2file0

So the whole goal is to reduce that dwell time by finding attackers earlier in the kill chain.

## My Thought Process While Reading

At first I thought threat hunting was just running queries in a SIEM.

But the more I read the more I realized it's actually:

1. Using threat intelligence
2. Creating hypotheses
3. Searching logs to confirm or reject them

It's more investigative than just monitoring dashboards.

## Things I Learned

- Threat hunting is **proactive**, not reactive.
- It relies heavily on **logs and threat intel**.
- Analysts often use **Elastic, Splunk, or other SIEM tools** to perform hunts.
