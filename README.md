# TamperCheck
This was a job task automated using Python. I'll post a summary of the project on here for those who want to follow this:

Workflow (#build 0.1 - 2.5)

The algorithm summary:
#Build 0.1 - 1.8
1. Load the dataset.
2. Prepare the dataset by selecting only columns necessary for analysis, then other minor things (e.g split function).
3. Compare the location arrived at to the next location departed from (n to n+1) <initially, I wanted to go an n to n-1 route, comparing backwards... since we're using a program, I thought why not just go straight anyway... makes no difference>
4. If locations are the same, go on.
5. Else? Compare their correpsonding coordinates (latitutde and logitude columns) by plugging into googlemaps API.
6. googlemaps API returns the distance along the route. (Replaced with OSMR in build 2.5)
7. If the distance returned is greater than 10.9, flag the two trips (that's the two concerned rows of data) and make a count.
This is what I achieved in this first build.

#Build 2.0:
8. Return a list which reports: The total number of tampering instances; details of individual tampering cases with the row index for manual confirmation of accuracy. (#build 0.2 - 1.0)
9. Returns an Excel workbook with two sheets. First sheet is the original dataset with the cases of tampering highlighted. Second sheet is a summary of tampering report showing for each asset: The total number of tampering instance; the sum_total of tampering_distances; the sum_total of recorded distance for that asset over that period. (#build 1.2 - 1.8)
10. Getting the program to create a summary report giving: (a) The tamper frequency (b) The sum of distances tampered (c) the total distance that asset travelled in the period we're considering <there's a distance column> (d) a percentage comparison of distance tampered against total recorded travel distance for asset. [As at #build 2.0: DONE]
11. There's a corresponding report which is basically a modified version of the original dataset. This one just contains only trucks with flagged tampering. Their full period trip report is there, but the flagged trips are highlighted. [As at #build 2.0: DONE]

#Build 2.0 Updates:
1. I have used Geopy as a placeholder instead of Googlemaps API (or OpenStreetMaps) to calculate distances and hence complete the rest of the program. This would be my next step, implementing the API to get route distances instead of 'as the crow flies'
2. I have updated the workflow to include the creation of excel report files. So the summary of the program processing is: input the data file, get one report file with two sheets.
3. Generally, I have also streamlined the coding to be more easy to follow for now. I'm adding comments for you to get a better picture of what's going on.

#Build 2.5 Updates:
1. I have implmented the route distance checking feature with OpenStreetMap's OSMR (OSMnx didn't work, dm for details or I'll explain later... was too conky a solution for the scale I'm working with).
