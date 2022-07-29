# CIS-18A-Project-


---------------------- menu.java ---------------------------------------------------------		

package Main;

import Products.Products;      // importing other package 

import java.util.Scanner; 

public class Menu {   // this class displays the main menu options 
	
	
	Scanner scan = new Scanner(System.in);   // this allows user input 
	
		public void displayMenu() {
			
			System.out.println("Welcome to 5-STAR GAMING where we literally only sell 5 video games!");
			System.out.println("Don't worry, however, as we change the selections each day. What would you like to do?"); 
			System.out.println("---------------------------------------------");
			System.out.println("(1) Look through selections");
			System.out.println("(2) Review previous orders");
			System.out.println("(3) View store hours");
			System.out.println("(4) Get me out of here.");
			
			System.out.println();          // blank space for neatness
			
			
			int choice = scan.nextInt();   // takes user input of type integer 
			
			System.out.println(); 		   // blank space for neatness
			
			
			do { 
				if (choice == 1) { 
					viewSelections(); }
				else if (choice == 2) {
					System.out.println("Last order's information..."); 
					
					Products.displayInfo(); 
					}
				else if (choice ==3) { 
					System.out.println("Store Hours are: ");
					System.out.println("Monday - Friday: 9AM to 9PM");
					System.out.println("Saturday and Sunday: 12PM - 7PM"); 
					}
				else if (choice == 4) {  
					System.out.println("Exiting Program..."); 
					
					System.exit(0);  }
				else {
					System.out.println("Invalid input. Try again.");  	}	
			
			} while (choice < 1 || choice > 4); 	
			
			
		} // end menu method 
	
		public void viewSelections() {
			
			System.out.println("Today, we are selling these products. Pick one.");    // Asks a user what game they would like 
			System.out.println("(1) MKX"); 
			System.out.println("(2) SFV"); 
			System.out.println("(3) COD"); 
			System.out.println("(4) RDR2");
			System.out.println("(5) BFV"); 
			System.out.println("(6)Nevermind. Take me back");    // takes back to menu 
			
			System.out.println();
			
			int input = scan.nextInt(); 
			
			System.out.println(); 
			
			
			// below are calling other classes --  not working properly 
			MKX game = new MKX();
			COD game1 = new COD(); 
			BF4 game2 = new BF4(); 
			RDR2 game3 = new RDR2(); 
			SFV game4 = new SFV(); 
			
			do { 
				switch (input ) {  // begin switch statement 
				
				case 1: {
					game.display_mk_info();      //  this is supposed to call a method from mk class
				}
				case 2: {
					game1.display_cod_info(); 	 // this is supposed to call a method from cod class 
				}
				case 3: {
					game2.display_bf_info();     // this is supposed to call a method from bf class 
				}
				case 4: {
					game3 = display_rdr_info();  // this is supposed to call a method from rdr class 
				}
				case 5: {
					game4 = display_sf_info();    // this is supposed to call a method from sf class 
				}
				case 6: { displayMenu();  		  // goes back to main menu 
				}
				default: {
					System.out.println("Invalid input. Try again.");   // input error from the user. The intention here is to make it loops back 
					
					scan.nextInt(); 
				}
				
				
				} // end switch statement
			
			} while (input < 1 || input > 6);   // end input validation loop (this doesn't work properly)
			
		}
		
---------------------- main.java ---------------------------------------------------------		

}  // end of class 

package Main;

import java.util.Scanner; 

public class Main {        // start main

	public static void main(String[] args) { 
	
		Menu x = new Menu(); 
		
		x.displayMenu(); 
		
		
	}

}							// end main 


---------------------- products.java ---------------------------------------------------------		
package Products;   

import Appointments.Appointments;            // this imports the other package 

public class Products implements Prices {    // this class contains all the product info and prices 
						   					 // I will use 6 video game titles as an example. I'm doing it this way because I have limited knowledge on designing an actual video game store 
											 // extends to prices interface 
	
	// declaring  class members for products 
	public static String itemNumber[] =  { "0001" , "0002" , "0003" , " 0004" , "0005" };  //  my intention here is to use a for loop to search through this array 
	private static String name; 
	private static String quantity; 
	private static double retailPrice;  
	
	Products(String item_number[], String NAME, String qty, double price) {    /// this acts as a constructor 
		
		item_number[] = itemNumber[];    // *error 
		
		NAME = name; 
		
		qty = quantity; 
		
		retailPrice = price; 	}
	
	// getter functions
	
	public String getItemNumber()   { return itemNumber[]; }   //*error
	public String getName() 		{ return name; }
	public String getQty()			{ return quantity; }
	public double getPrice() 		{ return retailPrice; }
	
	public static void displayInfo() {									// this function is supposed to display the order info 
		
		
		System.out.println("The item you selected is: "); 
		System.out.println("ITEM NUMBER: "); 
		
		for (int i = 0; i <= 5; i++)  {           		 // my intention here is to go through the loop via sequential and find the item 
														 // but i wasn't sure how to implement it properly 
			System.out.print(itemNumber[i]); 
		}
		
		System.out.println("ITEM NAME: " + name);                
		System.out.println("QUANTITY: " + quantity); 
		System.out.println("RETAIL PRICE: " + retailPrice); 
		System.out.println(); 
		
		Appointments.displayResults();    // this takes from the appointments package and displays a method 	
		
	}
	
	
} // end product class 

---------------------- deliveries.java (this is an interface) ---------------------------------------------------------		
package Appointments;

public interface Deliveries {         // this serves as an interface for the appointments 
	
	public void displayResults(); 

}
---------------------- prices.java (this is an interface) ---------------------------------------------------------		
package Products;

public interface Prices {    // this interface contains the prices of the products 

	double  mkx_price = 10.50; 
	double sf_price = 5.56; 
	double cod_price = 20.23; 
	double rdr_price = 59.99; 
	double bf_price = 30.0; 
	
	public void displayPrices();    
	
}   // end interface 

--------------------------------------- NOW FOR THE GAME SELECTIONS -------------------------------------------


------- MK.java -----------------------------------------

package Products;

import java.util.Scanner; 

public class MKX extends Products implements Prices {      			// my intention here was to implement inheritance -- using 'Products' as a parent class  
																    // I am not sure how to fix the error here. 
																	// I am also adding Interfaces here 
	Scanner scan = new Scanner(System.in) ;
	

public void display_mk_info () {
		
		System.out.println("Mortal Kombat is Item number: " + itemNumber[0]);  
		
		double game_price = 10.99; 
		
		System.out.println("This game costs " + game_price + "  US dollars. How many would you like?");
		
		int amount = scan.nextInt();  
		
		double total = amount * game_price;     // calculates sub-total 
		
		System.out.println("Your subtotal is " + total + " US dollars."); 
	}


}



------- sf.java -----------------------------------------

package Products;

import java.util.Scanner;

public class COD extends Products implements Prices {      // my intention here was to implement inheritance -- using 'Products' as a parent class  
																	 // I am not sure how to fix the error here. 
																	// I am also adding Interfaces here 
	Scanner scan = new Scanner(System.in) ;
	
public void display_cod_info () {
		
		System.out.println("Call of Duty is Item number: " + itemNumber[1]);  
		
		double game_price = 50.99; 
		
		System.out.println("This game costs " + game_price + "  US dollars. How many would you like?");
		
		int amount = scan.nextInt();  
		
		double total = amount * game_price;     // calculates sub-total 
		
		System.out.println("Your subtotal is " + total + " US dollars."); 
	}


}


------- bf.java -----------------------------------------

package Products;

import java.util.Scanner;

public class BF extends Products implements Prices {      // my intention here was to implement inheritance -- using 'Products' as a parent class  
																	 // I am not sure how to fix the error here. 
																	// I am also adding Interfaces here 
	Scanner scan = new Scanner(System.in) ;
	
	public void display_bf_info () {
 		
		System.out.println("Battle Field 4 is Item number: " + itemNumber[2]);  
		
		double game_price = 5.99; 
		
		System.out.println("This game costs " + game_price + "  US dollars. How many would you like?");
		
		int amount = scan.nextInt();  
		
		double total = amount * game_price;     // calculates sub-total 
		
		System.out.println("Your subtotal is " + total + " US dollars."); 
	}


}


------- sf.java -----------------------------------------
package Products;

import java.util.Scanner;

public class SFV extends Products implements Prices {      // my intention here was to implement inheritance -- using 'Products' as a parent class  
																	 // I am not sure how to fix the error here. 
																	// I am also adding Interfaces here 
	Scanner scan = new Scanner(System.in) ;
	
public void display_sf_info () {
		
		System.out.println("Street Fighter is Item number: " + itemNumber[4]);  
		
		double game_price = 40.99; 
		
		System.out.println("This game costs " + game_price + "  US dollars. How many would you like?");
		
		int amount = scan.nextInt();  
		
		double total = amount * game_price;     // calculates sub-total 
		
		System.out.println("Your subtotal is " + total + " US dollars."); 
	}


}

------- rdr.java -----------------------------------------

package Products;

import java.util.Scanner;

public class RDR2 extends Products implements Prices {      // my intention here was to implement inheritance -- using 'Products' as a parent class  
																	 // I am not sure how to fix the error here. 
																	// I am also adding Interfaces here 
	Scanner scan = new Scanner(System.in) ;
	
public void display_RDR_info () {
		
		System.out.println("Read Dead Redemption is Item number: " + itemNumber[3]);  
		
		double game_price = 69.99; 
		
		System.out.println("This game costs " + game_price + "  US dollars. How many would you like?");
		
		int amount = scan.nextInt();  
		
		double total = amount * game_price;     // calculates sub-total 
		
		System.out.println("Your subtotal is " + total + " US dollars."); 
	}


}

// END OF CODE 


