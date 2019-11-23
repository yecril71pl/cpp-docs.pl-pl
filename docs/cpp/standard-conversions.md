---
title: Konwersje standardowe
ms.date: 10/02/2019
helpviewer_keywords:
- standard conversions, categories of
- L-values [C++]
- conversions, standard
ms.assetid: ce7ac8d3-5c99-4674-8229-0672de05528d
ms.openlocfilehash: c51a5ea5aaabb27babb9e4cd355721742088d31e
ms.sourcegitcommit: c51b2c665849479fa995bc3323a22ebe79d9d7ce
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "71998898"
---
# <a name="standard-conversions"></a>Konwersje standardowe

C++ Język definiuje konwersje między typami podstawowymi. Definiuje również konwersje dla typów pochodnych wskaźnika, odwołania i wskaźnika do elementu członkowskiego. Te konwersje są nazywane *konwersjemi standardowymi*.

W tej sekcji omówiono następujące Konwersje standardowe:

- Promocje integralne

- Konwersje całkowite

- Konwersje przestawne

- Konwersje zmiennoprzecinkowe i całkowite

- Konwersje arytmetyczne

- Konwersje wskaźników

- Konwersje odwołań

- Konwersje wskaźników do elementów członkowskich

  > [!NOTE]
  > Typy zdefiniowane przez użytkownika mogą określać własne konwersje. Konwersja typów zdefiniowanych przez użytkownika jest objęta [konstruktorami](../cpp/constructors-cpp.md) i [konwersjemi](../cpp/user-defined-type-conversions-cpp.md).

Poniższy kod powoduje konwersje (w tym przykładzie, Promocje całkowite):

```cpp
long  long_num1, long_num2;
int   int_num;

// int_num promoted to type long prior to assignment.
long_num1 = int_num;

// int_num promoted to type long prior to multiplication.
long_num2 = int_num * long_num2;
```

Wynik konwersji jest wartością l, tylko wtedy, gdy tworzy typ referencyjny. Na przykład zdefiniowana przez użytkownika konwersja zadeklarowana jako `operator int&()` zwraca odwołanie i jest l-wartością. Jednak konwersja zadeklarowana jako `operator int()` zwraca obiekt i nie jest l-wartością.

## <a name="integral-promotions"></a>Promocje integralne

Obiekty typu całkowitego mogą być konwertowane na inne szerszego typu całkowitego, czyli typu, który może reprezentować większy zestaw wartości. Ten rozszerzony typ konwersji nazywa się *promocją integralną*. Dzięki promocji typu całkowitego można użyć następujących typów w wyrażeniu, w którym można wykorzystać inny typ całkowity:

- Obiekty, literały i stałe typu **char** i **short int**

- Typów wyliczeniowych

- pola bitowe **int**

- Modułów wyliczających

C++promocje są "z zachowaniem wartości", ponieważ wartość po podwyższeniu poziomu powinna być taka sama jak wartość przed podwyższeniem poziomu. W promocjach z zachowaniem wartości, obiekty krótszych typów całkowitych (takie jak pola bitowe lub obiekty typu **char**) są podwyższane do typu **int** , jeśli **int** może reprezentować pełen zakres oryginalnego typu. Jeśli **int** nie może reprezentować pełnego zakresu wartości, obiekt zostanie podwyższony do typu **unsigned int**.  Chociaż ta strategia jest taka sama jak używana w standardowym języku C, konwersje z zachowaniem wartości nie zachowują "podpisu" obiektu.

Zachowujące wartość promocje i promocje, które zachowują znak zazwyczaj generują te same wyniki. Jednak mogą generować różne wyniki, jeśli podwyższony obiekt jest wyświetlany jako:

- Operand `/`, `%`, `/=`, `%=`, `<`, `<=`, `>`lub `>=`

   Operatory te opierają się na znaku w celu określenia wyniku. Zachowywanie wartości i oszczędność z zachowaniem konta daje różne wyniki w przypadku zastosowania do tych operandów.

- Lewy argument operacji `>>` lub `>>=`

   Te operatory traktują podpisane i niepodpisane liczby inaczej w operacji przesunięcia. W przypadku cyfr ze znakiem operacja przesunięcia w prawo propaguje bit znaku do pozycji opuszczone bit, natomiast pozycje bitu opuszczone są puste od zera w niepodpisanych ilościach.

- Argument funkcji przeciążonej lub operand przeciążonego operatora, który zależy od typu argumentu operacji dla dopasowywania argumentów. Aby uzyskać więcej informacji na temat definiowania przeciążonych operatorów, zobacz [przeciążone operatory](../cpp/operator-overloading.md).

## <a name="integral-conversions"></a>Konwersje całkowite

*Konwersje całkowite* są konwersjami między typami całkowitymi. Typy całkowite to **char**, **Short** (lub **short int**), **int**, **Long**i **Long Long**. Te typy mogą być kwalifikowane ze **znakiem** lub **bez znaku** **, a nie** mogą być używane jako skróty dla **niepodpisanych liczb całkowitych**.

### <a name="signed-to-unsigned"></a>Podpisana do niepodpisanego

Obiekty podpisanych typów całkowitych można przekonwertować na odpowiednie typy bez znaku. Gdy te konwersje wystąpią, faktyczny wzorzec bitowy nie zmienia się. Jednak interpretacja zmian danych. Rozważmy ten kod:

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

W powyższym przykładzie ze **znakiem Short**, `i`, jest zdefiniowany i zainicjowany do liczby ujemnej. Wyrażenie `(u = i)` powoduje, że `i` być konwertowane na **krótkie bez znaku** przed przypisaniem do `u`.

### <a name="unsigned-to-signed"></a>Niepodpisane z podpisem

Obiekty niepodpisanych typów całkowitych można przekonwertować na odpowiednie typy podpisane. Jeśli jednak wartość bez znaku jest poza zaprezentowanym zakresem typu podpisanego, wynik nie będzie miał poprawnej wartości, jak pokazano w następującym przykładzie:

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

W poprzednim przykładzie `u` jest **niepodpisanym krótkim** obiektem całkowitym, który musi zostać skonwertowany na liczbę ze znakiem, aby oszacować `(i = u)`wyrażenia. Ponieważ jej wartość nie może być poprawnie reprezentowana w formie **krótkiej**, dane są interpretowane jako pokazane.

## <a name="floating-point-conversions"></a>Konwersje zmiennoprzecinkowe

Obiekt typu zmiennoprzecinkowego może być bezpiecznie konwertowany na bardziej precyzyjny typ zmiennoprzecinkowy — to znaczy, że konwersja nie powoduje utraty znaczenia. Na przykład konwersje z typu **float** do **Double** lub z **podwójnego** na **Long Double** są bezpieczne, a wartość nie jest zmieniana.

Obiekt typu zmiennoprzecinkowego może być również konwertowany na mniej dokładny typ, jeśli znajduje się w zakresie, który jest zaprezentowany przez ten typ. (Zobacz [limity przestawne](../cpp/floating-limits.md) dla zakresów typów zmiennoprzecinkowych). Jeśli pierwotna wartość nie jest możliwa do zaprezentowania, można ją przekonwertować na następną wyższą lub następną dolną wartość. Wynik jest niezdefiniowany, jeśli taka wartość nie istnieje. Rozważmy następujący przykład:

```cpp
cout << (float)1E300 << endl;
```

Wartość maksymalna do zaprezentowania przez typ **float** to 3.402823466 E38 — dużo mniejsza liczba niż 1E300. W związku z tym liczba jest konwertowana na nieskończoność, a wynikiem jest "inf".

## <a name="conversions-between-integral-and-floating-point-types"></a>Konwersje między typami całkowitymi i zmiennoprzecinkowymi

Niektóre wyrażenia mogą spowodować przekonwertowanie obiektów typu zmiennoprzecinkowego na typy całkowite lub odwrotnie. Gdy obiekt typu całkowitego jest konwertowany na typ zmiennoprzecinkowy, a oryginalna wartość nie jest możliwa do zaprezentowania dokładnie, wynikiem jest kolejna wyższa lub Następna Dolna wartość.

Gdy obiekt typu zmiennoprzecinkowego jest konwertowany na typ całkowity, część ułamkowa jest *obcinana*lub zaokrąglana w kierunku zera. Liczba, na przykład 1,3, jest konwertowana na 1, a-1,3 jest konwertowana na-1. Jeśli wartość obcięta jest większa niż największa wartość, lub mniejsza niż najmniejsza wartość, wynik jest niezdefiniowany.

## <a name="arithmetic-conversions"></a>Konwersje arytmetyczne

Wiele operatorów binarnych (omówionych w [wyrażeniach z operatorami binarnymi](../cpp/expressions-with-binary-operators.md)) powoduje konwersje argumentów operacji i daje wyniki w taki sam sposób. Konwersje te powodują, że są to *typowe konwersje arytmetyczne*. Konwersje arytmetyczne operandów o różnych typach natywnych są wykonywane jak pokazano w poniższej tabeli. Typy typedef zachowują się zgodnie z ich podstawowymi typami natywnymi.

### <a name="conditions-for-type-conversion"></a>Warunki konwersji typów

|Spełnione warunki|Konwersja|
|--------------------|----------------|
|Oba operandy są typu **Long Double**.|Inny operand jest konwertowany na typ **Long Double**.|
|Poprzedni warunek nie jest spełniony, a oba operandy są typu **Double**.|Inny operand jest konwertowany na typ **Double**.|
|Powyższe warunki nie zostały spełnione, a oba operandy są typu **zmiennoprzecinkowego**.|Inny operand jest konwertowany na typ **float**.|
|Powyższe warunki nie są spełnione (żaden z operandów nie jest typu zmiennoprzecinkowego).|Operandy otrzymują całkowite promocje w następujący sposób:<br /><br />-Jeśli jeden z operandów jest typu **unsigned long**, drugi operand jest konwertowany na typ **unsigned long**.<br />-Jeśli poprzedni warunek nie został spełniony i jeśli którykolwiek z operandów jest typu **Long** , a drugi typ **int bez znaku**, oba operandy są konwertowane na typ **unsigned long**.<br />— Jeśli powyższe dwa warunki nie są spełnione i jeśli oba operandy są typu **Long**, drugi operand jest konwertowany na typ **Long**.<br />— Jeśli powyższe trzy warunki nie są spełnione, a jeśli oba operandy są typu **int bez znaku**, drugi operand jest konwertowany na typ **unsigned int**.<br />-Jeśli żaden z powyższych warunków nie zostanie spełniony, oba operandy są konwertowane na typ **int**.|

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

Pierwsza instrukcja w powyższym przykładzie pokazuje mnożenie dwóch typów całkowitych: `iVal` i `ulVal`. Spełniony warunek polega na tym, że żaden operand nie jest typu zmiennoprzecinkowego, a jeden operand jest typu **int bez znaku**. Dlatego drugi operand, `iVal`, jest konwertowany na typ **unsigned int**. Następnie wynik zostanie przypisany do `dVal`. Warunek został spełniony to oznacza, że jeden operand jest typu **Double**, więc **niepodpisany wynik int** operacji mnożenia jest konwertowany na typ **Double**.

Druga instrukcja w powyższym przykładzie pokazuje dodanie wartości **zmiennoprzecinkowej** i typu całkowitego: `fVal` i `ulVal`. Zmienna `ulVal` jest konwertowana na typ **float** (Trzeci warunek w tabeli). Wynik dodawania jest konwertowany na typ **Double** (drugi warunek w tabeli) i przypisany do `dVal`.

## <a name="pointer-conversions"></a>Konwersje wskaźników

Wskaźniki można przekonwertować podczas przypisywania, inicjowania, porównywania i innych wyrażeń.

### <a name="pointer-to-classes"></a>Wskaźnik do klas

Istnieją dwa przypadki, w których wskaźnik do klasy można przekonwertować na wskaźnik do klasy bazowej.

Pierwszym przypadkiem jest to, że określona klasa bazowa jest dostępna, a konwersja jest niejednoznaczna. Aby uzyskać więcej informacji na temat niejednoznacznych odwołań klas podstawowych, zobacz [wiele klas bazowych](../cpp/multiple-base-classes.md).

Określa, czy klasa bazowa jest dostępna, zależy od rodzaju dziedziczenia używanego do wyprowadzania. Rozważ dziedziczenie zilustrowane na poniższej ilustracji.

![Wykres dziedziczenia przedstawiający wykres dziedziczenia dostępności klasy podstawowej&#45;](../cpp/media/vc38xa1.gif "przedstawiający dostępność klasy podstawowej&#45;") <br/>
Wykres dziedziczenia dla zilustrowania dostępności klasy podstawowej

W poniższej tabeli przedstawiono dostępność klasy podstawowej dla sytuacji zilustrowanej na rysunku.

|Typ funkcji|Pochodnych|Konwersja z<br /><br /> B * na\*ą prawną?|
|----------------------|----------------|-------------------------------------------|
|Funkcja zewnętrzna (nieobjęta zakresem klasy)|Prywatna|Nie|
||Chronione|Nie|
||Publiczne|Tak|
|B funkcja członkowska (w zakresie B)|Prywatna|Tak|
||Chronione|Tak|
||Publiczne|Tak|
|Funkcja członkowska języka c (w zakresie języka C)|Prywatna|Nie|
||Chronione|Tak|
||Publiczne|Tak|

Drugi przypadek, w którym wskaźnik do klasy może być konwertowany na wskaźnik do klasy bazowej, jest używany w przypadku jawnej konwersji typu. Aby uzyskać więcej informacji na temat jawnych konwersji typów, zobacz [operator Explicit konwersji typu](explicit-type-conversion-operator-parens.md).

Wynikiem takiej konwersji jest wskaźnik do *podobiektu*, część obiektu, która jest całkowicie opisana przez klasę bazową.

Poniższy kod definiuje dwie klasy, `A` i `B`, gdzie `B` pochodzi od `A`. (Aby uzyskać więcej informacji na temat dziedziczenia, zobacz [klasy pochodne](../cpp/inheritance-cpp.md)). Następnie definiuje `bObject`, obiekt typu `B`i dwa wskaźniki (`pA` i `pB`) wskazujące na obiekt.

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

`pA` wskaźnika jest typu `A *`, który może być interpretowany jako "wskaźnik do obiektu typu `A`". Elementy członkowskie `bObject` (takie jak `BComponent` i `BMemberFunc`) są unikatowe dla typu `B` i w związku z tym są niedostępne za poorednictwem `pA`. Wskaźnik `pA` umożliwia dostęp tylko do tych cech charakterystycznych (funkcje składowe i dane) obiektu, które są zdefiniowane w `A`klas.

### <a name="pointer-to-function"></a>Wskaźnik do funkcji

Wskaźnik do funkcji można przekonwertować na typ `void *`, jeśli typ `void *` jest wystarczająco duży, aby pomieścić ten wskaźnik.

### <a name="pointer-to-void"></a>Wskaźnik na typ void

Wskaźniki do typu **void** mogą być konwertowane na wskaźniki do dowolnego innego typu, ale tylko w przypadku jawnego rzutowania typu (w przeciwieństwie do języka C). Wskaźnik do dowolnego typu można przekonwertować niejawnie na wskaźnik do typu **void**. Wskaźnik do niekompletnego obiektu typu można przekonwertować na wskaźnik na **typ void** (niejawnie) i odwrotnie (jawnie). Wynik takiej konwersji jest równy wartości oryginalnego wskaźnika. Obiekt jest uznawany za niekompletny, jeśli jest zadeklarowany, ale nie ma wystarczających informacji, aby określić jego rozmiar lub klasę bazową.

Wskaźnik do dowolnego obiektu, który nie jest **stałą** lub **volatile** , może być niejawnie konwertowany na wskaźnik typu `void *`.

### <a name="const-and-volatile-pointers"></a>const i volatile, wskaźniki

C++nie dostarcza standardowej konwersji z typu **const** lub **volatile** na typ, który nie jest **stałą** lub **nietrwały**. Jednak każde sortowanie konwersji można określić za pomocą jawnego rzutowania typu (w tym konwersje, które są niebezpieczne).

> [!NOTE]
> C++wskaźniki do elementów członkowskich, z wyjątkiem wskaźników do statycznych elementów członkowskich, różnią się od normalnych wskaźników i nie mają tych samych konwersji standardowych. Wskaźniki do statycznych elementów członkowskich są normalnymi wskaźnikami i mają takie same konwersje jak normalne wskaźniki.

### <a name="null-pointer-conversions"></a>Konwersje wskaźnika o wartości null

Wyrażenie stałej całkowitej, którego wynikiem jest wartość zero lub takie rzutowanie wyrażenia na typ wskaźnika, jest konwertowane na wskaźnik o nazwie *wskaźnik o wartości null*. Ten wskaźnik zawsze porównuje nierówne wskaźnikiem z dowolnym prawidłowym obiektem lub funkcją. Wyjątek jest wskaźnikiem do obiektów opartych na obiektach, które mogą mieć te same przesunięcie i nadal wskazują na inne obiekty.

W języku C++ 11, typ [nullptr](../cpp/nullptr.md) powinien być preferowany dla wskaźnika o wartości null w stylu C.

### <a name="pointer-expression-conversions"></a>Konwersje wyrażeń wskaźnika

Dowolne wyrażenie z typem tablicowym można przekonwertować na wskaźnik tego samego typu. Wynikiem konwersji jest wskaźnik do pierwszego elementu tablicy. Poniższy przykład ilustruje taką konwersję:

```cpp
char szPath[_MAX_PATH]; // Array of type char.
char *pszPath = szPath; // Equals &szPath[0].
```

Wyrażenie, które powoduje zwrócenie funkcji zwracającej określony typ, jest konwertowane na wskaźnik do funkcji zwracającej ten typ, z wyjątkiem sytuacji, gdy:

- Wyrażenie jest używane jako operand do operatora address-of ( **&** ).

- Wyrażenie jest używane jako argument operacji operatora wywołania funkcji.

## <a name="reference-conversions"></a>Konwersje odwołań

Odwołanie do klasy może być konwertowane na odwołanie do klasy bazowej w takich przypadkach:

- Określona klasa bazowa jest dostępna.

- Konwersja jest niejednoznaczna. (Aby uzyskać więcej informacji na temat niejednoznacznych odwołań klas podstawowych, zobacz [wiele klas bazowych](../cpp/multiple-base-classes.md)).

Wynikiem konwersji jest wskaźnik do podobiektu, który reprezentuje klasę bazową.

## <a name="pointer-to-member"></a>Wskaźnik do elementu członkowskiego

Wskaźniki do elementów członkowskich klasy mogą być konwertowane podczas przypisywania, inicjowania, porównywania i innych wyrażeń. W tej sekcji opisano następujące Konwersje wskaźników do elementów członkowskich:

### <a name="pointer-to-base-class-member"></a>Wskaźnik do składowej klasy bazowej

Wskaźnik do składowej klasy bazowej można przekonwertować na wskaźnik do elementu członkowskiego klasy pochodnej, gdy spełnione są następujące warunki:

- Konwersja odwrotna ze wskaźnika do klasy pochodnej na wskaźnik klasy podstawowej jest dostępna.

- Klasa pochodna nie dziedziczy praktycznie z klasy bazowej.

Gdy argument operacji po lewej stronie jest wskaźnikiem do elementu członkowskiego, prawy operand musi być typu wskaźnika do składowej lub być wyrażeniem stałym, którego wynikiem jest 0. To przypisanie jest prawidłowe tylko w następujących przypadkach:

- Prawy operand jest wskaźnikiem do składowej tej samej klasy, co lewy argument operacji.

- Lewy operand jest wskaźnikiem do składowej klasy pochodnej publicznie i jednoznacznie z klasy argumentu operacji po prawej stronie.

### <a name="null-pointer-to-member-conversions"></a>pusty wskaźnik do konwersji elementów członkowskich

Wyrażenie stałej całkowitej, którego wynikiem jest zero, jest konwertowane na wskaźnik o wartości null. Ten wskaźnik zawsze porównuje nierówne wskaźnikiem z dowolnym prawidłowym obiektem lub funkcją. Wyjątek jest wskaźnikiem do obiektów opartych na obiektach, które mogą mieć te same przesunięcie i nadal wskazują na inne obiekty.

Poniższy kod ilustruje definicję wskaźnika do składowej `i` w klasie `A`. Wskaźnik, `pai`, jest zainicjowany do 0, który jest wskaźnikiem o wartości null.

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

[C++Dokumentacja języka](../cpp/cpp-language-reference.md)