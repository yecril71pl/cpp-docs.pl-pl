---
title: Błąd kompilatora C2299
ms.date: 11/04/2016
f1_keywords:
- C2299
helpviewer_keywords:
- C2299
ms.assetid: d001c2bc-f6fd-47aa-8e42-0eb824d6441d
ms.openlocfilehash: 009a441ec610053176e79126d9f2663f29b26bc6
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759051"
---
# <a name="compiler-error-c2299"></a>Błąd kompilatora C2299

"Function": zmiana zachowania: Jawna specjalizacja nie może być konstruktorem kopiującym ani operatorem przypisania kopiowania

Ten błąd może być również wygenerowany jako wynik zgodności kompilatora, który został wykonany dla programu Visual Studio 2005: poprzednie wersje wizualizacji C++ dopuszczają jawne specjalizacje dla konstruktora kopiującego lub operatora przypisania kopiowania.

Aby rozwiązać C2299, nie należy tworzyć konstruktora kopiującego ani operatora przypisania jako funkcji szablonu, ale raczej nie jest funkcją szablonu, która przyjmuje typ klasy. Każdy kod, który wywołuje Konstruktor kopiujący lub operator przypisania przez jawne określenie argumentów szablonu, musi usunąć argumenty szablonu.

Poniższy przykład generuje C2299:

```cpp
// C2299.cpp
// compile with: /c
class C {
   template <class T>
   C (T t);

   template <> C (const C&);   // C2299
   C (const C&);   // OK
};
```
