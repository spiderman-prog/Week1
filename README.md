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
 import java.io.IOException;
 import java.io.InputStreamReader; 
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

4.Write a Java program to demonstrate  a) packages    

Message.java
package mypackage; 
public class Message { 
public String showMessage() {
System.out.println(" Package class method executed");
}  } 
Helper.java
package mypackage; 
public class Helper {
public String  showHelper(){
System.out.println(" Helper class accessed successfully"); 
}  }
PackageDemo.java
import  mypackage.Message; 
import  mypackage.Helper;
import  java.util.Scanner;
public class PackageDemo { 
public static void main(String[] args) { 
 Message msg = new Message();
 msg.showMessage(); 
 Helper helper = new Helper();
 helper.showHelper();
 Scanner sc = new Scanner(System.in);
 System.out.print("Enter your name: ");
 String name = sc.nextLine();
 System.out.println("Input read successfully: " + name);
 sc.close();
 } } 

 4b) abstract classes and interfaces.

 interface Printable { 
 void print();
 } 
 abstract class Shape { 
 abstract double calculateArea();
 void showShape() {
 System.out.println("Shape method executed"); 
 } }
 class Circle extends Shape { 
 private double radius;
 Circle(double radius) { this.radius = radius; }
double calculateArea() { 
return Math.PI * radius * radius; } }
class Document implements Printable { 
public void print() {
System.out.println("Print method executed");
} } 
class Rectangle extends Shape implements Printable {  
private double length, breadth; 
Rectangle(double length, double breadth) { 
this.length = length;   
this.breadth = breadth;   
}    
double calculateArea() { 
return length * breadth; 
}     
public void print() { 
System.out.println("Rectangle details printed");
} }  
public class AbstractInterfaceDemo { 
public static void main(String[] args) { 
Circle circle = new Circle(5); 
System.out.println("Circle Area = " + circle.calculateArea());  
 Document doc = new Document();   
 doc.print();         
 Rectangle rect = new Rectangle(10, 5);    
 System.out.println("Rectangle Area = " + rect.calculateArea());    
 rect.print();  
 Shape s = new Shape(); 
 class Test implements Printable {       
     }        
     }}

 5.Write a Java program to a)  demonstrate exception handling     

 public class ExceptionHandlingDemo {  
 public static void main(String[] args) {   
 try {   
 int a = 10;  
 int b = 2;  
 int result = a / b;    
 System.out.println("Result = " + result);
 int arr[] = {10, 20, 30, 40};     
 System.out.println("Value displayed: " + arr[3]); 
 String str = "abc";     
 int num = Integer.parseInt(str); 
 System.out.println(num);
 } 
 catch (ArithmeticException e) {  
 System.out.println("ArithmeticException caught");   
 }
 catch (ArrayIndexOutOfBoundsException e) 
 {    
 System.out.println("ArrayIndexOutOfBoundsException caught");   
 }  
 catch (NumberFormatException e) {  
 System.out.println("NumberFormatException caught");    
 } } } 

5 b)  create user-defined exception 

class InvalidAgeException extends Exception { 
public InvalidAgeException(String message) {  
super(message); 
} }
class InvalidMarksException extends Exception {   
public InvalidMarksException(String message) { 
super(message); 
} }
public class UserDefinedExceptionDemo {   
static void validateAge(int age) throws InvalidAgeException {
if (age < 18) {       
throw new InvalidAgeException("Custom exception: Invalid age"); 
}
else {  
System.out.println("Valid age");     
}  
}  
static void validateMarks(int marks) throws InvalidMarksException {   
if (marks < 0 || marks > 100) {   
throw new InvalidMarksException("Custom exception: Invalid marks");    
}
else {   
System.out.println("Valid marks");    
}     }  
static void validateBalance(double balance) {     
if (balance >= 0) {  
System.out.println("Valid balance");   
}     }  
public static void main(String[] args) {   
try {    
validateAge(20); 
}
catch (InvalidAgeException e) {    
System.out.println(e.getMessage()); 
}        
try {         
validateMarks(75); 
} 
catch (InvalidMarksException e) {    
System.out.println(e.getMessage());    
}        
validateBalance(5000);          
try {         
validateAge(15);   
}
catch (InvalidAgeException e) { 
System.out.println(e.getMessage());  
}        
try {            
validateMarks(-10);  
} 
catch (InvalidMarksException e) {  
System.out.println(e.getMessage());  
}     } }  

6.Write a Java program to implement the producerconsumer problem using threads. 

class Buffer { 
private int item;   
private boolean available = false; 
public synchronized void produce(int value) {  
while (available) {      
try {            
wait();        
}
catch (InterruptedException e) {  
e.printStackTrace();  
}         }  
item = value;    
available = true;  
System.out.println("Produced: " + item);    
notify();     }  
public synchronized int consume() {   
while (!available) {      
try {  
System.out.println("Consumer waits, no crash");       
wait();           
} 
catch (InterruptedException e) {
e.printStackTrace();          
}         }   
available = false;       
System.out.println("Consumed: " + item);  
notify();     
return item;  
} }
class Producer extends Thread {  
private Buffer buffer;     
public Producer(Buffer buffer) {    
this.buffer = buffer;   
}   
public void run() {   
for (int i = 1; i <=5; i++) {   
buffer.produce(i);        
try {         
Thread.sleep(500); 
}
catch (InterruptedException e) { 
e.printStackTrace();         
}         }     } }
class Consumer extends Thread {  
private Buffer buffer;    
public Consumer(Buffer buffer) { 
this.buffer = buffer;
}    
public void run() {  
for (int i = 1; i <=5; i++) {    
buffer.consume();       
try {         
Thread.sleep(800); 
}
catch (InterruptedException e) { 
e.printStackTrace();       
}         }     } }
public class ProducerConsumer {    
public static void main(String[] args) {    
Buffer buffer = new Buffer();       
Producer producer = new Producer(buffer);    
Consumer consumer = new Consumer(buffer);  
consumer.start();
producer.start();   
} }  

7. Write a Swings program to a) mouse and keyboard events

import javax.swing.*;
import java.awt.*; 
import java.awt.event.*;
public class MouseKeyboardEvents extends JFrame 
implements MouseListener, MouseMotionListener, KeyListener {
private JLabel statusLabel;
public MouseKeyboardEvents() { 
setTitle("Mouse and Keyboard Events Demo"); 
setSize(500, 300);
setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
setLayout(new BorderLayout()); 
statusLabel = new JLabel("Perform mouse or keyboard actions", SwingConstants.CENTER); 
statusLabel.setFont(new Font("Arial", Font.BOLD, 16)); add(statusLabel, BorderLayout.CENTER); addMouseListener(this); addMouseMotionListener(this); addKeyListener(this); setFocusable(true); setVisible(true); } 
public void mouseClicked(MouseEvent e) { 
statusLabel.setText("Mouse clicked at (" + e.getX() + ", " + e.getY() + ")");
}
public void mousePressed(MouseEvent e) {}
public void mouseReleased(MouseEvent e) {}
public void mouseEntered(MouseEvent e) {
statusLabel.setText("Mouse entered frame"); 
}
public void mouseExited(MouseEvent e) { 
statusLabel.setText("Mouse exited frame");
} 
public void mouseMoved(MouseEvent e) { 
statusLabel.setText("Mouse moved: X=" + e.getX() + ", Y=" + e.getY()); }
public void mouseDragged(MouseEvent e) {}
public void keyPressed(KeyEvent e) {
statusLabel.setText( "Key Pressed: " + KeyEvent.getKeyText(e.getKeyCode()) + " (Code: " + e.getKeyCode() + ")" ); 
}
public void keyReleased(KeyEvent e) { 
statusLabel.setText( "Key Released: " + KeyEvent.getKeyText(e.getKeyCode()) );
} 
public void keyTyped(KeyEvent e) {
if (!Character.isISOControl(e.getKeyChar())) { 
statusLabel.setText("Key Typed: " + e.getKeyChar());
} } 
public static void main(String[] args){ 
SwingUtilities.invokeLater(()-> new MouseKeyboardEvents()); 
} }

7b) factorial computation.

import javax.swing.*; 
import java.awt.*; import java.awt.event.*;
public class FactorialSwing extends JFrame implements ActionListener {
JLabel lblInput, lblResult;
JTextField txtNumber;
JButton btnCalculate;
public FactorialSwing() {
setTitle("Factorial Calculator"); 
setSize(400, 200); 
setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
setLayout(new GridLayout(3, 2, 10, 10)); 
lblInput = new JLabel("Enter a Number:"); 
txtNumber = new JTextField();
btnCalculate = new JButton("Calculate Factorial"); 
btnCalculate.addActionListener(this);
lblResult = new JLabel("Result will be displayed here");
add(lblInput);
add(txtNumber);
add(btnCalculate);
add(new JLabel(""));
add(lblResult);
setVisible(true);
} 
public void actionPerformed(ActionEvent e) { 
try { 
int n = Integer.parseInt(txtNumber.getText()); 
if (n < 0) { 
lblResult.setText("Error: Factorial not defined for negative numbers");
return;
}
long factorial = 1; 
for (int i = 1; i <= n; i++) { 
factorial *= i; 
} 
lblResult.setText("Factorial of " + n + " = " + factorial);
}
catch (NumberFormatException ex) { 
lblResult.setText("Error: Please enter a valid numeric value");
} } 
public static void main(String[] args) {
new FactorialSwing(); 
} }
