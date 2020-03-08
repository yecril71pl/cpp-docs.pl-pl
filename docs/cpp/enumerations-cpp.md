---
title: Wyliczenia (C++)
ms.date: 06/01/2018
f1_keywords:
- enum_cpp
helpviewer_keywords:
- declarations, enumerations
- enumerators, declaring
- enum keyword [C++]
- named constants, enumeration declarations
- declaring enumerations
ms.assetid: 081829db-5dca-411e-a53c-bffef315bcb3
ms.openlocfilehash: caec9ea7ac5482ff23b73676a3fd7b3d25ad293f
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78884166"
---
# <a name="enumerations-c"></a>Wyliczenia (C++)

Wyliczenie jest typem zdefiniowanym przez użytkownika, który składa się z zestawu nazwanych stałych, które są znane jako Numeratory.

> [!NOTE]
>  W tym artykule omówiono typ C++ **WYLICZENIA** języka standardowego ISO oraz typ **klasy wyliczeniowej** z określonym zakresem (lub z jednoznacznie określonymi typami) wprowadzony w języku c++ 11. Aby uzyskać informacje o **publicznej klasie wyliczenia** lub **prywatnych typach klas wyliczeniowych** C++w C++/CLI i/CX, zobacz [enum Class](../extensions/enum-class-cpp-component-extensions.md).

## <a name="syntax"></a>Składnia

```
// unscoped enum:
enum [identifier] [: type]
{enum-list};

// scoped enum:
enum [class|struct]
[identifier] [: type]
{enum-list};
```

```cpp
// Forward declaration of enumerations  (C++11):
enum A : int; // non-scoped enum must have type specified
enum class B; // scoped enum defaults to int but ...
enum class C : short;  // ... may have any integral underlying type
```

## <a name="parameters"></a>Parametry

*identyfikatora*<br/>
Nazwa typu nadana wyliczeniem.

*type*<br/>
Typ podstawowy modułów wyliczających; wszystkie Numeratory mają ten sam typ podstawowy. Może być dowolnym typem całkowitym.

*Lista wyliczeniowa*<br/>
Rozdzielana przecinkami lista modułów wyliczających w wyliczeniu. Każdy moduł wyliczający lub nazwa zmiennej w zakresie musi być unikatowy. Jednak wartości mogą być zduplikowane. W wyliczeniu nieobjętym zakresem zakres jest otaczającym zakresem; w wyliczeniu z zakresem zakres jest sam *listy wyliczeniowej* .  W wyliczeniu z zakresem lista może być pusta, która w efekcie definiuje nowy typ całkowity.

*class*<br/>
Za pomocą tego słowa kluczowego w deklaracji należy określić zakres wyliczenia i należy podać *Identyfikator* . Można również użyć słowa kluczowego **struct** zamiast **klasy**, ponieważ są one semantycznie równoważne w tym kontekście.

## <a name="enumerator-scope"></a>Zakres modułu wyliczającego

Wyliczenie zawiera kontekst do opisania zakresu wartości, które są reprezentowane jako nazwane stałe i są również nazywane modułami wyliczającymi. W oryginalnych typach C i C++ enum, niekwalifikowane moduły wyliczające są widoczne w całym zakresie, w którym jest zadeklarowane Wyliczenie. W przypadku typów wyliczeniowych Nazwa modułu wyliczającego musi być kwalifikowana przez nazwę typu wyliczenia. Poniższy przykład ilustruje tę podstawową różnicę między dwoma rodzajami wyliczeń:

```cpp
namespace CardGame_Scoped
{
    enum class Suit { Diamonds, Hearts, Clubs, Spades };

    void PlayCard(Suit suit)
    {
        if (suit == Suit::Clubs) // Enumerator must be qualified by enum type
        { /*...*/}
    }
}

namespace CardGame_NonScoped
{
    enum Suit { Diamonds, Hearts, Clubs, Spades };

    void PlayCard(Suit suit)
    {
        if (suit == Clubs) // Enumerator is visible without qualification
        { /*...*/
        }
    }
}
```

Każda nazwa w wyliczeniu ma przypisaną całkowitą wartość, która odpowiada jej miejscu w kolejności wartości w wyliczeniu. Domyślnie pierwsza wartość jest przypisywana 0, następna z nich jest przypisana 1 itd., ale można jawnie ustawić wartość modułu wyliczającego, jak pokazano poniżej:

```cpp
enum Suit { Diamonds = 1, Hearts, Clubs, Spades };
```

`Diamonds` modułu wyliczającego jest przypisana `1`wartość. Kolejne Numeratory, jeśli nie otrzymają jawnej wartości, otrzymają wartość poprzedniego modułu wyliczającego plus jeden. W poprzednim przykładzie `Hearts` będzie mieć wartość 2, `Clubs` byłoby 3 i tak dalej.

Każdy moduł wyliczający jest traktowany jako stała i musi mieć unikatową nazwę w zakresie, w którym zdefiniowano **Wyliczenie** (dla typów wyliczeniowych nieobjętych zakresem) lub w obrębie samego **wyliczenia** (dla typów wyliczeniowych w zakresie). Wartości nadane nazw nie muszą być unikatowe. Na przykład jeśli deklaracja wyliczenia nieobjętego zakresem `Suit` jest taka:

```cpp
enum Suit { Diamonds = 5, Hearts, Clubs = 4, Spades };
```

Następnie wartości `Diamonds`, `Hearts`, `Clubs`i `Spades` są odpowiednio 5, 6, 4 i 5. Zauważ, że 5 jest używany więcej niż jeden raz; jest to dozwolone, chociaż może nie być zamierzone. Te reguły są takie same dla typów wyliczeniowych w zakresie.

## <a name="casting-rules"></a>Reguły rzutowania

Stałe wyliczeniowe nieobjęte zakresem mogą być niejawnie konwertowane na **typ int**, ale **int** nigdy nie jest możliwa do niejawnego konwersji na wartość enum. W poniższym przykładzie pokazano, co się dzieje w przypadku próby przypisania `hand` wartości, która nie jest `Suit`:

```cpp
int account_num = 135692;
Suit hand;
hand = account_num; // error C2440: '=' : cannot convert from 'int' to 'Suit'
```

Rzutowanie jest wymagane do przekonwertowania **int** na moduł wyliczający w zakresie lub w zakresie nienależącym do zakresu. Można jednak podwyższyć poziom modułu wyliczającego nieobjętego zakresem do wartości całkowitej bez rzutowania.

```cpp
int account_num = Hearts; //OK if Hearts is in a unscoped enum
```

Użycie niejawnych konwersji w ten sposób może prowadzić do niezamierzonych efektów ubocznych. Aby pomóc wyeliminować błędy programistyczne związane z wyliczeniem nienależącym do zakresu, wartości wyliczeniowe w zakresie są jednoznacznie wpisywane. Moduł wyliczający w zakresie musi być kwalifikowana przez nazwę typu wyliczenia (identyfikator) i nie może być niejawnie konwertowany, jak pokazano w następującym przykładzie:

```cpp
namespace ScopedEnumConversions
{
    enum class Suit { Diamonds, Hearts, Clubs, Spades };

    void AttemptConversions()
    {
        Suit hand;
        hand = Clubs; // error C2065: 'Clubs' : undeclared identifier
        hand = Suit::Clubs; //Correct.
        int account_num = 135692;
        hand = account_num; // error C2440: '=' : cannot convert from 'int' to 'Suit'
        hand = static_cast<Suit>(account_num); // OK, but probably a bug!!!

        account_num = Suit::Hearts; // error C2440: '=' : cannot convert from 'Suit' to 'int'
        account_num = static_cast<int>(Suit::Hearts); // OK
    }
}
```

Zauważ, że wiersz `hand = account_num;` nadal powoduje błąd występujący z wyliczeniem nieobjętym zakresem, jak pokazano wcześniej. Jest to dozwolone w przypadku jawnego rzutowania. Jednak w przypadku typów wyliczeniowych w zakresie próba konwersji w następnej instrukcji `account_num = Suit::Hearts;`nie jest już dozwolona bez jawnego rzutowania.

## <a name="no_enumerators"></a>Wyliczenia bez modułów wyliczających

**Visual Studio 2017 w wersji 15,3 i nowszej** (dostępne w [/std: c++ 17](../build/reference/std-specify-language-standard-version.md)): przez zdefiniowanie wyliczenia (regularnego lub w zakresie) z jawnym typem podstawowym i brak modułów wyliczających, można wprowadzić nowy typ całkowity, który nie ma jawnej konwersji na inny typ. Przy użyciu tego typu, a nie wbudowanego typu podstawowego, można wyeliminować potencjalne błędy powodowane przez przypadkowe konwersje niejawne.

```cpp
enum class byte : unsigned char { };
```

Nowy typ jest dokładną kopią typu bazowego i dlatego ma tę samą konwencję wywołania, co oznacza, że może być używany przez interfejsy ABI bez żadnej kary wydajności. Nie jest wymagane rzutowanie, gdy zmienne typu są inicjowane przy użyciu inicjalizacji listy bezpośredniej. Poniższy przykład pokazuje, jak zainicjować wyliczenia bez modułów wyliczających w różnych kontekstach:

```cpp
enum class byte : unsigned char { };

enum class E : int { };
E e1{ 0 };
E e2 = E{ 0 };

struct X
{
    E e{ 0 };
    X() : e{ 0 } { }
};

E* p = new E{ 0 };

void f(E e) {};

int main()
{
    f(E{ 0 });
    byte i{ 42 };
    byte j = byte{ 42 };

    // unsigned char c = j; // C2440: 'initializing': cannot convert from 'byte' to 'unsigned char'
    return 0;
}
```

## <a name="see-also"></a>Zobacz też

[Deklaracje modułów wyliczających języka C](../c-language/c-enumeration-declarations.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)