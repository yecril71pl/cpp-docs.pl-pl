---
title: Wyrażenia przyrostków | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- operators [C++], postfix
- postfix expressions
- expressions [C++], postfix
ms.assetid: 7ac62a57-06df-422f-b012-a75b37d7cb9b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a116e4f1c937a1656f337396a8b10206e0776c0e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
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
|[Operator inkrementacji przyrostka](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md)|`++`|  
|[Operator dekrementacji przyrostka](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md)|**--**|  
  
 Następująca składnia opisuje możliwe wyrażenia przyrostkowe:  
  
```  
  
      primary-expression   
postfix-expression[expression]postfix-expression(expression-list)simple-type-name(expression-list)postfix-expression.namepostfix-expression->namepostfix-expression++postfix-expression--cast-keyword < typename > (expression )typeid ( typename )  
```  
  
 *Wyrażenie przyrostek* powyżej może być wyrażeniem podstawowego lub innego wyrażenia przyrostek.  Zobacz **wyrażenia podstawowe**.  Grupa wyrażeń przyrostkowych od lewej do prawej, umożliwia w ten sposób łączenie wyrażeń w następujący sposób:  
  
```  
func(1)->GetValue()++  
```  
  
 W powyższym wyrażeniu, func jest wyrażeniem podstawowym, func(1) jest wyrażeniem przyrostkowym funkcji, func(1)->GetData jest wyrażeniem przyrostkowym określającym składową klasy, func(1)->GetData() jest innym wyrażeniem przyrostkowym funkcji, a całe wyrażenie jest wyrażeniem przyrostkowym, zwiększającym wartość zwracaną GetData.  Znaczenie wyrażenia jako całości to „wywołaj funkcję przekazywania 1 jako argument i uzyskaj wskaźnik do klasy jako wartość zwracaną.  Następnie wywołaj GetValue() dla tej klasy i zwiększ wartość zwracaną.  
  
 Wyrażenia wymienione powyżej są wyrażeniami przypisania, co oznacza, że wyniki wyrażenia muszą być r-wartościami.  
  
 Forma wyrażenia przyrostkowego  
  
```  
simple-type-name ( expression-list )  
```  
  
 wskazuje wywołanie konstruktora.  Jeśli simple-type-name jest typem podstawowym, lista wyrażeń musi być wyrażeniem pojedynczym, a to wyrażenie wskazuje rzutowanie wartości wyrażenia na typ podstawowy.  Ten typ wyrażenia rzutującego naśladuje konstruktor.  Jako że ta forma umożliwia konstruowanie podstawowych typów i klas przy użyciu tej samej składni, ta forma jest szczególnie przydatna podczas definiowania klas szablonów.  
  
 *— Słowo kluczowe rzutowania* jest jednym z `dynamic_cast`, `static_cast` lub `reinterpret_cast`.  Więcej informacji można znaleźć w **dynamic_cast**, **static_cast** i **reinterpet_cast**.  
  
 Operator `typeid` jest uważany za wyrażenie przyrostkowe.  Zobacz **operatora typeid**.  
  
## <a name="formal-and-actual-arguments"></a>Argumenty formalne i rzeczywiste  
 Wywoływanie programów przekazuje informacje do wywołanych funkcji w „bieżących argumentach”. Wywołane funkcje mają dostęp do informacji za pomocą odpowiadających im „argumentów formalnych”.  
  
 Po wywołaniu funkcji, wykonywane są następujące zadania:  
  
-   Wszystkie rzeczywiste argumenty (dostarczane przez wywołującego) są obliczane. Nie ma niejawnego porządku, w którym argumenty są obliczane, ale wszystkie argumenty są obliczone i wszystkie efekty uboczne zakończone przed wejściem do funkcji.  
  
-   Każdy argument formalny jest inicjowany z odpowiadającym mu argumentem rzeczywistym na liście wyrażeń. (Argument formalny to argument, który jest zadeklarowany w nagłówku funkcji i używany w treści funkcji). Operacje są wykonywane jakby przez inicjowanie — konwersje standardowe i zdefiniowane przez użytkownika są wykonywane w konwersji rzeczywistego argumentu do poprawnego typu. Wykonywane inicjowanie zostało koncepcyjnie zilustrowane przez następujący kod:  
  
    ```  
    void Func( int i ); // Function prototype  
    ...  
    Func( 7 );          // Execute function call  
    ```  
  
     Koncepcyjne inicjalizacje przed wywołaniem to:  
  
    ```  
    int Temp_i = 7;  
    Func( Temp_i );  
    ```  
  
     Należy zauważyć, że inicjalizacja jest wykonywana jakby przy użyciu składni znaku równości zamiast składni nawiasów. Kopia `i` została utworzona przed przekazaniem wartości do funkcji. (Aby uzyskać więcej informacji, zobacz [inicjatory](../cpp/initializers.md) i [konwersje](../cpp/user-defined-type-conversions-cpp.md)).  
  
     W związku z tym jeśli prototypu funkcji (deklaracji) odwołuje się do argumentu typu **długi**, a jeśli program wywołujący dostarcza rzeczywiste argumentu typu `int`, rzeczywisty argument jest podwyższany, za pomocą konwersji standardowej Aby wpisać **długi** (zobacz [konwersje standardowe](../cpp/standard-conversions.md)).  
  
     Błędem jest podawanie rzeczywistego argumentu, dla którego nie ma żadnych standardowych lub zdefiniowanych przez użytkownika konwersji do typu argumentu formalnego.  
  
     Dla rzeczywistych argumentów typu klasy, argument formalny jest inicjowany przez wywołanie konstruktora klasy. (Zobacz [konstruktorów](../cpp/constructors-cpp.md) Aby uzyskać więcej informacji o tych funkcjach Członkowskich klasy specjalnej.)  
  
-   Wywołanie funkcji jest wykonywane.  
  
 Poniższy fragment programu demonstruje wywołanie funkcji:  
  
```  
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
  
 Gdy `func` jest wywoływana z głównym, formalny parametr `param1` został zainicjowany z wartością `i` (`i` jest konwertowana na typ **długi** odpowiadać poprawnego typu przy użyciu standardowego Konwersja) i parametr formalny `param2` został zainicjowany z wartością `j` (`j` jest konwertowana na typ **podwójne** za pomocą konwersji standardowej).  
  
## <a name="treatment-of-argument-types"></a>Traktowanie typów argumentu  
 Argumenty formalne deklarowane jako const typów nie można zmienić w treści funkcji. Funkcje można zmienić dowolny z argumentów nie jest typu **const**. Jednak zmiana jest lokalny dla funkcji i nie wpływa na rzeczywisty argument wartości, chyba że rzeczywisty argument jest odwołaniem do obiektu nie jest typu **const**.  
  
 Następujące funkcje zilustrować niektóre z tych pojęć:  
  
```  
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
 Funkcje mogą być deklarowane akceptować argumenty mniej niż określona w definicji funkcji, przy użyciu jednej z dwóch metod: wielokropka (`...`) lub argumenty domyślne.  
  
 Wielokropek oznaczają, że argumenty mogą być wymagane, ale że liczbę i typy nie są określone w deklaracji. Jest to zwykle niską praktyki programowania C++, ponieważ jego pozbawia jedną z zalet C++: bezpieczeństwo typu. Przekształceniami są stosowane do funkcji zadeklarowany z wielokropkiem niż do tych funkcji, które są znane typy argumentów formalne i rzeczywiste:  
  
-   Jeśli rzeczywisty argument jest typu **float**, jest podwyższany do typu **podwójne** przed wywołaniem funkcji.  
  
-   Wszystkie podpisane lub unsigned `char`, **krótki**, typ wyliczeniowy lub pola bitowego jest konwertowana na zalogowany lub niepodpisany `int` przy użyciu promocję typu całkowitego.  
  
-   Dowolny z argumentów typu klasy jest przekazywany przez wartość jako struktura danych; Kopia zostanie utworzona przez skopiowanie binarne zamiast wywołując konstruktora kopiowania klasy (jeśli istnieje).  
  
 Wielokropek, jeśli używany, musi być zadeklarowany ostatniego na liście argumentów. Aby uzyskać więcej informacji na temat przekazywanie zmienna liczba argumentów można znaleźć w omówieniu [va_arg, makra va_start i va_list](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md) w *odwołanie do biblioteki wykonawczej*.  
  
 Uzyskać informacji o domyślnych argumentów w programowaniu CLR, zobacz [zmiennej listy argumentów (...) (C + +/ CLI) ](../windows/variable-argument-lists-dot-dot-dot-cpp-cli.md).  
  
 Argumenty domyślne umożliwiają wartości argumentu powinien założyć, jeśli nie zostanie podana w wywołaniu funkcji. Poniższy fragment kodu przedstawia, jak działają argumenty domyślne. Aby uzyskać więcej informacji na temat ograniczeń dotyczących dotyczące określania argumentów domyślnych, zobacz [argumenty domyślne](../cpp/default-arguments.md).  
  
```  
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
  
 Program poprzedniego deklaruje funkcję, `print`, która przyjmuje dwa argumenty. Jednak drugi argument `terminator`, ma wartość domyślną `"\n"`. W **głównego**, dwa pierwsze wywołania `print` Zezwalaj na drugi argument domyślny dostarczyć nowy wiersz, aby zakończyć drukowanymi ciągu. Trzeci wywołanie określa jawną wartość jako drugi argument. Dane wyjściowe z programu  
  
```  
hello,  
world!  
good morning, sunshine.  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Typy wyrażeń](../cpp/types-of-expressions.md)