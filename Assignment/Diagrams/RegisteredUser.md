```uml
@startuml
actor User
participant "BookMyShow App" as BMSApp
participant "Auth Service" as Auth
participant "Location Service" as Location
participant "Movie Service" as Movie
participant "Payment Gateway" as Payment
participant "Ticketing System" as Ticketing

User -> BMSApp: Open App
BMSApp -> Auth: Check if User is logged in
alt User Not Logged In
    BMSApp -> User: Show login or registration screen
    User -> BMSApp: Login or Register
    BMSApp -> Auth: Authenticate user
    Auth -> BMSApp: User logged in successfully
else User Logged In
    Auth -> BMSApp: User is already logged in
end

BMSApp -> User: Prompt to input current location
User -> BMSApp: Enter current city/location
BMSApp -> Location: Fetch available cities and validate location
Location -> BMSApp: Return valid location

BMSApp -> Movie: Fetch movies available in the selected city
Movie -> BMSApp: Return list of movies available in the city

User -> BMSApp: Select movie
BMSApp -> Movie: Fetch movie details and showtimes
Movie -> BMSApp: Return movie details and showtimes

User -> BMSApp: Select date and time
alt Showtimes Available
    BMSApp -> Ticketing: Check seat availability
    Ticketing -> BMSApp: Seats available
else Showtimes Not Available
    BMSApp -> User: Prompt user to select another date
    User -> BMSApp: Select other date
    BMSApp -> Movie: Fetch movie details and showtimes for new date
    Movie -> BMSApp: Return new showtimes
end

User -> BMSApp: Select theater and seats
BMSApp -> Ticketing: Check seat availability in selected theater
Ticketing -> BMSApp: Confirm seats are available

User -> BMSApp: Proceed to payment
BMSApp -> Payment: Initialize payment
Payment -> Payment: Process payment
Payment -> BMSApp: Payment successful
alt Payment Failed
    BMSApp -> User: Payment failed, retry or select another payment method
else
    BMSApp -> Ticketing: Confirm booking and issue tickets
    Ticketing -> BMSApp: Booking confirmed, generate ticket
    BMSApp -> User: Show booking confirmation and ticket details
end
@enduml
```
![image](https://github.com/user-attachments/assets/0c81ade7-3fd3-4e0e-8f5e-ec497a8713c4)
