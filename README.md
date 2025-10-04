# Ex.05 Design a Website for Server Side Processing
## Date:4/10/2025

## AIM:
 To design a website to calculate the Body Mass Index(BMI)  in the server side. 


## FORMULA:
BMI = W/HI<sup>2</sup>
<br> BMI-->Body Mass Index
<br> W --> Weight
<br> H --> Height

## DESIGN STEPS:

### Step 1:
Clone the repository from GitHub.

### Step 2:
Create Django Admin project.

### Step 3:
Create a New App under the Django Admin project.

### Step 4:
Create python programs for views and urls to perform server side processing.

### Step 5:
Create a HTML file to implement form based input and output.

### Step 6:
Publish the website in the given URL.

## PROGRAM :
````
infinity.html
<html>
    <head>
        <title>BMI_Calculator</title>
        <style>
           body {
                background-color: purple;
                font-family:'Times New Roman';
                display: flex;
                justify-content: center;
                align-content: center;
                height: 100vh;
            }
            .bmibox {
                background-color:violet;
                border: 10px inset navy;
                padding: 30px;
                text-align: center;
                height: 350px;
                width: 350px;
            }
            input[type="text"] {
                width: 80%;
                padding: 8px;
                margin: 10pypx;
                border: 2px solid black;
                background-color: plum;
            }

        </style>
    </head>

    <body>
        <div class="bmibox">
            <h1 align="center">BMI CALCULATOR</h1>
            <h3 align="center">LEKSHMEENDHRA S(25016379)</h3>
            <form method="POST">
            {%csrf_token %}
            <div class="formelt">
            Height: <input type="text" name="height" value="{{height}}" placeholder="Enter height in m">
            <br>
            <br>
            </div>
            <div class="formelt">
            Weight: <input type="text" name="weight" value="{{weight}}" placeholder="Enter weight in kg">
            <br>
            <br>
            </div>
            <div class="formelt">
            <input  type="submit" value="Calculate">
            <br>
            <br>
            </div>
            <div class="formelt">
            BMI: <input type="text" name="BMI" value="{{BMI}}">
            <br>
            </div>
            </form>
        </div>
    </body>
</html>

views.py
from django.shortcuts import render
def calculate_BMI(request):
  context = {}
  context['BMI'] = "0"
  context['height'] = "0"
  context['weight'] = "0"
  if (request.method=="POST"):
    print("POST method is used")
    height = request.POST.get("height","0")
    weight = request.POST.get("weight","0")
    print("Request=", request)
    print("Height=", height)
    print("Weight=", weight)
    BMI = float(weight)/(float(height)*float(height))
    context['BMI'] = BMI
    context['height'] = height
    context['weight'] = weight
    print("BMI=", BMI)
  return render (request,'mathapp/infinity.html',context)

  urls.py
  from django.contrib import admin
  from django.urls import path
  from mathapp import views
  urlpatterns = [
    path("admin/", admin.site.urls),
    path('calculate_BMI/', views.calculate_BMI, name = "BMI"),
    path('', views.calculate_BMI, name="BMIroot")
 ]
````


## SERVER SIDE PROCESSING:
![alt text](<Screenshot 2025-10-04 102552.png>)
## HOMEPAGE:
![alt text](<Screenshot 2025-10-04 102608.png>)
## RESULT:
The program for performing server side processing is completed successfully.
