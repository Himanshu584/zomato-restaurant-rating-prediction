# zomato-restaurant-rating-prediction
dataset used = https://www.kaggle.com/datasets/himanshupoddar/zomato-bangalore-restaurants?resource=download

linked github repo (application building) :- https://github.com/Himanshu584/restaurant-rating-app

deployed version of app :- https://himanshu584-restaurant-rating-app-app-6nusqf.streamlitapp.com/

STAGES OF PROJECT :
1. Preprocessing & Feature engeenering
2. EDA 
3. Model Building 
4. Model testing
5. Building interface


There are 17 columns in out dataset namely :  `'url', 'address', 'name', 'online_order', 'book_table', 'rate', 'votes',
       'phone', 'location', 'rest_type', 'dish_liked', 'cuisines',
       'approx_cost(for two people)', 'reviews_list', 'menu_item',
       'listed_in(type)', 'listed_in(city)'`
       
       `url` - It contains the url to indivisual restaurants website
       `address` - It as the name suggests comtains address of restaurants in bangalore
       `name` - name of the restaurant
       `online_order` - weather a restaurant accepts online orders or not
       `book_table` - weather a restaurant provides online table booking facility or not
       `rate` - rating of the restaurant (column to be predicted)
       `votes` - number of votes given to a restaurant by users
       `phone` - contact number of a restaurant
       `location` - location of restaurant
       `rest_type` - restaurant type (casual dining , quick bites , etc)
       `dish_liked` - dishes that got upvotes /likes 
       `cuisines` - cuisines offered in restaurant (indian, chinese,thai,etc)
       `approx_cost(for two people)` - cost per 2 plates in a restaurant
       `reviews_list` - indivisual reviews on a restaurant
       `menu_item` - list of items served in restaurant
       `listed_in(type)` - type of restaurant (buffet,food truck,dining ,etc)
       `listed_in(city)` - city in which the restaurant is listed
       

# Preprocessing & Data Cleaning
For preprocessing and data cleaning , we first found what columns will add value to our analysis and model building and which not.
At first glance , we could see that url, address , phone, dish_liked, reviews_list, menu_item are of no use to us so we drop these columns.
further we checked for data types and corrected the needed ones (eg: we found that rating was string and needed to be converted to float)
we checked for percentages of missing values , we found `rating` had many missing values which could not be ignored. so we had 2 approaches
1. we drop missing values : 
       by droping missing values we found that distribution was normal 
       ![rate_null_dropped](https://github.com/Himanshu584/zomato-restaurant-rating-prediction/blob/main/pics/rate_null_removed.png)
 
 2. we fill the null values with median
       ![rate_null_filled](https://github.com/Himanshu584/zomato-restaurant-rating-prediction/blob/main/pics/rate_null_filled.png)
       
 By looking at these distribution curves , we see that it is more favourable to drop the null values than filling them with median.
 
 Further, main preprocessing state involved encoding the catagorical variables . For this we used the `Label-Encoder` technique and not `One-Hot encoding` because
 using one hot encoding would increase the dimentions of our dataset tremendously.
 we then created a encoded datatable that could be used to map the encodings to their respective original catagory. 

# EDA

#### - Top restaurant chains in bangalore:
![Top restaurant chains](https://github.com/Himanshu584/zomato-restaurant-rating-prediction/blob/main/pics/top_restaurant_chains.png)

#### - Top rated restaurants in banagalore
![top voted restaurants](https://github.com/Himanshu584/zomato-restaurant-rating-prediction/blob/main/pics/most_voted_restaurants.png)

We can clearly see that biggest restaurant chains are not the most voted ones, so lets find what factors lead to high voting and rating

#### - Restaurant offering online ordering and table booking facilities
![online_ordering](https://github.com/Himanshu584/zomato-restaurant-rating-prediction/blob/main/pics/online_orders.png) ![table_booking](https://github.com/Himanshu584/zomato-restaurant-rating-prediction/blob/main/pics/table_booking.png)

#### - Restaurant rating vs cost_for_2 based on online ordering facility
we found out that restaurants which accept online orders and whose cost of 2 plates is moderately affordable are the restaurants with highest ratings

![rate_vs_costfor2](https://github.com/Himanshu584/zomato-restaurant-rating-prediction/blob/main/pics/rate_vs_costfor2.png)


#### location with highest number of restaurant
![location_restaurant_max](https://github.com/Himanshu584/zomato-restaurant-rating-prediction/blob/main/pics/location_restaurants_max.png)

#### location with highest & lowest average cost for 2
![location_highest_avg_cost](https://github.com/Himanshu584/zomato-restaurant-rating-prediction/blob/main/pics/location_highest_average_cost.png)
       ![location_lowest_avg_cost](https://github.com/Himanshu584/zomato-restaurant-rating-prediction/blob/main/pics/location_lowest_average_cost.png)

#### Most Popular cuisines of bangalore
![most_popular_cuisines](https://github.com/Himanshu584/zomato-restaurant-rating-prediction/blob/main/pics/most_popular_cusines.png)

#### votes vs online ordering facility
![votes_vs_online](https://github.com/Himanshu584/zomato-restaurant-rating-prediction/blob/main/pics/votes_onlineorders.png)
we can clearly see the restaurants with online ordering facility are much highly voted than others with no online ordering facility

#### price vs online ordering facility
![price_vs_online](https://github.com/Himanshu584/zomato-restaurant-rating-prediction/blob/main/pics/price_onlineorder.png) 
we can see that restaurants which do not genrerally provide online ordering facility have much higher price as compared to ones that provide online ordering facilities

While performing EDA we found out that major factors that led to high rating of restaurants were :
* wether a restaurant has online ordering and table booking facilty or not
* whether the price of the restauarant is affordable to most public 
* type of restaurant, type and type of cuisines
* location , city 
* number of votes given to a particular restaurant

we encoded the catagorical variables with label encoder because if we used One-hot encoding , it would have increased our dimentions enormously

# Model Building
Since this is a regression problem , we used various regression models namely : linear regression , decision tree , random forest , extra tree regressor, XGboost,etc

`Extra tree regressor` gave us the best result with accuracy of about 99.99% and smallest mse ( mean squared error )

# Model saving and loading
we used the `Pickle` library for saving and loading this model and encoded dataframe





# application building
The user interface is built in streamlit library that has various components like selectbox, textfield that helps make applications easily.
we made the interface such that user can select from catagorical variables and enter the numeric fields . these fields after getting encoded from encoding dataframe in backend if needed will be converted into a 2-d list which will pass into the pickled model for futher processing. after the prediction is made , it will be reflected onto users window.

# application deployment
this app is deployed on `streamlit share cloud platform`.

