#include <iostream>
#include <cmath>
#include <string>
#include <algorithm>  
#define M_PI 3.141592653589793238462643383279502884197169399375105820974944592307816406286

using namespace std;

void pythagorus(double* A = 0, double* O = 0, double* H = 0){ //Uses pythagoruses theorem to find the missing side(s)
    if (*H == 0){
        *H = sqrt((pow(*A,2) + pow(*O,2)));
    } else if (*O == 0){
        *O = sqrt((pow(*H,2) - pow(*A,2)));
    } else if (*A == 0) {
        *A = sqrt((pow(*H,2) - pow(*O,2)));
    }
}

void main(){
    cout << "         /|" << endl; //Prints triangle
    cout << "        /y|" << endl;
    cout << "     H /  |" << endl;
    cout << "      /   | O" << endl;
    cout << "     /    |" << endl;
    cout << "    /)x   |" << endl;
    cout << "    -------" << endl;
    cout << "       A" << endl;

    char options[] = {'H', 'A', 'O', 'x', 'y'}; //Identifies the variables that can be worked out
    char firstKnownType, secondKnownType;
    double valA, valO, valH, valX, valY;
    double* ptrFirstVal, *ptrSecondVal;
    valA = 0;
    valO = 0;
    valH = 0;
    valX = 0;
    valY = 0;
    bool validEntry = false;
    while (!validEntry){
        cout << "What is one piece of information you know, H,A,O,x,y? "; //Asks the user one piece of information they know
        cin >> firstKnownType;

        char * p;
        p = find (options, options+5, firstKnownType);
        if (p == options+5){
            cout << "Invalid entry, try again!" << endl;
        } else{
            validEntry = true;
        }
    }

    if (firstKnownType == 'x'){
        options[3] = NULL;
        options[4] = NULL;
        ptrFirstVal = &valX;
    } else if (firstKnownType == 'y'){
        options[3] = NULL;
        options[4] = NULL;
        ptrFirstVal = &valY;
    } else if (firstKnownType == 'H'){
        options[0] = NULL;
        ptrFirstVal = &valH;
    } else if (firstKnownType == 'A'){
        options[1] = NULL;
        ptrFirstVal = &valA;
    } else{
        options[2] = NULL;
        ptrFirstVal = &valO;
    }

    cout << "What is the value of " << firstKnownType << "? ";
    cin >> *ptrFirstVal;

    validEntry = false;
    while (!validEntry){
        cout << "What is another piece of information you know?";
        cin >> secondKnownType;

        char * p;
        p = find (options, options+5, secondKnownType);
        if (p == options+5 && secondKnownType){
            cout << "Invalid entry, try again!" << endl;
        } else{
            validEntry = true;
        }
    }

    if (secondKnownType == 'x'){
        options[3] = NULL;
        ptrSecondVal = &valX;
    } else if (secondKnownType == 'y'){
        options[4] = NULL;
        ptrSecondVal = &valY;
    } else if (secondKnownType == 'H'){
        options[0] = NULL;
        ptrSecondVal = &valH;
    } else if (secondKnownType == 'A'){
        options[1] = NULL;
        ptrSecondVal = &valA;
    } else{
        options[2] = NULL;
        ptrSecondVal = &valO;
    }

    cout << "What is the value of " << secondKnownType << "? ";
    cin >> *ptrSecondVal;

    if (valX == 0 && valY == 0){
        pythagorus(&valA, &valO, &valH);
        
        valX = asin((valO/valH)) * 180 / M_PI;
        valY = 90 - valX;
    } else if (valX > 0){
        double angle_radians = valX * M_PI  / 180.0;
        valY = 90 - valX;
        if (valH > 0){
            valO = sin(angle_radians) * valH;
        } else if (valA > 0){
            valH = valA / cos(angle_radians);
        } else if (valO > 0){
            valH = valO / sin(angle_radians);
        }
        pythagorus(&valA, &valO, &valH);
    } else if (valY > 0){
        valX = 90 - valY;
        double angle_radians = valX * M_PI  / 180.0;
        if (valH > 0){
            valO = sin(angle_radians) * valH;
        } else if (valA > 0){
            valH = valA / cos(angle_radians);
        } else if (valO > 0){
            valH = valO / sin(angle_radians);
        }
        pythagorus(&valA, &valO, &valH);
    }    

    cout << "H = " << valH << endl;
    cout << "A = " << valA << endl;
    cout << "O = " << valO << endl;
    cout << "x = " << valX << endl;
    cout << "y = " << valY << endl;
}
