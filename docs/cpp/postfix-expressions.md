---
title: Wyrażenia przyrostków
ms.date: 11/04/2016
helpviewer_keywords:
- operators [C++], postfix
- postfix expressions
- expressions [C++], postfix
ms.assetid: 7ac62a57-06df-422f-b012-a75b37d7cb9b
ms.openlocfilehash: eb6e6e8914cf260df09581232066caf3f873c04e
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58779264"
---
# <a name="postfix-expressions"></a>Wyrażenia przyrostków

Wyrażenia przyrostkowe składają się z podstawowego wyrażenia lub wyrażeń, w których operatory przyrostkowe następują po wyrażeniu podstawowym. Operatory przyrostkowe są wymienione w poniższej tabeli.

### <a name="postfix-operators"></a>Operatory przyrostka

|Nazwa operatora|Notacja operatora|
|-------------------|-----------------------|
|[Operator indeksu dolnego](../cpp/subscript-operator.md)|**[ ]**|
|[Operator wywołania funkcji](../cpp/function-call-operator-parens.md)|**( )**|
|[Operator jawnej konwersji typu](../cpp/explicit-type-conversion-operator-parens.md)|*Nazwa typu* **)**|
|[Operator dostępu do elementu członkowskiego](../cpp/member-access-operators-dot-and.md)|**.** lub **->**|
|[Operator inkrementacji przyrostkowej](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md)|**++**|
|[Operator dekrementacji przyrostkowej](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md)|**--**|

Następująca składnia opisuje możliwe wyrażenia przyrostkowe:

```
primary-expression
postfix-expression[expression]postfix-expression(expression-list)simple-type-name(expression-list)postfix-expression.namepostfix-expression->namepostfix-expression++postfix-expression--cast-keyword < typename > (expression )typeid ( typename )
```

*Wyrażeniem przyrostkowym* powyżej może być wyrażeniem podstawowym lub innym wyrażeniem przyrostkowym.  Zobacz **wyrażenia podstawowe**.  Grupa wyrażeń przyrostkowych od lewej do prawej, umożliwia w ten sposób łączenie wyrażeń w następujący sposób:

```cpp
func(1)->GetValue()++
```

W powyższym wyrażeniu `func` jest wyrażeniem podstawowym `func(1)` jest wyrażeniem przyrostkowym funkcji `func(1)->GetValue` jest wyrażeniem przyrostkowym składowej klasy, `func(1)->GetValue()` jest innym wyrażeniem przyrostkowym funkcji, a cały wyrażenie jest wyrażeniem przyrostkowym, zwiększającym wartość elementu GetValue.  Znaczenie wyrażenia jako całości to „wywołaj funkcję przekazywania 1 jako argument i uzyskaj wskaźnik do klasy jako wartość zwracaną.  Następnie wywołaj `GetValue()` dla tej klasy, a następnie zwiększ wartość zwracaną.

Wyrażenia wymienione powyżej są wyrażeniami przypisania, co oznacza, że wyniki wyrażenia muszą być r-wartościami.

Forma wyrażenia przyrostkowego

```cpp
simple-type-name ( expression-list )
```

wskazuje wywołanie konstruktora.  Jeśli simple-type-name jest typem podstawowym, lista wyrażeń musi być wyrażeniem pojedynczym, a to wyrażenie wskazuje rzutowanie wartości wyrażenia na typ podstawowy.  Ten typ wyrażenia rzutującego naśladuje konstruktor.  Jako że ta forma umożliwia konstruowanie podstawowych typów i klas przy użyciu tej samej składni, ta forma jest szczególnie przydatna podczas definiowania klas szablonów.

*Cast-keyword* jest jednym z **dynamic_cast**, **static_cast** lub **reinterpret_cast**.  Więcej informacji można znaleźć w **dynamic_cast**, **static_cast** i **reinterpet_cast**.

**Typeid** operator jest uważany za wyrażenie przyrostkowe.  Zobacz **typeid operator**.

## <a name="formal-and-actual-arguments"></a>Argumenty formalne i rzeczywiste

Wywoływanie programów przekazuje informacje do wywołanych funkcji w „bieżących argumentach”. Wywołane funkcje mają dostęp do informacji za pomocą odpowiadających im „argumentów formalnych”.

Po wywołaniu funkcji, wykonywane są następujące zadania:

- Wszystkie rzeczywiste argumenty (dostarczane przez wywołującego) są obliczane. Nie ma niejawnego porządku, w którym argumenty są obliczane, ale wszystkie argumenty są obliczone i wszystkie efekty uboczne zakończone przed wejściem do funkcji.

- Każdy argument formalny jest inicjowany z odpowiadającym mu argumentem rzeczywistym na liście wyrażeń. (Argument formalny to argument, który jest zadeklarowany w nagłówku funkcji i używany w treści funkcji). Operacje są wykonywane jakby przez inicjowanie — konwersje standardowe i zdefiniowane przez użytkownika są wykonywane w konwersji rzeczywistego argumentu do poprawnego typu. Wykonywane inicjowanie zostało koncepcyjnie zilustrowane przez następujący kod:

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

   W związku z tym jeśli prototyp funkcji (deklaracja) wymaga argumentu typu **długie**, a jeśli program wywołujący dostarcza rzeczywisty argument typu **int**, rzeczywisty argument jest podnoszony za pomocą Konwersja standardowa typu na typ **długie** (zobacz [konwersje standardowe](../cpp/standard-conversions.md)).

   Błędem jest podawanie rzeczywistego argumentu, dla którego nie ma żadnych standardowych lub zdefiniowanych przez użytkownika konwersji do typu argumentu formalnego.

   Dla rzeczywistych argumentów typu klasy, argument formalny jest inicjowany przez wywołanie konstruktora klasy. (Zobacz [konstruktory](../cpp/constructors-cpp.md) więcej informacji na temat tych funkcji składowych klas specjalnych.)

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

Gdy `func` jest wywoływana z main, parametr formalny `param1` jest inicjowany z wartością `i` (`i` jest konwertowany na typ **długie** odpowiadać poprawnego typu przy użyciu standardowego Konwersja) i parametru formalnego `param2` jest inicjowany z wartością `j` (`j` jest konwertowany na typ **double** za pomocą konwersji standardowej).

## <a name="treatment-of-argument-types"></a>Traktowanie typów argumentu

Argumenty formalne zadeklarowane jako typy stałe, nie można zmienić w treści funkcji. Funkcje można zmienić którykolwiek z argumentów ma typ inny niż **const**. Jednak zmiana jest lokalny dla funkcji i nie wpływa wartość rzeczywistego argumentu, chyba że rzeczywisty argument jest odwołaniem do obiektu nie jest typu **const**.

Następujące funkcje przedstawiają niektóre z tych pojęć:

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

Funkcje mogą być zadeklarowane do akceptowania mniej argumentów niż określono w definicji funkcji przy użyciu jednej z dwóch metod: wielokropka (`...`) lub domyślnych argumentów.

Elipsy oznaczają, że argumenty mogą być wymagane, ale że liczba i typy nie są określone w deklaracji. Jest to zwykle niska praktyka programowania C++, ponieważ unieważnia jedną z zalet języka C++: bezpieczeństwo typów. Różne konwersje są stosowane do funkcji zadeklarowanych z wielokropkiem niż te funkcje, dla których są znane typy argumentów formalne i rzeczywiste:

- Jeżeli rzeczywisty argument jest typu **float**, jest promowany do typu **double** przed wywołaniem funkcji.

- Wszystkie podpisane lub niepodpisane **char**, **krótki**, typ wyliczeniowy lub pole bitowe są konwertowane na podpisane lub niepodpisane **int** za pomocą promocji integralnej.

- Każdy argument dla typu klasy jest przekazywany przez wartość jako struktura danych; Kopia zostanie utworzona przez skopiowanie binarne zamiast przez wywołanie konstruktora kopiowania klasy (jeśli istnieje).

Elipsy, jeśli używane, muszą być zagwarantowane ostatnio na liście argumentów. Aby uzyskać więcej informacji o przekazywaniu zmienną liczbę argumentów, zobacz Omówienie [va_arg, va_start i va_list](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md) w *odwołanie do biblioteki wykonawczej*.

Aby uzyskać informacje o domyślnych argumentach w programowaniu CLR, zobacz [zmiennej listy argumentów (...) (C + +/ CLI) ](../extensions/variable-argument-lists-dot-dot-dot-cpp-cli.md).

Argumenty domyślne umożliwiają określenie wartości, które argument założyć, że jeśli nie zostanie podana w wywołaniu funkcji. Poniższy fragment kodu pokazuje, jak działają argumenty domyślne. Aby uzyskać więcej informacji na temat ograniczeń w określaniu domyślnych argumentów, zobacz [argumenty domyślne](../cpp/default-arguments.md).

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

Poprzedni program deklaruje funkcję, `print`, która przyjmuje dwa argumenty. Jednakże drugi argument *terminator*, ma wartość domyślną `"\n"`. W `main`, dwa pierwsze wywołania `print` Zezwalaj domyślnemu drugiemu argumentowi dostarczyć nowy wiersz, aby zakończyć drukowany ciąg. Trzecie wywołanie określa wartość dla drugiego argumentu. Dane wyjściowe z programu

```Output
hello,
world!
good morning, sunshine.
```

## <a name="see-also"></a>Zobacz także

[Typy wyrażeń](../cpp/types-of-expressions.md)