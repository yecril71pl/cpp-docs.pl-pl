---
title: Omówienie składowej klasy | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- members [C++], types of class members
- members [C++]
- class members [C++], types of
- class members
ms.assetid: 8802cfa9-705d-4f37-acde-245d6838010c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6fa736315554786435ec8a8eca453df9de79e2bd
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46033904"
---
# <a name="class-member-overview"></a>Omówienie elementu członkowskiego klasy

Klasa lub Struktura składa się z jej członków. Pracy, która jest klasą odbywa się przez jego elementów członkowskich. Stan, który przechowuje są przechowywane w składowych danych. Inicjowanie elementów członkowskich jest wykonywane przez konstruktory i pracy czyszczenia, taką jak zwalnianie pamięci, a przy zwalnianiu zasobów jest wykonywane przez destruktory. W języku C ++ 11 i nowszych wersjach elementy członkowskie danych można i zwykle należy zostać zainicjowana w punkcie deklaracji.

## <a name="kinds-of-class-members"></a>Rodzaje elementów członkowskich klas

Pełna lista kategorii elementu członkowskiego jest następująca:

- [Specjalne funkcje Członkowskie](special-member-functions.md).

- [Przegląd funkcji Członkowskich](overview-of-member-functions.md).

- [Elementy członkowskie danych](static-members-cpp.md) w tym wbudowane typy i innych użytkowników zdefiniowanych typów.

- Operatory

- [Zagnieżdżone deklaracje klas](nested-class-declarations.md) i.)

- [Unie](unions.md)

- [Wyliczenia](../cpp/enumerations-cpp.md).

- [Pola bitowe](../cpp/cpp-bit-fields.md).

- [Znajomych](../cpp/friend-cpp.md).

- [Aliasy i definicje typów](../cpp/aliases-and-typedefs-cpp.md).

    > [!NOTE]
    >  Elementy zaprzyjaźnione są ujęte w powyższej liście, ponieważ są zawarte w deklaracji klasy. Jednak nie są one prawdziwymi składowymi klasy, ponieważ nie są one w zakresie tej klasy.

## <a name="example-class-declaration"></a>Przykład deklaracji klasy

Poniższy przykład przedstawia deklarację klasy proste:

```cpp
// TestRun.h

class TestRun
{
    // Start member list.

    //The class interface accessible to all callers.
public:
    // Use compiler-generated default constructor:
    TestRun() = default;
    // Don't generate a copy constructor:
    TestRun(const TestRun&) = delete;
    TestRun(std::string name);
    void DoSomething();
    int Calculate(int a, double d);
    virtual ~TestRun();
    enum class State { Active, Suspended };

    // Accessible to this class and derived classes only.
protected:
    virtual void Initialize();
    virtual void Suspend();
    State GetState();

    // Accessible to this class only.
private:
    // Default brace-initialization of instance members:
    State _state{ State::Suspended };
    std::string _testName{ "" };
    int _index{ 0 };

    // Non-const static member:
    static int _instances;
    // End member list.
};

// Define and initialize static member.
int TestRun::_instances{ 0 };
```

## <a name="member-accessibility"></a>Ułatwienia dostępu członków

Elementy członkowskie klasy są zadeklarowane na liście elementów członkowskich. Lista składowych klasy może być podzielona na dowolnej liczbie **prywatnej**, **chronione** i **publicznych** sekcje przy użyciu słów kluczowych, znanych jako specyfikatory dostępu.  Dwukropek **:** musi określać specyfikator dostępu.  Sekcje nie muszą być ciągłe, to znaczy dowolne z tych słów kluczowych mogą wystąpić kilka razy na liście elementów członkowskich.  Słowo kluczowe wyznacza dostęp do wszystkich elementów członkowskich aż do następnego specyfikatora dostępu lub nawiasu zamykającego. Aby uzyskać więcej informacji, zobacz [kontroli dostępu do elementu członkowskiego (C++)](../cpp/member-access-control-cpp.md).

## <a name="static-members"></a>Statyczne elementy członkowskie

Element członkowski danych może być zadeklarowana jako statyczne, co oznacza, że wszystkie obiekty klasy mają dostęp do tej samej kopii. Funkcji składowej może być zadeklarowane jako statyczne, w którym to przypadku dostępne tylko statyczne elementy członkowskie danych klasy (i nie ma *to* wskaźnika). Aby uzyskać więcej informacji, zobacz [statyczne elementy członkowskie danych](../cpp/static-members-cpp.md).

## <a name="special-member-functions"></a>Specjalne funkcje Członkowskie

Specjalne funkcje Członkowskie są funkcje, które są obsługiwane automatycznie przez kompilator, jeśli nie określisz je w kodzie źródłowym.

1. Konstruktor domyślny

1. Konstruktor kopiujący

1. **(C ++ 11)**  Konstruktor przenoszący

1. Operator przypisania kopiowania

1. **(C ++ 11)**  Operator przypisania przenoszenia

1. Destruktor

Aby uzyskać więcej informacji, zobacz [specjalnych funkcji Członkowskich](../cpp/special-member-functions.md).

## <a name="memberwise-initialization"></a>Inicjowanie elementów członkowskich

W języku C ++ 11 i nowszych wersjach niestatycznej składowej deklaratory mogą zawierać inicjatory.

```cpp
class CanInit
{
public:
    long num {7};       // OK in C++11
    int k = 9;          // OK in C++11
    static int i = 9; // Error: must be defined and initialized
                      // outside of class declaration.

    // initializes num to 7 and k to 9
    CanInit(){}

    // overwrites original initialized value of num:
    CanInit(int val) : num(val) {}
};
int main()
{
}
```

Jeśli członek jest przypisywana wartość w konstruktorze, ta wartość zastępuje wartość, z którym element członkowski została zainicjowana w punkcie deklaracji.

Istnieje tylko jedna kopia udostępnionych danych statycznych składowych dla wszystkich obiektów typu danej klasy. Dane statyczne członków muszą być zdefiniowane i mogą być zainicjowane w zakresie pliku. (Aby uzyskać więcej informacji na temat elementów członkowskich danych statycznych, zobacz [statyczne elementy członkowskie danych](../cpp/static-members-cpp.md).) Poniższy przykład pokazuje sposób wykonywania takiego inicjowania:

```cpp
// class_members2.cpp
class CanInit2
{
public:
    CanInit2() {} // Initializes num to 7 when new objects of type
                 //  CanInit are created.
    long     num {7};
    static int i;
    static int j;
};

// At file scope:

// i is defined at file scope and initialized to 15.
// The initializer is evaluated in the scope of CanInit.
int CanInit2::i = 15;

// The right side of the initializer is in the scope
// of the object being initialized
int CanInit2::j = i;
```

> [!NOTE]
>  Nazwa klasy `CanInit2` musi znajdować się przed `i`, aby określić, że definiowany `i` jest składową klasy `CanInit2`.

## <a name="see-also"></a>Zobacz także

[Klasy i struktury](../cpp/classes-and-structs-cpp.md)