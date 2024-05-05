// This file has been created via https://markdownlivepreview.com/ //

# -SETU-Web-Development
This is a website created to be submitted as a second Web Development assignment for SETU, Waterford, Ireland.

# Whether Weather website
This website is about forecasts of 9 cities whose data are originated in json files and rounded up in a js file, as an instantiation of a const variable, namely 'weatherData'.

# What this project does
Its purpose is simply to provide forecasts of the cities added to the website by means of clickable cards in the index/dashboard page.
In a nutshell, the data shown on the website homepage reflect the dayly data/forecasts (Max temperature and wind speed at 10 meters above ground). Upon clicking on one of the cities, a city-focus page will present an array of data to the user about daily and hourly forecasts as well as dayly hourly forecasts of the current week.


# Why the project is useful
The project is useful for those users that would like to check the weather forecasts of the the day or of the entire week. However, the main purpose of the project was for the writer to be exposed to the use of Bulma components and, above all, JavaScript.
The ultimate ideas here would have been to expand the website insofar that it would have included city-focus pages with forecasts focused on each single day of the week as well as a favourite city list to enable the user to only show the cities he wishes.
However, being still technically challenged at this stage and also due to time constraints, I decided not to pursue such objectives.

# How users can get started with the project

## Home page

As a user opens up the Whether Weather AN Homepage, they will see a sticky nav bar on the top for an easy navigation through the website.

### Navigation bar

The Navbar show all items that user needs for a comfortable and friendly navigation. There is also a dropdown listing all cities (upon clicking a city, a user will land to the city-focus page of that city).
The nav (nav.njk partial) also contains the logo, which is clickable and links to the Homepage/Dashboard 'index.njk'.

![image](https://github.com/AndreaNardinocchi/SETU-AssignmentWeb2/assets/51911079/6e8a2138-d76d-42f2-9ea4-5f8360d044b0)


#### Source attribution

Apart from the official bulma documentation in:
*https://bulma.io/documentation/components/navbar/

I also studied some examples online such as *https://www.geeksforgeeks.org/bulma-navbar/.

### Header

This element is just a layer added below the menu to give the website a more elevated touch when scrolling down the page. It has practically an aesthetic purpose which is to make the website easy on the eyes of the user. As a matter of fact, the lighter background color used in here 'has-background-info-light', accompany the user's eyes when moving from the navbar ('has-background-info') to the Banner (has-background-primary-light).

![image](https://github.com/AndreaNardinocchi/SETU-AssignmentWeb2/assets/51911079/76baf156-d38b-4aef-abe7-0667af8c9a06)


(header.njk partial).

### Banner

Right below the sticky nav bar, the user will see a bigger version of the logo added to the navbar and a centered heading letting the user know that he is seeing the dashboard.


![image](https://github.com/AndreaNardinocchi/SETU-AssignmentWeb2/assets/51911079/65b77828-6cbc-4175-9709-2f8b6614df2f)



### City cards Grid

As the user scrolls down, they will reach the city cards grid which will give them an overview of the website content. The dashboard looks pretty intuitive as a subtitle also guides the user through by inviting them to click on the cards to check out the city forecasts.

The layout has been achieved by using Bulma classes such as 'columns' to create a container for the columns embedded in it such as the 'column' class.
Also, the column units are 3 per 'columns' container as the class 'is-4' determins each column size (each column shows a city card nested into it):

image to add

#### City Card

Each card shows the city name on the top center, an image, right below, (I call it icon throughout the project) representative of the daily weather, and, in the footer, maximun temperature and wind speed at 10 meters (dayly data).

![image](https://github.com/AndreaNardinocchi/SETU-AssignmentWeb2/assets/51911079/7fa8d6ab-b5bc-4abe-8b36-bc2fa54b4304)


To ensure that the correct icon is shown based upon the weather code, the following if statements have been used:


```
// Icons changing based upon the weather code
  let iconDailyToday = "unknown";
 
  if (currentCityData.daily.weather_code[indexOfToday] === 0) {
  iconDailyToday = '/images/sun.png';
  } else if ((currentCityData.daily.weather_code[indexOfToday] >= 1) && (currentCityData.daily.weather_code[indexOfToday] <=3)) {
  iconDailyToday = '/images/cloudy.png';
  } else if ((currentCityData.daily.weather_code[indexOfToday] >= 45) && (currentCityData.daily.weather_code[indexOfToday] <=48)) {
  iconDailyToday = '/images/fog.png';
  } else if ((currentCityData.daily.weather_code[indexOfToday] >= 51) && (currentCityData.daily.weather_code[indexOfToday] <=67)) {
  iconDailyToday = '/images/rain.png';
  } else if ((currentCityData.daily.weather_code[indexOfToday] >= 80) && (currentCityData.daily.weather_code[indexOfToday] <=82)) {
  iconDailyToday = '/images/rain.png';
  }  else if ((currentCityData.daily.weather_code[indexOfToday] >= 71) && (currentCityData.daily.weather_code[indexOfToday] <=75)) {
  iconDailyToday = '/images/snow.png';
  } else if (currentCityData.daily.weather_code[indexOfToday] === 95){
  iconDailyToday = '/images/storm.png';
  } else {
  iconDailyToday = '/images/sun.png';
  }
```
indexOfToday is a const variable created earlier in the index.njk file script, which fetches the value from the daily weather_code in weather_data.js:

```
const indexOfToday = currentCityData.daily.time.indexOf(`Today`);
````

#### Source attribution

https://bulma.io/documentation/elements/title/
https://bulma.io/documentation/columns/basics/
https://bulma.io/documentation/components/card/#examples

All icons/images have been taken from:
https://www.flaticon.com/


### Footer

At the bottom of the page there is a footer (footer.njk partial), whose layout is a 4 column one achieved by using the class 'column is-3'.
While the first column shows an Irish address, the rest of the columns show nav lonks split into 2 columns and some contact details in the last column.
Additionally, there is an underfooter with the 'whether weather' icon again to boost brand awareness and a string with developer linkedin link.

![image](https://github.com/AndreaNardinocchi/SETU-AssignmentWeb2/assets/51911079/cd61f7ca-e4df-4db4-8703-92e754c67ace)


#### Source attribution

https://bulma.io/documentation/layout/footer/

## City Focus page

One interesting element here, apart from the use of the URL Search Params such as ex. '/city-focus/?city=berlin' is the way the city name fetched from the weather_data.js was manipulated to render in a nice way and readable.

![image](https://github.com/AndreaNardinocchi/SETU-AssignmentWeb2/assets/51911079/bc7e447a-16c7-4a3c-8812-227897e8ca9c)


The code is shown below:

```
/**
   * This function removes any underscores and capitalize the first letter of each word and it is used to change the value
   * of the cities in the weather_data.js to make it suitable to be used as a heading in the 'city-focus' page
   *
   * Source:
   * https://www.codeease.net/programming/javascript/javascript-remove-underscore-and-capitalize
   */
   
   function removeUnderscoreAndCapitalize(str) {
     return str.split('_')
       .map(word => word.charAt(0).toUpperCase() + word.slice(1))
       .join('');
     }
     const input = currentCity; // The current city is the instantiation of the variable 'input'
     const output = removeUnderscoreAndCapitalize(input); // The current city value (input) is passed through the function as a parameter
     
     /**
     * Once the above function has completed its scope, the below method 'replace' add a space back between the 2 capitalized letters
     *
     * Source:
     * https://www.sourcetrail.com/javascript/js-add-space-before-capital-letter/
     */
 
     
     let addingSpaceBack = output;
     
     addingSpaceBack = addingSpaceBack.replace(/([A-Z])/g, ' $1');
     cityHeading.innerHTML = addingSpaceBack;
```

A key role here is played by the 'map()' method , which creates a new array with the results and provides a function on every element in the array. It is the map() function that is used to capitalize the first letter of each word, which is called in by the charAt(index) method (toUpperCase(), of course, does the needful).

### Right Now card
This is the page where a user lands after clicking on one of the city cards in the Dashboard.

![image](https://github.com/AndreaNardinocchi/SETU-AssignmentWeb2/assets/51911079/b4498cc1-e67f-4d0b-8f03-db1713abd41f)


On the top right, there is a card with weatherData dayly data and the current date and hour. This card is 'dynamic' in the sense that changes its data and icon every hour.
This has been achieved by setting up a const variable 'indexOfCurrentHour' as per the below code:

```
 const indexOfCurrentHour = currentCityDataHourly.hourly.time.indexOf(`TodayT${currentIndexHour}:00`);
```
The currentIndexHour, in turn, is a const variable created by using the object dayjs.js:

```
// Creating a new date object to show the current hour
    const timeNow = dayjs();
    // Returning the current hour in the format HH:mm
    const currentHour = timeNow.format("HH:mm");
    // Returning the current hour in the format HH
    const currentIndexHour = timeNow.format("HH");
````

Furthermore, the current date and time are achieved by calling the below date object:

```
const today = new Date();
```
in the below strings, the toDateString() method has been used to make the date format readable:

```
const cityFocusOneCardTopRightSubHeading = document.querySelector('#cityfocus-1-top-card-sub-heading');
cityFocusOneCardTopRightSubHeading.innerHTML = `${currentHour} ${today.toDateString() }`;

```

The hourly data shown in here are the temperature above 2 meters and the wind speed at 10 meters, both hourly


#### Source attribution

https://www.w3schools.com/jsref/jsref_todatestring.asp
https://www.w3schools.com/js/js_dates.asp
https://www.codeease.net/programming/javascript/javascript-remove-underscore-and-capitalize
https://www.sourcetrail.com/javascript/js-add-space-before-capital-letter/


### Daily Forecast cards

Right below the 'Right Now' card there is a 4 colum layout, which shows 2 forecast cards, The one on the left shows the today's maximum temperature, whereas the one on the right shows the today's wind speed at 10 meters (this one also shows its own set of icons which slightly differs from the ones used throughout the site):

```
//------------ Right card Daily Weather---------------------------//

   let iconWindDaily = "unknown";
 
   
   if (currentCityData.daily.weather_code[indexOfToday] === 0) {
   iconWindDaily = '/images/gust.png';
   } else if ((currentCityData.daily.weather_code[indexOfToday] >= 1) && (currentCityData.daily.weather_code[indexOfToday] <= 3)) {
   iconWindDaily = '/images/windy.png';
   } else {
   iconWindDaily = '/images/sun.png';
   }

```
![image](https://github.com/AndreaNardinocchi/SETU-AssignmentWeb2/assets/51911079/364c6478-2d24-4dc6-968c-ce56fa500642)

### Modal

The modal is shown after clicking on the button 'Check more forecasts':

![image](https://github.com/AndreaNardinocchi/SETU-AssignmentWeb2/assets/51911079/34d7c8ae-55a6-4e28-92ba-2d6c02ee7996)


It has been used to shown some more dayly data and not to clutter up the page with an excessive amount of it as it is already showing quite a bit of information.
To nicely present the data to the user, a table element has been used.

![image](https://github.com/AndreaNardinocchi/SETU-AssignmentWeb2/assets/51911079/ab57b9fd-e31c-4e91-be42-3004d48d4380)


#### Source attribution

The Javascript to make this modal work has been taken from here:

https://www.geeksforgeeks.org/bulma-modal/


### Dayly Hourly Forecasts section

This 7 column section layout has been achieved by using a plain class 'column' which has filled the 'columns' container with equally-sized columns.

![image](https://github.com/AndreaNardinocchi/SETU-AssignmentWeb2/assets/51911079/d7627e5c-876a-4d53-88f5-abea978a6bbf)


This is an interesting section as each element of these cards is dynamic.
The Header for instance is a day name and changes according to the current date. I was able to achive this by using the functions below which I got from an online source and refactored to adapt it to my project goal:

```
// The below function gets the name of the current day out of variable 'date'

function getDayName(date = new Date(), locale = 'en-US') {
      return date.toLocaleDateString(locale, {weekday: 'long'});
     }

```

```
// The below function will enable the incrementation of the current day of a unit each time

 function getDayTodayPlusOne(date = new Date()) {
      const dateCopy = new Date(date.getTime());
     
      const todayPlusOne = new Date(
        dateCopy.setDate(
          dateCopy.getDate() + 1,
        ),
      );
      return todayPlusOne;
     }
     
      function getDayTodayPlusTwo(date = new Date()) {
        const dateCopy = new Date(date.getTime());
     
        const todayPlusTwo = new Date(
          dateCopy.setDate(
            dateCopy.getDate() + 2,
          ),
        );
     
      return todayPlusTwo;
     }
     
     function getDayTodayPlusThree(date = new Date()) {
      const dateCopy = new Date(date.getTime());
     
      const todayPlusThree = new Date(
        dateCopy.setDate(
          dateCopy.getDate() + 3,
        ),
      );
     
     return todayPlusThree;
     }
     
     function getDayTodayPlusFour(date = new Date()) {
     const dateCopy = new Date(date.getTime());
     
     const todayPlusFour = new Date(
      dateCopy.setDate(
        dateCopy.getDate() + 4,
      ),
     )
     
     return todayPlusFour;
     }
     
     function getDayTodayPlusFive(date = new Date()) {
     const dateCopy = new Date(date.getTime());
     
     const todayPlusFive = new Date(
      dateCopy.setDate(
        dateCopy.getDate() + 5,
      ),
     );
     
     return todayPlusFive;
     }
     
     function getDayTodayPlusSix(date = new Date()) {
     const dateCopy = new Date(date.getTime());
     
     const todayPlusSix = new Date(
      dateCopy.setDate(
        dateCopy.getDate() + 6,
      ),
     );
     
     return todayPlusSix;
     }  
   
```

I then created an array of functions and iterated them through a forEach loop:

```
  // Array of day name functions
  let currentDays= [
  getDayName(),
  getDayName(getDayTodayPlusOne()),
  getDayName(getDayTodayPlusTwo()),
  getDayName(getDayTodayPlusThree()),
  getDayName(getDayTodayPlusFour()),
  getDayName(getDayTodayPlusFive()),
  getDayName(getDayTodayPlusSix())
  ];
 
 
  // Iterating the day name functions with forEach loop
  currentDays.forEach((currentDay, index) => {
 
   const cityFocusDayHeading = document.querySelector(`#cityfocus-${index + 1}-heading`);
   cityFocusDayHeading.innerHTML = currentDay;
 
  });
```

The rest of the hourly data (icon, temperature above 2 meters and apparent temperature) also change every hour.

The code here does not seem to be following the DRY principle, unfortunately, but, after days of failed attempts to reproduce what I learned through the lectures and labs, namely the layered JavaScript architecture - MVC) I decided to move on.
However, the page does seem to work as expected as per the assignment requirements.

This section HTML is in the city-forecasts.njk partial.


#### Source attribution


Name of the days:
https://bobbyhadz.com/blog/javascript-get-day-name-from-date

Incrementing days:
https://bobbyhadz.com/blog/javascript-get-date-of-next-monday


### Go back to the (Whether) Weather Dashboard !

This component is a card embedded in a 'container' followed by a 'columns' class and it is in the 'back-to-dashboard.njk' partial.

![image](https://github.com/AndreaNardinocchi/SETU-AssignmentWeb2/assets/51911079/a9660bb5-c97b-43da-81f5-f68b05dc1be2)

## Lifestyle page

This page is basically a blog embedded into the website and users can supposedly use the search bar on the top to search for a tourist destination (I found it interesting to combine the 2 subjects).
It shows a variegated layout (lifestyle.njk).

### Search Bar

![image](https://github.com/AndreaNardinocchi/SETU-AssignmentWeb2/assets/51911079/444a89cf-b074-46c3-9a14-7c6f75bf1928)


### Destinations Video

This has been achieved by using a Bulma image component embedded into a 'box' class and a Youtube video is, in turn, embedded into it.

![image](https://github.com/AndreaNardinocchi/SETU-AssignmentWeb2/assets/51911079/c82650e5-6546-41dd-9b06-05477d77e841)


### Blog
This is a 4 column layout section made of 4 Bulma cards with images.
At the bottom of each card, there isa 'Reade more' CTA, but it is 'performative' as the link gets the user back to the dashboard.

![image](https://github.com/AndreaNardinocchi/SETU-AssignmentWeb2/assets/51911079/e9b8e792-b871-427e-b529-57ab99f674b9)


### Things to do
Her, the only difference with the above section is the 3 column layout.

![image](https://github.com/AndreaNardinocchi/SETU-AssignmentWeb2/assets/51911079/e70f2e74-d7bb-4827-a847-042db68685a8)



#### Source attribution

https://bulma.io/documentation/elements/box/
https://bulma.io/documentation/elements/image/#arbitrary-ratios-with-any-

All images have been taken from:
https://pixabay.com/


## News

This page is supposed to be a 'news' page to get travelers up to speed with the latest about tourist destinations.
The interesting part here is the split layout, as on the left side (main layout) we have a blog made of boxes succeeding one another, whereas, on the rigth side, there is an 'aside tagged' element (sidebar.njk partial).

![image](https://github.com/AndreaNardinocchi/SETU-AssignmentWeb2/assets/51911079/e128f971-e79f-4cd6-80bc-96db3ba34249)


#### Source attribution

https://bulma.io/documentation/elements/box/

All images have been taken from:
https://pixabay.com/

# Contact info

Users can contact me at andrea.nardinocchi76@gmail.com or by clicking on the website underfoot where they can find my name linking to my Linkedin profile.

# Who maintains and contributes to the project

This project will be maintained by myself only.

# Acknowledgements

My lecture John Rellis provided all info I needed to build and set up the pages by transferring knowledge of programming/web-development languages and tools such as HTML, Bulma CSS framework, Javascript, Netlify, Nunjucks, Eleventy.

Special thanks to John Rellis again, Giovanni and David O'Connor who came to my rescue when I was stuck at some point and was failing to move the needle with showing 'dynamically' the hourly data on the days of the 'Dayly Hourly Forecasts section'.

Without them, this project would have been a failure. Thank you again!!!

