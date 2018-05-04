---
title: Struktura (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- struct_cpp
dev_langs:
- C++
helpviewer_keywords:
- struct constructors
ms.assetid: 3c6ba273-e248-4ff1-8c69-d2abcf1263c6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5a9ea6bea20ad1591db9b07507b4db959d10a318
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="struct-c"></a>struktura (C++)
`struct` — Słowo kluczowe definiuje typ struktury i/lub zmiennej typu struktury.  
  
## <a name="syntax"></a>Składnia  
  
```  
[template-spec] struct[ms-decl-spec] [tag [: base-list ]]  
{   
   member-list   
} [declarators];  
[struct] tag declarators;  
```  
  
#### <a name="parameters"></a>Parametry  
 `template-spec`  
 Opcjonalne specyfikacje szablonu. Aby uzyskać więcej informacji, zapoznaj się [specyfikacje szablonu](templates-cpp.md).  
  
 `struct`  
 `struct` — Słowo kluczowe.  
  
 `ms-decl-spec`  
 Opcjonalna specyfikacja klasy magazynowania. Aby uzyskać więcej informacji, zapoznaj się [__declspec](../cpp/declspec.md) — słowo kluczowe.  
  
 `tag`  
 Nazwa typu nadana strukturze. Znacznik staje się słowem zastrzeżonym w obrębie struktury. Znacznik jest opcjonalny. W przypadku pominięcia zostanie zdefiniowana anonimowa struktura. Aby uzyskać więcej informacji, zobacz [anonimowe typy klas](../cpp/anonymous-class-types.md).  
  
 `base-list`  
 Opcjonalna lista klas lub struktur, z której pochodzą składowe tej struktury. Zobacz [klasy podstawowej](../cpp/base-classes.md) Aby uzyskać więcej informacji. Każda podstawowa nazwa klasy lub struktury może być poprzedzone specyfikator dostępu ([publicznego](../cpp/public-cpp.md), [prywatnej](../cpp/private-cpp.md), [chronione](../cpp/protected-cpp.md)) i [wirtualnego](../cpp/virtual-cpp.md) słowo kluczowe. Znajdują się w tabeli dostęp do elementu członkowskiego [kontrolowanie dostępu do członków klasy](member-access-control-cpp.md) Aby uzyskać więcej informacji.  
  
 `member-list`  
 Lista składników struktury. Zapoznaj się [omówienie elementu członkowskiego klasy](../cpp/class-member-overview.md) Aby uzyskać więcej informacji. Jedyną różnicą jest to, że `struct` jest używany zamiast `class`.  
  
 `declarators`  
 Lista deklaratora określająca nazwy klasy. Listy deklaratorów deklarują jedno lub więcej wystąpień typu struktury. Deklaratory może zawierać listy inicjatorów, jeśli są wszystkie elementy członkowskie danych klasy `public`. Listy inicjatorów są często używane w strukturach, ponieważ są elementy członkowskie danych `public` domyślnie.  Zobacz [Przegląd Deklaratorów](../cpp/overview-of-declarators.md) Aby uzyskać więcej informacji.  
  
## <a name="remarks"></a>Uwagi  
 Typ struktury jest zdefiniowanym przez użytkownika typem złożonym. Składa się z pól lub elementów członkowskich, które mogą mieć różne typy.  
  
 W języku C++ struktury jest taka sama jak klasa z tą różnicą, że jej elementów członkowskich są `public` domyślnie.  
  
 Informacje dotyczące zarządzanych klas i struktur, zobacz [klas i struktur](../windows/classes-and-structs-cpp-component-extensions.md).  
  
## <a name="using-a-structure"></a>Korzystanie ze struktury  
 W języku C, należy jawnie użyć `struct` — słowo kluczowe, aby zadeklarować struktury. W języku C++ nie trzeba używać `struct` — słowo kluczowe po typ został zdefiniowany.  
  
 Istnieje opcja zadeklarowania zmiennych, kiedy typ struktury jest definiowany, przez umieszczenie jednej lub więcej nazw zmiennych, oddzielonych przecinkami, między zamykającym nawiasem klamrowym i średnikiem.  
  
 Zmienne struktury mogą być inicjowane. Inicjowanie dla każdej zmiennej musi być ujęte w nawiasy klamrowe.  
  
 Aby uzyskać odpowiednie informacje, zobacz [klasy](../cpp/class-cpp.md), [Unii](../cpp/unions.md), i [wyliczenia](../cpp/enumerations-cpp.md).  
  
## <a name="example"></a>Przykład  
  
```  
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
  
