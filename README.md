#include <iostream> 
#include <string>
#include <vector>
using namespace std;

void displayIntroduction(){

    cout << "Welcome to Daymark!\n";
    cout << "Daymark is a to-do list creator \n";
}

int main() {
    
    displayIntroduction();

    string name;
    string task;
    string choice;

    cout << "What is your name?\n";
    getline(cin, name);

    cout << "Hello " << name << "! Let's start planning your day.\n";

    vector<string> tasks;

    cout << "Please list out the tasks you need to complete today.\n";
    cout << "Type DONE when you have entered them all.\n\n";

    while (true) {

        cout << "Enter a task: ";
        getline(cin, task);

        if (task == "DONE") {

            break;
        }

        tasks.push_back(task);
        cout << "Task added!\n\n";
    }
 
    cout << "Your to-do list:\n";

    int number = 1;

    for (string item: tasks) {
        cout << number << ". " << item << "\n\n";
        number++;
    }

    while (true) {
        
        cout << "What would you like to do next?\n";
        cout << "1. View my list again\n";
        cout << "2. Exit Daymark\n";
        cout << "3. Add more tasks\n";
        cout << "4. Remove a task\n";
        cout << "Enter your choice: ";
        getline(cin, choice);

        if (choice == "1") {
            cout << "\nYour to-do list:\n";

            int number = 1;

            for (string item: tasks) {
                cout << number << ". " << item << '\n';
                number++;
            }
        }

        else if (choice == "2") {
            cout << "Goodbye, " << name << "!\n";
            break;
        }

        else if (choice == "3") {
            cout << "\nEnter more tasks. Type DONE when you are finished.\n";

            while (true) {
                cout << "Enter a task: ";
                getline(cin, task);

                if (task == "DONE") {
                    break;
                }

                tasks.push_back(task);
                cout << "Task added!\n";
            }
        }

        else if (choice == "4") {

            if (task.empty()) {

                cout << "There are no tasks to remove.\n";
                continue;
            }

        cout << "\nWhich task would you like to remove?\n";

        int number = 1;

        for (string item: tasks) {
            cout << number << "." << item << '\n';
            number ++;
        }

        string taskNumber;
        cout << "Enter its number: ";
        getline(cin, taskNumber);

        bool removed = false;

        for (int i = 0; i < static_cast<int>(tasks.size()); i++) {

            if (taskNumber == to_string(i + 1)) {
                tasks.erase(tasks.begin() + i);
                removed = true;
                break;
            }
        }

            if (removed) {
            cout << "Task removed!\n";
        }

            else {
            cout << "That task number isn't on your list.\n";
            }
        }

        else {
            cout << "Please enter 1, 2, 3, or 4.\n";
        }
    }

    return 0;
}
