#include <iostream>
#include <string>
#include <limits>
using namespace std;

// we gonna use struct
struct Student {
    string name;
    double gpa;
};

// we gonna create object for two types of array which holds the value of students  with gpa and declares number of student-
Student s[100], sorted[100];
int n;

// .....taking correct gpa that is beetwen o.o to 4.0.......
double getValidGPA() {
    double gpa;

    while (true) {
        cin >> gpa;

        if (cin.fail()) {
            cin.clear();
            cin.ignore(numeric_limits<streamsize>::max(), '\n');
            cout << "invalid input! Enter numeric GPA: ";
        }
        else if (gpa < 0.0 || gpa > 4.0) {
            cout << "GPA must be between 0.0 and 4.0. \nTry again: ";
        }
        else {
            return gpa;
        }
    }
}


// ---------------- SAFE NAME INPUT ----------------
void getValidName(int i) {
    while (true) {
        cin >> s[i].name;

        bool valid = true;

        for(char c : s[i].name) {
            if(!isalpha(c)) {
                valid = false;
                break;
            }
        }

        if(!valid) {
            cout << "Name must contain only letters. \nTry again: ";
        }
        else {
            break;
        }
    }
}

// ---------------- INPUT ----------------
void inputStudents() {
    for(int i = 0; i < n; i++) {

        cout << "\nEnter name of student " << i+1 << ": ";
        getValidName(i);

        cout << "Enter GPA of " << s[i].name << ": ";
        s[i].gpa = getValidGPA();
    }
}

// ---------------- COUNTING SORT ----------------
void countingSort() {

    int key[100];
    int count[10000] = {0};
    int max = 0;

    for(int i = 0; i < n; i++) {
        key[i] = (int)(s[i].gpa * 1000);

        if(key[i] > max)
            max = key[i];

        count[key[i]]++;
    }

    for(int i = 1; i <= max; i++)
        count[i] += count[i - 1];

    for(int i = n - 1; i >= 0; i--) {
        int pos = count[key[i]] - 1;
        sorted[pos] = s[i];
        count[key[i]]--;
    }
}

// ---------------- DISPLAY RANK ----------------
void displayRanking() {
    cout << "\n--- FINAL RANKING ---\n";

    for(int i = n - 1; i >= 0; i--) {
        cout << sorted[i].name << " - " << sorted[i].gpa << endl;
    }
}

// ---------------- WINNER ----------------
void showWinner() {
    cout << "\nTHE WINNER IS:\n";
    cout << sorted[n-1].name << " - " << sorted[n-1].gpa << endl;
}

// ---------------- identifying howmany gpa are identical ----------------
void sameGPA() {
    double x;

    cout << "Enter GPA you want to know: ";
    x = getValidGPA();

    bool found = false;

    cout << "Students with GPA " << x << ":\n";

    for(int i = 0; i < n; i++) {
        if(s[i].gpa == x) {
            cout << s[i].name << endl;
            found = true;
        }
    }

    if(!found)
        cout << "None\n";
}

//knowing greater gpa........
void greaterThanGPA() {
    double x;

    cout << "Enter GPA to know how many students are there above that GPA : ";
    x = getValidGPA();

    bool found = false;

    cout << "Students with GPA greater than " << x << ":\n";

    for(int i = 0; i < n; i++) {
        if(s[i].gpa > x) {
            cout << s[i].name << " - " << s[i].gpa << endl;
            found = true;
        }
    }

    if(!found)
        cout << "None of students have this GPA \n";
}

//SORTING ALPHABETICALLY.....................
void sortAlphabetically() {

    Student temp[100];

    for(int i = 0; i < n; i++)
        temp[i] = s[i];

    for(int i = 0; i < n - 1; i++) {
        for(int j = i + 1; j < n; j++) {
            if(temp[i].name > temp[j].name) {
                Student t = temp[i];
                temp[i] = temp[j];
                temp[j] = t;
            }
        }
    }

    cout << "\n==== ALPHABETICAL ORDER OF NAMES ====\n";

    for(int i = 0; i < n; i++) {
        cout << temp[i].name << " - " << temp[i].gpa << endl;
    }
}

// ---------------- DISPLAYING THE TOP 3 STUDENTS ----------------
void showTop3() {

    cout << "\n--- TOP 3 STUDENTS ARE: ---\n";

    int rank = 1;
    int printed = 0;

    for(int i = n - 1; i >= 0 && printed < 3; i--) {

        if(i == n - 1 || sorted[i].gpa != sorted[i+1].gpa) {
            cout << "\nRank " << rank << ":\n";
            printed++;
        }

        cout << sorted[i].name << " - " << sorted[i].gpa << endl;

        if(i > 0 && sorted[i].gpa != sorted[i-1].gpa)
            rank++;
    }
}

// ---------------- MAIN ----------------
int main() {

    cout << "Enter number of students: ";

    while(!(cin >> n) || n <= 0 || n > 100) {
        cin.clear();
        cin.ignore(numeric_limits<streamsize>::max(), '\n');
        cout << "Enter valid number (1–100): ";
    }

    inputStudents();
    countingSort();
    displayRanking();

    int choice;

    do {
        cout << "\n\n===== MENU =====\n";
        cout << "1. Same GPA Search\n";
        cout << "2. The Winner Student\n";
        cout << "3. Top 3 Students\n";
        cout << "4. knowing GPA \n";
        cout << "5. Alphabetical Order of Students\n";
        cout << "6. Exit\n";
        cout << "Enter choice: ";

        while(!(cin >> choice)) {
            cin.clear();
            cin.ignore(numeric_limits<streamsize>::max(), '\n');
            cout << "Enter valid menu number: ";
        }

        switch(choice) {

            case 1:
                sameGPA();
                break;

            case 2:
                showWinner();
                break;

            case 3:
                showTop3();
                break;

            case 4:
                greaterThanGPA();
                break;

            case 5:
                sortAlphabetically();
                break;

            case 6:
                cout << "Program Ended\n";
                break;

            default:
                cout << "Invalid choice\n";
        }

    } while(choice != 6);

    return 0;
}
