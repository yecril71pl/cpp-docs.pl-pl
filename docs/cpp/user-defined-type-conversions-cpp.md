---
title: "Zdefiniowane przez użytkownika konwersje typów (C++) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: explicit_cpp
dev_langs: C++
helpviewer_keywords:
- constructors [C++], and constants
- conversion functions [C++]
- explicit keyword [C++]
- type conversion
- constructors [C++], drawbacks
- conversion constructors
- type conversion [C++], explicit conversion
- coercion [C++]
- conversions [C++], explicit
- objects [C++], converting
- conversion functions [C++], rules for declaring
- declaring functions [C++], conversion functions
- functions [C++], conversion
- converting objects
- constructors [C++], conversion
- conversions [C++], by constructors
- data type conversion [C++], explicit
ms.assetid: d40e4310-a190-4e95-a34c-22c5c20aa0b9
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 561730527a215d5314f7239affc764d9f5925f67
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="user-defined-type-conversions-c"></a>Typ zdefiniowany przez użytkownika konwersje (C++)
A *konwersji* tworzy nową wartość typu z wartością innego typu. *Konwersje standardowe* są wbudowane w języku C++ i pomocy technicznej, można utworzyć swoją wbudowanych typów, a *zdefiniowane przez użytkownika konwersje* do wykonywania konwersji do z i między typy danych zdefiniowane przez użytkownika.  
  
 Konwersje standardowe wykonywania konwersji między wbudowanych typów między wskaźniki lub odwołania do typy powiązane z dziedziczenie do i z wskaźniki typu void i wskaźnika null. Aby uzyskać więcej informacji, zobacz [konwersje standardowe](../cpp/standard-conversions.md). Konwersje zdefiniowane przez użytkownika wykonywania konwersji między typy danych zdefiniowane przez użytkownika lub wbudowane typy i typy danych zdefiniowane przez użytkownika. Można wdrożyć je jako [konstruktory konwersji](#ConvCTOR) lub jako [funkcji konwersji](#ConvFunc).  
  
 Konwersje może być albo jawne — gdy programistę odwołuje się do jednego typu ma zostać przekonwertowany do innego, tak jak cast lub bezpośredniego inicjowania — ani niejawnych — gdy języka lub program odwołuje się do innego typu niż podany przez programistę.  
  
 Niejawne konwersje są próby po:  
  
-   Argument przekazany do funkcji nie ma tego samego typu co parametr dopasowania.  
  
-   Wartość zwrócona przez funkcję nie ma ten sam typ co typ zwracany funkcji.  
  
-   Wyrażenia inicjatora nie ma tego samego typu co obiekt, który jest podczas inicjowania.  
  
-   Wyrażenie, które kontroluje instrukcji warunkowej, konstrukcji pętli lub przełącznik nie ma typ wyniku, które są wymagane do nad nim kontroli.  
  
-   Argument przekazany do operator nie ma tego samego typu co dopasowywania parametru argument. Dla wbudowanych operatorów oba argumenty muszą być tego samego typu i są konwertowane na wspólny typ, mogącej reprezentować jednocześnie. Aby uzyskać więcej informacji, zobacz [konwersje standardowe](standard-conversions.md). Dla operatorów zdefiniowanych przez użytkownika każdy operand musi być taki sam typ jak dopasowywania parametru argument.  
  
 Po jednym konwersja standardowa nie może ukończyć niejawna konwersja, kompilator może być konwersji zdefiniowanych przez użytkownika, a następnie opcjonalnie dodatkowe konwersja standardowa zakończyć je.  
  
 Jeśli co najmniej dwa zdefiniowane przez użytkownika konwersje, które dokonać konwersji tego samego są dostępne w witrynie konwersji, konwersja jest określany jako niejednoznaczne. Takie niejednoznaczności są błąd kompilatora nie może ustalić, które z nich dostępne konwersje należy wybrać. Jednak nie jest błąd tak, aby zdefiniować wiele sposobów wykonywania tego samego konwersji, ponieważ zestaw dostępnych konwersji mogą być różne w różnych lokalizacjach w kodzie źródłowym — na przykład, w zależności od tego, które nagłówka pliki znajdują się w pliku źródłowym. Tak długo, jak tylko jedna konwersja jest dostępny w witrynie konwersji, nie istnieje żadne niejednoznaczności. Istnieje kilka metod, które mogą wystąpić Niejednoznaczne konwersje, ale są najbardziej typowe:  
  
-   Dziedziczenie wielokrotne. Konwersja jest zdefiniowany w więcej niż jedną klasę podstawową. 
  
-   Wywołanie funkcji niejednoznaczne. Konwersja jest zdefiniowany jako konstruktora konwersji typu docelowego, a funkcji konwersji typu źródłowego. Aby uzyskać więcej informacji, zobacz [funkcji konwersji](#ConvFunc).  
  
 Zwykle można usunąć niejednoznaczność, wystarczy kwalifikowanie nazwę typu zaangażowane w pełnym lub wykonując jawnego rzutowania Sprecyzuj wyrażenie z.  
  
 Zarówno konstruktory konwersji, jak i funkcji konwersji przestrzegać zasad kontroli dostępu do elementu członkowskiego, ale dostępność konwersje tylko uważa się wtedy, gdy można ustalić jednoznaczne konwersji. To oznacza, że konwersja może być niejednoznaczna nawet wtedy, gdy poziom dostępu konkurencyjnych konwersji uniemożliwiłyby on używany. Aby uzyskać więcej informacji o ułatwieniach dostępu elementu członkowskiego, zobacz [kontroli dostępu elementu członkowskiego](../cpp/member-access-control-cpp.md).  
  
## <a name="the-explicit-keyword-and-problems-with-implicit-conversion"></a>Explicit — słowo kluczowe i problemów z niejawna konwersja  
 Domyślnie podczas tworzenia konwersji zdefiniowanej przez użytkownika, kompilator służy do wykonywania niejawnej konwersji. Czasami jest to, co ma, ale innym razem prostych reguł, które prowadzą kompilatora w podejmowaniu niejawne konwersje może doprowadzić do kodu, których nie chcesz, aby zaakceptować.  
  
 Dobrze znane przykładem niejawnej konwersji, która może spowodować problemy jest konwersja `bool`. Istnieje wiele przyczyn, które można utworzyć typu klasy, które mogą być używane w kontekście Boolean — na przykład, tak że służy do sterowania `if` instrukcji lub pętli — gdy kompilator wykonuje zdefiniowane przez użytkownika konwersji na typ wbudowany , kompilator może zastosować później dodatkowe konwersja standardowa. Celem tego dodatkowe konwersja standardowa jest umożliwienie dla elementów, jak podwyższenia poziomu z `short` do `int`, zostanie otwarte także drzwi konwersje mniej oczywista, ale — na przykład z `bool` do `int`, co pozwala na klasę Typ ma być używany w kontekstach liczba całkowita, który nigdy nie powinien. Tego konkretnego problemu nosi nazwę *bezpieczne Bool Problem*. Tego rodzaju problem jest where `explicit` — słowo kluczowe może pomóc.  
  
 `explicit` — Słowo kluczowe informuje kompilator, że określonej konwersji nie może służyć do wykonywania niejawnej konwersji. Jeśli potrzebujesz składni wygodę niejawne konwersje przed `explicit` wprowadzono — słowo kluczowe, musieli zaakceptować niezamierzonych konsekwencji tego niejawna konwersja czasami tworzone albo użyj konwersji wygodny bez, o nazwie Funkcje jako obejście tego problemu. Teraz, używając `explicit` — słowo kluczowe, możesz utworzyć wygodny konwersje, które mogą służyć tylko do wykonaj jawne rzutowanie lub bezpośredniego inicjowania i który nie będzie prowadzić do rodzaju problemów wyjaśnienie działania przez bezpieczne Bool Problem.  
  
 `explicit` — Słowo kluczowe może odnosić się do konstruktory konwersji od języka C ++ 98 oraz do funkcji konwersji od języka C ++ 11. Poniższe sekcje zawierają więcej informacji o sposobie używania `explicit` — słowo kluczowe.  
  
##  <a name="ConvCTOR"></a>Konwersja konstruktorów  
 Konstruktory konwersji zdefiniuj konwersje z typów zdefiniowanych przez użytkownika lub wbudowanych do typu zdefiniowanego przez użytkownika. W poniższym przykładzie pokazano konwersji konstruktora, który konwertuje z typu wbudowanego `double` do typu zdefiniowanego przez użytkownika `Money`.  
  
```  
#include <iostream>  
  
class Money  
{  
public:  
    Money() : amount{ 0.0 } {};  
    Money(double _amount) : amount{ _amount } {};  
  
    double amount;  
};  
  
void display_balance(const Money balance)  
{  
    std::cout << "The balance is: " << balance.amount << std::endl;  
}  
  
int main(int argc, char* argv[])  
{  
    Money payable{ 79.99 };  
  
    display_balance(payable);  
    display_balance(49.95);  
    display_balance(9.99f);  
  
    return 0;  
}  
```  
  
 Powiadomienie, że pierwsze wywołanie funkcji `display_balance`, który przyjmuje argument typu `Money`, nie wymaga konwersji, ponieważ jej argument jest nieprawidłowego typu. Jednak na drugie wywołanie `display_balance`, konwersja jest potrzebna, ponieważ typ argumentu, `double` o wartości `49.95`, to nie to, co Funkcja spodziewa się. Funkcji nie można użyć tej wartości bezpośrednio, ale ponieważ brak konwersji z typu argumentu —`double`— typowi parametru dopasowania —`Money`— wartości tymczasowej typu `Money` jest tworzony w argumencie i używane do Ukończenie wywołania funkcji. W wywołaniu trzeci `display_balance`, zwróć uwagę, że argument nie jest `double`, ale zamiast tego jest `float` o wartości `9.99`— i jeszcze wywołania funkcji nadal może być ukończona, ponieważ kompilator można wykonać konwersji standardowej — w takim przypadku , z `float` do `double`— a następnie dokonaj konwersji zdefiniowanej przez użytkownika z `double` do `Money` do wykonania niezbędnych konwersji.  
  
### <a name="declaring-conversion-constructors"></a>Deklarowanie konstruktorów konwersji  
 Następujące reguły dotyczą deklarowanie konstruktora konwersji:  
  
-   Typ docelowy konwersji jest typ zdefiniowany przez użytkownika jest tworzona.  
  
-   Konstruktory konwersji zwykle zajmują dokładnie jednego argumentu, który jest typem źródła. Konstruktor konwersji można jednak określić dodatkowe parametry, jeśli każdy dodatkowy parametr ma wartość domyślną. Typ źródła pozostaje typ pierwszego parametru.  
  
-   Konstruktory konwersji, podobnie jak wszystkie konstruktory nie należy określać typu zwracanego. Określanie zwracanego typu w deklaracji występuje błąd.  
  
-   Konstruktory konwersji może być jawnego.  
  
### <a name="explicit-conversion-constructors"></a>Jawna konwersja konstruktorów  
 Przez zadeklarowanie konstruktora konwersji za `explicit`, mogą być używane tylko, wykonać bezpośredniego inicjowania obiektu lub wykonać jawnego rzutowania. Zapobiega to funkcje, które akceptuje argumentu typu klasy z również niejawnie przyjmuje argumenty konstruktora konwersji typu źródłowego i uniemożliwia typu klasy kopiowania zainicjowany z wartością typu źródłowego. W poniższym przykładzie pokazano sposób definiowania konstruktora jawnej konwersji i efekt, który ma na jakie kodu jest poprawnie sformułowany.  
  
```  
#include <iostream>  
  
class Money  
{  
public:  
    Money() : amount{ 0.0 } {};  
    explicit Money(double _amount) : amount{ _amount } {};  
  
    double amount;  
};  
  
void display_balance(const Money balance)  
{  
    std::cout << "The balance is: " << balance.amount << std::endl;  
}  
  
int main(int argc, char* argv[])  
{  
    Money payable{ 79.99 };        // Legal: direct initialization is explicit.  
  
    display_balance(payable);      // Legal: no conversion required  
    display_balance(49.95);        // Error: no suitable conversion exists to convert from double to Money.  
    display_balance((Money)9.99f); // Legal: explicit cast to Money  
  
    return 0;  
}  
```  
  
 W tym przykładzie zwróć uwagę, można nadal używać konstruktora jawnej konwersji do wykonania bezpośredniego inicjowania `payable`. Gdyby zamiast kopiowania zainicjować `Money payable = 79.99;`, może wystąpić błąd. W pierwszym wywołaniu `display_balance` jest nie dotyczy, ponieważ argument jest nieprawidłowego typu. Drugie wywołanie `display_balance` jest błąd, ponieważ Konstruktor konwersji nie mogą posłużyć do wykonania niejawne konwersje. Trzeci wywołanie `display_balance` jest dozwolony z powodu jawne Rzutowanie na `Money`, ale należy zauważyć, że kompilator nadal pomogła wykonać rzutowanie wstawiając niejawne rzutowanie z `float` do `double`.  
  
 Chociaż wygodę zezwalanie niejawne konwersje może być kuszące, spowoduje to mogą stać się twarde do znalezienia usterek. Zasadą jest zapewnienie wszystkie konstruktory konwersji jawnej z wyjątkiem przypadków, gdy wiesz, które mają określone konwersji występuje niejawnie.  
  
##  <a name="ConvFunc"></a>Funkcje konwersji  
 Funkcje konwersji zdefiniuj konwersji z typu zdefiniowanego przez użytkownika na inne typy. Te funkcje są czasami określane jako "operatory rzutowania" ponieważ, wraz z konstruktory konwersji, są one nazywane gdy wartość jest rzutowane do innego typu. W poniższym przykładzie pokazano konwertuje z typu zdefiniowanego przez użytkownika funkcja konwersji `Money`, na typ wbudowany `double`:  
  
```  
#include <iostream>  
  
class Money  
{  
public:  
    Money() : amount{ 0.0 } {};  
    Money(double _amount) : amount{ _amount } {};  
  
    operator double() const { return amount; }  
private:  
    double amount;  
};  
  
void display_balance(const Money balance)  
{  
    std::cout << "The balance is: " << balance << std::endl;  
}  
  
```  
  
 Zwróć uwagę, że zmiennej członkowskiej `amount` staje się prywatne i publiczne konwersji funkcja wpisz `double` wprowadza się tylko w celu zwracania wartości `amount`. W funkcji `display_balance`, niejawna konwersja występuje, gdy wartość `balance` przesyłane strumieniowo do wyjścia standardowego za pomocą operatora wstawiania strumienia `<<`. Ponieważ żaden operator wstawiania strumienia nie jest zdefiniowana dla typu zdefiniowanego przez użytkownika `Money`, ale jest on dostępny dla typu wbudowanego `double`, kompilator można użyć funkcji konwersji z `Money` do `double` do zaspokojenia wstawiania strumienia operator.  
  
 Funkcje konwersji są dziedziczone przez klasy pochodnej. Funkcji konwersji w klasie pochodnej zastąpić funkcji konwersji dziedziczone tylko jeśli Konwertuj dokładnie tego samego typu. Na przykład funkcja zdefiniowana przez użytkownika konwersja klasy pochodnej `operator int` nie przesłania — lub nawet wpływu — funkcja zdefiniowana przez użytkownika konwersja klasy podstawowej `operator short`, mimo że konwersje standardowe zdefiniuj konwersji Relacja między `int` i `short`.  
  
### <a name="declaring-conversion-functions"></a>Deklarowanie funkcji konwersji  
 Następujące reguły dotyczą deklarowania funkcji konwersji:  
  
-   Typ docelowy konwersji musi być zadeklarowana przed deklaracji funkcji konwersji. Nie można zadeklarować klasy, struktury, wyliczenia i definicji typów w deklaracji funkcji konwersji.  
  
    ```  
    operator struct String { char string_storage; }() // illegal  
    ```  
  
-   Funkcje konwersji nie przyjmują argumentów. Określanie parametrów w deklaracji występuje błąd.  
  
-   Funkcje konwersji ma typ zwracany jest określony przez nazwę funkcji konwersji, który jest także nazwa typ docelowy konwersji. Określanie zwracanego typu w deklaracji występuje błąd.  
  
-   Funkcje konwersji mogą być wirtualne.  
  
-   Funkcje konwersji może być jawnego.  
  
### <a name="explicit-conversion-functions"></a>Jawna konwersja funkcji  
 Gdy funkcja konwersji został zadeklarowany jako jawne, tylko umożliwia przeprowadzenie jawnego rzutowania. Zapobiega to funkcje, które akceptuje argumentu typu docelowego funkcji konwersji z również niejawnie przyjmuje argumenty typu klasy i uniemożliwia wystąpień typu docelowego kopii zainicjowany z wartością typu klasy. W poniższym przykładzie pokazano sposób definiowania funkcji jawnej konwersji oraz wpływ ma na jakie kodu jest poprawnie sformułowany.  
  
```  
#include <iostream>  
  
class Money  
{  
public:  
    Money() : amount{ 0.0 } {};  
    Money(double _amount) : amount{ _amount } {};  
  
    explicit operator double() const { return amount; }  
private:  
    double amount;  
};  
  
void display_balance(const Money balance)  
{  
    std::cout << "The balance is: " << (double)balance << std::endl;  
}  
  
```  
  
 Tutaj funkcji konwersji `operator double` wprowadzono jawne i jawne Rzutowanie na typ `double` został wprowadzony w funkcji `display_balance` do wykonania konwersji. Pominięcie tego rzutowania zostały kompilator będzie mógł zlokalizować operator odpowiedniego wstawiania strumienia `<<` dla typu `Money` i może wystąpić błąd.  
  
