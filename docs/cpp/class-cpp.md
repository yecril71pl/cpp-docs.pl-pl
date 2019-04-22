---
title: klasa (C++)
ms.date: 11/04/2016
f1_keywords:
- class_cpp
helpviewer_keywords:
- class types [C++], class statements
- class keyword [C++]
ms.assetid: dd23c09f-6598-4069-8bff-69c7f2518b9f
ms.openlocfilehash: c4ef9690a41737147354ee0976f6912c4711ff67
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58774818"
---
# <a name="class-c"></a>klasa (C++)

**Klasy** — słowo kluczowe deklaruje typu klasy lub definiuje obiekt typu klasy.

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

*template-spec*<br/>
Opcjonalne specyfikacje szablonu. Aby uzyskać więcej informacji, zobacz [szablony](templates-cpp.md).

*class*<br/>
**Klasy** — słowo kluczowe.

*ms-decl-spec*<br/>
Opcjonalna specyfikacja klasy magazynowania. Aby uzyskać więcej informacji, zobacz [__declspec](../cpp/declspec.md) — słowo kluczowe.

*Tag*<br/>
Nazwa typu nadana tej klasy. Znacznik staje się słowem zastrzeżonym w zakresie klasy. Znacznik jest opcjonalny. W przypadku pominięcia jest zdefiniowana klasa anonimowa. Aby uzyskać więcej informacji, zobacz [anonimowe typy klas](../cpp/anonymous-class-types.md).

*base-list*<br/>
Opcjonalna lista klas lub struktur tej klasy, z której pochodzą składowe. Zobacz [klasy podstawowej](../cpp/base-classes.md) Aby uzyskać więcej informacji. Każda podstawowa nazwy klasy lub struktury może być poprzedzona przez specyfikator dostępu ([publicznych](../cpp/public-cpp.md), [prywatnej](../cpp/private-cpp.md), [chronione](../cpp/protected-cpp.md)) i [wirtualnego](../cpp/virtual-cpp.md) słowo kluczowe. Zobacz tabelę dostępu do elementu członkowskiego w [kontrolowanie dostępu do składowych klasy](member-access-control-cpp.md) Aby uzyskać więcej informacji.

*Lista elementów członkowskich*<br/>
Lista składowych klasy. Zapoznaj się [omówienie składowej klasy](../cpp/class-member-overview.md) Aby uzyskać więcej informacji.

*deklaratory*<br/>
Lista deklaratora określająca nazwy co najmniej jedno wystąpienie typu klasy. Deklaratory mogą zawierać listy inicjatorów, jeśli wszystkie składowe danych klasy są **publicznych**. Jest to bardziej powszechne w strukturach, w których elementy członkowskie danych są **publicznych** domyślnie niż w klasach. Zobacz [Przegląd Deklaratorów](../cpp/overview-of-declarators.md) Aby uzyskać więcej informacji.

## <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat klas ogólnie rzecz biorąc, można skorzystać z jednego z następujących tematów:

- [struct](../cpp/struct-cpp.md)

- [Unia](../cpp/unions.md)

- [__multiple_inheritance](../cpp/inheritance-keywords.md)

- [__single_inheritance](../cpp/inheritance-keywords.md)

- [__virtual_inheritance](../cpp/inheritance-keywords.md)

Aby uzyskać informacje dotyczące zarządzanych klas i struktur w C++sposób niezamierzony i C++/CX, zobacz [klasy i struktury](../extensions/classes-and-structs-cpp-component-extensions.md)

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

## <a name="see-also"></a>Zobacz także

[Słowa kluczowe](../cpp/keywords-cpp.md)<br/>
[Klasy i struktury](../cpp/classes-and-structs-cpp.md)