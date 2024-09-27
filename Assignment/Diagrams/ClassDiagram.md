```uml
@startuml
class User {
  - name : char
  - mail : string
}

class NewUser {
  + browseMovies() : void
  + browseTheatres() : void
  + signup() : void
}

class RegisterUser {
  - id : char
  - attribute1 : char
  - address : char
  - password : char
  + login() : void
  + logout() : void
  + viewMovies() : void
  + viewEvents() : void
  + makePayment() : void
  + cancelTickets() : void
}

class Movie {
  - movie_id : int
  - movie_name : string
  - movie_language : string
  - movie_duration : float
  - movie_type : string
  - movie_description : string
  + updateDetails() : void
}

class Ticket {
  - no_of_seats_available : int
  - movie_name : string
  - show_time : datetime
  - value : float
  + updateSeatAvailability() : void
}

class Events {
  - event_id : int
  - event_name : string
  - event_place : string
  - event_duration : float
  - event_description : string
  - event_type : string
  + updateDetails() : void
}

class Payment {
  - amount : float
  - card_no : float
  - cvv : int
  + conformDetails() : void
}

class Refund {
  - amount : float
  - account_no : float
  + refund() : void
}

class Admin {
  - id : char
  - name : char
  - password : char
  + addMovieRecords() : void
  + updateMovieRecords() : void
  + deleteMovieRecords() : void
  + addOffers() : void
  + addEvents() : void
  + updateEvents() : void
  + deleteEvents() : void
}

User -- NewUser : inherits
User -- RegisterUser : inherits
RegisterUser -- Movie : views
RegisterUser -- Events : views
RegisterUser -- Payment : makes
Payment -- Refund : refunds
RegisterUser -- Ticket : cancels
Admin -- Movie : updates
Admin -- Events : manages
@enduml
```
![image](https://github.com/devdrx/devd-blog/blob/master/public/classdiagram.png)
