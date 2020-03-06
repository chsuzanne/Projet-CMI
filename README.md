# Projet-CMI
include <iostream> 
using namespace std; 
//zone[4*colonne + ligne] = 0; // acceder élement tableau 
bool get_element(bool* zone, int ligne, int colonne) { 
return zone[4 * colonne + ligne]; }void set_element(bool* zone, int ligne, int colonne, bool valeur) { 
zone[4 * colonne + ligne] = valeur; }// mm nb 0 1 // renvoie vrai si la condition est remplie // sinon, renvoie faux bool cond1_lin (bool* zone, int lin) { 
int nombre_0 = 0; int nombre_1 = 0; 
for (int i = 0; i < 4; i++) { 
bool element = get_element(zone, lin, i); //ligne stable colonne bouge if (element == true) 
{ 
nombre_1++; 
} else 
{ 
nombre_0++; 
} } if (nombre_0 == 2 && nombre_1 == 2) { 
return true; } else { 
return false; } }bool cond1_col (bool* zone, int col) { 
int nombre_0 = 0; int nombre_1 = 0; 
for (int i = 0; i < 4; i++) { 
bool element = get_element(zone, i, col); //colonne stable ligne bouge if (element == true) 
{ 
nombre_1++; } else { 
nombre_0++; } 
} if (nombre_0 == 2 && nombre_1 == 2) 
{ 
return true; 
} else 
{ 
return false; 
} }int main() { 
bool *zone = new bool[4*4]; 
for (int i = 0; i < 16; i++) 
{ 
zone[i] = 0; 
} set_element(zone, 0, 0, 0); set_element(zone, 0, 1, 0); 
set_element(zone, 0, 2, 1); set_element(zone, 0, 3, 0); 
// modif tt valeurs 1e ligne 
// zone , index , ligne? (1 si ligne 0 si colonne) 
cout << boolalpha << cond1_lin(zone, 0) << endl; 
delete[] zone; return 0; } 
