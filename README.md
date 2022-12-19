# Spring-boot-Microservice

-Currency Exchange Service
  -http://localhost:8000/currency-exchange/from/USD/to/INR

-Currency Conversion Service
  -http://localhost:8100/currency-conversion/from/USD/to/INR/quantity/10
  -http://localhost:8100/currency-conversion-feign/from/USD/to/INR/quantity/10

-Eureka
  -http://localhost:8761/

-Zipkin
  -http://localhost:9411/

-API GATEWAY
  -http://localhost:8765/currency-exchange/from/USD/to/INR
  -http://localhost:8765/currency-conversion/from/USD/to/INR/quantity/10
  -http://localhost:8765/currency-conversion-feign/from/USD/to/INR/quantity/10
  -http://localhost:8765/currency-conversion-new/from/USD/to/INR/quantity/10

Spring Boot & Spring Cloud
Service Registry using Eureka Naming Server
Load Balancing with Spring Cloud LoadBalancer 
API Gateway with Spring Cloud Gateway
Circuit Breaker with Resilience4j 
Distributed Tracing with Zipkin
