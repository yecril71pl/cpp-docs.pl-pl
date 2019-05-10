---
title: Błąd kompilatora C2299
ms.date: 11/04/2016
f1_keywords:
- C2299
helpviewer_keywords:
- C2299
ms.assetid: d001c2bc-f6fd-47aa-8e42-0eb824d6441d
ms.openlocfilehash: 39659baebf7dc1859a69021f60ed452964ae61af
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2019
ms.locfileid: "65447960"
---
# <a name="compiler-error-c2299"></a>Błąd kompilatora C2299

'Funkcja': Zmiana zachowania: jawną specjalizacją nie może być Konstruktor kopiujący lub kopia operatora przypisania

Ten błąd może być też wygenerowany w wyniku pracy zgodności kompilatora, która została wykonana dla programu Visual Studio 2005: poprzednie wersje Visual C++ Konstruktor kopiujący i operator przypisania kopiowania można używać jawne specjalizacje.

Aby rozwiązać C2299, nie należy wprowadzać Konstruktor kopiujący i operator przypisania funkcji szablonu, ale zamiast funkcji inne niż szablonu, która przyjmuje typ klasy. Wszelki kod, który wywołuje Konstruktor kopiujący i operator przypisania przez jawne określenie argumentów szablonu, musi usunąć argumentów szablonu.

Poniższy przykład spowoduje wygenerowanie C2299:

```
// C2299.cpp
// compile with: /c
class C {
   template <class T>
   C (T t);

   template <> C (const C&);   // C2299
   C (const C&);   // OK
};
```