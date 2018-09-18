---
title: Przenośność na granicach ABI (Modern C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: abbd405e-3038-427c-8c24-e00598f0936a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 891f56d763fc86efd62fb5bae3b21498336a8ccc
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46058422"
---
# <a name="portability-at-abi-boundaries-modern-c"></a>Przenośność na granicach ABI (Modern C++)

Użyj typów wystarczająco przenośnych i konwencje na granicach interfejsem binarnym. "Przenośne type" jest typem wbudowanym C lub struktura, która zawiera tylko typy wbudowane C. Typy klas należy używać tylko podczas obiektami wywołującym i wywoływanym wyrażanie zgody na układ, wywołanie Konwencji itp. Jest to możliwe tylko wtedy, gdy oba są kompilowane przy użyciu tego samego środowiska kompilatora i ustawienia kompilatora.

## <a name="how-to-flatten-a-class-for-c-portability"></a>Jak spłaszczanie klasy przenośności C

Podczas wywoływania może być skompilowana przy użyciu innego językowi kompilatora, a następnie "spłaszczanie", aby **extern "C"** interfejsu API za pomocą określonych konwencji wywoływania:

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

[Witamy z powrotem w C++](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[Dokumentacja języka C++](../cpp/cpp-language-reference.md)<br/>
[Standardowa biblioteka C++](../standard-library/cpp-standard-library-reference.md)