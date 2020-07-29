---
title: Omówienie elementu członkowskiego klasy
ms.date: 11/04/2016
helpviewer_keywords:
- members [C++], types of class members
- members [C++]
- class members [C++], types of
- class members
ms.assetid: 8802cfa9-705d-4f37-acde-245d6838010c
ms.openlocfilehash: 02c5593d9fb5e72ee6b398c9637397ab26c9f3f2
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229067"
---
# <a name="class-member-overview"></a>Omówienie elementu członkowskiego klasy

Klasa lub struktura składa się z jej elementów członkowskich. Prace, które Klasa jest wykonywana przez jej funkcje składowe. Stan, w którym utrzymuje się, jest przechowywany w jego elementach członkowskich danych. Inicjalizacja elementów członkowskich jest wykonywana przez konstruktory, a zadania oczyszczania, takie jak zwalnianie pamięci i zwalnianie zasobów, są wykonywane przez destruktory. W języku C++ 11 i nowszych składowe danych mogą (i zazwyczaj powinny) być inicjowane w punkcie deklaracji.

## <a name="kinds-of-class-members"></a>Rodzaje elementów członkowskich klasy

Pełna lista kategorii składowych jest następująca:

- [Specjalne funkcje członkowskie](special-member-functions.md).

- [Przegląd funkcji Członkowskich](overview-of-member-functions.md).

- [Składowe danych](static-members-cpp.md) , w tym typy wbudowane i inne typy zdefiniowane przez użytkownika.

- Operatory

- [Zagnieżdżone deklaracje klas](nested-class-declarations.md) i.)

- [Unie](unions.md)

- [Wyliczenia](../cpp/enumerations-cpp.md).

- [Pola bitowe](../cpp/cpp-bit-fields.md).

- [Przyjaciele](../cpp/friend-cpp.md).

- [Aliasy i definicje typów](../cpp/aliases-and-typedefs-cpp.md).

    > [!NOTE]
    >  Elementy zaprzyjaźnione są ujęte w powyższej liście, ponieważ są zawarte w deklaracji klasy. Jednak nie są one prawdziwymi składowymi klasy, ponieważ nie są one w zakresie tej klasy.

## <a name="example-class-declaration"></a>Przykładowa deklaracja klasy

W poniższym przykładzie przedstawiono prostą deklarację klasy:

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

Elementy członkowskie klasy są deklarowane na liście składowych. Lista składowych klasy może być podzielona na dowolną liczbę **`private`** **`protected`** i **`public`** sekcje przy użyciu słów kluczowych znanych jako specyfikatory dostępu.  Dwukropek **:** musi być zgodny ze specyfikatorem dostępu.  Sekcje nie muszą być ciągłe, to znaczy dowolne z tych słów kluczowych mogą wystąpić kilka razy na liście elementów członkowskich.  Słowo kluczowe wyznacza dostęp do wszystkich elementów członkowskich aż do następnego specyfikatora dostępu lub nawiasu zamykającego. Aby uzyskać więcej informacji, zobacz [element członkowski Access Control (C++)](../cpp/member-access-control-cpp.md).

## <a name="static-members"></a>Statyczne składowe

Element członkowski danych może być zadeklarowany jako statyczny, co oznacza, że wszystkie obiekty klasy mają dostęp do tej samej kopii. Funkcja członkowska może być zadeklarowana jako statyczna, w takim przypadku można uzyskać dostęp tylko do statycznych elementów członkowskich danych klasy (i nie ma *tego* wskaźnika). Aby uzyskać więcej informacji, zobacz [statyczne elementy członkowskie danych](../cpp/static-members-cpp.md).

## <a name="special-member-functions"></a>Specjalne funkcje składowe

Specjalne funkcje członkowskie są funkcjami, które są automatycznie dostarczane przez kompilator, jeśli nie zostaną określone w kodzie źródłowym.

1. Konstruktor domyślny.

1. Konstruktor kopiujący

1. **(C++ 11)** Konstruktor przenoszenia

1. Operator przypisania kopii

1. **(C++ 11)** Operator przypisania przenoszenia

1. Destruktor

Aby uzyskać więcej informacji, zobacz [specjalne funkcje składowe](../cpp/special-member-functions.md).

## <a name="memberwise-initialization"></a>Inicjalizacja składowych

W języku C++ 11 i nowszych niestatyczne Deklaratory Członkowskie mogą zawierać inicjatory.

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

Jeśli element członkowski ma przypisaną wartość w konstruktorze, ta wartość zastępuje wartość, za pomocą której element członkowski został zainicjowany w punkcie deklaracji.

Istnieje tylko jedna kopia udostępnionych danych statycznych składowych dla wszystkich obiektów typu danej klasy. Dane statyczne członków muszą być zdefiniowane i mogą być zainicjowane w zakresie pliku. (Aby uzyskać więcej informacji na temat statycznych elementów członkowskich danych, zobacz [elementy członkowskie danych statycznych](../cpp/static-members-cpp.md)). Poniższy przykład pokazuje, jak wykonać te inicjalizacje:

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

## <a name="see-also"></a>Zobacz także

[Klasy i struktury](../cpp/classes-and-structs-cpp.md)
