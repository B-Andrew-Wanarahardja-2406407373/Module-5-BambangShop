# BambangShop Publisher App
Tutorial and Example for Advanced Programming 2024 - Faculty of Computer Science, Universitas Indonesia

---

## About this Project
In this repository, we have provided you a REST (REpresentational State Transfer) API project using Rocket web framework.

This project consists of four modules:
1.  `controller`: this module contains handler functions used to receive request and send responses.
    In Model-View-Controller (MVC) pattern, this is the Controller part.
2.  `model`: this module contains structs that serve as data containers.
    In MVC pattern, this is the Model part.
3.  `service`: this module contains structs with business logic methods.
    In MVC pattern, this is also the Model part.
4.  `repository`: this module contains structs that serve as databases and methods to access the databases.
    You can use methods of the struct to get list of objects, or operating an object (create, read, update, delete).

This repository provides a basic functionality that makes BambangShop work: ability to create, read, and delete `Product`s.
This repository already contains a functioning `Product` model, repository, service, and controllers that you can try right away.

As this is an Observer Design Pattern tutorial repository, you need to implement another feature: `Notification`.
This feature will notify creation, promotion, and deletion of a product, to external subscribers that are interested of a certain product type.
The subscribers are another Rocket instances, so the notification will be sent using HTTP POST request to each subscriber's `receive notification` address.

## API Documentations

You can download the Postman Collection JSON here: https://ristek.link/AdvProgWeek7Postman

After you download the Postman Collection, you can try the endpoints inside "BambangShop Publisher" folder.
This Postman collection also contains endpoints that you need to implement later on (the `Notification` feature).

Postman is an installable client that you can use to test web endpoints using HTTP request.
You can also make automated functional testing scripts for REST API projects using this client.
You can install Postman via this website: https://www.postman.com/downloads/

## How to Run in Development Environment
1.  Set up environment variables first by creating `.env` file.
    Here is the example of `.env` file:
    ```bash
    APP_INSTANCE_ROOT_URL="http://localhost:8000"
    ```
    Here are the details of each environment variable:
    | variable              | type   | description                                                |
    |-----------------------|--------|------------------------------------------------------------|
    | APP_INSTANCE_ROOT_URL | string | URL address where this publisher instance can be accessed. |
2.  Use `cargo run` to run this app.
    (You might want to use `cargo check` if you only need to verify your work without running the app.)

## Mandatory Checklists (Publisher)
-   [:D] Clone https://gitlab.com/ichlaffterlalu/bambangshop to a new repository.
-   **STAGE 1: Implement models and repositories**
    -   [:D] Commit: `Create Subscriber model struct.`
    -   [:D] Commit: `Create Notification model struct.`
    -   [:D] Commit: `Create Subscriber database and Subscriber repository struct skeleton.`
    -   [:D] Commit: `Implement add function in Subscriber repository.`
    -   [:D] Commit: `Implement list_all function in Subscriber repository.`
    -   [:D] Commit: `Implement delete function in Subscriber repository.`
    -   [ ] Write answers of your learning module's "Reflection Publisher-1" questions in this README.
-   **STAGE 2: Implement services and controllers**
    -   [:D] Commit: `Create Notification service struct skeleton.`
    -   [:D] Commit: `Implement subscribe function in Notification service.`
    -   [:D] Commit: `Implement subscribe function in Notification controller.`
    -   [:D] Commit: `Implement unsubscribe function in Notification service.`
    -   [:D] Commit: `Implement unsubscribe function in Notification controller.`
    -   [ ] Write answers of your learning module's "Reflection Publisher-2" questions in this README.
-   **STAGE 3: Implement notification mechanism**
    -   [:D] Commit: `Implement update method in Subscriber model to send notification HTTP requests.`
    -   [:D] Commit: `Implement notify function in Notification service to notify each Subscriber.`
    -   [:D] Commit: `Implement publish function in Program service and Program controller.`
    -   [:D] Commit: `Edit Product service methods to call notify after create/delete.`
    -   [ ] Write answers of your learning module's "Reflection Publisher-3" questions in this README.

## Your Reflections
This is the place for you to write reflections:

### Mandatory (Publisher) Reflections

#### Reflection Publisher-1
1. As far as i know, it can be done without an interface, or trait as it's called here in rust. So far, here in BambangShop we only have a single kind of product and a single kind of subscriber. It wouldn't really matter. But if later on there are different kinds of subscribers like premium tiers or whatnot, it would be better to use interfaces so it can be written in a simpler way.  

2. I think it's possible. Turns out Vec can grow automatically when the number of data exceeds it's size, so no need to worry about that. the only thing in favor of using DashMap i can think of is performance, as using Vec would need to iterate through the whole thing to find a particular content unlike Maps which are generally faster because it hashes instead.

3. Not gonna lie, i'm confused by this question. I was under the impression that the singleton pattern means there's that singular instance inside a class that can be accessed by any instance of that class. and this DashMap fits that description. So asking if we still need DashMap or if we can implement the Singleton pattern instead, which implies only one can be chosen, makes me confused as i think both are implemented already. My lack of understanding aside, we probably still need DashMap to make it thread safe.

#### Reflection Publisher-2

#### Reflection Publisher-3
