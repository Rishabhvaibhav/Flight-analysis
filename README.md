# Flight-Delays-and-Cancellations

(Image: Jupyter Notebook)
4	American Airlines Inc.	34
1	Skywest Airlines Inc.	26
2	Atlantic Southeast Airlines	23
5	JetBlue Airways	19
8	American Eagle Airlines Inc.	18
ORIGIN_AIRPORT
In [49]:
#Percentage by ORIGIN_AIRPORT
cancelled_flights_by_origin_airpot = flights_data
grouped_cancelled_flights_by_origin_airpot=cancelled_flights_by_origin_airpot[["ORIGIN_AIRPORT","CANCELLED","ON_TIME"]].groupby(['ORIGIN_AIRPORT']).sum().reset_index()
grouped_cancelled_flights_by_origin_airpot["FLIGHTS_COUNT"]=cancelled_flights_by_origin_airpot[["ORIGIN_AIRPORT","ON_TIME"]].groupby(['ORIGIN_AIRPORT']).count().reset_index()["ON_TIME"]
grouped_cancelled_flights_by_origin_airpot["CANCELLED_PERCENTAGE"]=grouped_cancelled_flights_by_origin_airpot["CANCELLED"]*1.0/grouped_cancelled_flights_by_origin_airpot["FLIGHTS_COUNT"]*100
grouped_cancelled_flights_by_origin_airpot["ON_TIME_PERCENTAGE"]=grouped_cancelled_flights_by_origin_airpot["ON_TIME"]*1.0/grouped_cancelled_flights_by_origin_airpot["FLIGHTS_COUNT"]*100
grouped_cancelled_flights_by_origin_airpot[["ORIGIN_AIRPORT","FLIGHTS_COUNT","CANCELLED","ON_TIME","CANCELLED_PERCENTAGE","ON_TIME_PERCENTAGE"]].sort_values(by=['ON_TIME_PERCENTAGE'],ascending=[False])
plt.figure();
# print(len(grouped_cancelled_flights_by_origin_airpot["ORIGIN_AIRPORT"]))
plot = grouped_cancelled_flights_by_origin_airpot.sort_values(by=["ON_TIME_PERCENTAGE"],ascending=False).plot(x="ORIGIN_AIRPORT",y="ON_TIME_PERCENTAGE",kind='bar',figsize=(100,30))
<matplotlib.figure.Figure at 0x10e531d90>
(Image)
