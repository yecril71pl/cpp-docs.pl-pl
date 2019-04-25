---
title: Konwersje typów zdefiniowane przez użytkownika (C++)
ms.date: 11/04/2016
f1_keywords:
- explicit_cpp
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
ms.openlocfilehash: 2af30ad3d1244146f32bf2402ed7eccdc4785c1b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62244139"
---
# <a name="user-defined-type-conversions-c"></a>Konwersje typów zdefiniowane przez użytkownika (C++)

A *konwersji* tworzy nową wartość ciągu określonego typu z wartością innego typu. *Konwersje standardowe* wbudowane funkcje języka C++ i pomocy technicznej, jego typy wbudowane i możesz utworzyć *zdefiniowane przez użytkownika konwersje* do wykonywania konwersji do z lub między typami zdefiniowanymi przez użytkownika.

Konwersje standardowe wykonywania konwersji między wbudowanych typów między wskaźniki lub odwołania do typów powiązane przez dziedziczenie, do i z wskaźników typu void i wskaźnika o wartości null. Aby uzyskać więcej informacji, zobacz [konwersje standardowe](../cpp/standard-conversions.md). Konwersje zdefiniowane przez użytkownika wykonywać konwersje między typami zdefiniowanymi przez użytkownika lub między typami zdefiniowanymi przez użytkownika i typy wbudowane. Można wdrożyć je jako [konstruktory konwersji](#ConvCTOR) lub jako [funkcje konwersji](#ConvFunc).

Konwersje mogą być albo jawne — po potwierdzeniu programisty wywołuje dla jednego typu ma zostać przekonwertowany do innego, tak jak rzutowania lub inicjalizacji bezpośredniej — lub niejawne — gdy język lub program wywołuje dla innego typu niż ten, który został podany przez programistę.

Niejawne konwersje są próby po:

- Argument przekazany do funkcji nie ma tego samego typu co parametr dopasowania.

- Wartość zwrócona przez funkcję nie ma taki sam typ co typ zwracany funkcji.

- Wyrażenie inicjatora nie ma tego samego typu co obiekt, który inicjuje go.

- Wyrażenie kontrolujące instrukcji warunkowej, pętli konstrukcja lub przełącznik nie ma typu wyniku, które są wymagane do nad nim kontroli.

- Argument podany dla operatora nie ma tego samego typu jako zgodnego parametr argumentu operacji. Dla wbudowanych operatorów oba operandy muszą mieć taki sam typ, a są konwertowane na wspólny typ, który może reprezentować oba. Aby uzyskać więcej informacji, zobacz [konwersje standardowe](standard-conversions.md). Dla operatorów zdefiniowanych przez użytkownika każdy argument musi mieć tego samego typu jako zgodnego parametr argumentu operacji.

Gdy jeden konwersja standardowa nie może ukończyć niejawnej konwersji, kompilator służy konwersji zdefiniowanej przez użytkownika, a następnie opcjonalnie dodatkowe konwersją standardową, oznacz go jako ukończony.

Co najmniej dwóch zdefiniowane przez użytkownika konwersje, wykonujących tej samej konwersji są dostępne w witrynie konwersji, konwersja jest określane jako niejednoznaczny. Takie niejednoznaczności są błąd, ponieważ kompilator nie może określić, który z nich dostępne konwersje należy wybrać. Jednak nie jest to błąd, wystarczy, aby zdefiniować wiele sposobów wykonania tej samej konwersji, ponieważ zestaw dostępne konwersje mogą być różne w różnych miejscach w kodzie źródłowym — na przykład, w zależności od tego, który nagłówek pliki znajdują się w pliku źródłowym. Tak długo, jak tylko jednej konwersji jest dostępny w witrynie konwersji, nie ma żadnych niejednoznaczności. Istnieje kilka sposobów, mogą wystąpić Niejednoznaczne konwersje, które najbardziej typowymi są:

- Wielokrotne dziedziczenie. Konwersja jest zdefiniowany w więcej niż jednej klasy bazowej.

- Wywołanie funkcji niejednoznaczne. Konwersja jest zdefiniowany jako Konstruktor konwersji typu docelowego, a funkcję konwersji typu źródłowego. Aby uzyskać więcej informacji, zobacz [funkcje konwersji](#ConvFunc).

Zwykle można rozwiązać niejednoznaczność, po prostu kwalifikując nazwę typu zaangażowanych w pełnym lub wykonując jawnego rzutowania w celu wyjaśnienia intencji użytkownika.

Konstruktory konwersji i funkcje konwersji przestrzegają zasad kontroli dostępu do elementu członkowskiego, ale dostępność konwersje jest uwzględniana tylko, jeśli można określić jednoznaczna konwersja. Oznacza to, że konwersja może być niejednoznaczna, nawet wtedy, gdy poziom dostępu konkurencyjnych konwersji uniemożliwiałyby jej użycia. Aby uzyskać więcej informacji na temat ułatwień dostępu elementu członkowskiego zobacz [kontrola dostępu do składowych](../cpp/member-access-control-cpp.md).

## <a name="the-explicit-keyword-and-problems-with-implicit-conversion"></a>Explicit — słowo kluczowe i problemy z niejawnej konwersji

Domyślnie po utworzeniu konwersji zdefiniowanej przez użytkownika, kompilator służy do wykonywania niejawnej konwersji. Czasami jest to, co chcesz zrobić, ale innym razem prostych reguł, które prowadzą kompilatora w podejmowaniu niejawnych konwersji może doprowadzić do kodu, których nie chcesz, aby zaakceptować.

Dobrze znane przykładem niejawnej konwersji, które mogą powodować problemy jest konwersja **bool**. Istnieje wiele przyczyn, które można utworzyć typu klasy, które mogą być używane w kontekście Boolean — na przykład, tak że może służyć do sterowania **Jeśli** instrukcji lub pętli — ale kiedy kompilator wykonuje konwersja zdefiniowana przez użytkownika, aby wbudowany typ, kompilator może zastosować później dodatkowe konwersja standardowa. Celem tego dodatkowe konwersja standardowa jest umożliwiające elementów, takich jak promocji z **krótki** do **int**, ale również otwiera drzwi biblioteki mniej oczywistych konwersje — na przykład z  **wartość logiczna** do **int**, co pozwala danego typu klasa, ma być używany w kontekstach liczby całkowitej, nigdy nie jest przeznaczony. Tego konkretnego problemu jest znany jako *bezpieczne Bool Problem*. Tego rodzaju problemy to lokalizacja **jawne** — słowo kluczowe może pomóc.

**Jawne** — słowo kluczowe informuje kompilator, że określonej konwersji nie może służyć do wykonywania niejawnej konwersji. Jeśli chcesz składni wygody niejawne konwersje przed **jawne** wprowadzono — słowo kluczowe, musieli akceptować niezamierzone konsekwencje tego niejawna konwersja czasami tworzone albo użyj mniej wygodne Funkcje konwersji o nazwie obejść ten problem. Teraz, korzystając z **jawne** — słowo kluczowe, możesz utworzyć wygodne konwersji, należy używać tylko do wykonywania jawnych rzutowań lub inicjalizacji bezpośredniej i który nie zaprowadzi do rodzaju wyjaśnienie działania na bezpieczne Bool Problem problemów.

**Jawne** — słowo kluczowe może odnosić się do konstruktorów konwersji od C ++ 98 i funkcje konwersji, ponieważ C ++ 11. Poniższe sekcje zawierają więcej informacji o sposobie używania **jawne** — słowo kluczowe.

## <a name="ConvCTOR"></a> Konstruktory konwersji

Konstruktory konwersji zdefiniować konwersje z typów zdefiniowanych przez użytkownika lub wbudowane do typu zdefiniowanego przez użytkownika. W poniższym przykładzie pokazano Konstruktor konwersji, która konwertuje typ wbudowany **double** na typ zdefiniowany przez użytkownika `Money`.

```cpp
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

Zwróć uwagę, że pierwsze wywołanie do funkcji `display_balance`, który przyjmuje argument typu `Money`, nie wymaga konwersji, ponieważ jej argument ma poprawnego typu. Jednak na drugie wywołanie `display_balance`, konwersja jest niezbędne, ponieważ typ argumentu, **double** o wartości `49.95`, to nie funkcja oczekiwaniom. Funkcja nie może bezpośrednio, użyj tej wartości, ale ponieważ nie istnieje konwersja z typu argumentu —**double**— typ pasującej do parametru —`Money`— tymczasowej wartości typu `Money` jest zbudowany z argument i przeznaczyć na wykonywanie wywołań funkcji. W trzecim wywołaniu `display_balance`, zwróć uwagę, że argument nie jest **double**, jest jednak **float** o wartości `9.99`— i jeszcze wywołanie funkcji nadal może zostać ukończona, ponieważ kompilatora można wykonać konwersji standardowej — w tym przypadku z **float** do **double**— a następnie dokonaj konwersji zdefiniowanej przez użytkownika z **double** do `Money` można ukończyć konwersji konieczne.

### <a name="declaring-conversion-constructors"></a>Deklarowanie konstruktorów konwersji

Obowiązują następujące reguły do deklarowania konstruktora konwersji:

- Typ docelowy konwersji jest typ zdefiniowany przez użytkownika, który jest konstruowany.

- Konstruktory konwersji zwykle po dokładnie jednego argumentu, który jest typem źródła. Konstruktor konwersji można jednak określić dodatkowe parametry, jeśli każdy dodatkowy parametr ma wartość domyślną. Typ źródłowy pozostaje typ pierwszego parametru.

- Konstruktory konwersji, podobnie jak wszystkie konstruktory nie należy określać typ zwracany. Określanie zwracanego typu w deklaracji występuje błąd.

- Konstruktory konwersji może być jawne.

### <a name="explicit-conversion-constructors"></a>Jawna konwersja konstruktorów

Przez zadeklarowanie konstruktora konwersji za **jawne**, tylko można przeprowadzić bezpośredniego inicjowania obiektu lub wykonać jawnego rzutowania. Zapobiega to funkcje, które zaakceptowanie argumentu o typie danej klasy z również niejawnie przyjmuje argumenty typu źródła Konstruktor konwersji i zapobiega typu klasy kopiowania inicjowane z wartością typu źródłowego. Poniższy przykład pokazuje jak zdefiniować Konstruktor jawnej konwersji i efekt, który ma to na jaki kod jest poprawnie sformułowany.

```cpp
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

W tym przykładzie należy zauważyć, można nadal używać konstruktora jawną konwersję do wykonania bezpośredniego inicjowania `payable`. Gdyby natomiast Inicjowanie kopiowania `Money payable = 79.99;`, byłoby błąd. Pierwsze wywołanie `display_balance` jest nienaruszona, ponieważ argument jest poprawnego typu. Drugie wywołanie `display_balance` występuje błąd, ponieważ Konstruktor konwersji nie można używać do wykonywania niejawnej konwersji. Trzecie wywołanie `display_balance` jest legalna ze względu na jawne Rzutowanie na `Money`, ale Zwróć uwagę, że kompilator nadal pomogła wykonaj rzutowanie, wstawiając niejawne rzutowanie z **float** do **double**.

Chociaż wygody umożliwienia konwersji niejawnych; może być kuszące, spowoduje to więc wprowadzić twardych do znalezienia błędów. Podstawową zasadą jest zapewnienie wszystkie konstruktory konwersji jawnej, z wyjątkiem sytuacji, gdy wiesz, mają określone konwersję niejawnie wystąpić.

##  <a name="ConvFunc"></a> Funkcje konwersji

Funkcje konwersji zdefiniować konwersji z typu zdefiniowanego przez użytkownika do innych typów. Te funkcje są czasami określane jako "operatorami rzutowania" ponieważ one wraz z konstruktorów konwersji są wywoływane, gdy wartość jest rzutowany na innego typu. W poniższym przykładzie pokazano funkcję konwersji, która konwertuje typ zdefiniowany przez użytkownika `Money`, do typu wbudowanego **double**:

```cpp
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

Należy zauważyć, że zmiennej składowej `amount` wykonano prywatnych i publicznych konwersji funkcja wpisz **double** wprowadza się tylko do zwracania wartości `amount`. W funkcji `display_balance`, niejawna konwersja występuje, gdy wartość `balance` jest przesyłany strumieniowo do wyjścia standardowego za pomocą operatora wstawiania strumienia `<<`. Ponieważ żaden operator wstawiania strumienia jest zdefiniowany dla typu zdefiniowanego przez użytkownika `Money`, ale jest on dostępny dla typu wbudowanego **double**, kompilator może używać funkcji konwersji z `Money` do **podwójnejprecyzji** spełnić operator wstawiania strumienia.

Funkcje konwersji są dziedziczone przez klasy pochodne. Funkcje konwersji w klasie pochodnej tylko musi zostać zastąpiona funkcja konwersji odziedziczone po konwertują do dokładnie tego samego typu. Na przykład konwersja zdefiniowana przez użytkownika funkcja klasy pochodnej **operator int** nie zastępuje — lub nawet wpływu — konwersja zdefiniowana przez użytkownika funkcji klasy podstawowej **operator krótki**nawet Chociaż konwersje standardowe zdefiniować relację konwersji między **int** i **krótki**.

### <a name="declaring-conversion-functions"></a>Deklarowania funkcji konwersji

Do deklarowania funkcji konwersji stosowane następujące reguły:

- Typ docelowy konwersji musi być zadeklarowany przed deklaracją funkcji konwersji. Nie można zadeklarować klasy, struktury, wyliczenia i definicje typów w ramach deklaracji funkcji konwersji.

    ```cpp
    operator struct String { char string_storage; }() // illegal
    ```

- Funkcje konwersji nie przyjmują argumentów. Określanie parametrów w deklaracji występuje błąd.

- Funkcje konwersji mają zwracany typ, który jest określony przez nazwę funkcji konwersji, która jest również nazwą typ docelowy konwersji. Określanie zwracanego typu w deklaracji występuje błąd.

- Funkcje konwersji mogą być wirtualne.

- Funkcje konwersji może być jawne.

### <a name="explicit-conversion-functions"></a>Funkcje konwersji jawnej

Gdy funkcja konwersji jest zadeklarowany jawnie, może tylko służyć do wykonywania jawnego rzutowania. Zapobiega to funkcje, które akceptują argument typu docelowego funkcję konwersji z również niejawnie przyjmuje argumenty typu klasy i zapobiega wystąpień typu docelowego kopii inicjowane z wartością typu klasy. Poniższy przykład pokazuje jak zdefiniować funkcję konwersji jawnej i efekt, ma to na jaki kod jest dobrze sformułowany.

```cpp
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

Tutaj funkcję konwersji **operator double** wykonano jawnej i jawnego rzutowania na typ **double** został wprowadzony w funkcji `display_balance` dokonać konwersji. W przypadku pominięcia to rzutowanie były kompilator nie będzie można zlokalizować operator odpowiednie wstawiania strumienia `<<` dla typu `Money` i mógłby wystąpić błąd.