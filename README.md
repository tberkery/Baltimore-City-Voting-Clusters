# Baltimore-City-Voting-Clusters
Applying a cluster analysis to data from the 2016 Presidential (General) Election for Baltimore City. Observing how precincts can be grouped based on number of Republicans, number of Democrats, and voter turnout rate.

# Data Source
The dataset behind this analysis is from the [Baltimore City Government Website](https://elections.maryland.gov/elections/2016/index.html). Specifically, it is the dataset titled "Statewide by Party and Precinct (CSV)" on that webpage. The Excel workbook version of this dataset in this GitHub repository can be accessed [here](https://github.com/tberkery/Baltimore-City-Voting-Clusters/blob/main/Raw%20Data:%20Official%20by%20Party%20and%20Precinct).

# Statement of Background

# Business Question
How can we group Baltimore City precincts into clusters based on party affiliation, population, and voter turnout using data from the 2016 presidential election?

# Results and Visuals
Using a three cluster analysis, the three clusters are as follows:

Precinct 006-005 = blue = east of the Inner Harbor = near McElderly Park/Linwood

Precinct 006-001 = green = east of the Inner Harbor = near McElderly Park/Linwood

Precinct 013-002 = purple = slightly north and west of Johns Hopkins University = Hampden

![alt text](https://github.com/tberkery/Baltimore-City-Voting-Clusters/blob/main/Visual%20of%20Baltimore%20City%20Precincts.jpg)
Background diagram courtesy of [Baltimore City Government Website](http://boe.baltimorecity.gov/sites/default/files/CouncilDistricts_WardsPrecincts_tabloid-2012_1.pdf).

It's particularly interesting to note that two cluster anchors are immediately adjacent districts the border each other. It's also even more interesting to note that Route 40 (Pulaski Highway) runs right down the border between these two precincts. This supports the frequently observed phenomenon of highways separating two parts of a city that would otherwise have been connected disparate.

When it comes to the characteristics of each cluster, the first cluster (Precinct 006-005) appears to be highly populated (it has more of both democrats and republicans than average) and to have above average voter turnout. From an elections perspective, a district that has lots of people on both sides that gets a higher-than-average amount to turn out is likely a desirable outcome. Other precincts closely aligned with this cluster include the Inner Harbor and Downtown Baltimore.

The second cluster (precinct 006-001) is characterized by having both less democrats and replubicans than average (indicating a lower-than-average amount of party-affiliated voters) and lower-than-average voter turnout rates. This is an area that activists of both parties would likely seek out with the goal of encouraging increased involvement with elections. Other precincts closely aligned with this cluster include Harwood and Abel (two neighborhoods not too far east of Hopkins).

Lastly, the third cluster (precinct 013-002) is characterized by having fewer Democrats than average and more Republicans than average along with a higher-than-average voter turnout rate. This corresponds to the Hampden neighborhood, and other neighborhoods closely aligned with this cluster include Fells Point. The neighborhoods included in this third cluster tend to be among Baltimore's more affluent and developed neighborhoods. Considering nationwide demographic trends, it isn't surprising to see that this cluster is characterized by increased support of Republican candidates and increased voter turnout.

# Instructions for Replicating Analysis
1. Download the data titled “Statewide by Party and Precinct (CSV)” from https://elections.maryland.gov/elections/2016/index.html. Save it as an Excel workbook (.xlsx).
1. Apply several filters to the data by going to data and then filter. Filter the column titled LBE such that it only includes “Baltimore City.” Filter by “PRECICNT” to skip any records where the precinct is listed as “unable to be determined.” By filtering on “ELIGIBILE VOTERS,” remove any records for which there are less than 10 eligible voters. Copy all data that is still showing after these filters have been applied into a new worksheet titled “Filtered Data.”
1. In “Filtered Data,” add a column titled “Precinct-Party Key,” which will serve as a lookup key indicating a precinct and the party affiliation of a given group of voters. Do this by concatenating the value of the “PRECINCT” column with an underscore and the value of the party column, with one caveat: if the content of the “Party” column is not “DEMOCRAT” or “REPUBLICAN” concatenate the underscore with “OTHER”. The formula should look something like the following: “=CONCATENATE(D2, "_",IF(OR(E2="DEMOCRAT", E2="REPUBLICAN"), E2, "OTHER"))”
1. Create a PIVOT table out of the Filtered Data workbook (which now includes the Precinct-Party Key column). Set Precinct-Party key to be a row and sum of “ELIGIBLE_VOTERS” and sum of “Count of Voters” to be the columns in the PIVOT table. 
1. Create a new worksheet called “Lookup.” Copy and paste the entire precinct column from the initial dataset download (the worksheet titled “Official by Party and Precinct”). Highlight what you just pasted and navigate to data and then the remove duplicates button which looks like three cells in a column where the top and bottom cells are blue and there is a red x in the right corner. Remove duplicate values.
1. In the subsequent columns of “Lookup” to the right of the “Precinct” column, use either VLOOKUP or a combination of MATCH and INDEX to lookup the following quantities from the Pivot table you created in step 4 for each precinct: number of eligible Democrat voters, number of Democrat voters, number of eligible Republican voters, number of Republican voters, number of eligible Other voters, and number of Other voters. Concatenate the value of the precinct column with an underscore and either “DEMOCRAT,” “REPUBLICAN,” or “OTHER” depending on the column. This formula should look something like the following: “=INDEX('Voters by Party and Precinct'!$A$3:$C$877, MATCH(CONCATENATE($A2, "_DEMOCRAT"), 'Voters by Party and Precinct'!$A$3:$A$877, 0), 2)”
1. Create two columns titled “Overall number of eligible voters” and “Overall number of voters” by summing the appropriate column for each of the party categorizations (DEMOCRAT, REPUBLICAN, and OTHER). Create a new column called Overall Voter Turnout.
1. Copy the Precinct column, number of eligible Democrats column, number of eligible Republicans column, and Overall Voter Turnout column into a clean worksheet and prepare to perform a cluster analysis.
1. Insert two rows at the top of the pile that contain the mean and sample standard deviation of the number of eligible Democrats, number of eligible Republicans, and Overall Voter Turnout rate.
1. Insert a column to the left of the precinct code that will serve as the cluster number. Using the STANDARDIZE function, compute z-scores for the number of eligible Democrats, number of eligible Republicans, and Overall Voter Turnout rate.
1. Arbitrarily choose 3 precinct numbers that will serve as our three initial cluster anchors. List their cluster numbers above the data and one column to the left of the first column containing z-scores. Two cells above the topmost cluster number, type the label “Column.” For the three cells to the right of this cell, put the integer number corresponding to the index number of that column. For example, since column F is the sixth column in the workbook, the cell in column F should be 6 (the cell in column G would be 7 and so on).
1. Define the data from the Cluster Number column to the rightmost z-score column to be the named range named “Precinct_Cluster_stats.”
1. Use VLOOKUP in the cells immediately to the left of the cluster numbers discussed in step 11 to lookup the precinct code associated with the given cluster number. Your formula should look something like: “=VLOOKUP(E5, Precinct_Cluster_Stats, 2)”
1. Use VLOOKUP in the set of 3x3 cells immediately to the right of the cluster numbers discussed in step 11 to lookup the z-scores for the clusters that have been specified as anchors. Your formula should look something like the following (note the dollar signs): “=VLOOKUP($E5, Precinct_Cluster_Stats, F$3)”
1. In the normal data set below the data for the anchor clusters, compute the square distance of each precinct in the data from each of the anchor clusters. Use the SUMXMY2 function and the cells containing the z-scores for the three anchor clusters you produced in the previous step. For the leftmost column of square distances, the formula should look something like this: “=SUMXMY2($F9:$H9, $F$5:$H$5).” Every time you move a column to the right, increase the number indicating the row in the second parameter by 1.
1. Insert a column to the right of the rightmost distance column titled “Minimum Square Distance.” Utilize the MIN function to take the minimum of the square distances from the anchor clusters that you calculated in the prior three cells immediately to the left.
1. Above the Minimum Distance column header, compute the sum of the minimum square distances. The formula should look something like the following: “=MIN(I9:K9)”
1. Create a column to the right of the “Minimum Square Distance” column and title it “Assigned to”.  The formula should mirror the following construction: =MATCH(L9, I9:K9, 0). This formula basically identifies which anchor cluster the current cluster was closest to in terms of squared distance.
1. Go to the data tab and select solver (assuming it is already installed). Configure you solver’s settings as shown in the following screenshot. Also, select “Options,” “Evolutionary,” and set the mutation rate to 0.5. The key is that the cell currently represented as “$L$6” in the screenshot is the sum of minimum square distances and the cells currently represented as “$E$5:$E$7” in the screenshot correspond to the cluster numbers created in step 11. Note that we restrict the value of these cells to being an integer between 1 (our lowest cluster number) and 287 (our highest cluster number).
![alt text](https://github.com/tberkery/Baltimore-City-Voting-Clusters/blob/main/Solver%20Specifications%20Screenshot.png)
