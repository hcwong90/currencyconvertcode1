
import java.util.InputMismatchException;
import java.util.Scanner;
import java.text.DecimalFormat;

public class CurrencyProg {

    public static void main(String[] args)
    {
	

			
		// Declare objects
		Scanner scan = new Scanner(System.in);
		
		Currency dollarConv = new Currency("US Dollar",conversionDollar);
		Currency euroConv = new Currency("Euro Dollars",conversioneEuro);
		Currency sgdConv = new Currency ( "Singapore Dollars", conversionSgd);
		Currency austConv = new Currency ("Australian Dollar ", conversionAust);	
		
		DecimalFormat currencyOut = new DecimalFormat("0.00");
		
		
		// Declare variables
		double sterlingAmount = 100.0;
		double conversionDollar;
		double conversioneEuro;
		double conversionSgd;
		double conversionAust;

		boolean entryValid = false;
		
		
		System.out.println("Currency Converter");

		// Set a dummy selection value, so that we always show the options on the first go
		char selection = 'x';
		
		// Offer a list of options
		while (selection != 'q') { 
			System.out.println("\n\tCurrent sterling amount: " + currencyOut.format(sterlingAmount));
			System.out.println("\tType c to change the sterling amount");
			System.out.println("\tType d to display the dollar amount");
			System.out.println("\tType e to display the Euro dollar amount");
			System.out.println("\tType s to display the Singapore dollar amount");
			System.out.println("\tType w to display table for currency");
			System.out.println("\tType q to quit");
			
			// Read from the keyboard
			selection = scan.next().charAt(0);

			// Act on the selection
			switch(selection) {

				case 'c': // Get a new amount
					
	while (!entryValid)
	{
		try																				
		{																													//codes that may throw an exception in the class Exception_Class
		System.out.println();
					System.out.println("\n\t Please enter a new amount for sterling amount");
					sterlingAmount = scan.nextDouble();
		entryValid = true;																									//This line will end the loop
				}
		catch(InputMismatchException e)														
		{																													//Code to be performed if an exception of the named exception class is thrown in the try block
			entryValid=false;
			System.out.println("Error, enter a number"); 
			scan.next();
		}	
	}
					break;
				case 'd': // Display dollar amount
					System.out.print("\n\tUK Sterling: " + currencyOut.format(sterlingAmount));
					System.out.println(" =  Dollar: " + currencyOut.format(dollarConv.convert(sterlingAmount)));
					break;		
/*			
				case 'e': // Display Euro dollar amount
					System.out.print("\n\tUK Sterling: " + currencyOut.format(sterlingAmount));
					System.out.println(" = Euro Dollars: " + currencyOut.format(euroConv.convert(sterlingAmount)));
					break;
			
				case 's': // Display Singapore dollar amount
					System.out.print("\n\tUK Sterling: " + currencyOut.format(sterlingAmount));
					System.out.println(" = Singapore Dollars: " + currencyOut.format(sgdConv.convert(sterlingAmount)));
					break;
			
				case 'w': // Display currency table
					System.out.println("\n\t Rate\tCurrency Name");
					System.out.println("\n\t"+ conversionDollars + "\t Dollar amount");
					System.out.println("\n\t"+ conversioneEuro + "\t Euro amount");
					System.out.println("\n\t"+ conversionSgd + "\t Singapore dollar");
					System.out.println("\n\t"+ conversionAust + "\t Australian dollar");
			
			
					break;
			
*/					
				case 'q': // Don't do anything for q, we print a message later
					break;
					
				default: // If it is not c,d or q then default is error message
					System.out.println("\n\tOption " + selection + " not understood");
			}
		}
		System.out.println("\n\tPROGRAM ENDED");
	}
}
