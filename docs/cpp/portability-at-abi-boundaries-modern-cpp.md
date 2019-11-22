---
title: Przenośność na granicach ABI
description: Spłaszczanie C++ interfejsów do konwencji wywoływania języka C w granicach interfejsów binarnych.
ms.date: 11/19/2019
ms.topic: conceptual
ms.assetid: abbd405e-3038-427c-8c24-e00598f0936a
ms.openlocfilehash: b3b2b217739ff5900c8ef0329ff3e8909a3fe036
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74303315"
---
# <a name="portability-at-abi-boundaries"></a>Przenośność na granicach ABI

Używaj wystarczająco przenośnych typów i Konwencji w granicach interfejsów binarnych. "Typ przenośny" jest wbudowanym typem języka C lub strukturą, która zawiera tylko typy wbudowane w języku C. Typów klas można używać tylko wtedy, gdy element wywołujący i wywoływany są wyrażane zgodą na układ, konwencję wywoływania itd. Jest to możliwe tylko wtedy, gdy oba są kompilowane przy użyciu tych samych ustawień kompilatora i kompilatora.

## <a name="how-to-flatten-a-class-for-c-portability"></a>Jak spłaszczyć klasę dla przenośności C

Gdy obiekty wywołujące mogą być kompilowane przy użyciu innego kompilatora/języka, należy "spłaszczyć" do zewnętrznego interfejsu API **"C"** z określoną konwencją wywoływania:

```cpp
// class widget {
//   widget();
//   ~widget();
//   double method( int, gadget& );
// };
extern "C" {        // functions using explicit "this"
   struct widget;   // opaque type (forward declaration only)
   widget* STDCALL widget_create();      // constructor creates new "this"
   void STDCALL widget_destroy(widget*); // destructor consumes "this"
   double STDCALL widget_method(widget*, int, gadget*); // method uses "this"
}
```

## <a name="see-also"></a>Zobacz także

[Zapraszamy ponownie doC++](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[Dokumentacja języka C++](../cpp/cpp-language-reference.md)<br/>
[Standardowa biblioteka C++](../standard-library/cpp-standard-library-reference.md)
