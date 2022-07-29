# zomato-restaurant-rating-prediction
dataset used = https://www.kaggle.com/datasets/himanshupoddar/zomato-bangalore-restaurants?resource=download

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


## EDA

#### - Top restaurant chains in bangalore:
![Top restaurant chains](https://github.com/Himanshu584/zomato-restaurant-rating-prediction/blob/main/pics/top_restaurant_chains.png)
These are the biggest and most popular restaurant chains in bangalore and hence , these restaurants being so popular are prone to have a high rating

#### - Restaurant offering online ordering and table booking facilities
![online_ordering](https://github.com/Himanshu584/zomato-restaurant-rating-prediction/blob/main/pics/online_orders.png) ![table_booking](https://github.com/Himanshu584/zomato-restaurant-rating-prediction/blob/main/pics/table_booking.png)
