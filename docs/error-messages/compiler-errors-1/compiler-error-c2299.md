---
title: Błąd kompilatora C2299
ms.date: 11/04/2016
f1_keywords:
- C2299
helpviewer_keywords:
- C2299
ms.assetid: d001c2bc-f6fd-47aa-8e42-0eb824d6441d
ms.openlocfilehash: 4776ddede31dbcebe56a5919fd111f4df7248215
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62182694"
---
# <a name="compiler-error-c2299"></a>Błąd kompilatora C2299

'Funkcja': Zmiana zachowania: jawną specjalizacją nie może być Konstruktor kopiujący lub kopia operatora przypisania

Ten błąd może być też wygenerowany w wyniku pracy zgodności kompilatora, która została wykonana dla programu Visual C++ 2005: poprzednie wersje programu Visual C++ może jawne specjalizacje Konstruktor kopiujący lub kopia operatora przypisania.

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