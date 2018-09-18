---
title: Błąd kompilatora C2299 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2299
dev_langs:
- C++
helpviewer_keywords:
- C2299
ms.assetid: d001c2bc-f6fd-47aa-8e42-0eb824d6441d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b4977f4a5ac81cf4c04d3b143f6f7e670a9d9279
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46049621"
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