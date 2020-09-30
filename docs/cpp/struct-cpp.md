---
title: struktura (C++)
ms.date: 11/04/2016
f1_keywords:
- struct_cpp
helpviewer_keywords:
- struct constructors
ms.assetid: 3c6ba273-e248-4ff1-8c69-d2abcf1263c6
ms.openlocfilehash: d0092cf107159f4c84b431f5eeae130df64dc835
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91507458"
---
# <a name="struct-c"></a>struktura (C++)

**`struct`** Słowo kluczowe definiuje typ struktury i/lub zmienną typu struktury.

## <a name="syntax"></a>Składnia

```
[template-spec] struct [ms-decl-spec] [tag [: base-list ]]
{
   member-list
} [declarators];
[struct] tag declarators;
```

#### <a name="parameters"></a>Parametry

*szablon — Specyfikacja*<br/>
Opcjonalne specyfikacje szablonu. Aby uzyskać więcej informacji, zobacz [specyfikacje szablonu](templates-cpp.md).

*konstrukcja*<br/>
**`struct`** Słowo kluczowe.

*MS-decl-spec*<br/>
Opcjonalna specyfikacja klasy magazynowania. Aby uzyskać więcej informacji, zapoznaj się ze słowem kluczowym [__declspec](../cpp/declspec.md) .

*tag*<br/>
Nazwa typu nadana strukturze. Znacznik staje się słowem zastrzeżonym w obrębie struktury. Znacznik jest opcjonalny. W przypadku pominięcia zostanie zdefiniowana anonimowa struktura. Aby uzyskać więcej informacji, zobacz [anonimowe typy klas](../cpp/anonymous-class-types.md).

*Lista podstawowa*<br/>
Opcjonalna lista klas lub struktur, z której pochodzą składowe tej struktury. Aby uzyskać więcej informacji, zobacz [klasy bazowe](../cpp/base-classes.md) . Każda nazwa klasy bazowej lub struktury może być poprzedzona przez specyfikator dostępu ([Public](../cpp/public-cpp.md), [Private](../cpp/private-cpp.md), [Protected](../cpp/protected-cpp.md)) i [wirtualne](../cpp/virtual-cpp.md) słowo kluczowe. Aby uzyskać więcej informacji, zobacz tabelę dostępu do elementów członkowskich w temacie [Kontrola dostępu do składowych klasy](member-access-control-cpp.md) .

*Lista elementów członkowskich*<br/>
Lista składników struktury. Aby uzyskać więcej informacji, zapoznaj się z [omówieniem składowej klasy](../cpp/class-member-overview.md) . Jedyną różnicą jest to, że **`struct`** jest używana zamiast **`class`** .

*Deklaratory*<br/>
Lista deklaratora określająca nazwy struktury. Listy deklaratorów deklarują jedno lub więcej wystąpień typu struktury. Deklaratory może zawierać listę inicjatorów, jeśli wszystkie elementy członkowskie danych struktury są **`public`** . Listy inicjatorów są wspólne w strukturach, ponieważ elementy członkowskie danych są **`public`** domyślnie.  Aby uzyskać więcej informacji [, zobacz Omówienie Deklaratory](./declarations-and-definitions-cpp.md) .

## <a name="remarks"></a>Uwagi

Typ struktury jest zdefiniowanym przez użytkownika typem złożonym. Składa się z pól lub elementów członkowskich, które mogą mieć różne typy.

W języku C++ struktura jest taka sama jak Klasa, z tą różnicą, że jej członkowie są **`public`** domyślnie.

Aby uzyskać informacje dotyczące zarządzanych klas i struktur w języku C++/CLI, zobacz [klasy i struktury](../extensions/classes-and-structs-cpp-component-extensions.md).

## <a name="using-a-structure"></a>Korzystanie ze struktury

W języku C, należy jawnie użyć **`struct`** słowa kluczowego, aby zadeklarować strukturę. W języku C++ nie trzeba używać **`struct`** słowa kluczowego po zdefiniowaniu typu.

Istnieje opcja zadeklarowania zmiennych, kiedy typ struktury jest definiowany, przez umieszczenie jednej lub więcej nazw zmiennych, oddzielonych przecinkami, między zamykającym nawiasem klamrowym i średnikiem.

Zmienne struktury mogą być inicjowane. Inicjowanie dla każdej zmiennej musi być ujęte w nawiasy klamrowe.

Aby uzyskać powiązane informacje, zobacz [Class](../cpp/class-cpp.md), [Union](../cpp/unions.md)i [enum](../cpp/enumerations-cpp.md).

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
