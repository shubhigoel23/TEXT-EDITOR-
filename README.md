#include<iostream>
#include<conio.h>
#include<fstream>
#include<string.h>
#include<windows.h>
char fname[100];
void replace(char*);
void find(char*);
void background();
void append();
using namespace std;

create_file(char *fname)
{
	ofstream f;
	char data[10000];
	int i;
	
	
	cout<<"Press 1.text file\t2.html\t3.cpp file\t4.exe\n";
	cin>>i;
	switch(i)
	{
		case 1:
		strcat(fname,".txt");
		break;
		case 2:
		strcat(fname,".html");
		break;
		case 3:
		strcat(fname,".cpp");
		break;
		case 4:
		strcat(fname,".exe");
		break;
	
			
	}
	
	
	fflush(stdin);
	
	f.open(fname);
	cout<<"Type Text for your file and press enter key to save it: ";
	cin.getline(data,100000);
	f<<data;
		fflush(stdin);
	cout<<"Data written successfully press return key to save it\n";
	getch();
	fname=NULL;
	

   }
  


open(char *fname)
{
	ifstream f;
	int c;
	char *data=new char[10000];
	f.open(fname);
	//add fails when no file is present of the fname.
	while(f)
	{
	f.getline(data,10000);
puts(data);
	}int ci;
	cout<<"1.replace\t2.find\t3.Append\t4.Background and Text\t4.Exit"<<endl;
ci=getch();
fflush(stdin);
switch(ci)
{
    case '1':
    replace(fname);
    break;
    case '2':
    find(fname);
    break;
	case '3':
	background;
	break;
	case'4':
		exit(0);
		
	
		
	}
	while(ci==0);

	f.close();
}

void background()
{
	char *ch=new char[100];
	char *ch2=new char[100];
	cout<<"0 = Black\n8 = Gray\n1 = Blue\n9 = Light Blue\n2 = Green\nA = Light Green\n3 = Aqua\nB = Light Aqua\n4 = Red\nC = Light Red\n5 = Purple\nD = Light Purple\n6 = Yellow\nE = Light Yellow\n7 = White\nF = Bright White";
	cout<<"\nMake a combination from above option line 4a(4 for background and a for text)\n";
	cout<<"\nType a combination:";
	gets(ch);
	strrev(ch);
	ch2=strrev(strcat(ch," roloc"));
system(ch2);
cout<<"Press enter to exit";
	getch();
	
}
void replace(char *fname)
{

	char word[10000],data2[10000],*newdata,newword[10000];
	
	fstream f(fname,ios::in|ios::out);
	int count=0,pos[100];
cout<<"\nWhich word you wanna replace:";
cin>>word;
cout<<"\nWhich word you wanna place:";
cin>>newword;

	while(f)
	{
		f>>data2;
		
			if(strcmp(data2,word)==0)
			{
				newdata=newword;
			}
			else
			{
				newdata=data2;
			}
	
			cout<<newdata<<" ";
		
			

	}
}
void find(char *fname)
	{
			char word[10000],data2[10000];
	
	fstream f(fname,ios::in|ios::out);
	int count=0,pos[100];
	cout<<"which word u want to find: ";
	cin>>word;
	int count1=0;
	while(f)
	{
		f>>data2;
		
			if(strcmp(data2,word)==0)
			{
				HANDLE hConsole = GetStdHandle(STD_OUTPUT_HANDLE);
  int k=12;
  count1++;
    // pick the colorattribute k you want
    SetConsoleTextAttribute(hConsole, k);
    cout << word << endl;
		goto nextline;
		}
	cout <<" "<< data2 ;
	nextline:;
	}
	if(count1==0)
	{
		cout<<"\nword not found";
	}
	
}

int main()
{
char ch;
int i=0;

	do
	{
		fflush(stdin);
		system("cls");
	cout.width(55);
	label:
cout<<"--Text Editor--"<<endl;
cout<<"1.New File\t2.Replace\t3.Find\t4.Append\t5.Background and Text\t6.Open\t7.Exit"<<endl;
ch=getch();
fflush(stdin);
switch(ch)
{
	case '1':
		cout<<"Enter file name:";
		cin>>fname;
		create_file(fname);
		break;
	case '2':
	     replace(fname);
		 break;
		 
	case '3':
	     find(fname);
		 break;
		 /*
	case '4':
	     append();
		 break;	*/ 	 	
	case '5':
	     background();
	     break;
	     
	case '6':
		fflush(stdin);
	     cout<<"Enter file name:";
		cin>>fname;
		 open(fname);
		 break;
		 
    case '7':
		 exit(0);
		 break; 
}
}
while(i==0);
	getch();

}

