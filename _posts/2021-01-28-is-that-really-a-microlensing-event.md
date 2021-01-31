---
title:  "Is that really a predicted microlensing event?"
date:   2021-01-28 10:18:00
description: Break down of my recent paper
draft: false
---

This post briefly summarises my most recent paper, which can be found on the arxiv [here](https://arxiv.org/abs/2006.13958). This study was completed in collaboration with Andrew Everall, [Douglas Boubert](https://www.douglasboubert.com), and Leigh Smith.

![](http://astrophpeter.github.io/assets/images/flawed_abstract.jpeg)
*Paper title and abstract*

Gaia DR2 astrometry has allowed the prediction of alignments of stars to such great precision that we can actually predict when a gravitational lensing event will happen. In some cases, these events provide unique opportunities to extract gravitational masses of the lens.

Gaia DR2 reignited interest in trying to predict these alignments and has led to ~ 5700 predicted events occurring over the next century by many different studies.
The question we investigate is - Can all these predictions be trusted?

Firstly,  it's worth mentioning that the vast majority of predictions by all studies with maximums far into the future are fine. We tried to get to the bottom of some puzzling characteristics of events that Gaia would hopefully observe! 

The story begins with the predicted event caused by the lens G123-61A. Here is a DSS2 image of the field around the event. You can see the lens (square) heading towards the background source (circle), and some unrelated DR2 sources (triangles).

![](http://astrophpeter.github.io/assets/images/flawed_no_source.jpeg)
*A predicted microlensing event with no source*

Gaia G-band magnitudes are annotated text. But where is the 13th mag background source? This missing source also happens to be the background source for another predicted event! Turns out Gaia detected what is likely a binary component of the lens (G123-61B) and they both align with the missing background source causing separate events.

Here is a 2MASS image of the same field. Both the positions of G123-61A (square) and G123-61B (triangle) at the image epoch (2000.0) and the DR2 reference epoch (2015.5) are marked. The missing source (circle) is sandwiched between G123-61A & B at the Gaia reference epoch.

![](http://astrophpeter.github.io/assets/images/flawed_no_source_two.jpeg)
*A predicted microlensing event with no source*

The source also has a very similar magnitude and colour to the lens G123-61A. The number of times this system should have been observed with Gaia is ~ 65. That is, G123-61A,  G123-61B, and the background source should all have (~65) detections. However, the number of detections are G123-61A (54), G123-61B (42), and the background source (34). It's no coincidence that 54 + 42 + 34 = 130 (2x65) - the total number of detections we would expect for just the binary lens system!

We suspect this was a very rare and difficult case for the clustering algorithm used to assign detections to different sources. In this case, it looks like some of the detections of the binary lens system were donated to make a likely spurious third source.

We found some more examples of predicted events where the source appears to be missing so we decided to investigate. Here are plots of the source-lens magnitude and colour difference as a function Psi (~ measure of how “noisy” the astrometry of the source is).

![](http://astrophpeter.github.io/assets/images/flawed_noise.jpeg)
*Noise in the astrometric solution*

We can see that the vast majority of events are fine, with the background source in these cases generally having a more "noisy" astrometric solution if it is fainter. However, we can see a cluster of events where the source and lens have very similar magnitudes and colour, and in these cases, the sources have very "noisy" astrometry for their magnitude.

The vertical line in the plot is one of the thresholds Gaia uses to give a source either 5D or 2D astrometry. The cluster of suspicious events all have very bright sources where the astrometry was noisy enough to not give the source 5D astrometry.

We recommend only considering events if the background source has 5D astrometry for events with background sources brighter than G=18. While there are only some events in this cluster, these happen to be the best events for detection with Gaia. This is because the source appears to be quite bright, which is crucial for Gaia to obtain a precise measurement of the lensing signal.

This recommendation eliminates 61% of the predicted events forecast to happen over the Gaia mission with bright sources, including some of the best candidates where we would expect to get precise mass measurements of the lens. Requiring that the background source has 5D astrometry also remedies another puzzling aspect of the predicted events. Here is a plot of the distribution of the time of the closest approach for the events.

![](http://astrophpeter.github.io/assets/images/flawed_time_of_closest_approach_distribution.jpeg)
*Distribution of time of closest approach*

We’d expect the rate of events to be constant with a dip around the DR2 reference epoch (2015.5) where the lens and source were too close for Gaia to resolve them, so the event could not be predicted. But we can see from the plot the rate peaks either side of 2015.5 (Grey). 

If we apply our cut (blue), this gets rid of these sharp peaks. Excitingly this implies that ~ half the predictable microlensing events which Gaia will detect have yet to be identified! These events may be found in the later Gaia data releases. We suspect that in many of the cases of the events we eliminate, the background source is likely to be just a marginal detection of a binary component of the lens and a case like G123-61 is very rare!

Finally, it goes without saying that all the Gaia data is amazing, and the vast majority of microlensing predictions made with it are fine. We found out you have to be **really** careful when you’re trying to predict microlensing events near to the Gaia reference epoch!

This work made lots of use of Douglas and Andy’s Completeness of Gaia-verse project work which you can check out [here](https://gaiaverse.space/home). Also huge thanks to the Gaia Help desk, who really helped us understand all of this.
