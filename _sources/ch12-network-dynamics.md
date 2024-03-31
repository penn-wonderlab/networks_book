# Network Dynamics and Temporality

> It's About Time!

So far in this class we've been mostly working with `static` networks or `snapshots` of dynamic networks. That's enough for most of our needs. 

However, many networks are dynamic in nature. One important use of network analysis is to understand how a network would function -- and evolve -- given its current structure. Such a question is genuinely about network dynamics.

In this week, we will:

- Explore ways to conceptual temporality in SNA (and network analysis in general)
- Learn how to construct temporal networks
- Learn approaches to visualizing and analyzing temporal networks
- Explore potential applications of temporal SNA to our projects

**Note**: You may see people using different words *temporal*, *dynamic*,  *longitudinal* interchangeably to describe social networks.

## Getting started with network dynamics

### Why temporality in networks matters?

Watch a video below (also [link here](https://www.coursera.org/learn/model-thinking/lecture/1qEBU/schellings-segregation-model)) about the **Schelling's -@schelling1969models Segregation Model** to understand the importance of understanding network dynamics. 

<video controls width="100%">
<source src="https://d18ky98rnyall9.cloudfront.net/L2B_Cropped.6e7e92c0648e11e4b597fd570fa7692c/full/360p/index.webm?Expires=1617148800&Signature=DP8hgwGfqDmn48OguTM38Wh~8IJh9Q971i75h9EFJh2~rn0DtQgcRpYkT00AP5ndtvS4mxyfcxXU3DCY4BLVPcJ6w8hHCm3NA00bMaWrd5b3cXxF3pbKahPhDZGYAlUJXdqxrsB7FKeusCY6FrZV~QwOzGwFkkl6nWhksVhwOxw_&Key-Pair-Id=APKAJLTNE6QMUY6HBC5A" type="video/webm">
<source src="https://d18ky98rnyall9.cloudfront.net/L2B_Cropped.6e7e92c0648e11e4b597fd570fa7692c/full/360p/index.webm?Expires=1617148800&Signature=DP8hgwGfqDmn48OguTM38Wh~8IJh9Q971i75h9EFJh2~rn0DtQgcRpYkT00AP5ndtvS4mxyfcxXU3DCY4BLVPcJ6w8hHCm3NA00bMaWrd5b3cXxF3pbKahPhDZGYAlUJXdqxrsB7FKeusCY6FrZV~QwOzGwFkkl6nWhksVhwOxw_&Key-Pair-Id=APKAJLTNE6QMUY6HBC5A" type="video/mp4">
</video>



To further explore the Schelling's Segregation Model:

1. Open http://nifty.stanford.edu/2014/mccown-schelling-model-segregation/
2. Adjust Similarity threshold to 50% --> Record rounds
3. Adjust Similarity threshold to 75% --> Record rounds

How is the model related to network dynamics? 

<img src="images/schelling.gif" width="480px" />

### Approaches to considering time in networks

Temporal information is reflected in networks in several ways:

- Timestamp of an event (when)
- Duration of an event (how long)
- Frequency of of events (how often)
- Time-order / contingency of events (in which temporal order)

There are multiple ways to consider temporal information in network analysis:

**1. Time‐aggregated networks**

Consider email correspondences among members of an organization. Each week, members of the organization send each other emails. Each email has a timestamp and is directed from one member to one or several members. To generate *time‐aggregated networks*, one subsets the full record of email exchanges at different start and stop time points and retain any interactions that begin or stop within the window. One straightforward example is to create aggregate email interactions by week and create weekly aggregated networks. By doing so, one can then compare time-aggregated networks across weeks. 

A slightly more complex example of time-aggregated networks is to apply a *sliding window* on the dataset. To get a sense of how it works, click on the 'Play' button of the interactive visualization below. The slider/window will begin to slide rightward, while the window size remains constant. Each snappost you see is a time-aggregated network within its corresponding window. 

<iframe src="assets/file70664c4ffc8d.html" style="width:100%; height:400px;"></iframe>

The sliding window approach can be further enriched. According to @gloor2004temporal, instead of strictly restricting to events within a time window, you can choose to incorporate information about previous events to each time window. This technique is akin to adding a memory to the time-aggregated networks. 

<img src="assets/gloor-2004-fig1.png" width="80%"/>

<img src="assets/gloor-2004-fig2.png" width="80%"/>


**2. Time‐ordered networks**

According to @blonder2012temporal, "Time‐ordered networks represent data observed for a set of interactions that occur at certain times, thereby retaining complete information on the ordering, duration and timing of events." 

This approach retains more detailed temporal information and can be used to answer various questions about flow dynamics. You will have a chance to read more in @blonder2012temporal this week (see below).


**3. SNA measures with 'a temporal flavor'**

SNA concepts and measures we have explored so far can be extended to temporal networks. 

See the following example from @mascolo2013temporal. If it is a static network (the lower-right corner), the shortest path between `A` and `G` is `[A, B, D, E, G]`. When we consider the temporal network (see the time-sliced network above), A needs to go through `C` at time 2 in order to reach `G`; at time 3, the direct path between `E` and `G` is no longer available and `E` needs to go through `F` to reach `G`. As a result, the temporal shorted path between `A` and `G` becomes `[A, C, B, D, E, F, G]`. 

This is just one example concept that requires reconsideration in temporal networks. 

![](assets/Mascolo-2013.png)


### Tools for temporal network analysis

In Python, the `[networkx-temporal](https://pypi.org/project/networkx-temporal/)` package extends NetworkX functions for dynamic/temporal networks. 

If interested, please seek relevant tutorials and learn to work with temporal networks by yourself.

In R, there are a number of packages, such as `networkDynamic`, `tsna`, and `ndtv`, which are very useful for temporal network analysis and visualization. 

If you are interested, check out this amazing tutorial about [Temporal Network Analysis with R](https://programminghistorian.org/en/lessons/temporal-network-analysis-with-r).

In addition, novel social network analysis methods such as relational event modeling (REM) are powerful for analyzing moment-to-moment event data. You will learn more about REM in this week's readings. 


## Readings

1. Stehlé, J., Voirin, N., Barrat, A., Cattuto, C., Isella, L., Pinton, J.-F., Quaggiotto, M., Broeck, W. V. den, Régis, C., Lina, B., & Vanhems, P. (2011). High-Resolution Measurements of Face-to-Face Contact Patterns in a Primary School. PLOS ONE, 6(8), e23176. https://doi.org/10.1371/journal.pone.0023176
2. Pilny, A., Schecter, A., Poole, M. S., & Contractor, N. (2016). An illustration of the relational event model to analyze group interaction processes. Group Dynamics: Theory, Research, and Practice, 20(3), 181–195. https://doi.org/10.1037/gdn0000042

