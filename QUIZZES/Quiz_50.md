# QUIZ 050
![Screen Shot 2023-04-04 at 22 41 19](https://user-images.githubusercontent.com/111819437/229811582-8aeffdac-af8f-45c9-9c83-f9ce0ab9d3d0.png)

## CODE
```.py
# Define a class called Flight
class Flight:
    # Constructor to initialize the object with flight details
    def __init__(self, flight_number:str,flight_origin:str,destination:str,departure_time:str,duration:list):
        self.flight_number = flight_number
        self.flight_origin = flight_origin
        self.destination = destination
        self.departure_time = departure_time
        self.duration = duration

    # Method to get the duration of the flight
    def get_duration(self):
        return f"{self.duration[0]} hours {self.duration[1]} minutes and {self.duration[2]} seconds"

# Create two instances of the Flight class with different details
flight1 = Flight(flight_number="AA123", flight_origin="New york", destination="Los Angeles", departure_time="10:00 am",duration=[1,20,30])
flight2 = Flight(flight_number="AA321", flight_origin="Japan", destination="Brazil", departure_time="2:25 pm",duration=[4,50,40])

# Print the duration of each flight
print(flight1.get_duration())
print(flight2.get_duration())
```
## EVIDENCE
![Screen Shot 2023-04-04 at 23 14 35](https://user-images.githubusercontent.com/111819437/229820972-06c1bbde-8f62-455f-a99f-3f81532ef13a.png)
