---
title: struktura (C++)
ms.date: 11/04/2016
f1_keywords:
- struct_cpp
helpviewer_keywords:
- struct constructors
ms.assetid: 3c6ba273-e248-4ff1-8c69-d2abcf1263c6
ms.openlocfilehash: e9ffd30dd0017e912fd7c196e2d3f0e987fb0810
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62330586"
---
# <a name="struct-c"></a>struktura (C++)

**Struktury** — słowo kluczowe definiuje typ struktury i/lub zmienną typu struktury.

## <a name="syntax"></a>Składnia

```
[template-spec] struct [ms-decl-spec] [tag [: base-list ]]
{
   member-list
} [declarators];
[struct] tag declarators;
```

#### <a name="parameters"></a>Parametry

*template-spec*<br/>
Opcjonalne specyfikacje szablonu. Aby uzyskać więcej informacji, zobacz [specyfikacje szablonu](templates-cpp.md).

*struct*<br/>
**Struktury** — słowo kluczowe.

*ms-decl-spec*<br/>
Opcjonalna specyfikacja klasy magazynowania. Aby uzyskać więcej informacji, zobacz [__declspec](../cpp/declspec.md) — słowo kluczowe.

*Tag*<br/>
Nazwa typu nadana strukturze. Znacznik staje się słowem zastrzeżonym w obrębie struktury. Znacznik jest opcjonalny. W przypadku pominięcia zostanie zdefiniowana anonimowa struktura. Aby uzyskać więcej informacji, zobacz [anonimowe typy klas](../cpp/anonymous-class-types.md).

*base-list*<br/>
Opcjonalna lista klas lub struktur, z której pochodzą składowe tej struktury. Zobacz [klasy podstawowej](../cpp/base-classes.md) Aby uzyskać więcej informacji. Każda podstawowa nazwy klasy lub struktury może być poprzedzona przez specyfikator dostępu ([publicznych](../cpp/public-cpp.md), [prywatnej](../cpp/private-cpp.md), [chronione](../cpp/protected-cpp.md)) i [wirtualnego](../cpp/virtual-cpp.md) słowo kluczowe. Zobacz tabelę dostępu do elementu członkowskiego w [kontrolowanie dostępu do składowych klasy](member-access-control-cpp.md) Aby uzyskać więcej informacji.

*Lista elementów członkowskich*<br/>
Lista składników struktury. Zapoznaj się [omówienie składowej klasy](../cpp/class-member-overview.md) Aby uzyskać więcej informacji. Jedyną różnicą jest to, że **struktury** jest używana zamiast **klasy**.

*deklaratory*<br/>
Lista deklaratora określająca nazwy struktury. Listy deklaratorów deklarują jedno lub więcej wystąpień typu struktury. Deklaratory mogą zawierać listy inicjatorów, jeśli wszystkie elementy członkowskie danych struktury są **publicznych**. Listy inicjatorów są wspólne w strukturach, ponieważ elementy członkowskie danych są **publicznych** domyślnie.  Zobacz [Przegląd Deklaratorów](../cpp/overview-of-declarators.md) Aby uzyskać więcej informacji.

## <a name="remarks"></a>Uwagi

Typ struktury jest zdefiniowanym przez użytkownika typem złożonym. Składa się z pól lub elementów członkowskich, które mogą mieć różne typy.

W języku C++ struktura jest taka sama jak klasa z tą różnicą, że jej składowe są **publicznych** domyślnie.

Aby uzyskać informacje dotyczące zarządzanych klas i struktur w C++sposób niezamierzony, zobacz [klas i struktur](../extensions/classes-and-structs-cpp-component-extensions.md).

## <a name="using-a-structure"></a>Korzystanie ze struktury

W języku C, trzeba jawnie użyć **struktury** — słowo kluczowe, aby zadeklarować strukturę. W języku C++, nie trzeba używać **struktury** — słowo kluczowe po zdefiniowaniu typu.

Istnieje opcja zadeklarowania zmiennych, kiedy typ struktury jest definiowany, przez umieszczenie jednej lub więcej nazw zmiennych, oddzielonych przecinkami, między zamykającym nawiasem klamrowym i średnikiem.

Zmienne struktury mogą być inicjowane. Inicjowanie dla każdej zmiennej musi być ujęte w nawiasy klamrowe.

Aby uzyskać powiązane informacje, zobacz [klasy](../cpp/class-cpp.md), [Unii](../cpp/unions.md), i [wyliczenia](../cpp/enumerations-cpp.md).

## <a name="example"></a>Przykład

```cpp
#include <iostream>
using namespace std;

struct PERSON {   // Declare PERSON struct type
    int age;   // Declare member types
    long ss;
    float weight;
    char name[25];
} family_member;   // Define object of type PERSON

struct CELL {   // Declare CELL bit field
    unsigned short character  : 8;  // 00000000 ????????
    unsigned short foreground : 3;  // 00000??? 00000000
    unsigned short intensity  : 1;  // 0000?000 00000000
    unsigned short background : 3;  // 0???0000 00000000
    unsigned short blink      : 1;  // ?0000000 00000000
} screen[25][80];       // Array of bit fields

int main() {
    struct PERSON sister;   // C style structure declaration
    PERSON brother;   // C++ style structure declaration
    sister.age = 13;   // assign values to members
    brother.age = 7;
    cout << "sister.age = " << sister.age << '\n';
    cout << "brother.age = " << brother.age << '\n';

    CELL my_cell;
    my_cell.character = 1;
    cout << "my_cell.character = " << my_cell.character;
}
// Output:
// sister.age = 13
// brother.age = 7
// my_cell.character = 1
```
