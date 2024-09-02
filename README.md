#include <iostream>
#include <direct.h>
#include <string>
using namespace std;

void list_file();
void directory();
void change_dir();

int main() {
int choice;
while (true) {
cout << " Main Menu: " << endl;
cout << "--------------------------------\n";
cout << "1. To Display List of Files\n";
cout << "2. To Create New Directory\n";
cout << "3. To Change the Working Directory\n";
cout << "4. Exit Program\n";
cout << "Enter Number: ";
cin >> choice;

switch (choice) {
case 1:
list_file();
break;
case 2:
directory();
break;
case 3:
change_dir();
break;
case 4:
return 0;
default:
cout << "Invalid choice. Please try again.\n";
}
}
return 0;
}

void list_file() {
int choice;
cout << " LIST FILE DETAIL:" << endl;
cout << "--------------------------------------\n" << endl;
cout << "1. List All Files\n";
cout << "2. List of Extension Files\n";
cout << "3. List of Name Wise\n";
cout << "Enter Number: ";
cin >> choice;

switch (choice) {
case 1:
cout << "List of all (.) Files\n";
system("dir");
break;
case 2: {
string ext;
cout << "Enter file extension: ";
cin >> ext;
system(("dir *." + ext).c_str());
break;
}
case 3: {
string pattern;
cout << "Enter file name pattern: ";
cin >> pattern;
system(("dir " + pattern).c_str());
break;
}
default:
cout << "Invalid choice. Please try again.\n";
}
}

void directory() {
string dir;
cout << "Directory name: ";
cin >> dir;

if (_mkdir(dir.c_str()) == 0) {
cout << "Directory created." << endl;
} else {
cout << "Error creating directory. It may already exist or be invalid." << endl;
}
}

void change_dir() {
int command;
cout << "Change Directory Menu:" << endl;
cout << "1. Move one step back." << endl;
cout << "2. Move to the root directory." << endl;
cout << "3. Move to a specific directory provided by the user." << endl;
cout << "Enter your choice: ";
cin >> command;

switch (command) {
case 1:
if (_chdir("..") == 0) {
cout << "Moved to parent directory." << endl;
} else {
cout << "Error moving to parent directory." << endl;
}
break;
case 2:
if (_chdir("\\") == 0) {
cout << "Moved to root directory." << endl;
} else {
cout << "Error moving to root directory." << endl;
}
break;
case 3: {
string dir;
cout << "Directory name: ";
cin >> dir;
if (_chdir(dir.c_str()) == 0) {
cout << "Directory changed successfully." << endl;
} else {
cout << "Error changing directory. It may not exist." << endl;
}
break;
}
default:
cout << "Invalid, Try again." << endl;
}
}
