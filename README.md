# Design a Website for Server Side Processing

## AIM:
To design a website to perform mathematical calculations in server side.

## DESIGN STEPS:

### Step 1:
Desing your website for calculation using wireframe work.

### Step 2:
Then to execute the wireframe work desing use html,css

### Step 3:
Use views.py to execute the coding in serverside.

### Step 4:
Mention the path of the website in urls.py.

### Step 5:
Publish the website in the given URL.
## PROGRAM :
### Area.html
~~~
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
        font-family:'Trebuchet MS', 'Lucida Sans Unicode', 'Lucida Grande', 'Lucida Sans', Arial, sans-serif
    }

    body{
    background-color: rgb(201, 103, 141);
    }

    .container{
    width: 1080px;
    height: 350px;
    margin-top: 100px;
    margin-left: auto;
    margin-right: auto;
    border-radius: 25px;
    border: 10px solid rgb(72, 97, 45);
    box-shadow: inset 0 0 25px rgb(151, 216, 82);
    background-color:rgb(129, 158, 97);
    }
    h1{
        text-align: center;
        padding-top: 15px;
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
        <h1>VOLUME OF CYLINDER</h1>
        <form method="POST">
            {% csrf_token %}
            <div class="calculate"> 
                Radius:<input type="text" name="radius" value={{r}}></input><br/>
            </div>
            <div class="calculate">
                Height:<input type="text" name="height" value={{h}}></input><br/>
            </div>
            <div class="calculate">
                <input type="submit" value="Calculate Volume"></input><br/>
            </div>
            <div class="calculate">
                Volume:<input type="text" name="volume" value={{volume}}></input>
            </div>
        </form>
    </div>
    
</body>
</html>
~~~
### View.py
~~~
from django.shortcuts import render

def volumecalculation(request):
    context ={}
    context["volume"]='0'
    context["r"]='0'
    context["h"]='0'
    if request.method == 'POST':
        
        r=request.POST.get('radius','0')
        h=request.POST.get('height','0')
        volume= 3.14*int(r)*int(r)*int(h)
        context['volume'] = volume
        context['r']=r
        context['h']=h
    return render(request,"mathapp/area.html",context)
~~~
### Url.py
~~~
from django.contrib import admin
from django.urls import path
from mathapp import views

urlpatterns = [
    path('admin/', admin.site.urls),
    path('volumeofcylinder/',views.volumecalculation,name="volumeofcylinder"),
    path('',views.volumecalculation,name="volumeofcylinder")
]
~~~
## OUTPUT:
![output](p2.jpeg))
## Result:
A website to perform mathematical calculations in server side is created.
