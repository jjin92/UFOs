# UFOs

## Overview
Use JavaScript, HTML, CSS and Bootstrap to create a website with a dynamic data table. Users can browse various UFO sightings records and filter through five different specifications.

## Tools and Resources
*Data resource*
- [UFO sightings record in JavaScript](https://github.com/jjin92/UFOs/blob/master/static/js/app.js)

*Software*
- JavaScript, D3, HTML, CSS, Bootstrap

## Solution
*1. HTML webpage and bootstrap*
- Use Bootstrap and css to style the content layout and background color. 
- Add `id` to each user input field, so it can be referenced in the Javascript. 
- Add `id` to the filter button, so it can be referenced by d3.js to listen to the event
- Create place holder for the dynamic table.

*2. CSS*
- Adjust all `<body />` text to white.
- Beautify jumbotron with select image

*3. JavaScript*
- Save all data records into a variable
- Get table reference using d3 `var tbody = d3.select("tbody");`
- Create a `buildTable` function using a forEach loop
    - Create a row for each object in data
    - Create a cell for each value in the row
- Create a `filters` variable to hold all filters from user input
- Create a `updateFilters` function to update the filters list and values
    - Use d3 to capture the input field from user
    - If a filter field receives input, add the Key:Value pair to `filters` list
    - If no input in that filter field, remove the Key:Value pair from `filters`
    - In this project, we have five filters: Date, City, State, Country, and Shape
    - Call `filterTable` function to build the table with filtered data
- Create a `filterTable` function which takes in one argument of filter
    - Loop through all the data and keep only the ones that matches the filter `filteredData = filteredData.filter((row) => row[key] === filtersObject[key]);`
    - Rebuild the table by calling `buildTable` function with the filtered data
- Reference the filter button with its `id`; use d3 to listen to the `click` event and trigger the `updateFilter` function
- Make sure the table is built with unfiltered data when the page loads

## Further development
There are many potential areas to work on to improve the UX. For example:
- The current filter system allows only one input value for each field. We could let the user input multiple values, eg. `state: CA, NY, WA`.
- We could add a drop-down menu/list, or have auto-fill function to facilitate the search experience.
- After the table is filtered, an `export to csv` function would be very helpful for research purpose. 

## Website Preview
The screenshot below shows the search result with four filters applied.

![website_preview](https://github.com/jjin92/UFOs/blob/master/preview.png)