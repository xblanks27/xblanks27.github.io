# xblanks27.github.io
## Hello, my name is Larry Blanks

<p> 	Throughout the computer science program, taking various courses have shaped what path I would take in the computer science field. Solving various problems and developing projects for fictional clients has allowed me to develop my knowledge in different programing languages, learning different APIs and runtime environments to simplify workloads. I found that my strengths come when developing solutions through writing applications for clients, developing computer games, and graphics that allow software to go beyond the terminal. In CS-465: Full Stack Development, I developed the front end user interface and the back end logic behind a travel package website creating full web application with JavaScript using the Node.js runtime, Angular, MongoDB, and Express. In CS-250: Software Development Lifecycle, I have collaborated with others in a team simulating an agile environment in which a client works with a product owner on the requirements of the client, the scrum master works with the team in meetings and developers work to create software for a client. The team worked to create a travel website with various vacation packages making sure to calculate project risks and time to develop. CS-255: System Analysis and Design also showed me what is required in the beginning stages of software development. Using activity diagrams, sequence diagrams, and presentations, I have made pitches for developing software that would meet the clients requirements for an application to allow users to schedule time with instructors for driving lessons. With CS-305: Software Security, I have used maven dependency check plugin to detect vulnerabilities and make a report and use the information to make changes to software to mitigate risk to the client. Taking Software Test, Automation QA, I Developed automated tests to make sure a mobile application developed for the fictional company Grand Strand Systems is functioning to the clients requirements.</p>
<p>	I chose the final project for IT 145: found in app development, the application was designed for a fictional client, Grazioso Salvare, to make an application for the tracking and intake of animals, dogs and monkeys, for use in rescue situations of people in difficult situations. I have used this artifact to demonstrate my abilities by creating three enhancements for the application. For the first enhancement, I created a user interface for the application instead of having the application run in the console or terminal. This enhancement was chosen to demonstrate my ability to design, develop, and deliver professional quality oral, written, and visual communications that are coherent, technically sound, and appropriately adapted to specific audiences and contexts and use well founded and innovative techniques, skills, and tools in computing practices for the purpose of implementing computer solutions that deliver and accomplish industry specific goals. The second enhancement I implemented a hash table to hold and sort objects stored in the application. I chose a hash table for this enhancement as the previous storage solution in the application was an array list, when an animal is searched for with the reserve animal command, the application would need to go down the list searching one at a time to find the right animal. With a hash table key the search would not need to search down the list, as long as there are not any animals stacked in the hash table the best case search could take less time at O(n) time for the search. This enhancement demonstrates my ability to design and evaluate computing solutions that solve a given problem using algorithmic principles and computer science practices and standards appropriate to its solution while managing the trade-offs involved in design choices. For the third I implemented an SQL database and a login function for the application. Creating a login system for the application would mitigate the risk of an unauthorized user from manipulating data in the application. Along with the login, passwords would be encrypted and stored in an SQL database and pulled for comparison when the user tries to login. This enhancement would demonstrate my ability in developing a security mindset that anticipates adversarial exploits in software architecture and designs to expose potential vulnerabilities, mitigate design flaws, and ensure privacy and enhanced security of data and resources.</p>

## Code Review
[Here is the link to my code review of the artifact used for the computer science capstone](https://youtu.be/YbpxZj6mMDo)

## Original Artifact

<details><summary>This is the main class of the original artifact</summary>

```java
package com.Sample.capstone;

import java.util.ArrayList;
import java.util.Scanner;
import java.util.InputMismatchException;

public class Driver {
	//instance an array list for dog and monkey lists
    private static ArrayList<Dog> dogList = new ArrayList<Dog>();
    private static ArrayList<Monkey> monkeyList = new ArrayList<Monkey>();

    public static void main(String[] args) {

        initializeDogList();
        initializeMonkeyList();

        int userInput = 0;
        Scanner scanner = new Scanner(System.in);
        
        //Menu loop, user inputs an integer to select a menu option.
        do {
        	try {
        	displayMenu();
        	userInput = scanner.nextInt();
 
        	switch (userInput) {
        	
        	case 1:
        		scanner.nextLine();
        		intakeNewDog(scanner);
        		break;
        		
        	case 2:
        		scanner.nextLine();
        		intakeNewMonkey(scanner);
        		break;
        		
        	case 3:
        		scanner.nextLine();
        		reserveAnimal(scanner);
        		break;
        		
        	case 4:
        		printAnimals("dog");
        		break;
        		
        	case 5:
        		printAnimals("monkey");
        		break;
        		
        	case 6:
        		printAnimals("notReserved");
        		break;
        		
        	case 0:
        		System.out.println("goodbye");
        		break;
        	}
        	}
        	catch(InputMismatchException e) {
        		System.out.println("Invalid input, please type a number");
        		scanner.nextLine();
        		userInput = scanner.nextInt();
        		
        	}
        }while(userInput != 0);
    }

    // This method prints the menu options
    public static void displayMenu() {
        System.out.println("\n\n");
        System.out.println("\t\t\t\tRescue Animal System Menu");
        System.out.println("[1] Intake a new dog");
        System.out.println("[2] Intake a new monkey");
        System.out.println("[3] Reserve an animal");
        System.out.println("[4] Print a list of all dogs");
        System.out.println("[5] Print a list of all monkeys");
        System.out.println("[6] Print a list of all animals that are not reserved");
        System.out.println("[0] Quit application");
        System.out.println();
        System.out.println("Enter a menu selection");
    }


    // Adds dogs to a list for testing
    public static void initializeDogList() {
        Dog dog1 = new Dog("Spot", "German Shepherd", "male", "1", "25.6", "05-12-2019", "United States", "intake", false, "United States");
        Dog dog2 = new Dog("Rex", "Great Dane", "male", "3", "35.2", "02-03-2020", "United States", "Phase I", false, "United States");
        Dog dog3 = new Dog("Bella", "Chihuahua", "female", "4", "25.6", "12-12-2019", "Canada", "in service", true, "Canada");

        dogList.add(dog1);
        dogList.add(dog2);
        dogList.add(dog3);
    }


    // Adds monkeys to a list for testing
    //Optional for testing
    public static void initializeMonkeyList() {

    }


    // Complete the intakeNewDog method
    // The input validation to check that the dog is not already in the list
    // is done for you
    public static void intakeNewDog(Scanner scanner) {
        System.out.println("What is the dog's name?");
        String name = scanner.nextLine();
        for(Dog dog: dogList) {
            if(dog.getName().equalsIgnoreCase(name)) {
                System.out.println("\n\nThis dog is already in our system\n\n");
                return; //returns to menu
            }
        }
        System.out.println("What is the dog's breed?");
        String breed = scanner.nextLine();
        System.out.println("What is the dog's gender?");
        String gender = scanner.nextLine();
        System.out.println("What is the dog's age?");
        String age = scanner.nextLine();
        System.out.println("How much does the dog weigh?");
        String weight = scanner.nextLine();
        System.out.println("When was the dog aquired?");
        String aquisitionDate = scanner.nextLine();
        System.out.println("Where was the dog aquired?");
        String aquisitionCountry = scanner.nextLine();
        System.out.println("What is the dog's training status?");
        String trainingStatus = scanner.nextLine();
        System.out.println("is the dog reserved?");
        boolean reserved = scanner.nextBoolean();
        System.out.println("Where is the dog in service?");
        String inServiceCountry = scanner.nextLine();
        Dog dogInput = new Dog(name, breed, gender, age, weight, aquisitionDate, aquisitionCountry, trainingStatus, reserved, inServiceCountry);
        // Add the code to instantiate a new dog and add it to the appropriate list
        dogList.add(dogInput);
        return;
    }


        // Complete intakeNewMonkey
	//Instantiate and add the new monkey to the appropriate list
        // For the project submission you must also  validate the input
	// to make sure the monkey doesn't already exist and the species type is allowed
        public static void intakeNewMonkey(Scanner scanner) {
            System.out.println("What is the monkey's name?");
            String name = scanner.nextLine();
            for(Monkey monkey: monkeyList) {
            	if(monkey.getName().equalsIgnoreCase(name)) {
            		System.out.println("\n\nThis monkey is already in our system\n\n");
            		return;
            	}
            }
            
            
            System.out.println("What is the monkey's gender?");
            String gender = scanner.nextLine();
            System.out.println("What is the monkey's age?");
            String age = scanner.nextLine();
            System.out.println("What is the monkey's weight?");
            String weight = scanner.nextLine();
            System.out.println("When was the monkey aquired?");
            String aquisitionDate = scanner.nextLine();
            System.out.println("Where was the monkey aquired?");
            String aquisitionCountry = scanner.nextLine();
            System.out.println("What is the monkey's training status?");
            String trainingStatus = scanner.nextLine();
            System.out.println("Is the monkey reserved?");
            Boolean reserved = scanner.nextBoolean();
            System.out.println("where is the monkey in service?");
            String inServiceCountry = scanner.nextLine();
            System.out.println("What is the monkey's species?");
            String species = scanner.nextLine();
            System.out.println("What is the monkey's tail length?");
            String tailLength = scanner.nextLine();
            System.out.println("What is the monkey's height?");
            String height = scanner.nextLine();
            System.out.println("What is the monkey's body length?");
            String bodyLength = scanner.nextLine();
            
            Monkey monkeyInput = new Monkey(name, gender, age, weight, aquisitionDate, aquisitionCountry, trainingStatus, reserved, inServiceCountry, species, tailLength, height, bodyLength);
            monkeyList.add(monkeyInput);
            return;
        }

        // Complete reserveAnimal
        // You will need to find the animal by animal type and in service country
        public static void reserveAnimal(Scanner scanner) {
            System.out.println("Please type the animal type: ");
            String animalType = scanner.nextLine();
            if (animalType == "Dog") {
            	System.out.println("Please type the dog's country: ");
            	String country = scanner.nextLine();
            	for(int i = 0; i < (dogList.size()); i++) {
            		if (dogList.get(i).getInServiceCountry() == country) {
            			if (dogList.get(i).getReserved() == false && dogList.get(i).getTrainingStatus() == "in service") {
            				System.out.println("The dog: " + dogList.get(i).getName() + " has been reserved.");
            				dogList.get(i).setReserved(true);
            			}
            			else {
            				System.out.println("No available dog in this country.");
            			}
            		}
            	}
            }
            else if (animalType == "Monkey"){
            	System.out.println("Please type the monkey's country: ");
            	String country = scanner.nextLine();
            	for(int i = 0; i < (monkeyList.size()); i++) {
            		if (monkeyList.get(i).getInServiceCountry() == country) {
            			if (monkeyList.get(i).getReserved() == false && monkeyList.get(i).getTrainingStatus() == "in service") {
            				System.out.println("The monkey: " + monkeyList.get(i).getName() + " has been reserved.");
            				monkeyList.get(i).setReserved(true);
            			}
            			else {
            				System.out.println("No available monkey in this country.");
            			}
            		}
            	}
            }
            else {
            	System.out.println("Invalid animal type.");
            }

        }

        // Complete printAnimals
        // Include the animal name, status, acquisition country and if the animal is reserved.
	// Remember that this method connects to three different menu items.
        // The printAnimals() method has three different outputs
        // based on the listType parameter
        // dog - prints the list of dogs
        // monkey - prints the list of monkeys
        // available - prints a combined list of all animals that are
        // fully trained ("in service") but not reserved 
	// Remember that you only have to fully implement ONE of these lists. 
	// The other lists can have a print statement saying "This option needs to be implemented".
	// To score "exemplary" you must correctly implement the "available" list.
        public static void printAnimals(String animalType) {
        	if (animalType == "dog") {
        		for (int i = 0; i < (dogList.size()); i++) {
        			System.out.println(dogList.get(i).getName());
        		}
        	}
        	else if (animalType == "monkey") {
        		for (int i = 0; i < (monkeyList.size() - 1); i++) {
        			System.out.println(monkeyList.get(i).getName());
        		}
        	}
        	else if (animalType == "notReserved") {
        		for (int i = 0; i < (dogList.size()); i++) {
        			if (dogList.get(i).getReserved() == false) {
        				System.out.println(dogList.get(i).getName());
        			}
        		}
        		for (int i = 0; i < (monkeyList.size()); i++) {
        			if (monkeyList.get(i).getReserved() == false) {
        				System.out.println(monkeyList.get(i).getName());
        			}
        		}
        	}

        }
}


```

</details>

{::options parse_block_html="false" /}

[Here is the link to the original artifact file](https://github.com/xblanks27/CS-499-Computer-Science-Capstone-Project/tree/main)

## Enhanced Artifact
[Here is the link to the enhanced artifact files](https://github.com/xblanks27/CS-499-Computer-Science-Capstone-Project/tree/Module-Seven)

## Enhancement One Narrative
<p>The artifact is the final project from IT 145 Found In App Development the application was developed for a fictional client who needs the application to track and find rescue animals, dogs and monkeys, and reserve them for use in rescue of people from dangerous situations. The application allows the intake of dogs and monkeys, reserving an animal, and displaying a list of animals. I chose this artifact as it was the most versatile for the enhancements I could add to the application. Adding a user interface would show my abilities to adapt an application from a terminal application to a window API, it would show my ability to design and develop software to a specific audience. Through enhancing the artifact adding a user interface to the application, I have met the planned course outcome that I expected to meet in module one, if there are any updates to the outcome coverage plan, it could meet the ability to demonstrate an ability to use well-founded and innovative techniques, skills, and tools in computing practices for the purpose of implementing computer solutions that deliver and accomplish industry specific goals. While enhancing the artifact for the milestone, I learned the importance on the use of proper spacing, the importance of iterative testing as each change in the panels of the interface and function could have large effects on the application, from non functioning buttons to completely blank windows.</p>

## Enhancement Two Narrative
<p>The artifact chosen is the final project for IT 145: Found in App Development, the artifact is an application developed for a fictional client for the tracking and reserving of animals for rescuing people from difficult locations. The artifact was chosen for this enhancement as it uses a simple data structure for storing lists of animals for the application and could be replaced for a data structure that is optimal for use in the application. The data structure I replaced the original was a hash table, I chose this data structure as it has a best case notation of O(1) when searching in the data structure, compared to the original data structure having O(n) as it parses through the list for the right animal object. As searches in the data structure continue it will become O(n) as it searches the table where the key resides. Other than searching in the data structure, printing all animals in the list will remain O(n) as runs through the list. I feel this enhancement meets the outcomes planned in module one, I do not have any updates to the outcome-coverage plan at the moment. On making the enhancement for the application, I learned how different the process of making a hash table is in the java programming language compared to how I learned to do it in the C++ programming language.</p>

## Enhancement Three Narrative
<p>The artifact is the final project from IT 145: Found In App Development, the application is developed for a fictional client to track and reserve animals for use in rescuing humans in difficult locations. The application allows users to intake a dog or monkey, reserve, or print a list of dogs, monkeys, or animals not reserved in the system. I selected this artifact for my e-portfolio as it was versatile an was able to implement multiple enhancements to display for the portfolio. With this enhancement to the artifact, the enhancement would showcase my ability to implement a database as well as add security to the application. The application was enhanced through the implementation of a login screen at the start of the application. This would prevent unauthorized users from accessing and manipulating data in the application. Along with this implementation, encryption of user passwords was also added to the application, as the user registers for the software, the password is encrypted and when logging into the application, the password will be compared to the encrypted password in the software database. A database was also implemented in the application, I originally planned to implement MongoDB as the database, though I had later decided to implement an SQL database to hold login credentials. I feel I was able to meet the course outcome planned in module one in developing a security mindset that anticipates adversarial exploits in software architecture and designs to expose potential vulnerabilities and ensure privacy and enhanced security of data. One of the challenges I had when implementing the encryption was converting the password string, the original get string function for inputting the password was deprecated as there was a security issue with the string remaining in memory as the program ran and was replaced with a character array, I decided to convert the character array to a string to encrypt the password which added an extra step in the login action listener function.</p>

## Enhancement narratives
[Here is the link to the artifact narrative documents](https://github.com/xblanks27/CS-499-Computer-Science-Capstone-Project/tree/Module-Seven)
