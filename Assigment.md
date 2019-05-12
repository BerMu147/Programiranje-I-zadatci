# Programiranje-I-zadatci-Basic C++
Some solutions of assignments

#include<iostream>
#include<iomanip>
#include<Windows.h>
#include<conio.h>
#include<ctime>

using namespace std;

//Zbir prve i zadnje cifre
int Suma(int broj)
{
	int prvi = 0, zadnji= 0, suma = 0;
	zadnji = broj % 10;
	cout << "zadnji broj je: " << zadnji << endl;
	do
	{
		broj % 10;
		broj /= 10;
		prvi = broj;
	} while (broj >= 9);
	cout << "prvi broj je: " << prvi << endl;
	suma = zadnji + prvi;
	cout << "suma dva broja iznosi: ";
	return suma;
}
int main()
{
	int broj;
	cout << "Unesite minimalno trocifreni broj: ";
	do {
		cin >> broj;
	}while(broj <= 100);

	cout << Suma(broj) << endl;

	system("pause");
	return 0;
}

//10 karaktera, izbroj velike, male i ostale unesene
int main()
{
	char n;
	int brojacV = 0, brojacM = 0, brojacO = 0;
	cout << "Unesite 10 karaktera: " << endl;
	for (char i = 0; i < 10; i++)
	{
		cin >> n;
		if (n >= 'A' && n <= 'Z')
			brojacV++;
		else if (n >= 'a' && n <= 'z')
			brojacM++;
		else
			brojacO++;
	}
	cout << "Velikih slova uneseno: " << brojacV << endl;
	cout << "Malih slova uneseno: " << brojacM << endl;
	cout << "Ostalih uneseno: " << brojacO << endl;

	system("pause");
	return 0;
}

//Obrni broj i saberi svako drugu cifru
int obrni(int broj)
{
	int obrnuti = 0, temp;
	while (broj != 0)
	{
		temp = broj % 10;
		obrnuti = obrnuti * 10 + temp;
		broj /= 10;
	}
	cout << "Obrtnuti iznosi: ";
	return obrnuti;
}

int sumiraj(int broj)
{
	int suma = 0, temp = 0;
	while (broj != 0)
	{
		temp = broj % 10;
		suma += temp;
		broj /= 100;
	}
	cout << "Suma svakog drugog broja iznosi: ";
	return suma;
}

int main()
{
	int broj;
	cout << "Unesite broj veci od 9: ";
	do {
		cin >> broj;
	} while (broj < 10);

	cout << obrni(broj);
	cout << endl;
	cout << sumiraj(broj);
	cout << endl;

	system("pause");
	return 0;
}

/*Napišite program, poštujuæi sve faze procesa programiranja u kojem æete za uneseni prirodni broj n izraèunati sumu:
S=1!/3¨2 + 2!/5'2+... n!/(2n+1)'2*/
int faktorijel(int n)
{
	int fkt = 1;
	for (int i = 1; i <= n; i++)
	{
		fkt *= i;
	}
	return fkt;
}
float suma(int n)
{
	float s = 0;
	for (int i = 0; i < n; i++)
	{
		s += faktorijel(i) /pow ((2*n+1),2);
	}
	return s;
}

int main()
{
	int n;
	cout << "Unesite granicu n: ";
	cin >> n;
	cout << "Suma iznosi: " << suma(n) << endl;
	system("pause");
	return 0;
}

/*Napišite program, poštujuæi sve faze procesa programiranja u kojem æete omoguæiti unos dva prirodna broja.
Provjerite èine li uneseni brojev prijateljski par. Prirodni brojevi a i b èine prijateljski par brojeva ako je zbir pravih
djelitelja broja a (oni koji su manji od a) jednak broju b i istovremeno zbir pravih djelitelja broja b jednak je broju a.
Npr. Brojevi 220 i 284 su prijateljski brojevi
Pravi djelitelji broja 220 su:1,2,4,5,10,20,22,50,110, anjihova suma iznosi 284;
Pravi djelitelji broja 284 su: 1,2,4,71,142, a njihova suma iznosi 220;
Upotijebite funckije:
int sumaPravihDjelitelja(int);
bool provjera(int,int);
*/
int SumaPD(int m)
{
	int suma = 0;
	for (int i = 1; i <= m/2; i++)
	{
		if (m%i == 0)
			suma += i;
	}
	return suma;
}
bool provjera(int m, int n)
{
	if ((SumaPD(m) == n) && (SumaPD(n) == m))
	{
		cout << "Prijateljski" << endl;
		return true;
	}
	else
	{
		cout << "Nisu Prijateljski" << endl;
		return false;
	}
}
int main()
{
	int m, n;
	cout << "Unesite dva broja: ";
	cin >> m >> n;
	(provjera(m, n));
	system("pause");
	return 0;
}

/*Napišite program, poštujuæi sve faze procesa programiranja, koji mogucava da se ispisu svi brojevi koji zadovoljavaju
uvjet da im je zapis jednak zapisu posljednjih znamenki njihovog kvadrata. (Npr 6'2=36, 25'2=625).
Provjeru vrsiti za prvih 150 prirodnih brojeva.
Upotrijebite funckiju:
bool provjera(int); */

bool provjera(int a)
{
	int temp = pow(a, 2);
	if (a < 10)
	{

		if (a == temp % 10)
			return true;
		else
			return false;
	}
	else if (a >= 10)
	{
		if (a == temp % 100)
			return true;
		else
			return false;
	}
}

int main()
{
	for (int i = 0; i < 150; i++)
	{
		if (provjera(i))
			cout << i << endl;
	}

	system("pause");
	return 0;
}

/*Napišite program, poštujuæi sve faze procesa programiranja, u kojem cete omoguciti unos prirodnog broja.
Provjerite je li broj trivijalan(prost) uz pomoc funckije:
bool trivijalan(int);
u slucaju da broj NIJE trivijalan odredite i ispisite sve njegove djelitelje uz pomoc funkcije:
void djelitelj(int);
Napomena: Broje je trivijalan(prost) ako je djeljiv SAMO sa jedan i sa samim sobom. */

bool trivijalan(int n)
{
	for (int i = 2; i < n; i++)
	{
		if (n%i == 0)
			return false;
	}
	return true;
}

void djelitelj(int n)
{
	if (trivijalan(n) == false)
	{
		cout << "Broj nije prost, njegovi djeljitelji su: ";
		for (int i = 1; i < n; i++)
		{
			if (n%i == 0)
				cout << i << " ";
		}
	}
	else
	cout << n << " Broj je prost " << endl;
}

int main()
{
	int n;
	cout << "Unesite broj: ";
	cin >> n;

	djelitelj(n);
	cout << endl;

	system("pause");
	return 0;
}

/*Napišite program, koji će ispisati sve troznamenkaste brojeve koji su jednaki sumi
faktorijela svojih znamenki – ABC = A! + B! + C!
Upotrijebite funkcije:
bool provjera(int);
int faktorijel(int);*/

int faktorijel(int n)
{
	int fkt = 1;
	for (int i = 1; i <= n; i++)
	{
		fkt *= i;
	}
	return fkt;
}

bool provjera(int n)
{
	if (faktorijel)
		return true;
	else
		return false;
}

int main()
{
	int n;
	cin >> n;
	cout << faktorijel(n) << endl;

	system("pause");
	return 0;
}

/*Napišite program u kojem ćete deklarirati matricu 5x4. Redak u matrici je učenik, a kolona predmet. Uz pomoć funkcije:
* `void unos (int [] [4]);` omogućite unos samo prolaznih ocjena (2-5) za sve učenike;
* `float prosjek(int []);` izračunati prosječnu ocjenu učenika; za kojeg od učenika će se računati prosjek bira korisnik;
* `int prebroji (int [][4], int);` prebrojati koliko učenika ima ocjenu 4 i više na predmetu po izboru korisnika.*/

const int v1 = 5, v2 = 4;
void unos(int niz[v1][v2])
{
	for (int i = 0; i < v1; i++)
	{
		for (int j = 0; j < v2; j++)
		{
			cin >> niz[i][j];
		}
	}
}

float prosjek(int niz[])
{
	int suma = 0;
	cout << "Upisite broj ucenika: ";
	for (int i = 0; i < v1; i++)
	{
		cin >> i;
		if (i < 1 || i > 5) {
			cout << "Nepravilan unos." << endl;
			i--;
		}
		else
			for (int j = 0; j < v2; j++)
			{
				cout << niz[j] << " ";
				suma += niz[j];
			}
	}
	suma / v2;
	return suma;
}

int main()
{
	int niz[v1][v2];
	unos(niz);
	system("pause");
	return 0;
}

//Baratanje nizovima (sortiranje)

const int v = 5;

void unos(int niz[v])
{
	cout << "Unesite trocifrene clanove niza: " << endl;
	for (int i = 0; i < v; i++)
	{
		cin >> niz[i];
		if ((niz[i] < 100 || niz[i] > 999)) {
			cout << "ponovi unos" << endl;
			i--;
		}
	}
	cout << endl;
}

void ispis(int niz[v])
{
	cout << "Uneseni clanovi niza:" << endl;
	for (int i = 0; i < v; i++)
	{
		cout << niz[i] << " ";
	}
	cout << endl;
}

void sortiranje(int niz[v])
{
	int temp;
	bool promjena = true;
	while (promjena) {
		promjena = false;
		for (int i = 0; i < v; i++)
		{
			if (niz[i] < niz[i - 1]) {
				temp = niz[i];
				niz[i] = niz[i - 1];
				niz[i - 1] = temp;
				promjena = true;
			}
		}
	}
}

int main()
{
	int niz[v];
	unos(niz);
	ispis(niz);
	sortiranje(niz);
	ispis(niz);

	system("pause");
	return 0;
}

// Baratanje s 2D nizovima (transponse)
const int v = 4;

void unos(int niz[v][v])
{
	cout << "Unesite clanove niza: " << endl;
	for (int i = 0; i < v; i++)
	{
		for (int j = 0; j < v; j++)
		{
			cin >> niz[i][j];
		}
	}
	cout << endl;
}

void ispis(int niz[v][v])
{
	cout << "Uneseni 2D niz izgleda ovako: " << endl;
	for (int i = 0; i < v; i++)
	{
		for (int j = 0; j < v; j++)
		{
			cout << niz[i][j] << " ";
		}
		cout << endl;
	}
	cout << endl;
}

void transponuj(int niz[v][v])
{
	int niz2[v][v];
	for (int i = 0; i < v; i++)
	{
		for (int j = 0; j < v; j++)
		{
			niz2[i][j] = niz[i][j];
		}
	}
	for (int i = 0; i < v; i++)
	{
		for (int j = 0; j < v; j++)
		{
			niz[i][j] = niz2[j][i];
		}
	}
}

int main()
{
	int niz[v][v];
	unos(niz);
	ispis(niz);
	transponuj(niz);
	cout << endl;
	ispis(niz);

	system("pause");
	return 0;
}


/*Napišite program u kojem ćete deklarirati niz od 7 cijelih brojeva. Uz pomoć funkcije:
* `void unos (int [], int);` omogućite unos elemenata u niz;
* `float prosjecna(int [], int);` izračunati prosječnu vrijednost elemenata niza;
* `bool opadajuci (int [], int);` provjeriti jesu li elementi niza poredani u opadajuæem poretku (n1 > n2 > n3 > n4 > n5 > n6 > n7);*/

const int vel = 7;
void unos(int niz[])
{
	cout << "Unesite clanove niza: " << endl;
	for (int i = 0; i < vel; i++)
	{
		cin >> niz[i];
	}
	cout << endl;
}

float prosjecna(int niz[])
{
	float s = 0;
	for (int i = 0; i < vel; i++)
	{
		s += niz[i];
	}
	s = s / 7;
	return s;
}

bool opadajuci(int niz[])
{
	for (int i = 0; i < vel; i++)
	{
		if (niz[i] > niz[i + 1])
			return true;
		else
			return false;
	}
}

int main()
{
	int niz[vel];

	unos(niz);
	cout << "Prosjecna vrijednost elementa niza je: " << prosjecna(niz) << endl;
	cout << "Opadajuci (0-false, 1-true): " << opadajuci(niz) << endl;

	system("pause");
	return 0;
}

/*Napišite program u kojem ćete deklarirati matricu 5x4. Redak u matrici je student, a kolona predmet. Uz pomoć funkcije:
* `void unos (int [] [4]);` omogućite unos samo prolaznih ocjena (6-10) za sve studente;
* `float prosjek(int []);` izračunati prosječnu ocjenu jednog studenta; za kojeg od studenta će se računati prosjek bira korisnik;
* `int prebroji (int [][4], int);` prebrojati koliko studenata ima ocjenu 8 i više na predmetu po izboru korisnika.*/

void unos(int niz[5][4])
{
	cout << "Unesi studenta, zatim njegove prolazne ocjene ";
	for (int i = 0; i < 5; i++)
	{
		for (int j = 0; j < 4; j++)
		{
			cin >> niz[i][j];
			if (niz[i][j] < 6 || niz[i][j] > 10) {
				niz[j--];
				cout << "Ponovi unos" << endl;
			}
		}

	}
}

void ispis(int niz[][4])
{
	for (int i = 0; i < 5; i++)
	{
		for (int j = 0; j < 4; j++)
		{
			cout << niz[i][j] << "   ";
		}
		cout << endl;
	}
	cout << endl;
}

float prosjek(int niz[])
{
	float suma = 0;
	for (int i = 0; i < 5; i++)
	{
		suma += niz[i];
	}
	suma /= 5;
	return suma;
}

int prebroji(int niz[][4], int izbor)
{
	int brojac = 0;
	for (int i = 0; i < 4; i++)
	{
		if (niz[i][izbor - 1] >= 8)
			brojac++;
	}
	return brojac;
}

int main()
{
	int niz[5][4];
	int izbor, ponocniNiz[5];
	unos(niz);
	ispis(niz);

	cout << "Izaberi studenta za prosjek: ";
	cin >> izbor;
	for (int i = 0; i < 5; i++)
	{
		ponocniNiz[i] = niz[izbor - 1][i];
	}
	cout << "Prosjek studenta je: " << prosjek(ponocniNiz);
	cout << "Izaberi predmet: ";
	cin >> izbor;
	cout <<"Studenata koji ima ocjenu 8 ili vise: " << prebroji(niz, izbor) << endl;

	system("pause");
	return 0;
}

/*Dat je 2D niz koji simulira šahovsku tablu. Omogućiti korisniku unos cjelobrojnih elemenata 2D niza tako da se u
svako „crno“ polje unese parni broj
sa neparnim brojem cifara a u „bijelo“ polje neparni broj sa parnim brijem cifara.
Izračunati i ispisati prosjeke (aritmetičke sredine) svih elemenata na bijelim poljima iznad
glavne dijagonale te na crnim poljima ispod sporedne dijagonale.*/

const int vel = 4;
bool ParniBrcfr(int n)
{
	int brojac = 0;
	while (n > 0)
	{
		brojac++;
		n /= 10;
	}
	if (brojac % 2 == 0)
		return true;

	return false;
}

void unos(int niz[][vel])
{
	cout << "Unesite clanove: " << endl;
	for (int i = 0; i < vel; i++)
	{
		for (int j = 0; j < vel; j++)
		{
			int unos;
			cin >> unos;
			if ((((i % 2 == 0) && (j % 2 == 0)) || ((i % 2 != 0) && (j % 2 != 0))) && (ParniBrcfr(unos) == false && unos % 2 == 0))
			{
				niz[i][j] = unos;
			}
			else if ((((i % 2 == 0) && (j % 2 != 0)) || ((i % 2 != 0) && (j % 2 == 0))) && (ParniBrcfr(unos) == true && unos % 2 != 0))
			{
				niz[i][j] = unos;
			}
			else
			{
				j--;
				cout << "Ponovi unos";
			}
		}
		cout << endl;
	}
	cout << endl;
}

float aritmetickaB(int niz[][vel])
{
	float suma = 0;
	int brojac = 0;
	for (int i = 0; i < vel; i++)
	{
		for (int j = 0; j < vel; j++)
		{
			if (i < j)
			{
				if ((i % 2 == 0 && j % 2 != 0) || (i % 2 != 0 && j % 2 == 0))
				{
					suma += niz[i][j];
					brojac++;
				}
			}
		}
	}
	return suma / brojac;
}

float aritmerickaC(int niz[][vel])
{
	float suma = 0;
	int brojac = 0;
	for (int i = 0; i < vel; i++)
	{
		for (int j = 0; j < vel; j++)
		{
			if ((i + j) >= vel)
			{
				if ((i+j) % 2 == 0)
				{
					suma += niz[i][j];
					brojac++;
				}
			}
		}
	}
	return suma / brojac;
}

void ispis(int niz[][vel])
{
	cout << "Ispis 2D niza: " << endl;
	for (int i = 0; i < vel; i++)
	{
		for (int j = 0; j < vel; j++)
		{
			cout << niz[i][j] << " ";
		}
		cout << endl;
	}
	cout << endl;
}

int main()
{
	int niz[vel][vel];
	unos(niz);
	ispis(niz);

	cout << "Aritmeticka sredina bjelih polja iznad dijagonale: " << aritmetickaB(niz) << endl;
	cout << "Aritmeticka sredina crnih polja ispod dijagonale: " << aritmerickaC(niz) << endl;

	system("pause");
	return 0;
}

const int v = 4;

bool BrCfr(int n)
{
	int brojac = 0;
	while (n > 0)
	{
		brojac++;
		n /= 10;
	}
	if (brojac % 2 != 0)
		return true;

	return false;
}

void unos(int niz[][v])
{
	int unos;
	cout << "Unesite clanove niza sa neparnim brojem cifara: ";
	for (int i = 0; i < v; i++)
	{
		for (int j = 0; j < v; j++)
		{
			cin >> unos;
			if (BrCfr(unos) == true)
			{
				niz[i][j] = unos;
			}
			else
			{
				cout << "Ponovi unos: ";
				j--;
			}
		}
	}
	cout << endl;
}

void ispis(int niz[][v])
{
	cout << "Niz izgleda ovako: " << endl;

	for (int i = 0; i < v; i++)
	{
		for (int j = 0; j < v; j++)
		{
			cout << niz[i][j] << "   ";
		}
		cout << endl;
	}
	cout << endl;
}

float aritmetickaR(int niz[v])
{
	float suma = 0;
	int brojac = 0;
	for (int i = 0; i < v; i++)
	{
		suma += niz[i];
		brojac++;
	}
	return suma / brojac;

}
float aritmetickaC(int niz[v])
{
	float suma = 0;
	int brojac = 0;
	for (int j = 0; j < v; j++)
	{
		suma += niz[j];
		brojac++;
	}
	return suma / brojac;
}

int main()
{
	int niz[v][v];
	unos(niz);
	ispis(niz);
	cout << "Aritmeticka redova: " << aritmetickaR(niz[v]) << endl;
	cout << "Aritmeticka kolona: " << aritmetickaC(niz[v]) << endl;
	system("pause");
	return 0;
}

/* Napisati program koji će učitati elemente matrice dimenzija n x n (const int n vrijednost izaberite po želji)
te ispisati je li matrica centralno simetrična s obzirom na središnji element. Ako jest, program treba ispisati 1,
ako nije, ispisati 0, a ako je broj redova paran (pa nema središnjeg elementa), ispisati -1.
Koristiti zasebne funkcije za unos elemenata i provjeru simetričnosti.*/

const int n = 3;

void unos(int niz[][n])
{
	cout << "Unesi clanove matrice: " << endl;
	for (int i = 0; i < n; i++)
	{
		for (int j = 0; j < n; j++)
		{
			cin >> niz[i][j];
		}
	}
	cout << endl;
}

void ispis(int niz[][n])
{
	cout << "Ispis: " << endl;
	for (int i = 0; i < n; i++)
	{
		for (int j = 0; j < n; j++)
		{
			cout << niz[i][j] << "  ";
		}
		cout << endl;
	}
	cout << endl;
}

int provjera(int niz[][n])
{
	if (n % 2 == 0)
		return -1;


	for (int i = 0; i < n; i++)
	{
		for (int j = 0; j <  n; j++)
		{
			if (niz[i][j] != niz[n - i - 1][n - j - 1])
				return 0;
		}
	}
	return 1;
}

int main()
{
	int niz[n][n];
	unos(niz);
	ispis(niz);
	cout << provjera(niz) << endl;

	system("pause");
	return 0;
}

/*Provjerite jel broj trivijalan. Ako jest ispišite ga, ako nije, ispiši njegove djelitelje*/

bool trivijalan(int n)
{
	for (int i = 2; i < n; i++)
	{
		if (n % i == 0)
			return false;
	}
	return true;
}

int djelitelji(int n)
{
	int brojac = 0;
	if (trivijalan(n) == false)
	{
		for (int i = 1; i < n; i++)
		{
			if (n % i == 0) {
				cout << i << endl;
				brojac++;
			}
		}
	}
	return brojac;
}

int main()
{
	int n;
	cout << "Unesite broj: ";
	cin >> n;

	if (trivijalan(n) == false)
		cout << "Broj nije trivijalan. Ukupno Djelioca broja: " << djelitelji(n) << endl;
	else
		cout << "Uneseni broj je trivijalan" << endl;

	system("pause");
	return 0;
}

/*Napišite program, poštujuæi sve faze procesa programiranja, u kojem æete za uneseni prirodni
broj n izrčunati sumu: S = 1! + 2! + … +n!
Upotrijebite funkciju:
```cpp
float suma (int);
int faktorijel(int);*/

int faktorijel(int n)
{
	int fkt = 1;
	for (int i = 1; i <= n; i++)
	{
		fkt *= i;
	}
	return fkt;
}

float suma(int n)
{
	float sum = 0;
	for (int i = 1; i <= n; i++)
	{
		sum += faktorijel(i);
	}

	return sum;
}

int main()
{
	int n;
	cout << "Unesite broj: ";
	cin >> n;

	cout << "Faktorijel unesenog broja: " << faktorijel(n) << endl;
	cout << "Suma Faktorijela: " << suma(n) << endl;

	system("pause");
	return 0;
}

/*Poštujući sve faze procesa programiranja napraviti program koji pronalazi i ispisuje 
sve složene brojeve brojeve iz intervala m-n (10 < m < 100, 500 < n < 2000, m < n; 
ukoliko unesene vrijednosti nisu ispravne, učitavanje treba ponavljati), te pronalazi i ispisuje njihovu aritmetičku sredinu. Napraviti sljedeće funkcije:
* bool slozeni – koja će ispitivati da li je broj složeni i
* ispis – koja koja će ispisivati sve složene brojeve i vratiti main funkciji njihovu aritmetičku sredinu.

U glavnom programu je potrebno ispisati aritmetičku sredinu. 

Složeni broj je svaki broj koji nije prosti, odnosno koji ima bar jednog djelioca osim broja 1 i samog sebe.*/

bool slozen(int n, int m)
{
	for (int i = 2; i < m; i++)
	{
		if (m % i == 0)
			return true;
	}
	return false;
}

int ispis(int n, int m)
{
	int brojac = 0;
	float suma = 0;
	for (int i = m; i < n; i++)
	{
		if (slozen(n, m) == true)
		{
			cout << i << endl;
			suma += i;
			brojac++;
		}
	}
	return suma / brojac;
}
int main()
{
	int n, m;
	cout << "Unesite brojeve (10 < m < 100) i (500 < n < 2000) ";
	do {
		cin >> m >> n;
	} while ((m < 10 || m > 100) && (n < 500 || n > 2000));

	cout << slozen(n, m) << endl;
	cout << "Aritmeticka sredina brojeva iznosi: " << ispis(n, m) << endl;

	system("pause");
	return 0;
}

/*Napisati program koji će omogućiti unos minimalno trocifrenih cijelih brojeva u jednodimenzionalni niz od 20 elemenata. 
Zatim napraviti funkciju koja će u nizu pronaći sve brojeve kojima je prva cifra (početna cifra sa lijeve strane) parna i ukloniti ih iz niza. 
Uklanjanje elemenata niza obavezno uraditi tako da ne ostaju prazni elementi već da se ostatak niza pomjeri kako ne bi bilo prazni.
Pomjeranje ostatka niza niza obavezno raditi prilikom uklanjanja elemenata a ne sortiranjem poslije uklanjanja.*/

int v = 8;

void unos(int niz[])
{
	cout << "Unesite trocifrene clanove niza: " << endl;
	for (int i = 0; i < v; i++)
	{
		cin >> niz[i];
		if (niz[i] < 100)
		{
			niz[i--];
			cout << "Ponovi unos:" << endl;
		}
	}
	cout << endl;
}

void ispis(int niz[])
{
	for (int i = 0; i < v; i++)
	{
		cout << niz[i] << "   ";
	}
	cout << endl;
}

void ukloni(int niz[])
{
	int tmp;
	for (int i = 0; i < v; i++)
	{
		tmp = niz[i];
		while (tmp > 9)
		{
			tmp /= 10;
		}

		if (tmp % 2 != 0)
		{
			niz[i];
		}
	}
}

int main()
{
	int niz[8];
	unos(niz);
	ispis(niz);
	ukloni(niz);
	ispis(niz);

	system("pause");
	return 0;
}

/*Napišite program, poštujuæi sve faze procesa programiranja u kojem æete za uneseni prirodni broj n izraèunati sumu:
S=1!/3¨2 + 2!/5'2+... n!/(2n+1)'2
Upotrijebite funckije:
float suma(int);
int faktorijel(int);*/

int faktorijel(int n)
{
	int fkt = 1;
	for (int  i = 1; i <= n; i++)
	{
		fkt *= i;
		cout << fkt << endl;
	}
	return fkt;
}

float suma(int n)
{
	float sum = 0;
	for (int i = n; i <= n; i++)
	{
		sum += (faktorijel(i) / pow((2 * n + 1), 2));
		cout << sum << endl;
	}
	return sum;
}

int main()
{
	int n;
	cout << "Unesite broj: ";
	cin >> n;
	cout << "Faktorijel: " << faktorijel(n) << endl;
	cout << "Suma: " << suma(n) << endl;
	
	system("pause");
	return 0;
}

/*Napišite program, poštujuæi sve faze procesa programiranja, u kojem cete unijeti jedan prirodan broj koji predstavlja
vrijeme u minutama, a izracunati i ispisati koliko je to vremena u danima, satima i minutama.
Upotrijebite funckije:
int sati(int&);
int dani(int&);
Npr. ako korisnik unese 1520 minute program treba ispisati da je to 1 dan 1 sat i 20 minuta.
(1 sat=60 minuta, 1 dan= 24 sata=1440 minuta)
*/

int dani(int& n)
{
	int dan = 0;
	dan = n / 1440;
	n -= 1440 * dan;
	return dan;
}

int sati(int& n)
{
	int sat = 0;
	sat = n / 60;
	n -= 60 * sat;
	return sat;
}


int main()
{
	int n;
	cout << "Unesite broj minuta: ";
	cin >> n;
	cout << "Dani: " << dani(n) << endl;
	cout << "Sati: " << sati(n) << endl;
	cout << "Minute: " << n << endl;

	system("pause");
	return 0;
}

/* Poštujuæi sve faze procesa programiranje napisati program koji korisniku omoguæava unos cijelog broja N,
te izraèunava vrijednost sume faktorijela neparnih brojeva u intervalu[1, N] koji nisu djeljivi sa brojem 7.
Rezultat treba biti zaokružen na dvije decimale.Suma faktorijela prikazana je sljedeæom formulom
S = 1!+ 3!+ 5!+ … + N! */

int faktorijel(int n)
{
	int fkt = 1;
	float suma = 0;
	for (int i = 1; i <= n; i++)
	{
		fkt *= i;
		cout << "faktorijel: " <<fkt << endl;
		if (i % 2 != 0 && i % 7 != 0)
		{
			cout << "Broj koji se uracunava u sumu: " <<i << endl;
			suma += fkt;
		}
		cout << endl;
	}
	return suma;
}


int main()
{
	int n;
	cout << "Unesite krajnju vrijednost faktorijela: ";
	cin >> n;
	cout << "Suma faktorijela: " << setiosflags(ios::fixed) << setprecision(2) << faktorijel(n) << endl;
	// ukoliko se izostavi -setiosflags, rezultat nece biti citljiv
	// setprecision(2) znaci da se rezultat zaokruzi na dvije decimale
	// na faktorijel se dodaje *1.0 zbog decimala. Ukoliko rezultat nema decimalne vrijednosti, zaokruzit ce cjeli broj.

	system("pause");
	return 0;
}

/*Napisati program u kojem je potrebno unijeti odabrani broj znamenaka poèevši od znamenke najveæe težinske vrijednosti
pa od njih sastaviti i ispisati prirodni broj. Unos znamenaka se prekida kada se unese broj manji od 0 ili veæi od 9. 
Ispisati poruku ukoliko je dobiveni broj savršen. Ispis neka bude oblika:
Primjer izlaza:
Upisi znamenku:2
Upisi znamenku:8
Upisi znamenku:-1
...
Broj sastavljen od zadanih znamenaka je 28.
Broj je savršen.
Svršenim se naziva onaj prirodni broj kojim je zbroj pozitivnih djelitelja razlièitih od sebe samog jedanak samom tom broju.
Najmanji broj koji ima ovakva svojstva je broj 6. Zbroj njegovih djelitelja (osim broja 6) jednak je upravo tom broju.*/

bool savrsen(int n)
{
	int tmp = 0;
	for (int i = 1; i < n; i++)
	{
		if (n % i == 0)
			tmp += i;
	}
	if (n == tmp)
		return true;
	else
		return false;
}

int main()
{
	int n, temp, suma = 0;
	cout << "Unesite znamenke izmedju 0 i 9: " << endl;
	cin >> n;
	while (n > 0 && n < 9)
	{
		temp = n % 10;
		suma = suma * 10 + temp;
		cin >> n;
	}
	cout << "Unijeli ste broj " << suma << endl;
	if (savrsen(suma) == true)
		cout << "Broj je savrsen." << endl;
	else
		cout << "Broj nije savrsen." << endl;
	system("pause");
	return 0;
}

/*Šahovska tabla*/

const int v = 8;

bool paran(int unos)
{
	int brojac = 0;
	while (unos > 0)
	{
		brojac++;
		unos /= 10;
	}
	if (brojac % 2 == 0)
		return true;
	else
		return false;
}

void unos(int niz[][v])
{
	int unos;
	for (int i = 0; i < v; i++)
	{
		for (int j = 0; j < v; j++)
		{
			unos = rand() % 1000 + 1;
			if (((i % 2 == 0) && (j % 2 == 0)) || ((i % 2 != 0) && (j % 2 != 0)))
			{
				if ((paran(unos) == false) && (unos % 2 == 0))
					niz[i][j] = unos;
				else{
					j--;
					//cout << "Ponovi unos ";
				}
			}
			else if (((i % 2 != 0) && (j % 2 == 0)) || ((i % 2 == 0) && (j % 2 != 0)))
			{
				if ((paran(unos) == true) && (unos % 2 != 0))
					niz[i][j] = unos;
				else {
					j--;
					//cout << "Ponovi unos ";
				}
			}
		}
	}
}

void ispis(int niz[][v])
{
	for (int i = 0; i < v; i++)
	{
		for (int j = 0; j < v; j++)
		{
			cout << niz[i][j] << "   ";
		}
		cout << endl;
	}
	cout << endl;
}

int aritmetickaCrn(int niz[][v])
{
	float suma = 0;
	int brojac = 0;
	for (int i = 0; i < v; i++)
	{
		for (int j = 0; j < v; j++)
		{
			if (((i % 2 != 0) && (j % 2 == 0)) || ((i % 2 == 0) && (j % 2 != 0)))
			{
				suma += niz[i][j];
				brojac++;
			}
		}
	}
	return suma / brojac;
}

int aritmetickaBjl(int niz[][v])
{
	float suma = 0;
	int brojac = 0;
	for (int i = 0; i < v; i++)
	{
		for (int j = 0; j < v; j++)
		{
			if (i + j > v)
			{
				if (((i % 2 == 0) && (j % 2 == 0)) || ((i % 2 != 0) && (j % 2 != 0)))
				{
					suma += niz[i][j];
					brojac++;
				}
			}
		}
	}
	return suma / brojac;
}


int main()
{
	int niz[v][v];
	unos(niz);
	ispis(niz);

	cout << "Aritmeticka sredina crnih je: " << aritmetickaCrn(niz) << endl;
	cout << "Aritmeticka sredina bjelih je: " << aritmetickaBjl(niz) << endl;

	system("pause");
	return 0;
}

/*Unesi trocifrene clanove i sortiraj uzlazno po srednjoj cifri*/

const int vel = 7;

void unos(int niz[])
{
	cout << "Unesite clanove: " << endl;
	for (int i = 0; i < vel; i++)
	{
		cin >> niz[i];
		if (niz[i] < 100 || niz[i] > 999)
			i--;
	}
	cout << endl;
}

void ispis(int niz[])
{
	for (int i = 0; i < vel; i++)
	{
		cout << niz[i] << "  ";
	}
	cout << endl;
}

void sort(int niz[])
{
	int temp, cifra1, cifra2;
	bool promjena = true;
	while (promjena) {
		promjena = false;
		for (int i = 0; i < vel - 1; i++)
		{
			cifra1 = (niz[i] / 10) % 10;
			cifra2 = (niz[i + 1] / 10) % 10;
			if (cifra1 > cifra2)
			{
				temp = niz[i];
				niz[i] = niz[i + 1];
				niz[i + 1] = temp;
				promjena = true;
			}
		}
	}
}

int main()
{
	int niz[vel];

	unos(niz);
	ispis(niz);
	sort(niz);
	cout << "Nakon sortiranja, niz izgleda ovako: " << endl;
	ispis(niz);

	system("pause");
	return 0;
}

/*Napisati funkciju koja niz od 10 cijelih brojeva sortira u opadajućem ili rastućem poretku.
Unos elemenata niza se obavlja u glavnom programu, kao i odabir opcije koja određuje da li rezultirajući niz treba biti opadajući
ili rastući. Obavezno testirati implementiranu funkciju vodeći se datim primjerom ispisa.
(Pojasnjenje: Nema posebnog pojasnjenja jer se radi o najjednostavijem sortiranju uzlazno ili silazno u odnosu na korisnicki izbor.)

Unesite elemente niza: 12 2 3 0 45 6 98 -9 3 -10
Kako zelite sortirati niz (unesite 1 ili 2):
1.  U opadajucem poretku
2.  U rastucem poretku
1
Rezultirajuci niz: 98 45 12 6 3 3 2 0 -9 -10
*/

const int v = 5;

void unos(int niz[v])
{
	cout << "Unesite clanove niza: " << endl;
	for (int i = 0; i < v; i++)
	{
		cin >> niz[i];
	}
	cout << endl;
}

void sort(int niz[v])
{
	int izbor, temp;
	cout << "Unesite broj: 1 za sortiranje po rastucem, 2 za sortiranje po opadajucem redoslijedu: ";
	cin >> izbor;
	bool promjena = true;
	if (izbor == 1)
	{
		while (promjena)
		{
			promjena = false;
			for (int i = 1; i < v; i++)
			{
				if (niz[i] < niz[i - 1])
				{
					temp = niz[i];
					niz[i] = niz[i - 1];
					niz[i - 1] = temp;
					promjena = true;
				}
			}
		}
	}
	else if (izbor == 2)
	{
		while (promjena) {
			promjena = false;
			for (int i = 1; i < v; i++)
			{
				if (niz[i] > niz[i - 1])
				{
					temp = niz[i];
					niz[i] = niz[i - 1];
					niz[i - 1] = temp;
					promjena = true;
				}
			}
		}
	}
	else
		cout << "Fail: Invalid choice";
}

void ispis(int niz[v])
{
	for (int i = 0; i < v; i++)
	{
		cout << niz[i] << "  ";
	}
	cout << endl;
}

int main()
{
	int niz[v];
	unos(niz);
	ispis(niz);
	sort(niz);
	cout << "Nakon sortiranja:  ";
	ispis(niz);
	system("pause");
	return 0;
}

/*Napisati program koji će učitati prirodni broj n ≤ 10, a zatim n prirodnih trocifrenih brojeva koje treba pospremiti u odgovarajući niz.
Taj niz brojeva treba sortirati uzlazno po srednjoj cifri. Nakon sortiranja treba ispisati dobiveni niz. 
Za sortiranje koristiti zasebnu funkciju kojoj se proslijeđuje nesortiran niz.*/

void unos(int niz[], int n)
{
	cout << "Unesite clanove niza: " << endl;
	for (int i = 0; i < n; i++)
	{
		cin >> niz[i];
		if (niz[i] < 100 || niz[i] > 999)
		{
			cout << "Ponovi unos ";
			i--;
		}
	}
	cout << endl;
}

void sort(int niz[], int n)
{
	int temp, s1, s2;
	bool promjena = true;
	while (promjena)
	{
		promjena = false;
		for (int i = 1; i < n; i++)
		{
			s1 = (niz[i] / 10) % 10;
			s2 = (niz[i - 1] / 10) % 10;
			if (s1 < s2)
			{
				temp = niz[i];
				niz[i] = niz[i - 1];
				niz[i - 1] = temp;
				promjena = true;
			}
		}
	}
}

void ispis(int niz[], int n)
{
	cout << "Clanovi niza su: ";
	for (int i = 0; i < n; i++)
	{
		cout << niz[i] << "  ";
	}
	cout << endl;
}

int main()
{
	int n, niz[10];
	cout << "Unesite velicinu niza (manji od 10): ";
	do {
		cin >> n;
	} while (n > 10);

	unos(niz, n);
	sort(niz, n);
	ispis(niz, n);

	system("pause");
	return 0;
}

/*Napisati program koji će omogućiti:
•	Unos 2D niza od 10x10 elemanata vodeći računa da su svi elementi dvocifreni (ukoliko unos nekog elementa ne zadovoljava uslov, 
ponavljati unos tog elementa dok se ne zadovolji uslov) – Koristiti funkciju unos 
•	Izvršiti transpoziciju niza tako što će se zamjeniti redovi i kolone – Koristiti funkciju transpose, a zatim na osnovu izmijenjenog 2D niza:
•	Izračunati aritmetičku sredinu svih prostih brojeva ispod sporedne dijagonale – Koristiti dvije funkcije: 
aritmeticka i prost_broj (pozivati će se iz funkcije aritmeticka)
•	Napisati funkciju simpatican koja će provjeriti da li su brojevi iznad sporedne dijagonale simpatični*.
Obavezno koristiti navedene funkcije, a parametre i eventualne povratne vrijednosti definisati prema potrebi. 
U main() funkciji napisati testni program koji će omogućiti izvršenje svih funkcija navedenim redoslijedom.*/

const int v = 4;

void unos(int niz[][v])
{
	cout << "Unesite dvocifrene clanove matrice: " << endl;
	for (int i = 0; i < v; i++)
	{
		for (int j = 0; j < v; j++)
		{
			cin >> niz[i][j];
			if (niz[i][j] < 10 || niz[i][j] > 99)
			{
				j--;
				cout << "Dvocifreni clan niza: ";
			}
		}
	}
	cout << endl;
}

void transponse(int niz[][v], int niz2[][v])
{
	for (int i = 0; i < v; i++)
	{
		for (int j = 0; j < v; j++)
		{
			niz2[j][i] = niz[i][j];
		}
	}
	for (int i = 0; i < v; i++)
	{
		for (int j = 0; j < v; j++)
		{
			niz[i][j] = niz2[i][j];
		}
	}
}

bool prost(int n)
{
	for (int i = 2; i < n; i++)
	{
		if (n % i == 0)
			return false;
	}
	return true;
}

float aritmeticka(int niz[][v])
{
	int brojac = 0;
	float suma = 0;

	for (int i = 0; i < v; i++)
	{
		for (int j = 0; j < v; j++)
		{
			if (prost(niz[i][j]) == true && (i + j > v - 1))
			{
				suma += niz[i][j];
				brojac++;
			}
		}
	}
	return suma / brojac;
}

int sumacfr(int n)
{
	int suma = 0;
	while (n > 0)
	{
		suma += n % 10;
		n /= 10;
	}
	return suma;
}

bool simpatican(int niz[][v])
{
	for (int i = 0; i < v; i++)
	{
		for (int j = 0; j < v; j++)
		{
			if(i + j <= v / 2)
			{
				if (sumacfr(pow(niz[i][j], 2)) != pow(sumacfr(niz[i][j]), 2))
					return false;
			}
		}
	}
	return true;
}

void ispis(int niz[][v])
{
	for (int i = 0; i < v; i++)
	{
		for (int j = 0; j < v; j++)
		{
			cout << niz[i][j] << "  ";
		}
		cout << endl;
	}
}

int main()
{
	int niz[v][v], niz2[v][v];
	unos(niz);
	cout << "Unesena matrica izgleda ovako: " << endl;
	ispis(niz);
	transponse(niz, niz2);
	cout << "Transponovana matrica izgleda ovako: " << endl;
	ispis(niz);
	cout << "Aritmeticka sredina elemenata ispod sporedne dijagonale iznosi: " << aritmeticka(niz) << endl;
	cout << "Da li su simpaticni brojevi iznad sporedne dijagonale? (0-Ne, 1-Da) :" << simpatican(niz) << endl;


	system("pause");
	return 0;
}

// U sumu pohraniti stepen broja 2 (2,3,8,16,32,64...)

int Stepen(int n)
{
	int suma = 0;
	for (int i = 1; i <= n; i++)
	{
		if(pow(2,i) <= n)
			suma += pow(2, i);
	}
	return suma;
}

int main()
{
	int n;
	cout << "Unesite granicu N: ";
	cin >> n;

	cout << "Suma brojeva stepena 2 iznosi: " << Stepen(n) << endl;

	system("pause");
	return 0;
}



bool provjeri_uniju(int niz[], int velicina, int cifra)
{
	for (int i = 0; i < velicina; i++)
		if (niz[i] == cifra)
			return true;
	return false;
}

void dodaj_u_uniju(int niz[], int &velicina, int broj)
{
	while (broj)
	{
		int cifra = broj % 10;
		if (!provjeri_uniju(niz, velicina, cifra))
			niz[velicina++] = cifra;
		broj /= 10;
	}

}

void sortiraj(int niz[], int velicina)
{
	for (int i = 0; i < velicina - 1; i++)
		for (int j = i + 1; j < velicina; j++)
			if (niz[i] > niz[j])
			{
				int temp = niz[i];
				niz[i] = niz[j];
				niz[j] = temp;
			}
}

int main()
{
	int broj1, broj2;
	do
	{
		cin >> broj1;
	} while (broj1 <= 0);

	do
	{
		cin >> broj2;
	} while (broj2 <= 0);

	int niz[10], velicina = 0;
	dodaj_u_uniju(niz, velicina, broj1);
	dodaj_u_uniju(niz, velicina, broj2);
	sortiraj(niz, velicina);

	for (int i = 0; i < velicina; i++)
		cout << niz[i] << " ";

	system("pause>0");
}

/*Napisati program koji simulira bacanje 3 kockice (jedna kockica ima 6 strana i na tim stranama su brojevi 1-6). 
Simuliranje bacanja svake kockice ostvariti funkcijom rand()%6+1.Simulirati konstanto bacanje sve tri kockice dok se u dva uzastopna bacanja 
ne desi da se dobiju isti brojevi na sve tri kockice (npr. u šestom bacanju se dobiju brojevi 2,2,2 a u sedmom 4,4,4 na sve tri kockice). 
Ispisati koliko je ukupno bilo bacanja dok se nije ispunio navedeni uslov. Nije potrebno tražiti bilo kakav unos od korisnika.*/

int main()
{
	srand(time(NULL));
	int k1, k2, k3, br1=0, br2=0;

	do
	{
		k1 = rand() % 6 + 1;
		k2 = rand() % 6 + 1;
		k3 = rand() % 6 + 1;
		br1++;
		if ((k1 == k2) && (k2 == k3) && (k1 == k3)) {
			br2++;
			cout << "Bacanje br. " << br1 << ": " << k1 << " " << k2 << " " << k3 << endl;
		}
		else
			br2 = 0;
	} while (br2 != 2);

	cout << "Ukupan broj bacanja: " << br1 << endl;

	system("pause");
	return 0;
}

/*apisati program koji će generisati Fibonacci niz i smjestiti ga u jednodimenzionalni niz od 20 elemenata. 
(Fibonaccijev niz je niz brojeva koji počinje brojevima 0 i 1, a svaki sljedeći broj u nizu dobije se zbrajanjem prethodna dva: 
F0 = 0, F1 = 1; Fn = FN - 1 + Fn – 2). Zatim napraviti funkciju koja će u nizu pronaći sve brojeve koji završavaju parnom cifrom i ukloniti ih iz niza. 
Uklanjanje elemenata niza obavezno uraditi tako da ne ostaju prazni elementi već da se ostatak niza pomjeri kako ne bi bilo praznih elemenata. 
Pomjeranje ostatka niza obavezno raditi prilikom uklanjanja elemenata a ne sortiranjem poslije uklanjanja. */


void fibonaci(int niz[], int vel) {
	int prvi = 0, drugi = 1;
	for (int i = 0; i < vel; i++) {
		if (i == 0)
			niz[i] = prvi;
		if (i == 1)
			niz[i] = drugi;
		else {
			int temp = prvi + drugi;
			prvi = drugi;
			drugi = temp;
			niz[i] = drugi;
		}
		cout << niz[i] << " ";
	}
}

void pronadji(int niz[], int vel, int &nVel) {
	for (int i = 0; i < vel; i++) {
		if ((niz[i] % 10) % 2 != 0) {
			niz[nVel++] = niz[i];
		}
	}
}

void ispis(int niz[], int v) {
	for (int i = 0; i < v; i++) {
		cout << niz[i] << " ";
	}
	cout << endl;
}

void main() {
	const int vel = 20;
	int niz[vel];
	fibonaci(niz, vel);
	cout << endl;
	int nVel = 0;
	pronadji(niz, vel, nVel);
	ispis(niz, nVel);

	system("pause>0");
}

/*Poštujući sve faze procesa programiranja, napisati  program koji učitava prirodni broj n. 
Program treba ispisati najmanji prirodni broj m, veći ili jednak n, koji je potencija nekog prirodnog broja, 
tj. m = k^l, gdje su k i l ≥ 2 prirodni brojevi. */

int main()
{
	int n,m, maxi = INT_MAX;
	cout << "Unesite broj n: ";
	cin >> n;
	for (int i = 2; i < 10; i++)
	{
		for (int j = 2; j < 10; j++)
		{
			m = pow(j, i);
			if (m >= n && m <= maxi)
			{
				maxi = m;
				cout << m << " = " << j << " ^ " << i << endl;
				break;
			}
		}
	}

	system("pause");
	return 0;
}

/*Poštujući sve faze procesa programiranje, napisati program će odrediti i ispisati zadnje tri cifre broja x^n. 
Unos brojeva x i n vršiti u glavnoj funkciji uz uslov 10<x<100 i 2<n<10, a funkciju za određivanje zadnje tri cifre napraviti zasebno.*/

int cifre(int s)
{
	int cfr = 0;
	cfr = s % 1000;
	return cfr;
}

int main()
{
	int n, x, s=0;
	cout << "Unesi bazu: ";
	do
	{
		cin >> x;
	} while (x < 10 || x > 100);
	cout << "Unesi eksponent: ";
	do {
		cin >> n;
	} while (n < 2 || n > 10);

	s = pow(x, n);
	cout << "Rezultat je: " << s << endl;
	cout << "Zadnje tri cifre: " << cifre(s) << endl;

	system("pause");
	return 0;
}

/*Napisati program koji će omogućiti korisniku unos broja n (10<=n<=1000). Zatim simulirati n bacanja kockice 
(kockica ima 6 strana i na tim stranama su brojevi 1-6). Simuliranje bacanja svake kockice ostvariti funkcijom rand()%6+1. 
Izračunati statističke podatke u kojem procentu ukupnog bacanja se dobiva svaki od mogućih brojeva kockice 1-6. 
Obvezno koristiti switch statement za zbrajanje rezultata bacanja kockice.*/

double postotak(int n, int b)
{
	double procenat = (b / 100) * n;
	return procenat;
}

int main()
{
	srand(time(NULL));
	int n, k;
	int b1=0, b2=0, b3=0, b4=0, b5=0, b6=0;
	cout << "Unesite broj bacanja kockice: ";
	cin >> n;


	for (int i = 1; i <= n; i++)
	{
		k = rand() % 6 + 1;
		cout << k << endl;

		switch (k)
		{
		case 1:
			if (k = 1);
				b1++;
		break;
		case 2: 
			if (k = 2)
				b2++;
		break;
		case 3:
			if (k = 3)
				b3++;
		break;
		case 4:
			if (k = 4)
				b4++;
		break;
		case 5:
			if (k = 5)
				b5++;
		break;
		case 6:
			if (k = 6)
				b6++;
		break;
		}
	}

	cout << "Procenat bacanja za 1: " << postotak(n, b1) << "%"<< endl;
	cout << "Procenat bacanja za 2: " << postotak(n, b2) << "%"<< endl;
	cout << "Procenat bacanja za 3: " << postotak(n, b3) << "%" << endl;
	cout << "Procenat bacanja za 4: " << postotak(n, b4) << "%" << endl;
	cout << "Procenat bacanja za 5: " << postotak(n, b5) << "%" << endl;
	cout << "Procenat bacanja za 6: " << postotak(n, b6) << "%" << endl;


	system("pause");
	return 0;
}

/*Napisati program koji će učitati niz od 50 integer vrijednosti. 
Napisati funkciju koja će provjeriti da li se u nizu nalazi sekvenca od minimalno 4 uzastopna broja. 
Funkcija treba da provjeri i prebroji koliko takvih sekvenci postoji u nizu i da ispise broj takvih sekvenci.
Npr. 256,985,/321,322,323,324/,456,457,458,503,/201,202,203,204/,658....*/


const int v = 8;

void sekvenca(int niz[])
{
	bool sekvenca = false;
	int brojac = 0;
	for (int i = 0; i < v; i++)
	{
		if (niz[i] + 1 == niz[i + 1] && niz[i] + 2 == niz[i + 2] && niz[i] + 3 == niz[i + 3]) {
			sekvenca = true;
			brojac++;
		}
		if (sekvenca)
		{
			i += 3;
			while (niz[i+1] == niz[i]+1)
				i++;
			sekvenca == false;
		}
	}//Linija koda == Godina mog rođenja hehehe
	cout << "Broj sekvenci: " << brojac << endl;
}

int main()
{
	int niz[10] = { 354,355,356,432,433,434,435,123,147,179 };

	sekvenca(niz);
	
	system("pause");
	return 0;
}

/*Godina univerzalnog smaka svijeta*/


/*Svaki paran broj može se prikazati kao suma dvaju  prostih  brojeva  (tkzv.  Goldbachovo  pravilo). Razraditi logiku programa koji će najprije učitati 
dva prirodna broja n1 i n2. Ako je n1 > n2 zamijeniti n1 sa n2. Prikazati sve parne brojeve u intervalu n1 do n2 kao sumu dvaju prostih brojeva. 
U glavnom programu samo unijeti navedena dva prirodna broja i pozvati funkciju koja obavlja zadani posao.*/

int prost(int x)
{
	for (int i = 2; i < x; i++)
	{
		if (x%i == 0)
			return 0;
	}
	return 1;
}

void goldbach(int n1, int n2)
{
	int i, j;
	if (n1 % 2 != 0)
		n1++;
	for (n1 == 2 ? i = 1 : i = 2; i < n2; i++)
	{
		for (n1 == 2 ? j = 1 : j = 2; j < n2; j++)
		{
			if (prost(i) && prost(j))
			{
				if (i + j == n1)
				{
					cout << n1 << " = " << i << " + " << j << endl;
					n1 += 2;
				}
			}
			if (n1 > n2)
				break;
		}
	}
}

int main()
{
	int n1, n2;
	cout << "Unesite dva broja: ";
	cin >> n1 >> n2;
	if (n1 > n2)
	{
		int temp = n2;
		n1 = n2;
		n1 = temp;
	}
	goldbach(n1, n2);

	system("pause");
	return 0;
}

int faktorijel(int n)
{
	int fkt = 1;
	for (int i = 1; i <= n; i++)
	{
		fkt *= i;
	}
	return fkt;
}

int main()
{
	int n,brojac=0;
	float s = 0;
	cout << "Unesi broj: ";
	cin >> n;
	for (int i = 1; i < n; i++)
	{
		brojac++;
		if (brojac % 2 != 0)
			s += i / (n + faktorijel(i));
		else
			s -= i / (n + faktorijel(i));
	}

	cout << s << endl;

	system("pause");
	return 0;
}

/*Napisati program koji će omogućiti korisniku unos dva minimalno trocifrena prirodna broja m i n (n > m, m > 100, n < 500). 
Zatim napraviti funkciju koja će vratiti aritmetičku sredinu svih srednjih cifara svih brojeva u rangu od m do n. 
Također ta funkcija treba ispisati najveću srednju cifru navedenog ranga.*/

int srednja(int broj)
{
	broj /= 10;
	return broj % 10;
}

float funkcija(int m, int n)
{
	float suma = 0;
	int temp, brojac = 0;

	for (int i = m; i <= n; i++)
	{
		brojac++;
		suma += srednja(i);
	}

	temp = srednja(m);
	for (int i = m+1; i < n; i++)
	{
		if (temp < srednja(i))
			temp = srednja(i);
	}

	cout << "Najveca srednja cifra je: " << temp << endl;
	return suma / brojac;
}

int main()
{
	int m, n;
	cout << "Unesite n da je manji od 500 i m da je veci od 100 " << endl;

	do {
		cout << "Unesi n: ";
		cin >> n;
		cout << "Unesi m: ";
		cin >> m;
	} while ((n > 500 || n <= 0) && (m > 100 && m < n));
	cout << "Pocetna vrijednost: " << m << " , a krajnja vrijednost: " << n << endl;
	cout << "Aritmeticka sredina iznosi:" << funkcija(m, n) << endl;
	system("pause");
	return 0;
}

/*Napisati program koji æe korisniku omoguæiti unos pozitivnih neparnih cijelih brojeva za koje æe se ispitivati da
li im je prva cifra parna (npr. 4993 ili 4999). Ukoliko je zadovoljen uslov broj se smješta u niz od 10 elemenata.
Unos se ponavlja dok se ne popuni niz od 10 elemenata koji zadovoljavaju uslov unosa.
Unos se prekida ukoliko korisnik unese vrijednost 0 te se i izvršenje program završava uz poruku „Forsirani prekid“.
Zatim se za sve elementi niza ispituje da li je broj prost i da li ima samo jednu parnu cifru.
Ako  broj nije prost i ako ima više od jedne parne cifre, broj se izbacuje iz niza tako što se njegova vrijednost mijenja sa 0.
Na kraju niz sortirati od najveæeg ka najmanjem broju te ga ispisati.
Koristiti odvojene funkcije za provjeru da li je broj prost, za sortiranje i ispis niza.

*/

int vel = 10;

int Prva(int a) {
	do {
		a % 10;
		a /= 10;
	} while (a >= 9);
	return a;
}

bool Parna(int a) {
	int brojac = 0;
	do {
		a % 10;
		if (a % 2 == 0)
			brojac++;
		a /= 10;
	} while (a >= 0);
	if (brojac > 1)
		return false;
	return true;
}

bool Prost(int a) {
	for (int i = 2; i < a; i++)
	{
		if (a%i == 0)
			return false;
	}
	return true;
}

void Unos(int niz[]) {
	int brojac=0, temp = 0;
	cout << "Unesi brojeve (neparne): " << endl;
	for (size_t i = 0; i < vel; i++)
	{
		cin >> niz[i];

		if (niz[i] % 2 != 0 && Prva(niz[i]) % 2 == 0) {
			temp += niz[i];
			cout << "Prvi cifra je parna, i broj se smjesta se u niz" << endl;
		}
		else if (niz[i] == 0) {
			cout << "Forsiran Prekid " << endl;
			break;
		}
		else {
			i--;
			cout << "Broj se ne smjesta u niz" << endl;
		}
	}
}

void Provjera(int niz[], int vel) {
	for (size_t i = 0; i < vel; i++)
	{
		if (Prost(niz[i]) == false && Parna(niz[i]) == false)
			niz[i] = 0;
	}
}

void Ispis(int niz[]) {
	for (size_t i = 0; i < vel; i++)
	{
		cout << niz[i] << " ";
	}
}

void Sort(int niz[], int vel) {
	int temp;
	bool promjena = true;
	while (promjena) {
		promjena = false;
		for (size_t i = 0; i < vel; i++)
		{
			if (niz[i + 1] > niz[i]) {
				temp = niz[i];
				niz[i] = niz[i + 1];
				niz[i + 1] = temp;
				promjena = true;
			}
		}
	}
}

int main()
{
	int niz[10];
	Unos(niz);
	Provjera(niz, vel);
	Sort(niz, vel);
	Ispis(niz);
	cout << endl;

	system("pause");
	return 0;
}
