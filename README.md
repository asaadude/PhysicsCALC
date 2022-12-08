# PhysicsCALC
#include <iostream>
#include <cstdlib>
#include <cmath>
#include<string>
#include <sstream>
  #include "Validate.h"
using namespace std;

void optionMenu();
void ifOptions(char);
void motMenu(char);
string calVelocity( double, double, string, string);
string calAcc(double, double, string, string);


void optionMenu(){
  
  
  cout << "\nA: Find Velocity";
  cout << "\nB: Find Acceleration";
  cout << "\nC: Find Motion(Motion Menu)";
  cout << "\nD: Find Force";
  cout << "\nE: Find Weight";
  cout << "\nF: Find Momentum";
  cout << "\n\n Please enter a character from above (A-F)";

  
}




void motMenu(){
  cout << "\nA: Solve for Velocity";
  cout << "\nB: Solve for Speed";
  cout << "\nC: Find V^2";
  cout << "\nD: Find V-BAR";
}

//THE BIG BOY

void ifOptions(string ifOption)
{
  double mass = 0.0;
   double speed =0.0;
  double time= 0.0;
  string dtime = "";
  string ddistance = "";
  double velocity = 0.0;
  double acceleration = 0.0;
  const double gravity = 9.81;
string dmass= " ";
  bool test = false;
  
    if(ifOption == "A" || ifOption == "a"){
      cout << "-----find the velocity of a function!!\n\n";
      cout << "Enter the distance:";
      speed = validateDouble(speed);
      cout << "Enter the time it took: ";
      time = validateDouble(time);
      cout << "enter the unit of measurement of distance: ";
      ddistance = validateString(ddistance);
      cout << "enter the unit of measurement of time: ";
      dtime = validateString(dtime);
      calVelocity(speed, time, ddistance, dtime);
    }
      
  else if(ifOption == "B" || ifOption == "b"){
    cout << "-----calculate the acceleration!!\n\n";
    cout << "Enter the final velocity: ";
    velocity = validateDouble(velocity);
    cout << "Enter the time it took: ";
      time = validateDouble(time);
      cout << "enter the unit of distance measurement used in the velocity: ";
      ddistance = validateString(ddistance);
      cout << "enter the unit of time measurement : ";
      dtime = validateString(dtime);
    calAcc(velocity, time, ddistance, dtime);
    
  }
    else if(ifOption == "C" || ifOption == "c"){
      string choice;
      double intialV;
      double intialS;
      motMenu();
      cout << "\n Please Enter a choice from above: ";
      choice = validateString(choice);


      
      if (choice == "A" || choice == "a"){
        cout << "-----Finding Velocity as a function of time\n\n";
        cout << "please enter the intial Velocity: ";
        intialV = validateDouble(intialV);
        cout << "please enter the acceleration: ";
        acceleration = validateDouble(acceleration);
        cout << "Please enter the time it took: ";
        time = validateDouble(time);
        cout << "Enter the unit of measurement of distance: ";
        ddistance = validateString(ddistance);
        cout << "Please enter the measurement of time: ";
        dtime = validateString(dtime);
        cout << "The velocity as a function of time is " << (intialV +(acceleration * time)) << " " 
          << ddistance << " per " << dtime <<  "^2";
      }
      else  if (choice == "B" || choice == "b"){
        cout << "-----Calculate position function!!\n\n";
        cout << "please enter the intial speed: ";
        intialS = validateDouble(intialS);
         cout << "please enter the intial velocity: ";
        intialV = validateDouble(intialV);
         cout << "please enter the time: ";
        time = validateDouble(time);
         cout << "please enter the acceleration: ";
        acceleration = validateDouble(acceleration);
        cout << "Enter the unit of measure meant of distance: ";
        ddistance = validateString(ddistance);
        cout << "postion is "<<intialS + (intialV * time) + (0.5*(acceleration * pow(time, 2))) << " " << ddistance ;
      }
      else  if (choice == "C" || choice == "c"){
        cout << "-----calculate v^2!!\n\n";
        cout << "please enter the intial velocity: ";
        intialV = validateDouble(intialV);
        cout << "please enter the intial speed: ";
        intialS = validateDouble(intialS);
         cout << "please enter the acceleration: ";
        acceleration = validateDouble(acceleration);
         cout << "Enter the distance: ";
      speed = validateDouble(speed);
         cout << "enter the unit of measurement of distance: ";
      ddistance = validateString(ddistance);
      cout << "enter the unit of measurement of time: ";
      dtime = validateString(dtime);
        cout << "V^2 is " << pow(intialV , 2) + ((2*acceleration) * (intialS - speed)) << " " 
          << ddistance << " per " << dtime;
        
      }
      else  if (choice == "D" || choice == "d"){
        cout << "-----calculate vBAR!!\n\n";
        cout << "enter velocity: ";
        velocity = validateDouble(velocity);
         cout << "please enter the intial velocity: ";
        intialV = validateDouble(intialV);
         cout << "enter the unit of measurement of distance: ";
      ddistance = validateString(ddistance);
      cout << "enter the unit of measurement of time: ";
      dtime = validateString(dtime);
        cout << "vBAR is " << 0.5 * (velocity + intialV) << " " << ddistance << " Per " << dtime;
      }


      
    }
    else if(ifOption == "D" || ifOption == "d"){
      cout << "-----Calculate Force!!n\n\n";
      cout << "Please enter the mass: ";
      mass = validateDouble(mass);
      cout << "please enter the acceleration: ";
        acceleration = validateDouble(acceleration); 
      cout << "enter the unit of measurement of time: ";
      dtime = validateString(dtime);
       cout << "enter the unit of measurement of distance: ";
      ddistance = validateString(ddistance);
       cout << "enter the unit of measurement of mass: ";
      dmass = validateString(dmass);
      cout << "The force is " << mass * acceleration << dmass << ddistance << " per " << dtime << "^2";
    }
    else if(ifOption == "E" || ifOption == "e"){
      cout << "-----Find weight!!\n\n";
      cout << "enter the mass: ";
      mass = validateDouble(mass);
      cout << "enter the measurement of mass: ";
      dmass = validateString(dmass);
      cout << "the weight is " << mass * gravity << " " << dmass;
    }
   else if(ifOption == "F" || ifOption == "f"){
     cout << "-----Find Momentum!!\n\n";
     cout << "enter the mass: ";
      mass = validateDouble(mass);
      cout << "enter velocity: ";
      velocity = validateDouble(velocity);
      cout << "enter the unit of measurement of distance: ";
      ddistance = validateString(ddistance);
       cout << "enter the unit of measurement of mass: ";
      dmass = validateString(dmass);
     cout << "The Momentum is " << mass * velocity << dmass << ddistance << " per " << dtime;
     
   } else{
cout << "\nPlease Restart Your Program and Enter a Valid option!";

     }
  }
  



// CALCULATION FUNCTIONS

  string calVelocity (double s, double t, string ds, string dt){
    double v = s / t;
    cout << "The Velocity is " << v <<" "<< ds << " per " << dt;
    string blank;
    return blank;
  }
  string calAcc(double v, double t, string dd, string dt){
    double a = v / t;
    cout << "The acceleration is " <<  a <<" " << dd << " per " << dt << "^2";
    string blank;
    return blank;
  } 
  
