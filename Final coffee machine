//N.M.Tharindu Rewatha || UCL 300205 || G20863502 || nmrtharindu@gmail.com

#include <iostream>

#include <string>

#include <iomanip>//Format Manipulator(Fixed,Setprecision)

#include <conio.h>//getch

#include <vector>//vector<coffee>

#include <windows.h>//MaximizeOutputWindow(); **Only for windows**

using namespace std;

//This code parts is for the password that gives the access to operator part.(177-192)
string typepassword(const char* prompt, bool show_stars = true) {
    const char BACKSPACE = 6;
    const char RETURN = 13;

    string password;
    unsigned char ch = 0;

    cout << prompt;

    while ((ch = _getch()) != RETURN) //hold the letter by getch()
    {
        //show stars to the letters that user types
        password += ch;
        if (show_stars)
            cout << '*';
    }
    cout << endl;
    return password;
}

//Here I've used a structure and  made the variables that keep the details of coffee types
struct coffee {
    string name;
    float itemprice = 1;
    string country;
    int quantity = 1;
};

//Here i've specified the elements set that I"ve stored inside the structure.(This is a global variable)
//Also i've used this vector function;Because by the using vector we can easily modify a structure
vector < coffee > coffee_drink ={
{"Espresso", 120, "Italy", 20},
{"Iced coffee", 150, "France", 20},
{"Long black", 80, "Austral", 20},
{"Americano", 100, "America", 20},
{"Latte", 200, "Italy", 20},
{"Irishcoffee", 130, "Ireland", 20},
{"Cappuccino", 180, "Italy", 20}
};

//These are the functions
void modeSelection(); //Select the mode(Customer mode or operator mode (83 - 118)
void customerMode(); //Customer mode (121 -174)
void hidePassword(); //Hide the password from others(Asterisks) (177 - 192)
void showCoffee(); //Displays the details of all coffee types (262 -274)
void selectOperator(); //Switch operator through all operator modifications (194 - 244)
void addCoffee(); //Add a new coffee type (246-260)
void no_more(); //Displays a message when a coffee type is finished (277-288)
void add_coffeePowder(); //Add or remove coffee mixture (304-336)
void switch_betweenOperator(); //Switch between operator modes (290 -302)
void get_salesReport(); //Displays the sales report after shutting down the machine (339 -349)
void change_itemPrice(); //increase or reduce the current item price (351-398)
void total_price(); //Calculate the total amount collected (416-423)
void MaximizeOutputWindow(); //Maximize the CL interface when it satarts to run the code (426 -429)
void delete_coffeeType(); //delete a cofee type from the list (400 -414)

int coffeetype = 1;

int main() {

    modeSelection();

}

//This part switch the user between operator mode and customer mode at the initial moment..
void modeSelection() {
    MaximizeOutputWindow();
    system("CLS");
    cout << "\n\n\n\n\n\n \t\t\t\t\t\t\t\t\t\t\t\t\x1B[36m  sWelcome to coffee machine by seek the freak\033[0m"; //1st impression
    cout << "\n\t\t\t\t\t\t\t\t\t\t\tPress '1' for customer mode || Press '2' for operator mode : ";

    int input;
    cin >> input;
    system("CLS"); //Clear the screan before operations

    if (input == 2) {
        cout << "\n\t\t\t\t\t\t\t\t\t\t\t\t\t\x1B[31m   Welcome to operator mode\033[0m \n"; //Welcome to the operator mode
        cout << "\t\t\t\t\t\t\t\t\t\t\t\t  Press '1' for continue || Press '2' for exit : "; //Chance to access customer mode if a customer presses 2 mistakenly
        int op;
        cout << "\t\t\t\t\t\t\t\t\t";
        cin >> op;
        system("CLS");
        if (op == 1) {
            hidePassword();
            //customerMode();

        }
        else {
            customerMode();
        }
    }
    else if (input == 1) {
        customerMode();
    }
    else {//If anyone press a wrong numbe it displays this
        cout << "\n\t\t\t\t\t\t\t\t\t\x1B[31mIncorrect response !! you will be redirected to customer mode  >>> Press any key";
        _getch();
        customerMode();
        return;
    }
}

//This is the customer part.this displays all details of coffee types  and does the buying process
void customerMode() {

    float remainder, price2, price;

    while (coffeetype <= (coffee_drink.size() + 1)) {
        showCoffee();

        cout << "\n\n\t\t\t\t\t\t\t\t\t\t " << (coffee_drink.size() + 1) << ") Operator Mode\x1B[31m[**RESTRICTED**]\033[0m";
        cout << "\n\t\t\t\t\t\t\t\t\t\t " << (coffee_drink.size() + 2) << ") Shut down the coffee machine";
        cout << "\n\n\t\t\t\t\t\t\t\t\t\t Choose one(Enter the relevant number) : ";
        cin >> coffeetype;

        no_more();

        if (coffeetype == (coffee_drink.size() + 2)) {  //Shut down the coffee machine
            system("CLS");
            cout << "\n\n\n\n\n\n\t\t\t\t\t\t\t\t\t\t\t\tThanks for using it.Have a nice day!\n";
            get_salesReport();
        }
        else if (coffeetype <= coffee_drink.size()) {  //Part that sells the coffee

            cout << "\t\t\t\t\t\t\t\t\t\t To grab your " << coffee_drink[coffeetype - 1].name << " pay Rs." << coffee_drink[coffeetype - 1].itemprice << " here : ";
            cin >> price;

            for (price; price < coffee_drink[coffeetype - 1].itemprice; price = (price + price2)) {// This part comes into play when a customer puts not enough money
                remainder = coffee_drink[coffeetype - 1].itemprice - price;

                cout << "\n\t\t\t\t\t\t\t\t\t\t Enter more Rs." << remainder << " here : ";
                cin >> price2;
            }
            cout << "\n\t\t\t\t\t\t\t\t\t\t\t\t\x1B[93m Coffee is a hug in a mug\033[0m ";
            cout << "\n\t\t\t\t\t\t\t\t\t\t\t\t\x1B[93m    Enjoy your beverage\033[0m \n\n";//At the end of every successful transaction machine displays this..

            coffee_drink[coffeetype - 1].quantity = coffee_drink[coffeetype - 1].quantity - 1;

            if (price > coffee_drink[coffeetype - 1].itemprice) { //This part gives customer change if he or she puts more money than required
                remainder = price - coffee_drink[coffeetype - 1].itemprice;
                cout << "\t\t\t\t\t\t\t\t\t\t Your change, Rs." << remainder << " just dropped into the Change Dispenser." << endl;
            }
            cout << "\n\t\t\t\t\t\t\t\t\t\t Press any key to continue";
            _getch();
            system("CLS");
        }
        else if (coffeetype == (coffee_drink.size() + 1)) {  //Operator mode
            hidePassword();
        }
        else {
            cout << "\t\t\t\t\t\t\t\t\t\t\x1B[31mIncorrect response !! you will be redirected to mode selection >>> Press any key";
            _getch();
            system("CLS");
            modeSelection();
        }
    }
}

//This part redirects operator to the operator mode if the pssword is matching
void hidePassword() {
    const char* correct_password = "coffee";

    string password = typepassword("\n\t\t\t\t\t\t\t\t\t\t Please enter the password : ", true); // Check password
    if (password == correct_password) {
        cout << "\t\t\t\t\t\t\t\t\t\t\x1B[93m Correct password\033[0m\n\n";
        cout << "\t\t\t\t\t\t\t\t\t\t Press any key to proceed >>>>";
        _getch();
        selectOperator();
    }
    else {
        cout << "\t\t\t\t\t\t\t\t\t\t\x1B[31m Incorrect password. Try again >> Press any key..\033[0m\n";
        _getch();
        modeSelection();
    }
}
//Following function is for swich operator between 4 operator modes
void selectOperator() {
    int type = 1;
    int type2 = 1;
    char yes = 1;
    system("CLS");
    cout << "\n\n\t\t\t\t\t\t\t\x1B[32m Enter No.1 for add new coffee type || No.2 for add or remove coffee || No.3 for change prices || No.4 for delete a coffee type :\033[0m "; //ions
    cin >> type;
    system("CLS");
    switch (type) {
    case 1:
        addCoffee();//Add a new coffee type
        break;

        cout << "\n\t\t\t\t\t\t\t\t\t\tDo you want add more? If yes press 'y' else 'n' : ";
        cin >> yes;
        if (yes == 'y') {

            addCoffee();

            cout << "\n\t\t\t\t\t\t\t\t\t\tPress '1' to access user mode||Press '2' to add more : ";
            cin >> type2;
            system("CLS");
            if (type2 == 1) {
                customerMode();
            }
            else {

                addCoffee();
                customerMode();
            }
        }
        else
            (yes == 'n'); {

            customerMode();
        }
    case 2:
        add_coffeePowder();//Add or remove coffee mixture powder from the machine
        break;
    case 3:
        change_itemPrice();//Change item price
        break;
    case 4:
        delete_coffeeType();//Delete a coffee type
        hidePassword();
        break;
    default:
        cout << "\t\t\t\t\t\t\t\t\t\t\x1B[31m Please enter correct number\033[0m";
        break;
    }
}
//add new types of coffee.Here I've written the code to add 3 coffee types at a time.But You can add any number of new coffees.
void addCoffee() { 

    coffee enter_coffee;
    cout << "\n\n\t\t\t\t\t\t\t\t\t\t\x1B[93mEnter the detailsof new coffee here!\033[0m" <<
        "\n\n\t\t\t\t\t\t\t\t\t\tEnter the name of new coffee type : "; //Name of new coffee type
    cin >> enter_coffee.name;
    cout << "\n\t\t\t\t\t\t\t\t\t\tEnter the price of new coffee type : "; //price of new coffee type
    cin >> enter_coffee.itemprice;
    cout << "\n\t\t\t\t\t\t\t\t\t\tEnter the country of origin : "; //Country of origin
    cin >> enter_coffee.country;
    cout << "\n\t\t\t\t\t\t\t\t\t\tEnter the quantity : "; //Quantity 
    cin >> enter_coffee.quantity;
    coffee_drink.push_back(enter_coffee); //Transfers data to the structure
    system("CLS");
}
//This part displays the cofffee menu and the welcome note
void showCoffee() {

    cout << fixed;
    cout << setprecision(2); //rounding  off the item price up to 2 decimal points

    cout << "\n\x1B[36m  <<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<< WELCOME >>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>\033[0m\n";
    cout << "\n\t\t\t\t\t\t\t\t\t\t\033[43;30m..........HEY THERE,HAVE A NICE DAY WITH A REFRESHING COFFEE..........\033[0m\n"; //Here I've used few text colour variations

    for (int i = 0; i != coffee_drink.size(); ++i) {
        cout << " \n\t\t\t\t\t\t\t\t\t\t " << i + 1 << ") " << coffee_drink[i].name << "\t\t" << coffee_drink[i].itemprice << "\t\t" << coffee_drink[i].country << "\t\t(" << coffee_drink[i].quantity << ") remaining";
    }

}

//Displaying a message if there is no more coffee powder in selected type
void no_more() {
    if (coffeetype >= 1 && coffeetype <= coffee_drink.size()) {
        if (coffee_drink[coffeetype - 1].quantity <= 0) { //check the coffee quantity equals to zero or not
            cout << "\n\t\t\t\t\t\t\t\t\t\t Oh bad time \n";
            cout << "\t\t\t\t\t\t\t\t\t\t No more " << coffee_drink[coffeetype - 1].name << " Available ..\n";
            cout << "\n\t\t\t\t\t\t\t\t\t\t But we have more tastes.Press any key to check 'em out\n";
            _getch();
            system("CLS"); //Clear screen
            customerMode();
        }
    }
}
//This allows operator to do more than one customization at a time
void switch_betweenOperator() {
    int leave = 1;
    cout << "\n\t\t\t\t\t\t\t\t\t\t Press '1' for modify more.|| Press '2' for leave operator mode\n";
    cout << "\t\t\t\t\t\t\t\t\t\t ";
    cin >> leave;
    system("CLS");
    if (leave == 1) {
        add_coffeePowder();
    }
    else if (leave == 2) {
        customerMode();
    }
}
//This adds coffee powder to the machine.Only operator can access this part
void add_coffeePowder() {

    int addpowder = 1;
    int quantity = 1;
    string addMinus;

    showCoffee();
    cout << endl;

    cout << "\n\t\t\t\t\t\t\t\t\t\t For which coffee type you want to add or remove coffee powder : ";

    cin >> addpowder;
    cout << "\n\t\t\t\t\t\t\t\t\t\t\x1B[31m The maximum coffee powder limit machine could store is 20.Do not exeed the limit\033[0m";
    cout << "\n\t\t\t\t\t\t\t\t\t\t Type 'Add' for add coffee powder || Type 'Remove' for remove coffee powder\n";
    cout << "\t\t\t\t\t\t\t\t\t\t ";
    cin >> addMinus;
    cout << "\t\t\t\t\t\t\t\t\t\t How many coffee cups you want to " << addMinus << " for " << coffee_drink[addpowder - 1].name << "\n";
    cout << "\t\t\t\t\t\t\t\t\t\t ";
    cin >> quantity;

    if (addMinus == "Add") {
        coffee_drink[addpowder - 1].quantity += quantity; //this will add  cups of coffee
    }
    else if (addMinus == "Remove") {
        coffee_drink[addpowder - 1].quantity -= quantity; //this will remove cups of coffee
    }
    else {
        cout << "\t\t\t\t\t\t\t\t\t\t\x1B[31m Incorrect response !! you will be redirected \033[0m >>> Press any key";
        _getch();
        system("CLS");
    }
    switch_betweenOperator();
}

//This displays the sales report after shutting down the coffee machine
void get_salesReport() {

    cout << "\t\t\t\t\t\t\t\t\t\t\033[43;30m........................Sales Report..........................\033[0m\n";

    for (int i = 0; i != coffee_drink.size(); ++i) {
        cout << "\n\t\t\t\t\t\t\t\t\t\t " << i + 1 << ") " << coffee_drink[i].name << "\t\t(" << (20 - coffee_drink[i].quantity) << ") sold" << "\t\t(" << coffee_drink[i].quantity << ") remaining";
    }
    total_price(); //Cout the total amount collected
    cout << "\n\t\t\t\t\t\t\t\t\t\t**************************************************************\n";
    cout << "\n\n\t\t\t\t\t\t\t\t\t\t    Press any key to leave the coffee machine >>>>>> _\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n";
}
//This helps to change item price.Only operator can access this fuction
void change_itemPrice() {

    int change_price = 1;
    int incred = 1;
    long new_price;
    int loop = 1;

    cout << "\n\n\t\t\t\t\t\t\t\t\t\tEnter '1' for change prices || '2' for return to  customer mode : ";
    cin >> loop;
    if (loop == 1) {
        showCoffee();//display coffee menu

        cout << "\n\n\t\t\t\t\t\t\t\t\t\tWhich coffee type you want to change the price : ";
        cin >> change_price;
        cout << "\n\t\t\t\t\t\t\t\t\t\tPress '1' to increase the price || Press '2' for reduce the price : ";
        cin >> incred;
        system("CLS");

        if (incred == 1) {

            cout << "\n\t\t\t\t\t\t\t\t\tCurrent price of " << coffee_drink[change_price - 1].name << " is Rs." << coffee_drink[change_price - 1].itemprice;
            cout << "\n\t\t\t\t\t\t\t\t\tFrom which amount you want to increase the item price : ";
            cin >> new_price;
            coffee_drink[change_price - 1].itemprice += new_price;//This will increase the item price
            system("CLS");
        }
        else if (incred == 2) {
            cout << "\n\t\t\t\t\t\t\t\t\t\tCurrent price of " << coffee_drink[change_price - 1].name << " is Rs." << coffee_drink[change_price - 1].itemprice;
            cout << "\n\t\t\t\t\t\t\t\t\t\tFrom which amount you want to reduce the item price : ";
            cin >> new_price;
            coffee_drink[change_price - 1].itemprice -= new_price;//This will reduce the item price

        }
        else {
            cout << "\t\t\t\t\t\t\t\t\t\t\x1B[31mIncorrect response !! you will be redirected to customer mode\033[0m >>> Press any key";
            _getch();
            system("CLS");
        }
    }
    else if (loop == 2) {
        customerMode();
    }
    else {
        cout << "\t\t\t\t\t\t\t\t\t\t\x1B[31mIncorrect response !! you will be redirected to customer mode\033[0m >>> Press any key";
        _getch();
        system("CLS");
    }
}
//This fuction deletes the existing coffee types.Only operator can access this part
void delete_coffeeType() {
    showCoffee();
    int deleteCoffee = 1;

    cout << "\n\t\t\t\t\t\t\t\t\t\t\t Which coffee type you want to delete : ";
    cin >> deleteCoffee;
    if (deleteCoffee > coffee_drink.size()) {
        cout << "\n\t\t\t\t\t\t\t\t\t\t\tInvalid ";
    }
    else {
        coffee_drink.erase(coffee_drink.begin() + (deleteCoffee - 1));
        system("CLS");
        customerMode();
    }
}
//This function calculates the total amount that collec from sales
void total_price() {
    float total = 0;
    for (int i = 0; i != coffee_drink.size(); ++i) {
        total = (coffee_drink[i].itemprice * (20 - coffee_drink[i].quantity)) + total;
    }
    cout << "\n\n\t\t\t\t\t\t\t\t\t\t\t Total amount collected from sales = Rs.";
    cout << total;
}

//Maximize CLI window.This part runs only in windows OS.If you are using linux ,mac or any other OS just delete this code part , line 71 and line 13.
void MaximizeOutputWindow() {
    HWND consoleWindow = GetConsoleWindow(); // This gets the value Windows uses to identify  output window 
    ShowWindow(consoleWindow, SW_MAXIMIZE); // this mimics clicking on its' maximize button
}
