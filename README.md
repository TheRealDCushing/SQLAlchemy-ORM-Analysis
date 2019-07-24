### Explanation of my approach to completing the first section

We begin with a sqlite database that contains a few tables of specific interest. For this first part, we want to get information from the Measurement table from the 'date' and 'prcp' columns. First, we a datetime module to create an object that has the specific date we want to use as a reference. (I used an sqlite DB browser to find out what the relevant date would be.) Then, we use SQL alchemy to query this database, and filter by referencing that date.

The output for our SQL alchemy query is in list format, with each item containing two pieces of separate information that we want to parse. Thankfully (because of automap), each piece retains its 'date' and 'prcp' identifying tags. So, I use a loop that appends each side of the combined list structure we've created into separate lists (to make sure it's coming out right, I print every 500 results). Then, I mash the two lists together into a dictionary. Finally, I use pd.DataFrame() to turn our new dict into a dataframe, from which I can create the first plot.

Since there are multiple stations per day, it is necessary to use some sort of method to converge the information by day. I used sum() because it produced a result identical to the objective, but it would actually make more sense to take a median value.

Once a plot object is created, it can be modified with MatPlotLib even though the plot was not created using MatPlotLib.

### Explanation of my approach to completing the second section

Next I was interested in different information. I used SQL Alchemy queries to find out how many stations are in the Station datatable, and how active each station is (from how many rows are provided for each station). I filtered the dataset, only considering the most active station, and then I went through the same process as before to create two separate lists (via a for-loop), a dictionary, and then a dataframe I could use to plot the results.
