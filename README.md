<div align="center">

## AI\_Attempt


</div>

### Description

Attempts to simulate AI. This is my very first time trying to make an AI, so please vote.
 
### More Info
 
The enter button.

The status of the AI.


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[Donny Beals](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/donny-beals.md)
**Level**          |Advanced
**User Rating**    |3.5 (21 globes from 6 users)
**Compatibility**  |Microsoft Visual C\+\+
**Category**       |[Algorithms](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/algorithms__3-29.md)
**World**          |[C / C\+\+](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/c-c.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/donny-beals-ai-attempt__3-5740/archive/master.zip)

### API Declarations

```
#include <iostream.h>
#include <string.h>
#include <stdlib.h>
#include <conio.h>
#include <windows.h>
#include <time.h>
```


### Source Code

```
#include <iostream.h>
#include <string.h>
#include <stdlib.h>
#include <conio.h>
#include <windows.h>
#include <time.h>
enum States{ Hungry = 0,Diseased,Wandering,Dead,Searching,Found=5};
class g_StateManager
{
public:
	char Current[35];
	States sCurrent;
	States Determiner;
}SM;
static int Count = -1;
void StateChange(States* Dtrmnr = &SM.Determiner);
void StateDisplay();
void DisplayDeadMessage();
int r;
int main()
{
	SM.sCurrent = Wandering;
	SM.Determiner = Wandering;
	while(SM.sCurrent != Dead)
	{
		StateChange();
		StateDisplay();
		getch();
	}
	return 0;
}
void StateChange(States* Dtrmnr)
{
	switch(*Dtrmnr)
	{
		case Hungry:
			srand((unsigned)time(NULL));
			r = rand() % 2;
			switch(r)
			{
			case 0:
				strcpy(SM.Current,"Searching for food...");
				SM.sCurrent = Searching;
				SM.Determiner = Searching;
				Count++;
				return;
				break;
			case 1:
				strcpy(SM.Current,"Dead");
				SM.sCurrent = Dead;
				SM.Determiner = Dead;
				Count++;
				return;
				break;
			}
			return;
			break;
		case Diseased:
			srand((unsigned)time(NULL));
			r = rand() % 2;
			switch(r)
			{
			case 0:
				strcpy(SM.Current,"Looking for cure...");
				SM.sCurrent = Searching;
				SM.Determiner = Searching;
				Count++;
				return;
				break;
			case 1:
				strcpy(SM.Current,"Dead");
				SM.sCurrent = Dead;
				SM.Determiner = Dead;
				Count++;
				return;
				break;
			}
			return;
			break;
		case Wandering:
			r = rand() % 2;
			switch(r)
			{
			case 0:
				strcpy(SM.Current,"I'm hungry...");
				SM.sCurrent = Hungry;
				SM.Determiner = Hungry;
				Count++;
				return;
				break;
			case 1:
				strcpy(SM.Current,"Now I have something to search for!");
				SM.sCurrent = Searching;
				SM.Determiner = Searching;
				Count++;
				return;
				break;
			}
			return;
			break;
		case Searching:
			srand((unsigned)time(NULL));
			r = rand() % 2;
			switch(r)
			{
			case 0:
				strcpy(SM.Current,"Still searching...");
				SM.sCurrent = Searching;
				SM.Determiner = Searching;
				Count++;
				return;
				break;
			case 1:
				strcpy(SM.Current,"Found it!");
				SM.sCurrent = Found;
				SM.Determiner = Found;
				Count++;
				return;
				break;
			}
			return;
			break;
		case Found:
			srand((unsigned)time(NULL));
			r = rand() % 2;
			switch(r)
			{
			case 0:
				strcpy(SM.Current,"I'm hungry!");
				SM.sCurrent = Hungry;
				SM.Determiner = Hungry;
				Count++;
				return;
				break;
			case 1:
				strcpy(SM.Current,"I don't feel so good!");
				SM.sCurrent = Diseased;
				SM.Determiner = Diseased;
				Count++;
				return;
				break;
			}
			break;
		default:
			strcpy(SM.Current,"Dead");
			SM.sCurrent = Dead;
			return;
			break;
	}
	return;
}
void StateDisplay()
{
	system("CLS");
	cout<<"Current state:"<<SM.Current<<endl;
	cout<<"Current state:"<<SM.sCurrent<<endl;
	cout<<"State changes:"<<Count<<endl;
	return;
}
```

