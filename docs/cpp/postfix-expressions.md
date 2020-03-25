---
title: Wyrażenia przyrostków
ms.date: 11/04/2016
helpviewer_keywords:
- operators [C++], postfix
- postfix expressions
- expressions [C++], postfix
ms.assetid: 7ac62a57-06df-422f-b012-a75b37d7cb9b
ms.openlocfilehash: 25dfc6fd8f28f6c78fd5a4e9f76759ac076cae1b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80177693"
---
# <a name="postfix-expressions"></a>Wyrażenia przyrostków

Wyrażenia przyrostkowe składają się z podstawowego wyrażenia lub wyrażeń, w których operatory przyrostkowe następują po wyrażeniu podstawowym. Operatory przyrostkowe są wymienione w poniższej tabeli.

### <a name="postfix-operators"></a>Operatory przyrostka

|Nazwa operatora|Notacja operatora|
|-------------------|-----------------------|
|[Operator indeksu dolnego](../cpp/subscript-operator.md)|**[ ]**|
|[Operator wywołania funkcji](../cpp/function-call-operator-parens.md)|**( )**|
|[Operator jawnej konwersji typu](../cpp/explicit-type-conversion-operator-parens.md)|*type-name* **()**|
|[Operator dostępu do elementów członkowskich](../cpp/member-access-operators-dot-and.md)|**.** lub **->**|
|[Przyrostkowy operator przyrostu](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md)|**++**|
|[Operator zmniejszania przyrostu](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md)|**--**|

Następująca składnia opisuje możliwe wyrażenia przyrostkowe:

```
primary-expression
postfix-expression[expression]postfix-expression(expression-list)simple-type-name(expression-list)postfix-expression.namepostfix-expression->namepostfix-expression++postfix-expression--cast-keyword < typename > (expression )typeid ( typename )
```

*Wyrażenie przyrostkowe* powyżej może być wyrażeniem podstawowym lub innym wyrażeniem przyrostkowym.  Zobacz **wyrażenia podstawowe**.  Grupa wyrażeń przyrostkowych od lewej do prawej, umożliwia w ten sposób łączenie wyrażeń w następujący sposób:

```cpp
func(1)->GetValue()++
```

W powyższym wyrażeniu `func` jest wyrażeniem podstawowym, `func(1)` jest wyrażeniem przyrostkowym funkcji, `func(1)->GetValue` jest wyrażeniem przyrostkowym określającym składową klasy, `func(1)->GetValue()` jest innym wyrażeniem przyrostkowym funkcji, a całe wyrażenie jest wyrażeniem przyrostkowym zwiększającym wartość zwracaną GetValue.  Znaczenie wyrażenia jako całości to „wywołaj funkcję przekazywania 1 jako argument i uzyskaj wskaźnik do klasy jako wartość zwracaną.  Następnie Wywołaj `GetValue()` tej klasy, a następnie zwiększ wartość zwracanej wartości.

Wyrażenia wymienione powyżej są wyrażeniami przypisania, co oznacza, że wyniki wyrażenia muszą być r-wartościami.

Forma wyrażenia przyrostkowego

```cpp
simple-type-name ( expression-list )
```

wskazuje wywołanie konstruktora.  Jeśli simple-type-name jest typem podstawowym, lista wyrażeń musi być wyrażeniem pojedynczym, a to wyrażenie wskazuje rzutowanie wartości wyrażenia na typ podstawowy.  Ten typ wyrażenia rzutującego naśladuje konstruktor.  Jako że ta forma umożliwia konstruowanie podstawowych typów i klas przy użyciu tej samej składni, ta forma jest szczególnie przydatna podczas definiowania klas szablonów.

*Słowo kluczowe Cast* to jeden z **dynamic_cast**, **static_cast** lub **reinterpret_cast**.  Więcej informacji można znaleźć w **dynamic_cast**, **static_cast** i **reinterpet_cast**.

Operator **typeid** jest traktowany jako wyrażenie przyrostkowe.  Zobacz **Operator typeid**.

## <a name="formal-and-actual-arguments"></a>Argumenty formalne i rzeczywiste

Wywoływanie programów przekazuje informacje do wywołanych funkcji w „bieżących argumentach”. Wywołane funkcje mają dostęp do informacji za pomocą odpowiadających im „argumentów formalnych”.

Po wywołaniu funkcji, wykonywane są następujące zadania:

- Wszystkie rzeczywiste argumenty (dostarczane przez wywołującego) są obliczane. Nie ma niejawnego porządku, w którym argumenty są obliczane, ale wszystkie argumenty są obliczone i wszystkie efekty uboczne zakończone przed wejściem do funkcji.

- Każdy argument formalny jest inicjowany z odpowiadającym mu argumentem rzeczywistym na liście wyrażeń. (Formalny argument jest argumentem zadeklarowanym w nagłówku funkcji i używanym w treści funkcji). Konwersje są wykonywane tak jak w przypadku inicjalizacji — zarówno Konwersje standardowe, jak i zdefiniowane przez użytkownika są wykonywane w wyniku konwersji rzeczywistego argumentu na poprawny typ. Wykonywane inicjowanie zostało koncepcyjnie zilustrowane przez następujący kod:

    ```cpp
    void Func( int i ); // Function prototype
    ...
    Func( 7 );          // Execute function call
    ```

   Koncepcyjne inicjalizacje przed wywołaniem to:

    ```cpp
    int Temp_i = 7;
    Func( Temp_i );
    ```

   Należy zauważyć, że inicjalizacja jest wykonywana jakby przy użyciu składni znaku równości zamiast składni nawiasów. Kopia `i` została utworzona przed przekazaniem wartości do funkcji. (Aby uzyskać więcej informacji, zobacz [inicjatory](../cpp/initializers.md) i [konwersje](../cpp/user-defined-type-conversions-cpp.md)).

   W związku z tym, jeśli prototyp funkcji (Deklaracja) wywołuje argument typu **Long**i jeśli program wywołujący dostarcza rzeczywisty argument typu **int**, rzeczywisty argument zostanie podwyższony przy użyciu standardowej konwersji typu do typu **Long** (zobacz [Konwersje standardowe](../cpp/standard-conversions.md)).

   Błędem jest podawanie rzeczywistego argumentu, dla którego nie ma żadnych standardowych lub zdefiniowanych przez użytkownika konwersji do typu argumentu formalnego.

   Dla rzeczywistych argumentów typu klasy, argument formalny jest inicjowany przez wywołanie konstruktora klasy. (Zobacz [konstruktory](../cpp/constructors-cpp.md) , aby uzyskać więcej informacji na temat tych specjalnych funkcji składowych klasy).

- Wywołanie funkcji jest wykonywane.

Poniższy fragment programu demonstruje wywołanie funkcji:

```cpp
// expre_Formal_and_Actual_Arguments.cpp
void func( long param1, double param2 );

int main()
{
    long i = 1;
    double j = 2;

    // Call func with actual arguments i and j.
    func( i, j );
}

// Define func with formal parameters param1 and param2.
void func( long param1, double param2 )
{
}
```

Gdy `func` jest wywoływana z poziomu Main, formalny parametr `param1` zostanie zainicjowany z wartością `i` (`i` jest konwertowana na typ **Long** , aby odpowiadała poprawnym typowi przy użyciu konwersji standardowej), a formalny parametr `param2` jest inicjowany z wartością `j` (`j` jest konwertowany na typ **Double** przy użyciu konwersji standardowej).

## <a name="treatment-of-argument-types"></a>Traktowanie typów argumentów

Nie można zmienić formalnych argumentów zadeklarowanych jako typy stałe w treści funkcji. Funkcje mogą zmieniać dowolny argument, który nie jest typu **const**. Jednak zmiana jest lokalna dla funkcji i nie ma wpływu na wartość rzeczywistego argumentu, chyba że rzeczywisty argument był odwołaniem do obiektu, który nie jest typu **const**.

Następujące funkcje ilustrują niektóre z tych koncepcji:

```cpp
// expre_Treatment_of_Argument_Types.cpp
int func1( const int i, int j, char *c ) {
   i = 7;   // C3892 i is const.
   j = i;   // value of j is lost at return
   *c = 'a' + j;   // changes value of c in calling function
   return i;
}

double& func2( double& d, const char *c ) {
   d = 14.387;   // changes value of d in calling function.
   *c = 'a';   // C3892 c is a pointer to a const object.
    return d;
}
```

## <a name="ellipses-and-default-arguments"></a>Wielokropki i argumenty domyślne

Funkcje mogą być deklarowane w celu akceptowania mniejszej liczby argumentów niż określono w definicji funkcji, przy użyciu jednej z dwóch metod: wielokropka (`...`) lub domyślnych argumentów.

Wielokropki oznacza, że argumenty mogą być wymagane, ale liczba i typy nie są określone w deklaracji. Jest to zwykle słabe C++ rozwiązanie programistyczne, ponieważ zakłóca jedną z zalet C++: bezpieczeństwo typu. Różne konwersje są stosowane do funkcji zadeklarowanych za pomocą elipsy niż do tych funkcji, dla których znane są typy argumentów formalnych i rzeczywistych:

- Jeśli rzeczywisty argument jest typu **zmiennoprzecinkowego**, zostanie podwyższony do typu **Double** przed wywołaniem funkcji.

- Wszystkie podpisane lub niepodpisane pola **char**, **Short**, wyliczeniowy typ lub bit są konwertowane na podpisaną lub niepodpisane **int** przy użyciu promocji całkowitej.

- Każdy argument typu klasy jest przenoszona przez wartość jako strukturę danych; kopia jest tworzona przez kopiowanie binarne zamiast wywoływania konstruktora kopiującego klasy (jeśli taki istnieje).

Elipsy, jeśli są używane, muszą być zadeklarowane jako ostatnie na liście argumentów. Aby uzyskać więcej informacji na temat przekazywania zmiennej liczby argumentów, zobacz Omówienie [va_arg, va_start i va_list](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md) w *dokumentacji dotyczącej biblioteki wykonawczej*.

Aby uzyskać informacje na temat argumentów domyślnych w programowaniu środowiska CLR, zobacz [listy zmiennych argumentów (..C++.) (/CLI)](../extensions/variable-argument-lists-dot-dot-dot-cpp-cli.md).

Argumenty domyślne umożliwiają określenie wartości argumentu, który ma zostać przyjęty, jeśli nie jest podany w wywołaniu funkcji. Poniższy fragment kodu pokazuje, jak działają argumenty domyślne. Aby uzyskać więcej informacji na temat ograniczeń dotyczących określania argumentów domyślnych, zobacz [argumenty domyślne](../cpp/default-arguments.md).

```cpp
// expre_Ellipses_and_Default_Arguments.cpp
// compile with: /EHsc
#include <iostream>

// Declare the function print that prints a string,
// then a terminator.
void print( const char *string,
            const char *terminator = "\n" );

int main()
{
    print( "hello," );
    print( "world!" );

    print( "good morning", ", " );
    print( "sunshine." );
}

using namespace std;
// Define print.
void print( const char *string, const char *terminator )
{
    if( string != NULL )
        cout << string;

    if( terminator != NULL )
        cout << terminator;
}
```

Poprzedni program deklaruje funkcję, `print`, która przyjmuje dwa argumenty. Jednak drugi argument, *terminator*ma wartość domyślną, `"\n"`. W `main`pierwsze dwa wywołania do `print` umożliwiają użycie przez drugi argument domyślny, aby zakończyć wydrukowany ciąg. Trzecie wywołanie określa wartość jawną dla drugiego argumentu. Dane wyjściowe programu są

```Output
hello,
world!
good morning, sunshine.
```

## <a name="see-also"></a>Zobacz też

[Typy wyrażeń](../cpp/types-of-expressions.md)
