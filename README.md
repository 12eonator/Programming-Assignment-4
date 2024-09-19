# Programming-Assignment-4

PS. Quick Readme since I am running out of time. will edit someother time

# ECE BOARD EXAM PROBLEM: 
Using data wrangling and data visualization technique with storytelling, analyze the data and present different (i) data frames; and (ii) visuals using the dataset given.

## 1. Create the following data frames based on the format provided:

### a. Filename: Instru = [“Name”, “GEAS”, “Electronics >70”]; where track is constant as Instrumentation and hometown Luzon


````
Instru = all[(all.Track == 'Instrumentation') 
            & (all.Hometown == 'Luzon') 
            & (all.Electronics > 70)][['Name', 'GEAS', 'Electronics']].reset_index(drop=True)
````
I used simple syntax, boolean operations, and the dataframe elements to create a new dataframe with the specifications needed
For making it pretty, I used the .reset_index function to make the index reset


b. Filename: Mindy = [ “Name”, “Track”, “Electronics”, “Average >=55”]; where hometown is
constant as Mindanao and gender Female

````
# Filename: Mindy = [ “Name”, “Track”, “Electronics”, “Average >=55”]; where hometown is constant as Mindanao and gender Female

# Add an 'Average' collumn at dataframe all
all['Average'] = all[['Math', 'Electronics', 'GEAS','Communication']].mean(axis=1)
all
````

I used the .mean function to find the average and added it as a collumn to my original data frame

````
# Filter the values to only show what is needed
# [ “Name”, “Track”, “Electronics”, “Average >=55”]; where hometown is constant as Mindanao and gender Female

Mindy = all[(all.Hometown == 'Mindanao')
            & (all.Gender == 'Female')
            & (all.Average >= 55)][['Name', 'Track', 'Electronics','Average']].reset_index(drop=True)
Mindy

````
Using the newly added column, I created a new dataframe with the given specifications similar to part A

3. Create a visualization that shows how the different features contributes to average grade. Does
chosen track in college, gender, or hometown contributes to a higher average score?

````
# Create a figure with size 20 x 5 (2o width, 5 length)
fig2 = plt.figure(figsize=(20,5))

# Group by track and create a box plot using average scores as content in the Dataframe 'all'
grouped = all.groupby('Track')['Average'].apply(list)

# Prepare data for plotting
plot_data = [group for group in grouped]

# Create box plot
fig2 = plt.figure(figsize=(20, 5))
plt.boxplot(plot_data, labels=grouped.index)
````
I used box plots of for the different tracks, gender, and hometowns with average as the x axis. and compare each results. 
