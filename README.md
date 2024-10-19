# Road-Accident-
Python Code

Code :- 1)The Percentage of Road Accidents During All the Years
import pandas as pd
import matplotlib.pyplot as plt

# Assuming the data is loaded in df with columns 'Year' and 'Accidents'
total_accidents_per_year = df.groupby('Year')['Accidents'].sum()

# Calculate the percentage change year over year
percentage_change_accidents = total_accidents_per_year.pct_change() * 100

# Print results
print(percentage_change_accidents)

# Plotting
percentage_change_accidents.plot(kind='bar', title='Yearly Percentage Change in Road Accidents')
plt.xlabel('Year')
plt.ylabel('Percentage Change (%)')
plt.show()



Code :- 2)Mean Accidents per Lakh Population for Each Year
# Assuming df has columns 'Year', 'Population', 'Accidents'
df['Accidents_per_Lakh'] = (df['Accidents'] / df['Population']) * 100000
mean_accidents_per_year = df.groupby('Year')['Accidents_per_Lakh'].mean()

# Print results
print(mean_accidents_per_year)

# Plotting
mean_accidents_per_year.plot(kind='line', title='Mean Accidents per Lakh Population by Year')
plt.xlabel('Year')
plt.ylabel('Mean Accidents per Lakh Population')
plt.show()




Code :- 3)The Highest and Least Number of Accident States
# Assuming df has a 'State' and 'Accidents' column
accidents_by_state = df.groupby('State')['Accidents'].sum()
highest_accident_state = accidents_by_state.idxmax()
least_accident_state = accidents_by_state.idxmin()

# Print results
print(f"Highest Accident State: {highest_accident_state}, Least Accident State: {least_accident_state}")

# Plotting
accidents_by_state.plot(kind='bar', title='Total Accidents by State')
plt.xlabel('State')
plt.ylabel('Total Accidents')
plt.show()



Code :- 4)Offenders and Victims Who Died According to Gender
# Assuming df1 has columns 'Gender', 'Offenders_Deaths', 'Victims_Deaths'
gender_deaths = df1.groupby('Gender')[['Offenders_Deaths', 'Victims_Deaths']].sum()

# Print results
print(gender_deaths)

# Plotting
gender_deaths.plot(kind='bar', title='Offenders and Victims Deaths by Gender')
plt.xlabel('Gender')
plt.ylabel('Number of Deaths')
plt.show()




Code :- 5)Percentage of Deaths Due to Non-Wearing Helmets (Male vs. Female)
# Assuming df2 has columns 'Gender' and 'Deaths'
total_deaths_helmet = df2.groupby('Gender')['Deaths'].sum()
percentage_deaths_helmet = (total_deaths_helmet / total_deaths_helmet.sum()) * 100

# Print results
print(percentage_deaths_helmet)

# Plotting
percentage_deaths_helmet.plot(kind='pie', autopct='%1.1f%%', title='Deaths Due to Non-Wearing Helmets (Male vs Female)')
plt.show()




Code :- 6)Number of Accidents Happening per State from 2003 to 2016
# Assuming df3 has columns 'State', 'Year', and 'Accidents'
accidents_per_state = df3.groupby(['State', 'Year'])['Accidents'].sum().unstack()

# Print results
print(accidents_per_state)

# Plotting
accidents_per_state.plot(kind='line', title='Accidents per State from 2003 to 2016')
plt.xlabel('Year')
plt.ylabel('Number of Accidents')
plt.legend(title='State', bbox_to_anchor=(1.05, 1), loc='upper left')
plt.show()




Code :- 7)Number of Accidents for 1, 2, 3, 4 Lanes per Lakh Population of Respective State
# Assuming df4 has columns 'Lane_Type', 'State', 'Population', 'Accidents'
df4['Accidents_per_Lakh'] = (df4['Accidents'] / df4['Population']) * 100000
accidents_by_lane = df4.groupby(['Lane_Type', 'State'])['Accidents_per_Lakh'].sum().unstack()

# Print results
print(accidents_by_lane)

# Plotting
accidents_by_lane.plot(kind='bar', stacked=True, title='Accidents by Lane Type and State per Lakh Population')
plt.xlabel('Lane Type')
plt.ylabel('Accidents per Lakh Population')
plt.show()



Code :- 8)Number of People Injured for 1, 2, 3, 4 Lanes per Lakh Population
# Assuming df4 has an 'Injuries' column
df4['Injuries_per_Lakh'] = (df4['Injuries'] / df4['Population']) * 100000
injuries_by_lane = df4.groupby(['Lane_Type', 'State'])['Injuries_per_Lakh'].sum().unstack()

# Print results
print(injuries_by_lane)

# Plotting
injuries_by_lane.plot(kind='bar', stacked=True, title='Injuries by Lane Type and State per Lakh Population')
plt.xlabel('Lane Type')
plt.ylabel('Injuries per Lakh Population')
plt.show()



Code :- 9)Number of People Killed for 1, 2, 3, 4 Lanes per Lakh Population
# Assuming df4 has a 'Deaths' column
df4['Deaths_per_Lakh'] = (df4['Deaths'] / df4['Population']) * 100000
deaths_by_lane = df4.groupby(['Lane_Type', 'State'])['Deaths_per_Lakh'].sum().unstack()

# Print results
print(deaths_by_lane)

# Plotting
deaths_by_lane.plot(kind='bar', stacked=True, title='Deaths by Lane Type and State per Lakh Population')
plt.xlabel('Lane Type')
plt.ylabel('Deaths per Lakh Population')
plt.show()




Code :- 10)Number of Accidents, Injuries, Deaths on Single Lane per Lakh Population
single_lane = df4[df4['Lane_Type'] == 'Single Lane']
single_lane['Accidents_per_Lakh'] = (single_lane['Accidents'] / single_lane['Population']) * 100000
single_lane_stats = single_lane.groupby('State')[['Accidents_per_Lakh', 'Injuries_per_Lakh', 'Deaths_per_Lakh']].sum()

# Print results
print(single_lane_stats)

# Plotting
single_lane_stats.plot(kind='bar', stacked=True, title='Single Lane Accidents, Injuries, Deaths per Lakh Population')
plt.xlabel('State')
plt.ylabel('Rate per Lakh Population')
plt.show()

Code :- 11)Number of Accidents, People Injured, Killed on Double Lane per Lakh Population
double_lane = df4[df4['Lane_Type'] == 'Double Lane']
double_lane['Accidents_per_Lakh'] = (double_lane['Accidents'] / double_lane['Population']) * 100000
double_lane_stats = double_lane.groupby('State')[['Accidents_per_Lakh', 'Injuries_per_Lakh', 'Deaths_per_Lakh']].sum()

# Print results
print(double_lane_stats)

# Plotting
double_lane_stats.plot(kind='bar', stacked=True, title='Double Lane Accidents, Injuries, Deaths per Lakh Population')
plt.xlabel('State')
plt.ylabel('Rate per Lakh Population')
plt.show()




Code :- 12)Number of Accidents, People Injured, Killed on Three Lane per Lakh Population
Repeat the process for three lanes:
three_lane = df4[df4['Lane_Type'] == 'Three Lane']
three_lane['Accidents_per_Lakh'] = (three_lane['Accidents'] / three_lane['Population']) * 100000
three_lane_stats = three_lane.groupby('State')[['Accidents_per_Lakh', 'Injuries_per_Lakh', 'Deaths_per_Lakh']].sum()

# Print results
print(three_lane_stats)

# Plotting
three_lane_stats.plot(kind='bar', stacked=True, title='Three Lane Accidents, Injuries, Deaths per Lakh Population')
plt.xlabel('State')
plt.ylabel('Rate per Lakh Population')
plt.show()



Code :- 13) Number of Accidents, People Injured, Killed on Four Lane per Lakh Population
Repeat the process for four lanes:
four_lane = df4[df4['Lane_Type'] == 'Four Lane']
four_lane['Accidents_per_Lakh'] = (four_lane['Accidents'] / four_lane['Population']) * 100000
four_lane_stats = four_lane.groupby('State')[['Accidents_per_Lakh', 'Injuries_per_Lakh', 'Deaths_per_Lakh']].sum()

# Print results
print(four_lane_stats)

# Plotting
four_lane_stats.plot(kind='bar', stacked=True, title='Four Lane Accidents, Injuries, Deaths per Lakh Population')
plt.xlabel('State')
plt.ylabel('Rate per Lakh Population')
plt.show()




Code :- 14) Total Number of Injured, Killed, Road Accidents Irrespective of Lanes per Lakh Population
df4['Total_Accidents_per_Lakh'] = (df4['Accidents'] / df4['Population']) * 100000
df4['Total_Injuries_per_Lakh'] = (df4['Injuries'] / df4['Population']) * 100000
df4['Total_Deaths_per_Lakh'] = (df4['Deaths'] / df4['Population']) * 100000

total_stats = df4.groupby('State')[['Total_Accidents_per_Lakh', 'Total_Injuries_per_Lakh', 'Total_Deaths_per_Lakh']].sum()

# Print results
print(total_stats)

# Plotting
total_stats.plot(kind='bar', stacked=True, title='Total Road Accidents, Injuries, Deaths per Lakh Population')
plt.xlabel('State')
plt.ylabel('Rate per Lakh Population')
plt.show()



Code :- 15 to 23. Analysis by Reasons (Fault of Driver, Pedestrian, Defects in Road Condition, Weather, etc.)
These analyses follow the same grouping and aggregation pattern:
# Group by state and reason, and calculate per lakh population
df5['Accidents_per_Lakh'] = (df5['Accidents'] / df5['Population']) * 100000
accidents_by_reason = df5.groupby(['Reason', 'State'])['Accidents_per_Lakh'].sum().unstack()

# Print results
print(accidents_by_reason)

# Plotting
accidents_by_reason.plot(kind='bar', stacked=True, title='Accidents by Reason per Lakh Population')
plt.xlabel('Reason')
plt.ylabel('Accidents per Lakh Population')
plt.show()



Code :- 24 to 26. Accidents, Fatalities, and Injuries per Vehicle Type
For vehicle types:
df6['Accidents_per_Lakh'] = (df6['Accidents'] / df6['Population']) * 100000
df6['Deaths_per_Lakh'] = (df6['Deaths'] / df6['Population']) * 100000
df6['Injuries_per_Lakh'] = (df6['Injuries'] / df6['Population']) * 100000

vehicle_stats = df6.groupby('Vehicle_Type')[['Accidents_per_Lakh', 'Deaths_per_Lakh', 'Injuries_per_Lakh']].sum()

# Print results
print(vehicle_stats)

# Plotting
vehicle_stats.plot(kind='bar', stacked=True, title='Accidents, Deaths, Injuries by Vehicle Type per Lakh Population')
plt.xlabel('Vehicle Type')
plt.ylabel('Rate per Lakh Population')
plt.show()



Code :- 27. Accidents by Day and Night for 2014 and 2016
For day/night accidents:
df7_day_night = df7[df7['Year'].isin([2014, 2016])]
day_night_stats = df7_day_night.groupby(['Time_of_Day', 'Year'])['Accidents'].sum().unstack()

# Print results
print(day_night_stats)

# Plotting
day_night_stats.plot(kind='bar', stacked=True, title='Accidents by Day and Night (2014 vs 2016)')
plt.xlabel('Time of Day')
plt.ylabel('Number of Accidents')
plt.show()
