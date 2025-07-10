# Tinashe Thoka
Vehicle Registration applications 
package com.cars;

/**
 * This class represents a vehicle with attributes such as make, model, plate number, VIN, year, and millage.
 */

public class Car {
                    // Attributes

    private String make;
    private String model;
    private String vin;
    private String plateNumber;
    private int year;
    private int millage;

    // Constructor
    public Car() {}

    // Getters and setters for the attributes

    public String getMake() {
        return make;
    }

    public void setMake(String make) {
        this.make = make;
    }

    public String getModel() {
        return model;
    }

    public void setModel(String model) {
        this.model = model;
    }

    public String getVin() {
        return vin;
    }

    public void setVin(String vin) {
        this.vin = vin;
    }

    public String getPlateNumber() {
        return plateNumber;
    }

    public void setPlateNumber(String plateNumber) {
        this.plateNumber = plateNumber;
    }

    public int getYear() {
        return year;
    }

    public void setYear(int year) {
        this.year = year;
    }

    public int getMillage() {
        return millage;
    }

    public void setMillage(int millage) {
        this.millage = millage;
    }
}

//Author : Tinashe Thoka.
package com.cars;

import java.util.ArrayList;
import java.util.Collection;
import java.util.Scanner;

public class Main {

    public static void main(String[] args){
                //Create a new Scanner object to read input from the user.

        Scanner input = new Scanner(System.in);
                //Create a collection to store vehicle objects
        Collection<Car> cars = new ArrayList<Car>();
                //Display the welcome message and menu options
        System.out.println("Good welcome to the app");
        System.out.println("(1) Capture vehicle details/n" + "(2) View vehicle report/n" + "(3) Exist app");

                //Read the user's menu option choice
        int menuOption = input.nextInt();
        System.out.println("Logged: " + menuOption);

                //Continue to display the menu and process user input until the user choooses to exit
        while((menuOption == 1) || (menuOption == 2)){

            if(menuOption == 1){
                    //Create a new Car object to store the vehicle's details
                Car carObj = new Car();
                    //Read the vehicle's details from the users
                int year;
                int millage;
                String model;
                String plateNum = "";
                String vinNum;

                System.out.println("Enter make");
                String make = input.next();

                System.out.println("Enter model");
                model = input.next();

                System.out.println("Enter vinNum");
                vinNum = input.next();
                        //Validate the VIN number to ensure it is 17 characters long
                while(!(vinNum.length() == 17)){
                    System.out.println("Enter vin and make sure its 17 characters long");
                    vinNum = input.next();
                }
                            //Ask  the user to choose the license plate number format
                System.out.println("Please enter (1) for old format license plate number, and for new format plate number");
                int plateChoice = Integer.parseInt(input.next());

                         // Read the license plate number if the user chose the old format
                if(plateChoice == 1){
                    System.out.println("Enter plate number e.g FMT740G");
                    plateNum = input.next();
                }
                // Read the vehicle's millage and year

                System.out.println("Enter millage");
                    millage = input.nextInt();

                System.out.println("Enter year");
                       year = input.nextInt();

                // Set the vehicle's details in the Car object
                carObj.setMake(make);
                carObj.setModel(model);

                carObj.setPlateNumber(plateNum);
                carObj.setVin(vinNum);

                carObj.setYear(year);
                carObj.setMillage(millage);
                // Add the Car object to the collection of vehicles

                cars.add(carObj);

            }else if(menuOption == 2){
                if(cars.isEmpty()){
                    System.out.println("There are no cars captured");
                }else {
                    // Display the vehicle report
                    System.out.println("********************\n" + "VEHICLE REPORT\n" + "********************");
                    for (Car carObject: cars){
                        System.out.println("MAKE: " + carObject.getMake()  + "\nMODEL: " + carObject.getModel());
                    }
                }
            }
            // Display the menu options again and read the user's next choice
            System.out.println("(1) Capture vehicle details\n" +
                                "(2) View vehicle report\n" +
                                 "(3) Exist app");

            menuOption = input.nextInt();
        }
        // Display a thank-you message when the user exits the application
        System.out.println("Thanks for using the app");
    }

}
