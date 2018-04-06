# Final Project Proposal

Your assignment this week is to write a detailed proposal for your final
project. In proposing your final, try to address each of the following
areas.

## Problem / Question

Applications are ultimately just tools. What problem or question does
your application attempt to resolve or grapple with? How does your
application speak to this problem/question?

The idea of this project comes from a exploratory project that I did during my summer internship at SFCTA where I was trying to validate the OD travel time estimation from San Francisco Bay Area’s regional travel demand model using alternative data sources such as Google Maps API.

The goal of this project is to develop an application that could be used internally at the transportation agency to fetch real-time or designated time’s OD travel time and compare with SF-CHAMP model output visually.

## The data

Geospatial applications are all about working with data. What datasets
would you plan/like to use? If the data you'll be working with isn't
already stored in a way that you can use, how will you be storing your data?
(If it is too large for a javascript application, using a backend might
be necessary)

Ideally, this application should be able to map out each link of the SF-CHAMP model, and compare with Google’s real time/interpolated data. However due to time constraint and API’s access limit, I’ve decided at this stage I will mainly focusing on the travel time validation of 245 CPM segments (as mapped out in the Mid-term project). Potential validation data sources are Goole Maps Direction API and Google Maps Distance Matrix API. [I have difficulty in this part]

## Technologies used

Which technologies covered in class (or discovered on your own!) do you
plan to use? How do you anticipate using each of these technologies?

Review the APIs/online examples of leaflet, turf, jQuery, underscore (or
any library not explicitly covered in class) for functions/uses which
you'd like to explore. Briefly describe how you might use them.

The next step is to convert the CMP link nodes to compatible format as API query input (origin and destination), and test with different parameters. Potential technologies include Google Maps API, leaflet, turf, jQuery and underscore.

## Design spec

#### User experience

At a high level, how do you expect people to use your application?
- Who are the users?
- What do they gain from your application' use?
- Are there any website/application examples in the wild to which you can compare your final?

I expect this application to be primarily used as an internal application for travel demand modelers validation purpose. So far there has been an interactive map built to visualize the data in the agency’s data warehouse (http://congestion.sfcta.org/). However there has not been an easy tool to fetch external data for model validation purpose. Potentially it could be used by the public to see the real-time travel time on these CMP segments.

#### Layouts and visual design

So far, we've built all our applications with a side bar for
representing non-map content and navigation. This is not the only
successful design. Extra content could be displayed in a top bar,
through modals, through side bars on both sides, and any combination of
these as well as a number not mentioned. Try to describe your
application's visual layout. Conceptually (no need for extensive CSS
here), what will this design require?

The user interface would be simple and clear with a map and sidebar that allows the user to filter the scope of CMP segments (for example, different time of day, facility type, area type, etc.). It should also be able to plot out the validation charts with statistics such as RMSE and percentage error.

## Anticipated difficulties

Thinking about weaknesses can be useful. What do you anticipate being
most difficult about this project? How will you attempt to cope with
these difficulties? For example, asynchronous behavior (ajax, events)
are hard to use and think about. Global variables are a strategy for
coping with that difficulty by breaking data out of the asynchronous
context.

One big challenge of using Google Maps API data as I tested out earlier is to set the departure time parameter in the API query. Since our CMP data covers AM and PM periods, I will have to query at least at two points. It is still unclear how Google’s estimation algorithm works since the departure time could only be set to NOW or a future time point (which might not reflect actual traffic condition). I will still have to see if the real-time data make sense (this could be tested by manually query each hour for several OD pairs in a day, and set the departure time to NOW; only Google Maps Direction API instead of Distance Matrix API might work). [reference: Hanna, R., Kreindler, G., & Olken, B. A. (2017). Citywide effects of high-occupancy vehicle restrictions: Evidence from “three-in-one” in Jakarta. Science, 357(6346), 89–93. https://doi.org/10.1126/science.aan2747].

## Missing pieces

We've only managed to scratch the surface of the available technologies
by which you could construct an application. What use-cases haven't we covered
that you think would be useful? What technologies not covered seem exciting to
you (you don't necessarily have to fully understand what they're for,
this is a chance for you to get our help interpreting a technology's
purpose/usage).

I still have little sense in terms of what is the best way to host the application, store data, spatially join the API data to CMP segments. I am also not sure if this is more of a data management problem that might take more time than designing the application. I appreciate any suggestions!

## References
Hanna, R., Kreindler, G., & Olken, B. A. (2017). Citywide effects of high-occupancy vehicle restrictions: Evidence from “three-in-one” in Jakarta. Science, 357(6346), 89–93. https://doi.org/10.1126/science.aan2747
