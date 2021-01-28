---
title:  "Is that really a predicted microlensing event?"
date:   2021-01-28 10:18:00
description: Break down of my recent paper
draft: true
---

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

[](http://astrophpeter.github.io/assets/images/flawed_no_source_two.jpeg)
*A predicted microlensing event with no source*

The source also has a very similar magnitude and colour to the lens G123-61A. The number of times this system should have been observed with Gaia is ~ 65. That is, G123-61A,  G123-61B, and the background source should all have (~65) detections. However, the number of detections are G123-61A (54), G123-61B (42), and the background source (34). It's no coincidence that 54 + 42 + 34 = 130 (2x65) - the total number of detections we would expect for just the binary lens system!

We suspect this was a very rare and difficult case for the clustering algorithm used to assign detections to different sources. In this case, it looks like some of the detections of the binary lens system were donated to make a likely spurious third source.
