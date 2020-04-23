---
title: Wyrażenia przyrostków
ms.date: 11/04/2016
helpviewer_keywords:
- operators [C++], postfix
- postfix expressions
- expressions [C++], postfix
ms.assetid: 7ac62a57-06df-422f-b012-a75b37d7cb9b
ms.openlocfilehash: 897eb80c713f786ecf0f7e6c9cf24cd8bdfc0aa8
ms.sourcegitcommit: 89d9e1cb08fa872483d1cde98bc2a7c870e505e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "82032281"
---
# <a name="postfix-expressions"></a>Wyrażenia przyrostków

Wyrażenia przyrostkowe składają się z podstawowego wyrażenia lub wyrażeń, w których operatory przyrostkowe następują po wyrażeniu podstawowym. Operatory przyrostkowe są wymienione w poniższej tabeli.

### <a name="postfix-operators"></a>Operatory przyrostka

|Nazwa operatora|Notacja operatora|
|-------------------|-----------------------|
|[Operator indeksu dolnego](../cpp/subscript-operator.md)|**[ ]**|
|[Operator wywołania funkcji](../cpp/function-call-operator-parens.md)|**( )**|
|[Jawny operator konwersji typu](../cpp/explicit-type-conversion-operator-parens.md)|*nazwa typu* **( )**|
|[Operator dostępu do członków](../cpp/member-access-operators-dot-and.md)|**.** Lub**->**|
|[Operator inkrementacji przyrostkowej](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md)|**++**|
|[Operator dekrementacji przyrostkowej](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md)|**--**|

Następująca składnia opisuje możliwe wyrażenia przyrostkowe:

```
primary-expression
postfix-expression[expression]postfix-expression(expression-list)simple-type-name(expression-list)postfix-expression.namepostfix-expression->namepostfix-expression++postfix-expression--cast-keyword < typename > (expression )typeid ( typename )
```

*Powyższe wyrażenie postfix* może być wyrażeniem podstawowym lub innym wyrażeniem postfix.  Zobacz **wyrażenia podstawowe**.  Grupa wyrażeń przyrostkowych od lewej do prawej, umożliwia w ten sposób łączenie wyrażeń w następujący sposób:

```cpp
func(1)->GetValue()++
```

W powyższym `func` wyrażeniu `func(1)` jest wyrażeniem podstawowym, `func(1)->GetValue` jest wyrażeniem postfix funkcji, jest `func(1)->GetValue()` wyrażeniem postfix określającym element członkowski klasy, jest innym wyrażeniem postfix, a całe wyrażenie jest wyrażeniem postfix, które zwiększa wartość zwracaną GetValue.  Znaczenie wyrażenia jako całości to „wywołaj funkcję przekazywania 1 jako argument i uzyskaj wskaźnik do klasy jako wartość zwracaną.  Następnie `GetValue()` wywołać tę klasę, a następnie przyrost zwracaną wartość.

Wyrażenia wymienione powyżej są wyrażeniami przypisania, co oznacza, że wyniki wyrażenia muszą być r-wartościami.

Forma wyrażenia przyrostkowego

```cpp
simple-type-name ( expression-list )
```

wskazuje wywołanie konstruktora.  Jeśli simple-type-name jest typem podstawowym, lista wyrażeń musi być wyrażeniem pojedynczym, a to wyrażenie wskazuje rzutowanie wartości wyrażenia na typ podstawowy.  Ten typ wyrażenia rzutującego naśladuje konstruktor.  Jako że ta forma umożliwia konstruowanie podstawowych typów i klas przy użyciu tej samej składni, ta forma jest szczególnie przydatna podczas definiowania klas szablonów.

*Cast-keyword* jest jednym z **dynamic_cast,** **static_cast** lub **reinterpret_cast**.  Więcej informacji można znaleźć w **dynamic_cast,** **static_cast** i **reinterpet_cast**.

Operator **typeid** jest uważany za wyrażenie postfix.  Zobacz **operator typeid**.

## <a name="formal-and-actual-arguments"></a>Argumenty formalne i rzeczywiste

Wywoływanie programów przekazuje informacje do wywołanych funkcji w „bieżących argumentach”. Wywołane funkcje mają dostęp do informacji za pomocą odpowiadających im „argumentów formalnych”.

Po wywołaniu funkcji, wykonywane są następujące zadania:

- Wszystkie rzeczywiste argumenty (dostarczane przez wywołującego) są obliczane. Nie ma niejawnego porządku, w którym argumenty są obliczane, ale wszystkie argumenty są obliczone i wszystkie efekty uboczne zakończone przed wejściem do funkcji.

- Każdy argument formalny jest inicjowany z odpowiadającym mu argumentem rzeczywistym na liście wyrażeń. (Argument formalny jest argumentem, który jest zadeklarowany w nagłówku funkcji i używany w treści funkcji.) Konwersje są wykonywane tak, jakby przez inicjowanie — zarówno konwersje standardowe, jak i zdefiniowane przez użytkownika są wykonywane podczas konwertowania rzeczywistego argumentu na poprawny typ. Wykonywane inicjowanie zostało koncepcyjnie zilustrowane przez następujący kod:

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

   Należy zauważyć, że inicjalizacja jest wykonywana jakby przy użyciu składni znaku równości zamiast składni nawiasów. Kopia `i` została utworzona przed przekazaniem wartości do funkcji. (Aby uzyskać więcej informacji, zobacz [Inicjatory](../cpp/initializers.md) i [konwersje](../cpp/user-defined-type-conversions-cpp.md)).

   W związku z tym, jeśli prototyp funkcji (deklaracja) wymaga argumentu typu **long**, a program wywołujący dostarcza rzeczywisty argument typu **int,** rzeczywisty argument jest promowany przy użyciu konwersji typu standardowego na typ **długi** (patrz [Konwersje standardowe](../cpp/standard-conversions.md)).

   Błędem jest podawanie rzeczywistego argumentu, dla którego nie ma żadnych standardowych lub zdefiniowanych przez użytkownika konwersji do typu argumentu formalnego.

   Dla rzeczywistych argumentów typu klasy, argument formalny jest inicjowany przez wywołanie konstruktora klasy. (Zobacz [konstruktorów,](../cpp/constructors-cpp.md) aby uzyskać więcej informacji na temat tych funkcji elementów członkowskich klasy specjalnej.)

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

Gdy `func` jest wywoływana z `param1` głównego, parametr formalny `i` `i` jest inicjowany z wartością ( jest konwertowany `param2` na typ **long,** aby odpowiadać poprawnemu typowi przy użyciu standardowej konwersji), a parametr formalny jest inicjowany z wartością `j` (`j` jest konwertowany na typ **double** przy użyciu standardowej konwersji).

## <a name="treatment-of-argument-types"></a>Traktowanie typów argumentów

Formalne argumenty zadeklarowane jako typy const nie można zmienić w treści funkcji. Funkcje mogą zmieniać dowolny argument, który nie jest **typu const**. Jednak zmiana jest lokalna dla funkcji i nie wpływa na rzeczywistą wartość argumentu, chyba że rzeczywisty argument był odwołaniem do obiektu nie typu **const**.

Następujące funkcje ilustrują niektóre z tych pojęć:

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

## <a name="ellipsis-and-default-arguments"></a>Wielokropek i argumenty domyślne

Funkcje można zadeklarować, aby akceptować mniej argumentów niż określono w`...`definicji funkcji, przy użyciu jednej z dwóch metod: wielokropek ( ) lub argumentów domyślnych.

Wielokropek oznacza, że argumenty mogą być wymagane, ale że liczba i typy nie są określone w deklaracji. Jest to zwykle słaba praktyka programowania Języka C++, ponieważ pokonuje jedną z zalet języka C++: bezpieczeństwo typu. Różne konwersje są stosowane do funkcji zadeklarowanych za pomocą wielokropek niż do tych funkcji, dla których znane są typy argumentów formalnych i rzeczywistych:

- Jeśli rzeczywisty argument jest **typu float**, jest promowany do typu **double** przed wywołaniem funkcji.

- Każdy podpisany lub niepodpisany **znak,** **krótki,** wyliczony typ lub pole bitowe jest konwertowany na podpisane lub niepodpisane **int** przy użyciu integralnej promocji.

- Każdy argument typu klasy jest przekazywany przez wartość jako strukturę danych; kopia jest tworzona przez kopiowanie binarne, a nie przez wywołanie konstruktora kopii klasy (jeśli istnieje).

Wielokropek, jeśli jest używany, musi być zadeklarowany jako ostatni na liście argumentów. Aby uzyskać więcej informacji na temat przekazywania zmiennej liczby argumentów, zobacz omówienie [va_arg, va_start i va_list](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md) w *odwołaniu do biblioteki w czasie wykonywania*.

Aby uzyskać informacje na temat argumentów domyślnych w programowaniu CLR, zobacz [Listy argumentów zmiennych (...) (C++/CLI)](../extensions/variable-argument-lists-dot-dot-dot-cpp-cli.md).

Domyślne argumenty umożliwiają określenie wartości, którą argument powinien przyjąć, jeśli żaden z nich nie jest podany w wywołaniu funkcji. Poniższy fragment kodu pokazuje, jak działają domyślne argumenty. Aby uzyskać więcej informacji na temat ograniczeń określania argumentów domyślnych, zobacz [Argumenty domyślne](../cpp/default-arguments.md).

```cpp
// expre_Ellipsis_and_Default_Arguments.cpp
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

Poprzedni program deklaruje funkcję, `print`czyli dwa argumenty. Jednak drugi argument, *terminator*, ma `"\n"`wartość domyślną, . W `main`obszarze , pierwsze `print` dwa wywołania, aby umożliwić domyślny drugi argument do dostarczenia nowego wiersza, aby zakończyć wydrukowany ciąg. Trzecie wywołanie określa jawną wartość dla drugiego argumentu. Dane wyjściowe z programu są

```Output
hello,
world!
good morning, sunshine.
```

## <a name="see-also"></a>Zobacz też

[Typy wyrażeń](../cpp/types-of-expressions.md)
