# Horsepower-and-year-vs-MPG

```
#CIS 443 01
#Assignment 3
#11/8/24

import pandas as pd
import matplotlib.pyplot as plt
from scipy.stats import linregress

car_data = pd.read_csv('AutoMPGdata.csv')

#Horsepower vs MPG
horsepower = car_data['Horsepower']
mpg = car_data['MPG']

slope, intercept, r_value, p_value, std_err = linregress(horsepower, mpg)

#Creating the graph for Horsepower vs MPG
plt.figure(figsize=(10, 5))
plt.scatter(horsepower, mpg, color='blue', label='Plot Points')
plt.plot(horsepower, intercept + slope * horsepower, color='red', label='Regression Line')
plt.title('Horsepower vs MPG')
plt.xlabel('Horsepower')
plt.ylabel('MPG')
plt.legend()
plt.show()

#using the given 125 horsepower given to create a prediction 
mpg_prediction = intercept + slope * 125
print(f"The predicted MPG for a car with 125 Horsepower is {mpg_prediction}")
#printing the values
print(f"R-squared for Horsepower vs MPG: {r_value**2}")
print(f"P-value for Horsepower vs MPG: {p_value}")
print(f"Slope for Horsepower vs MPG: {slope}")
print(f"Intercept for Horsepower vs MPG: {intercept}")
print("----------------------------------------------------------------------")



#Year vs MPG
year = car_data['Year']
slope2, intercept2, r_value2, p_value2, std_err2 = linregress(year, mpg)

#Creating the graph for Year vs MPG
plt.figure(figsize=(10, 5))
plt.scatter(year, mpg, color='purple', label='Plot Points')
plt.plot(year, intercept2 + slope2 * year, color='red', label='Regression Line')
plt.title('Year vs MPG')
plt.xlabel('Year')
plt.ylabel('MPG')

#using the given the year 1984. 84 is used to keep with the standard set in the data
mpg_prediction2 = intercept2 + slope2 * 84
print(f"Predicted MPG for a car built in 1984 is {mpg_prediction2}")
#printing the values
print(f"R-squared for : {r_value2**2}")
print(f"P-value: {p_value2}")
print(f"Slope: {slope2}")
print(f"Intercept: {intercept2}")


#deciding if the calculations are statistically significant.
print("----------------------------------------------------------------------")
print("Is Horsepower statistically significant?")
if p_value < 0.05:
    print("Yes")
else:
    print("No")

print("Is the year statistically significant?")
if p_value2 < 0.05:
    print("Yes")
else:
    print("No")
```
