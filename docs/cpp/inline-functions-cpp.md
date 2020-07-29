---
title: Funkcje śródwierszowe (C++)
description: Wbudowanego słowa kluczowego C++ można użyć, aby zasugerować wbudowane funkcje do kompilatora.
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
ms.openlocfilehash: d2356d7813167f3973ac2748423c6af7f0b5573b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227416"
---
# <a name="inline-functions-c"></a>Funkcje śródwierszowe (C++)

Funkcja zdefiniowana w treści deklaracji klasy jest funkcją wbudowaną.

## <a name="example"></a>Przykład

W poniższej deklaracji klasy `Account` Konstruktor jest funkcją wbudowaną. Funkcje składowe `GetBalance` , `Deposit` i `Withdraw` nie są określone jako, **`inline`** ale mogą być implementowane jako funkcje wbudowane.

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
> W deklaracji klasy funkcje zostały zadeklarowane bez **`inline`** słowa kluczowego. **`inline`** Słowo kluczowe może być określone w deklaracji klasy; wynik jest taki sam.

Dana Wbudowana funkcja członkowska musi być zadeklarowana w taki sam sposób w każdej jednostce kompilacji. To ograniczenie powoduje, że funkcje wbudowane zachowują się tak, jakby były wystąpieniami funkcji. Ponadto należy mieć dokładnie jedną definicję wbudowanej funkcji.

Funkcja członkowska klasy domyślnie łączy zewnętrzny, chyba że definicja tej funkcji zawiera **`inline`** specyfikator. Powyższy przykład pokazuje, że nie trzeba deklarować tych funkcji jawnie za pomocą **`inline`** specyfikatora. Użycie **`inline`** w definicji funkcji powoduje, że jest funkcją wbudowaną. Jednakże nie można ponownie zadeklarować funkcji jako **`inline`** po wywołaniu tej funkcji.

## <a name="inline-__inline-and-__forceinline"></a>`inline`, `__inline` i`__forceinline`

**`inline`** **`__inline`** Specyfikatory i instruują kompilator, aby wstawiali kopię treści funkcji w każdym miejscu, w którym wywoływana jest funkcja.

Wstawianie, nazywane *rozwinięciem wbudowanym* lub *dekonspektem*, występuje tylko wtedy, gdy analiza kosztów i korzyści kompilatora pokazuje, że jest to wartościowa. Rozszerzanie wbudowane minimalizuje obciążenie wywołania funkcji z potencjalnym kosztem większego rozmiaru kodu.

**`__forceinline`** Słowo kluczowe przesłania analizę kosztu korzyści i opiera się na ocenie programisty. Należy zachować ostrożność podczas korzystania z programu **`__forceinline`** . Użycie programu **`__forceinline`** może spowodować powstanie większego kodu z tylko marginalnymi wzrostami wydajności lub, w niektórych przypadkach, nawet strat wydajności (z powodu zwiększonego stronicowania większego pliku wykonywalnego, na przykład).

Korzystanie z funkcji wbudowanych może przyspieszyć pracę programu, ponieważ eliminuje obciążenie związane z wywołaniami funkcji. Wbudowane funkcje functions podlegają optymalizacji kodu, które nie są dostępne dla normalnych funkcji.

Kompilator traktuje wbudowane opcje rozwijania i słowa kluczowe jako sugestie. Nie ma gwarancji, że funkcje są wbudowane. Nie można wymusić, aby kompilator przetworzył konkretną funkcję, nawet ze **`__forceinline`** słowem kluczowym. Podczas kompilowania przy użyciu **`/clr`** , kompilator nie będzie wbudowana funkcji, jeśli istnieją atrybuty zabezpieczeń zastosowane do funkcji.

**`inline`** Słowo kluczowe jest dostępne tylko w języku C++. **`__inline`** **`__forceinline`** Słowa kluczowe i są dostępne zarówno w C, jak i C++. W celu zapewnienia zgodności z poprzednimi wersjami **`_inline`** i **`_forceinline`** są synonimami dla **`__inline`** i, **`__forceinline`** chyba że opcja kompilatora [ `/Za` \( Wyłącz rozszerzenia języka)](../build/reference/za-ze-disable-language-extensions.md) jest określona.

**`inline`** Słowo kluczowe informuje kompilator, że jest preferowane rozwijanie wbudowane. Jednak kompilator może utworzyć oddzielne wystąpienie funkcji (instancji) i utworzyć standardowe powiązania wywołań zamiast wstawiania kodu wbudowanego. Dwa sytuacje, w których takie zachowanie może wystąpić:

- Funkcje cykliczne.

- Funkcje, które są określane za pomocą wskaźnika w innym miejscu w jednostce translacji.

Te przyczyny mogą zakłócać tworzenie, jak to *inne*, od uznania kompilatora; nie należy zależeć od **`inline`** specyfikatora, aby spowodować, że funkcja ma być wbudowana.

Podobnie jak w przypadku normalnych funkcji, nie zdefiniowano kolejności dla obliczeń argumentu w funkcji wbudowanej. W rzeczywistości może różnić się od kolejności oceny argumentu podczas przekazywania przy użyciu normalnego protokołu wywołania funkcji.

[`/Ob`](../build/reference/ob-inline-function-expansion.md)Opcja optymalizacji kompilatora pomaga ustalić, czy w rzeczywistości występuje rozwijanie funkcji wbudowanej.

[`/LTCG`](../build/reference/ltcg-link-time-code-generation.md)wykonuje międzymodułowe odwołanie, niezależnie od tego, czy jest ono żądane w kodzie źródłowym.

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

Funkcje składowe klasy mogą być deklarowane wewnętrznie przy użyciu **`inline`** słowa kluczowego lub przez umieszczenie definicji funkcji w definicji klasy.

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

**specyficzne dla firmy Microsoft**

**`__inline`** Słowo kluczowe jest równoważne **`inline`** .

Nawet z **`__forceinline`** , kompilator nie może w żaden sposób zakodować kodu. Kompilator nie może wbudowana funkcji, jeśli:

- Funkcja lub jej obiekt wywołujący jest kompilowany z **`/Ob0`** (opcją domyślną dla kompilacji debugowania).

- Funkcja i obiekt wywołujący używają różnych typów obsługi wyjątków (obsługa wyjątków C++ w jednej, strukturalnej obsługi wyjątków w innym).

- Funkcja ma listę zmiennych argumentów.

- Funkcja używa wbudowanego zestawu, chyba że jest kompilowany z **`/Ox`** , **`/O1`** , lub **`/O2`** .

- Funkcja jest cykliczna i nie ma **`#pragma inline_recursion(on)`** ustawionej wartości. W przypadku dyrektywy pragma funkcje cykliczne są wbudowane w domyślną głębokość wynoszącą 16 wywołań. Aby zmniejszyć głębokość wyznaczania, użyj [`inline_depth`](../preprocessor/inline-depth.md) dyrektywy pragma.

- Funkcja jest wirtualna i jest wywoływana praktycznie. Bezpośrednie wywołania funkcji wirtualnych mogą być wbudowane.

- Program pobiera adres funkcji, a wywołanie jest nawiązywane za pośrednictwem wskaźnika do funkcji. Bezpośrednie wywołania do funkcji, które miały swój adres, mogą być umieszczone w wierszu.

- Funkcja jest również oznaczona [`naked`](../cpp/naked-cpp.md) [`__declspec`](../cpp/declspec.md) modyfikatorem.

Jeśli kompilator nie może Wbudowana funkcja zadeklarowana z **`__forceinline`** , generuje ostrzeżenie poziomu 1, z wyjątkiem sytuacji, gdy:

- Funkcja jest skompilowana przy użyciu/od lub/Ob0. W takich przypadkach nie jest oczekiwany sposób wykreślania.

- Funkcja jest zdefiniowana zewnętrznie, w dołączonej bibliotece lub innej jednostce tłumaczenia albo jest obiektem docelowym wywołania wirtualnego lub obiektem docelowym wywołania pośredniego. Kompilator nie może zidentyfikować kodu nieliniowego, którego nie można znaleźć w bieżącej jednostce tłumaczenia.

Funkcje cykliczne mogą zostać zastąpione kodem wbudowanym do głębokości określonej przez [`inline_depth`](../preprocessor/inline-depth.md) pragmę, maksymalnie do 16 wywołań. Po tej głębokości wywołania funkcji cyklicznej są traktowane jako wywołania do wystąpienia funkcji.  Głębokość, do której funkcje cykliczne są analizowane przez wbudowany algorytm heurystyczny, nie może przekraczać 16. [`inline_recursion`](../preprocessor/inline-recursion.md)Pragma kontroluje wbudowane rozwijanie funkcji obecnie pod ekspansją. Aby uzyskać powiązane [informacje, zobacz](../build/reference/ob-inline-function-expansion.md) opcję kompilatora (/ob).

**ZAKOŃCZENIE określonych przez firmę Microsoft**

Aby uzyskać więcej informacji na temat używania **`inline`** specyfikatora, zobacz:

- [Funkcje składowe klasy wbudowanej](../cpp/inline-functions-cpp.md)

- [Definiowanie wbudowanych funkcji języka C++ z dllexport i dllimport](../cpp/defining-inline-cpp-functions-with-dllexport-and-dllimport.md)

## <a name="when-to-use-inline-functions"></a>Kiedy używać funkcji wbudowanych

Funkcje śródwierszowe najlepiej używać w przypadku małych funkcji, takich jak dostęp do prywatnych elementów członkowskich danych. Głównym celem tych funkcji "akcesora" o jednej lub dwóch wierszach jest zwrócenie informacji o stanie dotyczących obiektów. Krótkie funkcje są wrażliwe na obciążenie wywołań funkcji. Więcej funkcji poświęca proporcjonalnie krótszy czas w wywołaniu i zwracaniu sekwencji oraz korzyści mniejsze od tworzenia.

`Point`Klasę można zdefiniować w następujący sposób:

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

Przy założeniu, że manipulacja koordynuje jest relatywnie powszechną operacją na kliencie takiej klasy, określając dwie funkcje dostępu ( `x` i `y` w poprzednim przykładzie), co **`inline`** zwykle oszczędza obciążenie:

- Wywołania funkcji (łącznie z przekazywaniem parametrów i umieszczaniem adresu obiektu na stosie)

- Zachowywanie ramki stosu obiektu wywołującego

- Nowa konfiguracja ramki stosu

- Komunikacja zwrotna z wartością

- Przywracanie starej ramki stosu

- Przesłać

## <a name="inline-functions-vs-macros"></a>Funkcje wbudowane a makra

Wbudowane funkcje są podobne do makr, ponieważ kod funkcji jest rozwinięty w punkcie wywołania w czasie kompilacji. Jednak funkcje wbudowane są analizowane przez kompilator, a makra są rozszerzane przez preprocesor. W związku z tym istnieje kilka istotnych różnic:

- Wbudowane funkcje przestrzegają wszystkich protokołów bezpieczeństwa typów wymuszanych w normalnych funkcjach.

- Funkcje wbudowane są określane przy użyciu tej samej składni co inna funkcja, z tą różnicą, że zawierają **`inline`** słowo kluczowe w deklaracji funkcji.

- Wyrażenia przekazane jako argumenty funkcji wbudowanych są oceniane raz. W niektórych przypadkach wyrażenia przekazane jako argumenty do makr można obliczyć więcej niż raz.

W poniższym przykładzie pokazano makro, które konwertuje małe litery na wielkie:

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

Celem wyrażenia `toupper(getc(stdin))` jest, że znak powinien być odczytany z urządzenia konsoli ( `stdin` ) i, w razie potrzeby, konwertowany na wielkie litery.

Ze względu na implementację makra `getc` jest wykonywane raz, aby określić, czy znak jest większy niż lub równy "a", i raz, aby określić, czy jest on mniejszy niż lub równy "z". Jeśli znajduje się w tym zakresie, `getc` jest wykonywane ponownie w celu przekonwertowania znaku na wielkie litery. Oznacza to, że program czeka dwa lub trzy znaki, w idealnym przypadku, powinien oczekiwać tylko na jeden.

Funkcje wbudowane zaradzą opisany wcześniej problem:

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

## <a name="see-also"></a>Zobacz także

[`noinline`](../cpp/noinline.md)<br/>
[`auto_inline`](../preprocessor/auto-inline.md)
