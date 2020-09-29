# Hellokotlin https://developer.android.com/kotlin/common-patterns

Kotlin variables:
Defined/declared by val keyword i.e val age;
Concatenate kt variable value in a string statement using ${ variableName }

Kt functions
A section of a program that performs a specific task.
A function is denoted using the  fun  keyword after which is the name oof the function and the parameters to be supplied to the function whenever the function i called within a class or program scope.
Ie 
fun printReceipt(oderNumber){ 
//some functionality to be executed
}.
Functions help avoid rewriting the same block of code multime times, instead the function can be defined then later accessed for the re-use of the functionality contained in it.
Function naming must clearly imply  what the function does, a verb.
A function takes arguments in the format  variableName then a colon : then the variable type at the end.
I.e printAge( age, 20  );

fun printAgee( age : int, timesToPrint : int){
	repeat(timesToPrint){
println( age )
}
}

Null safety
For a variable to hold  a null value, it must be of type  nullable.
KT conditionals 
If condition.
If-else condition to represent multiple conditions case.

Val answerString : String = if ( count == 42 ) {
“ This is the answer ”
} else if ( count > 4 ) { 
“Answer” }
eslse{ “ANS” }
println( answerString ) 
Nested If/else can be substituted with the when clause

Each branch in a when expression is represented by a condition, an arrow (->), and a result. If the condition on the left-hand side of the arrow evaluates to true, then the result of the expression on the right-hand side is returned.i.e
Val answerString = when { 
count== 42 -> “count at 43”
count== 28 -> “count at 28”
}
 println(answerString)

Checking if a variable under reference has a nullable value using a conditional statement.
	val languageName: String? = null
	If (languageName !=null) {
println(languageName.toUpperCase())
}

Alternative function definition in kt.
fun generateAnswerString():  String {
val answerString = if (count ==42) {
“String to be returned ”
}else {
“Answer for else ” 
}
return	answerString
}
Above function returns a value answerString of type String. To pass inputs to a function , create a function definition as bellow :
fun generateAnswerString(countTreshold: Int): String{
//logic that uses the passed integer here
}
In the function definition you specify the number of arguments and their respective types. When such a defined function is called , the call must supply the arguments defined.
High order functions -> are functions that take other functions as arguments.For instance a function that derives  an integer from a string that you pass into it .
	fun stringMapper(str: String, mapper: (String) → Int): int{
//invoke the passed function 
Return mapper( str )
}

Kt classes
Defined using the class keyword i.e class Car
To access a class and its properties one needs to declare a class instance accessing the constructor of the class. A constructor gives a dynamic mechanism for initialising a class object. I.e by defining custom constructors
From a class instance object , one can access the entire properties for the class.

Class functions and encapsulations.
Classes use functions to model behaviour, modify state helping one to expose certain components/data elements  you wish to expose within a given class definition.This whole concept is achieved using encapsulation.
Private properties of a class can only be accessed within the class while those declared as public are open to access from outside the class .

class Car(val wheels: List<Wheel>) {

    private val doorLock: DoorLock = ...

    var gallonsOfFuelInTank: Int = 15
        private set

    fun unlockDoor(key: Key): Boolean {
        // Return true if key is valid for door lock, false otherwise
    }
}


Common Kotlin patterns with Android 
Key focus on most  useful aspects of kt when developing for android ;
Inheritance :
Inheritance is indicated using the scope resolution operator  ‘ : ‘  i.e
	Class LoginFragment : Fragment()
-> Class LoginFragment is responsible for calling the constructor of the super class Fragment
One can implement/override the methods in the super cass using the @overide  keyword followed by the function 
 I.e 
override fun onCreateView(
        inflater: LayoutInflater,
        container: ViewGroup?,
        savedInstanceState: Bundle?
): View? {
    return inflater.inflate(R.layout.login_fragment, container, false)
}

To directly override a method in the Parent class use the super keyword i.e 
override fun onViewCreated(view: View, savedInstanceState: Bundle?) {
    super.onViewCreated(view, savedInstanceState)
}

Nullability and initialization.
Use ‘? ‘ suffix to denote that parameters passed for the arguments can be null hence , one needs to check for null safety when passing the arguments.

When using lateinit, you should initialize your property as soon as possible.For instance using lateinit to assign View objects in onViewCreated. Accessing a non-initialised lateinit variable will result in  a UninitializedPropertyAccessException

Click events.
Android click event implements the onClickListener interface.  This interface has a setOnclickListener which takes one parameter argument ‘OnclickListener’. OnclickLister has a single abstract method ‘onClick()’ that must be implemented.

An enum is a special "class" that represents a group of constants (unchangeable variables, like final variables). To create an enum , use the enum keyword (instead of class or interface), and separate the constants with a comma.
In android  when the constants in an enum are placed on separate lines, a blank line is not required between them except in the case where they define a body.
Implicit return/property types -> If an expression function body or a property initializer is a scalar value or the return type can be clearly inferred from the body then it can be omitted
I.e override fun toString(): String = "Hey"
// becomes
override fun toString() = "Hey"

Class names -> typically nouns or noun phrases
Interface names - > nouns or noun phrases
Test classes must based on the class they are testing ending with test.

Function names -> Written in camelCase, typically verbs or verb phrases.

Constant names are written in uppercase with words separated with underscores.. This includes immutable types and immutable collections of immutable types as well as scalars and string if marked as const
Non-constant names -> in camelCase i.e  instance properties, local properties, and parameter names.





https://www.raywenderlich.com/1364094-android-fragments-tutorial-an-introduction-with-kotlin#toc-anchor-001
Android fragments

A fragment  holds part  of  behaviour  or ui component of  an  activity. Fragments are tied to a single activity. Several fragments can be housed in the same activity.
Fragments ensure the following : Modularity, reusability and adaptability.


Using the support library has two benefits when developing applications for multiple versions of Android.
First, it ensures that you have consistency in your code and functionality across different devices and platform versions. This means that bugs and fixes will be more consistent across different versions of Android using these libraries.
Second, when they add new features to the latest version of Android, the Android team will often back-port these features via the support library in order for developers to use on older versions of Android.

