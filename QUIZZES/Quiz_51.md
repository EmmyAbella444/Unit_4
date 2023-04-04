# QUIZ 051
![Screen Shot 2023-04-04 at 22 42 58](https://user-images.githubusercontent.com/111819437/229812065-4484b80b-b14b-49ba-9ad8-f768463d8a47.png)

## CODE
```.py
class Bicycle:
    def __init__(self, wheel: "Wheel", material: str):
        self.wheel = wheel # assign wheel object to the bicycle's wheel attribute
        self.material = material # assign material string to the bicycle's material attribute

    def ride(self):
        return (f"The bicycle has {self.wheel.get_size()} wheel size and material: {self.material}") # return a formatted string with the bicycle's wheel size and material

class Wheel:
    def __init__(self, size: int):
        self.size = size # assign size int to the wheel's size attribute

    def get_size(self):
        return self.size # return the size of the wheel

    def get_perimeter(self):
        return self.size * 3.14 # return the perimeter of the wheel, which is the size multiply by pi

    def get_km_per_rotation(self):
        perimeter = self.get_perimeter() # get the perimeter of the wheel
        meters_per_rotation = perimeter / 100.0 # convert perimeter to meters dividing by 100
        km_per_rotation = meters_per_rotation / 1000.0 # convert meters to kilometers dividing by 1000
        return f"{km_per_rotation} KM per rotation with this Bicycle " # return a formatted string with the kilometers per rotation for the wheel

# Create object for the Whell and bicycle class
wheel = Wheel(size=26)
bicycle = Bicycle(wheel=wheel, material="aluminum")
print(bicycle.ride()) 
print(wheel.get_km_per_rotation()) 

```
## EVIDENCE
![Screen Shot 2023-04-04 at 23 36 38](https://user-images.githubusercontent.com/111819437/229827256-359781a7-d509-45c9-9145-e71b482d4150.png)


