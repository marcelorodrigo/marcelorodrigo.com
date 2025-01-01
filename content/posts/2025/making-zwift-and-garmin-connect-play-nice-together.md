---
author: "Marcelo Rodrigo"
categories:
  - Coisas da Vida
date: 2025-01-01T13:30:23+01:00
description: 'Making Zwift and Garmin Connect play nice together: A Manual but Rewarding Approach for metrics like Training Status, Vo2Max and Intensity Minutes synchronized.'
draft: false
keywords:
  - Bike
  - Zwift
  - Garmin
tags:
  - Bike
title: 'Making Zwift and Garmin Connect play nice together'
type: post
---

# Making Zwift and Garmin Connect play nice together

## The Problem
As an indoor cyclist using Zwift, I have discovered that the direct integration between Zwift and Garmin Connect isn't always perfect. While Zwift does an excellent job of making indoor cycling engaging, the workout data doesn't always translate well into Garmin Connect. Critical metrics like Training Status, VO2 Max, and Intensity Minutes often end up missing or incorrectly calculated.

To help on the issue, Garmin deliberately decided to not update metrics if you are not using a Garmin device to record your traning. While it makes sense from a vendor perspective, it does not help when you use Zwift, which is agnostic to which brand of trainer or smart bike you are using.

## The Experiement
Some users have reported that the missing metrics can be easily captured if you have a Garmin watch. The approach is to run the Garmin watch in parallel with Zwift, but discard the activity you started on your watch. This way, you trigger Garmin to closely monitor your heartbeat and other metrics in the background.

While this doesn't completely solve the problem, it can help you track your heart rate, SpO2, and other metrics more accurately and achieve better monitoring of your training and health condition.

## The Solution
After some experimentation, I found a solution that, while manual, ensures all my training metrics are properly captured in Garmin Connect.

First, I disabled the automatic integration between Zwift and Garmin Connect. This avoid the issue we faced above, where workouts that aren't recorded using Gardmin devices to compute metrics. Instead, I now handle the data transfer manually, with a trick!

After each ride, I visit the Zwift website to download the FIT file of my workout. This file contains all the raw data from my workout. The next step involves visiting fitfiletools.com, where I use their device conversion tool. Here's where the magic happens - I modify the file to appear as if it came from a Garmin device. In my case, I've had success using the Garmin Tacx Neo 2 as the device type.

Finally, I upload the modified FIT file directly to Garmin Connect.
The result? All my metrics are properly calculated, giving me a complete picture of my training progress.

## The Summary
- Disable Zwift integration with Garmin
- Record your workout normally using Zwift
- Download the FIT file from your workout on Zwift
- Change to a Garmin device using the _Device Changer_ option from [FitFileTools](https://www.fitfiletools.com)
- Update the modified FIT file to Garmin Connect

## The Outcome

While this workflow requires more effort than an automatic sync, I've come to appreciate the manual process. It gives me a moment to reflect on my ride and develop a deeper connection with my training data. That said, it would be wonderful if Garmin could enhance their integration with Zwift to make this manual process unnecessary.

For now, though, this approach ensures I maintain consistent, accurate training metrics across both platforms. It's a small price to pay for having reliable data to track my fitness progress.

And many thanks to [Kevin Flanagan](https://www.fitfiletools.com/#/about) for developing the functionality at FitFileTools.