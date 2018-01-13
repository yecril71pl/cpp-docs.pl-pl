---
title: Konwersje standardowe | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- standard conversions, categories of
- L-values [C++]
- conversions, standard
ms.assetid: ce7ac8d3-5c99-4674-8229-0672de05528d
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 324fa54362098e2b7ffae6fdf368bf590846f9c1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="standard-conversions"></a>Konwersje standardowe
Język C++ definiuje konwersji między typami podstawowymi. Definiuje również konwersji dla wskaźnika, odwołanie, i typów pochodnych wskaźnika do elementu członkowskiego. Konwersje te są nazywane "konwersje standardowe." (Aby uzyskać więcej informacji na temat typów, standardowych typów i typów pochodnych, zobacz [typy](http://msdn.microsoft.com/en-us/6882ee83-ea32-4373-8d57-c3efbbc15af0).)  
  
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
    >  Typy definiowane przez użytkownika można określić własne konwersji. Konwersja typów zdefiniowanych przez użytkownika została opisana w [konstruktorów](../cpp/constructors-cpp.md) i [konwersje](../cpp/user-defined-type-conversions-cpp.md).  
  
 Poniższy kod powoduje konwersje (w tym przykładzie promocje typów całkowitych):  
  
```  
long  long_num1, long_num2;  
int   int_num;  
  
// int_num promoted to type long prior to assignment.  
long_num1 = int_num;  
  
// int_num promoted to type long prior to multiplication.  
long_num2 = int_num * long_num2;  
```  
  
 Wynik konwersji jest wartością l-value tylko wtedy, gdy generuje Typ referencyjny. Na przykład konwersji zdefiniowanej przez użytkownika jest zadeklarowany jako `operator int&()` zwraca odwołanie i jest wartością l-value. Jednak konwersji zadeklarowany jako `operator int()`zwraca obiekt i nie jest wartością l-value.  
  
## <a name="integral-promotions"></a>Promocje typów całkowitych  
 Obiekty typu całkowitego można konwertować do innego, szerszego typu całkowitego (to znaczy typu, który reprezentuje większy zbiór wartości). Ta rozszerzająca typ konwersja nazywa się „promocją typu całkowitego”. Dzięki promocji typu całkowitego, można użyć w każdym wyrażeniu, w którym można użyć innego typu całkowitego:  
  
-   Obiektów, literałów i stałych typu `char` i `short int`  
  
-   Typów wyliczeniowych  
  
-   `int` pól bitowych  
  
-   Modułów wyliczających  
  
 Promocje w C++ „zachowują wartość”. Oznacza to, że wartość po promocji jest taka sama, jak wartość przed promocją. W zachowujących wartość promocjach, obiekty krótszych typów całkowitych (takie jak pola bitowe lub obiekty typu `char`) są promowane do typu `int`, jeśli `int` może reprezentować pełny zakres oryginalnego typu. Jeśli `int` nie może reprezentować pełnego zakresu wartości, obiekt jest promowany do typu `unsigned int`. Chociaż ta strategia jest taka sama, jak te stosowane w ANSI C, zachowujące wartość konwersje nie zachowują znaku obiektu.  
  
 Zachowujące wartość promocje i promocje, które zachowują znak zazwyczaj generują te same wyniki. Jednakże, mogą wygenerować różne wyniki, jeśli promowany obiekt jest jednym z poniższych:  
  
-   Argument operacji  **/** , `%`, `/=`, `%=`,  **<** ,  **\< =** ,  **>** , lub**>=**  
  
     Operatory te opierają się na znaku w celu określenia wyniku. W związku z tym, zachowujące wartość i znak promocje generują różne wyniki w razie zastosowania do tych operandów.  
  
-   Lewy argument operacji  **>>**  lub**>>=**  
  
     Podczas wykonywania operacji przesunięcia, operatory inaczej traktują ilości oznaczone i nieznaczone. W przypadku ilości oznaczonych, przesunięcie liczby w prawo powoduje propagację bitu znaku na pozycje opuszczonych bitów. W przypadku ilości nieznaczonych, opuszczone pozycje bitowe są wypełniane zerami.  
  
-   Argument do przeciążonej funkcji lub operand przeciążonego operatora, który zależy od tego, czy typ określa znak tego operandu dla dopasowywania argumentów. (Zobacz [przeciążone operatory](../cpp/operator-overloading.md) szczegółowe informacje na temat definiowania przeciążone operatory.)  
  
## <a name="integral-conversions"></a>Konwersje wartości całkowitych  
 Konwersje wartości całkowitych odbywa się między typów całkowitych. Typy całkowite są `char`, `int`, i **długi** (i **krótki**, **podpisany**, i `unsigned` wersje tych typów).  
  
 **Podpisanych na typy niepodpisane**  
  
 Obiekty podpisanych typów całkowitych można przekonwertować na odpowiednie typy bez znaku. Konwersje te wystąpią, nie powoduje zmiany wzorca bitowego rzeczywisty; jednak zmiany interpretację danych. Należy wziąć pod uwagę ten kod:  
  
```  
  
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
  
 W powyższym przykładzie `signed short`, `i`, został zdefiniowany i jest ustawiana na wartość ujemną. Wyrażenie `(u = i)` powoduje, że `i` ma zostać przekonwertowane na **niepodpisane krótko** przed przypisaniem do `u`.  
  
 **Niepodpisane podpisane**  
  
 Obiekty niepodpisanych typów całkowitych można przekonwertować na odpowiednie typy ze znakiem. Takie Konwersja może jednak spowodować błędnej interpretacji danych, jeśli wartość bez znaku obiektu jest poza zakresem można przedstawić według typu ze znakiem, jak pokazano w poniższym przykładzie:  
  
```  
  
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
  
 W powyższym przykładzie `u` jest `unsigned` **krótki** integralną obiekt, który należy przekonwertować podpisem ilość można oszacować wyrażenia `(i = u)`. Ponieważ jej wartość nie może być poprawnie reprezentowany w `signed short`, jest błędnie zinterpretowane danych, jak pokazano.  
  
## <a name="floating-point-conversions"></a>Punkt konwersje zmiennoprzecinkowe  
 Przestawne typu obiektu można bezpiecznie przekonwertować typu przestawne dokładniejsze — to znaczy konwersji spowoduje, że nie istotności. Na przykład konwersje z **float** do **podwójne** lub **podwójne** do `long double` są bezpieczne i wartość jest bez zmian.  
  
 Przestawne typu obiektu również można przekonwertować typowi mniej dokładne, jeśli są w jej zasięgu można przedstawić według tego typu. (Zobacz [limity liczb zmiennoprzecinkowych](../cpp/floating-limits.md) dla zakresów z typów zmiennoprzecinkowych.) Jeśli oryginalna wartość nie może być reprezentowany dokładnie, aby można było przekonwertować jednej następnej wyższej lub dalej można przedstawić niższą wartość. Jeśli takie wartość nie istnieje, wynikiem jest niezdefiniowany. Rozważmy następujący przykład:  
  
```  
cout << (float)1E300 << endl;  
```  
  
 Wartość maksymalna można przedstawić według typu **float** jest 3.402823466E38 — znacznie mniejszą wartość niż 1E300. W związku z tym liczba jest konwertowana do nieskończoności, a wynik jest 1. #INF.  
  
## <a name="conversions-between-integral-and-floating-point-types"></a>Konwersje między typami punktu całkowitych i zmiennoprzecinkowych  
 Niektóre wyrażenia może spowodować obiekty przestawne typu do konwersji na typy całkowite ani odwrotnie. Gdy obiekt typu całkowitego jest konwertowana na typ zmiennoprzecinkowych i oryginalna wartość nie może być reprezentowany dokładnie, wynikiem jest albo następnej wyższej lub dalej można przedstawić niższą wartość.  
  
 Gdy zmiennoprzecinkową typ obiektu jest konwertowany na typ całkowity, część ułamkowa zostanie obcięta. Zaokrąglanie nie odbywa się w procesie konwersji. Obcięcie oznacza, że liczba takich jak 1.3 jest konwertowana na 1 i-1.3 jest konwertowana na -1.  
  
## <a name="arithmetic-conversions"></a>Konwersje arytmetyczne  
 Wiele operatorów binarnych (omówiona w [wyrażenia z operatorami Dwuargumentowymi](../cpp/expressions-with-binary-operators.md)) powodują konwersje argumentów i dają wyniki w taki sam sposób. Sposób, w jaki te operatory powodują konwersje jest nazywany „typowe konwersje arytmetyczne”. Konwersje arytmetyczne operandów o różnych typach natywnych są wykonywane jak pokazano w poniższej tabeli. Typy typedef zachowują się zgodnie z ich podstawowymi typami natywnymi.  
  
### <a name="conditions-for-type-conversion"></a>Warunki dotyczące konwersji typów  
  
|Spełnione warunki|Konwersja|  
|--------------------|----------------|  
|Albo operand jest typu **podwójnej długości**.|Drugiego operandu jest konwertowana na typ **podwójnej długości**.|  
|Przed warunek nie jest spełniony którykolwiek argument operacji jest typu **podwójne**.|Drugiego operandu jest konwertowana na typ **podwójne**.|  
|Poprzedzających warunki nie zostały spełnione i którykolwiek argument operacji jest typu **float**.|Drugiego operandu jest konwertowana na typ **float**.|  
|Powyższe warunki nie są spełnione (żaden z operandów nie jest typu zmiennoprzecinkowego).|Promocje typów całkowitych są wykonywane na operandach w następujący sposób:<br /><br /> — Jeśli którykolwiek argument operacji jest typu `unsigned` **długi**, drugiego operandu jest konwertowana na typ `unsigned long`.<br />— Jeśli poprzedzających warunku nie zostały spełnione, a jeśli którykolwiek argument operacji jest typu **długi** i drugą typu `unsigned` `int`, obydwa argumenty operacji są konwertowane na typ `unsigned long`.<br />— Jeśli poprzednie dwa warunki nie są spełnione, a jeśli którykolwiek argument operacji jest typu **długi**, drugiego operandu jest konwertowana na typ **długi**.<br />— Jeśli poprzednie trzy warunki nie są spełnione, a jeśli którykolwiek argument operacji jest typu `unsigned int`, drugiego operandu jest konwertowana na typ `unsigned int`.<br />— Jeśli żaden z powyższych warunków nie jest spełniony, obydwa argumenty operacji są konwertowane na typ `int`.|  
  
 Następujący kod ilustruje reguły konwersji opisane w tabeli:  
  
```  
  
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
  
 Pierwsza instrukcja w powyższym przykładzie pokazuje mnożenie dwóch typów całkowitych: `iVal` i `ulVal`. Spełniony jest warunek, że żaden z operandów nie jest typu zmiennoprzecinkowego i jeden z operandów jest typu `unsigned int`. Z tego powodu, drugi operand `iVal` jest konwertowany na typ `unsigned int`. Wynik jest przypisany do `dVal`. Warunek jest spełniony jest, że jeden operand jest typu **podwójne**; w związku z tym `unsigned int` wyniku iloczyn jest konwertowana na typ **podwójne**.  
  
 Drugi instrukcji w tym przykładzie przedstawiono dodawanie **float** i typem całkowitym `fVal` i `ulVal`. `ulVal` Zmiennej jest konwertowana na typ **float** (trzeci warunku w tabeli). Wynik operacji dodawania jest konwertowana na typ **podwójne** (drugi warunek w tabeli) i przypisane do `dVal`.  
  
## <a name="pointer-conversions"></a>Konwersje wskaźników  
 Wskaźniki można przekonwertować ciągu przypisania, inicjowanie porównania i inne wyrażenia.  
  
### <a name="pointer-to-classes"></a>Wskaźnik do klasy  
 Istnieją dwa przypadki, w których można przekonwertować wskaźnika do klasy na wskaźnik do klasy podstawowej.  
  
 Pierwszy zdarza się, gdy określona klasa podstawowa jest dostępna, a konwersja jest jednoznaczny. (Zobacz [wiele klas podstawowych](../cpp/multiple-base-classes.md) uzyskać więcej informacji o niejednoznaczne odwołania do klasy podstawowej.)  
  
 Określa, czy klasa podstawowa jest niedostępna, zależy od rodzaju dziedziczenia używany podczas wyprowadzania. Należy wziąć pod uwagę dziedziczenia pokazano na poniższej ilustracji.  
  
 ![Dziedziczenie wykres przedstawiający base &#45; klasa dostępność](../cpp/media/vc38xa1.gif "vc38XA1")  
Wykres dziedziczenia do celów informacyjnych dostępności klasy podstawowej  
  
 W poniższej tabeli przedstawiono dostępność klasy podstawowej dla sytuacji przedstawione na rysunku.  
  
### <a name="base-class-accessibility"></a>Klasa podstawowa ułatwień dostępu  
  
|Typ funkcji|Tworzenie wartości pochodnych|Konwersja z<br /><br /> B * a\* prawne?|  
|----------------------|----------------|-------------------------------------------|  
|Funkcja zewnętrzna (nie klasy zakresu)|Private|Nie|  
||Protected|Nie|  
||Public|Tak|  
|Funkcja członkowska B (w zakresie B)|Private|Tak|  
||Protected|Tak|  
||Public|Tak|  
|Funkcja członkowska C (w zakresie C)|Private|Nie|  
||Protected|Tak|  
||Public|Tak|  
  
 Jeśli jest używany konwersja typu jawnego jest drugim przypadku, w którym można przekonwertować wskaźnika do klasy na wskaźnik do klasy podstawowej. (Zobacz [wyrażenia z jawne konwersje typów](http://msdn.microsoft.com/en-us/060ad6b4-9592-4f3e-8509-a20ac84a85ae) Aby uzyskać więcej informacji na temat jawne konwersje typów.)  
  
 Wynikiem tych konwersji jest wskaźnikiem do "podobiektów," część obiektu, który jest całkowicie opisanego przez klasę podstawową.  
  
 Poniższy kod definiuje dwie klasy `A` i `B`, gdzie `B` jest pochodną `A`. (Aby uzyskać więcej informacji o dziedziczeniu, zobacz [klas pochodnych](../cpp/inheritance-cpp.md).) Następnie definiuje `bObject`, typu obiektu `B`i dwóch wskaźników (`pA` i `pB`) na tym etapie do obiektu.  
  
```  
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
  
 Wskaźnik `pA` jest typu `A *`, które mogą być interpretowane jako znaczenie "wskaźnik do obiektu typu `A`." Elementy członkowskie `bObject` `(`takich jak `BComponent` i `BMemberFunc`) są unikatowe dla typu `B` i są niedostępne za pośrednictwem `pA`. `pA` Wskaźnika zezwala na dostęp tylko do tych właściwości (funkcji Członkowskich i dane) obiektu zdefiniowanych w klasie `A`.  
  
### <a name="pointer-to-function"></a>Wskaźnik do funkcji  
 Można przekonwertować na typ wskaźnika do funkcji **void \*** , jeśli typ **void \***  jest wystarczająco duży, aby pomieścić ten wskaźnik.  
  
### <a name="pointer-to-void"></a>Wskaźnik do typu void  
 Wskaźniki do typu `void` mogą być konwertowane do wskaźników do żadnego innego typu, ale tylko w przypadku typu jawnego rzutowania (w przeciwieństwie do w języku C). (Zobacz [wyrażenia z jawne konwersje typów](http://msdn.microsoft.com/en-us/060ad6b4-9592-4f3e-8509-a20ac84a85ae) Aby uzyskać więcej informacji na temat typu rzutowania.) Wskaźnik do dowolnego typu można niejawnie przekonwertować na wskaźnik do typu `void`. Wskaźnik do obiektu niekompletne typu mogą być konwertowane na wskaźnik do `void` (domyślnie) i wykonać ich kopię (jawnie). Wynik konwersji takie jest równa wartości oryginalnej wskaźnika. Obiekt jest traktowany jako niekompletne, jeśli jest on zadeklarowany, ale ma za mało informacji dostępne, aby określić jego rozmiar lub klasa bazowa.  
  
 Wskaźnik do dowolnego obiektu, który nie jest **const** lub `volatile` można niejawnie przekonwertować typu wskaźnik **void \*** .  
  
### <a name="const-and-volatile-pointers"></a>wskaźniki stałe i nietrwałe  
 C++ nie dostarcza konwersja standardowa ze **const** lub `volatile` typu na typ, który nie jest **const** lub `volatile`. Jednak dowolny rodzaj konwersji można określić przy użyciu typu jawnego rzutowania (w tym konwersje, które są niebezpieczne).  
  
> [!NOTE]
>  C++ wskaźników do elementów członkowskich, z wyjątkiem wskaźniki do statycznych elementów członkowskich, różnią się od normalnego wskaźników i nie mają tej samej konwersje standardowe. Wskaźniki do statyczne elementy członkowskie są wskaźnikami normalne i mieć tego samego konwersje jako normalne wskaźników.   
  
### <a name="null-pointer-conversions"></a>Konwersje wskaźników null  
 Całkowite stałe wyrażenie obliczane do zera lub przy użyciu wyrażenia Rzutowanie na typ wskaźnika jest konwertowana na wskaźnik o nazwie "wskaźnik null". Ten wskaźnik jest gwarantowane porównania nierówne na wskaźnik do prawidłowego obiektu ani funkcji (z wyjątkiem wskaźników do obiektów na podstawie, które mogą mieć tej samej przesunięcie i wciąż pkt do różnych obiektów).  
  
 W języku C ++ 11 [nullptr](../cpp/nullptr.md) typ powinien być preferowana względem wskaźnika null w stylu języka C.  
  
### <a name="pointer-expression-conversions"></a>Konwersje wskaźników wyrażenia  
 Dowolne wyrażenie z typem tablicy mogą być konwertowane do tego samego typu wskaźnika. Wynik konwersji jest wskaźnik do pierwszego elementu tablicy. W poniższym przykładzie pokazano takich konwersji:  
  
```  
char szPath[_MAX_PATH]; // Array of type char.  
char *pszPath = szPath; // Equals &szPath[0].  
```  
  
 Wyrażenie, które powoduje funkcji zwracającej określonego typu jest konwertowana na wskaźnik do funkcji zwracającej tego typu, chyba że:  
  
-   Wyrażenie, które jest używane jako argumentu address-of — operator (**&**).  
  
-   Wyrażenie jest używany jako argumentu operator wywołania funkcji.  
  
## <a name="reference-conversions"></a>Konwersje odwołań  
 Odwołanie do klasy mogą być konwertowane na odwołania do klasy podstawowej w następujących przypadkach:  
  
-   Określona klasa podstawowa jest dostępna.  
  
-   Konwersja jest jednoznaczny. (Zobacz [wiele klas podstawowych](../cpp/multiple-base-classes.md) uzyskać więcej informacji o niejednoznaczne odwołania do klasy podstawowej.)  
  
 Wynik konwersji jest wskaźnik do podobiektów, który reprezentuje klasę podstawową.  
  
## <a name="pointer-to-member"></a>Wskaźnik do elementu członkowskiego  
 Wskaźniki do elementów członkowskich klasy można przekonwertować ciągu przypisania, inicjowanie porównania i inne wyrażenia. W tej sekcji opisano następujące konwersje wskaźników do elementów członkowskich:  
  
## <a name="pointer-to-base-class-member"></a>Wskaźnik do elementu członkowskiego klasy podstawowej  
 Można przekonwertować wskaźnika do elementu członkowskiego klasy podstawowej na wskaźnik do elementu członkowskiego klasy pochodnej z niego, gdy są spełnione następujące warunki:  
  
-   Konwersji odwrotnej, ze wskaźnika do pochodnego na wskaźnik do klasy podstawowej klasy, jest dostępny.  
  
-   Klasa pochodna nie dziedziczy praktycznie z klasy podstawowej.  
  
 Lewy operand jest wskaźnik do elementu członkowskiego, prawy operand musi być typu wskaźnika do elementu członkowskiego lub być wyrażeniem stałym, którego wynikiem jest 0. To przypisanie jest prawidłowy tylko w następujących przypadkach:  
  
-   Prawy operand jest wskaźnik do elementu członkowskiego o tej samej klasy jako lewy operand.  
  
-   Lewy argument operacji jest wskaźnik do elementu członkowskiego klasy pochodnej publicznie i jednoznacznie z klasy prawy argument operacji.  
  
## <a name="integral-constant-conversions"></a>Konwersje wartości całkowitych stałej  
 Wyrażeniu dającym stałą całkowitą którego wartością zero jest konwertowana na wskaźnik o nazwie "wskaźnik null". Ten wskaźnik jest gwarantowane porównania nierówne na wskaźnik do prawidłowego obiektu ani funkcji (z wyjątkiem wskaźników do obiektów na podstawie, które mogą mieć tej samej przesunięcie i wciąż pkt do różnych obiektów).  
  
 Poniższy kod przedstawia definicję wskaźnik do elementu członkowskiego `i` w klasie `A`. Wskaźnik, `pai`, jest ustawiana na 0, co jest pustego wskaźnika.  
  
```  
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
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja języka C++](../cpp/cpp-language-reference.md)