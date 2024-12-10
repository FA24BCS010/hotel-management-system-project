//*************************************************************************************************************//
//*************************************************************************************************************//
//                                                                                                             //
//              ---->   HOTEL MANAGEMENT AND RESERVATION SYSTEM                                                //
//                                                                                                             //
//                                                                                                             //
//                                                                                                             //                           
//                >>  ABUZAR JAMIL                       FA24-BCS-124                                          //
//                >>  HASSAN MUSTAFA                     FA24-BCS-043                                          //
//                >>  AHMER IJAZ                         FA24-BCS-010                                          //
//                >>  MUHAMMAD ZULQARNAIN LONE           FA24-BCS-088                                          //
//                                                                                                             //
//                                                                                                             //
//*************************************************************************************************************//
//*************************************************************************************************************//


//...................................................................................................................
//...................................................................................................................

#include <iostream>
#include <string>
#include <ctime>
#include <cstring>
using namespace std;

// Group 1: User Authentication Functions
void loadingEffect(); // Function to show a loading effect
bool compareStrings(const char* str1, const char* str2, int length); // Function to compare two strings
bool humanVerification(); // Function for human verification

// Group 2: User Interface Functions
void displayWelcomeNote(); // Function to display a welcome note
void displayThankYou(); // Function to display a thank you message

// Group 3: Guest Management Functions
void checkIn(int guestID); // Function to check in a guest
void checkOut(int guestID); // Function to check out a guest
void cancelReservation(int guestID); // Function to cancel a reservation
void orderFood(int guestID); // Function to order food for a guest
void addSpaService(int guestID); // Function to add spa service for a guest
void addFitnessCenter(int guestID); // Function to add fitness center access for a guest
void addLaundryService(int guestID); // Function to add laundry service for a guest
void addRoomCleaningService(int guestID); // Function to add room cleaning service for a guest
void addMaintenanceRequest(int guestID); // Function to add maintenance request for a guest

// Group 4: Reporting Functions
void displayGrandTotal(); // Function to display the grand total
void displayAvailableRooms(); // Function to display available rooms
void displayAllGuests(); // Function to display all guests information
void searchGuestByID(int guestID); // Function to search for a guest by ID


//...................................................................................................................
//...................................................................................................................


//...................................................................................................................
//...................................................................................................................
//............................................MAIN FUNCTION..........................................................
//...................................................................................................................
//...................................................................................................................
//...................................................................................................................


// Main function
int main() {
    int choice, guestID;

    loadingEffect();

    //...................................................................................................................
    //...................................................................................................................
    //.............................PASSWORD..............................................................................
   char id[8], pass[7];

    cout << "\n\n\t\t\t\tUsername => ";
    cin >> id;
    cout << "\n\t\t\t\tPassword => ";
    cin >> pass;

    // Check login credentials
    bool validLogin = compareStrings(id, "admin", 5) && compareStrings(pass, "admin", 5);

    cout << "\n\n\t";

    if (validLogin) {
        // Perform human verification
        if (humanVerification()) {
            cout << "\n\n\t\t\t  !!!Login Successful!!!\n";
        } else {
            cout << "\n\n\t\t\t!!!HUMAN VERIFICATION FAILED!!!\n";
            exit(-1); // Exit the program if verification fails
        }
    } else {
        cout << "\n\n\t\t\t!!!INVALID CREDENTIALS!!!\n";
        exit(-1); // Exit the program if credentials are invalid
    }

    loadingEffect();
    system("cls");
    //..................................................................................................................
   //...................................................................................................................

    displayWelcomeNote();

   
        
 do {
        cout<<"\n";
        cout<<"\n";
        cout << "***********************************************************\n";
        cout<<"\n";
        cout << "              Hotel Management System\n";
        cout<<"\n";
        cout << "***********************************************************\n";
        cout << "1. Check-In a Guest\n";
        cout << "2. Check-Out a Guest\n";
        cout << "3. Cancel Reservation\n"; 
        cout << "4. Order Food for a Guest\n";
        cout << "5. Add Spa Service for a Guest\n";
        cout << "6. Add Fitness Center Access for a Guest\n";
        cout << "7. Add Laundry Service for a Guest\n";
        cout << "8. Clean Room Service\n";
        cout << "9. Add Maintenance Request for a Guest\n"; 
        cout << "10. Total hotel Income \n";
        cout << "11. Display Available Rooms\n";
        cout << "12. Display All Guests Information\n";
        cout << "13. Search Guest by ID\n";
        cout << "0. Exit\n";
        cout << "Enter your choice: ";
        cin >> choice;

        switch (choice) {
            case 1:
             system("cls");
                cout << "Enter Guest ID for Check-In: ";
                cin >> guestID;
                checkIn(guestID);//Call the check in function
                break;
            case 2:
             system("cls");
                cout << "Enter Guest ID for Check-Out: ";
                cin >> guestID;
                checkOut(guestID);//Call the check out function
                break;
            case 3:
            system("cls");
                cout << "Enter Guest ID to Cancel Reservation: ";
                cin >> guestID;
                cancelReservation(guestID); // Call the cancel reservation function
                break;
            case 4:
            system("cls");
                cout << "Enter Guest ID to Order Food: ";
                cin >> guestID;
                orderFood(guestID);//Call for Food order Function
                break;
            case 5:
            system("cls");
                cout << "Enter Guest ID for Spa Service: ";
                cin >> guestID;
                addSpaService(guestID);  // Call Spa Service function
                break;
            case 6:
            system("cls");
                cout << "Enter Guest ID for Fitness Center Access: ";
                cin >> guestID;
                addFitnessCenter(guestID);  // Call Fitness Center function
                break;
            case 7:
            system("cls");
                cout << "Enter Guest ID for Laundry Service: ";
                cin >> guestID;
                addLaundryService(guestID);  // Call Laundry Service function
                break;
            case 8:
            system("cls");
                cout << "Enter Guest ID for Room Cleaning Service: ";
                cin >> guestID;
                addRoomCleaningService(guestID); // Call Room Cleaning Service function
                break;
            case 9:
            system("cls");
                cout << "Enter Guest ID to Add Maintenance Request: ";
                cin >> guestID;
                addMaintenanceRequest(guestID); // Call to add maintenance request
                break;
            case 10:
            system("cls");
                displayGrandTotal(); // Call to display hotel income total
                break;
            case 11:
            system("cls");
                displayAvailableRooms(); // Call to display available rooms
                break;
            case 12:
            system("cls");
                displayAllGuests(); // Call to display all guests information
                break;
            case 13:
            system("cls");
                cout << "Enter Guest ID to Search: ";
                cin >> guestID;
                searchGuestByID(guestID); // Call to search guest by ID
                break;
            case 0:
            system("cls");
                cout << "Exiting the system. Goodbye!\n";
                displayThankYou(); // Call to display thank you message
                break;
            default:
                cout << "Invalid choice. Please try again.\n";
        }
    } while (choice != 0);

    return 0;
}


//...................................................................................................................
//...................................................................................................................
//........................................Functions Definition ......................................................
//...................................................................................................................
//...................................................................................................................


//function for loading 
void loadingEffect() {
    cout << "                                   Loading                                    " << endl;
    for (int i = 0; i < 3; i++) {
        cout << "................................................................................." << endl;

        // Simulate a delay (busy-waiting)
        clock_t startTime = clock();
        while (clock() < startTime + 950); // Wait for approximately 
    }
    cout << endl;
}

//...................................................................................................................
//...................................................................................................................
//...................................................................................................................
//...................................................................................................................


void displayWelcomeNote() {

    cout << "                   **********************************************                   " << endl;
    cout << "                   **********************************************                   " << endl;
    cout << "                   *                                            *                   " << endl;
    cout << "                   *       W E L C O M E   T O   O U R          *                   " << endl;
    cout << "                   *                                            *                   " << endl;
    cout << "                   *       H O T E L   M A N A G E M E N T      *                   " << endl;
    cout << "                   *                S Y S T E M                 *                   " << endl;
    cout << "                   *                                            *                   " << endl;
    cout << "                   *     Your Comfort is Our Priority!          *                   " << endl;
    cout << "                   *   Please select from the menu options.     *                   " << endl;
    cout << "                   *                                            *                   " << endl;
    cout << "                   **********************************************                   " << endl;
    cout << "                   **********************************************                   " << endl;
}

//...................................................................................................................
//...................................................................................................................




void displayThankYou() {
    cout << "                   ========================================                   " << endl;
    cout << "                               T H A N K   Y O U                              " << endl;
    cout << "                   ========================================                   " << endl;


    cout << "                     TTTTTT  H   H   AAAAA   N   N  K   K      Y   Y   OOO   U   U                   " << endl;
    cout << "                       TT    H   H  A     A  NN  N  K  K        Y Y   O   O  U   U                   " << endl;
    cout << "                       TT    HHHHH  AAAAAAA  N N N  KKK          Y    O   O  U   U                   " << endl;
    cout << "                       TT    H   H  A     A  N  NN  K  K         Y    O   O  U   U                   " << endl;
    cout << "                       TT    H   H  A     A  N   N  K   K        Y     OOO    UUU                    " << endl;


    cout<<"\n";
    cout<<"\n";

    // Displaying a heart
    cout << "                         ******       ******                        " << endl;
    cout << "                        **      **   **      **                     " << endl;
    cout << "                       **        ** **        **                    " << endl;
    cout << "                      **          ***          **                   " << endl;
    cout << "                      **           *           **                   " << endl;
    cout << "                       **                    **                     " << endl;
    cout << "                         **                **                       " << endl;
    cout << "                           **            **                         " << endl;
    cout << "                             **        **                           " << endl;
    cout << "                               **    **                             " << endl;
    cout << "                                 ** **                              " << endl;
    cout << "                                   *                                " << endl;
}



//...................................................................................................................
//...................................................................................................................
//...................................................................................................................
//...................................................................................................................


// Structure to hold guest information
struct Guest {
    string name;
    string roomType;
    string checkInDate;
    string checkOutDate;
    int roomNumber;
    int totalNights;
    double totalBill;
};


//...................................................................................................................
//...................................................................................................................


// Structure to hold food menu items
struct FoodItem {
    string name;
    double price;
};


//...................................................................................................................
//...................................................................................................................


// Global variables
Guest guestList[100]; // Guest list with guest ID as index
int availableRooms[] = { 101, 102, 103, 201, 202, 203, 301, 302, 303 };  // Array of room numbers
int roomCount = sizeof(availableRooms) / sizeof(availableRooms[0]);  // Number of rooms


//...................................................................................................................
//...................................................................................................................


// Function to display available rooms
void displayAvailableRooms() {
    cout << "Available Rooms: ";
    for (int i = 0; i < roomCount; ++i) {
        if (availableRooms[i] != 0) {  // If room is not reserved
            cout << availableRooms[i] << " ";
        }
    }
    cout << endl;
}


//...................................................................................................................
//...................................................................................................................


// Function to calculate the number of nights from check-in and check-out dates
int calculateNights(const string& checkInDate, const string& checkOutDate) {
    int checkInDay, checkInMonth, checkInYear;
    int checkOutDay, checkOutMonth, checkOutYear;

    // Parse the dates into day, month, and year
    sscanf_s(checkInDate.c_str(), "%d/%d/%d", &checkInDay, &checkInMonth, &checkInYear);
    sscanf_s(checkOutDate.c_str(), "%d/%d/%d", &checkOutDay, &checkOutMonth, &checkOutYear);

    // Convert both dates to "days since epoch" and calculate the difference (simplified version)
    int checkInTotalDays = checkInYear * 365 + checkInMonth * 30 + checkInDay;
    int checkOutTotalDays = checkOutYear * 365 + checkOutMonth * 30 + checkOutDay;

    return checkOutTotalDays - checkInTotalDays;  // Calculate the difference in days
}

//...................................................................................................................
//...................................................................................................................


// Function to reserve a room
void reserveRoom(int& roomNumber, bool& roomFound) {
    for (int i = 0; i < roomCount; ++i) {
        if (availableRooms[i] == roomNumber) {
            roomFound = true;
            availableRooms[i] = 0; // Mark as reserved
            break;
        }
    }
}



//...................................................................................................................
//...................................................................................................................




// Function to check in a guest
void checkIn(int guestID) {
    // Check if the guest already exists
    if (guestList[guestID].name != "") {
        cout << "Guest with ID " << guestID << " is already checked in.\n";
        return;
    }

    Guest newGuest;
    cout << "Enter Guest Name: ";
    cin.ignore();
    getline(cin, newGuest.name);

    cout << "Select Room Type:\n1. Single\n2. Double\n3. Suite\nEnter your choice: ";
    int roomChoice;
    cin >> roomChoice;

    switch (roomChoice) {
    case 1:
        newGuest.roomType = "Single";
        newGuest.totalBill = 5000.0;
        break;
    case 2:
        newGuest.roomType = "Double";
        newGuest.totalBill = 8000.0;
        break;
    case 3:
        newGuest.roomType = "Suite";
        newGuest.totalBill = 15000.0;
        break;
    default:
        cout << "Invalid room type.\n";
        return;
    }

    displayAvailableRooms();
    cout << "Enter Room Number to Reserve: ";
    cin >> newGuest.roomNumber;

    bool roomFound = false;
    reserveRoom(newGuest.roomNumber, roomFound);

    if (!roomFound) {
        cout << "Room " << newGuest.roomNumber << " is not available.\n";
        return;
    }

    cout << "Enter Check-In Date (DD/MM/YYYY): ";
    cin >> newGuest.checkInDate;
    cout << "Enter Check-Out Date (DD/MM/YYYY): ";
    cin >> newGuest.checkOutDate;

    newGuest.totalNights = calculateNights(newGuest.checkInDate, newGuest.checkOutDate);
    newGuest.totalBill += newGuest.totalNights * (roomChoice == 1 ? 5000 : (roomChoice == 2 ? 8000 : 15000));

    guestList[guestID] = newGuest; // Assign guest details to the indexed list

    cout << "Guest " << newGuest.name << " has been checked in. Room Number: " << newGuest.roomNumber << "\n";
    cout << "Total Room Bill: " << newGuest.totalBill << " PKR for " << newGuest.totalNights << " night(s) Including Check out day.\n";
}



//...................................................................................................................
//...................................................................................................................


// Function to check out a guest
void checkOut(int guestID) {
    bool guestFound = false;

    // Search the guest list for the guestID
    if (guestList[guestID].name != "") {
        guestFound = true;
    }

    if (!guestFound) {  // If guestID was not found
        cout << "No guest found with ID: " << guestID << "\n";
        return;
    }

    // Get the room number of the guest who is checking out
    int roomNumber = guestList[guestID].roomNumber;

    // Mark room as available again in the array (by changing it back to its original room number)
    for (int i = 0; i < roomCount; i++) {
        if (availableRooms[i] == 0) {  // Look for an empty slot in available rooms
            availableRooms[i] = roomNumber;  // Revert room number back
            break;
        }
    }

    // Output the checkout details
    cout << "Guest " << guestList[guestID].name << " has checked out.\n";
    cout << "Total Bill: " << guestList[guestID].totalBill << " PKR\n";

    // Remove guest from guest list
    guestList[guestID] = Guest();
}



//...................................................................................................................
//...................................................................................................................




// Function to cancel a reservation
void cancelReservation(int guestID) {
    // Check if the guest exists
    if (guestList[guestID].name == "") {
        cout << "No guest found with ID: " << guestID << "\n";
        return;
    }

    // Get the room number of the guest who is canceling the reservation
    int roomNumber = guestList[guestID].roomNumber;

    // Mark the room as available again
    for (int i = 0; i < roomCount; i++) {
        if (availableRooms[i] == 0) {  // Look for an empty slot in available rooms
            availableRooms[i] = roomNumber;  // Revert room number back to available
            break;
        }
    }

    // Output the cancellation details
    cout << "Reservation for guest " << guestList[guestID].name << " has been canceled.\n";

    // Clear guest information from the guest list
    guestList[guestID] = Guest(); // Reset the guest information
}


//...................................................................................................................
//...................................................................................................................
//...................................................................................................................
//...................................................................................................................




// Function to order food for a guest
void orderFood(int guestID) {
    bool guestFound = false;

    // Manually search the array for the guestID
    for (int i = 0; i < 100; ++i) {
        if (guestList[i].name != "" && i == guestID) {  // Check if the guest exists
            guestFound = true;  // Guest found
            break;  // Stop searching once found
        }
    }

    if (!guestFound) {  // If guestID was not found
        cout << "No guest found with ID: " << guestID << "\n";
        return;
    }

    int foodOption, deliveryOption;

    // Define food items for each menu as arrays
    FoodItem breakfastMenu[] = { {"Pancakes", 500.0}, {"Omelette", 400.0}, {"Coffee", 150.0} };

    FoodItem lunchMenu[] = { {"Burger", 700.0}, {"Pizza", 1000.0}, {"Salad", 300.0} };

    FoodItem dinnerMenu[] = { {"Steak", 1500.0}, {"Pasta", 1200.0}, {"Soup", 800.0} };

    cout << "Select Food Menu for " << guestList[guestID].name << ":\n";
    cout << "1. Breakfast\n2. Lunch\n3. Dinner\nEnter your choice (1, 2, or 3): ";
    cin >> foodOption;

    FoodItem* selectedMenu;
    int selectedMenuSize;

    switch (foodOption) {
    case 1:
        selectedMenu = breakfastMenu;
        selectedMenuSize = sizeof(breakfastMenu) / sizeof(breakfastMenu[0]);
        break;
    case 2:
        selectedMenu = lunchMenu;
        selectedMenuSize = sizeof(lunchMenu) / sizeof(lunchMenu[0]);
        break;
    case 3:
        selectedMenu = dinnerMenu;
        selectedMenuSize = sizeof(dinnerMenu) / sizeof(dinnerMenu[0]);
        break;
    default:
        cout << "Invalid menu selection. Please choose 1, 2, or 3.\n";
        return;
    }

    cout << "Available Food Items:\n";
    for (int i = 0; i < selectedMenuSize; ++i) {
        cout << i + 1 << ". " << selectedMenu[i].name << " - " << selectedMenu[i].price << " PKR\n";
    }

    cout << "Select an item number from the menu: ";
    int itemChoice;
    cin >> itemChoice;

    if (itemChoice < 1 || itemChoice > selectedMenuSize) {
        cout << "Invalid item selection.\n";
        return;
    }

    FoodItem selectedFood = selectedMenu[itemChoice - 1];
    cout << "Delivery Options:\n1. Room Service - 200 PKR\n2. Self-Pickup - Free\nEnter your choice: ";
    cin >> deliveryOption;

    double deliveryCost = 0.0;
    if (deliveryOption == 1) {
        deliveryCost = 200.0;
    }
    else if (deliveryOption != 2) {
        cout << "Invalid delivery option. Please choose 1 or 2.\n";
        return;
    }

    double totalFoodCost = selectedFood.price + deliveryCost;
    guestList[guestID].totalBill += totalFoodCost;

    cout << "Order Summary:\n"
        << "Food Item: " << selectedFood.name << "\n"
        << "Food Cost: " << selectedFood.price << " PKR\n"
        << "Delivery Cost: " << deliveryCost << " PKR\n"
        << "Total Cost: " << totalFoodCost << " PKR\n"
        << "Updated Total Bill: " << guestList[guestID].totalBill << " PKR\n";
}

//...................................................................................................................
//...................................................................................................................
//...................................................................................................................
//...................................................................................................................




struct ServiceItem {
    string name;
    double price;
};

// Declare the spaMenu as a global variable 
ServiceItem spaMenu[] = {
    {"Facial", 1000},
    {"Massage", 1500},
    {"Manicure", 800}
};

const int spaMenuSize = sizeof(spaMenu) / sizeof(spaMenu[0]); // Size of the spa menu


//...................................................................................................................
//...................................................................................................................


// Function to add Spa Service
void addSpaService(int guestID) {
    bool guestFound = false;

    for (int i = 0; i < 100; ++i) {
        if (guestList[i].name != "" && i == guestID) {
            guestFound = true;
            break;
        }
    }

    if (!guestFound) {
        cout << "No guest found with ID: " << guestID << "\n";
        return;
    }

    cout << "Select Spa Service:\n";
    for (int i = 0; i < spaMenuSize; ++i) {
        cout << i + 1 << ". " << spaMenu[i].name << " - " << spaMenu[i].price << " PKR\n";
    }

    int spaChoice;
    cout << "Enter your choice (1, 2, or 3): ";
    cin >> spaChoice;

    if (spaChoice < 1 || spaChoice > spaMenuSize) {
        cout << "Invalid service selection.\n";
        return;
    }

    // Take time input for the spa service
    string serviceTime;
    cout << "Enter the time when the service is required (HH:MM format): ";
     cin.ignore();
    getline(cin,serviceTime);

    ServiceItem selectedSpaService = spaMenu[spaChoice - 1];
    guestList[guestID].totalBill += selectedSpaService.price;
    cout << "Spa Service added: " << selectedSpaService.name << " - " << selectedSpaService.price << " PKR\n";
    cout << "Service required at: " << serviceTime << "\n";
    cout << "Updated Total Bill: " << guestList[guestID].totalBill << " PKR\n";
}



//...................................................................................................................
//...................................................................................................................



// Function to add Fitness Center Access
void addFitnessCenter(int guestID) {
    bool guestFound = false;
    for (int i = 0; i < 100; ++i) {
        if (guestList[i].name != "" && i == guestID) {
            guestFound = true;
            break;
        }
    }

    if (!guestFound) {
        cout << "No guest found with ID: " << guestID << "\n";
        return;
    }

    // Input for the time when the service is required
    string serviceTime;
    cout << "Enter the time you want to access the Fitness Center (e.g., 9:00 AM): ";
    cin.ignore();
    getline(cin,serviceTime);

    double serviceCost = 1000.0;
    cout << "Fitness Center Access added for Guest ID: " << guestID << " at " << serviceTime << ".\n";
    guestList[guestID].totalBill += serviceCost;
    cout << "Service Cost: " << serviceCost << " PKR\n";
    cout << "Updated Total Bill: " << guestList[guestID].totalBill << " PKR\n";
}



//...................................................................................................................
//...................................................................................................................




// Function to add Laundry Service
void addLaundryService(int guestID) {
    bool guestFound = false;
    for (int i = 0; i < 100; ++i) {
        if (guestList[i].name != "" && i == guestID) {
            guestFound = true;
            break;
        }
    }

    if (!guestFound) {
        cout << "No guest found with ID: " << guestID << "\n";
        return;
    }

    // Input for the time when the service is required
    string serviceTime;
    cout << "Enter the time you want to request the Laundry Service (e.g., 11:00 AM): ";
     cin.ignore();
    getline(cin,serviceTime);

    double serviceCost = 500.0;
    cout << "Laundry Service added for Guest ID: " << guestID << " at " << serviceTime << ".\n";
    guestList[guestID].totalBill += serviceCost;
    cout << "Service Cost: " << serviceCost << " PKR\n";
    cout << "Updated Total Bill: " << guestList[guestID].totalBill << " PKR\n";
}



//...................................................................................................................
//...................................................................................................................



// Function to add Room Cleaning Service
void addRoomCleaningService(int guestID) {
    bool guestFound = false;
    for (int i = 0; i < 100; ++i) {
        if (guestList[i].name != "" && i == guestID) {  // Check if the guest exists
            guestFound = true;
            break;
        }
    }

    if (!guestFound) {
        cout << "No guest found with ID: " << guestID << "\n";
        return;
    }

    // Input for the time when the service is required
    string serviceTime;
    cout << "Enter the time you want to request the Room Cleaning Service (e.g., 11:00 AM): ";
     cin.ignore();
    getline(cin,serviceTime);
   

    double serviceCost = 300.0; // Example cost for room cleaning service
    cout << "Room Cleaning Service added for Guest ID: " << guestID << " at " << serviceTime << ".\n";
    guestList[guestID].totalBill += serviceCost;
    cout << "Service Cost: " << serviceCost << " PKR\n";
    cout << "Updated Total Bill: " << guestList[guestID].totalBill << " PKR\n";
}



//...................................................................................................................
//...................................................................................................................



struct MaintenanceRequest {
    int roomNumber;
    string issueDescription;
    
};


MaintenanceRequest maintenanceRequests[100]; // Array to hold maintenance requests
int maintenanceCount = 0; // Counter for maintenance requests

// Function to add a maintenance request
void addMaintenanceRequest(int guestID) {
    bool guestFound = false;

    // Check if the guest exists
    for (int i = 0; i < 100; ++i) {
        if (guestList[i].name != "" && i == guestID) {
            guestFound = true;
            break;
        }
    }

    if (!guestFound) {
        cout << "No guest found with ID: " << guestID << "\n";
        return;
    }

    // Input for the maintenance issue
    string issueDescription;
    cout << "Enter the maintenance issue description: ";
    cin.ignore(); // Clear the input buffer
    getline(cin, issueDescription); // Get the full line of input

    // Log the maintenance request
    if (maintenanceCount < 100) { // Check if there's space for a new request
        maintenanceRequests[maintenanceCount].roomNumber = guestList[guestID].roomNumber;
        maintenanceRequests[maintenanceCount].issueDescription = issueDescription;
       
        maintenanceCount++;

        cout << "Maintenance request logged for room " << guestList[guestID].roomNumber 
             << ": " << issueDescription << endl;
    } else {
        cout << "Maintenance request limit reached. Cannot log more requests.\n";
    }
}




//...................................................................................................................
//...................................................................................................................
//...................................................................................................................
//...................................................................................................................


// Function to display all guest information
void displayAllGuests() {
    cout << "\nGuest Information:\n";
    for (int i = 0; i < 100; ++i) {  // Assuming guestList has a maximum of 100 guests
        if (guestList[i].name != "") {  // Check if the guest exists
            const Guest& guest = guestList[i];
            cout << "Guest ID: " << i << "\n"  // Using index as Guest ID
                << "Name: " << guest.name << "\n"
                << "Room Number: " << guest.roomNumber << "\n"
                << "Room Type: " << guest.roomType << "\n"
                << "Check-In Date: " << guest.checkInDate << "\n"
                << "Check-Out Date: " << guest.checkOutDate << "\n"
                << "Total Nights: " << guest.totalNights << "\n"
                << "Total Bill: " << guest.totalBill << " PKR\n\n";
        }
    }
}


//...................................................................................................................
//...................................................................................................................



// Function to calculate and display the grand total of all guests
void displayGrandTotal() {
    double grandTotal = 0.0; // Variable to hold the total amount

    // Loop through all guests in the guestList array
    for (int i = 0; i < 100; ++i) {  // Assuming guestList has a maximum of 100 guests
        if (guestList[i].name != "") {  // Check if the guest exists
            grandTotal += guestList[i].totalBill; // Add each guest's total bill
        }
    }

    // Display the grand total
    cout << "\nGrand Total of All Guests: " << grandTotal << " PKR\n";
}


//...................................................................................................................
//...................................................................................................................




// Function to search for a guest by Guest ID and display their information
void searchGuestByID(int guestID) {
    // Validate the guest ID
    if (guestID < 0 || guestID >= 100) {
        cout << "Invalid Guest ID. Please enter a value between 0 and 99.\n";
        return;
    }

    // Check if the guest exists
    if (guestList[guestID].name != "") {
        const Guest& guest = guestList[guestID];
        cout << "Guest ID: " << guestID << "\n"
            << "Name: " << guest.name << "\n"
            << "Room Number: " << guest.roomNumber << "\n"
            << "Room Type: " << guest.roomType << "\n"
            << "Check-In Date: " << guest.checkInDate << "\n"
            << "Check-Out Date: " << guest.checkOutDate << "\n"
            << "Total Nights: " << guest.totalNights << "\n"
            << "Total Bill: " << guest.totalBill << " PKR\n";
    }
    else {
        cout << "No guest found with ID: " << guestID << "\n";
    }
}




//...................................................................................................................
//...................................................................................................................



// Function to compare two strings
bool compareStrings(const char* str1, const char* str2, int length) {
    for (int i = 0; i < length; i++) {
        if (str1[i] != str2[i]) {
            return false;
        }
    }
    return true;
}


//...................................................................................................................
//...................................................................................................................


// Function for human verification
bool humanVerification() {
    int num1, num2, answer, userAnswer;

    // Seed the random number generator
    srand(static_cast<unsigned int>(time(0)));

    // Generate two random numbers
    num1 = rand() % 10; // Random number between 0 and 9
    num2 = rand() % 10; // Random number between 0 and 9

    // Calculate the correct answer
    answer = num1 + num2; // You can change this to any operation

    // Ask the user to solve the problem with enhanced output
    cout << "\n\n\t\t\t\t===============================" << endl;
    cout << "\t\t\t\t Human Verification" << endl;
    cout << "\t\t\t\t===============================" << endl;
    cout << "\n\t\t\tWhat is " << num1 << " + " << num2 << "? ";
    cin >> userAnswer;

    // Check if the user's answer is correct
    cout << "\n\t\t\t===============================" << endl;
    if (userAnswer == answer) {
        cout << "\t\t\t\tCorrect! Verification Passed." << endl;
    } else {
        cout << "\t\t\t\tIncorrect! Verification Failed." << endl;
    }
    cout << "\t\t\t===============================" << endl;

    return userAnswer == answer;
}
///////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////
//**********************************************  T H E      E N D   **************************************************************      
///////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////
