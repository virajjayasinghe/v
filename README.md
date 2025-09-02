import java.util.Scanner;


 class Stack{

    private int x;
    private int top;
    private int [] array;

    public Stack(int value){

        x = value;

        array = new int[x];

        top = -1;

    }

    public void push(int y){

        if(isFull()){

            System.out.println("Not stack values");

        }else{

            array[++top] = y;
            System.out.println("y add stack");

        }

    }

    public void pop(){

        if(isEmpty()){

            System.out.println("remove no data");


        }else{

            System.out.println(array[top--] + "data reove");


        }

    }

    public void peek(){

        if(isEmpty()){

            System.out.println("stack value no");

        }else{

            System.out.println(array[top] + "more values");

        }


    }


    public boolean isFull(){

        return (top == x - 1 );

    }

    public boolean isEmpty(){

        return (top == -1);

    }

    public void dispaly(){

        if(isEmpty()){

            System.out.println("no stack value");

        }else{

            System.out.println("this is a stack value");


            for(int i = 0 ; i<= top; i++){

                System.out.println(array[i]);


            }

            System.out.println();

        }



    }


}


public class Arraystack {
    
    public static void main(String args[]){

        Scanner as = new Scanner(System.in);

        System.out.println("Enter your stack size");

        int value = as.nextInt();

        Stack stack = new Stack(value);

        int chos;

        do{
            System.out.println("entwer your like function");
            System.out.println("1.push Add stack data");
            System.out.println("2.pop data removed");
            System.out.println("3.peek top  data");
            System.out.println("4.dispaly stack values");
            System.out.println("5.exit");
            System.out.println("this choise number");

            chos = as.nextInt();

            switch (chos) {
                case 1:
                    
                    System.out.println("Enter your stack data");
                    int y = as.nextInt();
                    stack.push(y);

                    break;

                case 2:

                    stack.pop();
                    System.out.println("data removed");

                    break;

                case 3:

                    stack.peek();
                    break;

                case 4:

                    
                    stack.dispaly();
                    break;

                case 5:

                    System.out.println("function exit");
                    break;
            
                default:

                    System.out.println("your amswer not valide");

                    break;
            }

        }while (chos != 5);

        as.close();
            
        

    }


}


-------------------------------------------------------


import java.util.Scanner;

// Custom Stack implementation
class CharStack {
    private char[] stack;
    private int top;

    // Constructor to initialize stack with given size
    public CharStack(int size) {
        stack = new char[size];
        top = -1;
    }

    // Push character onto stack
    public void push(char c) {
        if (top == stack.length - 1) {
            System.out.println("Stack overflow!");
        } else {
            stack[++top] = c;
        }
    }

    // Pop character from stack
    public char pop() {
        if (top == -1) {
            System.out.println("Stack underflow!");
            return '\0';
        }
        return stack[top--];
    }

    // Check if stack is empty
    public boolean isEmpty() {
        return top == -1;
    }
}

public class palindrome {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        // a. Accept a word from the user
        System.out.print("Enter a word: ");
        String word = sc.nextLine();

        // Create a stack with size equal to word length
        CharStack stack = new CharStack(word.length());

        // b. Push characters to stack
        for (char c : word.toCharArray()) {
            stack.push(c);
        }

        // c. Pop characters to form a reversed word
        StringBuilder reversed = new StringBuilder();
        while (!stack.isEmpty()) {
            reversed.append(stack.pop());
        }

        // d. Compare original and reversed word
        if (word.equalsIgnoreCase(reversed.toString())) {
            System.out.println(word + " is a palindrome.");
        } else {
            System.out.println(word + " is not a palindrome.");
        }

        sc.close();
    }
}

-----------------------------------------

public class MergeSort{
    public static void main(String [] args){
        int[] array = {25, 36, 12, 9, 48, 27, 2, 59, 15, 1};
        divide(array, 0, array.length - 1);

        System.out.println("\nSorted array:");
        printArray(array);
    }
    public static void divide(int [] arr, int left, int right){
        if(left < right){
            int mid = left + (right - left)/2;
            divide(arr, left, mid);
            divide(arr, mid+1, right);
            merge(arr, left, mid, right);
        }
    }
    public static void merge(int [] arr, int l, int m, int h){

        int n1 = m - l + 1;
        int n2 = h - m;

        int L[] = new int[n1];
        int R[] = new int[n2];

        for (int i = 0; i < n1; i++)
            L[i] = arr[l + i];
        for (int j = 0; j < n2; j++)
            R[j] = arr[m + 1 + j];

        int i = 0, j = 0;
        int k = l;
        while (i < n1 && j < n2) {
            if (L[i] <= R[j]) {
                arr[k] = L[i];
                i++;
            }
            else {
                arr[k] = R[j];
                j++;
            }
            k++;
        }

        while (i < n1) {
            arr[k] = L[i];
            i++;
            k++;
        }

        while (j < n2) {
            arr[k] = R[j];
            j++;
            k++;
        }
    }
    public static void printArray(int[] array) {
        for (int value : array) {
            System.out.print(value + " ");
        }
        System.out.println();
    }
}

---------------------------------------------------

import java.util.Scanner;

class Stack {
    private int size;
    private int top;
    private char[] array;

    public Stack(int value) {
        size = value;
        array = new char[size];
        top = -1;
    }

    // Push character
    public void push(char ch) {
        if (isFull()) {
            System.out.println("Stack is full, cannot add more characters.");
        } else {
            array[++top] = ch;
            System.out.println(ch + " added to stack");
        }
    }

    // Pop character
    public void pop() {
        if (isEmpty()) {
            System.out.println("Stack is empty, nothing to remove.");
        } else {
            System.out.println(array[top--] + " removed from stack");
        }
    }

    // Peek top character
    public void peek() {
        if (isEmpty()) {
            System.out.println("Stack is empty, no top element.");
        } else {
            System.out.println("Top element: " + array[top]);
        }
    }

    // Display all characters in the stack
    public void display() {
        if (isEmpty()) {
            System.out.println("Stack is empty.");
        } else {
            System.out.println("Stack elements:");
            for (int i = 0; i <= top; i++) {
                System.out.print(array[i] + " ");
            }
            System.out.println();
        }
    }

    // Check if the current stack is a palindrome
    public void checkPalindrome() {
        if (isEmpty()) {
            System.out.println("Stack is empty. Cannot check palindrome.");
            return;
        }
        boolean isPalindrome = true;
        for (int i = 0; i <= top / 2; i++) {
            if (array[i] != array[top - i]) {
                isPalindrome = false;
                break;
            }
        }
        if (isPalindrome) {
            System.out.println("Stack data forms a palindrome.");
        } else {
            System.out.println("Stack data does not form a palindrome.");
        }
    }

    // Helper methods
    public boolean isFull() {
        return (top == size - 1);
    }

    public boolean isEmpty() {
        return (top == -1);
    }
}

public class Arraystack {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        System.out.print("Enter stack size: ");
        int value = sc.nextInt();
        Stack stack = new Stack(value);

        int choice;
        do {
            System.out.println("\nChoose an operation:");
            System.out.println("1. Push (Add character to stack)");
            System.out.println("2. Pop (Remove character from stack)");
            System.out.println("3. Peek (Show top character)");
            System.out.println("4. Display stack");
            System.out.println("5. Exit");
            System.out.println("6. Check Palindrome");
            System.out.print("Enter your choice: ");
            choice = sc.nextInt();

            switch (choice) {
                case 1:
                    System.out.print("Enter character to push: ");
                    char ch = sc.next().charAt(0);
                    stack.push(ch);
                    break;
                case 2:
                    stack.pop();
                    break;
                case 3:
                    stack.peek();
                    break;
                case 4:
                    stack.display();
                    break;
                case 5:
                    System.out.println("Exiting...");
                    break;
                case 6:
                    stack.checkPalindrome();
                    break;
                default:
                    System.out.println("Invalid choice! Try again.");
            }
        } while (choice != 5);

        sc.close();
    }
}

------------------------------------------------------------

class Linkedlist{

    class Node{

        int data;
        Node next;

        Node(int data){
            this.data = data;
            this.next = null;
        }


    }


    class Charnode{
        char data;
        Charnode next;

        Charnode(char data){
            this.data = data;
            this.next  =null;
        }
    }

    private Node head;

public Linkedlist(){

    head = null;

}

public void insert(int data){

    Node newNode  = new Node(data);
    if(head == null){
        head = newNode;
    }else{
        Node current = head;
        while(current.next != null){
            current = current.next;
        }
        current.next = newNode;
    }

}

public void Delete(int data){

    if(head == null){
        return;
    }
    if(head.data == data){
        head = head.next;
        return;
    }
    Node current = head;
    while (current.next != null && current.next.data != data){
        current = current.next;
    }
    if (current.next != null){
        current.next = current.next.next;
    }
}

public boolean Serch(int data){

    Node current = head;
    while(current != null){

        if(current.data ==data){
            return true;
        }

        current = current.next;
        

    }
   return false;

}

public void display(){

    Node current = head;
    while(current != null){

        System.out.println( "->" +current.data );
        current = current.next;

    }
    System.out.println("null");

}

public static void main(String[] args){

    Linkedlist list = new Linkedlist();

    list.insert(1);
    list.insert(10);
    list.insert(5);
    list.insert(6);
    list.insert(4);

    list.display();

    list.Delete(10);
    list.display();

    list.insert(20);
    list.display();


     list.Delete(20);
     list.display();

}

}
