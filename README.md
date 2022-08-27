# Election_Analysis

## Overview of Election Audit
The purpose of this election analysis audit was to use Python script to easily extract the following pieces of information:
- The names of each county that the votes came from 
- The names of each candidate that were voted for
- The total count and percentage of votes for each county and which county had the greatest number of votes
- The total count and percentage of votes for each candidate 
- Lastly, the candidate with the greatest number of votes to help us determine the winner of the popular vote for this eelection 


## Election Audit Results
The analysis of the election show that:
- There were 369,711 total votes in the congressional election. We got this by first intializing the vote counter to be zero:
```
# Initialize a total vote counter.
total_votes = 0
```
And then by using the following code that allowed us to skip the header row of the csv to ensure it was not included in the vote count: 
```
    # For each row in the CSV file.
    for row in reader:

        # Add to the total vote count
        total_votes = total_votes + 1
```

- The counties, percentage of and total number of votes were:
  - Jefferson: 10.5% (38,855)
  - Denver: 82.8% (306,055)
  - Arapahoe: 6.7% (24,801)

From this we can see that Denver county had the largest share of votes in this election 

To find the above results we used a for loop:
```
 # Write a for loop to get the county from the county dictionary.
    for county_name in county_votes:
        # 6b: Retrieve the county vote count.
        countyvotes = county_votes[county_name]
        # 6c: Calculate the percentage of votes for the county.
        county_vote_percentage = float(countyvotes) / float(total_votes) * 100

         #  Print the county results to the terminal.
        county_results = (f"{county_name}: {county_vote_percentage:.1f}% ({countyvotes:,})\n")
        print(county_results)
         # 6e: Save the county votes to a text file.
        txt_file.write(county_results)

         #  Write an if statement to determine the winning county and get its vote count.
        if (countyvotes > largest_county_count) and (county_vote_percentage > largest_turnout_percentage):
            largest_county_count = countyvotes
            largest_turnout_percentage = county_vote_percentage
            largest_county = county_name
```
And then printed the results into our election analysis txt fiel

- The candidates, percentage of and total number of votes were:
  - Charles Casper Stockham: 23.0% (85,213)
  - Diana DeGette: 73.8% (272,892)
  - Raymon Anthony Doane: 3.1% (11,606)

From these results we can see that the candidate Diana DeGette won the popular vote in this election with 272,892 votes and 73.8% of the total votes

To get these results we used almost identical code as the one we used for counties but counted by candidate instead. The code was written as:
```
    # Save the final candidate vote count to the text file.
    for candidate_name in candidate_votes:

        # Retrieve vote count and percentage
        votes = candidate_votes.get(candidate_name)
        vote_percentage = float(votes) / float(total_votes) * 100
        candidate_results = (
            f"{candidate_name}: {vote_percentage:.1f}% ({votes:,})\n")

        # Print each candidate's voter count and percentage to the
        # terminal.
        print(candidate_results)
        #  Save the candidate results to our text file.
        txt_file.write(candidate_results)

        # Determine winning vote count, winning percentage, and candidate.
        if (votes > winning_count) and (vote_percentage > winning_percentage):
            winning_count = votes
            winning_candidate = candidate_name
            winning_percentage = vote_percentage
```

Printing all the code detailed above we were able to output the election results in easy to understand text file, which is pictured below:

![image description or alt text](https://raw.githubusercontent.com/charlotterotner/Election_Analysis_Final/main/Deliverable%202.png)


## Election Audit Summary

This script could be used in future elections for both the same congressional election or other types of elections. It can be used for any number of candidates, counties and votes. The script can also be re-used with minor changes if the election data csv file is collected in a different format. For example, if the election data is ordered differently or we have additional columns of information we can make a small adjustment to accomodate for that. In lines 49 and 52 we got the candidate and county names from each row by referencing a column.
 
```
         # Get the candidate name from each row.
        candidate_name = row[2]

        # Extract the county name from each row.
        county_name = row [1]
```

by adjusting the number in brackets after row we can have the computer pull that info from a different column in the CSV file if necessary. For example, if the county name was in the fifth column our code should be updated  to say county_name = row [4]

---

**Contact:**

Email: charlotte.rotner@gmail.com  
Linkedin: https://www.linkedin.com/in/charlotte-rotner/
