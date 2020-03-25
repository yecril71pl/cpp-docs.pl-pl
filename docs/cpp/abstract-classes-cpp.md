---
title: Klasy abstrakcyjne (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- classes [C++], abstract
- base classes [C++], abstract classes [C++]
- abstract classes [C++]
- derived classes [C++], abstract classes [C++]
ms.assetid: f0c5975b-39de-4d68-9640-6ce57f4632e6
ms.openlocfilehash: 2ea9d3765f65434cb738c2b7c53f9499bba24545
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80181697"
---
# <a name="abstract-classes-c"></a>Klasy abstrakcyjne (C++)

Klasy abstrakcyjne pełnią rolę wyrażeń ogólnych, z których można wyprowadzać bardziej konkretne klasy. Nie można utworzyć obiektu typu klasy abstrakcyjnej; można jednak używać wskaźników i odwołań do typów klas abstrakcyjnych.

Klasa, która zawiera co najmniej jedną czystą funkcję wirtualną, jest uznawana za klasę abstrakcyjną. Klasy pochodne klasy abstrakcyjnej muszą implementować czystą funkcję wirtualną lub są one również klasami abstrakcyjnymi.

Rozważmy przykład przedstawiony w [funkcjach wirtualnych](../cpp/virtual-functions.md). Celem klasy `Account` jest zapewnienie ogólnych funkcji, ale obiekty typu `Account` są zbyt ogólne, aby były użyteczne. W związku z tym `Account` jest dobrym kandydatem do klasy abstrakcyjnej:

```cpp
// deriv_AbstractClasses.cpp
// compile with: /LD
class Account {
public:
   Account( double d );   // Constructor.
   virtual double GetBalance();   // Obtain balance.
   virtual void PrintBalance() = 0;   // Pure virtual function.
private:
    double _balance;
};
```

Jedyną różnicą między tą deklaracją a poprzednią jest to, że `PrintBalance` jest zadeklarowany za pomocą czystego specyfikatora (`= 0`).

## <a name="restrictions-on-abstract-classes"></a>Ograniczenia dotyczące klas abstrakcyjnych

Klas abstrakcyjnych nie można używać dla:

- Zmienne lub dane elementu członkowskiego

- Typy argumentów

- Zwracane typy funkcji

- Typy konwersji jawnych

Inne ograniczenie polega na tym, że jeśli Konstruktor klasy abstrakcyjnej wywołuje czystą funkcję wirtualną, bezpośrednio lub pośrednio, wynik jest niezdefiniowany. Konstruktory i destruktory dla klas abstrakcyjnych mogą jednak wywoływać inne funkcje członkowskie.

Czyste funkcje wirtualne można definiować dla klas abstrakcyjnych, ale można je wywoływać bezpośrednio tylko przy użyciu składni:

*abstrakcyjna klasa-Name*::*Function-Name*()

Pomaga to podczas projektowania hierarchii klas, których klasy podstawowe zawierają czyste destruktory wirtualne, ponieważ destruktory klasy bazowej są zawsze wywoływane w procesie niszczenia obiektu. Rozważmy następujący przykład:

```cpp
// Declare an abstract base class with a pure virtual destructor.
// deriv_RestrictionsonUsingAbstractClasses.cpp
class base {
public:
    base() {}
    virtual ~base()=0;
};

// Provide a definition for destructor.
base::~base() {}

class derived:public base {
public:
    derived() {}
    ~derived(){}
};

int main() {
    derived *pDerived = new derived;
    delete pDerived;
}
```

Gdy obiekt wskazywany przez `pDerived` jest usuwany, destruktor dla klasy `derived` jest wywoływany, a następnie destruktor klasy `base` jest wywoływany. Pusta implementacja czystej funkcji wirtualnej zapewnia, że dla funkcji istnieje co najmniej pewna implementacja.

> [!NOTE]
> W poprzednim przykładzie czysta funkcja wirtualna `base::~base` jest wywoływana niejawnie z `derived::~derived`. Istnieje również możliwość wywołania czystych funkcji wirtualnych jawnie przy użyciu w pełni kwalifikowanej nazwy funkcji składowej.

## <a name="see-also"></a>Zobacz też

[Dziedziczenie](../cpp/inheritance-cpp.md)
