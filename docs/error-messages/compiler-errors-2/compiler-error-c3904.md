---
title: Błąd kompilatora C3904
ms.date: 11/04/2016
f1_keywords:
- C3904
helpviewer_keywords:
- C3904
ms.assetid: 08297605-e4f2-4c6c-b637-011f1fd40631
ms.openlocfilehash: 4675bf95012c8e6662d7dba281c38ed2d684c448
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "58779875"
---
# <a name="compiler-error-c3904"></a>Błąd kompilatora C3904

"property_accessor": należy określić numer następującą liczbą parametrów:

Sprawdź liczbę parametrów w swojej `get` i `set` metody względem właściwości wymiarów.

- Liczba parametrów `get` metody musi być równa liczbie wymiarów właściwości lub mieć wartość zero dla właściwości nieindeksowanych.

- Liczba parametrów `set` metody musi być większa niż liczba wymiarów właściwości.

Aby uzyskać więcej informacji, zobacz [właściwość](../../extensions/property-cpp-component-extensions.md).

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C3904.

```
// C3904.cpp
// compile with: /clr /c
ref class X {
   property int P {
      // set
      void set();   // C3904
      // try the following line instead
      // void set(int);

      // get
      int get(int, int);   // C3904
      // try the following line instead
      // int get();
   };
};
```

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C3904.

```
// C3904b.cpp
// compile with: /clr /c
ref struct X {
   property int Q[double, double, float, float, void*, int] {
      // set
      void set(double, void*);   // C3904
      // try the following line instead
      // void set(double, double, float, float, void*, int, int);

      // get
      int get();   // C3904
      // try the following line instead
      // int get(double, double, float, float, void*, int);
   }
};
```