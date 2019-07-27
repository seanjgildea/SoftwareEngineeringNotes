# GOTO 2019 - REACTIVE SPRING - JOSH LONG


- Publisher< T > 
- Subscriber < T > 
- onNext( T t )
- onError( Throwable t )
- onSubscribe( Subscription sub ) 

- Publisher class
- Subscriber class
- Subscription class 
- Processor class


## Publisher Types

- Mono
- Flux


## Netty Server

- Example using Publisher REST Mapping

        @GetMapping("/reservations")
        Publisher< Reservation > reservationPublisher() {         
           return this.reservationRepository.findAll();
        }
    
    
 
 

## Lombok methods 

- @RequiredArgsConstructor

- @NoArgsConstructor

- @Log4j2 ( inject a logger field )
- log::info

## IntelliJ methods

- Generate lambda expression
- Replace with lambda

## Java 11

- var

## Mongo DB

- Reactive driver
- Natively asynchronous
- tailable queries
- transactions
- 
