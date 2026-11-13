1a)Write a Java program to find the roots of quadratic equation ax2+bx+c = 0 

java.util.Scanner;
public class QuadraticRoots {  
public static void main(String[] args) {  
Scanner sc = new Scanner(System.in);     
System import.out.print("Enter a: ");    
double a = sc.nextDouble();     
System.out.print("Enter b: ");    
double b = sc.nextDouble();       
System.out.print("Enter c: ");       
double c = sc.nextDouble();      
if (a == 0) {         
System.out.println("Not quadratic"); 
} else {
double discriminant = b * b - 4 * a * c; 
if (discriminant < 0) {        
System.out.println("Imaginary roots");  
} else {                 
double root1 = (-b + Math.sqrt(discriminant)) / (2 * a);     
double root2 = (-b - Math.sqrt(discriminant)) / (2 * a);               
if (root1 == (int) root1 && root2 == (int) root2) {     
System.out.println("Roots = " + (int) root1 + ", " + (int) root2);     
} else {                  
System.out.println("Roots = " + root1 + ", " + root2);     
} 
}  
}    
sc.close();  
}
}  

1b)Write a Java program to print prime numbers up to a given integer (use BufferedReader) 

 import java.io.BufferedReader;
 import java.io.IOException; import java.io.InputStreamReader; 
 public class PrimeNumbers { 
 public static void main(String[] args) throws IOException {   
 BufferedReader br = new BufferedReader(new InputStreamReader(System.in));  
 System.out.print("Enter N: ");   
 int N = Integer.parseInt(br.readLine()); 
 if (N < 0) { 
 System.out.println("Invalid input");
 } else if (N < 2) {       
 System.out.println("No prime numbers");     
 } else {      
 for (int i = 2; i <= N; i++) {  
 boolean isPrime = true;  
 for (int j = 2; j <= Math.sqrt(i); j++) {  
 if (i % j == 0) {         
 isPrime = false;       
 break;     
 }           
 }      
 if (isPrime) {     
 System.out.print(i + " ");  
 }         
 }      
 } 
 } } 
 
 3a) method overloading and method overriding

class Parent {  
void display() {  
System.out.println("Parent display method executed"); 
} } 
class Child extends Parent {   
void display() {     
System.out.println("Child display method executed"); 
} } 
class Calculator {    
int add(int a, int b) {  
return a + b;   
}     
double add(double a, double b) {      
return a + b;  
} }  
public class MethodDemo {  
public static void main(String[] args) {    
Calculator calc = new Calculator();          
System.out.println("add(10, 5) = " + calc.add(10, 5));    
System.out.println("add(2.5, 3.5) = " + calc.add(2.5, 3.5));         
Child child = new Child();      
child.display();         
Parent ref = new Child();     
ref.display();         
System.out.println(calc.add("10", "5"));    
} } 

3b) inheritance (single, multilevel) and interfaces (for multiple inheritance) 

class Person { 
void showPerson() {  
System.out.println("Person method executed"); 
} }  
class Student extends Person{  
void showStudent() {    
System.out.println("Student method executed");  
} }  
class Animal {   
void eat() {  
System.out.println("Animal can eat"); 
} }  
class Dog extends Animal { 
void bark() { 
System.out.println("Dog can bark"); 
} }
class Puppy extends Dog { 
void weep() {    
System.out.println("Puppy can weep");  
} }
 interface Father {   
 void fatherProperty();
 }
 interface Mother { 
 void motherProperty(); 
 } 
 class Child implements Father, Mother { 
public void fatherProperty() { 
System.out.println("Father's property method executed");   
} 
public void motherProperty() {  
System.out.println("Mother's property method executed"); 
} } 
public class InheritanceDemo { 
public static void main(String[] args) {  
System.out.println("Single Inheritance:");   
Student student = new Student();   
student.showPerson();
student.showStudent(); 
System.out.println("\nMultilevel Inheritance:");   
Puppy puppy = new Puppy();    
puppy.eat();   
puppy.bark(); 
puppy.weep();  
System.out.println("\nMultiple Inheritance using Interfaces:");
Child child = new Child(); 
child.fatherProperty();    
child.motherProperty();  
class Parent {  
private int age = 25;  
}     
class ChildClass extends Parent {  
void display() {     
System.out.println(age);     
}       
}     
} }  
