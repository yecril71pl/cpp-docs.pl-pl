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
ms.openlocfilehash: e74d5b3a748a9aab22a6a9d83c4d6c4bd3379df4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374683"
---
# <a name="user-defined-type-conversions-c"></a>Konwersje typów zdefiniowane przez użytkownika (C++)

*Konwersja* tworzy nową wartość pewnego typu z wartości innego typu. *Konwersje standardowe* są wbudowane w język C++ i obsługują jego wbudowane typy i można tworzyć *konwersje zdefiniowane przez użytkownika,* aby przeprowadzać konwersje do typów zdefiniowanych przez użytkownika, z lub między nimi.

Konwersje standardowe wykonują konwersje między typami wbudowanymi, między wskaźnikami lub odwołaniami do typów związanych z dziedziczeniem, do i z wskaźników void i do wskaźnika null. Aby uzyskać więcej informacji, zobacz [Konwersje standardowe](../cpp/standard-conversions.md). Konwersje zdefiniowane przez użytkownika przeprowadzają konwersje między typami zdefiniowanymi przez użytkownika lub między typami zdefiniowanymi przez użytkownika a typami wbudowanymi. Można je zaimplementować jako [konstruktory konwersji](#ConvCTOR) lub jako [funkcje konwersji.](#ConvFunc)

Konwersje mogą być jawne — gdy programista wymaga przekonwertowania jednego typu na inny, jak w rzutowaniu lub inicjowaniu bezpośrednim — lub niejawne — gdy język lub program wymaga innego typu niż podany przez programistę.

Niejawne konwersje są podejmowane, gdy:

- Argument dostarczony do funkcji nie ma tego samego typu co pasujący parametr.

- Wartość zwracana z funkcji nie ma tego samego typu co typ zwracany funkcji.

- Wyrażenie inicjatora nie ma tego samego typu co obiekt, który jest inicjowanie.

- Wyrażenie, które kontroluje instrukcję warunkową, konstrukcję pętli lub przełącznik nie ma typu wyniku, który jest wymagany do kontrolowania go.

- Operand dostarczony do operatora nie ma tego samego typu co pasujący parametr operand. Dla operatorów wbudowanych oba operandy muszą mieć ten sam typ i są konwertowane na wspólny typ, który może reprezentować oba. Aby uzyskać więcej informacji, zobacz [Konwersje standardowe](standard-conversions.md). W przypadku operatorów zdefiniowanych przez użytkownika każdy operand musi mieć ten sam typ co pasujący parametr operand.For user-defined operators, each operand must have the same type as the matching operand-parameter.

Gdy jedna konwersja standardowa nie może ukończyć konwersji niejawnej, kompilator może użyć konwersji zdefiniowanej przez użytkownika, a następnie opcjonalnie dodatkowej konwersji standardowej, aby ją ukończyć.

Gdy w witrynie konwersji dostępne są co najmniej dwie konwersje zdefiniowane przez użytkownika, które wykonują tę samą konwersję, konwersja jest niejednoznaczna. Takie niejasności są błędem, ponieważ kompilator nie może określić, którą z dostępnych konwersji powinien wybrać. Jednak nie jest to błąd tylko zdefiniować wiele sposobów wykonywania tej samej konwersji, ponieważ zestaw dostępnych konwersji może być różny w różnych lokalizacjach w kodzie źródłowym — na przykład w zależności od tego, które pliki nagłówkowe są zawarte w pliku źródłowym. Dopóki w witrynie konwersji jest dostępna tylko jedna konwersja, nie ma dwuznaczności. Istnieje kilka sposobów, że niejednoznaczne konwersje mogą powstać, ale te najczęściej są:

- Wielokrotne dziedziczenie. Konwersja jest zdefiniowana w więcej niż jednej klasie podstawowej.

- Niejednoznaczne wywołanie funkcji. Konwersja jest zdefiniowana jako konstruktor konwersji typu docelowego i jako funkcja konwersji typu źródłowego. Aby uzyskać więcej informacji, zobacz [Funkcje konwersji](#ConvFunc).

Zazwyczaj można rozwiązać niejednoznaczności tylko przez zakwalifikowanie nazwę danego typu pełniej lub wykonując jawne rzutowanie w celu wyjaśnienia intencji.

Zarówno konstruktory konwersji, jak i funkcje konwersji są zgodne z regułami kontroli dostępu do elementu członkowskiego, ale dostępność konwersji jest brana pod uwagę tylko wtedy, gdy można określić jednoznaczną konwersję. Oznacza to, że konwersja może być niejednoznaczna, nawet jeśli poziom dostępu do konkurencyjnej konwersji uniemożliwiłby jej użycie. Aby uzyskać więcej informacji na temat ułatwień dostępu dla członków, zobacz [Kontrola dostępu do członków](../cpp/member-access-control-cpp.md).

## <a name="the-explicit-keyword-and-problems-with-implicit-conversion"></a>Jawne słowo kluczowe i problemy z konwersją niejawną

Domyślnie podczas tworzenia konwersji zdefiniowanej przez użytkownika kompilator może jej używać do wykonywania konwersji niejawnych. Czasami jest to, co chcesz, ale innym razem proste reguły, które prowadzą kompilator w tworzeniu konwersji niejawnych może prowadzić do zaakceptowania kodu, który nie chcesz go.

Jednym z dobrze znanych przykładów niejawnej konwersji, która może powodować problemy, jest konwersja na **bool**. Istnieje wiele powodów, dla których można utworzyć typ klasy, który może być używany w kontekście logicznym — na przykład, aby można było go używać do kontrolowania **instrukcji** if lub pętli — ale gdy kompilator wykonuje konwersję zdefiniowaną przez użytkownika na typ wbudowany, kompilator może później zastosować dodatkową standardową konwersję. Celem tej dodatkowej konwersji standardowej jest umożliwienie promocji od **krótkiego** do **int,** ale także otwiera drzwi dla mniej oczywistych konwersji , na przykład od **bool** **do int**, co pozwala na użycie typu klasy w kontekstach integer, których nigdy nie zamierzałeś. Ten szczególny problem jest znany jako *Safe Bool Problem*. Ten rodzaj problemu polega na tym, że słowo kluczowe **jawne** może pomóc.

**Jawne** słowo kluczowe informuje kompilatora, że określona konwersja nie może służyć do wykonywania konwersji niejawnych. Jeśli chcesz, aby wygoda składniowa niejawnych konwersji przed wprowadzeniem **jawnego** słowa kluczowego, musisz albo zaakceptować niezamierzone konsekwencje, które czasami tworzyła konwersja niejawna, lub używać mniej wygodnych, nazwanych funkcji konwersji jako obejścia. Teraz, za pomocą **jawnego** słowa kluczowego, można utworzyć wygodne konwersje, które mogą być używane tylko do wykonywania jawnych rzutowania lub bezpośredniego inicjowania, a to nie doprowadzi do tego rodzaju problemów przykładem problemu Bezpiecznego Bool.

**Jawne** słowo kluczowe można zastosować do konstruktorów konwersji od C++ 98 i funkcji konwersji od C++11. Poniższe sekcje zawierają więcej informacji na temat używania **jawnego** słowa kluczowego.

## <a name="conversion-constructors"></a><a name="ConvCTOR"></a>Konstruktory konwersji

Konstruktory konwersji definiują konwersje od typów zdefiniowanych przez użytkownika lub wbudowanych do typu zdefiniowanego przez użytkownika. W poniższym przykładzie pokazano konstruktor konwersji, **double** który konwertuje z `Money`wbudowanego typu double na typ zdefiniowany przez użytkownika.

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

Należy zauważyć, że pierwsze `display_balance`wywołanie funkcji , `Money`która przyjmuje argument typu, nie wymaga konwersji, ponieważ jego argument jest poprawnym typem. Jednak w drugim wywołaniu `display_balance`, konwersja jest potrzebna, ponieważ typ argumentu, **podwójne** z wartością `49.95`, nie jest to, czego oczekuje funkcja. Funkcja nie może używać tej wartości bezpośrednio, ale ponieważ istnieje konwersja z typu argumentu —**dwukrotnie**`Money`— do typu `Money` pasującego parametru — tymczasowa wartość typu jest konstruowana z argumentu i używana do wykonania wywołania funkcji. W trzecim wywołaniu `display_balance`, należy zauważyć, że argument nie jest **double**, ale zamiast **float** z wartością `9.99`— a jednak wywołanie funkcji nadal można wykonać, ponieważ kompilator może wykonać standardową konwersję — w tym przypadku, od **float** do **double**— a następnie wykonać konwersję zdefiniowaną przez użytkownika od **podwójnej** do, `Money` aby zakończyć niezbędną konwersję.

### <a name="declaring-conversion-constructors"></a>Deklarowanie konstruktorów konwersji

Następujące reguły mają zastosowanie do deklarowania konstruktora konwersji:

- Typ docelowy konwersji jest typ zdefiniowany przez użytkownika, który jest konstruowany.

- Konstruktory konwersji zazwyczaj przyjmują dokładnie jeden argument, który jest typu źródłowego. Jednak konstruktor konwersji można określić dodatkowe parametry, jeśli każdy dodatkowy parametr ma wartość domyślną. Typ źródła pozostaje typem pierwszego parametru.

- Konstruktory konwersji, podobnie jak wszystkie konstruktory, nie określają typu zwracanego. Określenie typu zwracanego w deklaracji jest błędem.

- Konstruktory konwersji mogą być jawne.

### <a name="explicit-conversion-constructors"></a>Jawne konstruktory konwersji

Deklarując konstruktora konwersji **jako jawne,** może służyć tylko do wykonywania bezpośredniego inicjowania obiektu lub do wykonywania jawnego rzutowania. Zapobiega to funkcjom, które akceptują argument typu klasy, również niejawnie akceptują argumenty typu źródłowego konstruktora konwersji i zapobiega inicjowaniu typu klasy z wartości typu źródłowego. W poniższym przykładzie pokazano, jak zdefiniować konstruktor konwersji jawne i wpływ ma na jaki kod jest dobrze sformułowany.

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

W tym przykładzie należy zauważyć, że nadal można użyć konstruktora konwersji jawne do wykonywania bezpośredniego inicjowania `payable`. Jeśli zamiast tego były do `Money payable = 79.99;`kopiowania i inicjowania , byłoby błędem. Pierwsze wywołanie `display_balance` jest nienaruszone, ponieważ argument jest poprawnym typem. Drugie wywołanie `display_balance` jest błędem, ponieważ konstruktor konwersji nie może służyć do wykonywania konwersji niejawnych. Trzecie wywołanie `display_balance` jest legalne ze `Money`względu na jawne rzutowanie do , ale należy zauważyć, że kompilator nadal pomógł zakończyć rzutowanie, wstawiając niejawne rzutowanie z **float** do **double**.

Chociaż wygoda zezwalania na niejawne konwersje może być kusząca, może to spowodować trudne do znalezienia błędy. Zasadą jest, aby wszystkie konstruktory konwersji jawne, z wyjątkiem sytuacji, gdy masz pewność, że chcesz określonej konwersji występuje niejawnie.

## <a name="conversion-functions"></a><a name="ConvFunc"></a>Funkcje konwersji

Funkcje konwersji definiują konwersje z typu zdefiniowanego przez użytkownika na inne typy. Funkcje te są czasami określane jako "operatory rzutowania", ponieważ, wraz z konstruktorami konwersji, są wywoływane, gdy wartość jest rzutowy na inny typ. W poniższym przykładzie pokazano funkcję konwersji, która `Money`konwertuje z typu zdefiniowanego przez użytkownika, na typ wbudowany, **double:**

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

Należy zauważyć, `amount` że zmienna elementu członkowskiego jest prywatna i że publiczna `amount`funkcja konwersji do typu **double** jest wprowadzana tylko po to, aby zwrócić wartość . W funkcji `display_balance`konwersja niejawna występuje, gdy wartość jest przesyłana strumieniowo do standardowego `balance` wyjścia przy użyciu operatora wstawiania strumienia `<<`. Ponieważ dla `Money`typu zdefiniowanego przez użytkownika nie zdefiniowano operatora wstawiania strumienia, ale istnieje jeden dla wbudowanego typu **double,** kompilator może użyć funkcji konwersji od `Money` do **podwojenia,** aby spełnić operator wstawiania strumienia.

Funkcje konwersji są dziedziczone przez klasy pochodne. Funkcje konwersji w klasie pochodnej zastępują tylko dziedziczoną funkcję konwersji podczas konwersji na dokładnie ten sam typ. Na przykład zdefiniowana przez użytkownika funkcja konwersji operatora klasy pochodnej **int** nie zastępuje ani nawet nie wpływa na zdefiniowaną przez użytkownika funkcję konwersji **operatora**klasy podstawowej, nawet jeśli standardowe konwersje definiują relację konwersji między **int** a **short**.

### <a name="declaring-conversion-functions"></a>Deklarowanie funkcji konwersji

Następujące reguły mają zastosowanie do deklarowania funkcji konwersji:

- Typ docelowy konwersji musi być zadeklarowany przed deklaracją funkcji konwersji. Klasy, struktury, wyliczenia i typedefs nie można zadeklarować w deklaracji funkcji konwersji.

    ```cpp
    operator struct String { char string_storage; }() // illegal
    ```

- Funkcje konwersji nie mają argumentów. Określenie dowolnych parametrów w deklaracji jest błędem.

- Funkcje konwersji mają typ zwracany określony przez nazwę funkcji konwersji, która jest również nazwą typu docelowego konwersji. Określenie typu zwracanego w deklaracji jest błędem.

- Funkcje konwersji mogą być wirtualne.

- Funkcje konwersji mogą być jawne.

### <a name="explicit-conversion-functions"></a>Jawne funkcje konwersji

Gdy funkcja konwersji jest zadeklarowana jako jawna, może służyć tylko do wykonywania jawnego rzutowania. Zapobiega to funkcjom, które akceptują argument typu docelowego funkcji konwersji, również niejawnie akceptują argumenty typu klasy i zapobiega inicjowaniu przez wystąpienia typu docelowego z wartością typu klasy. W poniższym przykładzie pokazano, jak zdefiniować jawną funkcję konwersji i wpływ, jaki ma na jaki kod jest dobrze sformułowany.

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

W tym miejscu operator funkcji konwersji **dwukrotnie** został jawny i jawne `display_balance` rzutowania do typu **double** został wprowadzony w funkcji do wykonywania konwersji. Jeśli ta rzutowanie zostały pominięte, kompilator nie będzie w `<<` stanie `Money` zlokalizować odpowiedni operator wstawiania strumienia dla typu i wystąpiłby błąd.
