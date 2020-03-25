---
title: klasa (C++)
ms.date: 11/04/2016
f1_keywords:
- class_cpp
helpviewer_keywords:
- class types [C++], class statements
- class keyword [C++]
ms.assetid: dd23c09f-6598-4069-8bff-69c7f2518b9f
ms.openlocfilehash: c1b9d8f6510dfe15644f0e47cad7e0aecbac36c9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180979"
---
# <a name="class-c"></a>klasa (C++)

Słowo kluczowe **Class** deklaruje typ klasy lub definiuje obiekt typu klasy.

## <a name="syntax"></a>Składnia

```
[template-spec]
class [ms-decl-spec] [tag [: base-list ]]
{
   member-list
} [declarators];
[ class ] tag declarators;
```

#### <a name="parameters"></a>Parametry

*szablon — Specyfikacja*<br/>
Opcjonalne specyfikacje szablonu. Aby uzyskać więcej informacji, zapoznaj się z [szablonami](templates-cpp.md).

*class*<br/>
Słowo kluczowe **Class** .

*MS-decl-spec*<br/>
Opcjonalna specyfikacja klasy magazynowania. Aby uzyskać więcej informacji, zapoznaj się ze słowem kluczowym [__declspec](../cpp/declspec.md) .

*seryjn*<br/>
Nazwa typu nadana klasie. Tag zostaje zastrzeżonym słowem w zakresie klasy. Znacznik jest opcjonalny. W przypadku pominięcia zostanie zdefiniowana Klasa anonimowa. Aby uzyskać więcej informacji, zobacz [anonimowe typy klas](../cpp/anonymous-class-types.md).

*Lista podstawowa*<br/>
Opcjonalna lista klas lub struktur, z których ta klasa będzie dziedziczyć członków. Aby uzyskać więcej informacji, zobacz [klasy bazowe](../cpp/base-classes.md) . Każda nazwa klasy bazowej lub struktury może być poprzedzona przez specyfikator dostępu ([Public](../cpp/public-cpp.md), [Private](../cpp/private-cpp.md), [Protected](../cpp/protected-cpp.md)) i [wirtualne](../cpp/virtual-cpp.md) słowo kluczowe. Aby uzyskać więcej informacji, zobacz tabelę dostępu do elementów członkowskich w temacie [Kontrola dostępu do składowych klasy](member-access-control-cpp.md) .

*Lista elementów członkowskich*<br/>
Lista elementów członkowskich klasy. Aby uzyskać więcej informacji, zapoznaj się z [omówieniem składowej klasy](../cpp/class-member-overview.md) .

*Deklaratory*<br/>
Lista deklarator określa nazwy jednego lub większej liczby wystąpień typu klasy. Deklaratory może zawierać listę inicjatorów, jeśli wszystkie elementy członkowskie danych klasy są **publiczne**. Jest to bardziej popularne w strukturach, których elementy członkowskie danych są domyślnie **publiczne** , niż w klasach. Aby uzyskać więcej informacji [, zobacz Omówienie Deklaratory](../cpp/overview-of-declarators.md) .

## <a name="remarks"></a>Uwagi

Więcej informacji o klasach ogólnie można znaleźć w następujących tematach:

- [struct](../cpp/struct-cpp.md)

- [Unii](../cpp/unions.md)

- [__multiple_inheritance](../cpp/inheritance-keywords.md)

- [__single_inheritance](../cpp/inheritance-keywords.md)

- [__virtual_inheritance](../cpp/inheritance-keywords.md)

Aby uzyskać informacje dotyczące zarządzanych klas i struktur w C++/CLI i C++/CX, zobacz [klasy i struktury](../extensions/classes-and-structs-cpp-component-extensions.md)

## <a name="example"></a>Przykład

```cpp
// class.cpp
// compile with: /EHsc
// Example of the class keyword
// Exhibits polymorphism/virtual functions.

#include <iostream>
#include <string>
#define TRUE = 1
using namespace std;

class dog
{
public:
   dog()
   {
      _legs = 4;
      _bark = true;
   }

   void setDogSize(string dogSize)
   {
      _dogSize = dogSize;
   }
   virtual void setEars(string type)      // virtual function
   {
      _earType = type;
   }

private:
   string _dogSize, _earType;
   int _legs;
   bool _bark;

};

class breed : public dog
{
public:
   breed( string color, string size)
   {
      _color = color;
      setDogSize(size);
   }

   string getColor()
   {
      return _color;
   }

   // virtual function redefined
   void setEars(string length, string type)
   {
      _earLength = length;
      _earType = type;
   }

protected:
   string _color, _earLength, _earType;
};

int main()
{
   dog mongrel;
   breed labrador("yellow", "large");
   mongrel.setEars("pointy");
   labrador.setEars("long", "floppy");
   cout << "Cody is a " << labrador.getColor() << " labrador" << endl;
}
```

## <a name="see-also"></a>Zobacz też

[Słowa kluczowe](../cpp/keywords-cpp.md)<br/>
[Klasy i struktury](../cpp/classes-and-structs-cpp.md)
