# Initialization Lab


## 1: Structs Review

Download the resources at the link below:

https://developer.apple.com/go/?id=app-dev-swift-student (Links to an external site.)


Open the folder titled "2 - Introduction to UIKit" then open the folder titled "3 - Structures".  Open the Playground there, and work through the exercises.
```swift
struct GPS{
var longitude = 0.0
var latitude = 0.0
}
var somePlace = GPS()
print(somePlace)
somePlace = GPS(longitude: 0.125226, latitude: 51.514004)
print(somePlace)

struct Book{

var title = ""
var author = ""
var pages = 0
var prices = 0.0
}

var favoriteBook = Book(title: "Lightning Thief", author: "Rick Riordan", pages: 400, prices: 18.95)
print("My favorite book \(favoriteBook.title) by \(favoriteBook.author) has \(favoriteBook.pages) pages and only cost as low as \(favoriteBook.prices)")
```
```swift
struct RunningWorkout{
var distance = 0.0
var time = 0.0
var elevation = 0.0
}

var firstRun = RunningWorkout()
firstRun.distance = 2396
firstRun.elevation = 94
firstRun.time = 15.3
print(firstRun)
```
```swift
struct GPS{
var longitude: Double
var latitude: Double

init(longitude: Double, latitude: Double) {
self.latitude = latitude
self.longitude = longitude
}
}
var somePlace = GPS(longitude: 0.125226, latitude: 51.514004)
print(somePlace)

struct Book{

var title: String
var author: String
var pages: Int
var prices: Double

init(title: String, author: String, pages: Int, prices: Double) {
self.title = title
self.author = author
self.pages = pages
self.prices = prices
}
}

var favoriteBook = Book(title: "Lightning Thief", author: "Rick Riordan", pages: 400, prices: 18.95)
print("My favorite book \(favoriteBook.title) by \(favoriteBook.author) has \(favoriteBook.pages) pages and only cost as low as \(favoriteBook.prices)")

struct Height{
var heightInInches: Double
var heightInCentimeters: Double

init(inches: Double) {
self.heightInCentimeters = inches * 2.54
self.heightInInches = inches
}


}

var someonesHeight = Height(inches: 65)
print(someonesHeight.heightInCentimeters)
print(someonesHeight.heightInInches)

var myHeight = Height(inches: 65)
print(myHeight.heightInCentimeters)
print(myHeight.heightInInches)
```
```swift
struct User{
var name: String
var age: Int
var height: Double
var weight: Double
var activityLevel: Int

init(name: String, age: Int, height: Double, weight: Double, activityLevel: Int) {
self.name = name
self.age = age
self.height = height
self.weight = weight
self.activityLevel = activityLevel
}
}

var user1 = User(name: "tom", age: 99, height: 65, weight: 120, activityLevel: 5)

struct Distance{
var meters: Double
var feet: Double

init(value: Double) {
self.meters = value * 3.28084
self.feet = value
}
}

var test = Distance(value: 1600)
print(test.meters)
```
```swift
struct Book {
var title: String
var author: String
var pages: Int
var price: Double

init(title: String, author: String, pages: Int,price: Double) {
self.title = title
self.author = author
self.pages = pages
self.price = price
}
}

let description = Book(title: "bla", author: "blaaa", pages: 5, price: 1)
print(description)

struct Post {
var message: String
var likes: Int
var numberOfComments: Int

init(message: String, numberOfComments: Int, likes: Int) {
self.message = message
self.numberOfComments = numberOfComments
self.likes = likes
}
mutating func like(){
likes += 1
}
}

var test = Post(message: "bla", numberOfComments: 4, likes: 2)
print(test.likes)
test.like()
print(test.likes)
```
```swift
struct RunningWorkout {
var distance: Double
var time: Double
var elevation: Double

func postWorkOutStats(){
print("Ran \(distance) meters within \(time) minutes and elevation at \(elevation)")
}
}

let test = RunningWorkout(distance: 50.0, time: 5, elevation: 5.0)
print(test.postWorkOutStats())

struct Steps {
var steps: Int
var goal: Int

mutating func takeStep(){
steps += 1
}
}
var walk = Steps(steps: 5, goal: 10)
print(walk.steps)
walk.takeStep()
print(walk.steps)
```
## 2: Classes and Inheritance

Open the folder titled "2 - Introduction to UIKit" then open the folder titled "4 - Classes and Inheritance".  Open the Playground there, and work through the exercises.
```swift
class Spaceship{
var name: String
var health = 100
var position = 0

init(name: String){
self.name = name
}
func moveLeft(){
self.position = position - 1
}
func moveRight(){
self.position = position + 1
}
func wasHit(){
self.health = health - 5
if health <= 0{
print("Sorry you ship was hit too many times")
}
}
}
let falcon = Spaceship(name: "Falcon")
print(falcon.name)
falcon.moveLeft()
falcon.moveLeft()
falcon.moveRight()
print("position: \(falcon.position)")

falcon.wasHit()
falcon.wasHit()
print("health: \(falcon.health)")
```
```swift
class Spaceship {
var name: String = ""
var health = 100
var position = 0

func moveLeft() {
position -= 1
}

func moveRight() {
position += 1
}

func wasHit() {
health -= 5
}
}

class Fighter: Spaceship{
var weapon: String
var remainingFirePower = 5

init(weapon:String, remainingFirePower: Int, name: String, health: Int, psition: Int){
self.weapon = weapon
self.remainingFirePower = remainingFirePower
}

func fire(){
if remainingFirePower > 0 {
remainingFirePower -= 1
}
else{
print("you have no more fire power")
}
}
}

var destroyer = Fighter(weapon: "laser", remainingFirePower: 10, name: "Destroyer", health: 90, position: 0)

print(destroyer.position)
destroyer.moveLeft()
destroyer.moveRight()
//falcon does not inherit stuff from its subclass it doesnt work that way
destroyer.fire()
destroyer.fire()
destroyer.fire()
destroyer.fire()
print(destroyer.remainingFirePower)
```
```swift
class Spaceship {
var name: String = ""
var health = 100
var position = 0

init(name: String, health: Int, position: Int) {
self.name = name
self.health = health
self.position = position
}
func moveLeft() {
position -= 1
}

func moveRight() {
position += 1
}

func wasHit() {
health -= 5
}
}

class Fighter: Spaceship {
var weapon = ""
var remainingFirePower = 5

init(name: String, health: Int, position: Int, weapon: String, remainingFirePower: Int ) {

super.init(name: name, health: health, position: position)
}

func fire() {
if remainingFirePower > 0 {
remainingFirePower -= 1
} else {
print("You have no more fire power.")
}
}
}

class ShieldedShip: Fighter{
var shieldStrength = 25

init(name: String, health: Int, position: Int, weapon: String, remainingFirePower: Int, shieldStrength: Int ) {

super.init(name: name, health: health, position: position, weapon: weapon, remainingFirePower: remainingFirePower)
}
override func wasHit() {
if shieldStrength > 0{
shieldStrength -= 5
}
else{
health -= 5
}
}
}

var defender = ShieldedShip(name: "Defender", health: 5, position: 5, weapon: "canon", remainingFirePower: 5, shieldStrength: 0)
defender.moveRight()
print(defender.position)
defender.fire()
print(defender.remainingFirePower)
defender.wasHit()
print(defender.shieldStrength)
print(defender.health)
print(defender.name)
```
```swift
var falcon = Spaceship(name: "Falcon", health: 100, position: 0)
var sameShip = falcon
print(sameShip.position)
print(sameShip.position)
sameShip.moveLeft()
print(sameShip.position)
print(sameShip.position)
// yes the positions are the same because it is a class and classes pass by reference so both values will change
```

## BONUS: Actor mini-project

Complete each of the following exercises by creating a new Command Line App in Xcode.  Classes and structs allow us to separate out our code into multiple different files.  In you main.swift file, copy and paste the code at the link below.

 https://gist.github.com/benstone1/75ae3cf24c8cb2ade792b9c66e79ee5c



## 3

Create a new file and name it "Movie.swift".  Make sure to save it right below your main.swift file.
```swift
class Movie{
var name: String
var year: Int
var genre: String
var cast: [String]
var description: String

init(name: String, year: Int, genre: String, cast: [String], description: String){
self.name = name
self.year = year
self.genre = genre
self.cast = cast
self.description = description
}
}
```

Inside of the Movie.swift file, create a class called Movie that has properties for name (String), year (Int), genre (String), cast ([String]), and description (String).


Inside of main.swift, populate an array of Movies converted from the array of dictionaries in the gist above.

## 4

Then, for each movie in the Movie array, print the name of each movie and associated cast on a single line. Be sure not to print the array of cast members, only the string elements.



Correct Output Examples:

Minions: Sandra Bullock, Jon Hamm, Michael Keaton
Shrek: Mike Myers, Eddie Murphy, Cameron Diaz


Incorrect Output Examples (printing an array instead of the actors joined together as a String):

Minions: ["Sandra Bullock", "Jon Hamm", "Michael Keaton"]
Shrek: ["Mike Myers", "Eddie Murphy", "Cameron Diaz"]


## 5

Let's refactor our Movie class with what we learned today.



Create a failable convenience initializer convenience init?(with dict: [String:Any]) for the Movie class that takes in a dictionary, and uses the values of the input dictionary to initialize a Movie object.



Go back to the for loop in main.swift where we iterate through the movies array. Rewrite the body of the loop such that it creates a Movie object for each dictionary in the movies array using the new convenience initializer.


## 6

Repeating the same process you used to make the Movie.swift file, create files named:

- Person.swift
- Actor.swift


In Person.swift, create a class named Person with

- A name of type String
- A birthYear of type Int
- A deathYear of type Optional Int

In Actor.swift, create a class named Actor that

- Inherits from Person
- Has a breakoutYear of type Int
- Has a breakoutRole of type String

Rewrite your Movie class to have its case property be an array of Actors instead of Strings.

## 7

Repeating the same process you used to make the Movie.swift file, create a file named:

Genre.swift

In Genre.swift, create an enumeration with raw String values with the following cases:

- animation
- action
- drama


Rewrite your Movie class to have its genre property be of type Genre instead of String.


## 8

Refactor your code and create an area of your improved Movie class out of the array of dictionaries.

Then, use your new array to complete each of the following questions:

a. Print the name of the first movie.

b. Print a list of all movie names on one line.

c. Print a list of all movie years and names (each on a new line) as follows:

2015: Minions
2001: Shrek

d. Print the title of each movie and add an appropriate emoji to represent its genre.

e. Print out the title of each movie and all of the actors that were older than 40 when then movie was made.
