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
ms.openlocfilehash: e7889a7365a6b3a362804d3dad4b2fefc3780d01
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227039"
---
# <a name="user-defined-type-conversions-c"></a>Konwersje typów zdefiniowane przez użytkownika (C++)

*Konwersja* tworzy nową wartość pewnego typu z wartości innego typu. *Konwersje standardowe* są wbudowane w język C++ i obsługują swoje wbudowane typy. można także tworzyć *konwersje zdefiniowane przez użytkownika* w celu przeprowadzenia konwersji do, z lub między typami zdefiniowanymi przez użytkownika.

Konwersje standardowe wykonują konwersje między typami wbudowanymi, między wskaźnikami lub odwołaniami do typów związanych przez dziedziczenie, do i z wskaźników typu void oraz do wskaźnika o wartości null. Aby uzyskać więcej informacji, zobacz [standardowe konwersje](../cpp/standard-conversions.md). Konwersje zdefiniowane przez użytkownika wykonują konwersje między typami zdefiniowanymi przez użytkownika, a także między typami zdefiniowanymi przez użytkownika i typami wbudowanymi. Można je zaimplementować jako [konstruktory konwersji](#ConvCTOR) lub [funkcje konwersji](#ConvFunc).

Konwersje mogą być jawne — gdy programista wywołuje dla jednego typu konwersję na inny, jak w przypadku inicjowania rzutowania lub bezpośredniego — lub niejawne — gdy język lub program wywołuje dla innego typu niż ten określony przez programistę.

Niejawne konwersje są podejmowane w przypadku:

- Argument przekazany do funkcji nie ma tego samego typu co pasujący parametr.

- Wartość zwrócona przez funkcję nie ma tego samego typu co typ zwracany funkcji.

- Wyrażenie inicjatora nie ma tego samego typu co obiekt, który jest inicjowany.

- Wyrażenie sterujące instrukcją warunkową, konstrukcja zapętlenia lub przełącznik nie ma typu wyniku wymaganego do jego kontroli.

- Operand przekazany do operatora nie ma tego samego typu co parametr pasującego operandu. W przypadku operatorów wbudowanych oba operandy muszą mieć ten sam typ i są konwertowane na wspólny typ, który może reprezentować oba elementy. Aby uzyskać więcej informacji, zobacz [standardowe konwersje](standard-conversions.md). Dla operatorów zdefiniowanych przez użytkownika każdy operand musi mieć taki sam typ jak pasujący parametr operandu.

Jeśli jedna standardowa konwersja nie może zakończyć konwersji niejawnej, kompilator może użyć konwersji zdefiniowanej przez użytkownika, a opcjonalnie przez dodatkową konwersję standardową, aby ją ukończyć.

Gdy w lokacji konwersji są dostępne co najmniej dwie konwersje zdefiniowane przez użytkownika, które wykonują tę samą konwersję, konwersja jest uznawana za niejednoznaczną. Takie niejasności są błędem, ponieważ kompilator nie może określić, która z dostępnych konwersji powinna wybrać. Jednak nie jest to błąd tylko w celu zdefiniowania wielu sposobów wykonywania tej samej konwersji, ponieważ zestaw dostępnych konwersji może różnić się w różnych lokalizacjach w kodzie źródłowym — na przykład, w zależności od tego, które pliki nagłówkowe znajdują się w pliku źródłowym. Tak długo, jak tylko jedna konwersja jest dostępna w lokacji konwersji, nie ma niejednoznaczności. Istnieje kilka sposobów, że mogą wystąpić niejednoznaczne konwersje, ale najbardziej typowe są następujące:

- Wielokrotne dziedziczenie. Konwersja jest zdefiniowana w więcej niż jednej klasie bazowej.

- Niejednoznaczne wywołanie funkcji. Konwersja jest definiowana jako Konstruktor konwersji typu docelowego i jako funkcja konwersji typu źródłowego. Aby uzyskać więcej informacji, zobacz [funkcje konwersji](#ConvFunc).

Zazwyczaj można rozwiązać niejednoznaczność, kwalifikując nazwę danego typu w pełni lub przez wykonanie jawnego rzutowania w celu wyjaśnienia intencji.

Zarówno konstruktory konwersji, jak i funkcje konwersji przestrzegają reguł kontroli dostępu do elementów członkowskich, ale dostępność konwersji jest brana pod uwagę tylko wtedy, gdy można określić niejednoznaczną konwersję. Oznacza to, że konwersja może być niejednoznaczna, nawet jeśli poziom dostępu konkurencyjnej konwersji uniemożliwi jego użycie. Aby uzyskać więcej informacji na temat ułatwień dostępu członków, zobacz [Access Control członkowskich](../cpp/member-access-control-cpp.md).

## <a name="the-explicit-keyword-and-problems-with-implicit-conversion"></a>Jawne słowo kluczowe i problemy z niejawną konwersją

Domyślnie podczas tworzenia konwersji zdefiniowanej przez użytkownika kompilator może używać go do wykonywania konwersji niejawnych. Czasami jest to to, czego potrzebujesz, ale inne proste reguły, które przeprowadzą kompilator w celu przeprowadzenia konwersji niejawnych, mogą spowodować zaakceptowanie kodu, którego nie chcesz.

Jednym dobrze znanym przykładem niejawnej konwersji, która może spowodować problemy, jest konwersja na **`bool`** . Istnieje wiele powodów, dla których można utworzyć typ klasy, który może być używany w kontekście Boolean — na przykład, aby można było go użyć do sterowania **`if`** instrukcją lub pętlą, ale gdy kompilator wykonuje konwersję zdefiniowaną przez użytkownika do typu wbudowanego, kompilator może później zastosować dodatkową konwersję standardową. Celem tej dodatkowej konwersji standardowej jest umożliwienie takich, jak promocja z **`short`** do **`int`** , ale również drzwi do konwersji o mniej oczywisty sposób — na przykład od **`bool`** do **`int`** , które umożliwiają użycie typu klasy w kontekstach całkowitych, które nigdy nie zostały zamierzone. Ten konkretny problem jest znany jako *bezpieczny problem logiczny*. Ten rodzaj problemu polega na tym, że **`explicit`** słowo kluczowe może pomóc.

**`explicit`** Słowo kluczowe informuje kompilator, że nie można użyć określonej konwersji do wykonywania konwersji niejawnych. Jeśli chcesz, aby składnia niejawnych konwersji była przydatna przed **`explicit`** wprowadzeniem słowa kluczowego, musisz zaakceptować niezamierzone konsekwencje niejawnej konwersji lub użyć mniej wygody, nazwanych funkcji konwersji jako obejścia. Teraz za pomocą **`explicit`** słowa kluczowego można utworzyć wygodne konwersje, które mogą być używane tylko do wykonywania jawnych rzutowania lub inicjowania bezpośredniego, i które nie będą powodować problemów exemplified przez bezpieczny problem logiczny.

**`explicit`** Słowo kluczowe może być stosowane do konstruktorów konwersji od c++ 98 oraz do konwersji funkcji od c++ 11. Poniższe sekcje zawierają więcej informacji na temat używania **`explicit`** słowa kluczowego.

## <a name="conversion-constructors"></a><a name="ConvCTOR"></a>Konstruktory konwersji

Konstruktory konwersji definiują konwersje ze zdefiniowanych przez użytkownika lub typów wbudowanych do typu zdefiniowanego przez użytkownika. Poniższy przykład demonstruje Konstruktor konwersji, który konwertuje z typu wbudowanego **`double`** na typ zdefiniowany przez użytkownika `Money` .

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

Należy zauważyć, że pierwsze wywołanie funkcji `display_balance` , która przyjmuje argument typu `Money` , nie wymaga konwersji, ponieważ jej argument jest poprawnego typu. Jednak w drugim wywołaniu `display_balance` , konwersja jest wymagana, ponieważ typ argumentu, a **`double`** o wartości `49.95` , nie jest oczekiwaną przez funkcję. Funkcja nie może używać tej wartości bezpośrednio, ale ponieważ istnieje konwersja z typu argumentu — **`double`** — do typu pasującego parametru — `Money` — wartość tymczasowa typu `Money` jest tworzona z argumentu i używana do ukończenia wywołania funkcji. W trzecim wywołaniu do `display_balance` , Zauważ, że argument nie jest **`double`** , ale zamiast tego ma wartość, **`float`** `9.99` a mimo to wywołanie funkcji można nadal zakończyć, ponieważ kompilator może wykonać konwersję standardową, w tym przypadku z **`float`** do **`double`** — a następnie wykonać konwersję zdefiniowaną przez użytkownika z **`double`** do, `Money` Aby wykonać wymaganą konwersję.

### <a name="declaring-conversion-constructors"></a>Deklarowanie konstruktorów konwersji

Następujące reguły mają zastosowanie do Deklarującego konstruktora konwersji:

- Docelowy typ konwersji jest typem zdefiniowanym przez użytkownika, który jest tworzony.

- Konstruktory konwersji zwykle przyjmują dokładnie jeden argument, który jest typu źródłowego. Jednak Konstruktor konwersji może określić dodatkowe parametry, jeśli każdy dodatkowy parametr ma wartość domyślną. Typ źródłowy pozostaje typem pierwszego parametru.

- Konstruktory konwersji, takie jak wszystkie konstruktory, nie określają zwracanego typu. Określanie typu zwracanego w deklaracji jest błędem.

- Konstruktory konwersji mogą być jawne.

### <a name="explicit-conversion-constructors"></a>Konstruktory jawnych konwersji

Deklarując Konstruktor konwersji **`explicit`** , może być używany tylko do wykonywania bezpośredniej inicjalizacji obiektu lub do wykonania jawnego rzutowania. Zapobiega to funkcjom, które akceptują argument typu klasy z również niejawnie akceptujące argumenty typu źródła konstruktora konwersji i uniemożliwia zainicjowanie typu klasy z wartości typu źródłowego. W poniższym przykładzie pokazano, jak zdefiniować Konstruktor jawnej konwersji i wpływ na kod, który jest poprawnie sformułowany.

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

W tym przykładzie należy zauważyć, że można nadal używać konstruktora jawnej konwersji do wykonywania bezpośredniej inicjacji `payable` . Jeśli zamiast tego było konieczne skopiowanie-zainicjowanie `Money payable = 79.99;` , wystąpi błąd. Pierwsze wywołanie `display_balance` jest nienaruszone, ponieważ argument jest poprawnego typu. Drugie wywołanie `display_balance` jest błędem, ponieważ Konstruktor konwersji nie może być używany do wykonywania konwersji niejawnych. Trzecie wywołanie `display_balance` jest dozwolone z powodu jawnego rzutowania na `Money` , ale zauważ, że kompilator nadal pomogła zakończyć rzutowanie, wstawiając niejawne rzutowanie z **`float`** do **`double`** .

Chociaż wygoda dopuszczania niejawnych konwersji może być trudna, może to spowodować powstanie błędów. Reguła kciuka polega na tym, że wszystkie konstruktory konwersji są jawne, z wyjątkiem sytuacji, gdy na pewno chcesz, aby określona konwersja była wykonywana niejawnie.

## <a name="conversion-functions"></a><a name="ConvFunc"></a>Funkcje konwersji

Funkcje konwersji definiują konwersje z typu zdefiniowanego przez użytkownika na inne typy. Te funkcje są czasami określane jako "Operatory rzutowania", ponieważ wraz z konstruktorami konwersji są wywoływane, gdy wartość jest rzutowana na inny typ. Poniższy przykład ilustruje funkcję konwersji, która konwertuje z typu zdefiniowanego przez użytkownika, `Money` do typu wbudowanego **`double`** :

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

Zwróć uwagę, że zmienna członkowska `amount` jest prywatna i że funkcja konwersji publicznej do typu **`double`** jest wprowadzana tylko w celu zwrócenia wartości `amount` . W funkcji `display_balance` , niejawna konwersja występuje, gdy wartość `balance` jest przesyłana strumieniowo do wyjścia standardowego przy użyciu operatora wstawiania strumienia `<<` . Ponieważ żaden operator wstawiania strumienia nie jest zdefiniowany dla typu zdefiniowanego przez użytkownika `Money` , ale istnieje jeden dla typu wbudowanego **`double`** , kompilator może użyć funkcji konwersji z `Money` do, **`double`** Aby spełnić operator wstawiania strumienia.

Funkcje konwersji są dziedziczone przez klasy pochodne. Funkcje konwersji w klasie pochodnej przesłonią dziedziczone funkcje konwersji tylko wtedy, gdy konwertują się na dokładnie ten sam typ. Na przykład funkcja konwersji zdefiniowanej przez użytkownika w **operatorze** klasy pochodnej int nie przesłania się — lub nawet ma wpływ — zdefiniowana przez użytkownika funkcja konwersji **operatora**klasy bazowej, mimo że Konwersje standardowe definiują relację konwersji między **`int`** i **`short`** .

### <a name="declaring-conversion-functions"></a>Deklarowanie funkcji konwersji

Następujące reguły mają zastosowanie do deklarowania funkcji konwersji:

- Docelowy typ konwersji musi być zadeklarowany przed deklaracją funkcji konwersji. Klasy, struktury, wyliczenia i definicje typów nie mogą być deklarowane w deklaracji funkcji konwersji.

    ```cpp
    operator struct String { char string_storage; }() // illegal
    ```

- Funkcje konwersji nie przyjmują argumentów. Określanie parametrów w deklaracji jest błędem.

- Funkcje konwersji mają zwracany typ, który jest określany przez nazwę funkcji konwersji, która jest również nazwą typu docelowego konwersji. Określanie typu zwracanego w deklaracji jest błędem.

- Funkcje konwersji mogą być wirtualne.

- Funkcje konwersji mogą być jawne.

### <a name="explicit-conversion-functions"></a>Funkcje jawnej konwersji

Gdy funkcja konwersji jest zadeklarowana jako jawna, może być używana tylko do wykonywania jawnego rzutowania. Zapobiega to funkcjom, które akceptują argument typu docelowego funkcji konwersji z również niejawnie akceptujące argumenty typu klasy i uniemożliwia wystąpienia typu docelowego przed kopiowaniem z wartości typu klasy. W poniższym przykładzie pokazano, jak zdefiniować funkcję jawnej konwersji i wpływ na kod, który jest poprawnie sformułowany.

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

W tym miejscu operator funkcji konwersji **Double** został jawnie i jawne rzutowanie do typu **`double`** zostało wprowadzone w funkcji w `display_balance` celu wykonania konwersji. Jeśli rzutowanie zostało pominięte, kompilator nie będzie mógł zlokalizować odpowiedniego operatora wstawiania strumienia `<<` dla typu i wystąpił `Money` błąd.
