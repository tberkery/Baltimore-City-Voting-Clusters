# Baltimore-City-Voting-Clusters
Applying a cluster analysis to data from the 2016 Presidential (General) Election for Baltimore City. Observing how precincts can be grouped based on number of Republicans, number of Democrats, and voter turnout rate.

# Data Source
The dataset behind this analysis is from the [Baltimore City Government Website](https://elections.maryland.gov/elections/2016/index.html). Specifically, it is the dataset titled "Statewide by Party and Precinct (CSV)" on that webpage. The Excel workbook version of this dataset in this GitHub repository can be accessed [here](https://github.com/tberkery/Baltimore-City-Voting-Clusters/blob/main/Raw%20Data:%20Official%20by%20Party%20and%20Precinct).

# Statement of Background
The 2016 Election involved the same candidates across every precinct and Baltimore and every precinct nationwide. However, the specific dynamics of the election varied quite a bit across different precincts. Precincts, which combine to form a district and tend to span part or all of a neighborhood, each have different numbers of registered Republicans, different numbers of registered Democrats, and different voter turnout rates. This largely  makes sense: different neighborhoods tend to have people of different upbringings, backgrounds, socioeconomic status, and priorities, all of which play a role in political preferences and likelihood to be involved in the political process. Thus, as a means of comparing the similarity of the dynamics of the 2016 election in a given precinct to other Baltimore City precincts, a cluster analysis will of residents' party affiliations and degree of involvement in elections will be performed.

# Business Question
How can we group Baltimore City precincts into clusters based on party affiliation, population, and voter turnout using data from the 2016 presidential election?

# Results, Visuals, and Tying It All Together
For context, consider the following map of Baltimore precincts. The goal here is not to fixate on what precinct is where but rather to understand the approximate composition of precincts and how precincts come in all shapes and sizes.

**Map of Baltimore City Precincts**
![alt text](https://github.com/tberkery/Baltimore-City-Voting-Clusters/blob/main/Visual%20of%20Baltimore%20City%20Precincts.jpg)
Background diagram courtesy of [Baltimore City Government Website](http://boe.baltimorecity.gov/sites/default/files/CouncilDistricts_WardsPrecincts_tabloid-2012_1.pdf).

With these precincts as context, using a three cluster analysis, the three clusters are as follows (colored in in the prior visualization):

Precinct 006-005 = blue = east of the Inner Harbor = near McElderly Park/Linwood

Precinct 006-001 = green = east of the Inner Harbor = near McElderly Park/Linwood

Precinct 013-002 = purple = slightly north and west of Johns Hopkins University = Hampden

It's particularly interesting to note that two cluster anchors are immediately adjacent districts the border each other. It's also even more interesting to note that Route 40 (Pulaski Highway) runs right down the border between these two precincts. This supports the frequently observed phenomenon of highways separating two parts of a city that would otherwise have been connected disparate.

When it comes to the characteristics of each cluster, the first cluster (Precinct 006-005) appears to be highly populated (it has more of both democrats and republicans than average) and to have above average voter turnout. From an elections perspective, a district that has lots of people on both sides that gets a higher-than-average amount to turn out is likely a desirable outcome. From the perspective of people taking charge of the politicians who represent them, this cluster is largely the gold standard. Other precincts closely aligned with this cluster include the Inner Harbor and Downtown Baltimore.

The second cluster (precinct 006-001) is characterized by having both less democrats and replubicans than average (indicating a lower-than-average amount of party-affiliated voters) and lower-than-average voter turnout rates. This is an area that activists of both parties would likely seek out with the goal of encouraging increased involvement with elections. Other precincts closely aligned with this cluster include Harwood and Abel (two neighborhoods not too far east of Hopkins).

Lastly, the third cluster (precinct 013-002) is characterized by having fewer Democrats than average and more Republicans than average along with a higher-than-average voter turnout rate. This corresponds to the Hampden neighborhood, and other neighborhoods closely aligned with this cluster include Fells Point. The neighborhoods included in this third cluster tend to be among Baltimore's more affluent and developed neighborhoods. Considering nationwide demographic trends, it isn't surprising to see that this cluster is characterized by increased support of Republican candidates and increased voter turnout.

So, in relation to the overall business question, when grouping Baltimore City precincts into three clusters by party affiliation, population, and voter turnout, the clusters basically take the following forms: (1) high number of party-registered individuals and a high voter turnout rate, (2) a low number of party-registered individuals and a low voter turnout rate, and (3) high number of Republicans and high turnout rate.

**Map of Baltimore City Precincts Colored by Cluster**
![alt text](https://github.com/tberkery/Baltimore-City-Voting-Clusters/blob/main/Baltimore%20Clusters%20Map.jpg)
Background diagram courtesy of [Baltimore City Government Website](http://boe.baltimorecity.gov/sites/default/files/CouncilDistricts_WardsPrecincts_tabloid-2012_1.pdf).

This visual shows which anchor cluster every Baltimore City precinct maps to, with blue mapping to the first cluster, green to the second, and purple to the third. While there is naturally a lot of variety, there are some patterns. 

The second cluster (low amounts of registered Democrats and Republicans and low voter turnout) characterizes the majority of the western and eastern parts of central Baltimore and nearly all o fBaltimore surrounding and south of Interstate 95. With some exceptions, these areas tend to be less economically advantaged. This cluster analysis suggests that there is reason to believe there may be a relationship between economic resources and election participation. For example, perhaps precincts falling into the second cluster have low numbers of registered Democrats and Republicans and low voter turnout because these neighborhoods tend to be disadvantaged economically and lack the work flexibility or transportation to make it to the polls on eleciton day. Exploring these factors further by incorporating them into the cluster analysis would make it possible to better understand the underlying reasons behind the number of party-affiliated individuals for the Democrat and Republican parties and what truly drives voter turnout.

Moreover, this visual shows that very metropolitan, trendy areas like the Inner Harbor, Fells Point, and Hampden tend to have higher-than-average numbers of Republicans and higher-than-average voter turnout. Given that this is largely the oppposite of the areas of the first cluster indicated in green in terms of skewing towards people with lots of economic resources, this similarly provides evidence that there may be a strong relationship between economic resources and election participation.

Lastly, we have the areas in blue corresponding to the first cluster, which are more sporadic with the exception of frequently occurring in Northern Baltimore. It's harder to generalize and see a clear pattern for these areas, but they correspond to the desirable outcome of lots of Republicans and Democrats and higher-than-average voter turnout (i.e. higher-than-average election participation).

When it comes to future research, I think it would make sense to include additional measures of economic equality, access to resources and transportation, and the demographics reflecting the diversity (or lack thereof) of each precinct. This would make it possible to delve deeper than generalizations and top-level knowledge of the Baltimore community when exploring the underlying reasons for the voting patterns unveiled in this cluster analysis.

# Instructions for Replicating Analysis
[See instructions here.](https://github.com/tberkery/Baltimore-City-Voting-Clusters/blob/main/Instructions%20for%20Replicating%20Analysis.pdf)
