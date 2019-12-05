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
ms.openlocfilehash: efaaacc46f63ac1a702ab2110d35fe80727ead1d
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857518"
---
# <a name="inline-functions-c"></a>Funkcje śródwierszowe (C++)

Funkcja zdefiniowana w treści deklaracji klasy jest funkcją wbudowaną.

## <a name="example"></a>Przykład

W poniższej deklaracji klasy Konstruktor `Account` jest funkcją wbudowaną. Funkcje składowe `GetBalance`, `Deposit`i `Withdraw` nie są określone jako **wbudowane** , ale mogą być implementowane jako funkcje wbudowane.

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
>  W deklaracji klasy funkcje zostały zadeklarowane bez **wbudowanego** słowa kluczowego. **Wbudowane** słowo kluczowe można określić w deklaracji klasy; wynik jest taki sam.

Dana Wbudowana funkcja członkowska musi być zadeklarowana w taki sam sposób w każdej jednostce kompilacji. To ograniczenie powoduje, że funkcje wbudowane zachowują się tak, jakby były wystąpieniami funkcji. Ponadto należy mieć dokładnie jedną definicję wbudowanej funkcji.

Funkcja członkowska klasy domyślnie łączy zewnętrzny, chyba że definicja tej funkcji zawiera specyfikator **wbudowany** . W poprzednim przykładzie pokazano, że te funkcje nie muszą być jawnie zadeklarowane za pomocą specyfikatora **wbudowanego** ; Użycie **wbudowanej** w definicji funkcji powoduje, że jest funkcją wbudowaną. Nie można jednak ponownie zadeklarować funkcji jako **wbudowanej** po wywołaniu tej funkcji.

## <a name="inline-__inline-and-__forceinline"></a>Wbudowane, __inline i \__forceinline

Specyfikatory **inline** i **__inline** instruują kompilator, aby wstawiali kopię treści funkcji w każdym miejscu, w którym wywoływana jest funkcja.

Wstawianie (nazywane rozwinięciem wbudowanym lub deokładziną) występuje tylko wtedy, gdy analiza kosztów/korzyści kompilatora zostanie wyświetlona, aby uzyskać zyskowność. Rozszerzanie wbudowane zmniejsza obciążenie wywołania funkcji przy potencjalnym kosztie większego rozmiaru kodu.

Słowo kluczowe **__forceinline** przesłania analizę kosztów/korzyści i opiera się na ocenie programisty. Należy zachować ostrożność podczas korzystania z **__forceinline**. Użycie **__forceinline** może spowodować zwiększenie kodu z uwzględnieniem tylko krańcowych korzyści z wydajności lub w niektórych przypadkach nawet strat wydajności (z powodu zwiększonego stronicowania większego pliku wykonywalnego, na przykład).

Korzystanie z funkcji wbudowanych może przyspieszyć pracę programu, ponieważ eliminuje obciążenie związane z wywołaniami funkcji. Wbudowane funkcje functions podlegają optymalizacji kodu, które nie są dostępne dla normalnych funkcji.

Kompilator traktuje wbudowane opcje rozwijania i słowa kluczowe jako sugestie. Nie ma gwarancji, że funkcje są wbudowane. Nie można wymusić wbudowania określonej funkcji przez kompilator, nawet ze słowem kluczowym **__forceinline** . Podczas kompilowania z **/CLR**kompilator nie będzie wbudowana funkcji, jeśli istnieją atrybuty zabezpieczeń zastosowane do funkcji.

**Wbudowane** słowo kluczowe jest dostępne tylko w C++. Słowa kluczowe **__inline** i **__forceinline** są dostępne zarówno w języku C C++, jak i. W celu zapewnienia zgodności z poprzednimi wersjami **_inline** i **_forceinline** są synonimami dla **__inline**i **__forceinline** , chyba że opcja kompilatora [/za \(Disable Language Extensions)](../build/reference/za-ze-disable-language-extensions.md) jest określona.

**Wbudowane** słowo kluczowe informuje kompilator, że jest preferowane rozwijanie wbudowane. Jednak kompilator może utworzyć oddzielne wystąpienie funkcji (instancji) i utworzyć standardowe powiązania wywołań zamiast wstawiania kodu wbudowanego. Dwa przypadki, w których może się to zdarzyć:

- Funkcje cykliczne.

- Funkcje, które są określane za pomocą wskaźnika w innym miejscu w jednostce translacji.

Te przyczyny mogą zakłócać tworzenie, jak to *inne*, od uznania kompilatora; nie należy zależeć od specyfikatora wbudowanego, aby spowodować, że funkcja jest **wbudowana** .

Podobnie jak w przypadku normalnych funkcji, nie ma zdefiniowanej kolejności oceny argumentów dla funkcji wbudowanej. W rzeczywistości może się to różnić od kolejności, w której argumenty są oceniane podczas przekazywania przy użyciu standardowego protokołu wywołania funkcji.

Opcja optymalizacji kompilatora [/ob](../build/reference/ob-inline-function-expansion.md) pomaga ustalić, czy w rzeczywistości występuje rozwijanie funkcji wbudowanej.

[/LTCG](../build/reference/ltcg-link-time-code-generation.md) wykonuje wielomodułowe odwołanie, niezależnie od tego, czy zażądano go w kodzie źródłowym.

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

Funkcje składowe klasy mogą być deklarowane jako wbudowane przy użyciu **wbudowanego** słowa kluczowego lub przez umieszczenie definicji funkcji w definicji klasy.

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

**Microsoft Specific**

Słowo kluczowe **__inline** jest równoważne **wbudowanej**.

Nawet w przypadku **__forceinline**, kompilator nie może w żaden sposób zakodować kodu. Kompilator nie może wbudowana funkcji, jeśli:

- Funkcja lub jej obiekt wywołujący jest kompilowany z/Ob0 (opcja domyślna dla kompilacji debugowania).

- Funkcja i obiekt wywołujący używają różnych typów obsługi wyjątków (C++ obsługa wyjątków w jednej, strukturalnej obsłudze wyjątków w innych).

- Funkcja ma listę zmiennych argumentów.

- Funkcja używa wbudowanego zestawu, chyba że jest kompilowany z/og,/OX,/O1 lub/O2.

- Funkcja jest cykliczna i nie towarzyszy **inline_recursion #pragma (włączone)** . W przypadku dyrektywy pragma funkcje cykliczne są wbudowane w domyślną głębokość wynoszącą 16 wywołań. Aby zmniejszyć głębokość wyznaczania, użyj dyrektywy pragma [inline_depth](../preprocessor/inline-depth.md) .

- Funkcja jest wirtualna i jest wywoływana praktycznie. Bezpośrednie wywołania funkcji wirtualnych mogą być wbudowane.

- Program pobiera adres funkcji, a wywołanie jest nawiązywane za pośrednictwem wskaźnika do funkcji. Bezpośrednie wywołania do funkcji, które miały swój adres, mogą być umieszczone w wierszu.

- Funkcja jest również [oznaczona przy użyciu](../cpp/naked-cpp.md) modyfikatora " [__declspeca](../cpp/declspec.md) ".

Jeśli kompilator nie może wbudowana funkcji zadeklarowanej za pomocą **__forceinline**, generuje ostrzeżenie poziomu 1, z wyjątkiem sytuacji, gdy:

- Funkcja jest skompilowana przy użyciu/od lub/Ob0. W takich przypadkach nie jest oczekiwany sposób wykreślania.

- Funkcja jest zdefiniowana zewnętrznie, w dołączonej bibliotece lub innej jednostce tłumaczenia albo jest obiektem docelowym wywołania wirtualnego lub obiektem docelowym wywołania pośredniego. Kompilator nie może zidentyfikować kodu nieliniowego, którego nie można znaleźć w bieżącej jednostce tłumaczenia.

Funkcje cykliczne mogą zostać zastąpione w wierszu do głębokości określonej przez [inline_depth](../preprocessor/inline-depth.md) pragma, do maksymalnie 16 wywołań. Po tej głębokości wywołania funkcji cyklicznej są traktowane jako wywołania do wystąpienia funkcji.  Głębokość, do której funkcje cykliczne są badane przez wbudowany algorytm heurystyczny, nie może przekraczać 16. [Inline_recursion](../preprocessor/inline-recursion.md) pragma kontroluje wbudowane rozwijanie funkcji obecnie w obszarze rozszerzanie. Aby uzyskać powiązane [informacje, zobacz](../build/reference/ob-inline-function-expansion.md) opcję kompilatora (/ob).

**ZAKOŃCZENIE określonych przez firmę Microsoft**

Aby uzyskać więcej informacji na temat używania specyfikatora **wbudowanego** , zobacz:

- [Funkcje składowe klasy wbudowanej](../cpp/inline-functions-cpp.md)

- [Definiowanie funkcji śródwierszowych języka C++ z dllexport i dllimport](../cpp/defining-inline-cpp-functions-with-dllexport-and-dllimport.md)

## <a name="when-to-use-inline-functions"></a>Kiedy używać funkcji wbudowanych

Funkcje śródwierszowe najlepiej używać w przypadku małych funkcji, takich jak dostęp do prywatnych elementów członkowskich danych. Głównym celem tych funkcji "akcesora" o jednej lub dwóch wierszach jest zwrócenie informacji o stanie dotyczących obiektów; krótkie funkcje są wrażliwe na obciążenie wywołań funkcji. Więcej funkcji poświęca proporcjonalnie krótszy czas w sekwencji wywołującej/zwracającej i czerpie korzyści z wykreślania.

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

Przy założeniu, że manipulacja koordynuje jest relatywnie powszechną operacją klienta takiej klasy, określając dwie funkcje metody dostępu (`x` i `y` w poprzednim przykładzie), ponieważ metoda **wbudowana** zwykle oszczędza obciążenie:

- Wywołania funkcji (łącznie z przekazywaniem parametrów i umieszczaniem adresu obiektu na stosie)

- Zachowywanie ramki stosu obiektu wywołującego

- Nowa konfiguracja ramki stosu

- Komunikacja zwrotna z wartością

- Stary stos — przywracanie ramki

- Zwrot

## <a name="inline-functions-vs-macros"></a>Funkcje wbudowane a makra

Chociaż funkcje wbudowane są podobne do makr (ponieważ kod funkcji jest rozwinięty w punkcie wywołania w czasie kompilacji), funkcje wbudowane są analizowane przez kompilator, a makra są rozszerzane przez preprocesor. W związku z tym istnieje kilka istotnych różnic:

- Wbudowane funkcje przestrzegają wszystkich protokołów bezpieczeństwa typów wymuszanych w normalnych funkcjach.

- Funkcje wbudowane są określane przy użyciu tej samej składni co inna funkcja, z tą różnicą, że zawierają słowo kluczowe **wbudowane** w deklaracji funkcji.

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

Celem wyrażenia `toupper(getc(stdin))` jest to, że znak powinien być odczytany z urządzenia konsoli (`stdin`) i, w razie potrzeby, konwertowany na wielkie litery.

Ze względu na implementację makra `getc` jest wykonywane raz, aby określić, czy znak jest większy niż lub równy "a", i raz, aby określić, czy jest on mniejszy niż lub równy "z". Jeśli znajduje się w tym zakresie, `getc` jest wykonywane ponownie w celu przekonwertowania znaku na wielkie litery. Oznacza to, że program czeka na dwa lub trzy znaki, w idealnym przypadku, powinien czekać tylko jeden.

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

[noinline](../cpp/noinline.md)<br/>
[auto_inline](../preprocessor/auto-inline.md)