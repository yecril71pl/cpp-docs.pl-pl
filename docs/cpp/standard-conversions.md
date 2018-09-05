---
title: Konwersje standardowe | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- standard conversions, categories of
- L-values [C++]
- conversions, standard
ms.assetid: ce7ac8d3-5c99-4674-8229-0672de05528d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c2e8a69cf7f118af8753ebcb9e0e150c8dfc0859
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43687316"
---
# <a name="standard-conversions"></a>Konwersje standardowe
Język C++ definiuje konwersje między typami podstawowymi. Definiuje również konwersji do wskaźnik, odniesieni i typy pochodne wskaźników do elementów członkowskich. Konwersje te są nazywane *konwersje standardowe*.  
  
 W tej sekcji omówiono następujące konwersje standardowe:  
  
-   Promocje typów całkowitych  
  
-   Konwersje wartości całkowitych  
  
-   Konwersje zmiennoprzecinkowe  
  
-   Konwersje typów całkowitych i zmiennoprzecinkowych  
  
-   Konwersje arytmetyczne  
  
-   Konwersje wskaźników  
  
-   Konwersje odwołań  
  
-   Konwersje wskaźników do elementów członkowskich  
  
    > [!NOTE]
    >  Typy zdefiniowane przez użytkownika, można określić własne konwersji. Konwersja typów zdefiniowanych przez użytkownika są omówione w [konstruktory](../cpp/constructors-cpp.md) i [konwersje](../cpp/user-defined-type-conversions-cpp.md).  
  
Poniższy kod powoduje konwersje (w tym przykładzie promocje typów całkowitych):  
  
```cpp 
long  long_num1, long_num2;  
int   int_num;  
  
// int_num promoted to type long prior to assignment.  
long_num1 = int_num;  
  
// int_num promoted to type long prior to multiplication.  
long_num2 = int_num * long_num2;  
```  
  
 Wynik konwersji jest l wartością, tylko wtedy, gdy generuje typ odwołania. Na przykład konwersja zdefiniowana przez użytkownika jest zadeklarowany jako `operator int&()` zwraca odwołanie i jest l wartością. Jednak konwersja zadeklarowane jako `operator int()`zwraca obiekt, a nie jest l wartością.  
  
## <a name="integral-promotions"></a>Promocje typów całkowitych  
 Obiekty typu całkowitego można konwertować do innego, szerszego typu całkowitego (to znaczy typu, który reprezentuje większy zbiór wartości). Ta rozszerzająca typ konwersja nazywa się „promocją typu całkowitego”. Dzięki promocji typu całkowitego, można użyć w każdym wyrażeniu, w którym można użyć innego typu całkowitego:  
  
-   Obiektów, literałów i stałych typu **char** i **krótka wartość całkowita**  
  
-   Typów wyliczeniowych  
  
-   **int** pola bitowe  
  
-   Modułów wyliczających  
  
 Promocje w C++ „zachowują wartość”. Oznacza to, że wartość po promocji jest taka sama, jak wartość przed promocją. W zachowujących wartość promocjach, obiekty krótszych typów całkowitych (takie jak pola bitowe lub obiekty typu **char**) są promowane do typu **int** Jeśli **int** może reprezentować pełny zakres oryginalnego typu. Jeśli **int** nie może reprezentować pełnego zakresu wartości, a następnie obiekt jest promowany do typu **unsigned int**. Chociaż ta strategia jest taka sama, jak te stosowane w ANSI C, zachowujące wartość konwersje nie zachowują znaku obiektu.  
  
 Zachowujące wartość promocje i promocje, które zachowują znak zazwyczaj generują te same wyniki. Jednakże, mogą wygenerować różne wyniki, jeśli promowany obiekt jest jednym z poniższych:  
  
-   Argument operacji **/**, `%`, `/=`, `%=`, **<**, **\< =**, **>**, lub **>=**  
  
     Operatory te opierają się na znaku w celu określenia wyniku. W związku z tym, zachowujące wartość i znak promocje generują różne wyniki w razie zastosowania do tych operandów.  
  
-   Lewy operand **>>** lub **>>=**  
  
     Podczas wykonywania operacji przesunięcia, operatory inaczej traktują ilości oznaczone i nieznaczone. W przypadku ilości oznaczonych, przesunięcie liczby w prawo powoduje propagację bitu znaku na pozycje opuszczonych bitów. W przypadku ilości nieznaczonych, opuszczone pozycje bitowe są wypełniane zerami.  
  
-   Argument do przeciążonej funkcji lub operand przeciążonego operatora, który zależy od tego, czy typ określa znak tego operandu dla dopasowywania argumentów. (Zobacz [przeciążone operatory](../cpp/operator-overloading.md) więcej informacji na temat definiowania przeciążonych operatorów.)  
  
## <a name="integral-conversions"></a>Konwersje wartości całkowitych  
 Konwersje wartości całkowitych są wykonywane między typami całkowitymi. Typy całkowite są **char**, **int**, i **długie** (i **krótki**, **podpisany**i **niepodpisane** wersje tych typów).  
  
 **Podpisanych na typy niepodpisane**  
  
 Obiekty z podpisanych typów całkowitych można przekonwertować odpowiednie typy bez znaku. W przypadku wystąpienia takiej konwersji nie zmienia się wzorca bitowego rzeczywiste; jednak zmienia interpretację danych. Rozważmy ten kod:  
  
```cpp 
#include <iostream>  
  
using namespace std;  
int main()  
{  
    short  i = -3;  
    unsigned short u;  
  
    cout << (u = i) << "\n";  
}  
// Output: 65533  
```  
  
 W powyższym przykładzie **short ze znakiem**, `i`, został zdefiniowany i jest ustawiana na wartość ujemną. Wyrażenie `(u = i)` powoduje, że `i` są konwertowane na **typ unsigned short** przed przypisanie do `u`.  
  
 **Niepodpisane podpisane**  
  
 Obiekty niepodpisanych typów całkowitych można przekonwertować na odpowiednie typy ze znakiem. Taka Konwersja może jednak spowodować błędnej interpretacji danych, jeśli wartość obiektu bez znaku jest poza zakresem reprezentowanych przez typ ze znakiem, jak pokazano w poniższym przykładzie:  
  
```cpp
#include <iostream>  
  
using namespace std;  
int main()  
{  
 short  i;  
 unsigned short u = 65533;  
  
 cout << (i = u) << "\n";  
}  
//Output: -3  
```  
  
 W powyższym przykładzie `u` jest **typ unsigned short** całkowitego obiekt, który musi zostać skonwertowany do podpisem ilość można oszacować wyrażenia `(i = u)`. Ponieważ jej wartość nie można poprawnie przedstawić w **short ze znakiem**, danych jest niemożliwe, jak pokazano.  
  
## <a name="floating-point-conversions"></a>Punkt konwersje zmiennoprzecinkowe  
 Obiektu typu zmiennoprzecinkowego, które mogą być bezpiecznie konwertowane na bardziej precyzyjne typ zmiennoprzecinkowy — oznacza to, konwersja powoduje, że nie utrata znaczenia. Na przykład konwersja **float** do **double** lub **double** do **typu long double** są bezpieczne, a wartość pozostaje niezmieniony.  
  
 Obiekt typu zmiennoprzecinkowego można też przekonwertować na typ mniej dokładne, jeśli znajduje się w zakresie reprezentowanych przez tego typu. (Zobacz [limity liczb zmiennoprzecinkowych](../cpp/floating-limits.md) dla zakresów typu zmiennoprzecinkowego.) Jeśli oryginalna wartość nie może być przedstawiony w dokładnie, aby można było przekonwertować do jednej następnego wyższe lub niższe następną wartość. Jeśli nie ma takiej wartości, wynik jest niezdefiniowany. Rozważmy następujący przykład:  
  
```cpp
cout << (float)1E300 << endl;  
```  
  
 Wartość maksymalna reprezentowana przez typ **float** jest 3.402823466E38 — znacznie mniejszej liczby, niż 1E300. W związku z tym liczba jest konwertowana do nieskończoności, a wynik jest "inf".  
  
## <a name="conversions-between-integral-and-floating-point-types"></a>Konwersje między typami punktu całkowite i zmiennoprzecinkowe  
 Niektórych wyrażeń może spowodować obiekty typu zmiennoprzecinkowego typu przeznaczonego do konwersji do typów całkowitych lub na odwrót. Gdy obiekt typu Liczba całkowita jest konwertowany na typ zmiennoprzecinkowy i nie można dokładnie przedstawić oryginalnej wartości, wynik jest albo następnym wyższe lub niższe następną wartość.  
  
 Gdy obiekt typu zmiennoprzecinkowego jest konwertowany na typ całkowity, część ułamkowa zostanie obcięta. Zaokrąglenie nie odbywa się w procesie konwersji. Obcięcie oznacza, że numer, takie jak 1.3 jest konwertowana na 1 i-1.3 jest konwertowana na wartość -1.  
  
## <a name="arithmetic-conversions"></a>Konwersje arytmetyczne  
 Wiele operatorów binarnych (omówionych w [wyrażenia z operatorami Dwuargumentowymi](../cpp/expressions-with-binary-operators.md)) powoduje konwersje operandów i daje wyniki taki sam sposób. Sposób, w jaki te operatory powodują konwersje jest nazywany „typowe konwersje arytmetyczne”. Konwersje arytmetyczne operandów o różnych typach natywnych są wykonywane jak pokazano w poniższej tabeli. Typy typedef zachowują się zgodnie z ich podstawowymi typami natywnymi.  
  
### <a name="conditions-for-type-conversion"></a>Warunki dotyczące konwersji typów  
  
|Spełnione warunki|Konwersja|  
|--------------------|----------------|  
|Jeden z operandów jest typu **typu long double**.|Drugi operand jest konwertowany na typ **typu long double**.|  
|Poprzedza warunek nie jest spełniony i jeden z operandów jest typu **double**.|Drugi operand jest konwertowany na typ **double**.|  
|Poprzedza warunki nie są spełnione i jeden z operandów jest typu **float**.|Drugi operand jest konwertowany na typ **float**.|  
|Powyższe warunki nie są spełnione (żaden z operandów nie jest typu zmiennoprzecinkowego).|Promocje typów całkowitych są wykonywane na operandach w następujący sposób:<br /><br /> — Jeśli jeden z operandów jest typu **unsigned long**, to drugi operand jest konwertowany na typ **unsigned long**.<br />-Jeśli powyższy warunek nie zostały spełnione i jeden z operandów jest typu **długie** i drugą typu **unsigned int**, oba operandy są konwertowane na typ **unsigned long**.<br />-Jeśli dwa powyższe warunki nie są spełnione i jeden z operandów jest typu **długie**, to drugi operand jest konwertowany na typ **długie**.<br />-Jeśli trzy powyższe warunki nie są spełnione i jeden z operandów jest typu **unsigned int**, to drugi operand jest konwertowany na typ **unsigned int**.<br />— Jeśli żaden z powyższych warunków nie jest spełniony, oba operandy są konwertowane na typ **int**.|  
  
 Następujący kod ilustruje reguły konwersji opisane w tabeli:  
  
```cpp 
double dVal;  
float fVal;  
int iVal;  
unsigned long ulVal;  
  
int main() {  
   // iVal converted to unsigned long  
   // result of multiplication converted to double  
   dVal = iVal * ulVal;  
  
   // ulVal converted to float  
   // result of addition converted to double  
   dVal = ulVal + fVal;  
}  
```  
  
 Pierwsza instrukcja w powyższym przykładzie pokazuje mnożenie dwóch typów całkowitych: `iVal` i `ulVal`. Spełniony jest warunek, że żaden z operandów jest typu zmiennoprzecinkowego i jeden z operandów jest typu **unsigned int**. W związku z tym, drugi operand `iVal`, jest konwertowany na typ **unsigned int**. Wynik jest przypisany do `dVal`. Spełniony jest warunek, że jeden z operandów jest typu **double**; w związku z tym, **unsigned int** wynik mnożenia jest konwertowany na typ **double**.  
  
 Druga instrukcja w powyższym przykładzie pokazuje Dodawanie typu **float** i typem całkowitym `fVal` i `ulVal`. `ulVal` Zmienna jest konwertowany na typ **float** (trzeci warunek określony w tabeli). Wynik dodawania jest konwertowany na typ **double** (drugi warunek określony w tabeli) i przypisane do `dVal`.  
  
## <a name="pointer-conversions"></a>Konwersje wskaźników  
 Wskaźniki mogą być konwertowane podczas przypisywania, inicjowanie, porównania i inne wyrażenia.  
  
### <a name="pointer-to-classes"></a>Wskaźnik do klasy  
 Istnieją dwa przypadki, w których można przekonwertować na wskaźnik do klasy bazowej na wskaźnik do klasy.  
  
 Pierwszy przypadek jest, gdy określona klasa bazowa jest dostępny i jednoznaczna konwersja. (Zobacz [wielu klas bazowych](../cpp/multiple-base-classes.md) Aby uzyskać więcej informacji na temat niejednoznacznego odwołania do klasy bazowej.)  
  
 Czy klasa bazowa jest niedostępna, zależy od rodzaju dziedziczenia używany podczas wyprowadzania. Należy wziąć pod uwagę dziedziczenia zilustrowane na poniższym rysunku.  
  
 ![Wykres dziedziczenia, przedstawiający podstawowy&#45;klasy ułatwień dostępu](../cpp/media/vc38xa1.gif "vc38XA1")  
Wykres dziedziczenia opisano klasy podstawowej w ułatwienia dostępu  
  
 W poniższej tabeli przedstawiono dostępność klasy podstawowej w sytuacji, przedstawione na rysunku.  
  
### <a name="base-class-accessibility"></a>Klasa bazowa ułatwień dostępu  
  
|Typ funkcji|Tworzenie wartości pochodnych|Konwersja z<br /><br /> B * a\* prawne?|  
|----------------------|----------------|-------------------------------------------|  
|Funkcji zewnętrznych (nie klasy zakresu)|Private|Nie|  
||Protected|Nie|  
||Public|Tak|  
|Funkcja elementu członkowskiego B (w zakresie B)|Private|Tak|  
||Protected|Tak|  
||Public|Tak|  
|Funkcja elementu członkowskiego języka C (w zakresie języka C)|Private|Nie|  
||Protected|Tak|  
||Public|Tak|  
  
 Drugi przypadek, w którym wskaźnik do klasy można przekonwertować na wskaźnik do klasy bazowej jest w przypadku używania jawną konwersję typu. (Zobacz [jawnego operatora konwersji typu](explicit-type-conversion-operator-parens.md) Aby uzyskać więcej informacji dotyczących konwersji typu jawnego.)  
  
 Wynik konwersji elementu jest wskaźnikiem do "podobiektu," część obiektu, który jest całkowicie opisane przez klasę bazową.  
  
 Poniższy kod definiuje dwie klasy `A` i `B`, gdzie `B` jest tworzony na podstawie `A`. (Aby uzyskać więcej informacji na temat dziedziczenia, zobacz [klasy pochodne](../cpp/inheritance-cpp.md).) Następnie definiuje `bObject`, obiekt typu `B`i dwa wskaźniki (`pA` i `pB`) wskazujące na obiekt.  
  
```cpp 
// C2039 expected  
class A  
{  
public:  
    int AComponent;  
    int AMemberFunc();  
};  
  
class B : public A  
{  
public:  
    int BComponent;  
    int BMemberFunc();  
};  
int main()  
{  
   B bObject;  
   A *pA = &bObject;  
   B *pB = &bObject;  
  
   pA->AMemberFunc();   // OK in class A  
   pB->AMemberFunc();   // OK: inherited from class A  
   pA->BMemberFunc();   // Error: not in class A  
}  
```  
  
 Wskaźnik `pA` typu `A *`, który może być interpretowany jako znaczenie "wskaźnik do obiektu typu `A`." Elementy członkowskie `bObject` `(`takich jak `BComponent` i `BMemberFunc`) są unikatowe dla typu `B` i dlatego są niedostępne za pośrednictwem `pA`. `pA` Wskaźnik zezwala na dostęp tylko do tych właściwości (funkcje składowe i dane) obiektu, które są zdefiniowane w klasie `A`.  
  
### <a name="pointer-to-function"></a>Wskaźnik do funkcji  
 Wskaźnik do funkcji może być konwertowany na typ `void *`, jeśli typ `void *` jest wystarczająco duży, aby pomieścić ten wskaźnik.  
  
### <a name="pointer-to-void"></a>Wskaźnik do typu void  
 Wskaźniki do typu **void** mogą być konwertowane do wskaźników do jakichkolwiek innych typów, ale tylko w przypadku typu jawnego rzutowania (w przeciwieństwie do w języku C). Wskaźnik do dowolnego typu można niejawnie przekonwertować na wskaźnik do typu **void**. Wskaźnik do obiektu niekompletnego typu można przekonwertować na wskaźnik do **void** (niejawnie) i wykonać ich kopię (jawne). Wynik konwersji elementu jest równa wartości oryginalny wskaźnik. Obiekt jest traktowany jako niekompletne, jeśli jest on zadeklarowany, ale ma za mało informacji do określenia jego rozmiar lub klasa bazowa.  
  
 Wskaźnik do dowolnego obiektu, który nie jest **const** lub **volatile** można niejawnie przekonwertować na wskaźnik typu `void *`.  
  
### <a name="const-and-volatile-pointers"></a>wskaźniki stałe i nietrwałe  
 C++ nie dostarcza konwersja standardowa ze **const** lub **volatile** typu do typu, który nie jest **const** lub **volatile**. Jednak dowolny rodzaj konwersji można określić za pomocą typu jawnego rzutowania (w tym konwersje niebezpieczne).  
  
> [!NOTE]
>  C++ wskaźników do elementów członkowskich, z wyjątkiem wskaźniki do statycznych elementów członkowskich, różnią się od normalnych wskaźników i nie mają tego samego konwersje standardowe. Wskaźniki do statycznych elementów członkowskich są wskaźnikami normalne i mieć tej samej konwersji jako normalny wskaźniki.   
  
### <a name="null-pointer-conversions"></a>Konwersje wskaźników o wartości null  
 Wyrażenie stałe całkowite osiągnie wartość zero lub Rzutowanie na typ wskaźnika wyrażenia jest konwertowana na wskaźnik o nazwie "wskaźnik o wartości null." This, wskaźnik jest gwarantowane, aby porównać nierówne na wskaźnik do dowolnego prawidłowego obiektu lub funkcji (z wyjątkiem wskaźników do obiektów na podstawie, które mogą mieć tego samego przesunięcie, a nadal wskazują różne obiekty).  
  
 W języku C ++ 11 [nullptr](../cpp/nullptr.md) typ powinien być preferowana względem wskaźnika o wartości null w stylu języka C.  
  
### <a name="pointer-expression-conversions"></a>Konwersje wyrażenia wskaźników  
 Dowolne wyrażenie z typem tablicy można przekonwertować na wskaźnik do tego samego typu. Wynik konwersji jest wskaźnik do pierwszego elementu tablicy. W poniższym przykładzie pokazano konwersji elementu:  
  
```cpp 
char szPath[_MAX_PATH]; // Array of type char.  
char *pszPath = szPath; // Equals &szPath[0].  
```  
  
 Wyrażenie, które powoduje funkcja zwracająca określonego typu, jest konwertowany na wskaźnik do funkcji zwracającej tego typu, chyba że:  
  
-   Wyrażenie jest używana jako argument operatora address-of (**&**).  
  
-   Wyrażenie jest używana jako argument operatora wywołania funkcji.  
  
## <a name="reference-conversions"></a>Konwersje odwołań  
 Odwołanie do klasy mogą być konwertowane na odwołania do klasy bazowej w następujących przypadkach:  
  
-   Określona klasa bazowa jest dostępna.  
  
-   Konwersja jest jednoznaczna. (Zobacz [wielu klas bazowych](../cpp/multiple-base-classes.md) Aby uzyskać więcej informacji na temat niejednoznacznego odwołania do klasy bazowej.)  
  
 Wynik konwersji jest wskaźnikiem do podobiektów, który reprezentuje klasę bazową.  
  
## <a name="pointer-to-member"></a>Wskaźnik do składowej  
 Wskaźniki do składowych klasy mogą być konwertowane podczas przypisywania, inicjowanie, porównania i inne wyrażenia. W tej sekcji opisano następujące konwersje wskaźników do elementów członkowskich:  
  
## <a name="pointer-to-base-class-member"></a>Wskaźnik do składowej klasy bazowej  
 Wskaźnik do składowej klasy bazowej można przekonwertować na wskaźnik do składowej klasy pochodzącej od niego, gdy są spełnione następujące warunki:  
  
-   Odwrotność konwersji ze wskaźnika do klasy pochodnej na wskaźnik klasy bazowej, jest dostępny.  
  
-   Klasa pochodna nie dziedziczy praktycznie z klasy bazowej.  
  
 Kiedy Lewy argument operacji jest wskaźnik do składowej, prawy operand musi być typu wskaźnika do elementu członkowskiego lub być wyrażeniem stałym, którego wynikiem jest 0. To przypisanie jest prawidłowy tylko w następujących przypadkach:  
  
-   Prawy operand jest wskaźnik do składowej tej samej klasy jako lewy operand.  
  
-   Lewy operand jest wskaźnik do składowej klasy pochodnej publicznie i jednoznacznie z klasy prawy operand.  
  
## <a name="integral-constant-conversions"></a>Konwersje wartości całkowitych stałej  
 Wyrażenie stałe całkowite osiągnie wartość zero jest konwertowana na wskaźnik o nazwie "wskaźnik o wartości null." This, wskaźnik jest gwarantowane, aby porównać nierówne na wskaźnik do dowolnego prawidłowego obiektu lub funkcji (z wyjątkiem wskaźników do obiektów na podstawie, które mogą mieć tego samego przesunięcie, a nadal wskazują różne obiekty).  
  
 Poniższy kod ilustruje definicji wskaźnik do składowej `i` w klasie `A`. Wskaźnik, `pai`, jest ustawiana na 0, co jest wskaźnikiem wartości null.  
  
```cpp 
class A  
{  
public:  
 int i;  
};  
  
int A::*pai = 0;  
  
int main()  
{  
}  
```  
  
## <a name="see-also"></a>Zobacz także  
 [Dokumentacja języka C++](../cpp/cpp-language-reference.md)