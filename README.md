#include<iostream>
#include"stdio.h"
#include"string.h"

//made by Four_minutes (2017.05.24)

using namespace std;

int WhatIsOrder(char op)
{

	int num = 0;

	switch (op)
	{
	case '+':
		num = 1;
		break;
	case '-':
		num = 2;
		break;
	case '*':
		num = 3;
		break;
	case '/':
		num = 4;
		break;
	}

	return num;
}

float Answer(char equation[])
{
	char Temp;
	int length = strlen(equation);

	int sum = 0;

	for (int i = 0; i<length; i++)
	{

		Temp = equation[i];

		if (isdigit(Temp) == false)
		{
			if (WhatIsOrder(Temp) == 3)
			{
				sum =+ (equation[i - 1]-'0') * (equation[i+1] - '0') ;
				equation[i - 1] = '0';
				equation[i + 1] = '0';
			}
			else if (WhatIsOrder(Temp) == 4)
			{
				sum = +(equation[i - 1] - '0') * (equation[i + 1] - '0');
				equation[i - 1] = '0';
				equation[i + 1] = '0';
			}
		}


	}

	for (int i = 0; i<length; i++)
	{
		Temp = equation[i];
		
		if (isdigit(Temp))
		{
			if (i == 0)
			{
				sum = (sum + (Temp - '0'));
			}
			if (WhatIsOrder(equation[i - 1]) == 1)
			{
				sum = (sum + (Temp - '0'));
			}
			else if (WhatIsOrder(equation[i - 1]) == 2)
			{
				sum = (sum - (Temp - '0'));
			}
		}
	}

	return sum;
}

int main(void)
{
	while (true)
	{
		char equation[100];

		cout << "Enter : ";
		cin >> equation;

		if (equation[0] == 'e')
			break;

		cout << Answer(equation) << endl;
	}

	return 0;

}
