# Online-Reservation-system-

package onlinereservationsystem;

import java.util.Random;
import java.util.Scanner;

public class OnlineReservationSystem 
{
	Random pnr;
	
	Scanner s=new Scanner(System.in);
    String user_name, password, passenger_name, gender
    , train_name, boarding_station, destination, date_of_journey
    , class_type, next, exit;
    
    int passenger_age, PNR, pnr_num;
    
    public static void main(String[] args)
    {
        System.out.println("=================Welcome To The Online Reservation System==================");
 
        OnlineReservationSystem obj=new OnlineReservationSystem();
        obj.getUserDetails();
    }
    
    void getUserDetails()
    {
        
        System.out.println("Enter The User Name :");
        user_name=s.next();
        
        System.out.println("Enter the Password :");
        password=s.next();
        
        getPassword();
    }
    
    void getPassword()
    {
           if(password.equals("12345"))
           {
               System.out.println("==============================");
               System.out.println("Logged In successfully !!!");
               Login();
           }
           else
           {
               System.out.println("------------------------------");
               System.out.println("Please Enter Valid User Name & Password");
               System.out.println("                                ");
               getUserDetails();
           }
    }
    
    void Login()
    {
        System.out.println("Please Choose  The Option from Below :");
        System.out.println("                                         ");
        System.out.println("1. For Seat Booking");
        System.out.println("2. For Cancel Ticket");
        System.out.println("3. For Exit");
        System.out.println("===========================================");
        
        int option=s.nextInt();
        
        switch(option)
        {   
            case 1 : seatBooking();
            break;
            
            case 2 : cancelTicket();
            break;
            
            case 3 : exit();
            break;
            
            default : System.out.println("Please choose Valid Option");
                      System.out.println("===============================");
            Login();
            break;
        }
    }
       
    void seatBooking()
    {
        PNR=getPnr(100000,999999);
    	
        System.out.println("----------Please Enter Journey Details---------");
        System.out.println("Enter Train Name :");
        train_name=s.next();
        
        System.out.println("Enter Boarding Station : ");
        boarding_station=s.next();
        
        System.out.println("Enter Destination :");
        destination=s.next();
        
        System.out.println("Enter Date of Journey :");
        date_of_journey=s.next();
        
        System.out.println("Enter Class Type :");
        class_type=s.next();
        System.out.println("                        ");
        
        System.out.println("-------Now Enter Passenger Details--------");
        System.out.println("Enter Passenger Name : ");
        passenger_name=s.next();
        
        System.out.println("Enter Passenger Gender :");
        gender=s.next();
        
        System.out.println("Enter age :");
        passenger_age=s.nextInt();
        
        System.out.println("Your Seat Is Reserved Successfully !!!");
        
        System.out.println("----------------------------");
        
        System.out.println("For Review of Ticket Please Enter '1' ");
        int ticket_review=s.nextInt();
        
        if(ticket_review==1)
        {
        	showTicketDetails();
        }
        
    }
    void showTicketDetails()
    {
    	System.out.println("==========Ticket Details==========");
    	System.out.println("Train Name :- "+train_name);
    	System.out.println("PNR Number :- "+PNR);
    	System.out.println("Boarding Station :- "+boarding_station);
    	System.out.println("Destination :- "+destination);
    	System.out.println("Date of Jouney :- "+date_of_journey);
    	System.out.println("Class Type :- "+class_type);
    	System.out.println("Passenger Name :- "+passenger_name);
    	System.out.println("Passenger Gender :- "+gender);
    	System.out.println("Passenger Age :- "+passenger_age);
    	
    	System.out.println("=====================================");
    	System.out.println("do You Want to exit, If Yes then Enter 'Y' ");
    	exit=s.next();
    	
    	if(exit.equals("Y"))
    	{
    		exit();
    	}
    	else
    	{
    		System.out.println("=================================ankur"
    				+ "");
    		System.out.println("You are directed to Login Page");
    		Login();
    	}
    }
    
    void cancelTicket()
    {
       System.out.println("for cancel Ticket Please enter PNR number :");
       pnr_num=s.nextInt();
       if(pnr_num==PNR)
       {
    	   System.out.println("--------------------------------");
    	   System.out.println("For Cancel Your Ticket please Enter '2' ");
    	   int n=s.nextInt();
    	   if(n==2)
    	   {
    		   System.out.println("Your ticket has been Cancelled Successfully !!!");
    	   }
       }
       else
       {
    	   System.out.println("Please enter valid PNR number :");
    	   cancelTicket();
       }
    }
    
    public static int getPnr(int min, int max)
    {
    	Random pnr=new Random();
    	return (int) pnr.doubles(min, max).findFirst().getAsDouble();
    }
   
    void exit()
    {
    	System.out.println("Thank-you For Visit !!");
        System.exit(0);
    }
}
