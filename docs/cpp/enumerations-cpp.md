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
ms.openlocfilehash: 2a1b3d33534887568c6a55e320e77e0a018cafff
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366320"
---
# <a name="enumerations-c"></a>Wyliczenia (C++)

Wyliczenie jest typem zdefiniowanym przez użytkownika, który składa się z zestawu nazwanych stałych integralnych, które są znane jako wyliczacze.

> [!NOTE]
> W tym artykule omówiono typ **wyliczenia** języka iso standard C++ i typ **klasy wyliczenia** o określonym zakresie (lub silnie typizowane), który został wprowadzony w języku C++11. Aby uzyskać informacje na temat **klasy wyliczenia publicznego** lub prywatnych typów **klas wyliczenia** w językach C++/CLI i C++/CX, zobacz [klasę wyliczenia](../extensions/enum-class-cpp-component-extensions.md).

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

*Identyfikator*<br/>
Nazwa typu nadana wyliczenia.

*Typu*<br/>
Podstawowy typ wyliczaczy; wszystkie wyliczacze mają ten sam typ podstawowy. Może być dowolny typ integralny.

*wyliczeń*<br/>
Oddzielona przecinkami lista wyliczaczy w wyliczenia. Każdy wyliczacz lub nazwa zmiennej w zakresie musi być unikatowa. Jednak wartości mogą być duplikowane. W nieskopowym wyliczenia zakres jest otaczającym zakresem; w wyliczenia o określonym zakresie zakres jest samą *listą wyliczenia.*  W wyliczenia o określonym zakresie lista może być pusta, co w efekcie definiuje nowy typ integralny.

*class*<br/>
Za pomocą tego słowa kluczowego w deklaracji, należy określić wyliczenia jest o zakresie i *identyfikator* musi być podana. Można również użyć słowa kluczowego **struct** zamiast **klasy**, ponieważ są one semantycznie równoważne w tym kontekście.

## <a name="enumerator-scope"></a>Zakres wyliczenia

Wyliczenie zawiera kontekst do opisania zakresu wartości, które są reprezentowane jako stałe nazwane i są również nazywane wyliczaczy. W oryginalnych typach wyliczeń C i C++ niekwalifikowane wyliczenia są widoczne w całym zakresie, w którym wyliczeń jest zadeklarowany. W wyliczonych o określonym zakresie nazwa wyliczenia musi być kwalifikowana przez nazwę typu wyliczenia. Poniższy przykład pokazuje tę podstawową różnicę między dwoma rodzajami wyliczenia:

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

Każda nazwa w wyliczeniu jest przypisana wartość całkowita, która odpowiada jego miejsce w kolejności wartości w wyliczeniu. Domyślnie pierwsza wartość jest przypisana 0, następna jest przypisana 1 i tak dalej, ale można jawnie ustawić wartość wylicznika, jak pokazano poniżej:

```cpp
enum Suit { Diamonds = 1, Hearts, Clubs, Spades };
```

Wyliczacza `Diamonds` jest przypisana `1`wartość . Kolejne wyliczenia, jeśli nie są podane jawne wartości, otrzymują wartość poprzedniego wylicznika plus jeden. W poprzednim `Hearts` przykładzie, będzie miał `Clubs` wartość 2, miałby 3 i tak dalej.

Każdy wyliczyć jest traktowany jako stała i musi mieć unikatową nazwę w zakresie, w którym **wyliczenia** jest zdefiniowany (dla wyliczenia bezscoped) lub w samej **wyliczenia** (dla wyliczenia o określonym zakresie). Wartości podane do nazw nie muszą być unikatowe. Na przykład, jeśli deklaracja wyliczenia nieskopowego `Suit` jest taka:

```cpp
enum Suit { Diamonds = 5, Hearts, Clubs = 4, Spades };
```

Następnie wartości `Diamonds`, `Hearts` `Clubs`, `Spades` i są 5, 6, 4 i 5, odpowiednio. Należy zauważyć, że 5 jest używany więcej niż jeden raz; jest to dozwolone, nawet jeśli może nie być zamierzone. Reguły te są takie same dla wyliczenia o określonym zakresie.

## <a name="casting-rules"></a>Zasady rzucania

Stałe wyliczone bez wartości mogą być niejawnie konwertowane **na int,** ale **int** nigdy nie jest niejawnie konwertowane na wartość wyliczenia. Poniższy przykład pokazuje, co się `hand` stanie, jeśli `Suit`spróbujesz przypisać wartość, która nie jest:

```cpp
int account_num = 135692;
Suit hand;
hand = account_num; // error C2440: '=' : cannot convert from 'int' to 'Suit'
```

Rzutowanie jest wymagane do konwersji **int** do wylicznika o określonym lub niezakskopowym. Można jednak podwyższyć wartość wyliczenia nieskopowego do wartości całkowitej bez rzutowania.

```cpp
int account_num = Hearts; //OK if Hearts is in a unscoped enum
```

Korzystanie z konwersji niejawnych w ten sposób może prowadzić do niezamierzonych skutków ubocznych. Aby wyeliminować błędy programowania związane z wyliczeniami nieskopowanymi, wartości wyliczenia o określonym zakresie są silnie wpisywane. Wyliczenia o zakresie muszą być kwalifikowane przez nazwę typu wyliczenia (identyfikator) i nie mogą być niejawnie konwertowane, jak pokazano w poniższym przykładzie:

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

Należy zauważyć, `hand = account_num;` że wiersz nadal powoduje błąd, który występuje z wyliczeniami nieskopowymi, jak pokazano wcześniej. Jest to dozwolone z jawnym rzutem. Jednak z wyliczeniami o określonym zakresie próba `account_num = Suit::Hearts;`konwersji w następnej instrukcji, nie jest już dozwolona bez jawnego rzutowania.

## <a name="enums-with-no-enumerators"></a><a name="no_enumerators"></a>Wyliczenia bez wyliczaczy

**Visual Studio 2017 w wersji 15.3 i nowszej** (dostępne z [/std:c++17):](../build/reference/std-specify-language-standard-version.md)Definiując wyliczenia (regularne lub objęte zakresem) z jawnym typem podstawowym i bez wyliczaczy, można w efekcie wprowadzić nowy typ integralną, który nie ma niejawnej konwersji do innego typu. Za pomocą tego typu zamiast jego wbudowany typ podstawowy, można wyeliminować możliwość subtelne błędy spowodowane przez niezamierzone konwersje niejawne.

```cpp
enum class byte : unsigned char { };
```

Nowy typ jest dokładną kopią typu źródłowego i dlatego ma tę samą konwencję wywoływania, co oznacza, że może być używany w systemach ABI bez żadnych kar wydajności. Rzutowanie nie jest wymagane, gdy zmienne typu są inicjowane przy użyciu inicjowania listy bezpośredniej. W poniższym przykładzie pokazano, jak zainicjować wyliczenia bez wyliczaczy w różnych kontekstach:

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

[C Deklaracje wyliczenia](../c-language/c-enumeration-declarations.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)
