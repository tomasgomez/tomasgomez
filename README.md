- 👋 Hi, I’m @tomasgomez and this is my Github, I had used mostly for my college assessment so it is a little bit outdated, also my working projects are private so it is only visible the college ones, anyway, I'm here glad to respond any question ready to develop new projects.

To describe a little bit of what I’ve done in my career, I started by creating a full microservices payment system at one of the biggest Chilean retail companies. There, I got the mission of building from 0 the backend system that was going to handle the operation of self-service checkouts. For that, we were a very young team of 4 developers and one PO. That’s where I learned about microservices, all the structure needed to handle payments, and also started managing cloud services while digging into APIs and security. Of course, that code is not public, but the product has been running in production since then (about 6 years ago) and is still handling all self-service checkout payments for Chilean and Peruvian stores (yes, still the same backend system, I have friends working there, so I know it’s the same one).

After that, I moved to another retail company, the biggest in South America, and stayed there for 10 months, adapting a backend system to handle payroll for all +34 business units across 9 countries (Wasn’t fun, I missed the “startup” environment from my previous job). That’s when my old boss called me to join the current startup I’m at now. I came in to create the first all-in-one wallet from Chile. The project obviously evolved over time and right now became a B2B business processing fiat and crypto payments, with wallets, organizations, and users managed through a dashboard and API system. Of course, I can’t share those codebases either, but I can explain how I built the startup one.

First, we started using GCP as our cloud service and later moved new projects to AWS, so yes, we run a multicloud system. Our backend stack is Golang, Mongo, and many external systems—mostly to send and receive money and process KYC against terrorist lists and others. I designed a system with 3 layers:

Layer 1: All our APIs are defined in an OpenAPI YAML file handled by a Gateway connected to a LoadBalancer, with all its related services in between (Target Group, listener, AWS Cloud Map).

Layer 2: Public services in ECS, which we named “composite,” where we handle HTTP calls from the frontend client and add business logic to reach Layer 3.

Layer 3: The core internal services, working with gRPC to connect to the composites. Only these services can connect to MongoDB—they’re blocked from public IPs—and they’re defined by business entities (User, Account, Transaction, etc.).

Both the old GCP setup and the new AWS one are deployed through pipelines with CI/CD connected from GitHub. We manage only 2 environments (I regret that decision) dev and prod. Currently, we have more than 40 microservices, of course dockerized and all running smoothly. We used Clean Architecture to define each service’s structure, and we also use internal Golang modules as libraries shared across services, to avoid repeating functions. If a function is going to be generic, it goes into one of those modules.

Because of my experience building complete systems from 0 to production (cliché but true), I know exactly every step to build and deploy applications to different cloud providers. We used Terraform at first, but then realized multicloud code wasn’t as efficient as expected, so we dropped it.

Also, I own a barbershop where—using only agents to code (mostly Cursor and ChatGPT)—I built the reservation system, all in Node and Express with TypeScript. That’s just a small hobby project where the main rule is: I don’t write a single line of code. Still, it’s a really controlled, organized, and fully functional system (handles bookings, sales, barbers, admins, and all the shop’s operations).

That’s mostly about my programming career. You can see my activity (mostly from the startup, since retail companies of course only gave me internal repos to work on).

Anything you want to know, I’m completely (depending on my schedule) available to answer.

Have a good one!
