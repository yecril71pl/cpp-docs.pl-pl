---
title: Funkcje śródwierszowe (C++)
ms.date: 10/09/2018
f1_keywords:
- __forceinline_cpp
- __inline_cpp
- inline_cpp
- __inline
- _inline
- __forceinline
- _forceinline
helpviewer_keywords:
- inline functions [C++], class members
ms.assetid: 355f120c-2847-4608-ac04-8dda18ffe10c
ms.openlocfilehash: 703c04873a733d068da025b595909ecc681ff147
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374087"
---
# <a name="inline-functions-c"></a>Funkcje śródwierszowe (C++)

Funkcja zdefiniowana w treści deklaracji klasy jest funkcją wbudowaną.

## <a name="example"></a>Przykład

W poniższej deklaracji `Account` klasy konstruktor jest funkcją wbudowaną. Funkcje `GetBalance`członkowskie `Deposit`, `Withdraw` i nie są określone jako **wbudowane,** ale mogą być implementowane jako wbudowane funkcje.

```cpp
// Inline_Member_Functions.cpp
class Account
{
public:
    Account(double initial_balance) { balance = initial_balance; }
    double GetBalance();
    double Deposit( double Amount );
    double Withdraw( double Amount );
private:
    double balance;
};

inline double Account::GetBalance()
{
    return balance;
}

inline double Account::Deposit( double Amount )
{
    return ( balance += Amount );
}

inline double Account::Withdraw( double Amount )
{
    return ( balance -= Amount );
}
int main()
{
}
```

> [!NOTE]
> W deklaracji klasy funkcje zostały zadeklarowane bez słowa kluczowego **wbudowanego.** Słowo kluczowe **w łańce** można określić w deklaracji klasy; wynik jest taki sam.

Dana wbudowana funkcja elementu członkowskiego musi być zadeklarowana w taki sam sposób w każdej jednostce kompilacji. To ograniczenie powoduje, że funkcje wbudowane zachowują się tak, jakby były tworzone funkcje. Ponadto musi istnieć dokładnie jedna definicja funkcji wbudowanej.

Funkcja elementu członkowskiego klasy domyślnie łączy się z powiązaniem zewnętrznym, chyba że definicja tej funkcji zawiera specyfikator **wbudowany.** W poprzednim przykładzie pokazano, że te funkcje nie muszą być jawnie zadeklarowane z **wbudowanym specyfikatorem;** użycie **wbudowanego w** definicji funkcji powoduje, że jest to funkcja wbudowana. Jednak jest to niezgodne z prawem do ponownego zadeklarowania funkcji jako **wbudowane** po wywołaniu tej funkcji.

## <a name="inline-__inline-and-__forceinline"></a>Inline, __inline i \__forceinline

Specyfikatory **wbudowane** i **__inline** instruują kompilatora, aby wstawił kopię treści funkcji do każdego miejsca, w które wywoływana jest funkcja.

Wstawianie (nazywane rozszerzeniem wbudowanym lub inline) występuje tylko wtedy, gdy analiza kosztów i korzyści kompilatora pokazuje, że jest rentowna. Rozszerzenie wbudowane łagodzi obciążenie wywołaniem funkcji przy potencjalnym koszcie większego rozmiaru kodu.

Słowo kluczowe **__forceinline** zastępuje analizę kosztów i korzyści i opiera się na ocenie programisty. Należy zachować ostrożność podczas korzystania **z __forceinline**. Masowe użycie **__forceinline** może spowodować większy kod z tylko marginalnym wzrostem wydajności lub, w niektórych przypadkach, nawet utratą wydajności (na przykład ze względu na zwiększone stronicowanie większego pliku wykonywalnego).

Korzystanie z funkcji wbudowanych może przyspieszyć program, ponieważ eliminują obciążenie związane z wywołaniami funkcji. Funkcje rozszerzone wbudowane podlegają optymalizacji kodu nie są dostępne dla normalnych funkcji.

Kompilator traktuje wbudowane opcje rozszerzania i słowa kluczowe jako sugestie. Nie ma żadnej gwarancji, że funkcje będą inlined. Nie można wymusić kompilatora do wbudowanej określonej funkcji, nawet w **przypadku __forceinline** słowa kluczowego. Podczas kompilowania z **/clr**kompilator nie będzie wbudowany funkcji, jeśli istnieją atrybuty zabezpieczeń stosowane do funkcji.

**Wbudowane** słowo kluczowe jest dostępne tylko w języku C++. Słowa kluczowe **__inline** i **__forceinline** są dostępne zarówno w językach C, jak i C++. W celu zapewnienia zgodności z poprzednimi wersjami **_inline** i **_forceinline** są synonimami **__inline**i **__forceinline** chyba że określono opcję kompilatora [/Za \(Wyłącz rozszerzenia języka).](../build/reference/za-ze-disable-language-extensions.md)

**Wbudowane** słowo kluczowe informuje kompilator, że preferowane jest rozszerzenie wbudowane. Jednak kompilator można utworzyć oddzielne wystąpienie funkcji (tworzenie wystąpienia) i utworzyć standardowe powiązania połączeń zamiast wstawiania kodu wbudowanego. Dwa przypadki, w których może się to zdarzyć, to:

- Funkcje cykliczne.

- Funkcje, o których mowa za pomocą wskaźnika w innym miejscu jednostki tłumaczenia.

Powody te mogą kolidować z inlining, *podobnie jak inne,* według uznania kompilatora; nie należy polegać na **specyfikatorze wbudowanym,** aby spowodować, że funkcja ma być inlined.

Podobnie jak w normalnych funkcjach, nie ma zdefiniowanej kolejności oceny argumentów do funkcji wbudowanej. W rzeczywistości może się różnić od kolejności, w której argumenty są oceniane podczas przekazywania przy użyciu normalnego protokołu wywołania funkcji.

Opcja optymalizacji kompilatora [/Ob](../build/reference/ob-inline-function-expansion.md) pomaga określić, czy rozszerzenie funkcji wbudowanej faktycznie występuje.

[/LTCG](../build/reference/ltcg-link-time-code-generation.md) wykonuje inlining między modułami niezależnie od tego, czy został poproszony w kodzie źródłowym.

### <a name="example-1"></a>Przykład 1

```cpp
// inline_keyword1.cpp
// compile with: /c
inline int max( int a , int b ) {
   if( a > b )
      return a;
   return b;
}
```

Funkcje członkowskie klasy można zadeklarować w linii wbudowanej za pomocą słowa kluczowego **wbudowanego** lub umieszczając definicję funkcji w definicji klasy.

### <a name="example-2"></a>Przykład 2

```cpp
// inline_keyword2.cpp
// compile with: /EHsc /c
#include <iostream>
using namespace std;

class MyClass {
public:
   void print() { cout << i << ' '; }   // Implicitly inline
private:
   int i;
};
```

**Specyficzne dla firmy Microsoft**

__inline **__inline** słowo kluczowe jest **równoważne wbudowanemu**.

Nawet w **przypadku __forceinline**kompilator nie może wbudowany kod we wszystkich okolicznościach. Kompilator nie może wbudowanej funkcji, jeśli:

- Funkcja lub jej wywołujący jest skompilowany z /Ob0 (domyślna opcja dla kompilacji debugowania).

- Funkcja i wywołujący używać różnych typów obsługi wyjątków (obsługa wyjątków C++ w jednym, obsługa wyjątków strukturalnych w drugiej).

- Funkcja ma listę argumentów zmiennych.

- Funkcja używa zestawu wbudowanego, chyba że skompilowano z /Og, /Ox, /O1 lub /O2.

- Funkcja jest cykliczna i nie towarzyszy **#pragma inline_recursion(on)**. Z pragmy, funkcje cykliczne są inlined do domyślnej głębokości 16 wywołań. Aby zmniejszyć głębokość wskładnia, należy użyć [inline_depth](../preprocessor/inline-depth.md) pragmy.

- Funkcja jest wirtualna i jest wywoływana wirtualnie. Bezpośrednie wywołania funkcji wirtualnych mogą być inlined.

- Program przyjmuje adres funkcji i wywołanie odbywa się za pomocą wskaźnika do funkcji. Bezpośrednie połączenia z funkcjami, które miały swój adres podjęte mogą być inlined.

- Funkcja jest również oznaczona modyfikatorem [__declspec](../cpp/declspec.md) [nagim.](../cpp/naked-cpp.md)

Jeśli kompilator nie może wbudowanej funkcji zadeklarowanej za pomocą **__forceinline,** generuje ostrzeżenie poziomu 1, z wyjątkiem sytuacji, gdy:

- Funkcja jest kompilowana przy użyciu /Od lub /Ob0. W takich przypadkach nie oczekuje się inlineingu.

- Funkcja jest definiowana zewnętrznie, w dołączonej bibliotece lub innej jednostce tłumaczenia lub jest obiektem docelowym wywołania wirtualnego lub obiektem docelowym wywołania pośredniego. Kompilator nie może zidentyfikować kodu nienaklinowanego, który nie może znaleźć w bieżącej jednostce tłumaczenia.

Funkcje cykliczne można zastąpić wbudowane do głębokości określonej przez [pragmy inline_depth,](../preprocessor/inline-depth.md) maksymalnie do 16 wywołań. Po tej głębokości wywołania funkcji cyklicznej są traktowane jako wywołania wystąpienia funkcji.  Głębokość, do której są badane funkcje cykliczne przez heurystykę w linii, nie może przekraczać 16. [Pragma inline_recursion](../preprocessor/inline-recursion.md) kontroluje wbudowaną ekspansję funkcji, która jest obecnie rozbudowyna. Zobacz [opcję kompilatora rozszerzenia funkcji wbudowanych](../build/reference/ob-inline-function-expansion.md) (/Ob), aby uzyskać informacje pokrewne.

**ZAKOŃCZ Specyficzne dla firmy Microsoft**

Aby uzyskać więcej informacji na temat używania **specyfikatora wbudowanego,** zobacz:

- [Funkcje elementów członkowskich klasy wbudowanej](../cpp/inline-functions-cpp.md)

- [Definiowanie wbudowanych funkcji C++ z dllexport i dllimport](../cpp/defining-inline-cpp-functions-with-dllexport-and-dllimport.md)

## <a name="when-to-use-inline-functions"></a>Kiedy używać funkcji wbudowanych

Wbudowane funkcje są najlepiej używane dla małych funkcji, takich jak uzyskiwanie dostępu do prywatnych elementów członkowskich danych. Głównym celem tych jedno- lub dwuwierszowych funkcji "akcesor" jest zwrócenie informacji o stanie obiektów; funkcje krótkie są wrażliwe na obciążenie wywołań funkcji. Dłuższe funkcje spędzają proporcjonalnie mniej czasu w sekwencji wywoływania/zwracania i korzystają mniej z inline.

Klasę `Point` można zdefiniować w następujący sposób:

```cpp
// when_to_use_inline_functions.cpp
class Point
{
public:
    // Define "accessor" functions as
    //  reference types.
    unsigned& x();
    unsigned& y();
private:
    unsigned _x;
    unsigned _y;
};

inline unsigned& Point::x()
{
    return _x;
}
inline unsigned& Point::y()
{
    return _y;
}
int main()
{
}
```

Przy założeniu, że manipulowanie współrzędnymi jest stosunkowo powszechną`x` `y` operacją w kliencie takiej klasy, określając dwie funkcje akcesora (i w poprzednim przykładzie), ponieważ **wbudowany** zazwyczaj zapisuje obciążenie na:

- Wywołania funkcji (w tym przekazywanie parametrów i umieszczanie adresu obiektu na stosie)

- Zachowanie ramy stosu rozmówcy

- Nowa konfiguracja ramki stosu

- Komunikacja zwrotu i wartości

- Przywracanie starej ramki stosu

- Zwraca

## <a name="inline-functions-vs-macros"></a>Funkcje wbudowane a makra

Chociaż funkcje wbudowane są podobne do makr (ponieważ kod funkcji jest rozwijany w punkcie wywołania w czasie kompilacji), wbudowane funkcje są analizowane przez kompilator, podczas gdy makra są rozszerzane przez preprocesor. W rezultacie istnieje kilka istotnych różnic:

- Funkcje wbudowane są zgodne ze wszystkimi protokołami bezpieczeństwa typu wymuszanym na normalnych funkcjach.

- Wbudowane funkcje są określone przy użyciu tej samej składni, jak każda inna funkcja, z tą różnicą, że zawierają one **wbudowane** słowo kluczowe w deklaracji funkcji.

- Wyrażenia przekazywane jako argumenty do funkcji wbudowanych są oceniane raz. W niektórych przypadkach wyrażenia przekazywane jako argumenty do makr mogą być oceniane więcej niż jeden raz.

W poniższym przykładzie przedstawiono makro konwertujące małe litery na wielkie litery:

```cpp
// inline_functions_macro.c
#include <stdio.h>
#include <conio.h>

#define toupper(a) ((a) >= 'a' && ((a) <= 'z') ? ((a)-('a'-'A')):(a))

int main() {
   char ch;
   printf_s("Enter a character: ");
   ch = toupper( getc(stdin) );
   printf_s( "%c", ch );
}
//  Sample Input:  xyz
// Sample Output:  Z
```

Intencją wyrażenia `toupper(getc(stdin))` jest to, że znak powinien być`stdin`odczytywany z urządzenia konsoli ( ) i, jeśli to konieczne, konwertowany na wielkie litery.

Ze względu na implementację `getc` makra, jest wykonywany raz, aby ustalić, czy znak jest większy lub równy "a", a raz, aby ustalić, czy jest mniejszy lub równy "z". Jeśli znajduje się w `getc` tym zakresie, jest wykonywany ponownie, aby przekonwertować znak na wielkie litery. Oznacza to, że program czeka na dwa lub trzy znaki, gdy, najlepiej, powinien czekać tylko na jeden.

Funkcje wbudowane rozwiązuje opisany wcześniej problem:

```cpp
// inline_functions_inline.cpp
#include <stdio.h>
#include <conio.h>

inline char toupper( char a ) {
   return ((a >= 'a' && a <= 'z') ? a-('a'-'A') : a );
}

int main() {
   printf_s("Enter a character: ");
   char ch = toupper( getc(stdin) );
   printf_s( "%c", ch );
}
```

```Output
Sample Input: a
Sample Output: A
```

## <a name="see-also"></a>Zobacz też

[noinline](../cpp/noinline.md)<br/>
[auto_inline](../preprocessor/auto-inline.md)
