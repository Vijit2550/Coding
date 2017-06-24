# Coding
Java Programming
/*
Name : Vijit Sood, Student ID: S0250674, Date: 9-Apr-2014, File Name: DogRegistration.java, Assessment Item-1 Basic JAVA Program
*/
import java.util.Scanner;
public class DogRegistration
{
	private final int N=7;			// number of dogs
	private String response;	// to store de-sexed dog status
	private Scanner inputString=new Scanner(System.in); // scanner variable to input string values
	private Scanner inputInt=new Scanner(System.in); // scanner variable to input int values
	private double per; // to input percentage
	private String dogName; // to store dog name
	private int dogAge; //to store dog age
	private double fee; // registration fee
	private double discount;// to store discount
	private double totalFee; //var to store total fees
	private double totalDiscount;// to store total discount
	private double averageFee;// to calculate average fee



	//Function to receive inputs from user//
	public void processDogs()
	{
		for(int l=0;l<N;l++)
		{
			System.out.print("Enter the Name of the Dog for the Registration ==> ");
			dogName=inputString.nextLine();// Reading name of the dog
			System.out.print("Enter the age of "+dogName +" in years ==> ");
			dogAge=inputInt.nextInt();// reading age of the dog
			if(dogAge<10) // checking if age of dog is less than 10 for de-sexed
			{
				System.out.print("Is "+dogName+" dog is de-sexed (Y/N) ==>");
				response=inputString.nextLine(); //reading de-sex value
			}
			System.out.print("Enter any additional discount as a percentage ==> ");
			per=inputInt.nextDouble();// reading percentage of discount

			fee=calculateFee(dogAge);//calling function to calculate the fee
			discount=calculateDiscount();// calling function to calculate discount
			fee=fee-discount;// finding amount after discount
			totalFee=totalFee+fee; // calculating total fee
			totalDiscount=totalDiscount+discount;// calculating total discount
			System.out.println();//printing blank lines
			System.out.println();
			System.out.println("------------------------------------------------------------------------");
			if(per>0)//check if discount percentage  is more than 0
			{
				System.out.printf("Discount of %.2f  on a fee of $%.2f is %.2f%n",per,fee,discount);// printing percentage, fee and  discount

			}

			System.out.printf("The registration fee for "+ dogName +" dog is $%.2f%n",fee); // printing name of dog along with net fee
			System.out.println("------------------------------------------------------------------------");
			System.out.println();
			System.out.println();

		}
		finalOutput();// calling function to print final summary


	}

	//Function to calculate the fees depending upon dog age

	private double calculateFee(int dogAge)
	{
		if(dogAge>=10)
			return 15.00;
		else if(dogAge<10 && (response.equals("y")|| response.equals("Y")))
			return 25.00;
		else
			return 45.00;

	}


	// Function to calculate discount

	private double calculateDiscount()
	{
		double discountAmt=(fee*per)/100;// calculating discount
		return discountAmt;// return discount amount
	}

	//Function to print final summary of program
	private void finalOutput()
	{
		averageFee=totalFee/N;
		System.out.println("Final statistics");
		System.out.println("----------------------------------------------------");
		System.out.printf("Total Dogs %21d%n",N);// printing total number of dogs
		System.out.printf("Total Fee %22.2f%n",totalFee);// printing total fee
		System.out.printf("Total Discounts %16.2f%n",totalDiscount);// printing total discount
		System.out.printf("Average fee %20.2f%n",averageFee);// printing average fee.
		System.out.println("----------------------------------------------------");

		System.out.println("Thank you, program written by S0250674 ");
		System.out.println("Press any key to continue...........");
		inputString.nextLine();

		totalFee=0.0;//resetting totalFee
		totalDiscount=0.0;//resetting totalDiscount
		averageFee=0.0;//resetting averageFee
	}

	public static void main(String[] args)
	{
		System.out.println("Welcome To my Assignment. This assignment is submitted by ID:- S0250674");
		DogRegistration dogRegistration = new DogRegistration(); // Object of class
		dogRegistration.processDogs();// calling method of class to process data.

	}
}
