# dart-cheat-sheet

A curated list of awesome stuff needed to get started with your flutter development journey

[![Awesome](https://cdn.rawgit.com/sindresorhus/awesome/d7305f38d29fed78fa85652e3a63e154dd8e8829/media/badge.svg)](https://github.com/sindresorhus/awesome) 

![Branch master](https://img.shields.io/badge/branch-master-brightgreen.svg?style=flat-square)[![GitHub license](https://img.shields.io/badge/license-MIT-blue.svg)](https://raw.githubusercontent.com/temidtech/dart-cheat-sheet/master/LICENSE)

 ## Table of Contents

* [String interpolation](#string-interpolation)
* [Functions](#functions)
* [Parsing](#parsing)
* [List Arrays](#list-arrays)
* [Lambda Functions](#lambda-functions)
* [Null-aware Operators](#null-aware-operators)
* [Conditional Property Access](#conditional-property-access)
* [Collections Literals](#collections-literals)
* [Arrow Syntax](#arrow-syntax)
* [Iterations](#iterations)
* [Map](#map)
* [Variables](#variables)
* [Class](#class)
* [Getters and Setters](#getters-and-setters)
* [Futures: Async and Await](#future-async-await)
* [JSON and serialization](#json-and-serialization)
* [Reading and decoding a file](#Reading-and-decoding-a-file)

## String interpolation

Every language has it's own way of interpolating two ore more words or characters. In dart, you can put value of an expression inside a string as follows:

###  Example

 

``` dart
    int x=6;
    int y=2;
    String sum = '${x+y}';          // result is 8
    String subtraction = '${x-y}';  // result is 4
    String upperCase = '${"hello".toUpperCase()}'; // result is HELLO
    String concatXY = '$x$y'; // result is '62'
 ```

 ## Functions
Dart lang is an OOL(Object-oriented language), In this language, functions are objects and have a type, Function. This implies that functions can be assigned to 
variables or passed as args to other functions. Interestingly, you can also call an instance of a class as if it were a fuction. That's awesome, right?

###  Example

 

``` dart
    String fullName(){
        String firstName = "Temidayo";
        String lastName = "Adefioye";
        return '$firstName $lastName'; // returns 'Temidayo Adefioye'
    }
 ```

 

``` dart
    int length(String text){
        return text.length; // returns length of text
    }
 ```

 The above function can be rewritten in a more concise way:

  

``` dart
    int length(String text) => return text.length; // returns length of text
 ```

 The above approach is applicable where functions contain just ONE expression. This is also referred to as shorthand syntax.

 ## Parsing

Parsing a string to a number such as integer and double is very key. As a developer, often times I need to convert(parse) a string value
coming from a server-side to a number, tryParse method comes in handy. Take a look at this code snippet:

###  Example

 

``` dart
    var a = "121";
    var b = "120.56";
    var c = "100.a12";         
    var d = "abc";
    int parseA = int.tryParse(a); // result is 121
    double parseB = double.tryParse(b); // result is 120.56
    double parseC = double.tryParse(c); // result is null (that string contains invalid number)
    double parseD = double.tryParse(d); // result is null (that string contains invalid number)
 ```

  ## List Arrays

Perhaps the most common collection in nearly every programming language is the array or ordered set of objects. Please note that Dart arrays are Lists.

###  Example

 

``` dart
    var numList = [1,2,3,5,6,7];
    var countryList = ["Nigeria","United States","United Kingdom","Ghana","IreLand","Germany"];
    String numLength = numList.length; // result is 6
    String countryLength = countryList.length; // result is 6
    String countryIndex = countryList[1]; // result is 'United States'
    String numIndex = numList[0]; // result is 1

    countryList.add("Poland"); // Adds a new item to the list.

    var emailList = new List(3); // Set a fixed list size 
    var emailList = new List<String>(); // instance of a list of type String

 ```

 ## Lambda Functions

Lambda functions provide you with a short and concise way of representing small functions. They are also referred to as Arrow functions. In dart, if you need to write quick throw away functions without necessarily naming them, lambda fucntion is all you need. With the power of this function you can do the following and more:

###  Example

 

``` dart
    var numList = new List<int>.generate(5,(i) => i);
    print(numList); //result: {0,1,2,3,4}
    var loans = numList.map( (n) => "\#$n").toList();
    print(loans); // result: {#0, #1, #3, #4}

    printMsg()=> print("Hello world");

    // You can declare a state function this way in flutter
     _DashboardState createState() => _DashboardState(); 

    // How about creating a widget using lambda?
    Card makeCard(Asset assetViewModel) => Card(
          elevation: 8.0,
          margin: new EdgeInsets.symmetric(horizontal: 10.0, vertical: 6.0),
          child: Container(
            decoration: BoxDecoration(color: Colors.white),
            child: makeListTile(assetViewModel), // where makeListTile is a custom widget created already
          ),
    );

 ```

  ## Null-aware Operators

Handling null exceptions in app development is very essential, as this allows you to create a seamless experience for your app users. Dart provides you with some handy operators for dealing with values that might be null. One is the ??= assignment operator, which assigns a value of a variable only if that variable is currently null:

###  Example

 

``` dart
    int x; // The initial value of any object is null
    x ??=6;
    print(x); // result: 6

    x ??=3;
    print(x); // result is still 6

    print(null ?? 10); // result: 10. Display the value on the left if it's not null else return the value on the right

 ```

  ## Conditional Property Access

To properly safegaurd access to a property or method of an object that might be null, put a question mark (?) before the (.)

###  Example

 

``` dart

    userObject?.userName

    //The code snippet above is equivalent to following:

    (userObject !=null) ? userObject.userName : null

    //You can chain multiple uses of ?. together in a single expression

    userObject?.userName?.toString()

    // The preceeding code returns null and never calls toString() if either userObject or userObject.userName is null

 ```

   ## Collections Literals

With literals you can create Dart's built-in lists, maps and sets without hassle.

###  Example

 

``` dart

final fruitList = ["Orange","Bannana","Carrot","Apple"]; // A list of fruit
final countrySet = {"Nigeria","United States","Poland","Italy"}; // A set of country
final credMap = {
    'userName': 'temi',
    'password': 'xmen'
} // A map of user credentials

 ```

 You maybe wondering why we didn't explicitly declare a type for all of the collections above. It's interesting to know that dart's type inference can assign types to these variables for you. In this case, the inferred types are List<String>, Set<String> and Map<String, String>.

 Please note that you can choose to specify a type for your variable declaration like this:

  

``` dart

final fruitList = <String>[];
final countrySet = <String>{};
final credMap = <String, String>{};

 ```

   ## Arrow Syntax

 Remember Lambda Functions as discussed earlier in this sheet? We used a symbol => to define our lambda expression. You can check out Lambda function section for more explanation.

###  Example

 

``` dart

String _firstName = "Michael";
String _lastName = "Jones";
String _middleName = "Will";

String get fullName => '$_firstName $_middleName $_lastName'; // result: 'Michael Will Jones'

 ```

  ## Iterations

Just like every other programming language out there, you can perform iterations in dart. Here is a for loop example

###  Example

 

``` dart

for (int i=0; i<=20; i++){
    print(i); // prints 1 to 20
}

var fruitList = ["Orange","Bannana","Carrot","Apple"];
for (final fruit in fruits){
    print(fruit); // prints all types of fruit in the list
}

 ```

   ## Map 

Map can either be declared using literals or map constructor. To learn more about map declaration using literals, please go to the Collections Literals section. Here is how you can declare map using a map comstructor:

###  Example

 

``` dart
var user = new Map();
// To initialize the map, do this:
user['firstName'] = 'Paul';
user['lastName'] = 'Pogba';

// Result: {firstName: Paul, lastName: Pogba}

// Below are map properties

* Keys
* Values
* Length
* isEmpty
* isNotEmpty

// Below are map functions

* addAll()
* clear()
* remove()
* forEach()

 ```

   ## Variables

Here's an example of creating a variable and initializing it:

###  Example

 

``` dart
int x = 2; // explicitly typed
var p = 5; // type inferred
p = "cool"; // ops! throws an error
dynamic z = 8; // variable can take on any type
z = "cool"; // cool

// if you never intend to change a variable use final or const. Something like this:

final email = "temid@gmail.com"; // you can't change the value
final String email = "temid@gmail.com"; // you can't change the value

// iPhone 11 Pro max calculator using const

const qty = 5;
const totalCost = 1099 * qty;

 ```

   ## Class

In Dart, the class keyword is used to declare a class. Here is a basic example:

###  Example

 

``` dart
class Car {  
   // field 
   String engine = "E1001"; 
   // function 
   void disp() { 
      print(engine); 
   } 
}

 ```

   ## Getters and Setters

Getters and setters are special methods that provide read and write access to an object’s properties. Each instance variable of your class has an implicit getter, and a setter if needed. In dart, you can take this even further by implementing your own getters and setters. If you've had any experience in Object-Oriented Programming you'll feel right at home. Here is a basic syntax for a class:

###  Example

 

``` dart
class className {
 fields;
 getters/setters
 constructor
 methods/functions
}
 ```

``` dart
class Person {
  String firstName;
  String lastName;
  double height;
  int personAge;
  int yearofBirth;
  double weight;

  int get age {
    return personAge;
  }

  void set age(int currentYear) {
    personAge = currentYear - yearofBirth;
  }

  // We can also eliminate the setter and just use a getter.
  //int get age {
  //  return DateTime.now().year - yearofBirth;
  //}

  Person({this.firstName,this.lastName,this.personAge,this.yearofBirth,this.weight});
}
 ```

 We can implement Person class this way:

``` dart
void main() {
 Person person = Person(firstName:"Thanos",lastName:"Rednos",yearofBirth:1990,weight:200.5);
  print(person.firstName); // output - Thanos
  print(person.lastName); // output - Rednos
  person.age = 2019;
  print(person.age); // output - 29

}
```

   ## Futures: Async and Await

The async and await keywords provide a declarative way to define asynchronous functions and use their results. Remember these two basic guidelines when using async and await:

* To define an async function, add async before the function body:
* The await keyword works only in async functions.

###  Example

 

``` dart
Future<String> login() {
  // Imagine that this function is
  // more complex and slow.
  String userName="Temidjoy";
  return
   Future.delayed(
     Duration(seconds: 4), () => userName);
}

// Asynchronous
main() async {
  print('Authenticating please wait...');
  print(await userName());
}

 ```

   ## JSON and serialization

Most mobile and web apps use JSON for tasks such as exchanging data with a web server. With Dart support for JSON serialization and deserialization: converting Dart objects to and from JSON, data exchange is made easy in flutter development.

The following libraries and packages are useful across Dart platform:

* [dart:convert](https://dart.dev/guides/libraries/library-tour#dartconvert---decoding-and-encoding-json-utf-8-and-more)

   Converters for both JSON and UTF-8 (the character encoding that JSON requires).

* [package:json_serializable](https://pub.dev/packages/json_serializable)

   An easy-to-use code generation package. When you add some metadata annotations and use the builder provided by this package, the Dart build system generates serialization and deserialization code for you.

* [package:built_value](https://pub.dev/packages/built_value)

   A powerful, opinionated alternative to json_serializable.

You need to serialize and deserialize JSON in your Flutter project? [see this example](https://flutter.dev/docs/development/data-and-backend/json) to quickly get started.

   ## Reading and decoding a file

The code snippet below reads a file and runs two transforms over the stream. It first converts the data from UTF8 and then runs it through a LineSplitter. All lines are printed, except any that begin with a hashtag, #.

###  Example

 

``` dart
import 'dart:convert';
import 'dart:io';

Future<void> main(List<String> args) async {
  var file = File(args[0]);
  var lines = utf8.decoder
      .bind(file.openRead())
      .transform(LineSplitter());
  await for (var line in lines) {
    if (!line.startsWith('#')) print(line);
  }
}

 ```
