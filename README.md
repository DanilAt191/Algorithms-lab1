# Algorithms-lab1
№5

  Base level:
    #include <iostream>
    #include <string>

struct Tovar
{
	char T[52];
	char F[20];
	int year;
	int kol;
	int price;
};

using namespace std;
int main()
{
	const int N = 3;
	double sumprice = 0;
	setlocale(LC_ALL, "");
	Tovar group[N];
	for (int i = 0; i < N; i++)
	{
		cout << "Введите товар: ";
		cin.ignore(std::cin.rdbuf()->in_avail());
		cin.getline(group[i].T, 52);

		cout << "Введите изготовителя: ";
		cin.ignore(std::cin.rdbuf()->in_avail());
		cin.getline(group[i].F, 20);

		cout << "Введите год: ";
		cin.ignore(std::cin.rdbuf()->in_avail());
		cin>>group[i].year;

		cout << "Введите количество: ";
		cin.ignore(std::cin.rdbuf()->in_avail());
		cin>>group[i].kol;

		cout << "Введите цену: ";
		cin.ignore(std::cin.rdbuf()->in_avail());
		cin>>group[i].price;
		cout << endl;

		cin.clear();
	}
	for (int i = 0; i < N; i++)
	{
		if (group[i].year == 2020)
		{
			cout << "Товар: " << group[i].T << '\n';
			cout << "Изготовитель: " << group[i].F << '\n';
			cout << "Год: " << group[i].year << '\n';
			cout << "Количество: " << group[i].kol << '\n';
			cout << "Цена: " << group[i].price << '\n';
			cout << endl;

			sumprice += group[i].kol * group[i].price;
		}
		
	}
	cout << "Общаяя стоимость: " << sumprice;
}

Intermediate level:

  #include <iostream>
using namespace std;
struct Date {
	short day;
	short month;
	short year;
	bool isCorrect();
};

bool Date::isCorrect()
{
	bool result = false;
	switch (month)
	{
		case 1:
		case 3:
		case 5:
		case 7:
		case 8:
		case 10:
		case 12:
		{
			if ((day <= 31) && (day > 0))
				result = true;
			break;
		}

		case 4:
		case 6:
		case 9:
		case 11:
		{
			if ((day <= 30) && (day > 0))
				result = true;
			break;
		}

		case 2:
		{
			if (year % 4 != 0)
			{
				if ((day <= 28) && (day > 0))
					result = true;
			}
			else
				if (year % 400 == 0)
				{
					if ((day <= 29) && (day > 0))
						result = true;
				}
				else
					if ((year % 100 == 0) && (year % 400 != 0))
					{
						if ((day == 28) && (day > 0))
							result = true;
					}
					else
						if ((year % 4 == 0) && (year % 100 != 0))
							if ((day <= 29) && (day > 0))
								result = true;
			break;
		}

		default:
			result = false;
	}

	return result;
}

struct Workers
{
	char F[56];
	char I[32];
	char O[32];
	char dol[56];
	char zar[12];
	Date birthday;
};

int main()
{
	setlocale(LC_ALL, "");
	const int N = 3;
	Workers group[N];

	for (int i = 0; i < N; i++)
	{
		cout << "Введите фамилию: ";
		cin.ignore(std::cin.rdbuf()->in_avail());
		cin.getline(group[i].F, 56);

		cout << "Введите имя: ";
		cin.ignore(std::cin.rdbuf()->in_avail());
		cin.getline(group[i].I, 32);

		cout << "Введите отчество: ";
		cin.ignore(std::cin.rdbuf()->in_avail());
		cin.getline(group[i].O, 32);

		cout << "Введите должность: ";
		cin.ignore(std::cin.rdbuf()->in_avail());
		cin.getline(group[i].dol, 56);

		cout << "Введите зарплату: ";
		cin.ignore(std::cin.rdbuf()->in_avail());
		cin.getline(group[i].zar, 12);

		cout << "Введите дату рождения: ";
		do 
		{
			cin.ignore(std::cin.rdbuf()->in_avail());
			cin >> group[i].birthday.day >> group[i].birthday.month >> group[i].birthday.year;
		} while (!group[i].birthday.isCorrect());
		cout << endl;
		cin.clear();
	}

	for (int i = 0; i < N; i++)
	{
		if (group[i].birthday.month == 5)
		{
			cout << "Ф.И.О : " << group[i].F << " " << group[i].I << " " << group[i].O<<'\n';
			cout << "Должность: " << group[i].dol<<'\n';
			cout << "Зарплата: " << group[i].zar << '\n';
			cout << "Дата рождения: " << group[i].birthday.day << "." << group[i].birthday.month << "." << group[i].birthday.year<<'\n';
		}
	}
}


