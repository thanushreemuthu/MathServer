# Ex.05 Design a Website for Server Side Processing
## Date:24/04/2025

## AIM:
 To design a website to calculate the power of a lamp filament in an incandescent bulb in the server side. 


## FORMULA:
P = I<sup>2</sup>R
<br> P --> Power (in watts)
<br> I --> Intensity
<br> R --> Resistance

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
```
tfar.html

{% load static %}
<html>
<head>
    <title>tfar</title>
    <style>
        
h1{
    border: 2px solid black;
    padding: 20px;
    margin: 10px;
    border-radius: 5px;
    position: fixed;
    top: 200px;
    right: 500px;
    font-size: xx-large;
    font-weight: bolder;
    font-variant: small-caps;
    background: linear-gradient(to bottom,red,yellow,red);
    font-family: Georgia, 'Times New Roman', Times, serif;
    color: grey;
}
form{
    border: 2px solid black;
    background-color: rgba(128, 128, 128, 0.064) ;
    padding: 30px;
    margin: 10px;
    border-radius: 10px;
    width: 425px;
    position: fixed;
    top: 300px;
    left: 527px;
    background-image: url("{%static 'images/vijay.jpg' %}");
    
    background-size: 60%;
    background-repeat: no-repeat;
    background-position: left;
    
}

    </style>
</head>
<body>
    <h1 align="center" > power of a lamp filament</h1>
    <form align="center" method="POST">
    {%csrf_token%}
     
    <div class="power">

        <label for="INTENSITY"><b>INTENSITY:</b></label>
        <input type="text" name="intensity" id="INTENSITY" placeholder="Enter the Value" value="{{i}}">
    </div>
    <br>
    <div class="power">
        <label for="RESISTANCE"><b>RESISTANCE:</b></label>
        <input type="text" name="resistance" id="RESISTANCE" placeholder="Enter the Value" value="{{r}}">
    </div>
    <br>
    <input type="submit" value="CALCULATE">
    <br>
    <br>
    <div class="power">
        <label for="POWER"><b>POWER:</b></label>
        <input type="text" name="POWER" id="POWER" placeholder="Answer" value="{{power}}">
        
    </div>
</form>
</body>
</html>


views.py

from django.shortcuts import render
def powerlamp(request): 
    context={} 
    context['power']="0" 
    context['i']="0" 
    context['r']="0" 
    if request.method=='POST': 
        print("POST method is used")
        i=request.POST.get('intensity','0')
        r=request.POST.get('resistance','0')
        print('request=',request) 
        print('intensity=',i) 
        print('resistance=',r) 
        power=(int(i) ** 2 ) * int(r) 
        context['power']=power
        context['i']=i
        context['r']=r 
        print('Power=',power) 
    return render(request,'thalaforareason/tfar.html',context)
    

urls.py

from django.contrib import admin 
from django.urls import path 
from thalaforareason import views 
urlpatterns = [ 
    path('admin/', admin.site.urls), 
    path('powerlamp/',views.powerlamp,name="powerlamp"),
    path('',views.powerlamp,name="powerlamproot")
]
```
## SERVER SIDE PROCESSING:
![server](https://github.com/user-attachments/assets/7f158ca4-9ffb-4f61-be60-947d01e78bf9)


## HOMEPAGE:
![home](https://github.com/user-attachments/assets/f5e40f45-dccd-4d7f-b6e7-0c7c31a8bcc0)


## RESULT:
The program for performing server side processing is completed successfully.
