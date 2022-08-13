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


# EDA

#### - Top restaurant chains in bangalore:
![Top restaurant chains](https://github.com/Himanshu584/zomato-restaurant-rating-prediction/blob/main/pics/top_restaurant_chains.png)

#### - Top rated restaurants in banagalore
![top voted restaurants](https://github.com/Himanshu584/zomato-restaurant-rating-prediction/blob/main/pics/most_voted_restaurants.png)

We can clearly see that biggest restaurant chains are not the most voted ones

#### - Restaurant offering online ordering and table booking facilities
![online_ordering](https://github.com/Himanshu584/zomato-restaurant-rating-prediction/blob/main/pics/online_orders.png) ![table_booking](https://github.com/Himanshu584/zomato-restaurant-rating-prediction/blob/main/pics/table_booking.png)

#### - Restaurant rating vs cost_for_2 based on online ordering facility
we found out that restaurants which accept online orders and whose cost of 2 plates is moderately affordable are the restaurants with highest ratings

![rate_vs_costfor2](https://github.com/Himanshu584/zomato-restaurant-rating-prediction/blob/main/pics/rate_vs_costfor2.png)

## Analysis of Location

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

## Model Building
Since this is a regression problem , we used various regression models namely : linear regression , decision tree , random forest , extra tree regressor, XGboost,etc

Extra tree regressor gave us the best result with accuracy of about 99.99% and smallest mse ( mean squared error )


