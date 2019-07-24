[<< Back to Table of Contents](README.md)

# Bootiful TDD By Josh Long
- https://www.youtube.com/watch?v=E87XhgYBM-Y
- Desire to stay in the zone / dopamine / video games 
- In order to take advantage of this fast movement, you need safety
- We want validation that everytime we introduce a change
- We want to move quickly and safely to production, early and often

## Bob Martins 3 laws of TDD
1. Write production code only to make a failing unit test pass.
2. Write only enough of a unit test to fail.
3. Write only enough production code to make the failing unit test pass.


## The goal: Optimize for fast feedback

- Stay perpetually in the zone
- We want to enjoy that sense that we're continously moving forward
- That desire to constantly have feedback

## When you write your tests first:

- You write code that can be tested


## Steps

- Create the test
- Instantiate a class that doesnt exist
- Create the non-existant class ( Auto generate here )
- Instantiate example classes and use Matcher ( BaseMatcher ) 22:27

## Write an Entity Test next

- Prove that the mapping is correct
- Prove that I can talk to the DB
- Prove that I can make queries and the id is not null
-

## Write an [Class]HTTPTest

- Inject the WebTestClient
- WebTestClient expects certain responses and statuses
