---
title: Abstrakcyjne klasy (C++) | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 91ed7cb82bbf9036a32ee20ecf33a8138086a98c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46103955"
---
# <a name="abstract-classes-c"></a>Klasy abstrakcyjne (C++)

Klasy abstrakcyjne działają jak wyrażenia ogólnych pojęć, z których mogą być uzyskane bardziej specyficzne klasy. Nie można utworzyć obiektu typu klasy abstrakcyjnej; jednak można użyć wskaźników i odwołań do typu klasy abstrakcyjnej.

Klasa, która zawiera co najmniej jedną czystą mfunkcję wirtualną jest traktowany jako klasa abstrakcyjna. Klasy pochodne klasy abstrakcyjnej muszą implementować czystą funkcję wirtualną lub są one zbyt, klasy abstrakcyjne.

Rozważmy przykład przedstawiony w [funkcji wirtualnych](../cpp/virtual-functions.md). Zamiarem klasy `Account` ma na celu dostarczenie ogólnych funkcji, ale obiekty typu `Account` są zbyt ogólne, by były przydatne. W związku z tym `Account` jest dobrym kandydatem do klasy abstrakcyjnej:

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

Jedyna różnica pomiędzy tą deklaracją, a poprzedni dotyczy `PrintBalance` jest zadeklarowana za pomocą czysty specyfikator (`= 0`).

## <a name="restrictions-on-abstract-classes"></a>Ograniczenia dotyczące klasy abstrakcyjne

Klasy abstrakcyjne nie może służyć do:

- Element członkowski danych lub zmiennych

- Typy argumentów

- Zwracane typy funkcji

- Jawne konwersje typów

Innym ograniczeniem jest to, że jeśli Konstruktor dla klasy abstrakcyjnej wywołuje jest czysta funkcja wirtualna, albo bezpośrednio lub pośrednio, wynik jest niezdefiniowany. Jednak konstruktory i destruktory klasy abstrakcyjne mogą wywoływać innych funkcji Członkowskich.

Czyste funkcje wirtualne mogą być definiowane dla klas abstrakcyjnych, ale wywołać bezpośrednio tylko przy użyciu składni:

*abstrakcyjna klasa nazwa*::*nazwy funkcji*)

Dzięki temu podczas projektowania hierarchii klas, których klas podstawowych obejmują czysto wirtualne destruktory, ponieważ destruktory klasy bazowej zawsze są wywoływane w trakcie niszczenia obiektu. Rozważmy następujący przykład:

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

Gdy obiekt wskazywany przez `pDerived` zostanie usunięty, destruktor klasy `derived` nosi nazwę i następnie destruktor klasy `base` jest wywoływana. Pusty implementacji dla czystych funkcji wirtualnych gwarantuje, czy co najmniej kilku implementacja istnieje dla tej funkcji.

> [!NOTE]
> W powyższym przykładzie czystą funkcję wirtualną `base::~base` jest wywoływana niejawnie z `derived::~derived`. Istnieje również możliwość wywołania czystych funkcji wirtualnych, które jawnie przy użyciu funkcji składowej w pełni kwalifikowanej nazwy.

## <a name="see-also"></a>Zobacz także

[Dziedziczenie](../cpp/inheritance-cpp.md)