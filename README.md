# Book your space - An Open Source Application
<img src="https://github.com/carminemnc/imgs/blob/main/book-your-space.gif?raw=true" width="250" height="250">

Forking [this idea](https://github.com/devoteam-g-cloud/Office-Desk-Booking-with-Apps-Script) i made up some changes to suits my needs, allowing for the same user to book spaces on two weeks and displaying users name.

[Here](https://script.google.com/macros/s/AKfycbw7IDvU8-UN427sO_u5RLYf8kSGlOolFlrlPA_dk1Ha4H2MgACJn8H8j79t_YfKS1sJ/exec) a live version of the application.

[Here you can find the script](https://script.google.com/home/projects/1t4ZIZ6ycNl_eFugM__CVbttCiOh0aseu1NUhjj8VUkfQw6_Syh34rCuK/edit), take freely a copy.

# How it works

The application is designed to work inside a Google enviroment, so each user should log on with a valid google account.

## Managing person quota

In the file code.gs you have a function getOfficeData() and you can set your Office data.

In "jauge" you define your daily number of people allowed to book a space. If the number is always the same define the quota in the "DAY_JAUGE" variable.
Example :
```javascript
var DAY_JAUGE = 16 ; // Number of available places
```
```javascript
// This is the first week jauge for storing first week reservations
jauge:{
  "monday":{max:DAY_JAUGE- p_mon_count,index:0},
  "tuesday":{max:DAY_JAUGE - p_tue_count,index:1},
  "wednesday":{max:DAY_JAUGE - p_wed_count ,index:2},
  "thursday":{max:DAY_JAUGE - p_thu_count ,index:3},
  "friday":{max:DAY_JAUGE - p_fri_count,index:4}
},

// This is the next week jauge for storing next week reservations

jauge1:{
  "monday":{max:DAY_JAUGE- n_mon_count,index:0},
  "tuesday":{max:DAY_JAUGE - n_tue_count,index:1},
  "wednesday":{max:DAY_JAUGE - n_wed_count ,index:2},
  "thursday":{max:DAY_JAUGE - n_thu_count ,index:3},
  "friday":{max:DAY_JAUGE - n_fri_count,index:4}
}
```

> :warning: **Don't change the index value**

In this example each day the quota of person is the same and is define in the variable DAY_JAUGE.

## Managing names display

In the file code.js you've an array that will work as converter for downloading reservations.

> :warning: **Since the file will be downloaded as .csv it's suggested to have a space between Last name and first name**


Example:
```javascript
// Here you can define your converter as : account@gmail.com => Last name First name

   let arr = [
    { email:"carmine.mnc@gmail.com", name:"Minichini Carmine"}
    ];
```

> :warning: **The same operations MUST be done on page.html file that will render names. Here you can style names display as you want.**

Example:
```javascript
// Here you can define your converter as : account@gmail.com => Last name,First name

   let arr = [
    { email:"carmine.mnc@gmail.com", name:"Minichini,Carmine"}
    ];
```




