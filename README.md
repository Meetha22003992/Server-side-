# Design a Website for Server Side Processing

# AIM:

To design a website to perform mathematical calculations in server side.

# DESIGN STEPS:

## Step 1:
Clone the repository from GitHub

## Step 2:
Create Django Admin project.

## Step 3:
Create a New App.

## Step 4:
Create python programs for views and urls.

## Step 5:
Create a HTML file of forms

##Step 6:
Publish the website in the given URL.


# PROGRAM:
math.html
<!DOCTYPE html>
<html>
    <head>
    <meta charset='utf-8'>
    <meta http-equiv='X-UA-Compatible' content='IE=edge'>
    <title>Page Title</title>
    <meta name='viewport' content='width=device-width, initial-scale=1'>
    
</head>
<style>
    *{
        box-sizing: border-box;
        font-family:'Lucida Sans', 'Lucida Sans Regular', 'Lucida Grande', 'Lucida Sans Unicode', Geneva, Verdana, sans-serif
    }

    body{
    background-color: rgb(98, 114, 134);
    }

    .container{
    width: 1080px;
    height: 350px;
    margin-top: 100px;
    margin-left: auto;
    margin-right: auto;
    border-radius: 25px;
    border: 10px solid rgb(165, 97, 150);
    box-shadow: inset 0 0 15px rgb(172, 58, 58);
    background-color:rgb(90, 212, 221);
    }
    h1{
        text-align: center;
        text-emphasis-color:rgb(176, 202, 79)
        padding-top 15px;
        }
    .calculate{
        padding-top: 10px;
        padding-bottom: 10px;
        padding-left: 10px;
        padding-right:10px;
        text-align: center;
        font-size: 20px;
    }
</style>
<body>
    <div class="container">
        <h1>AREA OF A RECTANGLE</h1>
        <form method="POST">
            {% csrf_token %}
            <div class="calculate"> 
                Length:<input type="text" name="Length" value={{l}}></input><br/>
            </div>
            <div class="calculate">
                Breadth:<input type="text" name="Breadth" value={{b}}></input><br/>
            </div>
            <div class="calculate">
                <input type="submit" value="Calculate area"></input><br/>
            </div>
            <div class="calculate">
                Area:<input type="text" name="area" value={{area}}></input>
            </div>
        </form>
    </div>
</body>
</html>

views.py
from django.shortcuts import render
def rectarea(request):
    context={}
    context['area'] = "0"
    context['l'] = "0"
    context['b'] = "0"
    if request.method == 'POST':
        print("POST method is used")
        l = request.POST.get('length','0')
        b = request.POST.get('breadth','0')
        print('request=',request)
        print('Length=',l)
        print('Breadth=',b)
        area = int(l) * int(b)
        context['area'] = area
        context['l'] = l
        context['b'] = b
        print('Area=',area)
    return render(request,'myapp/math.html',context)
    
    urls.py
    from django.contrib import admin
from django.urls import path
from myapp import views
urlpatterns = [
    path('admin/', admin.site.urls),
    path('areaofrectangle/',views.rectarea,name="areaofrectangle"),
    path('',views.rectarea,name="areaofrectangleroot")
]

# OUTPUT:
![screenshot 5](https://user-images.githubusercontent.com/119401038/213916846-24d046fd-aa87-4a02-877b-f454d678d78e.jpg)


# RESULT:

The program is executed succesfully
