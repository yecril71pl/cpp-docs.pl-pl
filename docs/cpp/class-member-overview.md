---
title: Omówienie elementu członkowskiego klasy
ms.date: 11/04/2016
helpviewer_keywords:
- members [C++], types of class members
- members [C++]
- class members [C++], types of
- class members
ms.assetid: 8802cfa9-705d-4f37-acde-245d6838010c
ms.openlocfilehash: cb978434707a9a7808b3388fc541ce4e0d996b0f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366674"
---
# <a name="class-member-overview"></a>Omówienie elementu członkowskiego klasy

Klasa lub struktura składa się z jej elementów członkowskich. Praca, która wykonuje klasa jest wykonywana przez jego funkcje członkowskie. Stan, który utrzymuje jest przechowywany w jego elementów członkowskich danych. Inicjowanie elementów członkowskich odbywa się przez konstruktorów i oczyszczania pracy, takich jak zwalnianie pamięci i zwalnianie zasobów odbywa się przez destruktorów. W języku C++ 11 i nowszych elementy członkowskie danych można (i zwykle powinny) być inicjowane w punkcie deklaracji.

## <a name="kinds-of-class-members"></a>Rodzaje członków klasy

Pełna lista kategorii członków jest następująca:

- [Specjalne funkcje członkowskie](special-member-functions.md).

- [Omówienie funkcji członkowskich](overview-of-member-functions.md).

- [Elementy członkowskie danych,](static-members-cpp.md) w tym typy wbudowane i inne typy zdefiniowane przez użytkownika.

- Operatory

- [Deklaracje klas zagnieżdżonych](nested-class-declarations.md) i.)

- [Unie](unions.md)

- [Wyliczenia](../cpp/enumerations-cpp.md).

- [Pola bitowe](../cpp/cpp-bit-fields.md).

- [Przyjaciele](../cpp/friend-cpp.md).

- [Aliasy i typedefs](../cpp/aliases-and-typedefs-cpp.md).

    > [!NOTE]
    >  Elementy zaprzyjaźnione są ujęte w powyższej liście, ponieważ są zawarte w deklaracji klasy. Jednak nie są one prawdziwymi składowymi klasy, ponieważ nie są one w zakresie tej klasy.

## <a name="example-class-declaration"></a>Przykładowa deklaracja klasy

W poniższym przykładzie przedstawiono deklarację klasy prostej:

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

## <a name="member-accessibility"></a>Dostępność dla członków

Członkowie klasy są zadeklarowane na liście elementów członkowskich. Lista elementów członkowskich klasy może być podzielona na dowolną liczbę sekcji **prywatnych,** **chronionych** i **publicznych** przy użyciu słów kluczowych znanych jako specyfikatory dostępu.  Dwukropek **:** musi być zgodny ze specyfikatorem dostępu.  Sekcje nie muszą być ciągłe, to znaczy dowolne z tych słów kluczowych mogą wystąpić kilka razy na liście elementów członkowskich.  Słowo kluczowe wyznacza dostęp do wszystkich elementów członkowskich aż do następnego specyfikatora dostępu lub nawiasu zamykającego. Aby uzyskać więcej informacji, zobacz [Kontrola dostępu do członków (C++)](../cpp/member-access-control-cpp.md).

## <a name="static-members"></a>Statyczne składowe

Element członkowski danych może być zadeklarowany jako statyczny, co oznacza, że wszystkie obiekty klasy mają dostęp do tej samej kopii. Funkcja elementu członkowskiego może być zadeklarowana jako statyczna, w którym to przypadku może uzyskać dostęp tylko do statycznych elementów członkowskich klasy (i nie ma *tego* wskaźnika). Aby uzyskać więcej informacji, zobacz [Elementy członkowskie danych statycznych](../cpp/static-members-cpp.md).

## <a name="special-member-functions"></a>Specjalne funkcje składowe

Specjalne funkcje członkowskie są funkcje, które są automatycznie dostarczane przez kompilator, jeśli nie określisz je w kodzie źródłowym.

1. Konstruktor domyślny.

1. Konstruktor kopiujący

1. **(C++11)** Konstruktor przenoszenia

1. Operator przypisania kopiowania

1. **(C++11)** Przenoszenie operatora przydziału

1. Destruktor

Aby uzyskać więcej informacji, zobacz [Specjalne funkcje członkowskie](../cpp/special-member-functions.md).

## <a name="memberwise-initialization"></a>Inicjowanie członkowskie

W języku C++ 11 i nowszych niestatycznych deklaratorów członkowskich może zawierać inicjatorów.

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

Jeśli element członkowski jest przypisany wartość w konstruktorze, ta wartość zastępuje wartość, z którą element członkowski został zainicjowany w punkcie deklaracji.

Istnieje tylko jedna kopia udostępnionych danych statycznych składowych dla wszystkich obiektów typu danej klasy. Dane statyczne członków muszą być zdefiniowane i mogą być zainicjowane w zakresie pliku. (Aby uzyskać więcej informacji na temat elementów członkowskich danych statycznych, zobacz [Elementy członkowskie danych statycznych](../cpp/static-members-cpp.md).) W poniższym przykładzie pokazano, jak wykonać te inicjalizowania:

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
> Nazwa klasy `CanInit2` musi znajdować się przed `i`, aby określić, że definiowany `i` jest składową klasy `CanInit2`.

## <a name="see-also"></a>Zobacz też

[Klasy i struktury](../cpp/classes-and-structs-cpp.md)
