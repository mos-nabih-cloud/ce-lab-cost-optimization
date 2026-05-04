# Cost Optimization Plan

## Current state
- ~$27/month projected
- 3 instances (2 running, 1 stopped), 4 volumes (1 unattached)
- 100 GB volume sitting unused

## Optimizations

1. Delete the unattached 100 GB volume
   - vol-0995c274445241bba
   - Saves $8/month

2. Terminate the stopped instance
   - i-039c39ae5101fd302
   - Saves the 8 GB EBS = ~$0.64/month

3. Stop instances when I'm not using them (nights/weekends)
   - I really only use these ~40 hrs/week, not 168
   - Could cut compute cost roughly in half

## Priority

- delete unattached volume
- terminate stopped instance

## Projected savings

Before: ~$27/month
After deleting volume + terminating stopped instance: ~$18/month
If I also stop instances at night: ~$12/month

That's around 55% saved.
Annual: ~$180/year
