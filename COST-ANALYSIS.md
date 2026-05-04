# Cost Analysis

## What I have running

EC2 instances:
- i-06b2eec2e571a16df  t3.micro  running
- i-06947685a9b7a94d0  t3.micro  running
- i-039c39ae5101fd302  t3.micro  stopped

EBS volumes:
- vol-0995c274445241bba  100 GB  gp3  available (not attached!)
- vol-0bad55a7646956492  8 GB    gp3  in-use
- vol-0b682af5a24934095  8 GB    gp3  in-use
- vol-0f58e88300580845b  8 GB    gp3  in-use

## Current weekly cost (rough math)

2 running t3.micro × 168 hrs × $0.0104 = $3.49
Stopped instance still keeps its 8 GB EBS = $0.64/month
Attached volumes: 3 × 8 GB × $0.08 = $1.92/month
Unattached 100 GB volume: 100 × $0.08 = $8.00/month  (big waste) 

Week 2 total: ~$4.25
Monthly projection: ~$27 (the unattached volume bumps this up)

## Where the money is going

Biggest waste is the 100 GB unattached gp3 volume sitting there doing nothing = $8/month.
Second waste is the stopped instance still hanging onto its EBS volume.
The two running t3.micros are fine for what I'm doing this week.
