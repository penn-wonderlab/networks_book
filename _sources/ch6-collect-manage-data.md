# Collect and Manage Network Data

## Readings

- Scott, J. (2017). Social network analysis (4th edition) (Ch. 3-4). SAGE Publications.

## Understanding SNA Data

Blankly speaking, data collection in SNA research is concerned with two types of data: (1) **relational data** that describe *ties*, and (2) **attribute data** that describe *nodes*. 

For example, if I want to study friendship in a high school class, depending on my research questions I may choose to collect attribute data of each student (such as gender, race, GPA), and relational data of every possible pair of students (such as whether Student A texts Student B, or how many times A texts B). Quite simple, right?

However, real-world SNA projects in education demand a number of critical decisions to be made by the researcher. Just to list a few examples:

- how to gain access to the research "field" (e.g., a student fraternity, an intimate parent group)
- from whom are data collected (and who are excluded from data collection)
- which instruments are used for data collection
- how are data structured and stored
- how to transform data to different "shapes" to address specific research questions

This week's readings offer detailed suggestions on network data collection. Below I briefly comment on **a few key points**, before engaging you in detailed techniques in later sections.

### Sources of SNA data

SNA data may be obtained in a variety of ways---from historical archives, questionnaires, ethnographic studies, system logs of online platforms, Medicaid claims, etc. For example, from public records researchers could analyze *co-sponsorship of legislation* in the U.S. Senate {cite}`brandenberger2018trading`; from a classic Chinese novel, *[Dream of the Red Chamber](https://en.wikipedia.org/wiki/Dream_of_the_Red_Chamber)*, researchers could use SNA to estimate relationships between characters based on their co-occurrence. In these two cases, we can see that in SNA research some *relational data* are **natural** or readily available (e.g., co-sponsoring of a legislature), while some other need to be **derived** (e.g., relationship between novel characters based on the co-occurrence of names in a same sentence). 

No matter how relational data get gathered or derived, I want to emphasize the importance of **making sound justification** on the collection/creation of relational data. For example, I reviewed a manuscript that analyzed "co-location networks" based on students' simultaneous access to wifi hotspots on a university campus. As a critical reviewer, I would pay special attention to any strong claims made on "social" connections among students, because accessing a same wifi hotspot does not imply any social interaction. However, if the study looks at pairs of students simultaneously accessing 10 hotspots on the campus every day, it would become a totally different story as such intense co-location could be an indicator of (potential) social ties. Therefore, in SNA studies we need to constantly reflect on the **contextual definition(s)** of *ties* and the **operationalization of the definitions** in data collection.

### Totality and sampling

In some cases, we are able to collect a **whole** social network. Imagine [the year-long NASA simulation of a Mars mission in an isolated dome](https://www.theguardian.com/science/2016/aug/28/mars-scientists-nasa-dome-hawaii-mountain-isolation), researchers would have a better chance of studying the social network of all six scientists in its totality.[^1] In other cases, when it becomes impossible to study a whole network (e.g., terrorist networks), researchers will need to apply specific techniques of **sampling**.

[^1]: Whether researchers can investigate a phenomenon in its totality is a philosophical question. But if we focus on highly specified questions (e.g., whether scientists cooperate in an experiment), we can argue the phenomenon is observable and the likelihood of studying this phenomenon in its totality is very high.

**Sampling in SNA research is different from sampling we commonly discuss** in an introductory research methods course. This is because SNA research is concerned with both the *nodes* and the *ties*. Simply put, a representative sample of nodes does not naturally guarantee a meaningful sample of ties. SNA researchers need to be especially aware of the impact of sampling on relational data. For example, in a study we may *systematically sample* every 5th student from a school based on student IDs (sampling applied on nodes), and we may also ask each student to name up to 3 friends in this school (sampling applied on ties). 

Ego-network also implies an interesting sampling mechanism, as it cares about a focal ego and the nodes to whom the ego is directly connected to plus the ties. This could be intuitively understood by sampling based on *distance* from the ego.

How we sample nodes and/or ties depends on how we **specify the boundaries of networks**. The definition of network boundaries is highly critical for any SNA research and requires systematic considerations on research questions, theoretical perspectives, availability of data, etc. To quote {cite}`scott2012social`:

> ... the determination of network boundaries is not simply a matter of identifying the apparently natural or obvious boundaries of the situation under investigation. Although 'natural' boundaries may, indeed, exist, **the determination of boundaries in a research project is the outcome of a theoretically informed decision** about what is significant in the situation under investigation... Researchers are involved in a process of conceptual elaboration and model building, not a simple process of collecting pre-formed data (pp. 44-45)

This important recognition speaks back to my Week 1 video on the importance of **learning to make decisions** in such a research methodology class. Defining the boundaries of networks is certainly the most central decision for an SNA project. When we start to inspect these decisions, it may looks like we're opening **"a can of worms"**, as many decisions may look artificial, or slippery at best. In this class, I hope we see decision points as **"a bag of diamonds"**---each worth inspecting from different angles.[^2]

[^2]: I enjoy the analogy I'm making here :)

## Ethics in SNA research

Ethical considerations are important for both research and practice. You've already rightfully brought up this topic in prior discussions. We won't spent much time on this topic this week, but I want to encourage you to attend to ethical concerns in your specific research contexts. Does your research involve venerable populations (e.g., young children)? Does your research involve sensitive data (e.g., health data)? Is your research field online or offline? Because SNA is applied in all kinds of educational or organizational settings, it is almost impossible to come up with a unified ethics guideline. **I strongly encourage you to skim this [chapter from an Open Textbook](https://open.lib.umn.edu/principlesmanagement/chapter/9-5-ethical-considerations-with-social-network-analysis/)** produced by the UMN Libraries. What are the possible ethical concerns in your project? I encourage you to start taking notes on how you could address them.

I also want to mention that research ethics is never a static topic at all. In many emerging research spaces (e.g., social media), research ethics remains highly debatable {cite}`rivers2014ethical,kraut2004psychological`. 


## Managing SNA data

In this section, I introduce recommended ways of structuring and handling SNA data. Here I especially consider principles of **tidy data** {cite}`wickham2014tidy`, which may question things you encounter elsewhere. The principles of tidy data are very simple (p. 4), and I will explain each principle below with examples.

1. Each variable forms a column.
2. Each observation forms a row.
3. Each type of observational unit forms a table.

### Basic representations

Note that SNA data typically include **attribute data** about nodes and **relational data** about edges. So the most straightforward way to represent a network is to have two separate tables. 

For example, consider a student group with four students (**nodes**). Table 1 contains attribute data of each student. This table is *tidy* because each variable form a column, each observation (i.e., student) form a row, and it contains a single observational unit `student`. 
<!-- The third principle gets violated, for example, if you add students' yearly `test score` -- another observational unit -- into this table. -->

Table 1. A table of nodes.

| name | gender | age |
|:-----|:-------|:----|
| A    | F      | 15  |
| B    | M      | 14  |
| C    | M      | 13  |
| D    | F      | 14  |


Table 2 describes book lending activities (**ties**) among students. For example, Row 1 means Student A lent one book to B, while Row 4 shows B lent 2 books to C. It is also a tidy dataset.

Table 2. A table of weighted ties

| source | target | weight |
|:-----|:---|:-------|
| A    | B  | 1      |
| A    | C  | 0      |
| A    | D  | 0      |
| B    | C  | 2      |
| B    | D  | 1      |
| C    | D  | 0      |



Note that *weight* is not always required for networks. In a study that only cares about the existence of a tie, Column 3 will contain only 0 and 1. Or, rows with having a value of 0 in Column 3 will be simply removed from this table.

Table 3 could be the original record from which Table 2 is constructed. In Table 3, each row represents a book lending action, with its date recorded in Column 3. Here, you get a sense how researchers may need to **transform** data from its original observations (Table 3) to a specific format (Table 2), even though most SNA software can handle both formats.

Table 3. A table of raw data of ties.

| source | target | date |
|:-----|:---|:-------|
| A    | B  | 2017-02-03 |
| A    | C  | 2017-02-04 |
| A    | D  | 2017-02-05 |
| B    | C  | 2017-02-06 |
| B    | D  | 2017-02-07 |
| C    | D  | 2017-02-08 |
| B    | C  | 2017-02-09 |


Additionally, in situations you do not care about **node attributes** (in Table 1), you can simply only use relational data -- only about edges -- to construct a network. In this case, you will only have a table of relational data, which already contain the most basic information (identifiers) of nodes. Take Table 2 for example, all unique node identifers in columns `source` and `target` will be extracted to create a list of nodes, with no further information about their attributes.

### Two-mode data

Imagine the research project is actually more complicated: We are also interested in the relationship between book-lending behaviors and student affiliations with sports teams. In this case, you may have two additional tables below. 

Table 4. Sports teams in the school.

| sports_teams | pratice_day |
|:-------------|:-----------:|
| baseball     | Tue         |
| basketball   | Mon         |
| volleyball   | Fri         |

Table 5. Student affiliation with sports teams.

| student | team    |
|:-----|:-----------|
| A    | basketball |
| A    | volleyball |
| B    | baseball   |
| C    | basketball |
| D    | baseball   |
| D    | volleyball |


Like what I just mentioned, you could ignore Table 4 if Table 5 already contains all information about sports teams. But if there is a football team not covered by Table 5, you will need to include Table 6 as well.

Table 6. Sports teams in the school (version 2).

| sports_teams | pratice_day |
|:-------------|:-----------:|
| baseball     | Tue         |
| basketball   | Mon         |
| volleyball   | Fri         |
| football     | Wed         |


Using Table 5, you could construct a **two-mode network** -- also called as an affiliation network -- with students and sports teams as two types of *actors* in the network. In contrast, Table 2 only has one mode -- students. 

Finally, if your research project is concerned with friendship in general -- which covers both book lending and sports affiliation -- you could even merge two types of relational data together (with solid justification). For example, from Table 5 we can tell A and C are both in the basketball team. We can then adjust the weight between A and B in Table 2 accordingly. This is another type of **transformation** you may need to do in SNA research. Knowing basic data transformation techniques -- either in spreadsheet software or in R -- would be helpful for work in this class.

To summarize, this section provides a basic overview of how SNA data could be structured. You may encounter different ways of representing SNA data, such as a relationship matrix with rows and columns representing the same set of actors (see [the Harry Potter support networks](http://www.stats.ox.ac.uk/~snijders/siena/HarryPotterData.html) for example). Such representations could all be derived from a *tidy* dataset discussed above. In data collection, we will strive for keeping as much raw information as possible (such as timestamp), to enable analyses that only come to your mind afterwards.
