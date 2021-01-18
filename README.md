#include <iostream>
using namespace std;
struct app  //creating a struct to store details of the applications
{
string name, author, publisher;
int yearpub, price;
float version;
};
void print(struct app b) //function to print the details of a application
{
cout << "Name : " << b.name << endl;
cout << "Author : " << b.author << endl;
cout << "Version : " << b.version << endl;
cout << "Publisher :"<<b.publisher<<endl;
cout << "Year of publishing : " << b.yearpub << endl;
cout << "Price : " << b.price << endl;
}
struct app input() //function to input the details of a application from the user
{
struct app b;
cout << "Enter the name, author, version, publisher, year of publishing and price: " << endl;
cin >> b.name;
cin >> b.author;
cin >> b.version;
cin >> b.publisher;
cin >> b.yearpub;
cin >> b.price;
return b;
}
int main()
{
int n,i,j,y;
string s;
cout << "Enter the no of applications : " << endl;
cin >> n; //taking number of applications as input
struct app a[n]; //creating an array of applications
for(i=0;i<n;i++)  //taking the details of the applications as input from user
a[i]=input();
cout  << "Enter 1 to find all applications written by an author" << endl 
<< "Enter 2 to sort details of application in increasing order of price" << endl 
<< "Enter 3 to find all applications published by a publisher in a year" << endl 
<< "Enter 4 to sort details of application in increasing order of author and year of publishing" <<endl;
//displaying the menu and taking the choice of user as input
int choice;
cin >> choice;
switch(choice)
{
case 1:
cout << "Enter the author : " << endl;
cin >> s;
cout << "Applications by " << s << " are as follows :" << endl;
for(i=0;i<n;i++)
{
if(a[i].author==s)  //checking all the applications for input author and printing them
print(a[i]);
}
break;
case 2:
for(i=0;i<n-1;i++)
{
for(j=0;j<n-i-1;j++)
{
if (a[j].price>a[j+1].price) //sorting all the applications by price
{
struct app temp;
temp=a[j];
a[j]=a[j+1];
a[j+1]=temp;
}
      	}
}
cout << "Applications sorted by price are as follows :" << endl;
for(i=0;i<n;i++)
{
print(a[i]);
}
break;
case 3:
cout << "Enter the publisher and year of publishing : " << endl;
cin >> s;
cin >> y;
cout << "Applications  published by " << s << " in the year " << y << " are as follows :" << endl;
for(i=0;i<n;i++)
{
if(a[i].publisher==s && a[i].yearpub==y) //checking all the applications for input publisher and input year and printing them
print(a[i]);
}
break;
case 4:
for(i=0;i<n-1;i++)
{
for(j=0;j<n-i-1;j++)
{
if (a[j].author>a[j+1].author) //sorting all the applications by author
{
struct app temp;
temp=a[j];
a[j]=a[j+1];
a[j+1]=temp;
}
}
}
cout << "Applications sorted by author are as follows :" << endl;
for(i=0;i<n;i++)
{
print(a[i]);
}
for(i=0;i<n-1;i++)
{
for(j=0;j<n-i-1;j++)
{
if (a[j].yearpub>a[j+1].yearpub) //sorting all the applications by publishing year
{	
struct app temp;
temp=a[j];
a[j]=a[j+1];
a[j+1]=temp;
}
}
}
cout << "Applications sorted by publishing year are as follows :" << endl;
for(i=0;i<n;i++)
{
print(a[i]);
}
break;
default:
cout << "Wrong Input!" << endl;
}
return 0;
}
