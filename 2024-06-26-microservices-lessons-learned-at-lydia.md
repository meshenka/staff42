# Microservices Lesson Learned at Lydia in 10mn

**Sylvain Gogel** [Pro email: sylvain.gogel@lydia-app.com]

* Backend Lead/Principal Engineer
* 5 years @ Lydia
[Twitter: https://x.com/meshenka]

About me:

* ENSI Mecanical Engineer
* Aeronautical Engineer @ Aerospatiale
* Progiciel for car industry plant installation @PSA
* Web Agency CTO @ Ecedi
* Currently @ Lydia Solutions

## The Lydia story

```text
 ___       ___  ___  ________   __          __
|"  |     |"  \/"  ||"      "\ |" \        /""\
||  |      \   \  / (.  ___  :)||  |      /    \
|:  |       \\  \/  |: \   ) |||:  |     /' /\  \
 \  |___    /   /   (| (___\ |||.  |    //  __'  \
( \_|:  \  /   /    |:       :)/\  |\  /   /  \\  \
 \_______)|___/     (________/(__\_|_)(___/    \___)
```

From payment between friends to Neobanking

* 2011 **Creation** of Lydia
* 2019 all was a good old PHP **monolith**
  * with epic level of tech debt
  * 5 backend engineers
* 2020 decision was made to
  * go to the cloud,
  * go **microservices**,
  * switch to golang :boom:
* 2024 **80**-ish microservices runnings,
  * 5-10 deployments/day
  * ~45 backend engineers

## Lessons learned

Let's review **4 years** of hot takes :D

NOTE: We learned microservices the hard way!

### Consider your tradeoffs

* **Scalability vs Concistency**: transactional is hard
* /!\ What could fail will fail
  * threads crash,
  * memory and CPU exhaust,
  * network links breaks,
  * DB goes unavailable
* Polyglot is a lie

Microservices help scale **your organization**, not really your application.

### Observability is King

* Consolidated logs: ELK
* Metrics & Alerting: Prometheus
* **Distributed Tracing**: Open Telemetry
* Tag your releases in your dashboards

### Build Microservice backbone first

* Tooling, deployment/rollback flows, ...
* API Gateway
* Solid CI/CD
* Event Publisher/Consumer for asynchronous interservices communication
* **Feature Flags**
* Shared features should be asynchronous microservices
  * notifications
  * emails

### Coupling is your enemy

Study your domains boundaries very carefully.

* **Chatty services** is a symptom of wrong boundaries
* Service **Synchronous coupling** is to avoid at all costs
  * You want other services data as local projections from PubSub,
    so work on your projection setup

### Design and version your protocols

Because Backward Compatibility Breaks will happen.

* API should be **versionned**
* Async messages should be **versionned**

## Conclusion

* Should you do Microservices? **You probably do not**
* Dont do it if you dont have experienced engineers to help
* Train your team
