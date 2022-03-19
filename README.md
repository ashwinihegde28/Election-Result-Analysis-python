# Election-Result-Analysis-python
Uses Python scripting.

## Project Overview
A Colorado Board of Election commission requires the following tasks to complete the election audit of a recent local congressional election.

1. Calculate the total number of votes cast.
2. Get a complete list of candidates who received votes.
3. Calculate the total number of votes for each candidate received.
4. Calculate the percentage of votes each candidate won.
5. Determine the winner of the election based on popular vote.
6. Calculate the voter turnout for each county.
7. Calculate the percentage of votes from each county out of the total.
8. Determine the county with the highest turnout.

## Resources

- Data Source: election_results.csv
- Software: Python 3.10, Visual Studio Code, 1.65.2


## Summary
The analysis of the election shows that:
- There were 369,711 votes cast in the election.

- The candidates were:
    - Charles Casper Stockham
    - Diana DeGette
    - Raymon Anthony Doane

- The candidate results were:
    - Charles Casper Stockham received 23.0% of the vote, for a total of 85,213 votes.
    - Diana DeGette received 73.8% of the vote, for a total of 272,892 votes.
    - Raymon Anthony Doane received 3.1% of the vote, for a total of 11,606 votes.

- The winner of the election was:
    - Diana DeGette, who received 73.8% of the vote for a total of 272,892 votes.

- The voter turnout for each county was:
    - Jefferson produced 10.5% of voters, for a total of 38,855 voters.
    - Denver produced 82.8% of voters, for a total of 306,055 voters.
    - Arapahoe produced 6.7% of voters, for a total of 24,801 voters.

- The county with the largest voter turnout was:
    - Denver, which produced 82.8% of voters, for a total of 306,055 voters.

- The following images outlines the output in "command line" as well as "election_analysis.txt"   

![Command line Election Results Snapshot](https://github.com/ashwinihegde28/Election-analysis/tree/main/Resources/)
![Election Results In Text file](https://github.com/ashwinihegde28/Election-analysis/tree/main/Resources/)

### Election Audit brief analysis
Apart from the candidate centered election analysis, commission asked to automate and include voter turnout by county using "election_results.csv" (Since the code for candidate analysis already exists only the county analysis is included here). To achieve this few steps were followed.

1.  Initialized the list "county_list",  "county_votes" a dictionary and  variables "winning_candidate", "winning_count", "winning_percentage", "winning_candidate", "largest_county_turnout_count", "largest_county_percentage"
~~~
# Create a county list and county votes dictionary.
county_list=[]
county_votes = {}

# Track the largest county and county voter turnout.
largest_county=""
largest_county_turnout_count = 0
largest_county_percentage = 0
~~~
<br>
2.  Opened the file "election_results.csv" and using the csv reader 

   -  Provided the header, calculated the total votes
   -  Using "if" condition added the existing county to the list of counties and tracked the county's vote count. county's vote count is also incremented after the "if" statement

~~~
 #  Write an if statement that checks that the
        # county does not match any existing county in the county list.
        if county_name not in county_list:

            #  Add the existing county to the list of counties.
            county_list.append(county_name)

            #  Begin tracking the county's vote count.
            county_votes[county_name] = 0


        #  Add a vote to that county's vote count.
        county_votes[county_name] +=1

~~~
<br>

3. Opened the file "election_analysis.txt" in "write" mode to output the total votes to the election result and also printed it on the terminal.
~~~
# Save the results to our text file.
with open(file_to_save, "w") as txt_file:

    # Print the final vote count (to terminal)
    election_results = (
        f"\nElection Results\n"
        f"-------------------------\n"
        f"Total Votes: {total_votes:,}\n"
        f"-------------------------\n\n"
        f"County Votes:\n")
    print(election_results, end="")

    txt_file.write(election_results)
~~~
<br>

4. Iterated through the "for" loop to calculate the county from the county dictionary, percentage of votes for the county and printed it to the terminal as well as to the election_analysis.txt" file.

~~~
 #  Write a for loop to get the county from the county dictionary
 
    for county in county list:
        #  Retrieve the county vote count.
        votes_county = county_votes[county]
        
        #  Calculate the percentage of votes for the county.
        county_vote_percent = float(votes_county) / float(total_votes) * 100

         #  Print the county results to the terminal.
        county_results = (
            f"{county}: {county_vote_percent:.1f}% ({votes_county:,})\n")
        print(county_results)

         #  Save the county votes to a text file.
        txt_file.write(county_results)  
  ~~~
<br>

5. Used "if" statement to know the winning county, county turn out county and percentage of winning county and printed both in terminal as well as "election_results.csv".
~~~
  #  Write an if statement to determine the winning county and get its vote count.
        # Determine if the votes are greater than the winning count
        if (votes_county > largest_county_turnout_count) and (county_vote_percent> winning_percentage) :
            largest_county_turnout_count = votes_county
            largest_county = county
            largest_county_percentage = county_vote_percent
            
            
            # Print the county with the largest turnout to the terminal.

    largest_county_print = (
        f"-------------------------\n"
        f"Largest County Turnout: {largest_county}\n"
        f"-------------------------\n"
    )
    print(largest_county_print)


     Save the county with the largest turnout to a text file.
    txt_file.write(largest_county_print)   
       
~~~
<br>

## Election-Audit Summary:

 This code base is very valuable asset for the election commission.
- The same code base can be used for different elections like provincial or federal or any other.
- Using this stable code set, Election commission can add few modifications for future enhancement or change requests.
- Code can run efficiently for different years with or without modification.
- Even if the volume of the data for ballots or candidate or county change the same set of codes can be used.
