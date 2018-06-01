---
title: Abstrakcyjnej klasy (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- classes [C++], abstract
- base classes [C++], abstract classes [C++]
- abstract classes [C++]
- derived classes [C++], abstract classes [C++]
ms.assetid: f0c5975b-39de-4d68-9640-6ce57f4632e6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c35ea26bc5dda6c0dce27217cc75784034a77554
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2018
ms.locfileid: "34705364"
---
# <a name="abstract-classes-c"></a>Klasy abstrakcyjne (C++)

Klasy abstrakcyjne działa jako wyrażeń ogólnych pojęć, z których mogą pochodzić bardziej konkretnych klas. Nie można utworzyć obiektu typu klasy abstrakcyjnej; jednak można użyć wskaźników i odwołania do typu klasy abstrakcyjnej.

Klasa, która zawiera co najmniej jeden czystej funkcji wirtualnej uważa się klasy abstrakcyjnej. Klasy pochodne klasy abstrakcyjnej klasy należy zaimplementować czystej funkcji wirtualnej lub są one, zbyt, klas abstrakcyjnych.

Za pomocą funkcji wirtualnej zadeklarowano "czysty" *czysty specyfikator* składni (opisany w [klasa implementacji protokołu](http://msdn.microsoft.com/en-us/a319f1b3-05e8-400e-950a-1ca6eb105ab5)). Rozważmy przykład przedstawionych w [funkcji wirtualnych](../cpp/virtual-functions.md). Celem klasy `Account` jest zapewnienie funkcjonalności ogólne, ale obiektów typu `Account` są zbyt ogólne użyteczne. W związku z tym `Account` są odpowiednimi kandydatami dla klasy abstrakcyjnej:

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

Jedyną różnicą między tej deklaracji i poprzedniego jest to, że `PrintBalance` jest zadeklarowany za pomocą czysty specyfikator (`= 0`).

## <a name="restrictions-on-abstract-classes"></a>Ograniczenia dotyczące klasy abstrakcyjne

Klasy abstrakcyjne nie może służyć do:

- Zmienne lub element członkowski danych

- Typy argumentów

- Zwracane typy funkcji

- Jawne konwersje typów

Innym ograniczeniem to, że jeśli konstruktora dla klasy abstrakcyjnej wymaga czystej funkcji wirtualnej albo bezpośrednio lub pośrednio, wynikiem jest niezdefiniowany. Jednak inne funkcje Członkowskie mogą wywoływać konstruktory i destruktory dla klasy abstrakcyjnej.

Czystych funkcji wirtualnych mogą być definiowane dla klas abstrakcyjnych, ale wywołać bezpośrednio tylko przy użyciu składni:

*nazwy klasy abstrakcyjne*::*nazwy funkcji*)

Dzięki temu podczas projektowania klasy hierarchie którego klasy podstawowej obejmują czysty destruktory wirtualnego, ponieważ właśnie niszczenie obiektu zawsze zostaną wywołane destruktory klasy podstawowej. Rozważmy następujący przykład:

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

Gdy obiekt wskazywany przez `pDerived` zostanie usunięty, destruktor dla klasy `derived` nosi nazwę, a następnie destruktora dla klasy `base` jest wywoływana. Pusty implementację czystej funkcji wirtualnej zapewnia istnienie przynajmniej implementację funkcji.

> [!NOTE]
> W poprzednim przykładzie, czystej funkcji wirtualnej `base::~base` jest wywoływany niejawnie z `derived::~derived`. Jest również możliwe do wywołania czystych funkcji wirtualnych jawnie przy użyciu funkcji członkowskiej w pełni kwalifikowanej nazwy.

## <a name="see-also"></a>Zobacz także

- [Dziedziczenie](../cpp/inheritance-cpp.md)
