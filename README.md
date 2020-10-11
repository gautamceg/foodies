# foodies

Foodies Food Delivery Service

[img-high-level-architecture]: docs/foodies_high_level_architecture.jpg

[img-sequence-diagram]: docs/sequence_diagram.jpg

## Architecture

![High Level Architecture][img-high-level-architecture]


### Module Explanation

1. Consumer App, Delivery App and Web App to access Foodies service
2. **Onboarding Service** will be responsible for onboarding delivery personal and users
3. **Fulfillment Service** - To deliver prepared food to user 
4. **Location Service** - needed to assign trips, real-time tracking of an order, payment based on distance travelled etc. This component also interact with device resources such as GPS, network, bluetooth and other sensors for location tracking, proximity detection, distance travelled measurement, activity recognition etc.
5. **Notification Service**  - To notify delivery personal and user (push notification)
6. **Listing/Catalog Service** - To list restaurant and menus
7. **Order Management Service** - To Manage order e.g add to cart, call payment service, notify restaurant,



## Sequence Diagram

![Sequence Diagram][img-sequence-diagram]

### Explanation

1. Consumer will place the order which will be processed by Order Management Service(OMS) order created, restaured confirmes the order hence consumer is notified with the successful message
2. OMS call fulfillment service to initiate delivery and assign delivery personal.
3. Fulfillment service calls location service to get confirmed delivery personal.
4. Location service returns list of top 5 delivery personal based on serving zip code, nearest proximity to restaurant and ratings.
5. Fulfillment service sends push notification to list of delivery personal who is serving in the consumer zipcode and restaurant zip code
6. Once delivery personal accepts the order then notify to user with status.
7. Location service track the progress of delivery and send key notification to user 

## Assumption

1. Details of restaurant with serving zip code is avaialble in the system
2. Details of delivery personal serving zip code, working hours, ratings avaialbe in the system
3. Prediction of delivery time is calcualted based of treffic condition, speed of delivery personal, distance and time to prepare food at restaurant. There should be dynamic update to user, any change or congestion.
4. Delivery personal will get best route details from location service

## Use case

A consumer John place the food order using Foodies mobile app from restaurant "Food Lover" and after successful payment from the John and order acceptance from restaurant a delivery personal Rohn will be assigned to delivery the food to John address.
Delivery personal will reach the restaurant while chef is preparing the food. Now delivery personal will take the prepared food from restaurant and delive to John.